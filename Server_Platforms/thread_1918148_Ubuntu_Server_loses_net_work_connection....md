---
title: "Ubuntu Server loses net work connection..."
date: 2012-01-31
forum: Server Platforms
---

### Post by CGW on 2012-01-31
My Ubuntu Server loses network connection intermittently, but usually when transferring large files.  It will be working and then all of a sudden it's gone.  I usually just transfer file via SFTP whether inside or outside my network.  When the connection is lost I'm forced to either reboot the server (if possible) or flat-out force the server down by holding down the power button.

I'm running Ubuntu Server 10.10 on a AMD64 system.  Originally I was using the motherboard's built in ethernet chipset, but added a generic PCI ethernet adapter hoping that would solve the problem...It hasn't.  The system connects through a standard router/network setup that includes a few switches.  Of the half dozen devices connected to the network, only the server is affected. 

Any thoughts? What other info should I post?

Thanks in advance.

Chris

---

### Post by shumifan50 on 2012-01-31
I have never had network problems with 10.04, so
Some suggestions:
Eliminate hardware problems:
1. Try a different network cable.
2. Plug into different port on the switch/router.
3. You have already swapped the network card.

Configuration problems:
1. Check there are no conflicting IP address on the network, by using a different IP on the server.

Sorry id the above is too obvious.

---

### Post by CGW on 2012-01-31
No suggestions are to obvious.

I did switch cables a while back...but who knows, maybe I've got two bad ones :(

The router was replaced about 3 months ago, and I believe I did try moving to another port.  The router is full, so I guess I'll have to trade places with something else.

AFA the IP addys, I didn't see any conflicts, but I'll def double check that.

EDIT: I checked the DHCP and it appears all is well.  I've actually got the router reserving the IP addy for the server via it's MAC addy.  So, in theory, there should never be any conflicts.  At least in theory.

---

### Post by ruffEdgz on 2012-01-31
When looking around the log directory, I believe information related to dhclient or anything else related to this problem might be in a file called 'syslog'
```

less /var/log/syslog

```

When you look at the system logs, do you see it consistently disconnecting your network or is it random? Do you see any errors happening around the time you have network problems and do they seem relevant to your network problem? Does this server have a static IP assigned to it?

Good place to start as it might not be on the OS level but might be on the router level as well.

---

