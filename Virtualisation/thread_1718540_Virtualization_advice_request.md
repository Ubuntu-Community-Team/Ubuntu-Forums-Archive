---
title: "Virtualization advice request"
date: 2011-03-31
forum: Virtualisation
---

### Post by Sternfan on 2011-03-31
Hi all,

I have a network admin friend that is planning on moving all his desktops to win7 (sometime next year, so there is time).  We talked about it in reference to cost (it is a non-profit without much money) for new hardware etc.; and I threw out the idea of virtualization.  So this post is me looking for advice that I can pass on.

Scenario:
•	About 100 desktops (about 50 concurrent connections during the busy time of the day)
•	Servers – mixed bag – Dell pe1750, pe1850, pe2650 etc.  When all said and done, probably 6-10 rack servers available.  These are older (though in great shape) without virtualization-supporting CPU’s.  They can be maxed out in RAM however.
•	Storage – looking at a 8tb NAS (rack) – running raid 

Goals:
•	High-availability – servers in a cluster?  
•	Ability to add servers to the cluster as needed.
•	Shared resources (servers sharing workload) – once again – cluster?

Notes:
•	Just checking a few things on the internet, since the CPUs are not intel-vt capable, the options are limited.  I am assuming that XEN, KVM and ESXi are out?
•	Do ubuntu clusters share resources?  Or just for failover?
•	Ubuntu cloud – from what I can tell the VMs can only be Ubuntu?  No win7?

Any and all comments, advice, etc. greatly appreciated.

Rob

PS – if anyone has any books to recommend on this, please let me know.

---

### Post by ronnieredd on 2011-03-31
Take the 100 machines that were going to be replaced with windows 7 and install Ubuntu on them. Use the money that would have been spent on that and buy some vt capable servers running KVM. Use the current servers as a clustered file system like gluster and possibly iscsi.
You will still save money in the short term and the long term.

---

### Post by Sternfan on 2011-04-01
Ubuntu won't work as a client for a whole host of reasons.

Rob

---

### Post by jfluhmann on 2011-04-04
Being as brief as I can, I'll lay out what we're doing at my work (K-12 school district).  I can go into greater detail about things if you'd like.

~575 "desktops" to be virtualized for ~650 people
majority are old client machines (5-9+ years old)

Virtual Desktop software: Virtual Bridges VERDE - [http://vbridges.com](http://vbridges.com)
Server cluster: 4 x HP DL385 G7s with dual AMD 12-core and 128G memory each
Server capacity: ~120 concurrent desktop sessions per server
Storage: 3TB NFS share from another server (currently)
client machines: old PCs PXE booting into Ubuntu desktop that connects to user portal for launching Windows XP, Windows 7, and Linux desktop images


The VDI software we use allows us to add in more servers as needed.  We chose our server specs to try and maximize sessions, while minimizing hardware.  For a brand new server that should easily handle 50 concurrent session, I priced one out that included storage for under $5,000.  I'm sure if looking on e-bay or hitting up some universities for any "out of warranty" servers that have Intel-VT or AMD-V support, you could get a good deal.

Before going with the Virtual Bridges solution, I was looking at using OpenNebula to kick off the VMs and then just connect to those from each client machine.  My biggest roadblock was getting the clients to connect to the correct VM each time.  I needed a connection broker, and thus went with our current solution.

Something else I looked into was UlteoOVD.  Think of it as an open source Citrix XenApp.  There are other options out there for low-cost VDI, but so far the people I've talked to that have tested VERDE against the options have gone with VERDE.

Let me know if you'd like to go into detail about it.

Cheers!

---

### Post by Sternfan on 2011-04-11
Thanks for the prompt reply.  I have tried to reply to this before, but FF was giving me issues...  So here are some quick Qs:

Thanks for the info on vbridges - I downloaded the admin guide, printed it and am in the process of going through it.

Servers - do the servers have an OS?  Or does vbridges sit on the servers like a hypervisor?

Clients - you mention the PXE client booting into an ubuntu desktop - did you set that up yourself or is it part of vbridges?  What is the "user portal?"  I am curious how this works from the user perspective.

Client Images - when you make a VM (say win7) - and you have 100 users - do you have to create 100 VMs?  Can users connect to a specific VM - such as a VM with finance software that only the finance dept should have access to them?

Printing - how do the thin clients handle printing?  For instance, if there is an office of 10 people that connect to a shared printer now, once virtualized how do they share (and connect) to the printer in that office?  I imagine IP printers are easier to setup, but curious how this works with locally shared printers.

You mention an NFS share for storage.  Since it is NFS, I assume a NAS would work?

Thanks,
Rob

---

### Post by tgm4883 on 2011-04-12
> **Sternfan said:**
> Ubuntu won't work as a client for a whole host of reasons.

Rob

Why not? You would be using them as dumb terminals

---

### Post by Sternfan on 2011-04-13
The thin client (dumb terminal) needs to connect to some virtual desktop.  That VM has to be Win7 (for a variety of reasons).  And before the argument starts about using Ubuntu on a business desktop, I've been down that road, looked at the possiblities and Ubuntu is not (regrettably) ready for the business desktop.  

Rob

---

### Post by tgm4883 on 2011-04-13
> **Sternfan said:**
> The thin client (dumb terminal) needs to connect to some virtual desktop.  That VM has to be Win7 (for a variety of reasons).  And before the argument starts about using Ubuntu on a business desktop, I've been down that road, looked at the possiblities and Ubuntu is not (regrettably) ready for the business desktop.  

Rob

Sorry, not trying to be dense here, but why can't you use Ubuntu as the dumb terminal, and use something like terminal server client to connect to the windows 7 VM?

---

### Post by Sternfan on 2011-04-13
Not sure about the miscommunication, but that is pretty much what I have been trying to figure out:

Terminal - can be anything (Ubuntu) that connects to a virtual desktop on some cluster (thinking Ubuntu again).  With the virtual desktops being win7.

I am trying to get all the pieces together to get what the possible solution would look like.

Rob

---

### Post by jfluhmann on 2011-04-13
> **Sternfan said:**
> Servers - do the servers have an OS?  Or does vbridges sit on the servers like a hypervisor?
Yes, with our setup, we're running Ubuntu 10.04 (recommended), but RedHat and SUSE are also officially supported.  It's KVM-based, thus it uses a Linux OS on the server

> **Sternfan said:**
> Clients - you mention the PXE client booting into an ubuntu desktop - did you set that up yourself or is it part of vbridges?  What is the "user portal?"  I am curious how this works from the user perspective.
I set it up myself, however, I was talking with Leo (VBridges CTO) about it and I believe it's on the roadmap to be included as a piece of their solution.  The user portal is the web page where the user logs in and initiates their desktop session.  They basically visit a webpage, login with their credentials (in our case, AD credentials) and select which desktop image they would like to run.  Based on the connection choice, a Java applet kicks off either a SPICE or RDP connection to the virtual desktop.

> **Sternfan said:**
> Client Images - when you make a VM (say win7) - and you have 100 users - do you have to create 100 VMs?  Can users connect to a specific VM - such as a VM with finance software that only the finance dept should have access to them?
You'll only create a single image for each variation that you want.  Using your example, you could have a standard Win7 image that is offered to people in one group, and then a Win7 image with finance software offered to another set of users in a different group.  Each image that kicks off is a "copy" (sort of) of the original image.  Changes made by the user to the image itself are discarded once the VM shuts down, while user data is persistent and can be accessed by the user from any image that they run (such as 'My Documents' can be access by the same user from a Win7 image, Linux image, or XP image).

> **Sternfan said:**
> Printing - how do the thin clients handle printing?  For instance, if there is an office of 10 people that connect to a shared printer now, once virtualized how do they share (and connect) to the printer in that office?  I imagine IP printers are easier to setup, but curious how this works with locally shared printers.
The software can use the underlying client system's default printer as the default printer within the VM session.  You can also add networked printers to the golden image (or use logon scripts to add based on user and client location).

> **Sternfan said:**
> You mention an NFS share for storage.  Since it is NFS, I assume a NAS would work?
Yes.

---

### Post by Sternfan on 2011-04-21
JFluhmann - thanks for all the help.  I downloaded the manual, printed it and am in the process of going through it (so I am sure I will have some more Qs).

Off the top of my head, here are some more Qs:

- **hardware requirements** - about 50 concurrent win7 guests.  For sizing servers I am going with 1 CPU (core) can support up to 8 VMs.  And for RAM about 2gb per win7 vm.  Does that sound about right?  

- **cluster Qs** - Do the guests "run" on a particular host?  For instance, let's say I have 20 users using 1 win7 VM.  Does one particular host/server run this VM?  Or does the entire cluster provide CPU/RAM resources for this VM?

- **Thin Client** - For instance, let's say this is Ubuntu desktop.  The goal would be just enough OS to start a connection to a VM (I assume RDP) and perhaps printer sharing.  How do you set this up?  Uninstall all the apps etc?  Since this should be a "dumb terminal," how do you enforce the idea that the only thing they should be able to do is connect to a VM?

Thanks,
Rob

---

