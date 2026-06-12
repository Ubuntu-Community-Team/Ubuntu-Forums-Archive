---
title: "Strange CUPS issue... is it the router?"
date: 2009-05-30
forum: Server Platforms
---

### Post by lykwydchykyn on 2009-05-30
I have a little Debian etch server at home, which provides:
 - SAMBA
 - HTTP (Apache)
 - DNS (dnsmasq)
 - SSH
 - CUPS
To my LAN.  I've had this setup for about two or three years now, and it typically works fine.  Every now and then, however, CUPS messes up.

All our workstations/laptops (4 total) run Ubuntu, and we just use CUPS directly instead of going through SAMBA or anything.  The workstations are set up to automatically install shared printers, and the server is set up to share its printers.

Once every few weeks, the printer disappears from all the workstations.  Sometimes, if I reset the router, it starts working again.  Today after doing some rearranging in the computer room, I had to reset the router multiple times and the printers were appearing and disappearing at random times.

I ran wireshark while the printer was not working, and the UDP packets CUPS sends out seem to be corrupt.  Wireshark says "corrupt header length" by each cups UDP packet.

I tried switching ports on the router, but it didn't help.  The weird thing is, ONLY CUPS is being affected.  Packets from other services aren't showing up as corrupted, and the services are working just fine.

There is no firewalling going on on the router that I know of.

Now, it just occurs to me that I can only remember having problems printing from the laptops, which are wireless.  But we rarely print from the wired workstations since they are for the kids mostly.

The router is a netgear wgt624 with the latest firmware from netgear on it.

Any ideas?

---

