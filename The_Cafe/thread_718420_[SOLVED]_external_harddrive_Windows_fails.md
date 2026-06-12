---
title: "[SOLVED] external harddrive: Windows fails"
date: 2008-03-08
forum: The Cafe
---

### Post by conehead77 on 2008-03-08
EDIT: I formatted the harddrive with ext3, thats why windows cannot detect it ](*,)

I am using a Philips 500GB external harddrive for quite some time now. 
Everything worked just fine, but then i wanted to access it from Windows. I didnt see a "mass storage device" or something like that. 
Hm, i plugged the drive out and in again and out and in again with no luck. 

Then i thought maybe i need some drivers for it? 
Quickly i found the Philips support site: [http://www.p4c.philips.com/cgi-bin/dcbint/cpindex.pl?slg=ENG&cat=PC_STORAGE_CA&sct=EXTERNAL_HARD_DISKS_SU&grp=PC_PRODUCTS_GR&session=20080308050643_141.26.70.218&ctn=SPE3051CC/00&mid=Link_Software&hlt=Link_Software](http://www.p4c.philips.com/cgi-bin/dcbint/cpindex.pl?slg=ENG&cat=PC_STORAGE_CA&sct=EXTERNAL_HARD_DISKS_SU&grp=PC_PRODUCTS_GR&session=20080308050643_141.26.70.218&ctn=SPE3051CC/00&mid=Link_Software&hlt=Link_Software)
Drivers are only available for Win98 or ME ](*,)

Well, i will just reboot to Ubuntu as it works fine there.
But let this be a lesson for you: **Never buy hardware for Windows before checking if it works with your system!**

Actually it isnt Windows fault as Philips need to make a proper driver, but come on, its just a stupid USB device!

---

### Post by JacobRogers on 2008-03-08
500 GB, it can't be that old can it?  I'm surprised it doesn't have xp drivers

---

### Post by jetsam on 2008-03-08
The documentation on the site you linked to says the drive supports xp and vista.  I think it doesn't need extra drivers for those operating systems, so they aren't available for download.  

Did you format the drive to ext3?  That could prevent Windows from mounting it.  Maybe [this]("http://www.fs-driver.org/") would work if you have.

---

### Post by Joeb454 on 2008-03-08
I'm thinking along the same lines as jetsam - what file system did you use to format it?

---

### Post by conehead77 on 2008-03-08
> **jetsam said:**
> The documentation on the site you linked to says the drive supports xp and vista.  I think it doesn't need extra drivers for those operating systems, so they aren't available for download.  

Did you format the drive to ext3?  That could prevent Windows from mounting it.  Maybe [this]("http://www.fs-driver.org/") would work if you have.

Omg, i feel stupid now! How could i miss this? I dont even remember formatting the harddrive. Maybe 2 operating systems are too much for me :lolflag:

---

