---
title: "Post your working xorg.conf here"
date: 2008-11-01
forum: The Cafe
---

### Post by forger on 2008-11-01
- Some developers might find this topic interesting, could help them in developing a good tool for monitor/graphics adapter and xorg.conf setup!
- I call the community to post their **working xorg.conf**
- Please don't include or whine for unworking solutions, please keep it clean, maybe your configuration does not work, but others reading this might find it useful! :)
- And please don't ask for help here, use the link or quote it, but **make your own topic in Help forums to seek help**!

Instructions:
(A) Attach the file
> /etc/X11/xorg.conf
(New Reply > Scroll down > click Manage attachments > Browse and upload, then close)

Zip the file in order to get it uploaded:
```
echo "You are in: $PWD"
zip xorg.conf.zip /etc/X11/xorg.conf
```

*OR*

For lazy persons, post it within the reply
```
cat /etc/X11/xorg.conf
```
Post it **after the questions**, and use [QUOTE] tags to quote it :)

(B) Answer these simple questions:
[LIST=1]
[*] What is your graphics card brand/model?
For the graphics card, use the command: ```
lspci -nn
```
..then find your graphics card and post the output of that line here (**not all the lines**, keep it clean!)
[*] What is your monitor brand/model?
[*] Did System > Administration > Hardware drivers (aka jockeygtk) setup everything for you regarding graphics card/monitor properly? [Yes/No]
[*] Did you have a problem with your monitor or graphics card?
[*] If you had a problem configuring it, did you use other packages/commands to configure it properly? [Yes/No]
List them here!
[*] Any hacks (additional editing) required to be done on xorg.conf? [Yes/No]
(Explain if the notes below!)
[*] Optional: Notes (if any)?
[/LIST]

---

### Post by billgoldberg on 2008-11-01
Strange, xorg won't open from the command line interface.

And I'm to lazy to use nautilus to track it down. (read hangover)

Maybe I'll post it later.

---

### Post by forger on 2008-11-01
[LIST=1]
[*] What is your graphics card brand/model?
01:00.0 VGA compatible controller [0300]: nVidia Corporation G70 [GeForce 7300 GT] [10de:0393] (rev a1)
[*] What is your monitor brand/model?
Samsung SyncMaster 793S 17" CRT Monitor
[*] Did System > Administration > Hardware drivers (aka jockeygtk) setup everything for you regarding graphics card/monitor properly? [Yes/No]
Yes
[*] Did you have a problem with your monitor or graphics card?
Yes, default resolution
[*] If you had a problem configuring it, did you use other packages/commands to configure it properly? [Yes/No]
nvidia-settings
[*] Any hacks (additional editing) required to be done on xorg.conf? [Yes/No]
No
(Explain if the notes below!)
[*] Optional: Notes (if any)?
- nvidia-settings requires nvidia driver to be enabled in xorg.conf first.
- I used
```
gksu nvidia-settings
```
and set up my resolution at "X server display configuration" section.
[/LIST]

---

