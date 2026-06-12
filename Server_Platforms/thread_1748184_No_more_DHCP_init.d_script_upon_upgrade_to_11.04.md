---
title: "No more DHCP init.d script upon upgrade to 11.04"
date: 2011-05-03
forum: Server Platforms
---

### Post by Wootchismo on 2011-05-03
I upgraded our server today from 10.10 to 11.04.  I can no longer find the init.d script for the DHCP server.  Does anyone know where it's gone to?

---

### Post by funky_D on 2011-05-05
me neither.
sh#tty upgrade!

---

### Post by smslavin on 2011-05-10
It appears that most of the service start and stop commands are now done like this

sudo service <service name> start

I've been trying to get DHCP working since last night and I found that restarting the service requires the following...

sudo service isc-dhcp-server start

---

### Post by mrhelpman on 2011-05-10
> **Wootchismo said:**
> I upgraded our server today from 10.10 to 11.04.  I can no longer find the init.d script for the DHCP server.  Does anyone know where it's gone to?

I am still running 9.10 as this is the last distribution that would run the real-time kernel on my 10 year old Dell desktop.  I have the same DHCP failure since an upgrade at the weekend.

I got the network working again by entering my routers IP address into the gnome network manager application under the field "DHCP client". This has just by passed the problem and until proven otherwise I would say that dhcp has stopped working.

John T.

---

