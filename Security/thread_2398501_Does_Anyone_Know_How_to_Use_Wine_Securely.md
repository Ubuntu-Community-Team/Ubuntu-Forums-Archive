---
title: "Does Anyone Know How to Use Wine Securely?"
date: 2018-08-12
forum: Security
---

### Post by vampirefox2 on 2018-08-12
I switched over to Ubuntu and wanted to play some of my older Steam games such as Star Wars Battlefront 2 (2005) using Wine. I know Wine can cause security issues if not installed and used properly which will bother me since I take security really seriously. Does anyone know how I could do all of this properly? Thanks!

---

### Post by Perfect Storm on 2018-08-13
Moved to security.

---

### Post by kc1di on 2018-08-13
Hello vampirefox2 and welcome to Ubuntu,

I'm not sure there is any absolutely safe way to run windows programs on Linux.  As windows is inherently faulty in this area. But a couple options may be better.
1. Run windows in a Virtual box environment.  This allows you to separate the window install from the linux host somewhat. [this page]("vampirefox2") may be helpful. 
2. install playonlinux , available in the repository install from terminal with this command: ```
sudo apt install playonlinux
``` play on linux has the advantage of installing each program in a separate virtual file. which again separates the wine program somewhat from your linux install  once installed you install as many wine versions that you want some game/programs run better on older wine versions, some on newer.  You can read more about play on linux [here.]("https://ubuntuforums.org/newreply.php?do=postreply&t=2398501") 

All that being said, I've never run battlefront2 on wine so not sure it will work.  you can see what others have said about that on the wineHQ data base [here.]("https://appdb.winehq.org")

---

### Post by DuckHook on 2018-08-14
People tend to think of security as an on/off switch when it is instead very much a continuum. You can run apps on WINE reasonably safely if you follow these general guidelines:

[LIST=1]
[*]Never, ever, ever run WINE as root.
[*]Never, ever, ever run a Windows browser in WINE
[*]Don't run apps that you download from the Internet. This is harder than it sounds given the commercial Windows business model in which third party apps are hosted on their own websites.
[*]If it's only games that you already own and have run with no malware issues under Windows, then stick with those.
[*]Don't install mods or scripts or any other form of downloaded "goodies". These are often trojans masquerading as something innocent.
[*]As *kc1di* has already suggested, if it's a low-resource older game and you have good hardware, you are better off running it inside a Windows VM. *TheFu* (one of our resident security gurus) also recommends this approach, with the added suggestion of video passthrough for more graphically resource intensive apps (modern games). However, this is not a trivial setup.
[*]A further option is to run Windows on a separate partition only for games (or other Windows apps) and keep your Linux partition segregated only for your real (sensitive) work.
[/LIST]
It is important to note that you can't have additional functionality like WINE without creating more attack surface for bad actors. This is just a fact of life. But if you keep your WINE activity highly constrained to only very well known apps sourced from reliable media and don't do stupid risky things, then the possibility of getting compromised is quite small.

---

