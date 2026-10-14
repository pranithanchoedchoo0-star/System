# Solo System Floating UI

A retro, monochrome RPG status panel for SillyTavern. The interface opens as a draggable floating window over the chat instead of being inserted into a chat message.

## Features
- Floating `SYSTEM` launcher in the chat page
- Draggable and resizable panel with STATS, EQUIP, SKILL, ITEM, and QUEST tabs
- Clickable entries open a detail overlay
- Attempts to sync data from the latest chat messages
- No server plugin or third-party JavaScript dependency required

## Install from GitHub
1. Push this folder to a GitHub repository.
2. In SillyTavern, open **Extensions → Download Extensions & Assets → Install Extension**.
3. Paste the repository URL, for example `https://github.com/your-name/solo-system-ui`.
4. Enable **Solo System Floating UI** and reload SillyTavern if prompted.

For manual installation, place the folder in `data/<user-handle>/extensions/solo-system-ui/` (user-scoped) or the appropriate third-party extension directory for your installation.

## Supplying system data
The extension scans recent chat messages for a JSON object. You can provide it in a fenced JSON block or wrap it in `<system_data>...</system_data>`:

```json
{
  "level": 12,
  "exp": "340/500",
  "job": "Shadow Hunter",
  "title": "The Awakened",
  "hp": "850/1000",
  "mp": "240/300",
  "sp": "75/100",
  "str": 28,
  "agi": 35,
  "vit": 20,
  "int": 18,
  "per": 24,
  "cha": 12,
  "equipment": {
    "head": [{"name":"Hunter Hood", "stat":"AGI +3", "desc":"A lightweight hood."}],
    "chest": {"name":"Shadow Coat", "stat":"VIT +2"},
    "gloves": [], "pants": [], "shoes": [], "weapon": {"name":"Night Fang", "stat":"STR +8"}
  },
  "skills": {
    "passive": [{"name":"Keen Senses", "level": 2, "desc":"Improves perception."}],
    "active": [{"name":"Shadow Step", "level": 1, "exp":"0%", "desc":"Move through the shadows."}],
    "ultimate": [{"name":"Nightfall", "desc":"A powerful finishing move."}]
  },
  "inventory": [{"name":"Health Potion", "amount": 3, "desc":"Restores health."}],
  "quests": [{"name":"Clear the Ruins", "timer":"02:30:00", "goals":[{"name":"Defeat monsters","progress":"4/10","done":false}], "reward":"500 EXP"}]
}
```

Open the floating window and press the refresh icon to scan chat history again. If your roleplay prompt uses a different data format, adjust it to emit a JSON object with the keys above.

## Repository files
- `manifest.json` — SillyTavern extension metadata
- `index.js` — UI creation, interaction, and chat-data parsing
- `style.css` — floating window styling

## License
MIT
