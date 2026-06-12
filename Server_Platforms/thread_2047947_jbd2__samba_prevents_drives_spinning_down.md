---
title: "jbd2 / samba prevents drives spinning down"
date: 2012-08-25
forum: Server Platforms
---

### Post by jickerson on 2012-08-25
Hi, I just finished setting up a fresh 12.04 server installation to use as a file server. I installed samba but would like to us hdparm to spin down my raid array (ext4) when not in use. However, when I ran iotop, i found that jbd2 was writing to the array every 5 seconds or so preventing it from spinning down the disks.

Is there a way to prevent it from writing to the disk so often? I ran across a thread that suggested adding "noatime" to the fstab where the array is mounted, but after i did that iotop still shows it writing to the disk every few seconds.

I also saw that samba updates the cache very frequently, and to prevent the disks from spinning back up you should change the startup file to write to a tmpfs ramdisk instead. This suggestion was from this link: [http://info4admins.com/tips-to-spindown-your-hard-disk-in-debian-or-ubuntu/](http://info4admins.com/tips-to-spindown-your-hard-disk-in-debian-or-ubuntu/) But I can't seem to find the samba file in /etc/init.d/

Thank you for your help!

---

### Post by rubylaser on 2012-08-25
This [thread]("http://ubuntuforums.org/showthread.php?t=2014443&highlight=iostat") covers your issue.  Also, you'll want to insure you've setup SMART on your disks, and then [set it up properly ]("http://zackreed.me/articles/60-spin-down-idle-hard-disks")so that it too doesn't prevent spindown.

I hope that helps :)

---

### Post by jickerson on 2012-08-26
> **rubylaser said:**
> This [thread]("http://ubuntuforums.org/showthread.php?t=2014443&highlight=iostat") covers your issue.  Also, you'll want to insure you've setup SMART on your disks, and then [set it up properly ]("http://zackreed.me/articles/60-spin-down-idle-hard-disks")so that it too doesn't prevent spindown.

I hope that helps :)

Thanks! I had already configured SMART to not wake up spun down disks, but didn't know the formatting process for EXT 4 wasn't instantaneous. I posted on that thread too, but does anyone know how long the "format" should take? (I'm running 4 x 1TB drives)

---

