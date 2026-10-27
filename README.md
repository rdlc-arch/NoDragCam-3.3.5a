Claude (Anthropic) generated

# NoDragCam

A tiny World of Warcraft **3.3.5a (WotLK)** addon that stops the camera from rotating when you **left-click + drag** or **tap and hold on a touchscreen**.

Made for playing on handhelds (Lenovo Legion Go, Steam Deck, ROG Ally) and on Android emulators such as GameHub, where every tap is a left click and the slightest finger movement used to spin the camera.

## What still works

| Input | Camera |
|---|---|
| Left click / tap | ❌ no rotation, **click-to-target still works** |
| Left-drag / tap and hold | ❌ no rotation |
| Right-drag (mouselook) | ✅ normal |
| Left + right together (run and steer) | ✅ normal |
| **Move and Steer** keybind (keyboard or controller) | ✅ normal |
| Optional bypass modifier (Alt / Ctrl / Shift) | ✅ normal while held |

## Installation

1. Download the latest release (or **Code → Download ZIP**).
2. Extract it to `World of Warcraft\Interface\AddOns\`.
3. Make sure the folder is named exactly **`NoDragCam`** (rename `NoDragCam-main` if you downloaded from GitHub).
4. Restart the game or type `/reload`.

## Commands

| Command | What it does |
|---|---|
| `/ndc` | Toggle on/off |
| `/ndc on` / `/ndc off` | Enable / disable |
| `/ndc mod alt\|ctrl\|shift\|none` | Hold this key to rotate with left-drag normally |
| `/ndc status` | Show current and saved camera speeds |
| `/ndc debug` | Print button / mouselook / steer state on every change |
| `/ndc reset` | Restore default camera speeds (180 / 90) |

`/nodragcam` works too.

## How it works

The left-drag camera is handled by protected Blizzard code, so an addon can't simply turn it off without also breaking click-to-target. Instead, NoDragCam keeps the camera turn speeds (`cameraYawMoveSpeed` and `cameraPitchMoveSpeed`) at zero, or the lowest value your client accepts, **by default**. It switches your real speeds back on only while you are actually steering: right button held, Move and Steer active, or your bypass modifier held.

Keeping them low by default matters for touchscreens: a tap moves the cursor and presses the button in the same frame, which is too fast to react to.

Your original speeds are saved and restored when you log out or disable the addon. If the game closes unexpectedly, they're restored on the next login.

## Notes

- The **Mouse Look Speed** slider in Interface Options will appear to change on its own while the addon is active. That's expected. Change it with the addon off (`/ndc off`) if you want a different speed.
- If your camera ever feels stuck or slow after removing the addon, type `/console cameraYawMoveSpeed 180` and `/console cameraPitchMoveSpeed 90`.
- Tested on Warmane (3.3.5a) on Windows (Lenovo Legion Go) and Android (GameHub).

## Credits

Created by Radu.
Written with help from Claude (Anthropic's AI assistant). It doesn't include code from other addons; it only uses the game's standard interface functions.

## License

[MIT](LICENSE). Free to use, modify and share.
