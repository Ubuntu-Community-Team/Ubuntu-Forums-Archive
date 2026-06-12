---
title: "Ubuntu 9.04+Squid+Cache+Remote Box+Iptables=me with no hair"
date: 2010-03-14
forum: Server Platforms
---

### Post by cpatchett on 2010-03-14
As you can read from the title, I am about to pull my hair out on this. I have ready tutorial after tutorial and checked my configs like 9 times each. Here is the rundown of everything, ANY help on this would be greatly appriciated.
 
First off, all of this is running on a VM Ware ESXi Hypervisor, so it is all Virtual and I really really hope that isn't what is causing my problem. I am running Ubuntu 9.04, fully updated on every VM that is mentioned here.
 
 
 
Internet<--->Modem<--->Ubuntu Firewall with IPtables<--->Network--------->Client
[INDENT][INDENT][INDENT][INDENT][INDENT][INDENT][INDENT][INDENT]l_____>Squid proxy<____l
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT] 
Ok, so if you can read that, I have IPtables set up as my router/firewall/nat. I am running a script some friends and I have been working on for some time. Supposedly, you are suppose to be able to put 3 to 4 lines in iptables and have it Destination Nat the trafic BACK to the squid proxy server, AND then let the traffic back out onto the internet. 
 
I CAN'T GET THIS TO WORK!!!!
 
The proxy will work fine right now, but I have to point the clients at it, I don't want this, I want it to be transparent and IPtables to redirect ALL port 80 traffic through the squid proxy. I know I COULD run squid on the same box as the firewall, but I have my reasons why I don't want to do that, unless of course I have absolutely no choice.
 
I have tried a solution from one of the O'Reilly's books, I have tried serveral configs I have found on the internet, and NOTHING works. Any ideas WHAT could be missing? If you need to see the configs, that is not a problem, just let me know. Please Help

---

