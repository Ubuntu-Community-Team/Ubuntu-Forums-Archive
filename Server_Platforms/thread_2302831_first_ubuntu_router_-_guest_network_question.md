---
title: "first ubuntu router - guest network question"
date: 2015-11-13
forum: Server Platforms
---

### Post by sajansen on 2015-11-13
hey, its been a long time for me since i worked with ubuntu so im more then rusty at it... not to mention i wasn't the best ... but now im working on a little project to make a router out of a msi computer i have and wasn't using to often... i want to make a router out of it so i can skip out on paying like 150 for a new router thats at least a bit functional... (i do have a server running for websites and email and stuff) so it has to be secure as well

well onto the project... ive setup a ubuntu server 15.10 with 2 network cards, one going to internet and one going to my internal network... (not yet though... for now its connected to my existing network instead of directly to the internet so i can configure it and test tings out) ... so far so good... i have forwarding, dhcp and firewall running and it looks stable... my idea is to use some old routers as access-points to split up the wired network into wireless... also this is working fine... but now i have the question if its possible to make some sort of guest network available ... like every pc/tablet/whatever needs to login the first time it connects and based on mac address or something it should have just internet or full access... thing is, i have no idea how to make that work (also just now thinking... i do have media players and tvs and stuff that also need full access so it would be nice of i could add mac-addresses by hand... because not everything has the ability to go to a site and logon...... i herd something about pfsense... thy used it at a lanparty i go to and it looked nice... but to get it integrated into my router... i have no idea how to do it... Also what would be a option is just a mac filter for access... that i manually add things in and everything thats not in the list gets just internet...sounds easier to setup and manage... and maybe speed limits for guests... just to troll :P

also i have some problems with starting a .sh script at boot... somehow it wont run... i can run it manually just fine but that's not really what i had in mind... the file is in the attachments. if someone could help and tell my why its not starting at startup... i tried copying it to /etc/init.d/ and making a link to some folder i cant remember :P and it was picked up but at startup i got a "failed" instead of a "ok" and it was just not ran... 

well if you got to this part... thanks for reading everything,
Sander

---

### Post by TheFu on 2015-11-13
Skip the DIY solution, at least until you are better with Linux networking and have some more security knowledge.  Setting up a secure Linux router is non-trivial when starting from full Linux distro.   Every extra program is another risk to the  network.

You want **pfSense** or some other prebuilt router distro. Ask your professional network security friends about pfSense  - ones with a CISSP cert who are part of ISSA.

pfsense is a complete distro.  You load it like you load linux.

---

### Post by sajansen on 2015-11-13
i'm trying out pfsense now... my internal nic is supported but not my usb one that i need for the internet connection... i know its not ubuntu anymore... but does someone know how to get this driver in? : [COLOR=#505258][FONT=MyriadProRegular]RTL8153

as a alternitive im going to look for another usb 3 nic that hopefully has a supported chip... but im guessing its going to be hard to fiend some...[/FONT][/COLOR]

---

### Post by tripp98 on 2015-11-14
try untangle.  They have good nic support.

---

### Post by TheFu on 2015-11-14
> **tripp98 said:**
> try untangle.  They have good nic support.

There must be 10+ linux-based x86 router distros. I've never used them.

pfSense is BSD-based, so HW support is limited to the best hardware for the task. The BSD network stack is considered the worlds best. USB as a router NIC isn't a good idea; too much latency. Get a quad-port Intel PRO/1000 to make this the best router under pfSense.  A single-port PRO/1000 is $25 and THE industry standard.

Save the USB-to-eth adapter for a chromebook.

---

