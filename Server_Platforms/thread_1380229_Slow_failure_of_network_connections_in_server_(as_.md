---
title: "Slow failure of network connections in server (as compared to desktop)"
date: 2010-01-13
forum: Server Platforms
---

### Post by James Paige on 2010-01-13
I have two ubuntu boxes. One is a 9.04 desktop edition and the other is a 9.10 server edition

I am working on some code that needs to be highly tolerant of bad network connections. It sends transactions to a central database, but when the network is not available, it caches them locally to retry later.

I have the code working beautifully on my desktop box. but when I test it on this other box (the one running server edition) there is a HUGE DELAY every time it tries and fails to send a transaction to the database when the network is down.

I tested a little further, and I found that if i unplug my network cable and run **ping somehost** on the desktop, it fails *instantly* saying "ping: unknown host somehost"

But if I unplug the cable on the server box and run the same ping command it lingers for about 40 seconds before the ping fails.

Does anybody have any idea why this might be happening? Is this a 9.04 vs 9.10 difference? Is this a desktop vs server difference? Is there some package I can install, or some config setting I can change that will make the server box insta-fail just like the desktop does?

---

### Post by James Paige on 2010-01-13
Also, I just noticed that if I disconnect the network cable on my desktop box, the IP address goes away instantly (as verified by ifconfig) but when I disconnect the cable on the desktop box (which is also configured by dhcp) the IP address lingers indefinitely

---

### Post by DestructionsRightHand on 2010-01-13
What are the dhpc setting on the dhcp server?

---

### Post by James Paige on 2010-01-13
Both the desktop box and the server box are getting their IP address from the same dhcp server, so that probably couldn't make a difference... but since you ask, which dhcp settings would you like to know?

EDIT: actually, now that I check, the dhcp client setup on each is drastically different. The server box is using dhclient3 and the desktop box is using dhclient with some command-line arguments interacting with NetworkManager

---

### Post by KnottyMars on 2010-01-13
Im surprised you arent running a static IP. I would configure the contents of /etc/network/interfaces myself since its a server that is commuicating with another box (maybe over the WAN)

I wonder if its something to do with DNS, since its taking so long to timeout. You can specify the loopback as the nameserver to test it out at least.

Maybe see how it works with a static config with only itself as the nameserver, that should give you some clue where in the network layer, its taking so much time. 

Good luck.

---

### Post by James Paige on 2010-01-13
I am using server edition, but the application is specifically designed to not care what its own IP address is. I will eventually have to create a lot of these boxes, and I don't want to have to manually configure each one any more than absolutely necessary. So DHCP is pretty important.

On further investigation of the dhcp client, I see they are both running dhcp3-client, I was just confused because of /sbin/dhclient which turns out to just be a symling to /sbin/dhclient3

Current theory is that NetworkManager is what makes the difference...

EDIT: Solved! I needed to edit **/etc/NetworkManager/nm-system-settings.conf** on the server box and in the **[ifupdown]** section, I set **managed=true**

... although it is a little crazy that worked, because on my desktop box, the same setting is still **managed=false** :(

---

