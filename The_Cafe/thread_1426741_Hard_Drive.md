---
title: "Hard Drive ?"
date: 2010-03-10
forum: The Cafe
---

### Post by soryu on 2010-03-10
Hello,  I'm Going To Upgrade My Hard Dive. Just Want To Make Sure Is IDE The Same As ATA? 
I Have An IDE Interface Drive.
(uwave mobo compaq)

---

### Post by Barrucadu on 2010-03-10
Yes; IDE is the cabling/connector standard, and ATA is the entire standard, encompassing IDE.

---

### Post by cgb on 2010-03-10
Barrucadu is correct that ATA is the standard used.  Be careful if you are looking at hard drives, for an IDE Cable, though that it states PATA (Parallel ATA) if you do not have any SATA (Serial ATA) connectors.

---

### Post by The Real Dave on 2010-03-10
If you can, why not buy a PCI SATA card, like [this]("http://www.amazon.co.uk/Port-SATA-Card-Controller-Chipset/dp/B000MR7SNS/ref=pd_cp_ce_0") cheap one I picked up, so that you can connect a SATA drive to your computer? SATA drives are much cheaper per Gb, faster, cooler, and will be more useful to you in the future.

---

### Post by soryu on 2010-05-31
got my new drive but it doesnt power on.
tried Different settings (jumpers)and no go.
It's A E-IDE Should Be compatible,right?
anything im missing?

---

### Post by handy on 2010-05-31
> **soryu said:**
> got my new drive but it doesnt power on.
tried Different settings (jumpers)and no go.
It's A E-IDE Should Be compatible,right?
anything im missing?

E-IDE is fine.

Have you set your BIOS to enable this 2nd drive?

You will have to set it's jumbers as master/slave, depending on which of the 2 IDE channels you are using it. 

If you have an optical drive, set it to be slave & set your new drive to be master, both on the Secondary IDE channel. If you want to use it on the same channel as your boot drive (Primary channel), then it will have to be set as slave.

---

### Post by coolbrook on 2010-05-31
> **The Real Dave said:**
> If you can, why not buy a PCI SATA card

In fact I would take some of the the difference in cost between the IDE and the SATA drive and get a good SATA card that supports more than one drive and at least 3.0 Gbps transfer rate, which is probably what you'll find in a new drive.

EDIT: Just realized that this was an old thread.

> got my new drive but it doesnt power on.

Is it hooked up to your power supply.  If so, then have you tried another cable from the power supply?  It should get some power and be recognized in your BIOS.

---

### Post by lindsay7 on 2010-06-01
Run Gparted and see if it sees your new drive.  You may need to partition it and format it first or the computer may not recognize it.

---

