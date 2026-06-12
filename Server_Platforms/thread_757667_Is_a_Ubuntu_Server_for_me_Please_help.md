---
title: "Is a Ubuntu Server for me? Please help"
date: 2008-04-17
forum: Server Platforms
---

### Post by JovialKnight on 2008-04-17
Dear Ubuntu Server Experts,

I am about to start a server build project and would like to ask you if ubuntu server can be configured to satisfy my requirements. If the answer is yes I shall go figure out the set up and installation processes from the tips section. I'm hoping that this is not to much of a novice question to be asking, and that all you Ubuntu experts will provide me with a weath of expert info. :guitar:

This is what I want to do, I need a home server that can:

1) Back up data (Drive images from my workstation and laptops). Be in hardware  Raid 1 (2X 1 terabyte drives).  I also have a lot of Scientific data that I want to securely back up.

2) Act as home network server

3) Be used to serve scientific data to remote windows XP systems via a net connection

4) Act as remote media server for my home network and over the net (to store and serve MP3s and videos)

5) Act as a proxy web server for my laptops from internet cafes, so I can use an encrypted connection to surf the web from public places.

6) Be secure! – I need secure password protection, especially for my scientific data

This is the hardware I'm thinking of getting to run it on:

CASE: Gigabyte GZ-X1 ATX Mid Tower, Includes 350W PSU
MOTHERBOARD: ECS AMD690GM-M2 AM2 AMD 690G
PROCESSOR:  AMD Athlon 64 X2 4000+ Brisbane 2.1GHz
RAM:  Kingston 2GB (2 x 1GB) DDR2 800 (PC2 6400) Model KVR800D2K2/2GR 
HARD DRIVES: 2X SAMSUNG Spinpoint F1 HD753LJ 750GB SATA 2
RAID CONTROLER: 3ware 9650SE-2LP, PCI Express, SATA II
WIRELESS NETWORK ADAPTER: Linksys PCI wireless network card

Also, will I need dual gigabit LAN (my chosen MoBo does not feature this)?  Or will one wired and one wireless LAN connection do the job just fine?

Thanks for the help

---

### Post by lintoolman on 2008-04-17
Yes and very easy to do.  

Item 1 has several options depending the setup.  Research rsync.
Items 2-4 can be accomplished with Samba
Item 5 can be accomplished with OpenSSH with port forwarding.
Item 6 can be accomplished based on how authentication is setup.

---

### Post by daengbo on 2008-04-17
1) backuppc is an enterprise-grade backup solution with clients for all major operating systems.
2) Samba will act as domain and file server
3) You will need to have a hostname (likely va dyndns.org) to do this reliably. You can then use ssh to access and transfer files. There are GUI ssh file clients for all major systems. Port-forward from your router.
4) you can use an authenticated web application to do this. There are a few to choose from. If you don't want to do that, you can, again, use ssh
5) squid can act as a proxy server, and can require authentication. I'm also sure that there's a web app which can do this for you, but Idon't know of one off the top of my head.
6) Choose secure passwords and you won't have a problem. Avoid Internet-facing Samba or any other service you don't absolutely need. Use Snort or another IDS to help you. Put your ssh server on an alternative port. Enable key sign-ins and disable password sign-ins for ssh.

Hardware is virtually irrelevant for a file server. Wired is easier to set up on a server, but wireless will work.

---

