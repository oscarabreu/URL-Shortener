# URL-Shortener Service

# Overview

This Go program is a CLI URL shortener service that redirects users to full 
URLs based on provided mappings. It supports three backends for storing URL
mappings: JSON, YAML, and BoltDB. Users can specify the backend using 
command-line flags.

# Prerequisites

1. Go (Golang) should be installed on your system.
2. Install the required dependencies with go get github.com/boltdb/bolt gopkg.in/yaml.v2.

# Usage

1. Clone or download the program's source code.
2. Open a terminal and navigate to the directory containing the program.
3. Compile the program using the following command: `go build main.go`
4. Run the compiled program with optional flags:
```
    -json (string): Path to a JSON file containing URL mappings.
    -yaml (string): Path to a YAML file containing URL mappings.
    -bolt (string): Path to a BoltDB file containing URL mappings.
```
Example:
`./main -json url_mappings.json`

5. The program will start a server on port 8080.
6. Access the shortened URLs in your web browser. For example, if you 
have a mapping `/short` to `https://example.com`, access `http://localhost:8080/short` 
to be redirected to `https://example.com`.
7. To exit the program, press Ctrl+C.

## Supported Formats

### JSON Format

Create a JSON file with the following format:


```
[
  {
    "path": "/short",
    "url": "https://example.com"
  },
  {
    "path": "/go",
    "url": "https://golang.org"
  }
]
```
### YAML Format

Create a YAML file with the following format:

```
- path: /short
  url: https://example.com
- path: /go
  url: https://golang.org
```

BoltDB Format

Use a BoltDB file with a bucket named `pathstourls`. Store key-value pairs 
where the key is the path, and the value is the corresponding URL.

## Credits



This program is based on tutorials by [John Calhoun](https://github.com/joncalhoun). I followed along with his guidance, and will expand upon it. 
Special thanks to John for his valuable teachings and resources.
