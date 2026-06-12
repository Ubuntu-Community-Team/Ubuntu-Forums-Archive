---
title: "Installing Ubuntu Server from USB stick to another USB stick"
date: 2011-08-23
forum: Server Platforms
---

### Post by Monolith on 2011-08-23
Hello all,

I'm about to ditch Freenas as my NAS software and make it an Ubuntu server box. The mainboard is an Asus AT3ION-T dual core Atom board. Freenas runs happily from USB stick. I have no optical device to install Ubuntu from and would like to install Ubuntu Server to a USB stick.

So my question is: is it possible to install Ubuntu Server *from* USB stick to *another* USB stick?

---

### Post by oldfred on 2011-08-23
I have not installed server, but have installed desktop from one USB to another. You do have to be sure to install grub to the correct device.

The issue I had was with several internal drives the drive numbers of the flash drive changed when I rebooted without the install flash drive and the search did not work correctly. I had to manually edit the set root drive number to be correct to get it to boot.

---

### Post by dtfinch on 2011-08-23
I've done basically that before. Installing from usb to an sd card or usb drive on my desktop, configuring it, then booting it on a server.

One problem I ran into was with dhcp, booting Ubuntu Server on a different system than I did the install on. It detects the server's network card as a new ethernet card, eth1. The default /etc/network/interfaces only enables dhcp on eth0, so you need to edit it if you want dhcp to work on the new server.

Once it's up and running, you may want to disable dhcp on the interfaces you're not using, otherwise it'll spam your system log every 10 seconds or so complaining that dhcp failed on that interface (or at least 10.04 has this bug).

Another thing I did was create tmpfs mounts on /tmp, /var/tmp, /var/log, and /var/log/apt to minimize writes to the sd cards. 

Also be aware that the specific atom you have is 32-bit only.

---

### Post by Monolith on 2011-08-23
Thanks for all the suggestions.

I was planning on doing the install on the system itself to minimize problems with improperly configured hardware.

> **dtfinch said:**
> 
Also be aware that the specific atom you have is 32-bit only.

Is this an Ubuntu thing? It's running Freenas 0.7.2-AMD64 at the moment...

---

### Post by Monolith on 2011-08-23
> **dtfinch said:**
> 
Also be aware that the specific atom you have is 32-bit only.

> **Monolith said:**
> Is this an Ubuntu thing? It's running Freenas 0.7.2-AMD64 at the moment...

I see that I mis-guessed the processor, it's actually a 330 instead of the D525 I tagged (no possibility for re-tagging a thread?). Still, the 330 supports 64-bit, so the question remains.

---

### Post by volkswagner on 2011-08-23
Yes the Atom 330 support 64bit.  You will have no problems with Ubuntu 64bit.  I have installed 64bit Ubuntu server on an Atom 330 without issue.

---

### Post by Monolith on 2011-08-23
> **volkswagner said:**
> Yes the Atom 330 support 64bit.  You will have no problems with Ubuntu 64bit.  I have installed 64bit Ubuntu server on an Atom 330 without issue.

Excellent, many thanks.

I looked it up and the Atoms that don't support 64 bit are the N2xx, Z5xx and Z6xx.

---

### Post by dtfinch on 2011-08-25
I guess I didn't stare at the chart long enough. I could have sworn I saw a no for 64 bit next to the 330, but checking it again, it didn't. Sorry about that.

---

### Post by Monolith on 2011-08-25
> **dtfinch said:**
> I guess I didn't stare at the chart long enough. I could have sworn I saw a no for 64 bit next to the 330, but checking it again, it didn't. Sorry about that.

No problem whatsoever, I guess it's pretty confusing to have 32 and 64 bit mixed in the same family of processors. Intel's fault, not yours!

Also, this thread is now SOLVED. What I did was easier than I guessed it would be;

1. Use my Ubuntu laptop (11.04) to create a USB stick with Ubuntu Server 10.04.3LTS AMD64;
2. Boot my NAS system with the USB stick I created at (1)
3. Plug my destination USB stick in;
4. Point the installer to the destination USB stick;
5. Wait for a good while until GRUB was installed;
6. Remove source USB stick, reboot and;
7. Admire my handiwork!

Everything went smooth as butter, no problems whatsoever. Everything just worked out of the box. Feels good to be back at Ubuntu, I was beginning to feel a bit dirty after using Freenas for a month...

---

