---
title: "Free Online Security Check"
date: 2009-08-04
forum: Security
---

### Post by YMS_1975 on 2009-08-04
Hi,

I was wondering if anybody knew of a free online security test website that will work with Ubuntu.

There are some out there, but most of them require Windows. I'm just curious as to how secure my OS is out of the box.  :D

By the way, I already know of [Shields Up]("https://www.grc.com/x/ne.dll?bh0bkyd2").

---

### Post by cdenley on 2009-08-04
> **YMS_1975 said:**
> Hi,

I was wondering if anybody knew of a free online security test website that will work with Ubuntu.

There are some out there, but most of them require Windows. I'm just curious as to how secure my OS is out of the box.  :D

By the way, I already know of [Shields Up]("https://www.grc.com/x/ne.dll?bh0bkyd2").

All any website can do is check to see if you have any listening processes. This is what shields up does. Ubuntu has no listening TCP processes out of the box. However, if you connect to the internet through a router, you will be scanning your router, not your computer.

Perhaps a page can check your browser for known javascript or flash exploits, but I never heard of such a page. If you keep firefox and flash updated, this shouldn't be an issue. If you want to protect from unknown vulnerabilities, use noscript.
```

sudo apt-get install mozilla-noscript

```

If you want to verify you have no listening processes:
```

sudo netstat -tulnp

```
All you should see is dhclient and avahi, and maybe cups listening on 127.0.0.1.

So, to summarize, the only "security scanner" websites you are likely to find will be a port scanner similar to "shields up", which is (in my opinion) useless under most circumstances.

---

### Post by sasho_zl on 2009-08-04
[http://nmap-online.com/](http://nmap-online.com/) - one of the best port scanners out there.
[http://hackertarget.com/free-security-vulnerability-scans/](http://hackertarget.com/free-security-vulnerability-scans/) - here are some more strong and different security auditing tools.
Good luck!

---

### Post by Rob_H on 2009-08-04
What aspect of Ubuntu's security are you trying to assess? There are lots of tools out there, but to help us narrow it down, it might help to explain what has you worried.

---

### Post by fbnaia on 2009-08-04
Well not exactly websites, but lynis is now on the repos, latest version at [http://www.rootkit.nl/projects/lynis.html]("http://www.rootkit.nl/projects/lynis.html")

As for the hardening itself you can try Bastille, also installable from the repos, more info at [http://www.bastille-unix.org/]("http://www.bastille-unix.org/")

---

### Post by YMS_1975 on 2009-08-06
Thanks for the tips guys. I'll look into all the options (noscript, lynis, etc.).

As for what exactly was bothering me (in terms of security and not my own personal problems  :D) was whether or not I could visit a website, and have some sort of a malicious virus/script dropped onto my PC without me even knowing.

Here's where the fear set in. Like many, I came from a Windows environment and of course had both a firewall & antivirus. Now I have none, now that I'm using Ubuntu. I'm just using Ubuntu as is.

Anyways, one day (when I was still using Windows) Nortons 360 Internet Security pops up telling me my PC was "attacked" but Norton's had neutralized it (or something to that effect). 

So after that, I started to question just how safe is Ubuntu without any firewall or antivirus. If a website could simply attack my Windows computer without me downloading or installing anything, I got worried about having no protection on Ubuntu.

---

### Post by cariboo on 2009-08-06
If you are worried about malicious scripts on web sites, use the Firefox noscript addon.

---

### Post by cdenley on 2009-08-06
> **YMS_1975 said:**
> Thanks for the tips guys. I'll look into all the options (noscript, lynis, etc.).

As for what exactly was bothering me (in terms of security and not my own personal problems  :D) was whether or not I could visit a website, and have some sort of a malicious virus/script dropped onto my PC without me even knowing.

Here's where the fear set in. Like many, I came from a Windows environment and of course had both a firewall & antivirus. Now I have none, now that I'm using Ubuntu. I'm just using Ubuntu as is.

Anyways, one day (when I was still using Windows) Nortons 360 Internet Security pops up telling me my PC was "attacked" but Norton's had neutralized it (or something to that effect). 

So after that, I started to question just how safe is Ubuntu without any firewall or antivirus. If a website could simply attack my Windows computer without me downloading or installing anything, I got worried about having no protection on Ubuntu.

The "attack" you refer to is probably an attempt at exploiting a javascript vulnerability in your browser. It could have even been a false positive. Browser vulnerabilities are discovered often, but they almost always require javascript or flash. If the site isn't trusted by the noscript plugin, it can't exploit any vulnerabilities. This will protect you from known and unknown exploits. If you keep firefox up-to-date with security updates, then you don't have to worry about known exploits, which is probably all that Norton product you mentioned can protect you from.

Anti-virus isn't needed on ubuntu. There are no viruses, but there can be malware. However,the malware can only execute if you intend to execute it. If you don't execute anything that didn't come from the ubuntu repo's, you're safe from malware. Just make sure you keep your packages updated.

---

### Post by Bucky Ball on 2009-08-06
A windows virus will pass THROUGH Ubuntu to a Windows machine in a network perhaps, but not many viruses written for Linux and not easy to get in (unless you leave a window open).

MS/Linux ... they speak different language.

---

### Post by munky99999 on 2009-08-07
1. If they dont get anything on ur system. It wont be very accurate.

2. If they do get something on ur system. It wont be very secure itself.

That being said.

Nmap online in order to do the first one.

Secunia's online scanner is a trusted one.

[http://secunia.com/vulnerability_scanning/online/](http://secunia.com/vulnerability_scanning/online/)

---

