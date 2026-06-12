---
title: "Desktop frozen, mouse still moves after waking monitor from sleep"
date: 2020-07-18
forum: Ubuntu Development Version
---

### Post by accessd on 2020-07-18
Hi all,

This past week, after waking up my display in the morning after a period of inactivity, I find my desktop frozen (can't click anything, move windows, user the Super key or Alt-Tab), though the mouse still moves and I can kill the X server with Ctrl-Alt-Backspace and switch between terminals with Ctrl-Alt-FX. This just started happening after working perfectly for a long time, so I figure it was a result of a package upgrade, but I'm not sure which one. The Xorg.0.log file does not display anything relevant and journalctrl keeps logging the whole time and I'm not sure when in the middle of the night the freeze occurs, so I'm not sure what to look for. I tried switching to Wayland as I thought it might be an X Windows issue, but it put the display to sleep and I could not wake it by hitting any keys or moving the mouse and was forced to do a hard reboot (not sure if the problem is related as I've never used Wayland before).

I'm starting to think it's a Gnome issue but I have no idea how to diagnose it. I'm running Ubuntu 20.04. All the packages are up to date. The computer is running an Intel® Core™ i7-4790K CPU @ 4.00GHz × 8  CPU with a Radeon RX 560 Series (POLARIS11, DRM 3.35.0, 5.4.0-40-generic, LLVM 10.0.0) graphics card (using the open source drivers). Has anyone seen this issue or know how I might go about figuring out what is going on?

---

### Post by deadflowr on 2020-07-18
Duplicate thread
See other thread here: [https://ubuntuforums.org/showthread.php?t=2447428]("https://ubuntuforums.org/showthread.php?t=2447428")
This thread is Closed

---

