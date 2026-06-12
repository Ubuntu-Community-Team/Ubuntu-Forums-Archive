---
title: "fwbuilder problems"
date: 2007-01-11
forum: Server Platforms
---

### Post by dlehman on 2007-01-11
I installed fwbuilder from the repos configured a simple firewall to protect just my machine this is not a dedicated machine it only has one nic,  it compiled fine and when I wnt to install I got errors, I don't remember for sure but I think it was permission denied to /etc

I removed fwbuilder and compiled the latest version 2.1.8 from source, had a few problems with libfwbuilder but got that fixed and upgraded my previous file for the never version, compiled and installed got error on install I believe permission denied on /etc again 

so I changed the working directory to ~/firewall and then it says the install was a success 
I checked with a

```
sudo iptables -L
```

but then I can't access any thing at all so I did

```

sudo iptables -F
```

and still could not get anywhere so I rebooted and then it was flushed 

so I decied to try again I checked the firewall configuating to make sure it was giveing me access to what I need and installed 
I did a 
```
sudo iptables -L
```
again to see if it went it did 
I thought maybe I need to reboot for it to take effect properly 

after reboot iptables is empty  it did not save anything 

what am I doing wrong where to I tell the installer to put it and make it save and why didn't my firewall allow me to get out?

Thanks in advance

---

### Post by arkhitekton on 2007-06-10
I've had similar problems using fwbuilder to create a set of workstation rules for iptables.  The symptoms are Firefox 1.5 being unable to access the network (local and Internet) and ping failing with a message saying that sendmsg has failed.

I've had a fwbuilder-based firewall running for several months.   The problems have only arisen in the last few weeks.  I stopped the network access problems by removing the line to execute the .fw file from my rc.local.   When I execute the .fw file manually, iptables seems to accept the rules and I continue to get network access.   Its only when the rules are installed by rc.local the problem occurs for me.

I can only assume that there is an incompatibility with iptables/kernel/fwbuilder rule set.  For the record, I'm running:
Ubuntu 6.06 LTS
2.6.15-28-686 SMP kernel
iptables v1.3.3
Firewall Builder v2.0.9 rev 1 Build 651

I'm not worried about getting a fix to this as I'm already behind a router firewall.  However I'm going to try firestarter or bastille to see if they can set up iptables corrrectly.  I've posted this in the hope that someone who has similar symptoms does not have to do a complete rebuild (like I've just done) in order to find the problem!  Just stop iptables being initiated at boot.

---

