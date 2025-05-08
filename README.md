# This repo is a clone
- Main repo here [container-generator-ts](https://github.com/orbitalconsortium/orbital-collection/tree/master/container-generator-ts)
# Orbitals Container Generator (NodeJS only!)

A TypeScript library and CLI tool for generating WebAssembly (WASM) container files for orbital collections. This tool embeds data into a WebAssembly module using a template, making it easy to create data containers for the orbital-collection system.

## Features

- Generate WASM containers from any file type
- Support Node.js environments only!
- Customizable WebAssembly template
- Proper handling of both relative and absolute file paths
- Automatic creation of output directories


## Installation

### Prerequisites

- Node.js 14 or higher
- npm or yarn

### Setup

```bash
# Clone the repository
git clone https://github.com/wisdomabioye/orbital-container-generator-nodejs-only.git
cd orbital-container-generator-nodejs-only

# Install dependencies
npm install

# Build the project
npm run build
```
## CLI Usage

The CLI tool can be used to generate WASM containers from any file:

```bash
# Using from the project directory (wasm output are created in the output folder)
node ./dist/cli.js generate path/to/data.file -o container1.wasm # wasm output in ./output/container1.wasm
npm run generate path/to/data.file # wasm output in ./output/container.wasm

### Options

- `-o, --output <output>`: Output file path (default: "container.wasm")
- `-t, --template <template>`: Custom template WAT file path


# Generate a container with a custom template
node ./dist/cli.js generate path/to/data.file -o container.wasm -t custom-template.wat # wasm output in ./output/container.wasm

# Using relative paths
node ./dist/cli.js generate ./data/image.png -o container.wasm # wasm output in ./output/container.wasm
```

## Container Format

The generated WASM container has the following structure:

1. A memory section with the embedded data
2. An `__execute` function that returns a pointer to a CallResponse structure
3. The CallResponse structure has the format:
   - 16 bytes for alkanes count (always 0 for containers)
   - The embedded data
   - 
## License

MIT