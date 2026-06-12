---
title: "Win10 raw &quot;partition&quot; in Linux VM"
date: 2018-06-30
forum: Windows
---

### Post by imWACC0 on 2018-06-30
I assume this is the right spot to post this. It's for windows 10.
This is sort of rambling because I found a few things on-line.

I need to dual boot my system, Lubuntu and Win10. But I want to run the install of Win10(sda1) in the VM of Lubuntu(sda2).
But the reading I get is that Win10 is harder to do with VM and may wipe the partition (Yes, I know to make an .img of sda1)

I found something, but I don't know how to translate it:
> ```
VBoxManage internalcommands createrawvmdk -filename /path/to/file.vmdk
      -rawdisk /dev/sda -partitions 1,5
```

This  example would create the image /path/to/file.vmdk (which, again, must  be absolute), and partitions 1 and 5 of /dev/sda would be made  accessible to the guest.
How do I say SDA1 instead of "1,5"? Do I just say "-partitions 1"?

I have C:\Program File as a Junction Link(NTFS/DOS) to sdc1(D:\Program File), do I need to make a VM disk for that also? If so, how do I link it to the Win10 VM?
Also, my page file is on sdb1(E:\).... Dose that matter?



P.S. I'm in the mid range with Linux (I know just enough to screw it up a lot).

---

