---
title: "ubuntu 22.04 installer crashes with nvme's because of mdadm"
date: 2024-06-14
forum: Server Platforms
---

### Post by destroyer0701 on 2024-06-14
Hi all, first post so please be gentle.
I am installing the server iso for 22.04.3 onto a machine with a Samsung nvme ssd (1TB). 
Now, after going through the installer and "using the whole drive" i get an error that something went wrong...
i looked into the crash log and it says something along the lines of:
```
mdadm: No arrays found in config file or automatically
...
Detected Multipaath support
DM multipath kernel driver not loaded
... 
unexpected error while running command
multipath -r
Installation failed
```

Is this a driver issue? if so how do i fix it? 
thanks

---

### Post by darkod on 2024-06-14
I think the mdadm message is just that it didn't find any arrays, which is normal if you don't have any.

Not sure what the error might be. One thing that comes to my mind is if using EFI boot and not preparing the disk in advance, not sure if the installer can prepare the EFI partition etc.

I have always prepared my disks in advance, to have full control how the partitions end up.

---

### Post by volkswagner on 2024-06-15
Check your BIOS settings for the drive mode like (RAID vs AHCI).

Also like darkod mentioned, look at EFI settings and perhaps try
turning off secure boot.

---

