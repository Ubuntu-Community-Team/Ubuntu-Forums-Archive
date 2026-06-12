---
title: "Ubuntu LAMP server in Virtual Machine"
date: 2007-08-21
forum: Server Platforms
---

### Post by perianmellon on 2007-08-21
I'm trying to get an Ubuntu LAMP server set up in a virtual machine on my computer.  I'm using Feisty desktop edition and have been able to get everything (Apache, MySQL and php)  running well.  

I can access my server locally from within the virtual machine, but I cannot access it from outside (including everything from pinging the virtual machine to typing the url in my browser).  Since I'm setting up this vm to test a WAF and want to throw some outside attacks at it, this is kind of an important feature for me :p 

As far as I can tell apache is listening on all the right ports.  Could this have something to do with the Ubuntu default closed port policy?  

Any advice or thoughts on this problem would be greatly appreciated, I've been banging my head against this vm all day.

Thanks!
- Kristin

---

### Post by mizzouxc on 2007-08-21
Kristin, 

In order for me to help you a little bit more, are you using VMware virtual machine environment or the built in virtulization that comes with ubuntu. Either way, make sure your networking isn't setup in NAT mode. For example if your physical server has an ip address of 128.206.2.1, your virtual machine needs a "real" ipaddress of something like 128.206.2.2 instead of something like 192.168.1.1

---

### Post by perianmellon on 2007-08-21
I'm using vmware, and actually, yes, I am using NAT.  Unfortunately I'm on a company network that uses registered MACs, so I can't used bridged networking.  

I'm pretty sure I've set up servers in virtual machines using NAT before, and was able to access them from within the local network using the internal IP.  Is there a reason you know of why this wouldn't be possible?

Thanks so much!

---

### Post by perianmellon on 2007-08-21
Actually, it looks like i was wrong, i can use bridged networking.   I just tried it and it did the trick, thank you so much.  You definitely saved me a lot of  headaches trying to figure this out

---

### Post by mizzouxc on 2007-08-21
Think of NAT in vmware the same way you think of NAT with your cable/dsl router at home. In order to access the server behind the NAT you have to 1. Point your web browser to the real IP address, in this case your host machine. 2. In turn, you have to setup NAT rules to forward ports to the correct IP address behind the NAT.

Example:

Host machine IP address is 128.206.2.1
Virtual Machin IP address    192.168.1.1

Someone with their web browser will have to type [http://128.206.2.1](http://128.206.2.1)

In order for this to work you'll have to set a NAT rule that forwards port 80 (web) traffic to go from 128.206.2.1 to 192.168.1.1

As a background 192.168.1.1 is what is called a non routeable IP address. This basically means that your client cannot type [http://192.168.1.1](http://192.168.1.1) into their browser and be directed to your web page. They must hit, for example, 128.206.2.1 in order to get to your system behind the firewall.

VMware is traditionally similar in setup, so you could apply the Workstation 5.5 guide to other products made by them:

[http://www.vmware.com/support/ws55/doc/ws_net_nat_advanced.html](http://www.vmware.com/support/ws55/doc/ws_net_nat_advanced.html)

I really hope this helps you out.

---

### Post by mizzouxc on 2007-08-21
=) And I just posted the long explanation of NAT. I'm glad I could help.

> **perianmellon said:**
> Actually, it looks like i was wrong, i can use bridged networking.   I just tried it and it did the trick, thank you so much.  You definitely saved me a lot of  headaches trying to figure this out

---

