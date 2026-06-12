---
title: "Wireshark"
date: 2008-11-17
forum: Security
---

### Post by DoubleMcLovin on 2008-11-17
So I installed wireshark to monitor and analyze my own network just to play around with it. The first thing I notice is hundreds of this message:
```
627	392.331197	Nvidia_18:69:22	Broadcast	ARP	Who has 192.168.1.223?  Tell 192.168.1.102
``` highlighted in blue. Im wondering what this could possibly be if anyone is experienced with wireshark.

---

### Post by kevdog on 2008-11-17
Its the dhcp server in your router trying to figure out who owns the lease for the above local IP.  If you would plug the machine that originally had the lease back into the router -- this wouldn't be an issue.  Can't you clear all dhcp leases on the router?

---

### Post by Kinstonian on 2008-11-17
ARP is a common protocol and is used to find out the MAC address when all you know is the IP address (you need both to communicate).  We can't tell if there is a pattern to the traffic when you only post one ARP request...  However, if a host is sending 100's of ARP requests looking for the MAC address of a single IP it means:

1.  192.168.1.102 wants to communicate with 192.168.1.223.
2.  There is some kind of problem because a host shouldn't send 100's of ARP requests for a computer.

Here is what happens when I try to telnet to a non-existing host.

```

08:19:50.136285 arp who-has 192.168.1.145 tell 192.168.1.102
08:19:59.136378 arp who-has 192.168.1.145 tell 192.168.1.102

```

Notice there are only two ARP requests, and there is a 9 second gap between them.  I suggest going to 192.168.1.102 and seeing if you can find the process that wants to use the network.

---

### Post by tqzxzjhu on 2008-11-18
[&#27743;&#24178;&#21306;&#31649;&#36947;&#30095;&#36890;&#20844;&#21496;](http://classad.dahangzhou.com/223685.html)[&#35199;&#28246;&#21306;&#31649;&#36947;&#30095;&#36890;&#20844;&#21496;](http://classad.dahangzhou.com/223685.html)[&#25329;&#22661;&#21306;&#31649;&#36947;&#30095;&#36890;&#20844;&#21496;](http://classad.dahangzhou.com/223685.html)[&#30095;&#36890;&#31649;&#36947;&#30005;&#35805;](http://classad.dahangzhou.com/223685.html)[&#31649;&#36947;&#30095;&#36890;&#30005;&#35805;](http://classad.dahangzhou.com/223685.html)

---

