---
title: "Annoying repeated keystrokes in VMware Player"
date: 2014-12-07
forum: Virtualisation
---

### Post by John_Snow on 2014-12-07
Hi,
 
when  working in the guest, I randomly get repeated keystrokes. For example I  press return, and get 50 CRs instead (until I press another key). This  happens quite frequently and is really annoying.
 
I've googled this problem, and it seems to be around since quite some time - with no conclusive solution.

 

My setup:

VMware Player 6.0.3

Host: Windows 7 x 64

Guest: Ubuntu (13.x, 14.x, have tried various versions...) 64 bit

 

What to do?
 
cheers,
John

---

### Post by bashiergui on 2014-12-07
Network latency seems to cause it on remote vms, but if your vm is local then I wonder if your computer is beefy enough to run vms. What are your host specs?

Try this
[http://www.rayheffer.com/changing-text-typing-repeat-delay-on-a-vmware-virtual-machine/](http://www.rayheffer.com/changing-text-typing-repeat-delay-on-a-vmware-virtual-machine/)

If you don't know how to find the config for your VM this will tell you how
[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003880](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003880)

---

