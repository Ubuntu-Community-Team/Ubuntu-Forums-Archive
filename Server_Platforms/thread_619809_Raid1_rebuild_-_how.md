---
title: "Raid1 rebuild - how?"
date: 2007-11-21
forum: Server Platforms
---

### Post by Matakoo on 2007-11-21
Okay, first off...I'm a newbie when it comes to Linux software raid. That being said, I have my home-server set-up with RAID1 for the system.

It's using two 40-gig drives, using different IDE-channels and set up as this:

md0 /boot
md1 /
md2 /usr
md3 /opt
md4 /var

Now, however, one of the disks have died and I need to replace it.

What would be a proper way of doing so? I need to partition the new drive the same way for sure, but after that?

How do I make sure that the system know that hda1 on the functioning drive should "connect" to the new hdc1 to form md0? Or will the system take care of that automatically as long as the new drive has the same partition layout and same device-node number (i.e. it is still hdc)?

Thankful for any advice!

---

### Post by psusi on 2007-11-26
You use mdadm to remove the failed device from the raid set, and add the new device to it.

---

### Post by doogy2004 on 2007-11-26
> **Matakoo said:**
> Okay, first off...I'm a newbie when it comes to Linux software raid. That being said, I have my home-server set-up with RAID1 for the system.

It's using two 40-gig drives, using different IDE-channels and set up as this:

md0 /boot
md1 /
md2 /usr
md3 /opt
md4 /var

Now, however, one of the disks have died and I need to replace it.

What would be a proper way of doing so? I need to partition the new drive the same way for sure, but after that?

How do I make sure that the system know that hda1 on the functioning drive should "connect" to the new hdc1 to form md0? Or will the system take care of that automatically as long as the new drive has the same partition layout and same device-node number (i.e. it is still hdc)?

Thankful for any advice!

[http://www.gagme.com/greg/linux/raid-lvm.php](http://www.gagme.com/greg/linux/raid-lvm.php) - here is a great thorough article going step by step setting up a RAID as well as recovering one.

---

