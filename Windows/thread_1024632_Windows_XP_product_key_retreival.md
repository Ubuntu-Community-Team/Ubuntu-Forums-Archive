---
title: "Windows XP product key retreival"
date: 2008-12-29
forum: Windows
---

### Post by xRes on 2008-12-29
hey all,
Can anyone explain how I would be able to retreive the Windows XP product key from my dual boot machine. Windows seems to be having mouse/keyboard driver issues so I can't use it but before I reinstall I wish to get the product key have currently through ubuntu if possible. Any ideas?

---

### Post by ikonia on 2008-12-29
boot windows into safe mode so it uses the generic drivers for your keyboard and mouse rather than any fancy ones you may have.

Lets be honest, this isn't really anything to do with ubuntu.

You should also have either the packet/sticky label with your product code on if it's genuine.

---

### Post by oilchangeguy on 2008-12-29
> **xRes said:**
> hey all,
Can anyone explain how I would be able to retreive the Windows XP product key from my dual boot machine. Windows seems to be having mouse/keyboard driver issues so I can't use it but before I reinstall I wish to get the product key have currently through ubuntu if possible. Any ideas?

does your computer have the product key sticker on it? or on the cd jacket? and you don't need to reinstall windows, just to fix the mouse and keyboard.

---

### Post by xRes on 2008-12-29
Thanks for your reply. The OEM sticker is no longer on the machine and I would like to use my current legal product key for the reinstall. It is to do with ubuntu though because i'm using it for data recovery. Safe mode isn't an option most likely due to conflicting drivers or a registry corruption (This is my friends machine). Ive run <code>chkdsk /r</code> in recovery console (Windows)and still no joy so now i'm looking to ubuntu for solutions.

---

### Post by kevdog on 2008-12-29
Perhaps this will help you:

[http://magicaljellybean.com/keyfinder/](http://magicaljellybean.com/keyfinder/)

---

### Post by xRes on 2008-12-29
Indeed it would, but unfortunately i'm unable to use my mouse or keyboard when in Windows and that tool is Windows only :(

---

### Post by kevdog on 2008-12-29
If you are dual booting can you run it in wine?

---

### Post by oilchangeguy on 2008-12-29
> **xRes said:**
> Thanks for your reply. The OEM sticker is no longer on the machine and I would like to use my current legal product key for the reinstall. It is to do with ubuntu though because i'm using it for data recovery. Safe mode isn't an option most likely due to conflicting drivers or a registry corruption (This is my friends machine). Ive run <code>chkdsk /r</code> in recovery console (Windows)and still no joy so now i'm looking to ubuntu for solutions.

i've never seen a computer where the keyboard and mouse would not work (unless they were broken). are these wireless, usb, or ps2?

---

### Post by xRes on 2008-12-29
Yes I should be able to run it in wine but my real windows hive is not held in wine drive so it will be looking in the wrong place

---

### Post by ajcham on 2008-12-29
> **xRes said:**
> Yes I should be able to run it in wine but my real windows hive is not held in wine drive so it will be looking in the wrong place

From the website:
[QUOTE=http://magicaljellybean.com/keyfinder]# Load Hive option - allows you to load the registry hive of another Windows installation. To use, put the hard drive in a working machine (must also be Windows 2000,XP or Vista) or use Windows PE (not tested, should work) and click Load Hive. Then point it to the dead Windows install. If you're using Windows Vista, Administrator rights are required for this feature. You may have to right click on the Keyfinder and run as Administrator.[/QUOTE]

---

### Post by xRes on 2008-12-29
Thank you, will give it a a go and will let you know!

---

### Post by hal8000 on 2008-12-29
If that doesnt work have a look at the following post:

[http://ubuntuforums.org/showthread.php?t=955950](http://ubuntuforums.org/showthread.php?t=955950)

You can edit the windows registry by downloading the MiTEc file onto your ubuntu partition:-

[http://www.soft411.com/company/MiTeC/MiTeC-Windows-Registry-File-Viewer.htm](http://www.soft411.com/company/MiTeC/MiTeC-Windows-Registry-File-Viewer.htm)

Once downloaded mount your windows partition as read-write (or read only if you dont want to make any changes, then run the MiTec program with wine.
You need to point it to the mount point, and then to the windows registry:
e.g.
/media/sda1/WINDOWS/system32/config/software

The software hive will have your prodct key open Microsoft\Windows\CurrentVersion and then use google to convert it from ProductID to ProductKey

Edit: Just tried this and it looks as though you cannot delete or edit any registry keys or folders. I have write permission but there appears to be no way to make any changes.

---

### Post by cabbiinc on 2008-12-30
> **xRes said:**
> Indeed it would, but unfortunately i'm unable to use my mouse or keyboard when in Windows and that tool is Windows only :(

You could try the ultimate boot CD for Windows to get your keyboard up and running. That would make everything else a lot more manageable. [http://www.majorgeeks.com/UBCD4Win_d5710.html](http://www.majorgeeks.com/UBCD4Win_d5710.html) 

I've never used it so can't say how well it works or if it will even help.

---

