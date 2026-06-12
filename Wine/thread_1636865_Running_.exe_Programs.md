---
title: "Running .exe Programs"
date: 2010-12-03
forum: Wine
---

### Post by Pressondude on 2010-12-03
I'm trying to install my LEGAL copy of Battlefield 1942 from the disks that I have. In a previous Ubuntu install (a few years ago) I was able to accomplish this easily. I have now run into a problem. I can't execute the install program from the disk because I haven't changed the execution bit for it. I can't change the execution bit for it because it's read-only media (a CD). What do I do?

---

### Post by gyussz on 2010-12-03
Have you tried running it from terminal?
```
wine *something.exe*
```
Should work fine

Edit: Other thing I could imagine: copy the content of the disk to your hard drive, then you'll be able to modify things

---

### Post by Pressondude on 2010-12-03
Thanks man. I'm not really sure why that works, if it's locked in the GUI it should be in terminal too...

---

