---
title: "Firewall help for a webserver"
date: 2006-02-04
forum: Server Platforms
---

### Post by spyke01 on 2006-02-04
does anyone have some advice for setting up a firewall for a webserver, ill be using ftp, apache, mysql, and maybe a mailserver(not sendmail)

i want to know what people would suggest for the program, and an example setup

---

### Post by lol on 2006-02-05
AFAIK, The "default" firewall on Ubuntu is Firestarter, but the one I would recommand is Shorewall. It is a really simple backend to iptable, easy to configure and yet quite powerfull.

---

### Post by LordHunter317 on 2006-02-05
There is no "default" firewall.

And why are you setting one up?  Use the configuration to limit listening wherever possible.  A firewall should only be enabled when you cannot guess a sane default policy, or when you cannot control where the server listens.  For apache, neither is the case, and it's just as easy to provide control over where it listens.

---

### Post by dbee on 2006-02-06
Can you explain that point a little further pls LH ?

Am I right in interpreting that as suggesting that a webserver shouldn't have a firewall if possible ? :???:

---

### Post by LordHunter317 on 2006-02-06
Yes.  There's no need with Apache anyway, you can limit what it does and doesn't listen to, and what hosts it does and doesn't respond too, via it's configuration.

And that's usually preferable than using a firewall to do the same.  A firewall would only be used if you wanted to completely deny a host access to all services.

Even then, that's usually better done at network egress/ingress, because on a real network you have multiple servers and you don't want them talking to any of them.

As a rule for servers, host-based firewall usually isn't necessary, unless the server is a lone-box on an untrusted network (e.g., at a colo) or unless the box is performing actual router duties.

---

