---
title: "mapping additional drive to encrypted system"
date: 2012-04-01
forum: Security
---

### Post by sambhogi on 2012-04-01
(Reposting this here since I posted in the general forum with no luck.)

I encrypted my system drive using the whole disk encryption option on the 11.10 alternate install CD. I would now like to add a second drive, and have the system treat this drive space as part of the /home directory. I have seen guides on mapping the new drive to its own directory, but this is not what I want to do. I would like a logical volume spanning both the original drive and the new one under the /home directory. How do I set this up?

---

### Post by sambhogi on 2012-05-01
So I have mostly solved this. Starting with the standard LUKS+LVM setup created by the alternate install CD, I wanted to map a new drive to the LUKS+LVM root volume. 

I was able to do this as follows (I am working from memory, so the commands may not be exactly as I executed them, but at any rate, the commands I actually used all returned success messages):

sudo cryptsetup luksFormat /dev/sdb1
sudo cryptsetup luksOpen /dev/sdb1 sdb1_crypt
sudo pvcreate /dev/mapper/sdb1_crypt
sudo vgextend sambhogi-desktop /dev/mapper/sdb1_crypt
sudo lvextend -L sambhogi-desktop-root

I then shut down, booted from the live cd, and, following some of the steps in this howto ( [https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions) ), I resized the filesystem in logical volume sambhogi-desktop-root to fill the remaining space. 

When I attempted to reboot into the encrypted system, I was prompted for the sda5_crypt password as usual, however, this did not return a success message. After a minute or so I was dropped into an initramfs shell. I rebooted into the live CD, then edited /etc/crypttab on my system to add the new encrypted drive, /dev/sdb1. Still no luck booting into the encrypted system. However, when I boot into the liveCD I am able to mount the extended logical volume and it works fine. 

What am I missing here?

---

### Post by sambhogi on 2012-05-01
This thread seems to address the issue, but I am not sure where these parameters are set in Ubuntu:

[https://bbs.archlinux.org/viewtopic.php?pid=827495](https://bbs.archlinux.org/viewtopic.php?pid=827495)

---

### Post by sambhogi on 2012-05-02
Since I was able to boot into the alternate install's rescue shell, I fixed this problem. I executed the following commands, although I don't know if the first two were of any consequence, but I did them for good measure. I suspect these could have been done (using sudo) when I first enlarged the encrypted logical volume, and before booting into the LiveCD to resize the file system. At any rate, success. 

# vgscan --mknodes
# dmsetup mknodes
# update-initramfs -u

[Edited to add: I believe that /etc/crypttab must be edited to include the new device before running update-initramfs. Also, if you are doing this from the rescue disk, after decrypting the encrypted drives and mounting the logical volume (e.g. sambhogi-desktop-root) as root filesystem, you must manually mount /boot by doing, e.g., "mount /dev/sda1 /boot"]

---

### Post by sambhogi on 2012-05-02
Once I replicate this process trouble-free, I will write a HOWTO since I haven't been able to find a clear one anywhere.

---

### Post by beboylips on 2012-05-04
Looks interesting and like an issue that may pop up again so a HOWTO would be nice.

---

