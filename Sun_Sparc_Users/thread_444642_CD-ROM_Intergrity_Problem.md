---
title: "CD-ROM Intergrity Problem"
date: 2007-05-15
forum: Sun Sparc Users
---

### Post by soapyfish on 2007-05-15
Hi,

I seem to be having constant problems installing 6.10 for sparc on my Ultra 2. I have sucessfully sorted the esp driver problem  with the "modprobe esp"  command and managed to get the machine to allocate the RAM correctly at the swtart by removing 512MB of the total gig.

Currently The system insists that there are problems with the intergrity of the CD-ROM I have burnt.
I have downloaded the .iso file from the belgium mirror listed on the homepage. (I have tried all sorts of different servers and iso's ) 

after the install starts it tries to install a package called "base-utils"  this seems to be the problematic file the error I get is 

"There was a problem reading data from the CD-ROM. Please make sure it is in the drive. If retrying does not work check the integrity of the cdrom"

So I check the CD-ROM intergirty  and it tells me that     ./dists/etch/main/binary-sparc/Packages File failed the MD5 Checksum verifcation.  

what I am really asking is has any one else had this problem  ?  I have written the cd's as slow as I can on the best media I can find  (after all its an old 12x scsi cdrom in the Ultra 2 but what ever I do i have this problem.   

I have burnt the Iso using ubuntu as well as windows   :-(  

Thanks

---

### Post by tgm4883 on 2007-05-15
ive had problems like that.  turns out it was my cd drive

---

### Post by soapyfish on 2007-05-16
Oh thats not good news   :-(   

The machine does install solaris latest build from half a dozen CD's without a problem though.

---

### Post by gavinj44 on 2007-05-17
I had these problems with a couple of i386 laptops the CD would fail on one but not on the other, all the MD5 sums were ok.

Turns out after running memtest86+ to be duff memory .... files get corrupted in copying.

Not too sure if memtest is available on the sparc CD but you could try swapping the 512 you took out for the 512 that is currently in the box and give it a go.

Regards,
Gavin

---

### Post by soapyfish on 2007-05-17
Thankyou for that suggestion I will try that as soon as I can and update the thread.  I don't know why I did not think of that  :lolflag:

---

### Post by gavinj44 on 2007-05-25
Any luck with the memtest ?

---

### Post by tgm4883 on 2007-05-25
I don't know why I didn't see any of these updates.

I should be more clear.  When I said it was my cd drive I meant it only kinda was.  The cd drive was finiky about what drive the cd was burned on.  For instance if I had used my Liton CDRW to burn the CD, then I would have errors when I went to install it.  However, if I burned with my Memorex burner, then it would work fine during the install.  

Some CD players like some drives/media better than others.

My suggestion is that if the memtest doesn't pan out, try burning on a different drive.

It just occured to me, did you check the iso against the md5sum before burning?

---

### Post by soapyfish on 2007-06-08
I have given up on this for the time being  I think its something to do with the scsi bus or the drive maybe. I get many errors all to do with the drive and the interface on lots of different OS's I have recently tried including 

Debian
Ubuntu
OpenBSD 
FreeBSD,

Some others every system has FATAL problems with the drive or contoller, I think I am unlucky with this particular machine.

---

### Post by tgm4883 on 2007-06-08
Well you could always try to install from a usb key or a network install

---

### Post by Lord_Vader on 2007-08-01
I had problems until I formated the disk with the Solaris CD. Then ubuntu went on fine.

---

