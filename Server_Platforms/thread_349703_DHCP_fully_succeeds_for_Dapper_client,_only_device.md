---
title: "DHCP fully succeeds for Dapper client, only devices ping for DHCP Dapper server"
date: 2007-01-30
forum: Server Platforms
---

### Post by nero-r on 2007-01-30
The DHCP, DNS, WINS is on MS Windows 2003 Enterprise.:guitar: 

Right.. SO,

My 6.06 client machine, w/ gnome, does smashingly, getting DHCP request, connecting to the internet, Evolution IMAPs, shares, etc.

My 6.06 server I set up through DHCP, w/o startup error, and I can't leave the network or resolve names or ping the gateway or ping anything which is not a device.  I believe the static IP of the MS gateway is protected from ping, but the nameserver and DHCP machine are not, and they lose 100% of a hundred packets, or I don't hear the response.

The MS gateway has ISA2006 which has been configured to not interfere with the machine's group of ip's what.so.ever ( therefore NATted ) when I try this with a DHCP reservation by mac address, but with or without firewall rules, the 6.06 client does everything, and the 6.06 server does recover a DHCP request, does ping devices, and yet can't ping static MS machines, or apt-get anything, or ping a random ip number outdoors.  The client gui lets me add the search locale... but it looks just like what the server got from DHCP, in /etc/hosts and resolve.conf.

1. What's the MINIMUM of additional things I should add to function inside a generic network until I can publish out in the wild?
2. Can it be done during the first install?
3.  What net config sequence does the client do so well automagically?  Are there resources about this?

thanks for listening!  :confused:

---

