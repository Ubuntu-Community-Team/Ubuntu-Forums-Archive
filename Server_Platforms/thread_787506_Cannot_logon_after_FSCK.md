---
title: "Cannot logon after FSCK"
date: 2008-05-08
forum: Server Platforms
---

### Post by donwoodsnet on 2008-05-08
I'm using Server 7.10 with no desktop.
I had a corrupted root files system which couldn't be resolved locally. I booted off the CD in rescue mode and was able to fix the file system. Now the user database seems to have lost its mind. After the system boots I can't logon with any known user account. I tried the rescue disk again and when I try to type passwd I get a message stating "Authentication service cannot retrive authentication info". How do I fix this?

---

### Post by amohanty on 2008-05-09
Try booting in with a live CD. Then mount the root file system and check to see if the username still exists in the **/etc/passwd** file?

If not you can try the following:
(disclaimer: I have not tried this and this may not work)
I have assumed that your root drive is /dev/sda and you mounted it to /mnt/root via the live cd

sudo mkdir -p /mnt/root
sudo mount /dev/sda /mnt/root
chroot /mnt/root
useradd the_original_username
passwd the_original_username

then type exit and reboot.

If that does not work you may have to reinstall your root partition. I am hoping that you either:
a. backed up regularly OR
b. had /home on a separate partition.

HTH
AM

---

