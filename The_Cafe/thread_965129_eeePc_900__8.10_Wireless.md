---
title: "eeePc 900  8.10 Wireless"
date: 2008-10-31
forum: The Cafe
---

### Post by iains on 2008-10-31
In[COLOR="Red"]
[https://help.ubuntu.com/community/EeePC/Fixes](https://help.ubuntu.com/community/EeePC/Fixes)[/COLOR]

under 'Wireless' 'Issue'

it say

[COLOR="Red"]"Wireless should work out-of-the-box with Ubuntu 8.10 Intrepid Ibex (as from kernel 2.6.27-1-generic). EeePC 900s (and possibly 701s) may still require "blacklist ath_pci" added to /etc/modprobe.d/blacklist" to enable wireless.

The EeePC uses an Atheros card which is not supported by default (Bug #182489). It will be supported in Intrepid using the free ath5k driver that is now in the upstream kernel. "[/COLOR]

I have just re-installed 8.10 and edited 'blacklist' and still my 900 still cannot see the wireless card let alone the WLAN. 

I earlier (on 8.04) tried Adamm's bespoke kernel which saw my Netgear WG602 access point but would not connect to it. (wifi0: unknown hardware type 801).
I also tried installing the madwifi driver and nisdiswrapper solutions - no joy !

I know other 900 users can use wireless - why can't I ?

Any ideas ?

---

### Post by iains on 2008-10-31
After failing with standard Ubuntu 8.10 I tried Adam's bespoke kernel for 8.10 and[SIZE="5"][COLOR="DarkRed"]** IT WORKED**[/COLOR][/SIZE] !

see [http://www.array.org/ubuntu/](http://www.array.org/ubuntu/) for details.

---

### Post by wolfen69 on 2008-10-31
thanks for the link. at least i can see all networks now, but can't connect to any of them. i'll figure it out in time.

---

