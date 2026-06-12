---
title: "VirtualBox Ubuntu 8.10 Guest Host networking wsithout ether cable"
date: 2009-03-04
forum: Virtualisation
---

### Post by markotitel on 2009-03-04
Hi,
I have ubuntu host and XP guest setup on Vbox 2.1. Ive setup Host networking for guest. Now the problem is that I have to plug in ehternet cable on my host mashine in switch for working network between Guest an Host.

I want to test some server settings made on Host, and use them with Guest OS, but without plugging ether cable.

Is there a solution for this?

---

### Post by dcstar on 2009-03-05
> **markotitel said:**
> Hi,
I have ubuntu host and XP guest setup on Vbox 2.1. Ive setup Host networking for guest. Now the problem is that I have to plug in ehternet cable on my host mashine in switch for working network between Guest an Host.

I want to test some server settings made on Host, and use them with Guest OS, but without plugging ether cable.

Is there a solution for this?

You probably have to configure your host machine to work without the Ethernet connection.

You may have to set a manual IP address, set up a DNS proxy and probably other things that will allow the host to be reasonably happy even if it is unplugged.

---

### Post by HermanAB on 2009-03-05
Can't remember the details off-hand on Buntu, but the 'ifplugd' daemon will take the network interface down when a cable is unplugged - you got to prevent that - stop the ethernet hotplug daemon.

Cheers,

Herman

---

