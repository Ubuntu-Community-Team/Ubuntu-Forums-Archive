---
title: "Access FAT32 partition with VMWare Server XP install?"
date: 2008-08-04
forum: Virtualisation
---

### Post by scotters on 2008-08-04
Have a FAT32 partition on my Ubuntu laptop for shared access with XP VM...sda4 in my case.

Tried adding as a HD to the VM, but get permission denied errors? How to do....?

---

### Post by KatBuntu on 2008-08-04
Try to make a samba share between your Windows VM and your Linux host, you only have to mount your FAT32 HD somewere in your ubuntu, and share (samba) it with your windows.

You can add the share as a network disk in windows, in a cmd prompt:
```
net use <LABEL>: \\SERVER\SHARE
```

If you have problems with samba referent to permissions, check your samba configuration, and the HDD permissions. Add the user vmware to samba group.

---

### Post by scotters on 2008-08-04
:) Hadn't even thought of networking...geez.  Thanks!

---

