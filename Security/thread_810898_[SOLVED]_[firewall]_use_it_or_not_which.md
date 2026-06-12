---
title: "[SOLVED] [firewall] use it or not? which?"
date: 2008-05-28
forum: Security
---

### Post by kakyoism on 2008-05-28
Hi, 

I wonder whether or not I should use a firewall on my system (laptop/desktop), at a home wlan and lan at school, respectively.
I use torrent and emule a lot, take care of bank transactions online,
plus regular emailing and IMs. Before I switched to Ubuntu, I've been using
Norton on Windows, which was a failure in many cases. But I don't know if it'd be absolutely necessary to run a firewall on Ubuntu, because it's supposed to be a lot better in security aspect. 

If I do have to use one, is *firestarter* good enough?
I'm new to these network security issues and have really limited knowledge about networking. Where should I start if I do need to?
Thank you.

---

### Post by AlanR8 on 2008-05-28
Rightly or wrongly, I run no firewall or virus protection on my Kubuntu boxes. I rely on the firewall in my router.

18 months down the line I've had ZERO issues.....

The wife's XP box has been rebuilt twice in the same time frame!

---

### Post by borkborkbork on 2008-05-28
Regardless of necessity, would it hurt to install one? Its better to have and not need, then need and not have.



(why are my coffee beans all goofy?)

---

### Post by AlanR8 on 2008-05-28
Why bother

---

### Post by borkborkbork on 2008-05-28
It does not require a large amount of time to install and configure a firewall, so there is no harm in doing so.

---

### Post by kakyoism on 2008-05-28
thx, 

because i've experienced weird network debugging before, and firewalls, in peaceful times, always give me headaches...

so be it difficult to install or not,  i'd rather do it when it's absolutely necessary.

so please give an idea how i am gonna run into cumbersome authorization for sth that's really harmless and stuff...

thx.

---

### Post by Dr Small on 2008-05-28
Having a firewall on each system that is behind a router with a built in firewall is nonsense. I did it for several months, and then found out that every little application that the other network computers need to connect to me (Samba, HTTP, SSH, Bzflag, etc), I had to open a port.

It is much simpler now that I do not have a firewall, and just let my router handle all incoming requests from the internet.

By the way, Firestarter is _not_ a firewall. It simply manages the firewall (iptables) in a unique graphical way. It in itself is not a firewall.

Dr Small

---

### Post by lisati on 2008-05-28
> **AlanR8 said:**
> Why bother

It's a matter of personal choice. If you're not at risk, then there's no need. A bigger danger exists if you **think** you're not at risk when you are. The only truly secure computer is one which is not connected to anything else.

---

### Post by hyper_ch on 2008-05-29
(1) do you run any services on your computer? If no, then you don't need a firewall

(2) if you run services, do you use the computer only at home (behind a router) or in firewalled networks? --> If any is yes, then you don't need a firewall

(3) if you run services and if you do run your computer in "untrusted" networks then you might need a firewall

---

### Post by T-Virus on 2008-05-29
I use Firestarter myself and I don't see a point why I shouldn't. It blocks unnecessary ports, etc. If you're on Unix or Linux it doesn't make you 100 percent safe. That's what I think.

---

### Post by T-Virus on 2008-05-29
> **lisati said:**
> It's a matter of personal choice. If you're not at risk, then there's no need. A bigger danger exists if you **think** you're not at risk when you are. The only truly secure computer is one which is not connected to anything else.

Oh, and truly secure computer is the one that is powered off. :)

---

### Post by hyper_ch on 2008-05-29
and in your bank's vault :)

---

### Post by kevdog on 2008-05-29
Ubuntu's firewall is known as IpTables.  Its possible to manually edit the Iptables by hand, however for beginners its often easy if a program does it automatically.  Firestarter is such a program that modifies the IPtables in a very easy way.  If you are on Kubuntu, Guarddog is the Firestarter equivalent.  (I actually prefer Guarddog to Firestarter but that is my personal opinion).

You only really need a firewall if you are running open ports or running a server that is transparent to the outside world.  The Iptables are able to block by port number, IP address, access time, etc.  They are actually quite powerful.  If you are not running any services that are visible to the outside world, then you really don't need a firewall, since no service or daemon is listening for outside connections.  I suppose if you were really paranoid, in addition to blocking incoming ports, you could block outgoing ports in addition, however this would take a lot of trial and error since many outgoing ports are probably used frequently on your computer (sudo netstat -an <---Will show you what I mean). 

Evaluate your needs.  If you think you need a firewall, go with Firestarter initially.  Its fairly easy to understand.

---

### Post by kakyoism on 2008-05-29
thx guys and especially you kevdog.
That explained a lot!

---

