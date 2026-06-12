---
title: "I need advice: how to re-host an mdadm device from one server to another"
date: 2012-10-01
forum: Server Platforms
---

### Post by quintellarosa on 2012-10-01
Hi there.

I currently have a box with 5 Seagate 2TB mounted as RAID-5 using mdadm. It is working perfectly fine and I have all control over it. The computer is running a Pentium G620 and 8GB RAM, perfect for a fileserver, but not good for a virtual host, so I've bought a third generation i5, 16GB RAM and a new board. Now I want to migrate the original RAID from the running server (the running board) to the new server (the new board).

I need advice for doing that, because I can't risk losing all my data because of a wrong procedure.

Some info:


[LIST]
[*]I have a separate disk for the system (I don't need to boot from the RAID, for instance)
[/LIST]
 
[LIST]
[*]mdadm.conf
[/LIST]
          ```
# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts

# definitions of existing MD arrays

# This file was auto-generated on Sat, 31 Mar 2012 00:58:35 -0300
# by mkconf $Id$

DEVICE /dev/sda /dev/sdb /dev/sdc /dev/sdd /dev/sde
ARRAY /dev/md0 level=raid5 metadata=1.2 name=FileServer:0 devices=/dev/sda,/dev/sdb,/dev/sdc,/dev/sdd,/dev/sde UUID=16852ca4:db81ff76:c704b8b2:b6bd76c0
MAILADDR root
```

[LIST]
[*]fstab file:
[/LIST]
```
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=fd9e57c0-86ef-4336-a2c3-74a69a66b42c /               ext4    errors=remount-ro 0       1
/dev/md0  /media  ext4  defaults  0  0
/dev/sdg  /vmware  ext4  defaults  0  0
```
I've noticed that mdadm.conf seems to register the name of the server. I've changed it for the new server, from "FileServer" to "MainServer". I've also changed the IP (wich I doubt will change anything).




What I need are advices on how to proceed to do this migration. It doesn't seem to be difficult, but some advice is welcome. 



Thanks!

---

### Post by rubylaser on 2012-10-01
This is actually very easy and a totally safe procedure.  On the new host, you'll just need to install mdadm, and put the new disks in.  Once you've installed mdadm, you can just run this.

```
mdadm --assemble --scan
```

This should automatically find the mdadm info in the superblock on each disk, and then assemble the array.  If you want to be more thorough, you can explicitly tell it what disks to use.

```
mdadm --assemble /dev/md0 /dev/sd[abcd]
```

Once the array is running and shows up in cat /proc/mdstat, you'll want to create a new /etc/mdadm/mdadm.conf file like this.

```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR youruser@gmail.com" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

Create a mount point, and setup /etc/fstab and then update your initramfs like this.
```
update-initramfs -u
```

If you run into any snags or have any questions, please post back, I'll be happy to help you through this. Just as an FYI, the name, level  and device portion in your ARRAY line are completely unnecessary for mdadm to correctly assemble the array, it could be simplified to this and it will still assemble correctly.
```
ARRAY /dev/md0 metadata=1.2 UUID=16852ca4:db81ff76:c704b8b2:b6bd76c0
```

---

### Post by quintellarosa on 2012-10-02
Thank you, RubyLaser. That was a nice explanation.

I've installed mdadm before installing the disks. When I've started the server, for my complete surprise, mdadm did all work for me. Amazing.

mdadm is really working fine and it's a nice Linux feature. I recomend its use.

---

