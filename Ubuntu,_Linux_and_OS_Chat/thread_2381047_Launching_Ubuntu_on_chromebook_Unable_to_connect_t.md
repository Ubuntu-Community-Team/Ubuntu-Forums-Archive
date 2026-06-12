---
title: "Launching Ubuntu on chromebook:: Unable to connect to X server"
date: 2017-12-26
forum: Ubuntu, Linux and OS Chat
---

### Post by abettertomorrow on 2017-12-26
I am new to Chromebooks but I have used Ubuntu before alongside Windows. However, with my Chromebook I have been having an issue launching the desktop for Linux. I keep getting the same error saying the following.

[COLOR=#000000][FONT=Arial]Entering /mnt/stateful_partition/crouton/chroots/xenial...[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]/usr/bin/startxfce4: Starting X server[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial](EE) [/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Fatal server error:[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial](EE) Cannot move old log file "/tmp/Xorg.crouton.1.log" to "/tmp/Xorg.crouton.1.log.old"[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial](EE) [/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial](EE) [/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Please consult the The X.Org Foundation support [/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]         at [http://wiki.x.org](http://wiki.x.org)[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial] for help. [/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial](EE) [/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]/usr/bin/xinit: giving up[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]/usr/bin/xinit: unable to connect to X server: Connection refused[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]/usr/bin/xinit: server error[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Unmounting /mnt/stateful_partition/crouton/chroots/xenial...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
If anyone can find a fix for this please help me.[/FONT][/COLOR]

---

### Post by TheFu on 2017-12-28
This is a crouton question, not Ubuntu.  Generally, crouton fails whenever Google pushes an update, then we have to wait a few days/week for the crouton libraries to be rebuilt to match the new google stuff.  Update your crouton script and installation, then try again. See of that fixes it.  If not, wait a few days and try again.

If you are tired of having to deal with google's unwanted updates and need more control over your chromebook OS, then many of them can run Linux nicely.  Some models are easy and others are very difficult while others are next to impossible.  I've booted directly into Linux on an Acer C720 and I'm currently typing this on a Toshiba CB35-C3350 (Gandof core i3) chromebook.  I needed control over kernel modules, which chromeOS doesn't allow, so had to flush that OS.  If you are really industrious, you can install both Chromium-OS and some Linux onto the same chromebook. It isn't hard, just non-trivial.  I had it working a few months ago (needed for some international travel), but have since wiped the chromium-OS partitions.

Hopefully, this all makes sense.

---

