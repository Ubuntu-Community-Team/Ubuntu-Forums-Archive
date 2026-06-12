---
title: "Assembling RAID5 from LiveCD"
date: 2010-05-24
forum: Server Platforms
---

### Post by cadriel on 2010-05-24
Hi All,

I have a system running OpenFiler. System is on one disk, data is on a RAID5 set consisting of 4 other disks.

I'd like to boot in via the LiveCD - and mount / assemble the RAID array from CLI in order to make sure I can read my data from Ubuntu before I go ahead with a re-install.

I've done a little reading up and understand that I can re-assemble the RAID array using the UUID by inspecting some of the member disks. But, I'm unsure if this will effect my array in any way?

I.e., if I do this - will my OF installation still boot and think nothing has changed on the array? Or by assembling it under Ubuntu change it in some way?

Thanks!

--
Craig.

---

### Post by cadriel on 2010-05-24
Anyone?

It'd put my mind at ease If I knew I wasn't going to break my RAID. :)

---

### Post by richardjh on 2010-06-01
I have assembled RAID devices from rescue CDs.

You should always have backups before you start but no damage should occur from assembling and mounting your RAID devices in a Rescue CD environment.

Something like SystemRescueCD will find and mount the RAID for you automatically. 

If you want to do it yourself you can use:

mdadm --assemble --scan

Which will scan for RAID devices and rebuild the RAID, you can then mount it like a block device.

Alternatively if you know how the RAID was built initially you could manually create the RAID using the create and add options to mdadm. Check out the man page and post back if you need a step by step guide.

There is also another [relevant page here]("http://www.cyberpro.com.au/tips/Mounting_RAID_partitions.html").

---

### Post by cadriel on 2010-06-01
Yup - My main aim was to make sure Ubuntu was going to read the raid correctly and the move to Ubuntu server was going to be a smooth one.

I ended up booting into the liveCD, then;
```

sudo apt-get mdadm
mdadm --assemble --scan --uuid=...

```

Which worked fine. At this point I was happy that the raid was all good - so I installed Ubuntu on my system drive (after backing up the OF install).

To my surprise - once installed, Ubuntu had automatically detected the raid - setup the mdadm.conf file, applied the changes to fstab - and had ALSO re-created the LVM that sat on top of the RAID.

All I needed to do after the install was mount the LV.

So - big props to the Ubuntu team. This made my transition super easy.

--
Craig.

---

