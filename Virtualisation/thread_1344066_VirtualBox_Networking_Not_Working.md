---
title: "VirtualBox Networking Not Working"
date: 2009-12-02
forum: Virtualisation
---

### Post by Mindastray on 2009-12-02
Hi,
 
I have this rented headless server that has a ubuntu 9.10 minimal os installed.
 
I am trying to instal a virtual machine with a static ip using bridged networking, i tested this with my test machine and it worked flawlessly, out of the box... just selected:
 
 -nic1 bridged and -bridgedadapter1 eth0
 
Ran the virtual machine, edited /etc/network/interfaces and it worked perfectly.
 
With the production machine i can't come to set this thing to work although NAT seems to work just fine.
 
There are two diferences between the test machine and the production machine.
 
The production machine has ubuntu 9.10 minimal installed while the test machine has ubuntu 9.10 server
 
the other diference is that the production machine is amd64 and the test machine is x86, and so are the respective ubuntu versions.
 
I think i have exausted all internet resources i could find looking for an answer for this, but had no success.
 
Can someone please shed some light into this matter for me? I have absolutely no idea to what should be the problem.
 
Thank you.

---

