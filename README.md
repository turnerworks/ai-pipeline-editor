# AI Pipeline Editor

A visual node-based AI pipeline editor for creating and running AI workflows with input, transform, and output nodes.

![Pipeline Editor Screenshot](https://raw.githubusercontent.com/turnerworks/ai-pipeline-editor/main/screenshot.png)

## Features

- **Visual Node Editor**: Drag-and-drop interface for building AI pipelines
- **Multiple Input Types**: Text, Voice, and File inputs
- **Transform Nodes**: Rewrite, Classify, Translate, Extract, and Summarize
- **Output Options**: Text output and Email sending
- **Real-time Status**: Visual indicators showing node readiness

## How It Works

The AI Pipeline Editor follows a flow-based architecture where data flows from Input nodes through Transform nodes to Output nodes.

```mermaid
flowchart TD
    subgraph Inputs["INPUT NODES"]
        TI["Text Input"]
        VI["Voice Input"]
        FI["File Input"]
    end

    subgraph Transforms["TRANSFORM NODES"]
        RW["Rewrite"]
        CL["Classify"]
        TR["Translate"]
        EX["Extract"]
        SM["Summarize"]
    end

    subgraph Outputs["OUTPUT NODES"]
        TO["Text Output"]
        SE["Send Email"]
    end

    TI --> RW
    TI --> CL
    VI --> TR
    VI --> EX
    FI --> SM
    FI --> RW
    
    RW --> TO
    CL --> TO
    TR --> SE
    EX --> TO
    SM --> SE
```

## Architecture & Behavior

```mermaid
stateDiagram-v2
    [*] --> Ready: Node Created
    Ready --> Processing: Run Pipeline
    Processing --> Complete: Success
    Processing --> Error: Failure
    Complete --> Ready: Reset
    Error --> Ready: Reset
```

## Node Types

| Node Type | Category | Description |
|-----------|----------|-------------|
| Text Input | Input | Accept text data |
| Voice Input | Input | Accept audio/voice data |
| File Input | Input | Accept file uploads |
| Rewrite | Transform | Rewrite content with AI |
| Classify | Transform | Categorize content |
| Translate | Transform | Translate to other languages |
| Extract | Transform | Extract key information |
| Summarize | Transform | Create summaries |
| Text Output | Output | Display text results |
| Send Email | Output | Send results via email |

## Usage

1. Drag nodes from the sidebar onto the canvas
2. Connect nodes by dragging from output ports to input ports
3. Configure nodes using the properties panel
4. Click "Run Pipeline" to execute

## License

MIT License
