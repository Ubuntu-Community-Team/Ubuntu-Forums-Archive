---
title: "Windows 95 serious problems in VirtualBox"
date: 2013-04-14
forum: Virtualisation
---

### Post by createdcreature on 2013-04-14
Hi there!

I am using the latest version of Oracle VM Virtualbox, and I am running Win95 (without the Plus! add on), and am having massive problems. First, I should just tell you my configuration: 
VirtualBox knows it is Win95. 256MB RAM. Boot order: FDD, CD, HDD, Network. PAE/NX exposed to the VM. HAV and Nested Paging is turned OFF, like I have heard you should do. 32MB VRAM. 3D Accel. 2D Accel. No RDP server.
Controllers: IDE PIIX3 controller with 1 4GB HDD plugged in with Win95 installed on it, and one CD drive. One floppy controller with 2 Floppy drives. Both controllers are using Host I/O cache.
Sound set as SoundBlaster 16. Network set as NAT, with an AMD PC-NET PCI II card, with a unique MAC address, no port forwarding, and the cable connected. USB and serial ports are disabled. Shared folders are disabled as I do not have the guest additions (as they are not available). I have not written a description.

The problems: When I insert a floppy into any of the drives, and I click on the appropriate drive (A or B), it opens the disk (before I upgraded to 4.2.12 it said drive A was not accessible), but all I see is a bunch of unreadable, massive files (way more than 1.44MB) with funny names (see attachment). I am having even worse problems with CDs. When I open My Computer, even when I have a CD inserted, no CD drive shows up, and no CD drive shows up at the DOS prompt either. Add Hardware does not detect anything. Due to this CD problem, I cannot install the TCP/IP drivers, which means I cannot install the network card drivers, which means I cannot get on the internet. What's funny is that I installed Win95 from the CD in the first place!
Thanks!

---

### Post by sanderj on 2013-04-14
You have a computer with a floppy drive? Cooool! :)

---

### Post by createdcreature on 2013-04-14
I do have a computer with 1 floppy drive, but the floppy drives in the virtual machine is purely emulated, with no link to the physical one. The disks that you put in it are just disk images of floppy disks, with no connection to the real drive.

---

### Post by createdcreature on 2013-04-14
Anyone? I have looked on the Microsoft website, and the Virtualbox website, and there is nothing on this!

---

### Post by snowpine on 2013-04-14
I don't see it here:
[https://www.virtualbox.org/wiki/Guest_OSes](https://www.virtualbox.org/wiki/Guest_OSes)

also:

>  Support for Windows 95 ended in December 31, 2001.

[http://en.wikipedia.org/wiki/Windows_95](http://en.wikipedia.org/wiki/Windows_95)

---

### Post by andrew.46 on 2013-04-16
I have to admit that I am more than a little curious to know why you need Windows 95? I have a slightly nostalgic feeling about 95 as I remember installing it as an upgrade to Windows 3.11 for workgroups :)

---

