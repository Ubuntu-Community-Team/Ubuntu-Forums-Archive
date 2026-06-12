---
title: "Ubuntu 8.10 LVM + Software raid = boot problem"
date: 2009-04-14
forum: Server Platforms
---

### Post by straks on 2009-04-14
Hi,

Installed Ubuntu 8.10 server edition on a system yesterday. Configured the following partions:

Software Raid only
/dev/md0 as /boot, ext3

LVM over Software raid:
Volume group "main", over
/dev/md1 and /dev/md2
Logical volumes:
/dev/mapper/main-root as /, ext3 
/dev/mapper/main-tmp as /tmp, ext3 (nosuid, noexec)

Everything works fine, mdadm shows my raids to be in perfect working order. LVM is also working great.

Now, the problem i'm facing:
Whenever i boot, i get thrown in a busybox interactive shell with an error explaining it is unable to find my root device. If i just immediatly press CTRL-D (logout of the shell), it keeps booting as no problem exists, everything works great.

I've tried setting my root device in grub to the UUID and to /dev/mapper/main-root, both give me the interactive shell, and both boot perfect after exiting that shell...

So, server works, but it is really irritating i have to do the CTRL-D everytime it boots. That's not how it should be.

So, how can i fix this? 

Thanks!
Cheers

---

### Post by straks on 2009-04-14
Hmmz, fixed it myself apparently :p

For all facing the same problem, add this to your boot options:
rootdelay=180

(i've set it to 180 as a test, and i'm not going to tweak it now for now, but just test out what works best, i guess :))

---

