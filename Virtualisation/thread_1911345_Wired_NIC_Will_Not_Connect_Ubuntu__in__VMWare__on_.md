---
title: "Wired NIC Will Not Connect: Ubuntu  in  VMWare  on  Win Server 2008"
date: 2012-01-18
forum: Virtualisation
---

### Post by mOrloff on 2012-01-18
I have just installed my first instance of Ubuntu.
(**beautiful** ui, btw)
It is installed in a VM on my Win2008 Server (Dell PowerEdge R710).

In Win, the network connection is working perfectly.
In VMWare, the network card is set as "Bridged", and showing as connected and successfully getting a MAC address assigned.
In Ubuntu, it looks like the NIC is functioning fine, it's just saying it's disconnected ... that the cable's not plugged in.

What should I be looking at ??????
Where do I go from here ?
~ Mo

---

### Post by mOrloff on 2012-01-19
UPDATE: Still not able to get online, but I made ***some*** progress.

The *_Configure_* button in *SystemSettings*>*Network* was greyed out initially.
I gained access to it by switching the *_on_*/*_off_* slider to *ON* [COLOR=SlateGray](which I did test earlier ... it tried and tried but could not connect)[/COLOR].
Anyhow, I manually set an IP address [COLOR=SlateGray](and all the other associated fields)[/COLOR].

Now the status says Connected, but I am still unable to get online.
Also, when I try to browse the windows network I get the error: "*unable to mount location, failed to retrieve share list from server*".

Soooo, what now ??
~ Mo 

Also, is this problem more likely to be a visualization issue [COLOR=SlateGray](part of my VMWare settings)[/COLOR], or should this post get moved to the networking forum???

---

### Post by dcstar on 2012-01-20
> **mOrloff said:**
> UPDATE: Still not able to get online, but I made ***some*** progress.

The *_Configure_* button in *SystemSettings*>*Network* was greyed out initially.
I gained access to it by switching the *_on_*/*_off_* slider to *ON* [COLOR=SlateGray](which I did test earlier ... it tried and tried but could not connect)[/COLOR].
Anyhow, I manually set an IP address [COLOR=SlateGray](and all the other associated fields)[/COLOR].

Now the status says Connected, but I am still unable to get online.
Also, when I try to browse the windows network I get the error: "*unable to mount location, failed to retrieve share list from server*".

Soooo, what now ??
~ Mo 

Also, is this problem more likely to be a visualization issue [COLOR=SlateGray](part of my VMWare settings)[/COLOR], or should this post get moved to the networking forum???

Install VMware Tools on the Ubuntu VM.

---

