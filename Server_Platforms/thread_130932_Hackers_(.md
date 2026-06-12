---
title: "Hackers :("
date: 2006-02-15
forum: Server Platforms
---

### Post by Mr.X on 2006-02-15
WTF?
[img]img124.imageshack.us/img124/3186/hack13dv.png[/img]
Blocked out his IP, can anyone check if the ip was ever registered here? Thanks :neutral:

---

### Post by deBaas on 2006-02-15
Come on, nothing happened. Port 600 can be anything. Nothing to worry about.

---

### Post by Harold P on 2006-02-15
It's odd because it shows a weird hostname.

---

### Post by MJN on 2006-02-16
Weird hostname? *88-105-83--184.dynamic.dsl.as9105.com*? Quit simply a Tiscali DSL customer... (AS9105 is one of Tiscali's AS numbers)
 
Mathew

---

### Post by ice60 on 2006-02-16
hi, i don't understand why the exact same scan a few seconds before only showed the IP then when the attacker did the same scan a few seconds latter Mr.X's firewall performed a reverse DNS. why did it happen?

---

### Post by MJN on 2006-02-16
I'm not familiar with Firestarter however with many firewalls the user must explicitly request a reverse lookup for a log entry (it can get very confusing otherwise) - perhaps this was the case here and he only clicked that one (I note it is highlighted)...?

Mathew

---

### Post by ice60 on 2006-02-16
[QUOTE=MJN]I'm not familiar with Firestarter however with many firewalls the user must explicitly request a reverse lookup for a log entry (it can get very confusing otherwise) - perhaps this was the case here and he only clicked that one (I note it is highlighted)...?

Mathew[/QUOTE]
that's what i thought, i wasn't sure though. lol, i'm confused too by the Xwindows bit, but i'm not a network expert and i'm a Linux newbie :(   

>  can anyone check if the ip was ever registered here?
what were you up to?

 MrX there are some more columns you can add like in the screenshot, it won't help loads but it's something. i can't believe how active bittorrent is on this IP, i've just reconfigured it to not log port 6881, i'm glad i opened it to have a look now.

---

### Post by Mr.X on 2006-02-17
I did a lookup for the IP.:rolleyes: 
Should i contact ISP? :p

---

### Post by Mr.X on 2006-02-17
OH, i meant all the above, not just the one selected :p

---

### Post by suRoot on 2006-02-21
Looks like they were just running a port scan on you - it happens all the time.  If it bothers you, unplug your computer from the Internet, cause there's not a lot you can do about it.

You don't need to contact the ISP unless you have proof the guy hacked your machine & gained access (which doesn't appear to be the case here).  Sorry, but the ISP isn't going to do anything about it.

The firewall did exactly what it was supposed to do.  It blocked the connection.

---

### Post by tenshu on 2006-02-21
this is what you can call "internet noise"
don't worry about this
our linux are up to date
and there are sooooo few chances that those attack can pass through ...

---

### Post by LordHunter317 on 2006-02-21
This is why I hate firewalls that show people logs.  If you have to ask what the log did, chances are nothing bad happened.

There's a ton of noise on the Internet.  Boxes that get port scanned 100s of times an hour aren't unheard of.

---

### Post by Mr.X on 2006-02-23
[QUOTE=suRoot]Looks like they were just running a port scan on you - it happens all the time.  If it bothers you, unplug your computer from the Internet, cause there's not a lot you can do about it.

You don't need to contact the ISP unless you have proof the guy hacked your machine & gained access (which doesn't appear to be the case here).  Sorry, but the ISP isn't going to do anything about it.

The firewall did exactly what it was supposed to do.  It blocked the connection.[/QUOTE]

Thanks for all your answers.

I use to run a gameserver, i got portscans, people trying to run MSSQL exploits, people trying to flood etc about 30 times an hour. Probably people still trying to connect, and trying to hack.

---

### Post by Kurt` on 2006-02-23
[QUOTE=Mr.X]Thanks for all your answers.

I use to run a gameserver, i got portscans, people trying to run MSSQL exploits, people trying to flood etc about 30 times an hour. Probably people still trying to connect, and trying to hack.[/QUOTE]
Those aren't necessarily 'people' with ill intent... there are alot of infected Windows boxen connected to the internet you know. ;)

(and the occasional rooted bsd/nix box)

The only thing you can do is secure your own end, going after the "attackers" (who probably don't even realize their computer is being used by someone else) isn't really going to solve anything.

---

