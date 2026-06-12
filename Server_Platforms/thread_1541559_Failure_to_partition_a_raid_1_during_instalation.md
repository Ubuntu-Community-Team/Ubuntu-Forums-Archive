---
title: "Failure to partition a raid 1 during instalation"
date: 2010-07-29
forum: Server Platforms
---

### Post by tangerine0469 on 2010-07-29
I have built a small test server. i am planing on using this machine a an email and web server to test out its hosting capacities. in the future i will build a larger and more well equipped version. 

amd athlon x2 2.0ghz
2 160gb sata drives (hardware raid 1, done through the Motherboard)
2 gb ram (dual channel)

like i said small test server.

i am trying to install 10.04 server edition. when i get to the point of partitioning it asks me to activate the raid so i do. i get through the guided partitioning and get ready to write the file system to the drives and the screen goes red and says that it has failed. what am i doing wrong.

on a side note, this works if i install it on the same drives without any raid configuration. any help would be greatly appreciated.

---

### Post by sahabcse on 2010-07-29
How did u configure the hardware RAID? Using server setup installation CD or any other method??

---

### Post by tangerine0469 on 2010-07-29
my motherboard ahs an nvidia raid controller built into it. i turned it on via the bios and then hit the hotkey to go into the controller at post and set up the raid there.

---

### Post by jacekk015 on 2010-07-29
Think twice about using that motherboard pseudo-RAID. If you really think that's a hardware RAID you are wrong.
Better use mdadm / linux software RAID. Both of them are using your CPU.

One of the disadvantages: what will you do if a 6 months later you motherboard will die?
Will you be able to recover your data ??

---

### Post by tangerine0469 on 2010-07-29
probably not, thats why i will back everything up to a couple of externals. again this is a test, so maybe the raid is just overkill i guess.

---

### Post by flatline on 2010-07-29
> **jacekk015 said:**
> Think twice about using that motherboard pseudo-RAID. If you really think that's a hardware RAID you are wrong.
Better use mdadm / linux software RAID. Both of them are using your CPU.

One of the disadvantages: what will you do if a 6 months later you motherboard will die?
Will you be able to recover your data ??

Agreed - onboard RAID controllers aren't really hardware RAID.

Are you trying to boot off a RAID1 done in the motherboard?  It probably depends on the motherboard, but I'm almost sure this is impossible in Linux, or at least sufficiently difficult that I have no idea how to help you.  Since you're going to be using the CPU for the RAID either way, I highly recommend setting up the RAID in software using the partition tools on the CD.

Actually, my real recommendation would be to put the OS and everything on a single drive, but I understand you probably want it all mirrored for reliability reasons?

From wikipedia:
Hardware RAID controllers are expensive and proprietary. To fill this gap, cheap "RAID controllers" were introduced that do not contain a RAID controller chip, but simply a standard disk controller chip with special firmware and drivers. During early stage bootup the RAID is implemented by the firmware; when a protected-mode operating system kernel such as Linux or a modern version of Microsoft Windows is loaded the drivers take over.

These controllers are described by their manufacturers as RAID controllers, and **it is rarely made clear to purchasers that the burden of RAID processing is borne by the host computer's central processing unit, not the RAID controller itself**, thus introducing the aforementioned CPU overhead from which hardware controllers don't suffer. Firmware controllers often can only use certain types of hard drives in their RAID arrays (e.g. SATA for Intel Matrix RAID), as there is neither SCSI nor PATA support in modern Intel ICH southbridges; however, motherboard makers implement RAID controllers outside of the southbridge on some motherboards. Before their introduction, a "RAID controller" implied that the controller did the processing, and the new type has become known by some as "fake RAID" even though the RAID itself is implemented correctly.

---

### Post by ruffEdgz on 2010-07-29
> **tangerine0469 said:**
> probably not, thats why i will back everything up to a couple of externals. again this is a test, so maybe the raid is just overkill i guess.

I think you answered your own question :D

If you just want to see what it looks like, that's cool but I would prefer using the software RAID over the motherboard version any day and the hardware RAID controller over both options mentioned above.

I would play more with the software RAID and if you have any questions about that, we can help you there ;)

---

