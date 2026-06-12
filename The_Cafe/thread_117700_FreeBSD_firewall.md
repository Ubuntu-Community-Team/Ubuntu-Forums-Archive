---
title: "FreeBSD firewall"
date: 2006-01-15
forum: The Cafe
---

### Post by Zelut on 2006-01-15
I know this isn't *technically* Ubuntu related but since this is the most active, most useful forum anywhere on the internet I only post here.

I was thinking about setting up a firewall (just to learn more about IP tables, security, etc).  From what I've read BSD is considered very secure so I thought I would try that.

Can anyone give me any info on this?  Past experience?

Cheers.

---

### Post by BSDFreak on 2006-01-15
[quote=kuyaedz]I know this isn't *technically* Ubuntu related but since this is the most active, most useful forum anywhere on the internet I only post here.

I was thinking about setting up a firewall (just to learn more about IP tables, security, etc).  From what I've read BSD is considered very secure so I thought I would try that.

Can anyone give me any info on this?  Past experience?

Cheers.[/quote]

You won't learn IP Tables from FreeBSD. You have three firewalls to choose from in FreeBSD, it's IPFW, IPFilter and PF. I prefer PF.

After having set up any of them you'll still not know much about setting up a firewall in Linux.

If you are interested in learning how to set up a firewall in Linux (IP Tables) then use Linux for it instead. Want to make it really easy, install firestarter and then look at the config it created.

If you want the most secure system, set up an OpenBSD box and learn to use PF and you'll have an extremely secure box, quite possibly THE most secure box you can have.

---

### Post by Zelut on 2006-01-15
Ok.  I suppose IP tables isn't the best route for full security.. OpenBSD you say?  I'll check it out.  

note: I am not tempted to move away from ubuntu, just wanting to learn something new on one of my extra machines.

---

### Post by BSDFreak on 2006-01-15
[quote=kuyaedz]Ok.  I suppose IP tables isn't the best route for full security.. OpenBSD you say?  I'll check it out.  

note: I am not tempted to move away from ubuntu, just wanting to learn something new on one of my extra machines.[/quote]

[http://www.openbsd.org/](http://www.openbsd.org/)

If you have any questions or problems, feel free to PM me, i'll help you out. :)

---

### Post by curuxz on 2006-01-15
like the new avatar bsd ;)

I to am trying to expand my horizens with bsd systems. Is it good for development web servers, if its fast ?

---

### Post by xequence on 2006-01-15
Isnt the only reason OpenBSD is so secure is the fact everything is turned off by default, and when you accually do things it gets unsecure?

---

### Post by majikstreet on 2006-01-15
learn the freebsd firewall: [http://www.ipfwrocks.org/](http://www.ipfwrocks.org/)

---

### Post by mips on 2006-01-15
[QUOTE=xequence]Isnt the only reason OpenBSD is so secure is the fact everything is turned off by default, and when you accually do things it gets unsecure ?[/QUOTE]

Yes but it is also very stable. As far as I can tell it is regarded as the most secure/stable free OS out there.

Something i'm gonna try in the future.

---

### Post by lotusleaf on 2006-01-15
[QUOTE=xequence]Isnt the only reason OpenBSD is so secure is the fact everything is turned off by default, and when you accually do things it gets unsecure?[/QUOTE]

Just take a look at the history and development info about OpenBSD, it's quite informative. :)

---

### Post by mgor on 2006-01-15
[QUOTE=xequence]Isnt the only reason OpenBSD is so secure is the fact everything is turned off by default, and when you accually do things it gets unsecure?[/QUOTE]

and that's why apache, bind etc. is runned in a chroot by default.

there no way one can't love PF :)

---

