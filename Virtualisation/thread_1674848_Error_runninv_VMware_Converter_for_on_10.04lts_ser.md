---
title: "Error runninv VMware Converter for on 10.04lts server"
date: 2011-01-24
forum: Virtualisation
---

### Post by jstn on 2011-01-24
hey everyone,

i'm trying to p2v a 10.04lts server to our vmware esxi server (4.0.0, build 208167) using vmware converter (4.3, build 292238), but at the last screen in converter it says "Unable to create virtual machine Server1". 

the source machine is running LVM and all the LVs are picked up by converter and seem to be recognized. the only thing i can tell is that sda1 was configured with an 'fd' (Linux raid autodetect) partition id. see below:

```
root@puffin:~# fdisk -l

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x17bd76d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60802   488392033+  fd  Linux raid autodetect

```

i was able to successfully p2v a test vm (debian lenny) using LVM, running in virtualbox from my laptop, without a problem.

the issue i am experiencing as the same exact problem that is reported here on the vmware forums:

[http://communities.vmware.com/message/1670718](http://communities.vmware.com/message/1670718)

has anyone else seen this before?

thanks,

justin

---

### Post by jstn on 2011-01-24
i should also add that for some reason this server was built with /boot on lvm. wasn't me! ;)

justin

---

