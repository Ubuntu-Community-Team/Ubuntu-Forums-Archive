---
title: "install virtualbox on separate hdd"
date: 2009-06-17
forum: Virtualisation
---

### Post by ghostandmachine on 2009-06-17
so I've been looking around on the forums and I can't seem to find a straight forward answer.

I have a blank hdd that I want to install windows xp thru virtualbox on it.

1. What do I format the blank hdd as? ext3, ntfs?

2. Is it easier to just install the image on my host hdd (ubuntu) then move it to the blank hdd? Or is there a way to install it to the blank hdd right off the bat?

any links, suggestions, etc, is much appreciated.

thanks in advance.

---

### Post by leef on 2009-06-18
> **ghostandmachine said:**
> 
any links, suggestions, etc, is much appreciated.


Take a look at this post;

[http://ubuntuforums.org/showthread.php?t=664692](http://ubuntuforums.org/showthread.php?t=664692)

looks to me like you could issue a command similar to this;

```
VBoxManage internalcommands createrawvmdk -filename /home/dmccall/Documents/VirtualBox/WindowsVista_PhysicalPartition/sda.vdmk -rawdisk /dev/sda -register
```

select sda.vdmk as the drive during VM setup and let the xp setup wizard create the filesystem. I haven't had this sort of setup so I could be wrong.

---

