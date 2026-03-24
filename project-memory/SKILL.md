---
name: project-memory
description: Maintains a persistent memory of the project in UNDERSTAND.md. Use when starting a new task, exploring a codebase, or completing significant changes to ensure context is retained for future agents.
---

# Project Memory Skill

This skill enables agents to maintain a continuous, persistent memory of a project across sessions. It transforms the agent into a self-learner by treating the project's workspace as a place to store and retrieve high-level knowledge, architectural decisions, and important context.

## The UNDERSTAND.md File

The central source of truth for your memory is a file named `UNDERSTAND.md`, located at the root of the project workspace. This file acts as your "second brain."

### 1. Initializing Memory

If you are asked to learn about a project or establish context, immediately check if `UNDERSTAND.md` exists at the project root.
- If it exists, read it completely to internalize the project's state, rules, and architecture.
- If it does not exist, create it using the template provided below.

### 2. Updating Memory

You are responsible for keeping this memory up to date. You must update `UNDERSTAND.md` whenever:
- You discover a non-obvious architectural pattern, core assumption, or convention.
- You make a significant structural or architectural change to the codebase.
- You solve a complex bug whose root cause might trip up future work.
- The user explicitly asks you to remember or document something about the project.

### 3. Creating Additional Knowledge Files

If a specific domain or sub-system becomes too complex to fit cleanly into `UNDERSTAND.md` (e.g., exceeding 150 lines), create a separate `.md` file in an appropriate location (e.g., `docs/architecture.md`) and link to it from `UNDERSTAND.md`.

## Structure of UNDERSTAND.md

If you need to create `UNDERSTAND.md`, use the following structure:

```markdown
# Project Understanding

This file acts as the persistent memory for AI agents working on this project. It contains high-level context, architectural decisions, and important constraints.

## Core Purpose
[A brief description of what the project is and what problem it solves]

## Architecture & Tech Stack
[Key technologies, frameworks, and architectural patterns (e.g., MVC, clean architecture)]

## Key Conventions & Rules
- [e.g., "All new components must be purely functional"]
- [e.g., "Use absolute imports starting with '@/'"]

## Ongoing Decisions & Discoveries
- [Date] - [Discovery or decision made]
```

## Constraints
- **Keep it concise:** The goal is high-signal context. Avoid repeating information that is already obvious from reading `package.json` or standard framework boilerplate.
- **Do not store secrets:** Never write API keys, passwords, or personal credentials into this or any other `.md` file.
- **Be factual:** Write from the perspective of an objective observer documenting the system.
