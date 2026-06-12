---
title: "Strange SSD behavior"
date: 2012-04-30
forum: Server Platforms
---

### Post by Krupski on 2012-04-30
Hi all,

I bought a SuperTalent "CoreStore MP" board (PCI-X1 16GB solid state disk) to use as the boot drive in my Linux (Ubuntu) server.

[img]http://www.supertalent.com/largeImage/6_10056.jpg[/img]

The card has no BIOS, so it's not bootable. There are Windows drivers for it as well as Linux drivers, but no drivers for Ubuntu.

Strange thing is, right after upgrading my own computer to XUbuntu 12.04, the drive became visible on my machine (although it is NOT visible during an install). Apparently 12.04 now has the Marvell UMI driver included(?)

So, for the heck of it I took the disk image from my Ubuntu 12.04 server box, resized it to fit the CoreStore board and plugged the board into the server box (after removing it's usual boot SSD).

What the heck??? It WORKED!!!

Now, what has be baffled is this:

* It has no BIOS (not bootable)
* It needs drivers to be seen in Linux AND Windows
* The Ubuntu 12.04 install CD does not see it
* Yet with the OS pre-installed it works (i.e. boots up).

Anyone have any idea why this works???

---

