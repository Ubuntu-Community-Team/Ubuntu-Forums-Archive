---
title: "Neverending wireless woes (Intel 7260)"
date: 2014-03-14
forum: System76 Support
---

### Post by chirpis7 on 2014-03-14
Hi guys,

I'm on Spring Break, so I thought it would be a good time to try and fix my wifi problems. I have two major concerns (I think):

1. Have new drivers been released for the Intel 7260 adapter, or has any other progress been made in correcting its bizarre behavior under Linux/Ubuntu?

2. Has anything been done to address the problem of connecting to WPA-PEAP networks when the administrators don't supply certificates (this is very common at universities)? I've heard rumors that other distros have fixed this. Does anyone know?

I will continue doing my own research, but I'm just wondering if other people have been through this already. It's incredibly frustrating, to the point that I'm dual-booting Windows on this machine just to get things done. I'm tempted to ask System76 to replace my adapter with something older and more stable, but I'm afraid that it would involve waiting a couple of weeks and paying exorbitant shipping costs.

---

### Post by varunendra on 2014-03-16
1. Yes, the support for this device (Intel AC7260) has been improved a lot, and probably you would be able to get full AC speeds with kernel 3.13 (it's still under development it seems, so better let it come naturally with updates). For current solution, please see this post : [http://ubuntuforums.org/showthread.php?t=2204438&p=12924319#post12924319](http://ubuntuforums.org/showthread.php?t=2204438&p=12924319#post12924319)

2. Usually removing the line "system-ca-certs=true" in the connection's "key file" (located in /etc/NetworkManager/system-connections) or changing its value to "false" does the trick.

---

