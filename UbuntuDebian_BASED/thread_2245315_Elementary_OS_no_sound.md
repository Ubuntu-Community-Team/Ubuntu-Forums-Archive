---
title: "Elementary OS no sound"
date: 2014-09-22
forum: Ubuntu/Debian BASED
---

### Post by shakuganxxii on 2014-09-22
I have a Sony Viao and the sound does not work
$ lspci | grep audio
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)

---

### Post by oldfred on 2014-09-23
Moved to other OS since not Ubuntu.

Only other info I saved on sound was a Lenovo using Ubuntu.

 Lenovo Ideapad z585 Precise Installed wifi OK Dual Boot Win 7 no Sound SOLVED - other issues
[http://ubuntuforums.org/showthread.php?t=2170099](http://ubuntuforums.org/showthread.php?t=2170099)

---

### Post by Stinger on 2014-09-24
Hi shakuganxxii
Welcome to the Ubuntu forums.
Are you running elementary OS Luna or Freya ?
I can see you have two sound cards, did you try to switch them in 'switchboard' the control center of elementary ?
It seems like the HDMI audio controller is nr.1 and not the FCH Azalia Controller ?
Found this too:
[No audio devices - Kubuntu 13.04]("http://ubuntuforums.org/showthread.php?t=2158883") , seems that a newer kernel is needed ( 3.9 or above ).

---

### Post by Sasha_Aderolop on 2014-10-03
If it's an intermittent fault it's possible your sound card has a fault. If it's under warranty take it back to where you bought it from and let them sort it out.

---

