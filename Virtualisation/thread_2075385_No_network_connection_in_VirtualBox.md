---
title: "No network connection in VirtualBox"
date: 2012-10-23
forum: Virtualisation
---

### Post by nemarona on 2012-10-23
There's a [recent thread]("http://ubuntuforums.org/showthread.php?t=2074894") on this issue, but since it's already marked as solved, and the suggested solution doesn't work for me, I thought I'd better start my own thread.

I installed VirtualBox on Linux Mint 13 (which is based on Ubuntu 12.04, that's why I'm posting here), created a VM and installed WinXP on it. Now WinXP won't allow me to access the Internet, even though a network connection is reported as alive.

I've fiddled with the Network options in VirtualBox, trying different adapter types (PCnet-FAST III, PCnet-PCI II, and Intel PRO/1000 MT) and regenerating the MAC address, to no avail.

Initially I thought the problem might be related with the fact that I was using an old virtual hard drive (.vdi) from a previous installation, so I deleted it and started from scratch. I even uninstalled and reinstalled virtualbox (together with virtualbox-dkms, since I was having kernel issues), but the problem remains.

Any ideas?

---

### Post by cmont899 on 2012-10-23
Makes sure on the "Network" tab that "Attached To:" and "Name" correspond with you system. "Attached to" is generally "Bridged Adapter" or "NAT".

A common error is the name is set to eth0 and you're using wifi (wlan0).

Chris

---

### Post by fjgaude on 2012-10-23
> **cmont899 said:**
> Makes sure on the "Network" tab that "Attached To:" and "Name" correspond with you system. "Attached to" is generally "Bridged Adapter" or "NAT".

A common error is the name is set to eth0 and you're using wifi (wlan0).

Chris

I've tried just about everything, NAT, Bridges, eth0, etc., and nothing works. I'm using 4.2.2 with Guest Additions. Any ideas, more, that is?

---

### Post by nemarona on 2012-10-23
> **cmont899 said:**
> Makes sure on the "Network" tab that "Attached To:" and "Name" correspond with you system. "Attached to" is generally "Bridged Adapter" or "NAT".
The "Name" field is not activated when "Network" is set to "NAT". I changed NAT to Bridged Adapter and voila! That did the trick.

Thank you for the suggestion!

I just realized how the way "Bridged Adapter" works differs from NAT, at least in one respect. I'm connected to a wifi network that requires logging in at the browser level after entering the usual network password. When NAT worked for me (last week), I didn't have to perform this extra step on the VM. Now, with the Bridged Adapter, I do need it.

---

