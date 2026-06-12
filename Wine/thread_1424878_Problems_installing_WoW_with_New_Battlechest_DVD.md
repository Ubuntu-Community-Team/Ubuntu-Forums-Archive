---
title: "Problems installing WoW with New Battlechest DVD"
date: 2010-03-08
forum: Wine
---

### Post by EndlessWaltz1026 on 2010-03-08
Hello,

I'm trying to install WoW under Wine (Latest Verson) using the new Battlechest DVD. It's the one that has Original and BC on one DVD. I was able to get past the Installer.exe module not found by doing this. 

Unmount the DVD with: sudo umount /media/cdrom0
Remount the DVD with: sudo mount -t udf -o ro,unhide,uid=(number) /dev/cdrom /media/cdrom0

But now I am having a different problem. I enter: wine Installer.exe and I get a dialog box with this error.

 "The folder "<temporary data>" could not be created."

I am not sure how to do to fix this.

I also tried to use the download installer but for some reason, I am unable to click the "Agree" to continue the installation. It is grayed out. 

If you guys have any tips to resolve either one of these problems, I would appreciate it. I just want to install the game, don't care which method. 

Oh using Ubuntu 9.10 64bit. 

Thanks!

---

### Post by Soulcage on 2010-03-09
What version of wine are you using? ```
wine --version
```
The 2nd problem I read is from people using 1.0.1 which is pretty old. Newest is 1.1.40

---

### Post by ginsong on 2010-04-05
I am having the exact same problem.

---

### Post by asdfoo on 2010-04-06
> **ginsong said:**
> I am having the exact same problem.

See the reply by Soulcage then.

---

### Post by ginsong on 2010-04-06
I am using a newer version that that.  :\  Thanks though.

---

