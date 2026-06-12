---
title: "Server - Move data from NTFS drive"
date: 2010-02-05
forum: Server Platforms
---

### Post by flagators on 2010-02-05
I have installed the server edition.  I want to create a file server to save our pics and music in one place.  I also want to learn.  I am trying to find the best way to do this.  I have 2 harddrives.  One has server installed and the other one has my data on it.  My data drive is formatted as ntfs.  I want to move the data from the ntfs drive to the other drive so I can format the ntfs drive to the ext3 format.  What is the best way to do this?  ftp?

Sorry if this is a newbie question but I just started using ubuntu about 6 months ago.  I have also converted my wife and mother in law to ubuntu.

Thanks
Shannon

---

### Post by KiLaHuRtZ on 2010-02-06
```
sudo apt-get install ntfs-3g
sudo reboot
sudo mount -t ntfs /dev/[NTFS PARTITION] /mnt
sudo rsync -avn --progress /mnt/src/dir/ /some/dst/dir/ #### This runs a test first.
sudo rsync -av --progress /mnt/src/dir/ /some/dst/dir/
sudo umount /mnt
```

---

### Post by Zack McCool on 2010-02-06
What he said, except I wouldn't generally recommend mounting directly to /mnt.

Instead, do a sudo mkdir /mnt/ntfs and mount to that.  The other way won't break your system, but /mnt is a starting place for mounts, much like /media.

---

### Post by flagators on 2010-02-08
Thanks everyone.  It worked perfectly.

---

### Post by flagators on 2010-02-11
I did everything listed above and then I formatted the harddrive as ext4.  I copied everything over it was working fine.  Now when I mount the drive my folders are gone and I get a bunch of folders I didn't have before.

cdrom  debootstrap  etc  lost+found  media  var

Can anyone help?

Thanks
Shannon

---

