---
title: "Ubuntu Dapper Drake Server Install on Enterprise 250 UltraSPARC"
date: 2006-09-20
forum: Sun Sparc Users
---

### Post by akl on 2006-09-20
I am not able to boot from the Ubuntu CD ([http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-server-sparc.iso](http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-server-sparc.iso)) , using "boot cdrom." I get the following error message:

Bad magic number in disk label.
Can't open disk label package.

Can't open boot device.

I am able to boot from the cdrom with Debian Sarge and Solaris 2.6.  Does anyone know what is preventing the Ubuntu disk install?

Thanks!

---

### Post by kmantronix on 2006-09-20
I suppose your ubuntu install CD is defective.

Try to boot with it on another machine or burn it again on a new blank CD.

---

### Post by akl on 2006-09-20
Hi, thanks for the reply!

I burned a new CD with the same result.  I also tried both CDs on three other USparcs. No luck there either.

Any other ideas?

---

### Post by Mr.Vanman on 2006-09-21
> **akl said:**
> Hi, thanks for the reply!

I burned a new CD with the same result.  I also tried both CDs on three other USparcs. No luck there either.

Any other ideas?

I would suspect the application you are using to burn the image.  I have an E250 as well and using the same .iso from the same location without issue.  I burned it using "Disk Utility" on a Mac...

---

### Post by tideline on 2006-09-22
Did you check the MD5 for the download?

---

### Post by akl on 2006-09-29
Here’s what I have for the MD5:

2ccc1ec608040e6aac8913a016c31bed  ubuntu-6.06.1-server-sparc.iso

Does that look correct?  Does this MD5SUM have to be on the CD with the .iso?  I have one CD with it and one CD without it.  Neither CD works.

I also used two separate programs to burn the CDs.  I used the version installed on my XP platform (IBM’s RecordNow) and the version recommended on the website.  Same result for both programs.

I checked that I am able to boot from the CD with other both Solaris 2.6 OS and Debian Sarge OS.  No problems installing those.

Is it possible that the .iso available is corrupt?

I also noticed that Ubuntu’s Shipit does not provide SPARC cds.  Does Ubuntu plan to discontinue the OS for the SPARC platform?

Thanks again!

---

### Post by vikrant on 2006-10-01
I had a CD do that to me the 1st time I tried installing it.  I found that if I burned the CD at the lowest speed possible it worked.  Other then downloading the SPARC server iso again; that is the only other thing I can think of trying.

-Vik

---

### Post by yonderway on 2006-12-20
I have run into that error on a number of occasions, mostly for different reasons.

Your devalias for "cdrom" might not match the scsi device for your cdrom drive.  Try this:

1) From the 'ok' prompt, type 'probe-scsi-all'
2) Make note of the address of the CDROM
3) type 'nvalias cdrom2 /pci@8,600000/scsi@6,1/disk' substituting in the correct address for YOUR cdrom drive.
4) 'nvstore' to save the changes
5) 'boot cdrom' ... does this boot now?

I've also gotten that error accidentally booting an x86 CDROM in a Sparc box (doh!).  Additionally, some Sun machines that came with DVD-ROM drives had bad firmware that prevented them from booting off of certain discs.  If your drive is affected, I think you actually need to be running Solaris to install the patch!  It is probably worthwhile for you to buy a 9 or 18 GB drive in a sled off of eBay to have Solaris on so that you can patch firmware when needed.

---

### Post by prkfriryce on 2007-01-18
After reading many sunblade issues, I fel my reply for my sunblade 100 would fall under this topic.

I as well and receiving the message from boot cdrom using the 6.10 desktop 64bit image:

```
ok boot cdrom
Boot device: /pci@1f,0/ide@d/cdrom@1,0:f  File and args:
Bad madic number in disk label
Can't open disk label package

```

i was successful on other machines and burned the disc using cdrecord @ speed=8

any suggestions?

---

### Post by prkfriryce on 2007-02-13
:popcorn:

---

