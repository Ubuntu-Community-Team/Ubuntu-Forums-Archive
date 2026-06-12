---
title: "Automatic decrypt and boot LUKS partition from USB drive with keyfile"
date: 2013-10-10
forum: Security
---

### Post by Y8yxGhQ on 2013-10-10
Hello. First of all, I'm well aware of the fact that there are several posts regarding the use of dm-crypt and LUKS on these forums. However, none of them fit my specific setup. Here it is:  - Boot partition is on USB drive.  - GRUB is installed on USB drive.  - Keyfile is ALSO ON USB DRIVE, on the same partition as /boot on the USB drive.   - Encrypted filesystem is on hard drive.    I'd like to know how to set this up so my filesystem can automatically boot by reading the keyfile from the USB drive that it's booting from. I've read other guides on how to do this, but they focused on configurations with GRUB and /boot partition on the hard drive and only using the USB drive for the keyfile, so they took steps that are unnecessary for me, like adding the corresponding USB filesystem modules to initramfs, since the keyfile is already on the partition that should be enabled for read for the rest of the system to get unlocked and boot.  Thanks.

---

### Post by Y8yxGhQ on 2013-10-10
**Update:**   By following this post: [http://askubuntu.com/questions/59487/how-to-configure-lvm-luks-to-autodecrypt-partition](http://askubuntu.com/questions/59487/how-to-configure-lvm-luks-to-autodecrypt-partition) I was able to make some progress, but I haven't still been able to boot my system.    I edited my /etc/crypttab like so:   ```
sda1_crypt UUID=(...) /dev/disk/by-label/LABEL:/keyfile luks,keyscript=/lib/cryptsetup/scripts/passdev
```   "LABEL" being the label of the USB drive that also contains the /boot partition.  These are the messages I get at boot time:   ```
 Volume group "luks" not found   Skipping volume group luks   Unable to find LVM volume luks/xxxxxxxxx   **cryptsetup: sda1_crypt set up successfully**    Gave up waiting for root device. Common problems:   -Boot args (cat/proc/cmdline)   -Check rootdelay = (did the system wait long enough?)   -Check root = (did the system wait for the right device?)   -Missing modules (cat/proc/modules; ls /dev)   ALERT! /dev/mapper/luks-XXXXXXXXXXXXXXX does not exist. Dropping to a shell!  
```   So I'm guessing I need to find a way to make the luks LVM volume available at boot time.

---

### Post by djsephiroth on 2013-10-31
Did you do update-initramfs -u after editing /etc/crypttab? I recall having a similar issue when setting up Kali with LUKS; using the UUID instead of partition label + updating initramfs did the trick. Here's one of the threads that helped me get it working (I and the posters in the thread are using LVM on LUKS, but the issue was purely a LUKS one): [https://forums.kali.org/archive/index.php/t-5753.html](https://forums.kali.org/archive/index.php/t-5753.html)

---

