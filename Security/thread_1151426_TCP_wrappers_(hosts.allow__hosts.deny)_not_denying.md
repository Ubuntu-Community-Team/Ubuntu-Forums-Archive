---
title: "TCP wrappers (hosts.allow / hosts.deny) not denying"
date: 2009-05-06
forum: Security
---

### Post by Pseudonomous on 2009-05-06
Hello Everybody,

I'm somewhat new to the Debian/Ubuntu world, I've been using Arch Linux for about a year and half (and still am on my non-desktop machine), anyway, I'm trying to setup a secured remote access via ssh and I'm trying to deny hosts using tcp wrappers but it doesn't seem to be working.

Currently my hosts.allow file is empty and my hosts.deny file looks like:
```

ALL : ALL
```
this is based off of advice from:
[http://ubuntuforums.org/showthread.php?t=937270&highlight=hosts.allow](http://ubuntuforums.org/showthread.php?t=937270&highlight=hosts.allow)

I've also tried copying the hosts.allow file from my laptop (running arch linux):
```

ALL: ALL: DENY

```
On which I *know* the tcp wrappers work.

But either way I can still login from laptop, which *should* be denied.  So I'm wondering why this isn't working; I have the same problem with a virtual machine running Debian.  There are obvious ways to sidestep this problem, e.g. use a firewall instead of tcp-wrappers, but I'd still like to know why this doesn't work.  Any help would be appreciated.

Thanks!

---

### Post by dragos_iliescu_2005 on 2009-05-07
Maybe you just need to setup a firewall rule for ssh protocol. In this way you can control who are allow for connect very accurate.

---

### Post by bodhi.zazen on 2009-05-07
it works just fine, the problem I am guessing is you need a new line (carriage return)

> ALL: ALL[INDENT]#Note carriage return[/INDENT]And as proof :

```
 ssh root@192.168.1.7
[COLOR=red]ssh_exchange_identification: Connection closed by remote host[/COLOR]
```

---

### Post by Pseudonomous on 2009-05-08
> **bodhi.zazen said:**
> it works just fine, the problem I am guessing is you need a new line (carriage return)


Indeed you are right; sometimes it's the little things ...

[QUOTE=dragos_iliescu] 	
Re: TCP wrappers (hosts.allow / hosts.deny) not denying
Maybe you just need to setup a firewall rule for ssh protocol. In this way you can control who are allow for connect very accurate.
[/QUOTE]

I may eventually setup a firewall, but for now this is overkill; I've got some scripts relying on dns utils and tcp wrappers that work very well for my needs and ssh is the only service I expose to the internet (I have a router / firewall as my adsl modem).

---

### Post by kevdog on 2009-05-08
Im constantly in amazement about how much trivial but useful knowledge bodhi seems to have in his brain!  Simply an amazing, elegant solution!!!

Isn't pseudomonas a gram negative water loving bacteria?

---

