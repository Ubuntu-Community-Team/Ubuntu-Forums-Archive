---
title: "Installed VMWare, now internet doesn't work"
date: 2009-11-18
forum: Virtualisation
---

### Post by JaredFactley on 2009-11-18
I've really confused myself with this one. I installed VMWare Server 2 in Karmic last night as well as the patch. 

I was accesing the browser console for a few minutes until I got a message saying Firefox couldn't load the page and that it may be a problem with my internet or a firewall. But the internet worked fine for regular websites. I came back a while later and nothing would load, the VMWare console or regular websites. Same error each time. Now, the VMWare console works fine, but regular websites will not load. However I still connect to my network with no problems (as far as I can see) and the internet works on other computers on my router.

I cannot figure out what I did to cause this problem. The only thing that I can remember doing incorrectly was during the configuration of VMWare where you hit enter to accept the defaults, I got into a habit of hitting it without reading and selected eth0 as my host connection as bridged, when I really use eth2. Could this be the cause? Or any other thoughts about what could have done it?

Just to be clear, I'm saying I cannot connect to the internet in the host Ubuntu desktop, let alone my virtualized Vista.

---

### Post by dcstar on 2009-11-18
> **JaredFactley said:**
> 
.......
I cannot figure out what I did to cause this problem. The only thing that I can remember doing incorrectly was during the configuration of VMWare where you hit enter to accept the defaults, I got into a habit of hitting it without reading and selected eth0 as my host connection as bridged, when I really use eth2. Could this be the cause? Or any other thoughts about what could have done it?


Rerun the VMware configuration and change the network settings.

---

### Post by JaredFactley on 2009-11-19
> **dcstar said:**
> Rerun the VMware configuration and change the network settings.

Yeah, that was the first thing I tried. Didn't have any effect. 
I didn't have time to figure this out, so I just used it as an excuse to do a fresh install of 9.10 like I've been meaning to do. So I don't have a solution, but no more help is needed. Thanks for the suggestion though.

---

