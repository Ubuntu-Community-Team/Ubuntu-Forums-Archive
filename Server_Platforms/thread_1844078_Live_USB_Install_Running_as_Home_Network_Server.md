---
title: "Live USB Install Running as Home Network Server"
date: 2011-09-14
forum: Server Platforms
---

### Post by jingo_man on 2011-09-14
Hi guys,

I am looking for thoughts/recommendations/alternatives/etc to my intended setup, ahead of me actually undertaking this...

I have an HP Microserver (1.3GHz dual-core AMD Neo N36L, 8GB RAM, 1GB NIC)

Originally I ran this as an ESXi 4.1 Update 1 hypervisor. I had 2 VM's: a test Windows Server 2008 R2 for studying purposes, and an Amahi VM for home network server duties.

Unfortunately, I don't think this hardware was capable enough, as I would only see 6MBps throughput for AFP or SMB traffic and although not extensively tested, I am concerned that all VM's may suffer when under a heavy load (i.e. a whinging other-half if she is watching a film whilst I am doing some Windows-based intensive task on my server at the same time). Plus I can migrate my VM needs to VMWare Fusion running on my Mac.

But having played with Amahi, I really like greyhole for the home network server storage needs that also circumvents software RAID which I have little faith in. Also, greyhole drives will be mountable to other Linux installs, as its just an EXT volume, for migrations or issues. So I am likely to continue down the road of Linux for this server and I usually turn to Ubuntu (probably Server edition in this case, to be honest). This is serving as the primary storage for XBMC installations on the network as well as a network backup location.

I am intending to run this as a "Live USB" installation, and with the 8GB of RAM I have installed, would hope to run it mostly out of RAM. But with the newer Live USB setup, I would have a persistent partition in order to save my additions/amendments/installations/etc. The device has a 4-bay hard drive capacity, which I would like to reserve for the data/media aspects of the setup, and also an internal USB slot which the unit can boot from which again is the intention.

Having never run this type of install before, I have seen many pluses for running it this way (to minimise USB disk writes, takes advantage of the mountains or RAM I have available on the system, which is also the fastest "storage" medium available) over installing the O/S to the USB disk.

What would other server-based installations be like in this setup? Namely, Apache, BIND, DHCP, Samba, Greyhole, MySQL, PHP, which will be the primary functions of the server. Will they work well/better/worse in this "running from RAM setup"? Or will they still rely heavily on the USB device, including the persistent volume?

What are others interpretation of all this?
How much is this still going to be reliant on the USB disk read/writes during normal operations?

Cheers

---

