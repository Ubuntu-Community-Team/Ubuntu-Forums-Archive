---
title: "DHCP3 Per-User Gateway"
date: 2010-02-11
forum: Server Platforms
---

### Post by SectorNine50 on 2010-02-11
So this might seem a little weird, but I would like my DHCP3 server to assign certain clients to a different gateway.

Essentially this is what's happened, we have 2 different townhouses which have 2 different internet connections.  However, our ISPs have a bandwidth cap that is awfully annoying when you are trying to share files with your neighbor.

What we have done, is combined the two networks, and up 'til now, we have had each user assign their gateway manually.  However, the less tech-savvy users have issues when they take their laptops elsewhere, understandably.

I have the computers and their mac addresses all set-up, but I cannot for the life of me find a parameter that allows me to assign a gateway to them.  Is there something I'm missing?

Thanks for the help in advance.

---

### Post by jonrich on 2010-02-11
This works for me.  Hope it helps.

( /etc/dhcp3/dhcpd.conf )

host iphone {
hardware ethernet [your mac address];
fixed-address 192.168.0.9;
option routers 192.168.0.1;
option domain-name-servers 192.168.0.2;
}

---

### Post by Adina on 2010-02-11
maybe try to set a static route between the two networks, then you can have a dhcp server on each network.

---

### Post by SectorNine50 on 2010-02-11
> **jonrich said:**
> This works for me.  Hope it helps.

( /etc/dhcp3/dhcpd.conf )

host iphone {
hardware ethernet [your mac address];
fixed-address 192.168.0.9;
option routers 192.168.0.1;
option domain-name-servers 192.168.0.2;
}

I have something similar to this set up right now, is the fixed address and option domain-name-servers parameters required to get this to operate the way I want?

Here's what I have now:
host <hostname> {
hardware ethernet <mac address>
option routers 192.168.1.3
}

I'd prefer to have the DHCP server assign the IP if I can, if not, no real big deal, just uniformity I suppose! :p

> **Adina said:**
> maybe try to set a static route between the two networks, then you can have a dhcp server on each network.

I'm not very well read on static routes, what do I do to go about this?

---

### Post by SectorNine50 on 2010-02-11
Oh man, I feel kind of silly now...

The script I had in there worked, I just was restarting the networking without actually restarting the dhcp3-server.  Once I restarted the server everything worked perfectly.  Thanks for your help guys!

---

### Post by jonrich on 2010-02-11
Ahhhh yes, the famous tech support fix, "Have you restarted the computer?"  Actually, this is the first question I ask when one of my users calls into the help desk. ( 9 out of 10 times, it works )

---

