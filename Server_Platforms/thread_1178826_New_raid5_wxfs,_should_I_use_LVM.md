---
title: "New raid5 w/xfs, should I use LVM?"
date: 2009-06-04
forum: Server Platforms
---

### Post by littlegreiger on 2009-06-04
I'm going to be setting up a new software raid5 with 5x 1.5TB disks and I can't decide if I should be using LVM on it or not. I was going to just have it as a single partition, with XFS, and don't really need to be able to change partition sizes on the fly. Is there something I'm missing and I should be contemplating using LVM or should I just do without it and build the raid like usual?

Also does anyone have comments on using XFS on a partition this big (essentially 6TB).

---

### Post by PilotJLR on 2009-06-07
Although you could use both software RAID and LVM together, I personally wouldn't do this... given your stated needs, it's unnecessary complexity. Less to troubleshoot when/if things go south is a winner!

Since you can grow a RAID array and an XFS filesystem, I don't see how LVM would give you any functionality that you would need.

---

### Post by littlegreiger on 2009-06-07
That's kind of what I was thinking, however I'm starting to think about using LVM because I'll be migrating over an older RAID set and that will allow me to easily add the old RAID to the new one.

However I am having problems with mdadm in Jaunty, every time I try to create an array, which should be /dev/md1, it gets renamed to /dev/md_d1 or /dev/md1p1 gets created on reboot. Anyone have ideas?

FYI: This is with the newest mdadm which is version 2.6.7.1

---

### Post by grantemsley on 2009-06-08
the /dev/md1p1 thing is a partitionable array.  I haven't tested creating arrays in Jaunty, maybe they changed something to make that the default, since I've seen other people have that issue too.

You can use it just like /dev/md0

Recreating the array with "--auto=md" should fix that.

---

### Post by littlegreiger on 2009-06-08
I tried it with the --auto=md setting and that didn't work. The array gets built correctly when I run it, well it creates md1 and md1p1 which is good enough, but on reboot though it creates md_d1 and md_d1p1-p4. 

I created the config by running
```
mdadm --detail --scan --verbose > /etc/mdadm.conf
```

as root.
Is there maybe something I'm missing in creating the config because that's the way I've always done it before and I tested in 8.04 and it worked fine.

---

### Post by fjgaude on 2009-06-09
Where is your mdadm.conf file? Usually is /etc/mdadm/mdadm.conf. If so maybe you don't have the new file where it needs to be.

---

### Post by littlegreiger on 2009-06-09
I think I figured it out, the old mdadm used to read raid configs from /etc/mdadm.conf and now it only reads them from /etc/mdadm/mdadm.conf now.

Thanks guys!

---

### Post by fjgaude on 2009-06-10
Yes, many important changes have been occurring in mdadm, and most Linux OS stuff. Glad you found your problem. Let us know if you haven't. <smile>

---

### Post by littlegreiger on 2009-06-10
Yeah, everything worked as soon as I added the raid config to /etc/mdadm/mdadm.conf. I wouldn't have expected them to move the config file though.

---

### Post by wkulecz on 2009-06-10
> **littlegreiger said:**
> Yeah, everything worked as soon as I added the raid config to /etc/mdadm/mdadm.conf. I wouldn't have expected them to move the config file though.

What you don't think different is better?

These are the stupidest changes in computer science.  The first guy gets to decide where it should be and how it should be organized, then leave freaking well enough alone in future versions!

--wally.

---

### Post by littlegreiger on 2009-06-10
I actually think that the new file is in the correct spot, because in old versions you had /etc/mdadm/mdadm.conf which was the config file for mdadm settings and then you had /etc/mdadm.conf which just contained the raid sets. I'm sure you could probably put the raid sets in the /etc/mdadm/mdadm.conf in old versions but I haven't tested that.

---

### Post by cenwesi on 2009-06-12
I am also getting the md_d1 and md_d1p1-p4. So if i add **-auto=md** to the /etc/mdadm/mdadm.conf file will that get rid of it?

Also how do you guys deal with the sata drives device letters changing upon rebooting??? udev do not seem to be applying the rules correctly. Before rebuilding my system last night, drive sdb will point to sde or some other letter?

---

### Post by littlegreiger on 2009-06-12
Actually you have to use the --auto=md when you create the array.
Here's the command I used to create my array

```
sudo mdadm --create --auto=md --verbose /dev/md1 --level=5 --raid-devices=3 /dev/sd{b,c,d}
```
Then you need to add the raid config to the config file by running this command
```
sudo su
mdadm --detail --scan --verbose >> /etc/mdadm/mdadm.conf
```
you will be left logged in as root at this point so logoff that account now in case you forget to later.
Then you need to edit that config file and change metadata=00.90 to 0.90.

This is to create a raid5 array with 3 drives, /dev/sdb, /dev/sdc, and /dev/sdd. I haven't tried this on a physical machine, only on a virtual machine. However, I used a similar command to create my array on my physical server. 

As for the renaming sata devices I've never had that problem so I don't have any advice for you on that one.

If you have any other questions just post back.

---

