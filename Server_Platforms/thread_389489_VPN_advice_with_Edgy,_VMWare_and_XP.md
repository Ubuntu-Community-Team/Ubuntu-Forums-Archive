---
title: "VPN advice with Edgy, VMWare and XP"
date: 2007-03-20
forum: Server Platforms
---

### Post by goliant on 2007-03-20
Here is my scenario. I am looking at helping out a small physiotherapy business that has 2 satelite offices. The satelite offices are actually seperate business that are owned by the same person who wants to keep "control" of the operations. They do not want their satelites to have the database installed locally. 

I was thinking of installing Edgy, SAMBA and VMware with XP on a Xeon server with 4Gb ram at the head office. XP will be the OS at the satelites so as to minimize the changes the user will face. The XP workstations will RDP into the XP VMware clients.  This way the database can remain at the head office. The database is a based on Clarion and does not do well when run over WAN. 

For security I was thinking of using  Hotbricks VPN routers but I recently have come across OpenVPN (I am a recent convert).

My questions are:

1) Am I insane? What issues can you forsee?
2) Do I need a VPN solution? Can XP utilize OpenVPN?
3) Has anyone done something similar?

I really appreciate your comments on this!!

regards,

Brian

---

### Post by alamba on 2007-03-21
Hi,

One of my clients has a similar set up. Here's how I do it:

Head Office: 
1. OpenVPN Server on a Ubuntu Box (Headless)
2. Windows XP Box (Headless)

The windows XP box is just an old box for terminal services incase someone coming into the network via VPN needs a windows interface.

The satellite offices have VPN client setup on ubuntu and windows boxes (there's a windows GUI client for OpenVPN). Since all the applications (but 1) in this setup are html based, most clients just fireup the VPN client and then use firefox to get to the application. For the one windows accounting application (still there due to historical reasons), I have the users connect into the windows XP box via terminal services and then run the client side app for the service.

HTH.

A

---

