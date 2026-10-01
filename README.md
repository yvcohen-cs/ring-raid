# Ring Raid

A real-time room-code strategy game for 2–8 players. This is the first playable pass: gathering, raids, building, the Dispatch Hall, live map movement, scoring, and both win conditions work. The art and balance are ready for further polish.

## Project context

Created by Yuval Cohen through a Handshake project activity with AI-assisted development in ChatGPT. The project was iterated through user playtesting, including a Dispatch Hall purchase fix and shorter raid timing.

[Play the hosted game](https://ring-raid-party-2026.grassisspiky.chatgpt.site)

This repository contains the recovered local Node.js build. The hosted Sites version uses a separate deployment and may have hosting-specific changes.

## Run

1. Install Node.js 20 or newer.
2. Unzip this folder, open a terminal inside `ring-raid`, and run `npm start`.
3. Open **http://localhost:3000** on the computer running the server.
4. To join from another device on the same Wi-Fi, open `http://YOUR-COMPUTER-LAN-IP:3000`. Replace `YOUR-COMPUTER-LAN-IP` with the computer's local network address. Every player chooses a name; the host shares the room code shown in the game.

There are no npm dependencies or accounts. The server listens on all local network interfaces. Allow local connections through your computer's firewall if prompted. `localhost` on a phone refers to the phone, so use the computer's LAN address there.

For quick timer testing, set `MATCH_SECONDS=30` before starting the server (for example, `MATCH_SECONDS=30 npm start` on macOS/Linux). Default matches last 600 seconds.

## Rules in this build

- Each player starts with 8 wood and 7 stone. A gathering trip brings back 3 wood, 3 stone, or 1 crystal. Only one crew can be away initially.
- After the host starts, everyone sees a synchronized five-second countdown. The match timer begins when the countdown finishes.
- Gathering takes 5 seconds before Workshop bonuses, to a minimum of 2 seconds. Raids take 8 seconds before Workshop bonuses, to a minimum of 5 seconds. Each Workshop level cuts 1 second from either trip.
- A raid always departs, even if the target has none of the chosen resource. It takes up to 3 on arrival, which may be zero. A target can only be raided by the same attacker once per 20 seconds. Vault levels lower the raid limit to 2, then 1.
- Grove and Quarry produce their level in wood and stone every 20 seconds. Workshop levels shorten trips by a second each.
- Levels 1, 2, and 3 cost 4 wood + 3 stone; 6 wood + 5 stone + 1 crystal; and 8 wood + 7 stone + 3 crystals, respectively. Core levels score 2/5/9; other levels score 1/3/6.
- Dispatch Hall costs 10 wood, 9 stone, and 5 crystals, scores 4 points, and unlocks a second simultaneous crew.
- A player wins immediately upon reaching all five level-3 buildings and the Dispatch Hall (37 points). Otherwise highest points after 10 minutes wins, then most crystals, then most unspent resources; any remaining tie is shared.

The map shows an unlabeled snowy mountain with wood at the foothills, stone on its lower and middle slopes, and shining crystals at the summit. Raids circle around it while gathering carts head toward resource sites. The end panel unfolds gently over two seconds.

Match data is held in memory and resets when the server restarts. Rooms expire after six hours. This build is intended for trusted local playtesting and has no public hosting or player accounts.

## Updating from the first build

Stop the previous server, replace the old `ring-raid` folder with this one, and restart it. This resets any active match. All players should refresh their page after the restart.
