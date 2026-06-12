---
title: "smartctl and scsi drives"
date: 2010-07-07
forum: Server Platforms
---

### Post by lykwydchykyn on 2010-07-07
I have an old no-name "server" (more or less desktop components in a rack case with a SCSI card) which I'm trying to evaluate for a certain application at work.

I want to run some SMART tests on the drives, but I'm getting an error from smartctl when I attempt to launch either the short or long tests.

Here's the output:
```

$ sudo smartctl --all /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Device: ADAPTEC  RAID-5           Version: 370F
Device type: disk
Transport protocol: Parallel SCSI (SPI-4)
Local Time is: Wed Jul  7 13:12:38 2010 CDT
Device supports SMART and is Enabled
Temperature Warning Disabled or Not Supported
SMART Health Status: OK

Current Drive Temperature:     21 C
Drive Trip Temperature:        65 C
Manufactured in week 21 of year 2005
Recommended maximum start stop count:  10000 times
Current start stop count:      122 times

Error counter log:
           Errors Corrected by           Total   Correction     Gigabytes    Total
               ECC          rereads/    errors   algorithm      processed    uncorrected
           fast | delayed   rewrites  corrected  invocations   [10^9 bytes]  errors
read:          0       62         0         0          0      57550.945           0
write:         0        7         0         0          0       2473.982           0

Non-medium error count:      299
No self-tests have been logged
Long (extended) Self Test duration: 1479 seconds [24.6 minutes]

```

Now, trying to run tests:
```

$ sudo smartctl --test=long /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Long (extended) offline self test failed [badly formed scsi parameters]

```
```

$ sudo smartctl --test=short /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Short offline self test failed [badly formed scsi parameters]

```


I pretty much get that same "badly formed scsi paramters" error on most operations, apart from "--all".  Anyone know what I'm doing wrong here?

The SCSI adapter is an Adaptec SmartRAID V, it has 5 drives in a RAID 5 array.  The OS is 10.04 server.

Thanks.

---

### Post by lykwydchykyn on 2010-07-12
bump.... anyone?
If google is to be believed, I'm the only person in history to receive this error.  Loverly.

---

### Post by imwithid on 2011-01-18
You are not the only one. I get this when I try to enable SMART on my Samsung Spinpoint HM160HC. I have no idea what this means.

It's driving me crazy as I thought this drive had SMART capability (I should have known better and stuck to Western Digital or Seagate; Curiosity got the better of me to test one of these drives).

I wish I could help you. This is either a smartmontools error or a firmware limitation/error. If there is a firmware update, perhaps that may fix the problem. In my case, I suspect that this is a hard drive problem as I've had other connectivity problems with this drive (it does not like laptops when connected via USB, although I cannot be certain until I test it using a different OS; so far I have tested it using Ubuntu 10.04.1 x64).

---

### Post by disabledaccount on 2011-01-18
lykwydchykyn:
> The SCSI adapter is an Adaptec SmartRAID V, it has 5 drives in a RAID 5 array. Most of existing HW raid controllers, or fake-raids that are using proprietary software don't allow viewing SMART reports for particular array members. Instead You'll only get overview of **array** SMART condition, whatever that means. This is useless, but vendors still belive that they can predict hdd failure by checking SMART status.
This is also main reason why I prefer mdadm, and I'm using it everywhere, when it's possible.

imwithid:
I think that Your problem is completely different. You can try >hdparm -A on this samsung to check which functions are enabled.

---

