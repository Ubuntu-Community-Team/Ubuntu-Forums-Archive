---
title: "restore question tar and untar"
date: 2009-07-23
forum: Server Platforms
---

### Post by druca on 2009-07-23
Hi,

Just wanted to ask a few questions regarding restoring a linux server from a tar-ball.

I got all of the files from the root directory. Then I partitioned a hard disk on another computer, not the same way but valid nonetheless, and then untarred all of the files. 

If I changed some config files shouldn't it still boot? 



Thank you,
Dm

---

### Post by cdenley on 2009-07-23
> **druca said:**
> 
If I changed some config files shouldn't it still boot?


If you reinstalled grub to the boot sector. I think you can do it with a livecd. Mount your filesystem, then run
```

sudo grub-install --root-directory=/media/disk /dev/sda

```
Where /dev/sda is the boot drive, and /media/disk is the mount point for your filesystem. You will probably have to edit /etc/fstab to use the UUID of your new filesystem.

---

### Post by druca on 2009-07-24
I thank You kindly! 

That was great!!!! 

I also find a few of these links in case anyone else had this trouble

[http://ubuntuforums.org/showthread.php?t=504678](http://ubuntuforums.org/showthread.php?t=504678)


[http://www.cyberciti.biz/faq/error-devhdx-does-not-have-any-corresponding-bios-drive-and-solution/](http://www.cyberciti.biz/faq/error-devhdx-does-not-have-any-corresponding-bios-drive-and-solution/)

[http://www.cyberciti.biz/tips/restore-debian-linux-grub-boot-loader.html](http://www.cyberciti.biz/tips/restore-debian-linux-grub-boot-loader.html)

the last one is essentially the same thing as done in this forum already, instead they just chrooted the disk 

Thank you very much!

---

