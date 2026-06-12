---
title: "Will Ubuntu work with an old Sparc-10 ?"
date: 2006-10-19
forum: Sun Sparc Users
---

### Post by njcollins on 2006-10-19
Hi there,

I have a (very) old Sparc-10 with 64Mb memory, 9Gb SCSI HDD and single speed caddy loading SCSI CDROM doing nothing at the moment. I thought it might make a good LAMP server for playing with PHP & MySQL. There's no monitor, although there is a graphics card in it - I use an old terminal via the serial port as a console.

Does Ubuntu support this age of Sparc processor ? All I've been able to find out is that the UltraSparc is supported, but this machine predates that by at least 5 years.
And is 64Mb enough for a minimal load LAMP server ?

Many thanks,

Nigel.

---

### Post by H0bb3z on 2006-10-20
I use Ubuntu server on an old Sun Netra T1 and it works great.  I also have an old SparcStation5 that I'm likely to bring back to life.  I don't think it will work with Ubuntu though, because it is based on pre-UltraSparc architecture. 

I guess you can give it a try though...

---

### Post by willca on 2006-10-20
This is the min requirements.

Desktop
256 megabytes RAM
3 gigabytes HD

Server
64 megabytes RAM
500 megabytes HD


[http://www.ubuntu.com/download/releasenotes/606#head-e15a51f7ff4cac464dfd54cbed7506ef13814de3](http://www.ubuntu.com/download/releasenotes/606#head-e15a51f7ff4cac464dfd54cbed7506ef13814de3)

I am running it on my Ultra-10 with 512MB / 9GB with xfce desktop and it works fine. Still have to figure out though why X crashes when the screensaver kicks in. Anyway its my play machine at work. Resolution on my 17" sun monitor has been fine at 1280x1024. 

Good luck.
-W

---

### Post by netztier on 2006-10-21
> **willca said:**
> Still have to figure out though why X crashes when the screensaver kicks in. Anyway its my play machine at work. Resolution on my 17" sun monitor has been fine at 1280x1024. 


Disable the OpenGL screensavers, and it'll work. I have the same problem on all my sparc machines. Actually, some of the OpenGL Screensavers work, such as GLmatrix or the Hypertorus, but I have no clue why.

regards

Marc

---

### Post by njcollins on 2006-10-22
Well, links I followed suggest this will work on sun4m machines (inc Sparc 2/5/10/IPC/IPX), so I downloaded the ISO and gave it a try... SILO runs and the initial Ubuntu welcome message appears, then it halts with a data access error.
Tried burning another CD at lower speed on a different machine, same result.
At first I suspected the CD-ROM on the S-10 (it's one of those ancient single-speed caddy-loading external SCSI units), but it still boots the Solaris-8 CD OK.

So, is it because I only have 64Mb memory, or is it the brand of CD I'm using ? Or does it really not want to run on the 32bit SuperSparc processors ?

Any suggestions welcomed.
Otherwise it's back to Solaris 8 for this machine, and I'll use the old P3 at the back of the cupboard for Ubuntu...

---

### Post by yonderway on 2006-12-20
The SPARCstation 10 and Ultra 10 are completely different machines (I think that detail might have been lost on some folks).  The SPARCstation 10 is a sun4m 32 bit sparc platform.  Unfortunatley Ubuntu only runs on the 64 bit sparcs.

You might have better luck with Aurora if you must have Linux on the box.  My personal preference for sun4m machines is actually OpenBSD though.

---

