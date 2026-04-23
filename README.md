[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/steimerbyte)

# OpenRouter Image CLI

A powerful command-line tool for generating images using OpenRouter's API with full support for all available parameters.

## Features

- **Full OpenRouter API Support** - All chat completions parameters
- **Multiple Image Models** - Support for riverflow, gemini, GPT-5 image, and more
- **Base64 & URL Output** - Handles both response formats
- **Configurable** - JSON config file with defaults
- **Auto-Save** - Downloads images to ~/Bilder by default

## Installation

```bash
# Clone repo
git clone https://github.com/alephtex/openrouter-image-cli.git
cd openrouter-image-cli

# Make executable
chmod +x openrouter-img

# Setup config
cp config.json.example ~/.local/share/openrouter-img/config.json
# Edit config.json and add your API key
```

## Configuration

Edit `~/.local/share/openrouter-img/config.json`:

```json
{
  "apiKey": "sk-or-v1-your-key",
  "defaultModel": "sourceful/riverflow-v2-pro"
}
```

## Usage

```bash
# Basic
./openrouter-img -p "a beautiful sunset"

# With model and aspect ratio
./openrouter-img -p "cyberpunk city" -m sourceful/riverflow-v2-fast -a 16:9

# Full parameters
./openrouter-img -p "portrait" \
  -m sourceful/riverflow-v2-pro \
  -a 1:1 \
  --temperature 0.8 \
  --seed 42 \
  -v

# List available image models
./openrouter-img -l
```

## All Options

```
CORE OPTIONS:
  -p, --prompt <text>        Image prompt (required)
  -m, --model <model>       Model (default: sourceful/riverflow-v2-pro)
  -o, --output <file>       Custom output filename
  -d, --dir <path>          Output directory (default: ~/Bilder)
  -s, --system <text>      System prompt

GENERATION PARAMS:
  --max-tokens <N>          Max tokens
  --temperature <0-2>       Sampling temperature
  --top-p <0-1>             Nucleus sampling
  --top-k <N>               Top-k sampling
  --stop <tokens>           Stop sequences
  --seed <N>                Random seed
  --presence-penalty <-2-2> Presence penalty
  --frequency-penalty <-2-2> Frequency penalty

IMAGE OPTIONS:
  -n, --num <N>             Number of images
  -a, --aspect <ratio>     Aspect: 1:1, 16:9, 9:16, 4:3, 3:2, 21:9
  -r, --resolution <res>   Resolution: 1024x1024, 1792x1024

OTHER:
  --retry <N>               Max retries
  -l, --list-models         List image models
  -v, --verbose             Verbose output
```

## Available Image Models

| Model | Description |
|-------|-------------|
| `sourceful/riverflow-v2-pro` | High quality (recommended) |
| `sourceful/riverflow-v2-fast` | Fast generation |
| `google/gemini-2.5-flash-image` | Fast, cheap |
| `openai/gpt-5-image` | Premium quality |
| `google/gemini-3-pro-image-preview` | Latest Gemini |
| `openrouter/auto` | Automatic model selection |

## API Docs

- [OpenRouter Chat Completions](https://openrouter.ai/docs/api-reference/chat-completions)
- [Image Generation Guide](https://openrouter.ai/docs/guides/overview/multimodal/image-generation)

## License

MIT
