---
title: "403 Forbidden on localhost with Apache"
date: 2011-04-23
forum: Server Platforms
---

### Post by RIPPL on 2011-04-23
This seems like it shouldn't be a difficult fix, but I did a good bit of research and testing, and was still unable to fix my problem.

I am running Apache2 on a computer that is partitioned to run a dual-boot of Ubuntu 10.10 and Windows 7. I have Apache installed on both operating systems. I have my web development projects in a directory on the D:\ partition. When I updated the document root in Windows to point to D:\Webs, everything worked fine. When I updated it in Ubuntu, however, it returns a 403 Forbidden when I try to access [http://localhost](http://localhost).

My document root in the Apache configuration file in Linux is set to /media/Data/Webs (equivalent to D:\Webs).

I've tried a number of different chmod fixes while restarting apache after each time, and none of them have worked for me.

I feel that the problem may come from the fact that my document root directory is set in a separate drive partition (if it isn't mounted, it displays a 404 error instead. Once mounted, it goes to a 403).

---

### Post by falko on 2011-04-23
How do you mount the partition? What's in /etc/fstab, and what's the output of ```
mount
```?

---

### Post by RIPPL on 2011-04-23
> **falko said:**
> How do you mount the partition? What's in /etc/fstab, and what's the output of ```
mount
```?

Well I just click on the drive "Data" in the file browser and it mounts the partition. Here is what is in /etc/fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=817d07fc-5afc-445d-a9a8-36c78bb45c9f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=efd09bbb-96e3-434d-8b51-b8691c56e182 none            swap    sw              0       0

```

---

### Post by fenderr357 on 2011-04-24
What are the permissions on /media/Data/Webs/? I think a quick fix may be to chown the folder to the www-data group, like this:

```
sudo chown Administrator:www-data /media/Data/Webs
```This should allow apache to access the dir (just replace Administrator with your username). This may not work, but in my experience 403 usually has something to do with permissions.

---

