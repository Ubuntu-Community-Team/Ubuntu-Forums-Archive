---
title: "Ubuntu 11.10 on newest machine problem"
date: 2016-07-14
forum: Server Platforms
---

### Post by success127 on 2016-07-14
Hi, I am new in Ubuntu world. Recently we purchased a new server and we are required to install v11.10 into the server to be acted as proxy server. However, we faced problem installing into the server. It seemed that it does not detect the mouse (basic Logitech B100) and a message repeating over and over again 

udevadm[195]: timeout: killing '/sbn/modprobe -bv pci:v0008086d00008D62sv00008086sd000035C8bc01sc06101 [321] 

I am totally unsure what to do. The technical personnel suggested it is related to the onboard LAN which the Ubuntu 11.10 could not support. They were suggesting that we get a PCI network card instead. However, to my concern, buying a PCI network card would it solve the problem and more precisely, I asked them what network card model will be supported by v11.10.

This reason, I wrote to seek professional opinions on this issue of ours. 1) Does the error message above have to do with Network Card? 2) if so, what network card can be supported by 11.10? 

Btw, my motherboard is Intel Server Board S2600cw. Available PCIe is x8 and x16

Thanks

---

### Post by howefield on 2016-07-14
Thread moved to the "*Server Platforms*" forum.

By the way, Ubuntu 11.10 has long since passed its End Of Life and is no longer supported.

---

### Post by success127 on 2016-07-14
Yes, I understand about that. But our school required to use 11.10 to act as proxy server

---

### Post by darkod on 2016-07-14
I'm sorry, but that doesn't make much sense. Is it for compatibility, do they already have other proxy servers with that version and are afraid to use different one?

A proxy server in general is very basic and can work on any version. No need to insist on a version that is already EOL and will not have any security updates and fixes.

I would discuss it again with them and offer to install the latest LTS, the 16.04 or at least 14.04 LTS. Use only LTS releases (and 11.10 is not one of them, regardless whether it's EOL or not).

Another thing is, are you trying to install the server OS or the desktop OS on a server machine? You mentioned a mouse but the server OS by default is command line only. You don't need a mouse, and maybe because of that and because 11.10 is EOL it has issues detecting it.

---

### Post by MAFoElffen on 2016-07-16
Let me expand on that--

Being version 11.10 was an interim release from 5 years ago, those repo's are no longer where your install disk expected them to be (when that version was supported). So you can no longer do an update or upgrade. You can no longer install packages from the non-existent repo.

Your Intel Server Board S2600cw, even if you had the original version of that board, it would only be less than 1.5 years old... and has cutting edge hardware technology ... And since Ubuntu Server 11.10 was from 5 years ago... the newer hardware on that board didn't exist 5 years ago. We'll get back to that thought.

I could plus one on darkod's recommendation on installing an LTS version, but the earliest LTS version that is still in support is 12.04 LTS. There lies a challenge to that if you're using a old .deb package for your project. If it was packaged for kernel version 2.6 and is looking for what was then a kernel of 2.6.0 or newer ... kernel.org changed the kernel numbering scheme to allow kernel 3.x and newer, while I was testing in the 12.04 dev cycle.So if you have a package that was looking for kernel 2.6, you then might have to patch it to allow the 3.x and newer kernels. Note that 12.04 was kernel version 3.2.

If the .deb package does not look for kernel version and just looks for distro version, then you could just do a force on the version, and it should work with 12.04. 

If you are doing your own proxy work within Ubuntu Server manually, then was no difference in how you would do that between 11.10 and 12.04. If you were learning how to install and config a full featured proxy such as" Squid," there package name and how you configured squid was the same between 11.10 and 12.04 ... and Squid is still in the 12.04 repo's.

If you are doing a proxy, I don't see any change to your Professor's curriculum, if he just changes the version from 11.10 to 12.04 LTS. If he had just a bit of time to review, there would only be minor changes to update the curriculum to do the same on 16.04. The minor changes were that the package name changed from "squid" to "squid3", and init changed to a systemd service, so minor changes in how it's started, stopped, and on checking the status of. Basically beyond that, the config of details is fairly the same. The doc's are online in our wiki, our respective version Server Guides, and at [www.squid-cache.org](www.squid-cache.org).

That is... until you get back to your server board... as with networking, your onboard NIC and it's associated south bridge chipset might not be supported by 12.04.1 either, but may be on 12.04.5. It is supported by 16.04.

The question on your lan port error-- Your board has 2 internal 1 GbE Lan (intel i350 dualport controller) ports, and 2 10 GbE Lan (Intel x540 dualport controller) ports, i would think that error from 11.10 on your Lan ports are probably on those two 10 GbE ports. That technology did not exist 5 years ago. 12.04.5 might be be backported for that.

I don't recommend this but:
If neccessary, and if you still had  to do that with 11.10 ... and your if your instructor is still set in stone about that ... then tell him to there is a cost and a bit more work to make something old work on new hardware. First find the bus address of the offending NIC's and blackilst them from the boot process. That way the system will ignore them and not try to use them. Then go to Ebay and look for some: Intel® PRO/1000 PT Quad Port Server Adapter, P/N: EXPI9404PT or EXPI9404PTBLK. They  were made from 09/03/2009 through 12/31/2011. Those were supported by 11.10, it's kernel and it's related linux-firmware package. I just bought one on Ebay for $35. That card is PCI-E 8x and would be a good choice for a networking lab.

That would get the hardware working on 11.10. Then you would have to find whatever packages you would need, including all the related dependencies, and download them manually. Then install them locally.

---

