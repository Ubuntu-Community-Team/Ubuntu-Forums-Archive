---
title: "server 11.10 error once a week"
date: 2012-02-17
forum: Server Platforms
---

### Post by bazzieb on 2012-02-17
Hi There

i have a HP server running ubuntu server 11.10 which pretty much just runs nagios. At least once a week i need to reboot the server because it get an error that wont allow me to do anything.

I have attached a pic with this error as i was not able to take a screenshot.

Hopefully it is an easy fix.

Regards
BazzieB

---

### Post by ian dobson on 2012-02-17
Hi,

Looks as if something is really hitting your filesystem, causing other processes to be blocked for more than 120seconds.

When is running when it happens. Maybe run iotop -o -P to see who's hitting the disk.

Regards
Ian Dobson

---

### Post by cabaro on 2012-02-17
Is the server running as a virtual host?

I had a similar looking problem running ontop xen.
The problem went away after removing irqbalance totally.

---

### Post by bazzieb on 2012-02-17
Hi Ian

Thanks for your reply. After running iotop, i was able to capture these 2 processes, please view attachements. Those are the only 2 i see running. The hardware is a couple of years old as well.

Regards
BazzieB

---

### Post by bazzieb on 2012-02-17
Hi cabaro, nope, this is a stand alone OS.

---

### Post by ian dobson on 2012-02-17
Hi,

Looking at your attachments your running a HP raid controller.

Maybe try playing with the mount options for your hp device (try increasing or reducing the commit parameter).

Regards
Ian Dobson

---

### Post by bazzieb on 2012-02-22
Hi Ian

I am running an HP raid controller. It is a 64mb raid controller an i do think it needs a firmware update. I am using raid 5 on it as well. 

As to your options, i don't really know what you mean?

---

### Post by roelforg on 2012-02-22
What is that cciss process?
It appeared on all three shots.

---

### Post by ian dobson on 2012-02-22
> **roelforg said:**
> What is that cciss process?
It appeared on all three shots.

The cciss process is the process that controlled a HP raid controller.

bazzieb have a look at your /etc/fstab you can add an option commit=X which will cause the ext4 fs to wait/combine several writes (up to commit time) into one. Maybe that might help. Or try a firmware update.

Regards
Ian Dobson

---

### Post by roelforg on 2012-02-22
> **ian dobson said:**
> The cciss process is the process that controlled a HP raid controller.

bazzieb have a look at your /etc/fstab you can add an option commit=X which will cause the ext4 fs to wait/combine several writes (up to commit time) into one. Maybe that might help. Or try a firmware update.

Regards
Ian Dobson
Ah, never worked with RAID.

---

### Post by bazzieb on 2012-02-27
Hi there

I am going to try a raid card firmware update first and then i will try the fstab entry. 

Thanks for all the assistance so far.:)

---

### Post by bazzieb on 2012-03-05
Hi There

I updated all the firmware i could and the server hasnt gone down once, so i am glad to say that i think it is sorted. Thanks for all the suggestions.

---

