---
title: "Can't ping client(s)"
date: 2009-01-26
forum: Server Platforms
---

### Post by pi3832 on 2009-01-26
I'm trying to set up a couple of samba shares on my server.  It's not working, so I started through the [Samba checklist]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html"), and never made it past the *ping* test.

So, my clients (all running Windows XP) can ping my server, by IP address or by name.

My server cannot ping any client by name.  It can ping some, but not all, by IP address.  Trying FQDNs makes no difference.

/etc/resolve.conf
```
domain corp.foo.com
search corp.foo.com
nameserver 192.168.41.100
nameserver 192.168.1.100
```

/etc/network/interfaces
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.21.109
        netmask 255.255.255.0
        gateway 192.168.21.1
```

It's probably something simple/stupid, so don't assume anything.

What do I need to check/learn to get my TCP/IP right?  TIA.

---

### Post by windependence on 2009-01-26
You need to add all of your clients to your /etc/hosts file so the server can resolve the names, OR set up DNS, which, unless you have 25+ machines probably isn't worth the trouble. You add entries like this:

```
192.168.0.50    myserver.mydomain.com  myserver
```

Save the file and restart the network.

You also may have the Windoze firewall enabled on some clients and that may be preventing you from reaching them via IP.

Let me know how it works out.

-Tim

---

### Post by cdenley on 2009-01-26
Ubuntu won't resolve netbios names unless you install winbind and configure /etc/nsswitch.conf to use it. It shouldn't be necessary, though. ICMP pings are often filtered by firewalls, but this shouldn't affect your file server.

---

### Post by cariboo on 2009-01-26
I've noticed that sometimes XP with the firewall turned on will not return ping's, and yet other times it will. I have the firewall truned off on my desktop computer that runs XP, but the laptop that runs xp has the firewall turned on, and right now I can ping both of them.

Jim

---

### Post by Hobgoblin on 2009-01-26
> **windependence said:**
> You need to add all of your clients to your /etc/hosts file 

If he can't ping by IP then adding them to the hosts file won't help.

Besides they are probably dynamic IPs.

I would ignore the ones which won't ping for now and continue troubleshooting with those which will.

---

### Post by pi3832 on 2009-01-27
Thanks for all the help.

Turns out that I was able to get Samba working, even though I still can't get hostnames to resolve when pinging.  I just skipped ahead in the Samba checklist and went through the rest of the stuff.

Thanks again.

---

