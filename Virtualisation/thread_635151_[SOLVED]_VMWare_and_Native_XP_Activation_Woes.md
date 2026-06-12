---
title: "[SOLVED] VMWare and Native XP Activation Woes"
date: 2007-12-08
forum: Virtualisation
---

### Post by lvleph on 2007-12-08
I followed the instructions for Native WinXp in VMWare. Everything worked without a hitch. However, one needs to have the two different hardware profiles to be able to run WinXp this way. Because the hardware changes from native boot to vmware, one has to activate their copy of Xp everytime one changes between the two.

I found a solution to this problem that relied on a script that would copy the two activation files (wpa.dbl and wpa.bak) from a specific folder depending on the type of windows session (native or vmware). This script was a windows script. Windows scripts only work in Professional, and I have Home, so obviously I cannot run a start up script.

My solution was to write a script that would run VMware, but before it runs VMWare it would copy the vmware Xp activation files to its proper location. On shutdown it would, then copy the native boot activation files back. However, I have run into an Input/Output Error during that copy process. I have no idea what the problem is.

```
echo "Moving wpa.dbl from /media/windows/WINDOWS/system32/vmware/wpa.* to /media/windows/WINDOWS/system32"

cp -f /media/windows/WINDOWS/system32/vmware/wpa.* /media/windows/WINDOWS/system32/

vmware

echo "Moving wpa.dbl from /media/windows/WINDOWS/system32/nativeboot/wpa.* to /media/windows/WINDOWS/system32"

cp -f /media/windows/WINDOWS/system32/nativeboot/wpa.* /media/windows/WINDOWS/system32/
```

Any ideas of what might be wrong? Oh, and the force option doesn't help.

---

### Post by lvleph on 2007-12-10
Well, it looks as though that partition is corrupt. I ran a chkdsk /r, but windows hangs on startup. I could just copy my other computers windows files over, but I think I am going to just see if I can get virtualization to work properly with an image.

---

