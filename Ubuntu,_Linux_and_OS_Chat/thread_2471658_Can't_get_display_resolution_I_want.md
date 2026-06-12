---
title: "Can't get display resolution I want"
date: 2022-02-05
forum: Ubuntu, Linux and OS Chat
---

### Post by lalawawa on 2022-02-05
I'm an Ubuntu 20.04.3 LTS.
My graphics card is AMD Radeon(tm) vega 11 graphics
I have a dual monitor system, VGA landscape on the left, HDMI portrait on the right.
The right hand monitor has resolution going up to 1440x2560, but that resolution is not displayed when I try to change it in "Settings -> Displays".
The menu goes up to 4096x2160, so I figure the graphics card can handle 2560x1440, it's just not giving me the choice.

Looking at other discussion about setting resolution, the 'xandr' command is mentioned, but when I try it it's not found and I get told to
$ sudo apt install x11-server-utils
but when I try that install it says it already has the latest version and refuses to do anything and it still can't find 'xandr'.

---

### Post by yetimon_64 on 2022-02-06
> **lalawawa said:**
> ... and it still can't find '**xandr**'.

Maybe this is just a typo here but just in case it isn't; that command should be "**xrandr**".
Retry the command with "xrandr" if you were actually using "xandr" in the terminal.
Sorry but I can't really help much with your main issue, wait for other helpers to respond for your graphics issues.

Regards, yeti.

---

### Post by deadflowr on 2022-02-06
Duplicate thread
Other thread here: [https://ubuntuforums.org/showthread.php?t=2471662]("https://ubuntuforums.org/showthread.php?t=2471662")

This thread is closed

---

