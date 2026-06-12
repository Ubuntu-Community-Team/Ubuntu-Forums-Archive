---
title: "Ubuntu Server 12.04, /dev/mdx constantly changes device number!"
date: 2012-11-02
forum: Server Platforms
---

### Post by razor7 on 2012-11-02
Hi, I'm facing a really annoying bug, I have set up a Software RAID1 with mdamd, and the setup went just ok with this results

> /dev/md/lucas.mgscreativa.com.ar:0

I have also configured mdadm.conf like this
> DEVICE /dev/sda /dev/sdb

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/lucas.mgscreativa.com.ar:0 metadata=1.2 name=lucas.mgscreativa.com.ar:0 UUID=c913486a:e62c7ea1:cfb98b6b:253d1f62


And fstab configured like this 
> /dev/md/lucas.mgscreativa.com.ar:0 /media/data     ext4 defaults,noatime      0       0


But, some day, my array name suddenly changed from /dev/md/lucas.mgscreativa.com.ar:0 to /dev/md0, so i have done some changes in fstab and mdadm.conf (of course, after hours and hours of tryal and error) and everything went just ok, but today, AGAIN, the MD number changed from /dev/md0 to /dev/md127!!!

What's going on here? is this a bug I guess.

Is there any way to fix the MD number so my server can work as it shhould, without flaws?

Thanks!

---

