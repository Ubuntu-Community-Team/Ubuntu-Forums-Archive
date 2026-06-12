---
title: "measures against rootkits"
date: 2018-10-15
forum: Security
---

### Post by mike442 on 2018-10-15
Hi
anything we can do against rootkits?
I've put a passwork on the bios so hopefully this prevents the worst?
Thanks

---

### Post by wyliecoyoteuk on 2018-10-15
A Bios password won't stop rootkits.

try this:

```
sudo apt install lynis
sudo lynis audit system
```

which will tell you of vulnerabilities, and advise how to improve your security.

[https://cisofy.com/documentation/lynis/get-started/#first-run](https://cisofy.com/documentation/lynis/get-started/#first-run)

---

### Post by mike442 on 2018-10-16
Thanks I'll try that although I'd be surprised if it finds the Firefox vulnerability in 18.04 by which my system was hacked. (see thread I was hacked)
A Bios Password should hopefully not let rootkits write to bios.

---

### Post by HermanAB on 2018-10-19
Relax and enjoy your Linux system.  

You should probably worry more about lightning and gamma rays killing your kit, than rootkits.

---

### Post by mcyber4 on 2018-10-29
No I've been hacked the first time since 1998 on Linux! See "I was hacked" thread. Maybe it was this:
[https://arstechnica.com/information-technology/2018/10/x-org-bug-that-gives-attackers-root-bites-openbsd-and-other-big-name-oses/?comments=1&post=36258117#](https://arstechnica.com/information-technology/2018/10/x-org-bug-that-gives-attackers-root-bites-openbsd-and-other-big-name-oses/?comments=1&post=36258117#)
Has this been fixed?

---

### Post by mcyber4 on 2018-11-07
After that professional hack I might get paranoid, but I have the impression that I get support question emails and pm only to have me answer and build some malicious code upon that. Is such possible? I can't see html code, maybe some hidden parameters that add towards supporting a rootkit?
I'm using my MS laptop, the hacked pc is still down.

I wonder also how they hacked my pc last month. They mentioned a very old, simple passwort and a Video on that site. I've tried to watch that, but it says something alike unsupported mime type or so. So probably that was the rootkit but did they find a Firefox vulnerability to get onto my pc?

Many thanks

---

