---
title: "Failure to decrypt luks partition prevents OS boot"
date: 2017-12-14
forum: Security
---

### Post by Mamoth on 2017-12-14
Hello.

I have a Xubuntu 16.04 install in a virtual machine.
It basically has three partitions : the '/' root with the OS itself, a swap partition and luks-crypted data partition that is mounted.

The password for the crypted partition is stored in a root file placed somewhere in the uncrypted partition (for the moment, until I can make something better).
I tested deleting this file to check the behaviour of the system. I expected it could boot but that the crypted partition would be unavailable. That is the behaviour I want.

It behaved differently to my surprise : the system got stuck during boot at a splash screen demanding the user to enter manually the crypted partition's passphrase.

The fstab line is 
```
/dev/mapper/sda3_crypt    /mnt/mountLuksData/    ext4    defaults    0    2
```
The crypttab line is 
```
sda3_crypt /dev/sda3 /some/path/to/the/file/containing/the/passphrase luks
```

How can I work this out ?

Should I change the fstab line by putting the fsck byte (the '2' at the end of line) to 0 to skip checking, or replace the 'defaults' option to something else ?

---

### Post by TheFu on 2017-12-29
It appears you aren't using partitions. Rather, you are using LVM and logical volumes.  For many reasons, this is probably best.

Anyway, if you will post the output from **lsblk**, then we will be able to see the layout and confirm at which level the LUKS encryption container is.

---

