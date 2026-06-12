---
title: "i keep connecting to strange server... can someone tell me what is it?"
date: 2011-03-12
forum: Security
---

### Post by werty2010 on 2011-03-12
the addresses are 95.143.195.138 and 89.248.172.13
some info about these addresses would be helpful...?

---

### Post by sandyd on 2011-03-12
> **werty2010 said:**
> the addresses are 95.143.195.138 and 89.248.172.13
some info about these addresses would be helpful...?
[http://whois.domaintools.com/95.143.195.138](http://whois.domaintools.com/95.143.195.138)
[http://whois.domaintools.com/89.248.172.13/](http://whois.domaintools.com/89.248.172.13/)

[http://onsamemachine.com/89.248.172.13/](http://onsamemachine.com/89.248.172.13/)

---

### Post by Frogs Hair on 2011-03-12
The first is in Sweden , and the second is in the Netherlands

---

### Post by werty2010 on 2011-03-12
thank you but when i say info i mean further info about these servers like are they a part of a special-public service available to anyone or something else
the reason im asking is because my pc randomly connects to those servers without knowing why

---

### Post by adduds on 2011-03-13
sounds fishy? someone using ur computer to connect througha proxy?

---

### Post by fabricator4 on 2011-03-13
> **werty2010 said:**
> 
the reason im asking is because my pc randomly connects to those servers without knowing why

When you say "connects", what exactly is your computer doing? 

Are you running a router with a firewall?  Made any changes to security or firewalls?

Turn on your router firewall if it isn't already.  If it keeps on happening you can deny connections based on an IP address or range of addresses.  My router emails me any time there is an attempt on it, normally several times per week.  I stopped looking - as long as it's keeping the blighters out I'm happy.

Try:

```

netstat -W | grep tcp

```

And look for anything... well odd.

A couple of times today my netbook has asked for the keyring to be authenticated.  As far as I know I wasn't doing anything that would require authenticating, just browsing. I was already connected to the internet and my alternate connection that requires authentication wasn't even enabled.  Nothing stopped working or failed to work because I denied access to the keyring. :shock:

I'm no expert in this area so see what others have to say.

I also found this with a google search:

```

sudo nmap -sS -O 127.0.0.1

```

You'll have to install nmap.  It scans for open ports which might be used by someone else.  This machine says no ports open - 999 closed ports.  I'm about to hop over and try it on my netboook.


Chris

---

### Post by uRock on 2011-03-13
Moved to Security Discussions sub-forum.

---

### Post by fabricator4 on 2011-03-13
> **fabricator4 said:**
> 
```

sudo nmap -sS -O 127.0.0.1

```
You'll have to install nmap.  It scans for open ports which might be used by someone else.  This machine says no ports open - 999 closed ports.  I'm about to hop over and try it on my netboook.

Eeek!  I'm showing port 22 being open.  A look in /etc/services shows

```

ssh             22/tcp                          # SSH Remote Login Protocol

```

I didn't open this port, and I don't believe I've got remote access enabled anywhere.  I deleted remote desktop because I had no intention of using it.  I shall start a new thread...

Chris

---

