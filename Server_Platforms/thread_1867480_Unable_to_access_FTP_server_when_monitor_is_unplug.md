---
title: "Unable to access FTP server when monitor is unplugged"
date: 2011-10-23
forum: Server Platforms
---

### Post by ade234uk on 2011-10-23
I have set a wireless FTP server on my local network. It connects to my router wirelessly because it is to far from the router and I don't want a ugly black box sitting in the lounge. 

The FTP server runs Ubuntu 11.04. It is normal desktop version and not Ubuntu Server.

Basically my problem is the following. If I leave the monitor plugged in, the machine connects to the wireless network. I am able to access FTP and SSH and ping it from my Laptop and Desktop in the house.

However If I unplug the monitor, then the server does not join the network. I am unable to access FTP, SSH. I cant even ping it.

Am I making a really basic mistake here? If so is there a way to make this work without having the monitor plugged in. I would like to free this monitor up.

I have never experienced this issue before.

---

### Post by vasile002 on 2011-10-23
check the sleep settings, I believe it is going to sleep when the monitoring is unplugged

---

### Post by ade234uk on 2011-10-23
I disabled what I could in the BIOS but still no luck. 

In the end I had to edit xorg.conf file. I can now boot and access my ftp server over the network with the monitor unplugged.

Never had this issue before lol. Learn something new everyday.

---

