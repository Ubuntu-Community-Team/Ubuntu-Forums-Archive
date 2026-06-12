---
title: "getting rid of windows 7 boot screen"
date: 2009-01-26
forum: Windows
---

### Post by Jackp90 on 2009-01-26
I installed windoze 7 for someone on a  XP computer a while back.  After they decided that they didn't want it anymore I deleted the partition that I created with gparted and reallocated it for their XP partition.  However the 'dual boot' screen still appears with windows 7 set as the default OS even though the partition that it was on no longer exsists.  I was wondering how to get rid of this screen and have boot in XP normally.  

After some research on the web I came acrost the followin info:

Open a command prompt and type C:\boot.ini to edit the boot options, and it shoud be fairly easy to edit the options if you have any expirence with code.

However I have the following code and no trace of a Windows 7 operating system in the boot.ini file:

```


;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /NOEXECUTE=OPTIN /FASTDETECT


```

Any help would be much appreciated

---

### Post by Battie on 2009-01-26
The comments in the file explain it.  Boot.ini is obsolete.

However, you should be able to do what you want easily by going to the Properties page and clicking on Advanced system settings.  Go to the startup and recovery button and uncheck Time to Display choices, and choose your default OS.

---

