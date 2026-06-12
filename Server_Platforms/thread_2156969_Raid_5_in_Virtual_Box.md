---
title: "Raid 5 in Virtual Box"
date: 2013-06-23
forum: Server Platforms
---

### Post by samkarpluk on 2013-06-23
Trying to get some experience setting up a raid 5 environment. Following along with the following guide: [http://www.tcpdump.com/kb/os/linux/linux-raid-how-to/intro.html](http://www.tcpdump.com/kb/os/linux/linux-raid-how-to/intro.html)

I get it working fine, everything looks good, /dev/md0 is created and running, but I haven't managed to have it survive a reboot. 

Every time I restart the vm there are array errors reported. 

```
The disk drive for /RAID5 is not ready yet or not present. 
Continue to wait, or Press S to skip mounting or M for manual recover.
```

When I boot up using the Skip option, raid is setup on **/dev/md127**.

I can easily bring /dev/md0 with the following two commands:

```

mdadm --stop /dev/md127
mdadm --assemble --scan

```
 
I have also tried setting the array UUID in the /etc/mdadm/mdadm.conf file to the UUID reported by mdadm --detail --scan for /dev/md0, no love.

```
ARRAY /dev/md0 level=raid5 metadata=1.2 num-devices=3 UUID=blahblah
```

Not sure if it's just a product of the virtualized environment or what....any suggestions appreciated.

Sam.

---

### Post by CharlesA on 2013-06-23
Are you mounting the array with the UUID or the device name in fstab?

Sounds like the device name, so try using the UUID:

```
sudo blkid -c /dev/null
```

---

### Post by samkarpluk on 2013-06-23
Thanks CharlesA.

I found a solution, but I'm not sure if it is "correct" by any stretch. This stuff is new to me.

I added the UUID to mdadm.conf, and then issued the following as found in this horrific thread: [https://bugzilla.redhat.com/show_bug.cgi?id=606481](https://bugzilla.redhat.com/show_bug.cgi?id=606481)

```
update-initramfs -u
```

In my case this worked. I don't know if this is a general solution or something that worked for me in the virtualized environment.

I did not /do not reference UUID in the fstab at this point. Raid does survive reboot at this point.

My purpose is to create a raid5 setup for a home server for file sharing, media streaming, and backups in a mixed home environment. I am working through the virtualized setup to gain familiarity before assembling the server and setting up the os.

---

### Post by steeldriver on 2013-06-23
I'm not a RAID expert but I think the update-initramfs is necessary *if your root filesystem is on the RAID array* - because otherwise the system is left in a catch-22 (can't boot until the array is assembled, but can't assemble the array until it's booted and it can read the config from /etc/mdadm/mdadm.conf) - the update-initramfs effectively writes the mdadm.conf into the initial ram image to bootstrap the array assembly

---

### Post by samkarpluk on 2013-06-24
> **steeldriver said:**
> I'm not a RAID expert but I think the update-initramfs is necessary *if your root filesystem is on the RAID array* - because otherwise the system is left in a catch-22 (can't boot until the array is assembled, but can't assemble the array until it's booted and it can read the config from /etc/mdadm/mdadm.conf) - the update-initramfs effectively writes the mdadm.conf into the initial ram image to bootstrap the array assembly

In my case I have installed the root file system on its own drive. When I set up my server this will be the case; raid on separate drives, OS on a drive.

---

