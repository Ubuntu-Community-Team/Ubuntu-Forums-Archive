---
title: "1TB HD for Dell PowerEdge 2950?"
date: 2013-05-03
forum: Server Platforms
---

### Post by borgauf on 2013-05-03
[FONT=arial]I just bought a used Dell PowerEdge 2950 II with six PERC 5i SAS SATA drives at 73GB each (Seagate Cheetah 15k.5, Firmware S527). I plan to install Ubuntu Server on it. Since this will not be a "production" machine, just for experimenting, can I jerk five of those six drives and replace the one with a suitable 1TB drive? If so, what brand/model/spec 1TB could I use? Also, can I jerk out one of the two power supplies? ... All of this before installing U13.04 Server? Again, this is not meant to be for anything but learning and experimenting.[/FONT]

---

### Post by borgauf on 2013-05-03
[FONT=arial]I just bought a used Dell PowerEdge 2950 II with six PERC 5i SAS SATA drives at 73GB each (Seagate Cheetah 15k.5, Firmware S527). I plan to install Ubuntu Server on it. Since this will not be a "production" machine, just for experimenting, can I jerk five of those six drives and replace the one with a suitable 1TB drive? If so, what brand/model/spec 1TB could I use? Also, can I jerk out one of the two power supplies? ... All of this before installing U13.04 Server? Again, this is not meant to be for anything but learning and experimenting.[/FONT]

---

### Post by matt_symes on 2013-05-03
**Threads merged.**

Please do not create multiple threads on the same subject. It dilutes community effort and creates more work for staff.

It is also contrary to the Code of Conduct you signed when joining the forum.

---

### Post by borgauf on 2013-05-03
Sorry, I wanted to delete the other one but didn't know how.

---

### Post by SeijiSensei on 2013-05-03
I wouldn't remove the secondary power supply.  If you're concerned about electricity costs, see if you can disable it in the BIOS or physically.  I think there might even be a physical switch on the exterior of the back panel. 

If you are really interested in learning, I'd replace two of the hard drives with a pair of 1 TB drives and set them up as a RAID1 array using Linux software RAID and mdadm.  You might also consider putting the root of the operating system on the first of the existing drives then configure the remaining three as a RAID5 array.

So at the end you'd have
/dev/sda1   73 GB   /

/dev/sd[bcd] combined into
/dev/md0  146 GB  RAID5;  good candidate for /home or /var

/dev/sd[ef] combined into
/dev/md1      1 TB  RAID1; mount as /media/something

As for drive manufacturers, I've had less success with Samsung drives than other brands.  In general, I like to browse the [reviews at Newegg]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007603%20600003269&IsNodeId=1&bop=And&Order=PRICE&PageSize=20"). [This Seagate model](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148912) looks like a possible candidate.

---

### Post by sandyd on 2013-05-03
Note that the PERC 5i is already a HW RAID controller, and you *may* have to disable raid in the BIOS/PERC settings before beginning the setup

---

### Post by borgauf on 2013-05-03
@SeijiSensei: thanks for the tip. Will try eventually. But just to get one 1TB drive and have it non-RAID will have to do for now. Any ideas how to do that?

---

### Post by Vegan on 2013-05-04
you can use a single disk on a raid card, it will simply not be error tolerant until you use more than one disk

---

### Post by darkod on 2013-05-04
I have looked at PE 2950 but I'm not sure the PERC 5i can be disabled as HW raid. Although I haven't looked very closely, yet.

If it really can't be made simple pass through (which I think it can't), using mdadm is getting complicated, unfortunately. I would love mdadm on my 2950 too, and a pass through option.

Otherwise, you are looking into making 6 separate raid0 one disk logical drives, and using them as 6 devices in ubuntu. Which makes little overhead because the PERC is still involved, and in case it dies you can't simply connect the disk where ever since it will have the PERC meta data on it.

PS. One option would be to replace the PERC with something like IBM M1015 which you can easily flash to IT mode and make it a simple pass through HBA. That will allow you to use the 6 disks directly by the ubuntu OS, or any other similar OS that wan't to handle the disks directly like FreeNAS (my original reason I was looking into the 2950 I have at work).

---

### Post by tgalati4 on 2013-05-04
Try updating the PERC firmware from Dell's website.  Update the main server BIOS as well.  I have an older PE1750 with PERC and I can set the drives as JBOD--just a bunch of disks.  With the disks set individually, you can use the PERC's cloning tools and extensive diagnostics as well as SMART monitoring.  Or, just put in a 1/2 height SATA card and hang your disks off of that.  The PERC hardware RAID works well for smaller disks, I haven't used larger disks with it.

---

### Post by borgauf on 2013-05-04
Great help, people, thanks. Got 12.04 Server installed and I've got df -m reporting 307GB on /dev/sda1 . . . that's good enough for now. Thanks again. Maybe I'll get adventurous later....

---

