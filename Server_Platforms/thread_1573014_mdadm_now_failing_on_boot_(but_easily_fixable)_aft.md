---
title: "mdadm now failing on boot (but easily fixable) after a hardy -&gt; lucid upgrade"
date: 2010-09-12
forum: Server Platforms
---

### Post by ph8 on 2010-09-12
Morning all,

Does anyone know a little about mdadm? 

When I boot I get /dev/md0 could not be configured, it drops to busybox. If I use the mdadm binary in busybox to reassemble my arrays manually (by uuid) and then simply exit, it works. So the array is fine it's just an issue with the boot process.

 While i'm in busybox, if I look at /etc/mdadm/mdadm.conf it's got all the directives twice, in two identical blocks. This isn't the mdadm.conf that i have on my machine so i'm guessing it's auto generated - does anyone know how i influence this auto generation process and get it fixed? I think this is what's stopping the boot. 

I'm running Lucid (just upgraded from Hardy which is when these problems started).

Many thanks,

Henri

---

### Post by ph8 on 2010-09-12
I've managed to fix this.

The 'boot time' mdadm.conf was not reflective of the copy I had at /etc/mdadm/mdadm.conf once the system was booted.

The boot time mdadm.conf is packaged in the initramfs

So to fix I just ran update-initramfs -u

This moved the mdadm from my system, into the 'boot time' area - propagating my changes and fixing the issue!

This is a problem that's developed during a Hardy -> Lucid upgrade though and I gather raid 'messing up' is something quite common.

---

