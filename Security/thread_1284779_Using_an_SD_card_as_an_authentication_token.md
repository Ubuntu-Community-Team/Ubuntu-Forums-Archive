---
title: "Using an SD card as an authentication token"
date: 2009-10-07
forum: Security
---

### Post by M4NIC on 2009-10-07
Hi

I want to create a secure way to login to an embedded system (running linux kernel 2.6.32-rc2). The actual device is a Marvell SheevaPlug. This does not have a keyboard but has an SD card slot.
I have read some guides for disk encryption and the use of external media (such as SD cards) for keys, so it can be done.

My question is, just for starts, can this be done without encryption? I basically want to authenticate to create some sort of action (a flag if you wish) that would direct various systems on the embedded device to operate. This should be done without user intervention, so a user timeline would look a bit like this:

1. Device powers up (systems dont operate)
2. User puts SD card-> authenticates -> triggers flag
3. Systems operate

I can give more details if interested :P

Cheers :D

---

### Post by Kobalt on 2009-10-07
I know [pamusb]("http://pamusb.org/") can do that with a USB stick, but don't know about an SD card...

---

### Post by M4NIC on 2009-10-07
thnx for the tip. I have tried to use it but it doesnt work. Ive continued this at the relevant thread [http://ubuntuforums.org/showpost.php?p=8069540&postcount=28]("http://ubuntuforums.org/showpost.php?p=8069540&postcount=28")

In the meanwhile are there any other SD specific projects?

---

