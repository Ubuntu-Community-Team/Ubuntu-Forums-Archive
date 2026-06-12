---
title: "getting rid of windows 7 boot screen"
date: 2009-01-26
forum: Windows
---

### Post by Jackp90 on 2009-01-26
I installed windoze 7 for someone on a XP computer a while back.  After they decided that they didn't want it anymore I deleted the partition that I created with gparted and reallocated it for their XP partition.  However the 'dual boot' screen still appears with windows 7 set as the default OS even though the partition that it was on no longer exists.  I was wondering how to get rid of this screen and have boot in XP normally.  

After some research on the web I came accost the following info:

Open a command prompt and type C:\boot.ini to edit the boot options, and it should be fairly easy to edit the options if you have any experience with code.

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

Any help would be much appreciated.

---

### Post by markusf21 on 2009-01-27
if you have the xp cd handy. boot the cd and repair the install. at the prompt type fix mbr. that should take care of it

---

### Post by Jackp90 on 2009-02-03
> **markusf21 said:**
> if you have the xp cd handy. boot the cd and repair the install. at the prompt type fix mbr. that should take care of it

Unfortunately the command fixmbr did not work do you have any other suggestions?

---

### Post by djb6 on 2009-02-04
I would use Vista Boot Pro.  It works well, and seems to also work with XP.  It can be used to delete extra boot options.

---

### Post by Fzang on 2009-02-05
Sorry for all the mess, got it clear now

in cmd.exe, type

```
bcdedit.exe
```

It should list all your installed OS with partition, name, other stuff and an identifier, which is some huge number

Now, to remove windows 7, find the windows 7 identifier and then

```
bcdedit.exe /delete {long-ID-of-windows-7}
```

---

