---
title: "Is this enough?"
date: 2011-04-12
forum: Security
---

### Post by fela on 2011-04-12
I have a Debian server, behind an ADSL2+ modem/router.

A non-standard port is forwarded to it for SSH access (ie. one that's not 22), root login is disabled, and password authentication is disabled - so to login, you need an authenticated, valid SSH2 private key.

Ports 21, <undisclosed SSH port>, 80, 443, 25565, 16491, 9090, 993, 465, 143, 110 and 25 are all forwarded to it, however, ports 993, 21 and 465 are closed.

Anyone other than me that logs on to the system logs on as an under-privileged user who can't read most of the data in the system and is only a member of one group.

So, I'm not terribly worried about security issues on the server, as it's pretty tight at the moment. However, my home network contains three Windows 7 machines, two (other) Linux machines and one Windows XP (!) machine (that wasn't my choice :)).

So do you know of any vulnerability tests that I can run on all the computers in my network, looking for ways a potential luser could destroy my systems?

Thanks (oh and tell me if I'm being super-paranoid, ultra-laid back or rightly concerned :D)

Also, congratulations me on my 999th bean :P

---

### Post by bodhi.zazen on 2011-04-12
Penetration testing is a complex topic and IMO beyond a forms post.

If you have a specific question about a specific application perhaps we can help.

Otherwise take a look at the tools included in backtrack or OpenVAS and learn to use them.

---

### Post by fela on 2011-04-12
> **bodhi.zazen said:**
> Penetration testing is a complex topic and IMO beyond a forms post.

If you have a specific question about a specific application perhaps we can help.

Otherwise take a look at the tools included in backtrack or OpenVAS and learn to use them.

Okay. I think I've decided to keep all vital data on the server. That way, all the other PCs in the network are just clients in terms of data access / storage.

---

### Post by EJeanmaire on 2011-04-12
You have quite a few ports open/forwarded to this server, you'll have to keep an eye open on the server quite a bit.  SSH seems pretty well locked down, but you have quite a few other services you might need to harden.

Vulnerability scan -> Download NESSUS, you can get a copy for free for home use, the plugins are delayed a bit versus the professional version, but that shouldn't be a problem.

---

### Post by fela on 2011-04-12
Hmm, well it's operating as an e-mail server (partly why so many ports are forwarded to it), but the only email it does is PHP auto-emailing people about stuff on the websites that it runs.

I'll download nessus and see what that does, cheers :)

---

### Post by bodhi.zazen on 2011-04-12
> **EJeanmaire said:**
> You have quite a few ports open/forwarded to this server, you'll have to keep an eye open on the server quite a bit.  SSH seems pretty well locked down, but you have quite a few other services you might need to harden.

Vulnerability scan -> Download NESSUS, you can get a copy for free for home use, the plugins are delayed a bit versus the professional version, but that shouldn't be a problem.

> **fela said:**
> Hmm, well it's operating as an e-mail server (partly why so many ports are forwarded to it), but the only email it does is PHP auto-emailing people about stuff on the websites that it runs.

I'll download nessus and see what that does, cheers :)

FYI: 

OpenVAS is the open source nessus.

[http://www.openvas.org/](http://www.openvas.org/)

---

### Post by SeijiSensei on 2011-04-13
> So do you know of any vulnerability tests that I can run on all the computers in my network, looking for ways a potential luser could destroy my systems?

You can use **nmap** to scan all the machines on the network to see if they have open ports.

---

### Post by fela on 2011-04-13
> **SeijiSensei said:**
> You can use **nmap** to scan all the machines on the network to see if they have open ports.

Thanks, I'll try that.

Also, I downloaded OpenVAS, but have yet to put it on a USB / DVD. Tried booting it on Virtualbox but hung somewhere (can't remember where).

---

### Post by EJeanmaire on 2011-04-13
> **bodhi.zazen said:**
> FYI: 

OpenVAS is the open source nessus.

[http://www.openvas.org/](http://www.openvas.org/)

Ah, good to know.

---

### Post by josephmills on 2011-04-14
> **bodhi.zazen said:**
> FYI: 

OpenVAS is the open source nessus.

[http://www.openvas.org/](http://www.openvas.org/)

+1 thanks I did not know either

---

