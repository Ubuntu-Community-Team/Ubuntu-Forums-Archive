---
title: "avahi changind to hostname-2 after short time"
date: 2011-04-21
forum: Server Platforms
---

### Post by Vectorferret on 2011-04-21
I have avahi installed on Ubuntu Server 10.10. It broadcasts correctly initially, but after a short time (about 2 minutes) it changes to hostname-2.local instead of it's original hostname. I can manually correct this by restarting the avahi daemon but it only lasts for the two minutes again. Restarting the daemon every few minutes is not practical. Is there any solution to this problem?

---

### Post by ruffEdgz on 2011-04-22
When you do the command:
> hostname
what do you get? If you get 'hostname-2' as the output, then you will have to run the command:
> hostname <your hostname>
which should set the hostname in a file called /etc/hostname.

I checked my computer by running the command:
> avahi-resolve-address 192.168.0.12
(the address above isn't my real address)
From that, I was able to see that my hostname was a part of the avahi-resolve-address output.

Hope this helps.

---

