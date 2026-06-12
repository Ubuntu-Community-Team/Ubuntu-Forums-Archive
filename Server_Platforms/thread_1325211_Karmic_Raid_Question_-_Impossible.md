---
title: "Karmic Raid Question - Impossible?"
date: 2009-11-13
forum: Server Platforms
---

### Post by The Real Dave on 2009-11-13
Ok, so I recently installed Karmic Server on some old hardware of mine, a 451Mhz PIII with 128Mb RAM. Its installed on a 6GB HDD, with another 9GB and 2^2Gb flash drives attached. 

So my question is, can I setup RAID0 or JBOD with these flash drives, and maybe even the 9Gb HDD? Is it even possible, and if so, how do I go about doing it? :) Any advice would be much appreciated

---

### Post by ian dobson on 2009-11-13
Hi,

Have a look at mdadm. You can create an array using any file system capable device (Harddisk,RAM disk or even files on a real disk).

I'm using a mdadm RAID5 array of about 6Tb for almost 6 months without any problems.

Regards
Ian Dobson

---

### Post by The Real Dave on 2009-11-13
> **ian dobson said:**
> Hi,

Have a look at mdadm. You can create an array using any file system capable device (Harddisk,RAM disk or even files on a real disk).

I'm using a mdadm RAID5 array of about 6Tb for almost 6 months without any problems.

Regards
Ian Dobson

Thanks for the reply :) Found [this]("http://ubuntuforums.org/showthread.php?t=408461") on using mdadm, so I'm gonna give it a shot now :) I'll let ye know how it goes

---

### Post by The Real Dave on 2009-11-13
Mdadm did the job perfectly, made a linear RAID :) thanks :)

---

