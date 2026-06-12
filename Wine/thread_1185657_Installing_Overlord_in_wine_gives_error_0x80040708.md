---
title: "Installing Overlord in wine gives error 0x80040708."
date: 2009-06-12
forum: Wine
---

### Post by blckpythn on 2009-06-12
Hi, everytime I try to install Overlord in wine, Installshield gives me error number 0x80040708.
I googled it, and it seems to have something to do with user permissions, I don't know how to change these in wine, and I thought that all permissions were granted anyhow.
Anyone have a fix or workaround?:(

The Overlord .iso is mounted

---

### Post by cogadh on 2009-06-13
The game barely works in Wine anyway, you might not want to waste your time with it:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=5344](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5344)

However, if you want to keep trying, I would suggest you copy the contents of the ISO to a directory and run the install from there, that seems to be the only way to get the install to run.

If that still produces the same error message, then try running the install from the terminal and posting the output here. Wine's own error messages may shed some light on the issue.

---

### Post by blckpythn on 2009-06-13
> **cogadh said:**
> The game barely works in Wine anyway, you might not want to waste your time with it:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=5344](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5344)

However, if you want to keep trying, I would suggest you copy the contents of the ISO to a directory and run the install from there, that seems to be the only way to get the install to run.

If that still produces the same error message, then try running the install from the terminal and posting the output here. Wine's own error messages may shed some light on the issue.


Alright, here, is exactly what I got from the terminal.


```
matthew@matthew-desktop:~$ cd /home/matthew/Desktop/Overlord/Overlordwcrack
matthew@matthew-desktop:~/Desktop/Overlord/Overlordwcrack$ wine Launcher.exe
matthew@matthew-desktop:~/Desktop/Overlord/Overlordwcrack$ fixme:storage:StgCreateDocfile Storage share mode not implemented.
err:ole:get_unmarshaler_from_stream Failed to read common OBJREF header, 0x00000000
fixme:reg:GetNativeSystemInfo (0x331a8c) using GetSystemInfo()

```

---

