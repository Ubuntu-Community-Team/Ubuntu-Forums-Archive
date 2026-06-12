---
title: "Thic lient - how to set it up"
date: 2007-06-14
forum: Server Platforms
---

### Post by YigalB on 2007-06-14
I have Ubuntu 7.04 running on VMware on top of XP.
I would like to set a P3 machine, to boot from a floppy, to serve as thin client.

Any short guide line to do that?
are there any binaries for such floppy?
Can it also boot from A DiskOnKey to do that? (I have some old 8MB ones)

Thanks

---

### Post by elst on 2007-06-14
There are a few dedicated distributions for running on thin client systems, so you could use one of those - the first name that comes to mind is Thinstation, but Google will probably turn up several more. On the server end, VNC is more efficient than X, and most thin client distros should support it - the Ubuntu Wiki, or [www.google.com/linux](www.google.com/linux), will probably get you a VNC tutorial.

Having all the work of three operating systems happen on one disk drive will probably hurt a bit, but you probably figured that out already.

---

### Post by YigalB on 2007-06-15
Thanks, but it doesnt help.
For the server: I want to stick to Ubuntu 7.04, and activate the server only. I have read many articles, I just couldnt find the answer. There must be a single document with step by steo instructions, for dummies, how to do that.

For the client: I heard there are binaries ready for that. I just dont know where to get them from. again, a simple document telling how to prepare the diskette.

---

### Post by YigalB on 2007-06-17
Now that I used forums, I can clearly say that the documentation is not good - the data is there, but it is distributed in a terrible way. Now that I have server and 3 clients working at home, I can recommend the following guide lines for Ubuntu 7.04, it may be easier with Edubuntu: 
Topology:
- Have server with at least 512MB DRAM, better 1G. 
- Have two Network cards ("NICs"): one to the router to the web, the second one for a switch for all the clients (see entry A setup with two network cards in the server in [https://help.ubuntu.com/community/UbuntuLTSP/LTSPWiring](https://help.ubuntu.com/community/UbuntuLTSP/LTSPWiring) )

Bow run in server:
1- Install ubuintu 7.04 in the server
2- run: sudo apt-get install ltsp-server-standalone openssh-server
3- run: sudo ltsp-build-client

In client: 
- if the client has network-boot option(PXE) in BIOS, use it. If not: go make a floppy disk at [http://rom-o-matic.net/](http://rom-o-matic.net/) 
- note: you have to locate your NIC entry. This is not so simple. One way to do it is to run ScanPCI, by using a util you can easily find in google (search for SCANPCI). This util simply search for devices on the PCI bus. Find Network and see 2 items: Vendor ID and Device ID. these items should match the right entry in Rom-O-Matic. The rest there is "make a disk" or something like that, and burn it.
- in order to write the image you will need RAWWRITE from [http://www.chrysocome.net/rawwrite](http://www.chrysocome.net/rawwrite)
- Once you have the floppy ready, all you have to do is to boot the client with it, and pooof: it's supposed to work.

It may not work as well, since this guide is too short to be detailed enough. Here is where the great guys of #ltsp in #freenode which I was talking to in ChatIRC client (one of the applications you can easily install in Ubuntu).






Links:
[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

---

