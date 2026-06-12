---
title: "LUKS encryption on a restored virtual machine"
date: 2017-11-15
forum: Security
---

### Post by dave_f2 on 2017-11-15
Hi, I'm running into an issue where I'm not able to decrypt my LUKS-encrypted partition on a restored virtual machine. I believe the issue is that my disk's UUID changed and I'm unable to specify correct UUID for LUKS to decrypt. I'm able to get into single-user mode, but I'm assuming I only have a partial list of unencrypted programs that are needed to boot the OS to the decryption prompt. Any suggestions?

---

### Post by TheFu on 2017-11-15
I don't think that LUKS cares about the UUID.  Whenever I manually mount any LUKS stuff, the UUID is never entered.  
So ... if you can post exactly what you have tried, then we might be able to help.

Here are my steps:
```
 sudo cryptsetup luksOpen /dev/sdf5 c720
 sudo mkdir /mnt/root /mnt/Stuff
 sudo mount /dev/mapper/c720--vg-lv--Stuff /mnt/Stuff
 sudo mount /dev/mapper/c720--vg-root /mnt/root
```

sdf5 is the encrypted partition.
c720 is the LUKS name.
The mapper.... stuff is the LVM LVs to be mounted. The mount points (directories) must pre-exist.

If the machine hasn't seen the VGs before, a **vgscan** might be necessary after the luksOpen.  And if the LVs/VGs have the same names as any that exist on the current machine, then you'll need (must) rename them.

---

### Post by dave_f2 on 2017-11-16
Hi TheFu,

Thanks for the reply. I found out the issue was due to corruption during the restore process, so nothing will work anyway. Oddly enough, I can unlock the encrypted store, but when I go to mount the internal partition, I encounter errors.

---

