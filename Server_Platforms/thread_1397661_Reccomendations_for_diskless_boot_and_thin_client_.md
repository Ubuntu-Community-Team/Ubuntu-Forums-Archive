---
title: "Reccomendations for diskless boot and thin client server?"
date: 2010-02-03
forum: Server Platforms
---

### Post by CyberAxe on 2010-02-03
I'm looking for suggestions and comments on how to setup a thin client server within ubuntu server so i can plan it out properly

I volunteer for a charity organisation as IT Admin

At the moment the network is just a group of around 20 old donated PC's and Macs (between 800mhz and 1.5ghz with between 128 and 512mb ram) however it looks like we are getting funding to buy some new ones and I have put together a list of components for them, running an AMD 3200+ and 1GB of ram each.

Also planned out a server as the current one we have is fine for what it does (which is mainly DHCP, Firewall, Samba Sharing and what not) but i would like to be able to put a good web interface on it (mainly so the staff who aren't that knowledgeable about computers can add block rules to filter out website urls, and the last time i tried it on the current hardware it slowed to a crawl) and would like to run all the computers operating systems from the server itself.

I'd like to be able to serve Win XP Home images, mainly because we would like to run some windows media programs like photoshop and such on them (and that's one of the apps I've never had much success with in wine)

I'd like to run the old computers as thin clients so that all the processing and such is handled by the server and the newer more powerful computers as diskless boot clients since they have more than enough power to run everything locally but would like to be able to use the same windows image for both solutions if possible so regardless of the computer the end user experience would be pretty much the same, plus it would make it easier for me to configure the windows environment.

another feature that would be nice (but unsure if its possible) as the people come and go over a period of about 3 months is to have user accounts per person all the documents and such that they saved are stored to a folder on the linux server that named by that users username, so that the staff can keep an eye on what files have been downloaded by each user and have easy access for working with them, then the account gets deleted automatically after a period of like 4 weeks inactivity but the files are kept

the current hardware for the server i was thinking of was 

CPU: AMD Athlon 64 X2 6000+ (3GHz) Socket AM2 L2 2MB
Motherboard: MSI 770T-C45
MEM: 2x 4GB Kingston RAM DDR2 (cant remember the exact type at the moment)
HD: 1TB ecogreen hard disk

Dunno if that will be powerful enough or not.

Thanks

---

### Post by CyberAxe on 2010-02-03
I just read up on Xen on the ubuntu docs, just wondering how much I'd be able to do with that of what i want to do, and if the hard ware above is adequate or will i need a server with a newer cpu such as the phenom II with the newest virtualization architecture

Thanks

---

### Post by xpertuse on 2011-02-16
Hello, sorry to "dig up" this post but I am in the process of doing almost the same project. Did you have any luck?

---

### Post by tgalati4 on 2011-02-16
Since we are turning the soil here, I've had good luck with freenas for file storage and media serving on older hardware.  Turn one or two of those machines into freenas servers and it will immediately add to the capability of the network.  You don't need much RAM or processing power, just add some newer disks.  Since the price of hard disks has dropped, it's an affordable solution that will work with mac, windows or linux pc's.

I'm not sure how Xen would fit into the picture.  Xen is for running several different servers or operating systems at once.  It requires some serious hardware and lots of RAM.  Basically think enterprise-class server with 8GB of RAM or more.  Not that you can't find some good condition, used, business-grade servers on craigslist or ebay.  

I would take the old, donated hardware, and scavenge enough RAM to make decent Ubuntu desktop machines 256MB minimum with 256MB swap minimum or 512MB RAM if you have enough slots or dense-enough RAM sticks.  PIII, 500 MHz or better.  Anything less, I would either build an Ubuntu Lucid server (PII) or freenas server (PI) and hang them off of the network as the backbone of your computing infrastructure.

---

### Post by xpertuse on 2011-02-17
> **tgalati4 said:**
> Since we are turning the soil here, I've had good luck with freenas for file storage and media serving on older hardware.  Turn one or two of those machines into freenas servers and it will immediately add to the capability of the network.  You don't need much RAM or processing power, just add some newer disks.  Since the price of hard disks has dropped, it's an affordable solution that will work with mac, windows or linux pc's.

I'm not sure how Xen would fit into the picture.  Xen is for running several different servers or operating systems at once.  It requires some serious hardware and lots of RAM.  Basically think enterprise-class server with 8GB of RAM or more.  Not that you can't find some good condition, used, business-grade servers on craigslist or ebay.  


I've turned an old server with 2 500Gig disks in mirroring mode into a storage with freenas in a few clicks.
Then you can create luns to provide an extra storage to a Xenserver.
But I don't think that it was the issue here. 
He wanted somehow to be able to use diskless PCs and have them to boot an XP image on a Ubuntu 10.04 server through PXE. 
That is exactly what I am trying to do now with no luck.. Any help would be appreciated.

---

### Post by koenn on 2011-02-17
you can't run Windows XP disklessly. You might be able to have a diskless thin client run an rdp client or a web-based UI to a virtual machine, but that still means you need several instances of XP (virtualized or on real hardware) running somewhere. 
You also can't have multiple users use the same XP simultanously, for licensing reasons and because XP's rdp only allows 1 active user (even though it's technically a mukti-user system).


There's also this : [http://msdn.microsoft.com/en-us/library/ms838569%28v=winembedded.5%29.aspx](http://msdn.microsoft.com/en-us/library/ms838569%28v=winembedded.5%29.aspx) 
but I doubt that'll work on a linux server.

---

### Post by jvin248 on 2011-02-17
You'll want to run an LTSP setup with what you describe (see LTSP.org for background).

Take your most powerful machine and load up with disks and Ram, install Ubuntu Server, then run:

$ sudo apt-get install ltsp-server-standalone openssh-server
$ sudo ltsp-build-client
$ sudo nano /etc/ltsp/dhcpd.conf   [change the IP addresses to your LAN domain]
$ sudo invoke -rc.d dhcp3-server restart  [syntax here may be old]
$ ifconfig  [to check the IP setup looks right]
$ sudo ltsp-update-sshkeys

The client machines can be your P2's and P3's with 128MB ram and diskless. A little more ram can be helpful but going above 256MB won't gain anything.  The server doesn't need to be a monster either, I've even run a P2-450Mhz 512MB ram desktop with two LTSP clients linked into the LTSP server I'd installed on it back when Kubuntu 6.10 was fresh.  Brother of mine runs LTSP on a smallish server for 5 kids at his house.

If your older client pcs cannot do PXE booting on their own then look up "romomatic" and the site has a floppy disk image to match most ethernet cards.  Leave a floppy disk in the client (remove HDD and CDs), boot the romomatic image that kicks the machine into the LTSP environment.  By the way, note that LTSP only works across ethernet, the clients cannot connect via Wifi, usually not a problem to run wires.

The other suggestion for creating a FreeNAS box to hang on the network is good too.  I've also had success with pfSense for routing/firewall/etc.  And FreeSCO has worked well on really old hardware to either be a router or just use the print server function if your printers don't have ethernet.

there's an IRC channel for LTSP discussion and the people there are very helpful if you get stuck.

---

### Post by xpertuse on 2011-02-18
> **koenn said:**
> you can't run Windows XP disklessly. You might be able to have a diskless thin client run an rdp client or a web-based UI to a virtual machine, but that still means you need several instances of XP (virtualized or on real hardware) running somewhere. 
You also can't have multiple users use the same XP simultanously, for licensing reasons and because XP's rdp only allows 1 active user (even though it's technically a mukti-user system).


There's also this : [http://msdn.microsoft.com/en-us/library/ms838569%28v=winembedded.5%29.aspx](http://msdn.microsoft.com/en-us/library/ms838569%28v=winembedded.5%29.aspx) 
but I doubt that'll work on a linux server.

Thanks for the info.

---

### Post by rvchari on 2011-02-18
> **CyberAxe said:**
> I'm looking for suggestions and comments on how to setup a thin client server within ubuntu server so i can plan it out properly

I volunteer for a charity organisation as IT Admin

At the moment the network is just a group of around 20 old donated PC's and Macs (between 800mhz and 1.5ghz with between 128 and 512mb ram) however it looks like we are getting funding to buy some new ones and I have put together a list of components for them, running an AMD 3200+ and 1GB of ram each.

Also planned out a server as the current one we have is fine for what it does (which is mainly DHCP, Firewall, Samba Sharing and what not) but i would like to be able to put a good web interface on it (mainly so the staff who aren't that knowledgeable about computers can add block rules to filter out website urls, and the last time i tried it on the current hardware it slowed to a crawl) and would like to run all the computers operating systems from the server itself.

I'd like to be able to serve Win XP Home images, mainly because we would like to run some windows media programs like photoshop and such on them (and that's one of the apps I've never had much success with in wine)

I'd like to run the old computers as thin clients so that all the processing and such is handled by the server and the newer more powerful computers as diskless boot clients since they have more than enough power to run everything locally but would like to be able to use the same windows image for both solutions if possible so regardless of the computer the end user experience would be pretty much the same, plus it would make it easier for me to configure the windows environment.

another feature that would be nice (but unsure if its possible) as the people come and go over a period of about 3 months is to have user accounts per person all the documents and such that they saved are stored to a folder on the linux server that named by that users username, so that the staff can keep an eye on what files have been downloaded by each user and have easy access for working with them, then the account gets deleted automatically after a period of like 4 weeks inactivity but the files are kept

the current hardware for the server i was thinking of was 

CPU: AMD Athlon 64 X2 6000+ (3GHz) Socket AM2 L2 2MB
Motherboard: MSI 770T-C45
MEM: 2x 4GB Kingston RAM DDR2 (cant remember the exact type at the moment)
HD: 1TB ecogreen hard disk

Dunno if that will be powerful enough or not.

Thanks

a) you will need a thinclient card (something that has a rom and linux boot files are on the rom). next all the machines on client side needs to be set as first boot on network so that linux native boot takes place from the boot rom of thin client card. on the gui screen it will be configured to boot from server where in you will need to key in the username and password to get access to server.... these chips are readily available from various vendors (atleast here in india where i live, they usually supply a native linux boot and from the screen you can log on to server - win or linux)

thin client pcs hardware is not much of a matter. server hardware is what will take care of all the users... (more the users, more the load on server...)

next is a switch (depends on how many clients you wish to connect)

finally cabling thru the switch (add one port on the switch to accomodate your internet connection that can be shared / blocked among various users)

pardon my plain non techie language as i am sharing my set up on how we got it done at our place. we have 4 thin clients (3 thin clients that were purchased without hdd and 2 antique pcs that were fit with thin client card) server runs windows and all thin clients natively boot from linux and then we log on to server with respective username.

hope my simple rendering of my experience will be of help to you

---

### Post by xpertuse on 2011-02-18
> **jvin248 said:**
> You'll want to run an LTSP setup with what you describe (see LTSP.org for background).

Take your most powerful machine and load up with disks and Ram, install Ubuntu Server, then run:

$ sudo apt-get install ltsp-server-standalone openssh-server
$ sudo ltsp-build-client
$ sudo nano /etc/ltsp/dhcpd.conf   [change the IP addresses to your LAN domain]
$ sudo invoke -rc.d dhcp3-server restart  [syntax here may be old]
$ ifconfig  [to check the IP setup looks right]
$ sudo ltsp-update-sshkeys

The client machines can be your P2's and P3's with 128MB ram and diskless. A little more ram can be helpful but going above 256MB won't gain anything.  The server doesn't need to be a monster either, I've even run a P2-450Mhz 512MB ram desktop with two LTSP clients linked into the LTSP server I'd installed on it back when Kubuntu 6.10 was fresh.  Brother of mine runs LTSP on a smallish server for 5 kids at his house.

If your older client pcs cannot do PXE booting on their own then look up "romomatic" and the site has a floppy disk image to match most ethernet cards.  Leave a floppy disk in the client (remove HDD and CDs), boot the romomatic image that kicks the machine into the LTSP environment.  By the way, note that LTSP only works across ethernet, the clients cannot connect via Wifi, usually not a problem to run wires.

The other suggestion for creating a FreeNAS box to hang on the network is good too.  I've also had success with pfSense for routing/firewall/etc.  And FreeSCO has worked well on really old hardware to either be a router or just use the print server function if your printers don't have ethernet.

there's an IRC channel for LTSP discussion and the people there are very helpful if you get stuck.

OK, and the clients will have what? Linux or even XP. How? Don't I have to install a client image somewhere?

---

### Post by headvampyre@hotmail.co.uk on 2011-02-21
The client image (if your booting ubuntu via THIN/FAT) is generally stored in /opt/ltsp/i386 (/opt/ltsp/amd64 if your running a 64-bit OS and didnt configure the client to build a 32-bit OS). The images are built using the ltsp-build-client command.

---

### Post by koenn on 2011-02-21
> **headvampyre@hotmail.co.uk said:**
> The client image (if your booting ubuntu via THIN/FAT) is generally stored in /opt/ltsp/i386 (/opt/ltsp/amd64 if your running a 64-bit OS and didnt configure the client to build a 32-bit OS). The images are built using the ltsp-build-client command.

the OP is looking for ways to run _WinXP_. I doubt ltsp-build-client will build those, and if it could, I doubt LTSP would be capable of serving them in a bootable manner.

---

### Post by xpertuse on 2011-02-23
> **koenn said:**
> the OP is looking for ways to run _WinXP_. I doubt ltsp-build-client will build those, and if it could, I doubt LTSP would be capable of serving them in a bootable manner.

You are right. The ltsp-build-client doesn't build XP images...
So what? Dead end?

---

### Post by koenn on 2011-02-23
> **xpertuse said:**
>  Dead end?
no, different direction. 

Like I said before, you can look into virtual desktops, or Windows Terminal Services or something like that (maybe even something "cloudy" - see what Eucalyptus has to offer). That does mean you're going to need a server that can handle this stuff.

In such scenario, your clients only need to be able to run nothing more than a remote desktop client, or a client for the virtualization platform (eg with VMware Server, you could simply use a web browser). That's light, so your old PC's can handle it easily. It's up to you whether you want to set this up with PXE boot, completely disklessly, or from a locally installed (stripped down) OS. 




2nd option : forget XP, switch to (X)Ubuntu desktops or one of the lightweight respins, and decide whether you want this through LTSP or installed locally.
Before you do that, be very sure you can meat all functional requirements (in terms of software, support, training, self-help skills of your target audiance, ...)



--- 
Edit
sorry, confused you with the OP, so the hardware stuff etc might be off - but the general idea stands.

---

### Post by headvampyre@hotmail.co.uk on 2011-02-23
Couldnt you boot the clients into ltsp-kiosk but modify the ltsp image to run a virtualbox image instead of firefox?

---

### Post by CyberAxe on 2011-03-02
Thank's for the info, I hadn't actually found a solution though mainly due to being too busy to try and find one.

I did start working on setting up an Ubuntu environment via KVM which i was able to VNC into from my PC to start installing and interacting with but i got no further than installing it.

The older hard computers do have hard disks in them and I don't mind installing some form of software onto them just to get them to boot into the server.

I still need to run XP or some form of windows for certain instances but I can move over to Linux for the majority of the time since most of what the computers are needed for are only internet access.

Though sometimes our clients who use the computers do need to make presentations and such and they can barley use Powerpoint let alone any open/libre office.

Most of the old macs have gone, but would still be able to do this on the ones that are left too, we also have several newer PC's which rather than have vnc into would be nice to just serve them a pre installed image if they dont have it already cached on their local hard disks for example run the OS from it, which if is updated the updated image is downloaded from server and ran, would make administrating the computers far simpler.

In general as at the moment everything is very locked down XP Home OS's and everytime i need to make simple changes i need to go on each one and go into the admin account then remove all restructions on the limtied account load back onto limited acount makes changes back to admin and restore restructions, which is somewhat annoying and time consuming as i'm sure you can imagine and makes setting up new PC's time consuming aswell.

I'll certainly look into the info provied, thanks.

---

