---
title: "help setting up home file sharing network"
date: 2010-03-18
forum: Server Platforms
---

### Post by mechlad on 2010-03-18
first off, I am new to linux.
I am attempting to set up a headless home file server in 9.1 that has 2 network cards (one connected to wan and one to lan). I would like the end result to be a system that will distribute files across the lan and allow other networked computers to access the internet. The ability to remotely log into the lan is also desirable (to pull files off server from remote location).

I use qwest isp and an actiontech modem. My router is a D link with wireless.

I have installed the system with openssh, samba, and lamp, but cannot reach the internet upon ping. I think I may not have set up the correct addresses in the configure the network portion of the Ubuntu server install.

I am lost as far as the required set up for my needs. (dyndns, webmin...etc etc)

can anyone provide a step by step of setting this machine up to do the required tasks.

thankx

---

### Post by jrssystemsnet on 2010-03-18
Oi.  Well, you're certainly starting off with a bang, if you're new to Linux.

I would honestly recommend that for right now you ditch the whole bastion host idea (ie, one WAN nic and one LAN nic) and just connect the server to the LAN behind a router along with all your other LAN machines.  Get your feet wet before you try to tackle firewalls and DHCP server configs and routing and masquerading and NAT and oh, my. :)

If you don't want to take that advice... well, to start with, you're going to have to tell us more about the WAN side of the machine.  Is it connected to the LAN port of a router, or is it connected directly to modem that hands out the public IP address directly?  Is the modem using an ethernet handoff, or PPPoE?  Does your provider give you a static address, or dynamic?  ... this kind of thing goes on and on.

The very basics of it is, you have to get the WAN side correctly speaking to the outside world, *then* you can worry about setting up DHCP on the LAN side to hand out addresses to your inside machines, *then* you can start worrying about setting up a firewall, routing, and DNS masquerading...

Like I said, I'd really recommend you just set the box up as a server on the same LAN as your other machines.  SOHO routers are ridiculously cheap and generally do their job quite well... and they typically have a mean time between failures MUCH higher than that of a full-fledged PC.

---

### Post by partloer on 2010-03-18
Hi mechlad,

I also agree with jrssystemsnet about configuring your network of computers to be connected to the router.  It sounds like you have all of the equipment so it is just a matter of setup and configuration.  Let me know what you want to do I can step you through this if you like this option.

For some questions about the file distribution.
1. What are the other computer on your LAN that you want to transfer files with?
2. When transferring files between the internet and LAN does this have to be secure (encrypted)?
3. What type of logging into the remote computer do you plan on doing?

---

### Post by mechlad on 2010-03-18
> **partloer said:**
> Hi mechlad,

For some questions about the file distribution.
1. What are the other computer on your LAN that you want to transfer files with?
2. When transferring files between the internet and LAN does this have to be secure (encrypted)?
3. What type of logging into the remote computer do you plan on doing?

thanks for the quick reply
I see what you are saying.

1. a desktop running linux, a laptop running windows xp and 2 computers running xbmc (linux)
2. I would like it secure
3. I would like to remotely log in and admin the system. I would also like the ability to transfer files from the home network to a remote location.

---

### Post by spynappels on 2010-03-19
For remote administration, use either ssh or Webmin, depending on whether you want CLI or GUI.
You will need to forward ports from the router to the server, 10000 for Webmin (can be changed) and 22 for PuTTY/SSH (probably should be changed for security). If you do open a SSH/Telnet port you should also run something like denyhosts to stop brute force attacks.

Accessing files remotely becomes more tricky. I access my home LAN using a VPN, but that is always from my laptop. If you want to access from multiple computers, you need to look at SFTP. SCP would also work if the files will all be on your server.

If you want any more specific info, just shout, but I suggest tackling one of these points at a time.

---

