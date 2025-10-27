# ChainJockey
BurpSuite extension for taming async API flows. Chain state-dependent requests, add delays for resource readiness, and define custom retry logic. Built to handle the complexity that breaks Macros.

## Why?

**Built for:**
- Async API flows where timing matters
- Resources that need to reach a specific state before the next request
- Custom retry logic that isn't braindead
- Complex request chains that other tools can't touch

## Features

- **User-defined flows** - Chain requests your way
- **State management** - Wait for resources to be ready
- **Custom delays** - Let async operations complete
- **Retry logic** - Define your own failure handling
- **Actually works**

## Quick Start

1. Load extension in BurpSuite
2. Define your flow chain
3. Set state checks and delays
4. Configure retry behavior
5. Let it ride

## Example Flow

```
POST /api/order          → Wait 2s for order processing
GET /api/order/{id}      → Retry on 404 (max 3x, 1s delay)
PUT /api/order/{id}/ship → Execute when status=="processed"
```

## Installation

```bash
# Clone the repo
git clone https://github.com/sentient-zero/ChainJockey.git

# Load in BurpSuite
Extensions → Add → Select ChainJockey.py
```

## The Problem

**Macros:** Too rigid. Can't handle state dependencies or async timing.

**ATOR:** Good foundation, but limited retry logic and no state awareness.

**ChainJockey:** Handles the messy reality of modern APIs.

## Use Cases

- OAuth flows with token refresh dependencies
- Multi-step workflows requiring resource state validation
- APIs with eventual consistency that need retry logic
- Complex auth chains with timing requirements
- Any scenario where "just replay this request" doesn't cut it

## Configuration

Define flows in JSON or via the UI. Specify:
- Request sequence
- State validation logic
- Delay intervals
- Retry conditions and limits
- Failure handling

## Contributing

PRs welcome. Keep it clean, keep it fast.

## License

MIT - Use it, fork it, make it better.

## Credits

Inspired by the limitations of other tooling. Built because security testing shouldn't be blocked by tooling.

---

**sentient-zero** | [GitHub](https://github.com/sentient-zero) | Built for the chaos

