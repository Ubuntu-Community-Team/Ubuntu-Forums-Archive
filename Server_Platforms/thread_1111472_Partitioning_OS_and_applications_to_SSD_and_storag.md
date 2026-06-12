---
title: "Partitioning OS and applications to SSD and storage to disk harddrive"
date: 2009-03-30
forum: Server Platforms
---

### Post by pgalasti on 2009-03-30
I've searched the forum for any related threads but wasn't able to find much.

I've built my system (currently running Windows 7 as a Desktop until I can figure this out) composed of a SATA 16GB solid state drive and an internal SATA 1.5TB disk drive. I want to install Ubuntu server and future applications to the SSD and storage to the disk harddrive for best response results.

To do this, do I format everything except the /home directory to SSD giving users storage in their respective home directory or is there a better way to go about doing this? Also, what RAID configuration would be best?

If anyone has any solutions or are able to reference a thread I didn't see, I would be very thankful. :P

---

### Post by doogy2004 on 2009-03-30
> **pgalasti said:**
> To do this, do I format everything except the /home directory to SSD giving users storage in their respective home directory or is there a better way to go about doing this? Also, what RAID configuration would be best?

I have my setup using the following:

1 10GB HDD mounted at /
3 320 GB HDDs with RAID5 and LVM mounted at /home

---

### Post by pgalasti on 2009-03-30
By using Raid5, would I be limiting the complete storage compacity?

---

### Post by doogy2004 on 2009-03-30
> **pgalasti said:**
> By using Raid5, would I be limiting the complete storage compacity?

I believe that you woul loose 1 drives worth of space in favor of redundancy.  Also, I don't think that you can boot from RAID5.

---

### Post by pgalasti on 2009-03-30
What would be the best way of installing the server? Leaving out the ssd?

---

### Post by doogy2004 on 2009-03-30
> **pgalasti said:**
> What would be the best way of installing the server? Leaving out the ssd?

mount you SSD Drive as /
mount your HDD Drive as /home

This will keep all of your program files on the SSD for performance and keep all of your user's data on the HDD for disk space.

---

### Post by doogy2004 on 2009-03-30
I don't keep up with hardware too much but I was hearing that multiple rewrites can cause SSD disks to wear out sooner.  As a precaution I would suggest using a swap file located on the HDD disk.

Here is a good how-to on the process:
[http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)

---

### Post by tsh on 2009-04-20
I've been pondering the same route, you probably want /var on hdd, and maybe want to avoid anything which will be frequently written residing on SSD, not only because of the write wear, but writes being slower won't show the same sort of speed up as reads on ssd.

Motivations for this are NOT faster boot time (which is a once-a-month event) but better responsiveness, and reduced power consumption given that my box is running myth-backend (mostly idle most of the time)

---

### Post by doogy2004 on 2009-04-20
I'd apply the same concept of creating a swap file to creating a file to mount /var on or anyother directory.

---

