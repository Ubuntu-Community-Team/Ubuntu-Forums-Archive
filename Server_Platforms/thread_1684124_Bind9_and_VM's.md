---
title: "Bind9 and VM's"
date: 2011-02-08
forum: Server Platforms
---

### Post by jhazard112 on 2011-02-08
Hi All,

I am running a Ubuntu 10.04 server with the XFCE Gui.  I have installed Bind9 and I have a problem that I am trying to solve.  I have this running in a VM with VMWare Fusion and another VM running with XP SP3.  I am trying to link the two and have the XP VM look at the Server VM for DNS.  I do not want this getting to the outside world, so I am using "host-only" feature.  How exactly would I go about doing something like that?  This is also so I can setup wireshark and see exactly what the XP VM is trying to reach out to on the "network."  Any assistance is much appreciated and welcomed.

Hazard

---

### Post by elico on 2011-02-08
well you are doing wrong stuff cause what you need to do is one of two..
make two host only interfaces and bridge them 
or two.. make an internal network between the two machines on one eth card.
and put wireshark on the xp machine .. it's the same stuff on the xp vm and on the outside world.

---

