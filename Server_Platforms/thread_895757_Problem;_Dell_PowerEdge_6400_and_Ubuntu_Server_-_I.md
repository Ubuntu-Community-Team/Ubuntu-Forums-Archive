---
title: "Problem; Dell PowerEdge 6400 and Ubuntu Server - Installation"
date: 2008-08-20
forum: Server Platforms
---

### Post by Adoran on 2008-08-20
Hello forum,

I have just bought a [PowerEdge 6400 server]("http://support.dell.com/support/topics/global.aspx/support/product_support/product_support_central?~ck=ln&c=us&cs=555&l=en&lnki=0&s=biz&SystemID=PWE_PNT_P3T_6400") for an immaculate $500 and I am looking to get this mother running Ubuntu 8.04

I checked the manual before hand and saw that the server runs Red Hat - lovely, I thought surely this means it will run Ubuntu. Sadly not, but hopefully this will be a learning experience. 

The problem arises when the setup checks the CD's integrity; It throws out a chksum error. It has a problem, it would appear, on a random package of the CD as it is never the same package twice. I have run the "Check CD for Defect" option and it throws up the same error. 

Good. I thought if the CD is a coaster then I can re-download a copy of ubuntu, burn another CD and try that. No luck - with two different brands of CDs and chksum verified copy of Ubuntu. 

Why does this happen? The CD is good so why does a chksum error come up? Is there any way to suppress this and brute force the OS onto the server?

I'll talk to DELL but in the meantime if anyone has any insight into this it would be great to know.

---

### Post by commlord on 2008-09-03
I have the same issue with my old 6400.  I have checked the checksum on the download and CD and it works on another pc.
I started an install of windows to verify the basic hardware setup and that was good.

On mine I believe its related to the fact that the CD is a scsi interface rather then ide. If that is the case is there a driver and mechanism to load it?

---

### Post by windependence on 2008-09-04
It looks like this is probably a BIOS issue.

Check out this thread:

[http://ubuntuforums.org/showthread.php?t=549385](http://ubuntuforums.org/showthread.php?t=549385)


-Tim

---

### Post by commlord on 2008-09-04
> **windependence said:**
> It looks like this is probably a BIOS issue.

Check out this thread:

[http://ubuntuforums.org/showthread.php?t=549385](http://ubuntuforums.org/showthread.php?t=549385)


-Tim
Yes, it probably is.  The downside to that theory is that it has the latest BIOS from Dell which is several years old. So there is nothing to update.
So I had the great idea of booting to a USB with the iso on it but the bios doesnt support booting from USB.

---

### Post by windependence on 2008-09-04
Well you could also write the image to the drive and install from a live CD possibly, or maybe a network install?

-Tim

---

