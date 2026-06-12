---
title: "DL360p E5-2690 slower than expected"
date: 2014-02-12
forum: Server Platforms
---

### Post by Pontus_Uggla on 2014-02-12
I have just installed ubuntu 12.04 server on our new DL360p Gen8 E5-2690, but it generates a lamp-site slower than my iMac running os x.

The website runs about 20 queries on a normal load, if I reload both pages they load about equally fast, ~50 ms, but on first load the iMac is sometimes twice as fast, 100 vs 200 ms.

The iMac has an ssd, the hp server has 8 1.2 TB 10rpm raid 5.
The iMac has an i7 3.5Ghz, the hp has two 2.9GHz with 8 cores.
The iMac has 24 Gb ram, the server 64 Gb.

Running the website on my iMac in ubuntu using vmware renders the page 30 % faster than when using os x.

Is this expected? Is there something I´m missing?

---

### Post by Bucky Ball on 2014-02-12
*Thread moved to **Server Platforms**.*

Welcome. You might have better luck here. You might also try a more descriptive title by editing the first post and 'Go Advanced'. ;)

---

### Post by volkswagner on 2014-02-12
You may be seeing an advantage due to SSD.

Have you compared raw disk performance on the two servers?

[dd]("https://romanrm.net/dd-benchmark") can offer some insight.

---

### Post by brokenhachi on 2014-02-12
To add on to the above: Raid5 will also slow down disk performance. If you have 8 drives, maybe you can try Raid1+0.

---

### Post by Pontus_Uggla on 2014-02-13
The reason i use raid 5 is because I need the storage. I was hoping to fit it all in 1U, but I can go back to the plan of having a d2700 with the 1.2TB disks and buy smaller faster disks to put in the machine.

Do you know if I need an extra raid card for this or is it enough with a sas card and use the P420i for both?

Would you go raid10 with 4 146GB 15K SAS or raid1 with 2 100GB 3G sata ssd:s, like this one [http://www.amazon.com/HP-636621-B21-Internal-Solid-State/dp/B005ZXYQOI](http://www.amazon.com/HP-636621-B21-Internal-Solid-State/dp/B005ZXYQOI)

---

