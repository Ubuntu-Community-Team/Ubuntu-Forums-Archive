---
title: "Ubuntu Server 18.01 LTS Curtin command block-meta Error"
date: 2018-08-08
forum: Server Platforms
---

### Post by lee42 on 2018-08-08
Hi all

Ive just removed all partitions from a hard drive I previously had server 14.04 installed on

Tried installing 18.04 Server from scratch and using the use whole disk option but I get the above error all the time

Curtin command block-meta Error

Ive tried going to shell after that but that fails too - blank cursor

Anyone have any clue wot is the cause?? Been stuck for months and can find much yet

Thanks all

---

### Post by LHammonds on 2018-08-08
Are you using the default "LIVE" server ISO or the alternative ISO?  The "LIVE" ISO tries to emulate the desktop installer and give you less options when installing.  I always using the "alternative" image.

You might be having compatibility issues or have hardware errors.  Load up the "LIVE" desktop DVD and do a "try before install" to see if it will boot up on the hardware before trying to install on it.

I would also run some RAM and HDD diagnostics to rule out the hardware having failure issues.

LHammonds

---

