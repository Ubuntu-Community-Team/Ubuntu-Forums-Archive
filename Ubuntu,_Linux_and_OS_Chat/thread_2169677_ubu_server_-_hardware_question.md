---
title: "ubu server - hardware question"
date: 2013-08-23
forum: Ubuntu, Linux and OS Chat
---

### Post by torturednacho on 2013-08-23
So I'm running a dual core blah blah. 

A simple question I have. I tried tonight to put 3 SATA hard drives on the system. I was able to install the 500WD and the 1TB WD, however I wasn't able to get the system to recognize the additional 1 TB WD. 

I'm just wondering if there's something specific that I need to do in order for this to work. I'm going to update the bios, cause under the ACHI it only sees 2, but I'm not sure I checked it after I switched it from IDE to AHCI. 

Just wondering if this should just theoretically work without issues.

---

### Post by mastablasta on 2013-08-23
it could be that sata cable is bad or connection is bad. it can be as simple as that. hard to say with so little data.

---

### Post by torturednacho on 2013-08-23
> **mastablasta said:**
> it could be that sata cable is bad or connection is bad. it can be as simple as that. hard to say with so little data.

The cables are all brand new, the psu is brand new. 
I'm just looking for in theory this should work right. There's nothing I need to do other then make sure the mobo supports 3 hdds

---

### Post by cariboo on 2013-08-23
I'm ruuning an MSI G31M3-F V2, with a E5400 dual core cpu, the motherboard has 4 SATA ports, and I added another 4 port SATA pci board. My system is currently running 7 HDD with zero problems.

---

### Post by ikt on 2013-08-23
> **torturednacho said:**
> Just wondering if this should just theoretically work without issues.

Not just theoretically, there are millions of ubuntu systems with multiple hard drives. I myself have 2 x 128GB SSD's and a 2TB HDD.

> I'm going to update the bios, cause under the ACHI it only sees 2,

That to me makes it sound like a motherboard issue, if your BIOS sees all 3 hard drive, Ubuntu shouldn't have any issues.

Best of luck :)

---

### Post by torturednacho on 2013-08-23
> **ikt said:**
> Not just theoretically, there are millions of ubuntu systems with multiple hard drives. I myself have 2 x 128GB SSD's and a 2TB HDD.    That to me makes it sound like a motherboard issue, if your BIOS sees all 3 hard drive, Ubuntu shouldn't have any issues.  Best of luck :)   That's what I was thinking, I'm going to tinker around with it tonight and see what happens. I figured the mobo shouldn't have issues seeing the 3rd HDD .. then again I've miss calculated in the past.

---

### Post by tgalati4 on 2013-08-23
Dual Core Blah Blah machines have a limitation of 2 SATA drives when using combined IDE/SATA mode.

---

### Post by torturednacho on 2013-08-23
Well after a couple of beers, It looks like the HDD is dead. I haven't tested it in another setup but I did put it on the sata ports and using the sata cables that I know work and it wasn't recognized. I'll probably check to see if its actually dead alittle later.  Thanks everyone for the input!

---

### Post by torturednacho on 2013-08-23
> **tgalati4 said:**
> Dual Core Blah Blah machines have a limitation of 2 SATA drives when using combined IDE/SATA mode.  No IDE drives, I switched it to ACHI in the bios.

---

### Post by cariboo on 2013-08-23
> **tgalati4 said:**
> Dual Core Blah Blah machines have a limitation of 2 SATA drives when using combined IDE/SATA mode.

I use an ATA/IDE drive for a boot drive, and the other 6 are SATA, I didn't do anything special,just using the default bios settings, to use both interfaces, because there is only one IDE port, I'm limited to using 2 IDE/ATA drives.

---

