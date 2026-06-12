---
title: "USB has renamed itself (Virus?)"
date: 2012-04-03
forum: Security
---

### Post by laresistance2 on 2012-04-03
Hello,

My USB key has renamed herself suddenly with the name _mail.com"_
I wonder the cause that could cause this renaming without my knowledge.
Is it a virus?

How to fix this?

Thank you.

---

### Post by CharlesA on 2012-04-04
Do you use it on a windows box? That sort of thing shouldn't randomly happen. You would have to rename it manually.

As for changing the label back, it depends on what file system is on that drive.

e2label works for ext2/3/4 drives. Not sure about NTFS drives tho.

---

### Post by 0011235813 on 2012-04-04
I don't know about renaming it, but Charles is right, if you used a Windows box, it's possible it might be infected... So let's scan it. Ubuntu comes pre-installed with an antivirus program called clamscan. It is a command-line scanner, use:
```
clamscan -R <location> 
```
in the terminal (Ctrl+Alt+T). So if your usb stick is named /media/usb1 put that instead of "location". You can check it's name by opening up nautilus and hovering over it (nautilus is the second icon at the side, called home). 

Alternatively, you can use a graphical program. Open up "Ubuntu Software Center" search for "virus" and click install. Enter your password when it asks you.

---

