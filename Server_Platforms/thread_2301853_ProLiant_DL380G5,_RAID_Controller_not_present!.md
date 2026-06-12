---
title: "ProLiant DL380G5, RAID Controller not present!?"
date: 2015-11-05
forum: Server Platforms
---

### Post by n.e.t.gallatin on 2015-11-05
I have a ProLiant DL380G5 that was given to me, but recently it decided not to boot. So I started investigating, and there were no arrays, or raid controller present in the BIOS or through the POST. I reset the BIOS, and still nothing. Placed several linux CD's in, an nothing as far as RAID, Arrays, or even Hard Drives.

Does anyone one have any experience with this model of server, and/or advice on how to get this thing up and running?

S/N - AUB80400GN

---

### Post by darkod on 2015-11-05
You say it recently decided not to boot. Do you have data on the disks or you wanted to install ubuntu just now?

Are we talking about data recovery or just about making the empty server boot?

---

### Post by n.e.t.gallatin on 2015-11-05
It does not have any data I want to recover.

---

### Post by darkod on 2015-11-05
In that case, are you sure the raid card is not dead? If even the bios doesn't see it, it has nothing to do with the OS (linux, windows)... The card might be dead. With linux you have the option to use software raid, which many people prefer compared to HW raid. In such case you don't need to configure arrays in the card bios but the card has to be working at least to be passing on the disks to the system. The arrays are configured within the OS.

You need to play around with the HW, maybe even try to attach the card to another machine and see if it detects it. Check connections, unplug the card then plug it in, etc...

---

### Post by n.e.t.gallatin on 2015-11-06
Thank You! I reseated the PCIE card and the Riser Cage, and the P400 controller now registers. Problem 1 solved!

The card seems bad. on some boots, its detected, on others its not detected.

---

