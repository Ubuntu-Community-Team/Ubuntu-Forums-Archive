---
title: "error reading windows partition"
date: 2009-02-11
forum: Windows
---

### Post by doctorbighands on 2009-02-11
I'm trying to replace the hal.dll file in my Windows partition from inside Ubuntu. I get an I/O error, though, when trying to access /media/disk/WINDOWS (the equivalent to c:\windows).

```

user@dell-laptop:~$ cd /media/disk/WINDOWS
user@dell-laptop:/media/disk/WINDOWS$ ls
ls: reading directory .: Input/output error

```

When I try to navigate there in Nautilus, I double-click on the WINDOWS folder and get blank contents. Obviously that folder shouldn't be blank!

Does this mean my Windows installation is completely borked? Is there something I'm doing incorrectly to access that folder?

Any help is appreciated!

---

### Post by bodhi.zazen on 2009-02-11
How did you mount it and did you get any error messages ?

I assume you are doing this from Ubuntu because Windows is borked in some way ?

---

### Post by doctorbighands on 2009-02-11
> **bodhi.zazen said:**
> How did you mount it and did you get any error messages ?

I assume you are doing this from Ubuntu because Windows is borked in some way ?

Indeed, Windows is acting funny. It won't boot - I get a "hal.dll is missing or corrupt" message when I try. I attempted to use the Windows Recovery Console to fix this, but it gave me "Access Denied" messages when I tried to access the relevant folders on disk.

I mounted the partition by clicking on Places > Disk and entering a password. I can get into other relevant folders on the partition (e.g., Documents and Settings), but the WINDOWS folder comes up blank.

---

### Post by bodhi.zazen on 2009-02-11
Sounds like a pain. 

I am not familiar enough with Windows to offer much assistance, which is why I moved this thread to the windows section.

I am limited and can only suggest you copy / back up the data you need and re-install windows. I hope someone can offer you additional assistance.

---

### Post by doctorbighands on 2009-02-11
Well, I appreciate your help.

I was thinking I may have to reinstall anyway - this machine gave me a BSOD before it started telling me it couldn't boot. I think Windows completely messed itself up.

---

