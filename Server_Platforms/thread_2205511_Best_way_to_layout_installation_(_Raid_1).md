---
title: "Best way to layout installation ( Raid 1)"
date: 2014-02-14
forum: Server Platforms
---

### Post by ally2 on 2014-02-14
Hey guys got myself two 500 gig drives, Im undertaking new install and want to combine both drives into a Raid 1 array. 

I will be setting up the Raid during the install process. 

Questions I have are below 

1) do I put /boot outside the raid array on a separate partition? 

2) I want a share for data to 
be used for media and data
Mainly for Samba shares should I create a /data for this? 

3) Best partition scheme / layout 
How would you setup the drives.
I have read alot of Linux documentation and the partition schemes tend to vary. 

I was thinking 

/boot
/
/data
Swap 

And mirror the / and data would that be a good scheme to go with? 

Many Thanks

---

### Post by ally2 on 2014-02-14
Can anybody please help? need to start work on this soon :)

---

### Post by ally2 on 2014-02-15
Gods of ubuntu please help :)

---

### Post by nerdtron on 2014-02-16
I just put everything on the raid array. Create a RAID1 of the two disk and then partition the array for /boot, /, /data, and swap partitions.
You need redundancy for /boot too so it is important to be included on the raid.

---

### Post by SeijiSensei on 2014-02-16
I prefer to keep /boot out of the array so the machine can start up even if the array has gone south.

Personally I'm usually only concerned with /var and /home as most of the reading and writing after installation is concentrated there.  But it's probably simpler to set aside a small partition for /boot (I use 512 MB) on each drive, make the rest RAID1, and mount it as /.

---

### Post by ally2 on 2014-02-16
Thanks for the replies, using the above scheme how do you layout your samba shares? Am I right in thinking /home/data

---

### Post by nerdtron on 2014-02-16
You can place your share on it separate partition such as /data, or just put it in /home/data. Just make sure the partition is large enough for your needs.

---

### Post by ally2 on 2014-02-17
Many thanks for the advice chaps
Very informative as always this thread can be now marked as solved. 

Cheers :)

---

