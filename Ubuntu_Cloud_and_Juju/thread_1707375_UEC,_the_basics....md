---
title: "UEC, the basics..."
date: 2011-03-15
forum: Ubuntu Cloud and Juju
---

### Post by FiVAL on 2011-03-15
Hello cloud users!

the last couple of months a follow closely and investigate the working of the Ubuntu Cloud.
I have my VM ESX certificates and like the way virtualization works. But cloud computering
'looks' even better (in our situation)..! We are almost ride of the licensed OS's and at
the moment I admin about 14 (virtual) ubuntu servers.

So the next step is to find out if the Ubuntu (private) Cloud is, what I hope it is ;-)

At the moment I ordered three new Dell Rack Servers with the specifactions I'll need to
setup a UEC. The Topologie I want to use is the one with at least 2 Physical Systems.

Server 1 - CLC/Walrus/CC/SC
Server 2 - NC
Server 3 - NC

But before the servers are even delivered, I have already a couple of questions...!

[LIST]
[*]First of all: The 'Cloud Controller' and 'Walrus' aren't they a single point of failure whithin UEC?
Does the cloud go straight offline when the CLC and/or Walrus crashes?
And if so, what does the cloud 'loses'?

[I]Yes, I did read the following posts:
[[http://ubuntuforums.org/showthread.php?t=1409254]](http://ubuntuforums.org/showthread.php?t=1409254])
[[http://www.mail-archive.com/ubuntu-cloud@lists.ubuntu.com/msg00260.html]](http://www.mail-archive.com/ubuntu-cloud@lists.ubuntu.com/msg00260.html])[/I]


[*]Second: If I did my homework correct, I understand that the workstations (clients) always will
be connected on the public site of a cluster controller?
So the CC is also a router and maybe even a kind of firewall?
And if so, how does a workstation (client) finds his way to a MySQL Server (VM) in the cloud?
(because this MySQL Server can wakeup in cluster 2 if cluster 1 fails, isn't it?)


[*]Third: Are there (types of) services/tasks in a (small) business environment which are better
to NOT run in a cloud ?? (cups, databases, calander, postfix, etc....)


[*]The last, for now ;-) When I start installing UEC on my servers. Server 3, 2, 1/eth1 on a
private LAN and Server 1/eth0 on the company's 'production' LAN with a DHCP. Is there something
I have to be very carful with ??
[/LIST]

Thanks in advanced for everybody who will reply!

---

### Post by kim0 on 2011-03-16
Hi, let me try to answer :)

- Yes, it's a SPOF. You can build a HA CLC however if you want, read
[http://www.roaksoax.com/2010/10/high-availability-uec-clc-howto](http://www.roaksoax.com/2010/10/high-availability-uec-clc-howto)

- Yes all traffic is routed through CLC (DNAT'ed). CLC knows where to find the VM. I'm not sure if a VM fails, it is auto-restarted elsewhere

- The reasoning here would be like services you wouldn't want to run under virtualization. Basically, no except maybe for heavily loaded databases (performance reasons)

- Just read the docs carefully
[https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

---

### Post by FiVAL on 2011-03-17
Thanks Kim0... I'm, again, a little closer to my solution ;-)

---

