---
title: "Deny SSL Youtube without blocking google (IPTABLES)"
date: 2013-02-25
forum: Server Platforms
---

### Post by jesh on 2013-02-25
Hello! I live in Mexico. I've managed to block the youtube's subnet with iptables. But when I need to use Gmail, or search with google, it doesn't work. I think those pages use the same ssl certificate, and the same subnet. Somebody can help me? I'll really apreciate it! Thanks in advance.

---

### Post by darkod on 2013-02-25
Do you want to block Youtube login or Youtube completely? Because the youtube page doesn't request that you log in, you can view it without SSL session. So, even if you block SSL successfully, people might be able to open none-SSL session.

I'm not sure you can block this the way you want it with iptables. If you were using a proxy, you should be able to block specific content (websites, pages) with the proxy.

EDIT PS. Like i said, usually you don't do this with iptables, you do it with squid proxy:
[http://serverfault.com/questions/360689/permanently-blocking-a-domain-in-iptables](http://serverfault.com/questions/360689/permanently-blocking-a-domain-in-iptables)

---

### Post by jesh on 2013-02-25
Thanks I forget to mention that I have a proxy to block non SSL pages. And I was able to block the youtube's CDIR like in your example. The thing is... The CDIR of yotube is the same that gmail uses, and I can't open the gmail page, even if its not inthe block list in the proxy.

---

### Post by darkod on 2013-02-25
With a proxy block by domain, not by IP range.

---

### Post by jesh on 2013-02-25
Yes I have blocked the domain that way in the proxy, but it won't catch SSL request. That's why I need to use iptables.

---

### Post by jesh on 2013-02-27
Does anybody managed to solve this? I can block the sites via proxy, but  if  someone manually puts the [https://www.examplesite.com](https://www.examplesite.com) it opens with no problem.

---

### Post by darkod on 2013-02-27
Can't you specify the https version in the proxy too? I think you should be able to. Or somehow select an option to include the https, not only http when it blocks the specified domains.

---

### Post by sc0g on 2013-09-04
*bump*

I'm trying to do the same thing... I want to block Youtube SSL but if I just block the IP, it will block Google Drive since Google Drive and Youtube use the same IP address ranges:

```
host drive.google.com
drive.google.com has address 206.111.1.87
drive.google.com has address 206.111.1.88
drive.google.com has address 206.111.1.89
drive.google.com has address 206.111.1.90
drive.google.com has address 206.111.1.91
drive.google.com has address 206.111.1.84
drive.google.com has address 206.111.1.85
drive.google.com has address 206.111.1.86

```

and...

```
host youtube.com
youtube.com has address 206.111.1.84
youtube.com has address 206.111.1.85
youtube.com has address 206.111.1.86
youtube.com has address 206.111.1.87
youtube.com has address 206.111.1.88
youtube.com has address 206.111.1.89
youtube.com has address 206.111.1.90
youtube.com has address 206.111.1.91
```

I've started to get creative by using host entries and internal DNS zones but that is just silly. I want to handle this with an IPTABLES rule. There are a few other ranges they use other than the 206.111.1.x. so keep that in mind...

---

