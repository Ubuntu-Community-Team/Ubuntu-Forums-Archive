---
title: "Installing Windows 10 on DELL Inspiron 5558 when Ubuntu is pre-installed"
date: 2016-09-29
forum: Windows
---

### Post by 4imb0t on 2016-09-29
Hello world!
I bought a brand new DELL Inspiron 5558 i3-5005U/4GB/1000 without Windows, so Ubuntu was pre-installed. I want to install W10, but I don't know how, because:
1) There are two BIOS Boot option: Legacy and UEFI - which one to choose?
2) There is Ubuntu pre-installed and partitions are:
Partition 1: ESP, Total size: 500MB, Free space: 478MB, Type: System
Partition 2: DIAGS, Total size: 40MB, Free space: 35MB, Type: OEM (Reserved)
Partition 3: OS, Total size: 3GB, Free space: 885MB, Type: Primary
Partition 4: there were /ext4/ partition, but I unfortunately deleted it, so now there is Unallocated space: 920GB
Partition 5: SWAP, Total size: 7.8GB

I want to have ONLY W10, and nothing else. So, what do I have to do, step by step? Which partitions can I delete, and which must stay untouched?

Thanks in advance

---

### Post by howefield on 2016-09-29
Thread moved to the "*Windows*" forum.

---

### Post by westie457 on 2016-09-29
Welcome to the Forum.

Here is a link to possibly the best guide. [http://answers.microsoft.com/en-us/windows/wiki/windows_10-windows_install/clean-install-windows-10/1c426bdf-79b1-4d42-be93-17378d93e587](http://answers.microsoft.com/en-us/windows/wiki/windows_10-windows_install/clean-install-windows-10/1c426bdf-79b1-4d42-be93-17378d93e587)

Read through it. Only you know exactly which steps you will need to follow.

---

### Post by yancek on 2016-09-29
> I want to have ONLY W10, and nothing else. So, what do I have to do,  step by step? Which partitions can I delete, and which must stay  untouched?

If you want to overwrite Ubuntu and install windows 10, just do it.  I find it hard to believe you have a full install of Ubuntu on a 3GB partition as shown in your post?  If you have the windows iso on a DVD or on a flash drive, you should be able to just boot it and the installer will overwrite everything and install the system which is what you said you want.  If the link suggested above doesn't work for you, I would suggest you check a windows forum or the support.microsoft site.

---

