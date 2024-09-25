# Flow Log Parser and Tagger

## Overview

This project provides a Java-based tool for parsing flow log data and mapping rows to tags based on a lookup table. It is designed to process large flow log files (up to 10MB) and supports a lookup table containing up to 10,000 mappings. The tool generates an output file with statistics on matched tags and port/protocol combinations.

## Features

- **Processes Large Files**: Can handle flow log files up to 10MB and lookup tables with 10,000 mappings.
- **Line-by-Line Processing**: Efficiently processes logs line by line to manage memory usage.
- **Supports Multiple Tag Mappings**: Multiple tags can be mapped to the same port and protocol combination.
- **Case-Insensitive Protocol Matching**: The protocol matching is case-insensitive to ensure compatibility with diverse inputs.
- **Detailed Output**: Generates a CSV output file containing the count of matches for each tag and for each port/protocol combination.

## Input Files

1. **Flow Log File** (`flow_log.txt`): A plain text file containing flow log entries. Each log entry should have at least 7 fields, including the destination port and protocol.
2. **Lookup Table** (`lookup_table.csv`): A CSV file with three columns: 
    - Destination Port (`dstport`)
    - Protocol (TCP/UDP/Other)
    - Tag (a string label mapped to the port/protocol combination)

## Output

- **Output CSV** (`output.csv`): The result of the parsing, including:
    1. Tag counts showing how many times each tag was matched.
    2. Counts of each port and protocol combination.

## How It Works

1. **PortProtocol Class**: Represents a combination of destination port and protocol, used as a key in the lookup table.
2. **loadLookupTable Method**: Reads the lookup table CSV file and maps each port/protocol combination to one or more tags.
3. **parseFlowLog Method**: Processes the flow log file line by line, counts matches for tags and port/protocol combinations, and updates the statistics.
4. **writeOutput Method**: Writes the tag counts and port/protocol combination counts to the output CSV file.
5. **Main Method**: Orchestrates the loading of the lookup table, parsing the flow log, and writing the results to the output file.

## Usage

1. Place your flow log file (`flow_log.txt`) and lookup table (`lookup_table.csv`) in the project directory.
2. Run the program using the following command:
   ```bash
   java FlowLogParser
