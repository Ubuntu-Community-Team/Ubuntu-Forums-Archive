---
title: "Extra Security through NAT?"
date: 2008-12-13
forum: Virtualisation
---

### Post by WaeV on 2008-12-13
Does using a virtual machine (windows on ubuntu) with network address translation add any form of security?

---

### Post by Dedoimedo on 2008-12-14
In what form? Security for what, from what?

In general, virtualization is NOT equivalent/replacement for security and good security practices. If you infect your windows machine, it will still be infected. It may not hurt the linux host, but it will still be infected, with all the consequences that stem from such a situation.

Dedoimedo

---

### Post by HermanAB on 2008-12-14
Windows in a VM on Linux with NAT is equivalent to having a dinky little Linux based NAT router with a Windows PC behind it.

Cheers,

Herman

---

### Post by Dedoimedo on 2008-12-14
No, it's not.

Because your personal machine runs many more services than the router, plus it includes important personal data that you don't want to risk losing. And so forth.

Dedoimedo

---

### Post by bodhi.zazen on 2008-12-14
NAT vs what exactly ?

---

### Post by WaeV on 2008-12-16
Network Address Translation.

I understand good computing practices and all, and I follow them on my actual XP install, but I intended to run my VM XP free of slow scanning software etc and simply restore it to a snapshot if it got corrupted.

So it's no different that being behind a linux based router?

---

### Post by HermanAB on 2008-12-17
No, it is not really any different - Linux is Linux is Linux...
:)

---

