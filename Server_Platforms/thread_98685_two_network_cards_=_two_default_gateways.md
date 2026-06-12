---
title: "two network cards = two default gateways?"
date: 2005-12-03
forum: Server Platforms
---

### Post by ZylGadis on 2005-12-03
Hello,
As the topic says, I have two network cards connected to different networks on a Breezy that I'm running as a server. When I configure the network through the GUI app in System->Administration, it sets a default gateway for each of the two network cards. Clicking all kinds of buttons does not help (yes, I know there is a "default gateway" button, it does nothing). Needless to say, that screws the routing table and I have to manually 'route del' one of the gateways.
Of course, when I reboot, the two gateways are again up.
Is there an intelligent Ubuntu-like way to solve the problem, or do I have to tinker with disabling the networking GUI and/or including the 'route del' somewhere in the startup scripts?
Thanks

---

### Post by cactus on 2005-12-03
i generally just write a /etc/networking/interfaces by hand if the network gui tool fails me for whatever reason. I only have to do it with my wireless interfaces mostly, for whatever reason..

if you are unfamiliar with the interfaces file syntax, the man 5 page is quite reasonable (man 5 interfaces).

I have no mastery over this file, but I have workable knowledge.. if you have a specific question, I *might* be able to help.. no guarantees though. ;)

---

### Post by ZylGadis on 2005-12-04
Thanks :)
By looking at the man page of interfaces I saw what was going on. In order to not have a default gateway for a card, simply do not set a gateway, i.e. leave the field blank in the GUI.
If you're using more than one card with DHCP, though, you are out of luck. I did not see an obvious way to not set a default gateway for a DHCP scenario. Perhaps the "default gateway" button works then?

---

### Post by cactus on 2005-12-04
maybe. I honestly can't say. None of my ubuntu boxen have more than one nic active at a time...
;)

---

### Post by J.C. Denton on 2005-12-04
[QUOTE=Alex.P]
If you're using more than one card with DHCP, though, you are out of luck. I did not see an obvious way to not set a default gateway for a DHCP scenario. Perhaps the "default gateway" button works then?[/QUOTE]
It's my understanding that when you do DHCP for an interface, you can't really "reject" the defaulte gateway assignment.  Are you in control of that DHCP server?

---

### Post by LordHunter317 on 2005-12-04
Yes, you can, via various configuration directives for dhclient.  You can use supersede to totally override a directive from the DHCP server, for example.

---

### Post by J.C. Denton on 2005-12-05
[QUOTE=LordHunter317]Yes, you can, via various configuration directives for dhclient.  You can use supersede to totally override a directive from the DHCP server, for example.[/QUOTE]
*My mistake, I meant to say:*
I don't think there's anyway to override the gateway setting given from the dhclient command line (i.e., # dhclient eth0).

It was my understanding that one could "override" a presented setting in dhclient.conf, with something like:
```

       interface "eth0" {
           supersede routers "blah";
       }
```

...or you could just "request" only specific things.  Or am I mis-reading something?

---

