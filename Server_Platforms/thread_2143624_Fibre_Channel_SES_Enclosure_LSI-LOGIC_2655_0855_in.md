---
title: "Fibre Channel SES Enclosure LSI-LOGIC 2655 0855 in Ubuntu 12.04"
date: 2013-05-09
forum: Server Platforms
---

### Post by xavirp on 2013-05-09
Hi all,

I'm recently purchased an enclosure from LSI Logic, model 2655 0855, with 14x300Gb fibre channel drives on. Although I googled a lot, I cannot find any reference or guide for this product, and so I'm finding many problems to put it to work. Disks are wiped by whom sold it to me. I also have both a QLA2340 HBA from HP, located in an HP Proliant ML370 G5. 

What I know is:

- Fast!Util finds out a loop where the enclosure is named, but it's not a block device, so cannot format or make a raid.
- Ubuntu detect everything without problem. I can access through /sys/class/enclosure/2:0:0:0/ to all the disks, but at Scsi level, that is, I can blink or locate disks on the enclosures by changing leds (so i presume that the connection through fibre channel works).
- SANsurfer from Qlogic can see the hba and modify its parameters, but don't detect targets.

What I don't know:

- How to format the disks, make a RAID, access those disks, mount them....well, use the whole enclosure.

Anybody with skills about these products could help me? 

If you need further info, please ask for it and I will post whatever you want.

Thank you very much for your help. I don't know where to post this but at the Ubuntu Forums.

---

### Post by xavirp on 2013-05-10
Ok. I 'googled a lot today, and I found that if I don't have the Sun Common Array Manager, my storagetek is a nice and expensive paperholder. The free download from Sun don't work anymore, and only with a support account from Oracle can be downloaded.

Anybody could help here, even with an old version of this software?

Thx.

---

### Post by NigelRen on 2013-05-11
Not sure if this helps - but have you looked at thread [http://ubuntuforums.org/showthread.php?t=831223](http://ubuntuforums.org/showthread.php?t=831223)

---

### Post by Dave_Cook on 2014-01-30
Hi:

Are you still looking for CAM?

Cheers,
Dave

---

