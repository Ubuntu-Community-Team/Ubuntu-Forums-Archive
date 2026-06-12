---
title: "site goes down &amp; up frequently"
date: 2008-09-30
forum: Server Platforms
---

### Post by lefnire on 2008-09-30
I'm having a strange problem with my ubuntu server at [http://ocdevel.com](http://ocdevel.com). When accessing it remotely, it goes down for a couple minutes and comes back up almost every time I'm working with it.  I'll be adding content or modifying settings (it's a Drupal site), and every 3-4 page refreshes I suddenly get "Network Timed Out" error.  When that happens, I can't access it with SSH, I can't ping it, telnet, nothing.  Give it 5 minutes and it's back up!

Server logs aren't telling me anything... actually, syslog said there was an issue renewing DHCP leases for a while there, [which I fixed]("http://ubuntuforums.org/showthread.php?t=807148"), but that didn't stop this down-&-up problem.  
Any ideas where to start diagnosing this problem?

Edit: side note, this doesn't happen when I'm accessing it within the network, only remote.

---

### Post by alastair on 2008-09-30
I don't know what the problem is. But it might be worth using something like "wireshark" to sniff the packets to and fro as you work remotely - and see if anything funny happens anytime. Errors etc. 

Any firewall or traffic control? 
Is it a VM (e.g. Xen)? 

Alastair

---

### Post by lefnire on 2008-09-30
No VM, I don't think there's a firewall (I should know these things, but it was one of those "Ubuntu Perfect Sever" quick-install tutorials).  Per my ignorance, I'm hitting Amazon for books on Wireshark and Server Admin, since I don't even know what to look for in the packets :s

---

### Post by alastair on 2008-09-30
No need for any dead trees, wireshark (aka "ethereal") is here :

[http://www.wireshark.org/](http://www.wireshark.org/)

and can be installed from the normal Ubuntu repo. Lots of guides/tutorials around.

sudo iptables -L -n 

will tell you if you have firewall rules installed.

heers,


Alastair

---

### Post by lefnire on 2008-09-30
thanks for all the help Alastair.  Here's my, output, i'm assuming it means no firewall:
> 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

What does fierwall / no-firewall mean in my case?

---

### Post by alastair on 2008-10-01
Yes, that output means no firewall (no rules listed).

The firewall question was really just to see if there was any extra complexity to the network at your end. There may be other things getting in the way somewhere else. Hence the network analysis (packet sniffing) you could do.

Could there be some web/drupal process going on? e.g. snaptshot/autosave every few minutes (somewhere slow)? Or something else running regularly e.g. cron job?

Alastair

---

