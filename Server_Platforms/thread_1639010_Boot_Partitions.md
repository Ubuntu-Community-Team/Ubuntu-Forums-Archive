---
title: "Boot Partitions"
date: 2010-12-06
forum: Server Platforms
---

### Post by chrislynch8 on 2010-12-06
Hi,

I am building a 10.04.1LTS server. I am putting the /root filesystem into a Software RAID1 partition. I want to keeo my /boot partition outside of RAID.

Is there a way to have a boot partition on both sda and sdb so if one drive fails the second boot partition will work away - or should this be kept in with RAID also.

---

### Post by pricetech on 2010-12-06
As long is it's hardware RAID, I see no reason not to put your /boot partition there.

Software RAID is another story of course.

---

### Post by dtfinch on 2010-12-06
My first several servers all had / and /boot on an md raid 1, and I didn't have to do anything special. Though this was 5-6 years ago, and they ran CentOS. But I imagine it'd work fine on Ubuntu as well.

---

### Post by chrislynch8 on 2010-12-07
I'm not using Hardware RAID as I cannot see an benefits for it on a two disk array RAID1. 

In my pervious builds I have had / and /boot on md0 partition, but I've been advised that it would be benefical to move /boot out of the main / partition.

Now I have 
md0 -> /boot
md1 -> /

What issues are there with Software RAID for the /boot parition.

---

### Post by dtfinch on 2010-12-07
The main issue is that it has to be raid 1. And traditionally /boot has had its own partition, toward the beginning of the drive, because many bioses [had trouble](http://tldp.org/HOWTO/Large-Disk-HOWTO-4.html) accessing anything after the first several gb, so without a dedicated /boot partition an upgrade could randomly move your kernel/initrd image outside that range and your system would stop booting.

And you might want to make sure grub actually installs on both drives. In the distant past I've seen it only get installed on the first, but I don't know if that still happens.

---

### Post by ian dobson on 2010-12-07
Hi,

On my backend server I have a "small" 20Gb boot and root partition mirrored over 3 disks and the rest of the space a a RAID5 array.

Some time ago one of the drives died (the first one), and after booting from a LiveCD and loading grub onto the new drive the system ran without any problems. If I had installed on grub on all drives then the system would have booted without any intervention on my part.

Regards
Ian Dobson

---

### Post by chrislynch8 on 2010-12-08
I created a seperate boot partition and created RAID1 with it, in 10.04 also I noticed that after a upgrade it noticed GRUB was only installed on the first disk and ask if it could install onto the second disk - which was a susprise. I normally have to manaull install GRUB onto the other disk

Chris

---

