---
title: "Server: boots into x terminal as root"
date: 2013-12-04
forum: Server Platforms
---

### Post by diskmaster23 on 2013-12-04
I recently did a fresh install of ubuntu server 12.04 LTS, in the process I had to install X and xubuntu-desktop. When I installed these items, it seem to have displaced the usual command line login. I used to have getty sessions, but no more. What is really bothering me is the fact that it boots into a gui like terminal session while logged into root. It looks like a black desktop with a white box where the terminal session is. I had xubuntu-desktop and lightdm installed, but I removed it thinking it would get rid of this gui session, but it did not.

Does this terminal gui session exist because I don't have any getty sessions available for it? How can I fix this? Do you need more information? 

I would like to have it just boot into a terminal session as a non-gui (non-x session).

Please let me know.

Thanks!

PS. A separate issue is that I get a blank screen after the grub screen. I'd like to be able to see the bootup process to diagnose any problems that come up. I've tried changing the etc/default/grub settings to look like this GRUB_CMDLINE_LINUX_DEFAULT="text", ran sudo update-grub, but I still get a blank screen after grub until the login screen. Suggestions?

---

