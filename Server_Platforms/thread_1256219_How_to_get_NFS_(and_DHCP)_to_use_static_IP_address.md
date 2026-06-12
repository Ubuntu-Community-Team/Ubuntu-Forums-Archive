---
title: "How to get NFS (and DHCP) to use static IP addresses"
date: 2009-09-02
forum: Server Platforms
---

### Post by raymondvillain on 2009-09-02
Just installed 32 bit Jaunty server.  I would like to set up shares for a couple of workstations, each running Jaunty.  Right now all machines are assigned addresses at startup and these change.  So if I set up a share for 192.0.168.251 today, tomorrow that machine may have address 192.0.168.255 and the share just goes away.

What's the best way to have the server issue the same IP address every time one of the workstations boots up?  Is dhcp3-server the way to go?  Or is this something that is only meant to be nstalled on workstations?

Thanks

---

### Post by TwiceOver on 2009-09-02
So what you want is to have DHCP hand out the same address to the same machine every time?

Assuming that is what you want...  What is currently assigning addresses?  Is your router handing them out or do you have a linux server somewhere doing it.

Either way, what you are looking for is called "Static DHCP".  I don't know of any home routers (such as a linksys) that do this right out of the box.

The idea here is that your DHCP server keeps a list of MAC addresses (1 for each computer on the network) and you assign an IP to that MAC.  When the computer with a MAC from the list requests an address, the DHCP server gives that computer the assigned address.

---

### Post by nhanquy on 2009-09-02
1. Almost routers out there support ***assigning static IP by MAC***.

2. Also it can be programmed to ***have a block of IPs reserved ***and then you can assign your router a static IP (one in those reserved IPs).

So either way, it will work for you. I prefer the 2nd choice.

---

### Post by raymondvillain on 2009-09-02
Thanks, TwiceOver.  I have the MAC addresses of each machine and I intend to proceed with your suggestion.

Do you know if I need to install dhcp3-server?  Is there some other way to accomplish the same thing?

With dhcp3 I have instructions to modify /etc/dhcp3/dhcpd.conf and add a host section for each computer with its MAC address.

Nhanquy, your suggestion to have the router assign static IP's by MAC is most intriguing, do I do that by booting up the router configuration web page?

Thanks for all the help.

By the way, is NFS the best way to set up shares?  I want workstation X to have its own share on the server that cannot be used or seen by computer Y, workstation Y to have its own, etc.

---

### Post by ShutterAce on 2009-09-02
I only allow DHCP to use addresses of ".100" and above. Then all you do is just keep your static addressed machines, the servers, below ".100". Simple and easy to remember.

---

