---
title: "Vpn"
date: 2009-09-10
forum: Server Platforms
---

### Post by bigboy7foru on 2009-09-10
Has anyone Built one before?
 
I need assistance!!!

---

### Post by ainsworth_t on 2009-09-10
I've actually been reading around on the subject the past few days. Still feel a little lost, but picking up some of it.

What are you needing the VPN to do? i.e for roadwarriors or bridge two subnets? Also what type (IPSec, SSL, PPTP) are you looking to implement?

---

### Post by bigboy7foru on 2009-09-10
Both roadwarriors and bridge two subnets.
 
We are running it on ssl
 
just having a few problems getting it up and established

---

### Post by ainsworth_t on 2009-09-10
> just having a few problems getting it up and established
...such as?

---

### Post by bigboy7foru on 2009-09-10
we were getting a prompt that says: 
 
[I]Can not write openvpn server sysinit script here: 
/etc/rc.d/init.d/gadmin-openvpn-server [/I]
 
*and we did a command line thing to fix it but now it does nothing *

---

### Post by ainsworth_t on 2009-09-11
How did you install it? Did you install OpenVPN from the Ubuntu repositoris or did you download and install the access server .deb from the OpenVPN site?

---

### Post by bigboy7foru on 2009-09-11
OK we installed GADMIN from Synaptic
 
we made the certificates and have it almost running now but we ran into a hicup
 
we have an error:   TCP/UDP: Socket Bind failed on local address 216.253.219.22:1194: Cannot assign requested address

---

### Post by thefunnyman on 2009-09-11
> **bigboy7foru said:**
> OK we installed GADMIN from Synaptic
 
we made the certificates and have it almost running now but we ran into a hicup
 
we have an error:   TCP/UDP: Socket Bind failed on local address 216.253.219.22:1194: Cannot assign requested address

Make sure that openvpn isn't running and currently using that port.  I bet that's what's going on.

HTH

---

### Post by bigboy7foru on 2009-09-11
Well we shut down the machine several time and it keeps geting that error... would it still be open if we shut the computer down??

---

### Post by ainsworth_t on 2009-09-14
Usually when a service is installed on Linux, it creates an autostart script so the service will start at bootup. Therefore, whenever you reboot the box, it will start up again. Instead of bringing down the entire system, try stopping the service
```
sudo /etc/init.d/openvpn stop
```

---

### Post by bigboy7foru on 2009-09-15
Would that give me that error i posted above?

---

### Post by ainsworth_t on 2009-09-16
That I'm not sure of. You're problem is probably outside my understand now. Have you tried using the ubuntu community documentation as a guide for your setup? [https://help.ubuntu.com/community/VPNServer](https://help.ubuntu.com/community/VPNServer)

---

### Post by bigboy7foru on 2009-09-16
no but ill try it thanks
 
> **ainsworth_t said:**
> That I'm not sure of. You're problem is probably outside my understand now. Have you tried using the ubuntu community documentation as a guide for your setup? [https://help.ubuntu.com/community/VPNServer](https://help.ubuntu.com/community/VPNServer)

---

### Post by bigboy7foru on 2009-09-25
so its stil not fixed i have gotten alot more done since last time but im not sure

---

### Post by thefunnyman on 2009-09-25
> **bigboy7foru said:**
> so its stil not fixed i have gotten alot more done since last time but im not sure

reboot the machine and post the output of the following commands:

```

sudo netstat -tnap

```
and
```

dmesg

```
Maybe that will help figure out what the heck is going on...

---

### Post by bigboy7foru on 2009-09-25
ok im rebooting nowopenvpn Cannot assign requested address

---

### Post by thefunnyman on 2009-09-25
> **bigboy7foru said:**
> ok im rebooting nowopenvpn Cannot assign requested address

and the output of the commands I posted?

---

### Post by bigboy7foru on 2009-09-29
> **thefunnyman said:**
> and the output of the commands I posted?
 
 
i lost all internet connections
 
i was gone this weekend but am trying to restore them

---

### Post by El Menda on 2011-01-05
> **bigboy7foru said:**
> OK we installed GADMIN from Synaptic
 
we made the certificates and have it almost running now but we ran into a hicup
 
we have an error:   TCP/UDP: Socket Bind failed on local address 216.253.219.22:1194: Cannot assign requested address

I know it's late, but I solved this error commenting in openvpn.conf the line:

local #.#.#.#

---

