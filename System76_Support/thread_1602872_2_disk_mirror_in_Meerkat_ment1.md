---
title: "2 disk mirror in Meerkat ment1?"
date: 2010-10-22
forum: System76 Support
---

### Post by jpv on 2010-10-22
I have a Meerkat ment1 with a 2TB WD green drive, but no optical drive.  I'd like to get another drive and set up a Linux software mirror.

I've tried a regular 3.5" drive and aside from the fact that the bracket is set up for the optical drive I don't have, it won't physically fit under the cover anyway.

There is a SATA port and a SATA power cable (again for the optical I don't have), so I was thinking maybe I could put a 2.5" drive in there.  But it looks like they only go up to 1TB and I'd need 2TB.  I'm also hazy about the SATA cable or connector.

For various reasons I don't want to use any kind of external disk, and I'm not sure doing a mirror to an external disk is a Good idea anyway.

Anyone have any other ideas?

Thanks,
JP

---

### Post by P4man on 2010-10-22
Those sata connectors ought to work, laptop drives have the same connectors as desktop ones, but I dont think you will be able to cram another hdd in the space for a slimline DVD. Even if you could, I would worry a bit about the 80W powersupply your machine comes with. Hdd's dont consume all that much power, but 80W doesnt leave much headroom either, especially not for a fast desktop drive.

I think your best option is an external drive, but that will come with a performance penalty, regardless if you use USB or a NAS.  In both cases you will get at best around 40MB/s (with most NAS's even a lot less than that), and raiding it with a sata drive is probably not going to help performance.

One last thought; you dont need identical sizes for software raid. You could buy a 1TB laptop drive and if you manage to put it in, create a raid array with the new drive and a 1TB partition on your 2 TB drive, and have the remaining 1 TB not raided.

No solution seems optimal though. I would buy an external drive or NAS (if you want to put it away from the desktop) and make periodical backups or rsync and forget raid.

---

### Post by P4man on 2010-10-22
Well, maybe you can fit a hdd in there after all. Have a look here:
[http://forum.notebookreview.com/sony/469244-z11-replace-dvd-hdd-working-solution.html](http://forum.notebookreview.com/sony/469244-z11-replace-dvd-hdd-working-solution.html)

I dont know if your machine has a micro sata connector for the DVD (I think not from what you wrote?) but something like the above could be doable.

---

### Post by jpv on 2010-10-22
> **P4man said:**
> I think your best option is an external drive,...

Not an option in this case.


> **P4man said:**
> One last thought; you dont need identical sizes for software raid. You could buy a 1TB laptop drive and if you manage to put it in, create a raid array with the new drive and a 1TB partition on your 2 TB drive, and have the remaining 1 TB not raided.

Yeah, I thought of that.  But the point of the 2TB drive was to have...2TB.  And the point of mirroring is to mirror all of it.  Sigh...

Thanks for the sanity check!

---

