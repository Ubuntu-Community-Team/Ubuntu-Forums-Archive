---
title: "Is there a way to 'test' your O/S?"
date: 2009-02-23
forum: Security
---

### Post by listerdl on 2009-02-23
Is there a way to see if any ports are open? (I think they are all closed by default?)

I have firestarter installed but I am just curious to know if there is something i should do to prevent a security breach or am i just being paranoid?

---

### Post by HermanAB on 2009-02-23
Run the scan from another machine:
$ sudo nmap -sT -P0 -v -F 1.2.3.4

However, don't worry about it.  Relax and enjoy you nice new secure Ubuntu system.

Cheers,

Herman

---

### Post by Gouki on 2009-02-23
You can also use Nessus[0] to perform a local test on your computer, and makes changes based on the report it generates.

[0] - [http://www.nessus.org/nessus/](http://www.nessus.org/nessus/)

---

### Post by bodhi.zazen on 2009-02-23
I like :

```
lsof -i -n -P
```

Or scanning (nmap) from a remote computer.

---

### Post by xzero1 on 2009-02-23
See shields up on [http://www.grc.com/default.htm](http://www.grc.com/default.htm)

---

### Post by bodhi.zazen on 2009-02-23
Shields up is not such a good tool. It will scan your router but that is not the same thing as HIDS or NIDS.

---

### Post by cdenley on 2009-02-24
I like checking for listening services instead of port scanners. You shouldn't need a firewall to prevent open ports. Fix the problem at the source!
```

sudo netstat -tlnp

```
If you want to test your router, then you need an external port scanner.

---

### Post by bodhi.zazen on 2009-02-24
> **cdenley said:**
> You shouldn't need a firewall to prevent open ports. Fix the problem at the source!

Exactly, this is why we need to ask **why** and **how**someone wants to use a firewall.

It seems in other OS unnecessary services may be running and people are advised to use a firewall. They do not seem to understand what a firewall does or why they need it, they just run it.

There are valid reasons to run a firewall, for example one may wish to limit connections to http, ftp, or ssh. yes these services can also be configured without a firewall.

At the end of the day, a firewall is a tool and to be used properly one needs a little understanding of what they can do with a firewall, a basic understanding of services, and how it is used.

---

### Post by Roofdaddy on 2009-02-24
> **bodhi.zazen said:**
> At the end of the day, a firewall is a tool and to be used properly one needs a little understanding of what they can do with a firewall, a basic understanding of services, and how it is used.

[http://www.interhack.net/pubs/fwfaq/]("http://www.interhack.net/pubs/fwfaq/")

Will this help ?[-o<

---

