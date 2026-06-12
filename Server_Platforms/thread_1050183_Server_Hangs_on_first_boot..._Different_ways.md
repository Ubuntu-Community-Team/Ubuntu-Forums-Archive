---
title: "Server Hangs on first boot... Different ways"
date: 2009-01-25
forum: Server Platforms
---

### Post by Lemons on 2009-01-25
Right now I am trying to get wireless in my room. And since I am cheap, and a computer tech, I decided to make my own router. So I took an old gateway, 2 ethernet cards, and a wireless card, and threw them together. Now I try to install ubuntu server 8.10, with no avail. Everytime I get stuck on:

"Starting Kernel Log Daemon" or "Configuring Network Interfaces".

The only extras I installed were DNS and OpenSSH. Besides that it should be a basic setup. I have tried w/o the network cards and w/o the wireless.

Some possible problems I see is:

- Using a 6.8GB HDD
- Wireless Drivers (DLink)
- Ubuntu Server 8.10

Any help? I google this for about 2 days and I am lost... I have done this before with success, so its kind of throwing me off...

Thanks!

---

### Post by volkswagner on 2009-01-25
I would suggest booting a live cd to check compatibility of components.  Try  to boot up bare bones then try booting with additional cards one at a time.

That is provided the pc has enough ram to support a live cd.

---

### Post by Lemons on 2009-01-25
I just went and got 8.04.2 and it works fine... Probably some compatibility. I am using 1990's hardware, drivers might have been removed from the kernel? Just a thought. but anyways the older version worked fine.

---

