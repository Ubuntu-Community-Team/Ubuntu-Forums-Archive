---
title: "Feature Freeze for PP"
date: 2012-02-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-02-15
Incoming Feature Freeze for PP. See quote below:
Regards,
Effenberg

> Hello Ubuntu Developers,

Its now less than 24 hours before we enter Feature Freeze for Precise.

Please take care to ensure that any remaining packages have been well tested prior to uploading, so we minimize the daily image breakage.

For those packages that interact with others packages at the system level and that still need to be uploaded, please denote when you expect them to land in: [https://wiki.ubuntu.com/PrecisePangolin/FeatureLanding](https://wiki.ubuntu.com/PrecisePangolin/FeatureLanding) If there are too many conflicts occurring tomorrow, we may ask some to delay their upload for a day or two (not sure if it will be needed yet or not).

Thank you for your help with this,

Kate

---

### Post by effenberg0x0 on 2012-02-16
More on the Feature Freeze and confirmation on next milestone date. See below.

Regards,
Effenberg

> Hello Ubuntu Developers,
 
   2100 UTC has now passed and we are in Feature Freeze[1] for Precise.
Many thank yous to those developers who got their tested work in 
on time!  The focus from here until release is on fixing bugs and
polishing. [B]  Our next upcoming milestone release[2] is Beta 1 on 
_March 1st._[/B]

   Also, earlier today the decision was made that the default 
ARM architecture for Ubuntu 12.04 will transition to be armhf.
The armel architecture will continue to exist but not be the defulat
supported architecture.  Image builds will be switched to armhf (except
for omap3 and ac100 armel community project builds, which will retain
compatibility with their respective binary drivers).  More information
about this transition will be available soon.

Thanks,
Kate Stewart
on behalf of the Ubuntu Release Team

[1] [https://wiki.ubuntu.com/FeatureFreeze](https://wiki.ubuntu.com/FeatureFreeze)
[2] [https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule](https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule)

---

### Post by prusswan on 2012-02-16
so now they will concentrate only on bug fixing?

---

### Post by wolfen69 on 2012-02-16
> **prusswan said:**
> so now they will concentrate only on bug fixing?

Apparently. That's OK, as they need the dust to settle and work on any remaining bugs and polish. 12.04 is shaping up nicely.

---

### Post by ranch hand on 2012-02-16
> **prusswan said:**
> so now they will concentrate only on bug fixing?
Pretty much so but not completely.

There are usually a couple of exceptions that need to be made for critical packages that are not quite ready right at freeze time.

I don't know if that is the case this time or not but human nature, communication, and things that just happen probably mean that it is.

Not sure how many critical bugs are out there at this point but each may take more than one attempt at fixing.  The patch must be made, packaged and released to the testers.  Some are going to need tweaked after that to work on all hardware.  This all takes time.

There will probably be some things added to the OS that have not been seen before but this will be in the area of artwork mainly.

---

### Post by effenberg0x0 on 2012-02-16
Yes, I would expect great changes and innovation stuff to be done by now. 
We do have [UI Freeze on Feb 23rd]("https://wiki.ubuntu.com/UserInterfaceFreeze"), so there's space for a couple more change though.

Hopefully the next next ±60 days will be used wisely. It's time for us to recheck our bug reports, re-test as much as we can, etc. 

Regards,
Effenberg

---

