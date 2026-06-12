---
title: "Home data recovery."
date: 2007-08-06
forum: The Cafe
---

### Post by Maxster on 2007-08-06
so my 250 gb western-d hard drive decided to poop on me and be not detected anymore. i think its dead, maybe because of over heating.
but with my warranty i can get a new one, but i loose all my files....
data recovery companies= minimum of 600$ to get my data. 

is it possible to buy a second hard drive, exact same model and swap the  physical hard discs? has anyone done this at home or heard anything about attempting such thing?

thanks

---

### Post by ~LoKe on 2007-08-06
> **Maxster said:**
> is it possible to buy a second hard drive, exact same model and swap the  physical hard discs?
Yep.  Just make sure no dust/etc gets in.

---

### Post by mips on 2007-08-06
> **Maxster said:**
> so my 250 gb western-d hard drive decided to poop on me and be not detected anymore. i think its dead, maybe because of over heating.
but with my warranty i can get a new one, but i loose all my files....
data recovery companies= minimum of 600$ to get my data. 

is it possible to buy a second hard drive, exact same model and swap the  physical hard discs? has anyone done this at home or heard anything about attempting such thing?

thanks

Does it get seen by the BIOS ?

---

### Post by cmat on 2007-08-06
A company called OnTrack does data recovery and also sells some software.

[http://www.ontrackdatarecovery.com/](http://www.ontrackdatarecovery.com/)

I really don't recommend opening up hard drives. They are very tricky pieces of technology. First off the screws are designed to "round", you need to apply downward pressure on the driver to avoid stripping them. The keeping dust out of them is virtually impossible once it's open. Then you need to deal with removing small components. Get to the disks then transplant the disks. Really it should be left to the professionals that have the tools and clean rooms to do it.

---

### Post by Maxster on 2007-08-06
i just watched an interesting presentation about this on youtube
[http://www.youtube.com/watch?v=Kx-D1nJcv0k](http://www.youtube.com/watch?v=Kx-D1nJcv0k)

mips: well it says that the secondary master is not detected
it knows its there?

---

### Post by popch on 2007-08-06
> **Maxster said:**
> with my warranty i can get a new one, but i loose all my files....

duh

---

### Post by psusi on 2007-08-06
If it is the controller board that went bad, then yes, you can usually just swap the board from another good drive of the same model and recover.  If it is the physical platters that are bad, the only thing you can do is send it to one of those recovery companies.  

You did have backups though right?  right?

---

### Post by mips on 2007-08-06
> **psusi said:**
> 
You did have backups though right?  right?

If he had backups this would not be an issue ;)

---

### Post by Maxster on 2007-08-06
according to the guy in the video, if your gona swap parts, you need two drives that were built aproximatly during the same week. he says the firmware is updated often and it is set to some special things on the disc so the heads knows were its at. maybee what i said dosent make sense but watch the video.

---

### Post by mips on 2007-08-07
> **Maxster said:**
> according to the guy in the video, if your gona swap parts, you need two drives that were built aproximatly during the same week. he says the firmware is updated often and it is set to some special things on the disc so the heads knows were its at. maybee what i said dosent make sense but watch the video.

The serial numbers have to be close together or the board revisions have to be the same. It's worth a try to swap the logic boards out but I would NOT open the drive as you need a clean room and knowledge for that.

---

### Post by mips on 2007-08-07
Try this, 

[http://ubuntuforums.org/showthread.php?t=519632](http://ubuntuforums.org/showthread.php?t=519632)
[http://rescubuntu.info/](http://rescubuntu.info/)
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by az on 2007-08-07
> **Maxster said:**
> so my 250 gb western-d hard drive decided to poop on me and be not detected anymore. i think its dead, maybe because of over heating.
but with my warranty i can get a new one, but i loose all my files....
data recovery companies= minimum of 600$ to get my data. 


You may still be able to use software to retreive data.  Check the cables or possible put the drive in an external enclosure and see if you can make an image of it using gnu-ddrescue.  The fact that the bios currently does not see it is disturbing, but it could be worse.

Open your computer case and try to find out if you can hear it spin when you power up.

I don't think changing the controller card is a realistic option.  Nor would be actually opening up the drive in a clean room.  Unless you have thousands of dollars worth of files on there.

---

### Post by smoker on 2007-08-07
there is an app called 'spinrite' from the guys at gibson research which is worth a go. it is a pay for app, so, i suppose it depends on how much you are willing to pay! info here: [http://www.grc.com/spinrite.htm](http://www.grc.com/spinrite.htm)

best of luck.

---

### Post by Aarryn on 2007-08-08
If you are not hearing the clicking sound of your hard drive and BIOS is able to detect your hard drive by attaching as a slave then you can try with Stellar Phoenix Windows [Data Recovery Software]("http://www.stellarinfo.com") , it helps to recover data from inaccessible hard drive. 
Download the demo to try the software: [http://www.stellarinfo.com/partition-recovery.htm](http://www.stellarinfo.com/partition-recovery.htm)

---

### Post by az on 2007-08-08
> **smoker said:**
> there is an app called 'spinrite' from the guys at gibson research which is worth a go. it is a pay for app, so, i suppose it depends on how much you are willing to pay! info here: [http://www.grc.com/spinrite.htm](http://www.grc.com/spinrite.htm)

best of luck.

Spinrite writes to a corrupted disk.  In general, this should be avoided.  If you want to recover data, then you should just focus on that, and not try to un-corrupt the drive.  You can fix an image of the drive a lot more safely.  The only thing is you need another drive onto which you write the image.

You will save that money (a new 300 gig drive costs about 100 bucks, and the spinrite proprietary licence is ?$85? but your drive is either unfixable or on the verge of breaking down again.  Even if it got fixed, I would not trust that hard disk again.

> **Aarryn said:**
> If you are not hearing the clicking sound of your hard drive and BIOS is able to detect your hard drive by attaching as a slave then you can try with Stellar Phoenix Windows [Data Recovery Software]("http://www.stellarinfo.com") , it helps to recover data from inaccessible hard drive. 
Download the demo to try the software: [http://www.stellarinfo.com/partition-recovery.htm](http://www.stellarinfo.com/partition-recovery.htm)

Just use parted or testdisk for free. [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by mips on 2007-08-08
> **az said:**
> Spinrite writes to a corrupted disk.  In general, this should be avoided.  If you want to recover data, then you should just focus on that, and not try to un-corrupt the drive.  You can fix an image of the drive a lot more safely.  The only thing is you need another drive onto which you write the image.


Agreed, Spinrite is not the best option here. I used it once before and probably never will again, have it lying around somewhere.

---

### Post by smoker on 2007-08-08
> **az said:**
> Spinrite writes to a corrupted disk.  In general, this should be avoided

i'm not promoting spinrite one way or another, but if you check the user manual at the link i posted, you will note that there are different levels that can be chosen when using the app, and one includes it writing nothing to the damaged drive.

it is always wisest to have backups of crucial data, and of course, you are correct in that you should image a damaged drive before attempting risky recovery techniques, but, alas, this is not always possible. again, it comes down to if you think your data is worth paying $600 for a professional service to try to restore, or try (and hope) something at $85 will do the job.

i also, would never trust a drive again that had failed.:confused:

---

