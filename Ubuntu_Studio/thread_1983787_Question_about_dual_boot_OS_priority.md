---
title: "Question about dual boot OS priority"
date: 2012-05-20
forum: Ubuntu Studio
---

### Post by UbuNubi on 2012-05-20
I dual boot with Windows 7 and Ubuntu. I had Win 7 installed first.  However, by default when my computer boots up to the screen that gives  the choice of operating systems, if no choice is made it automatically  goes into Ubuntu. I was wondering how I can change that. I would like  for it to boot into Windows 7 by default.

---

### Post by jejeman on 2012-05-20
You need to change that settings in GRUB.
In file /etc/default/grub there is a line
GRUB_DEFAULT=0
change it to number of line on which win7 is. Or copy/paste the whole menuentry in quotes.
After that update grub.

---

### Post by oldfred on 2012-05-20
Another way and some more info on jejeman suggestion which works just fine if you want to edit grub.
gksudo gedit /etc/default/grub
Then do:
sudo update-grub

HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

drs305 wrote a Grub 2 Tweaks guide but it's pretty geeky stuff. If you are interested in editing the Grub2 scripts to rename a title, see Section 7 of the "Tweaks" link 
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
Grub 2 Title Tweaks-drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by UbuNubi on 2012-05-22
Thanks guys. I don't know much at all about Ubuntu, but I'll try to research this grub thing further and implement your suggestions.

---

