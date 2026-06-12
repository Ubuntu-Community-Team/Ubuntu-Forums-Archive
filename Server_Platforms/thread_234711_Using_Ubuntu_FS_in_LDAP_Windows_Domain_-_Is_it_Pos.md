---
title: "Using Ubuntu FS in LDAP Windows Domain - Is it Possible?"
date: 2006-08-11
forum: Server Platforms
---

### Post by drummer4lifex on 2006-08-11
Hello all, 

I'm doing a server migration away from a larger network that used to use Novell servers for file sharing. I tried replacing the Novell server with Windows Server and moved all the shares over, but it's just too slow (Windows Sux :mrgreen: ). I was reading up on the guide on linux file sharing, but it doesn't exactly make sense to me. So before I dig down and try to learn this stuff, I was wondering if it's even possible for me to create shares and assign LDAP security from a Windows Domain Controller so only certain users can view certain shares. 

So is it possible? :-k

---

### Post by fnjordy on 2006-08-12
Yes its possible, you might find it more convenient to use a software appliance like [FreeNAS]("http://www.freenas.org/") though as quite a few things need to be configured for it to work.  File sharing is via a package called Samba, and authentication to a Windows Domain Controller uses Winbind, NSS, and PAM.

---

### Post by n8bounds on 2006-08-12
> **fnjordy said:**
> Yes its possible, you might find it more convenient to use a software appliance like [FreeNAS]("http://www.freenas.org/") though as quite a few things need to be configured for it to work.  File sharing is via a package called Samba, and authentication to a Windows Domain Controller uses Winbind, NSS, and PAM.

I can vouch for FreeNAS--it is ridiculously easy to use if all you need is file sharing...I don't think it supports CUPS (printing), but I don't know..

---

