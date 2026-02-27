# Claude Code Brain

A research project extending [EverMemOS](https://github.com/EverMind-AI/EverMemOS) and [evermem-claude-code](https://github.com/EverMind-AI/evermem-claude-code) with structured workflows for enhanced AI-assisted development.

## Overview

Claude Code Brain builds upon existing memory infrastructure for Claude Code to provide:

- **Persistent Memory**: Automatic saving and retrieval of conversation context across sessions
- **Structured Workflows**: Pre-built slash commands for analysis, planning, and implementation
- **Local Deployment**: Fully self-hosted memory system with Docker-based infrastructure
- **Multi-Agent Support**: Collaborative AI agents for complex development tasks

## Forked Projects

This project is based on and extends the following open-source projects:

| Project | Original Repository | Fork | License |
|---------|---------------------|------|---------|
| **EverMemOS** | [EverMind-AI/EverMemOS](https://github.com/EverMind-AI/EverMemOS) | [wangmax2011/EverMemOS](https://github.com/wangmax2011/EverMemOS) | Apache 2.0 |
| **evermem-claude-code** | [EverMind-AI/evermem-claude-code](https://github.com/EverMind-AI/evermem-claude-code) | [wangmax2011/evermem-claude-code](https://github.com/wangmax2011/evermem-claude-code) | MIT |

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    Claude Code Brain                        │
├─────────────────────────────────────────────────────────────┤
│  Workflow Layer (_bmad/)                                    │
│  ├── Core Workflows (brainstorming, elicitation)           │
│  └── Implementation Workflows (PRD, Architecture, Dev)     │
├─────────────────────────────────────────────────────────────┤
│  EverMemOS (Memory Backend)                                 │
│  ├── Vector Database (Milvus)                               │
│  ├── Document Store (MongoDB)                               │
│  ├── Search Engine (Elasticsearch)                          │
│  └── Cache Layer (Redis)                                    │
├─────────────────────────────────────────────────────────────┤
│  evermem-claude-code (Plugin)                               │
│  ├── Session Memory Injection                               │
│  ├── Automatic Memory Save                                  │
│  └── Memory Hub Dashboard                                   │
└─────────────────────────────────────────────────────────────┘
```

## Prerequisites

- [Claude Code](https://code.claude.com/) installed
- [Docker](https://www.docker.com/) and Docker Compose
- [Node.js](https://nodejs.org/) 18+ (for plugin development)
- [Python](https://www.python.org/) 3.11+ with [uv](https://github.com/astral-sh/uv) (for EverMemOS)

## Quick Start

### 1. Clone This Repository

```bash
git clone git@github.com:wangmax2011/claude-code-brain.git
cd claude-code-brain
```

### 2. Set Up EverMemOS (Memory Backend)

```bash
cd /path/to/EverMemOS
./install.sh
```

For local setup details, see [EverMemOS LOCAL_SETUP.md](https://github.com/wangmax2011/EverMemOS/blob/main/LOCAL_SETUP.md).

### 3. Install EverMem Claude Code Plugin

```bash
cd /path/to/evermem-claude-code
./install-plugin.sh
```

### 4. Configure Environment

Add to your shell profile (`~/.zshrc` or `~/.bashrc`):

```bash
export EVERMEM_API_URL="http://localhost:1995"
```

### 5. Verify Installation

Run `/evermem:help` in Claude Code to check the plugin status.

## Available Workflows

This project includes structured workflows for AI-assisted development:

### Analysis
- `/workflow-init` - Initialize new project
- `/product-brief` - Create comprehensive product briefs

### Planning
- `/create-prd` - Generate Product Requirements Documents
- `/create-architecture` - Design system architecture
- `/create-ux-design` - Plan UX patterns and design systems

### Solutioning
- `/create-epics-stories` - Break down requirements into stories
- `/check-readiness` - Validate implementation readiness

### Implementation
- `/create-story` - Generate next development story
- `/dev-story` - Execute story implementation
- `/code-review` - Perform adversarial code review

## Project Structure

```
.
├── _bmad/                          # Workflow definitions
│   ├── core/                       # Core workflows
│   │   ├── workflows/              # Brainstorming, elicitation, etc.
│   │   └── agents/                 # Agent configurations
│   └── bmm/                        # Implementation workflows
│       └── workflows/
│           ├── 1-analysis/
│           ├── 2-plan-workflows/
│           └── 4-impl-workflows/
├── _bmad-output/                   # Generated documentation output
└── .claude/                        # Claude Code configuration
    ├── commands/                   # Custom slash commands
    └── settings.local.json         # Permission settings
```

## Usage Examples

### Start a New Project

```
/workflow-init
```

### Create Product Requirements

```
/create-prd
```

### Search Memory

```
/evermem:search authentication implementation
```

### Open Memory Hub

```
/evermem:hub
```

## Development

### Modifying EverMemOS

See [EverMemOS Contributing Guide](https://github.com/wangmax2011/EverMemOS/blob/main/CONTRIBUTING.md).

### Modifying Plugin

See [evermem-claude-code README](https://github.com/wangmax2011/evermem-claude-code/blob/main/README.md).

## Contributing

Contributions are welcome! Please:

1. Fork the relevant repository (EverMemOS, evermem-claude-code, or this project)
2. Create a feature branch
3. Make your changes
4. Submit a pull request

For major changes, please open an issue first to discuss what you would like to change.

## License

This project is licensed under the [Apache License 2.0](LICENSE).

### Third-Party Licenses

- **EverMemOS**: Apache License 2.0
- **evermem-claude-code**: MIT License

See individual project repositories for full license details.

## Acknowledgments

- [EverMind AI](https://evermind.ai/) for creating EverMemOS and the memory infrastructure
- [Anthropic](https://www.anthropic.com/) for Claude Code

## Support

- **EverMemOS Issues**: [wangmax2011/EverMemOS/issues](https://github.com/wangmax2011/EverMemOS/issues)
- **Plugin Issues**: [wangmax2011/evermem-claude-code/issues](https://github.com/wangmax2011/evermem-claude-code/issues)
- **This Project Issues**: [wangmax2011/claude-code-brain/issues](https://github.com/wangmax2011/claude-code-brain/issues)

---

**Note**: This is a research project. The memory system requires significant resources (recommended: 16GB+ RAM, 50GB+ disk space for Docker containers).
