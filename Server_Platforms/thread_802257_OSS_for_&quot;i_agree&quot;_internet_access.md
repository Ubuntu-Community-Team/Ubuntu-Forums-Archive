---
title: "OSS for &quot;i agree&quot; internet access?"
date: 2008-05-21
forum: Server Platforms
---

### Post by opportunity on 2008-05-21
Hi,

I was wondering if any of you know about a solution or method of requiring an "i agree" button to be pressed in order to provide internet access? This is for public computers which the acceptable use policy will be displayed and required to be agreed to before internet is enabled. We currently use wired broadband and an ipcop linux firewall.

Thanks.

---

### Post by cdenley on 2008-05-21
I think what you're looking for is called a captive portal. There might be some packages that work, but most are probably meant for wireless authentication. I built mine with apache, iptables, python, and php, but I always do things the hard way.

---

### Post by opportunity on 2008-05-22
thanks very much. It was a challange just finding a name to go from for the technology i knew existed.

---

### Post by elianthony on 2008-05-29
> **opportunity said:**
> I was wondering if any of you know about a solution or method of requiring an "i agree" button to be pressed in order to provide internet access?Thanks.

I need this as well here at the public library.

---

### Post by jonallport on 2008-05-31
You need Chillispot!

It's in the Ubuntu repositories and I've used it successfully for a couple of sites (A commercial company with 'I Agree' access for visitors amongst them).

Search for 'Chiilispot' in the forum; there's a link to a how-to somewhere which got me started.  Also, a few pointers that've helped me:

1 - Start with a LAMP install of Ubuntu or you'll get apache-perl to satisfy dependencies.
2 - Use the php 'hotspotlogin' page mentioned in the how-to; It's much more configurable (for a doofus like me) than the perl cgi-bin version.

If you need any help, just ask.  I'll be glad to help if I can.

Jon

---

### Post by opportunity on 2008-06-05
I just needed something for wired connection gateway to provide a policy before activing internet access[aka "catch and release"] and found it with the program nocat

[http://nocat.net/](http://nocat.net/)

---

