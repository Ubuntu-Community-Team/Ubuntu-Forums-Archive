---
title: "Domain Name &amp; IP question"
date: 2005-11-18
forum: Server Platforms
---

### Post by invalid on 2005-11-18
Hi,
 
I am fairly new to IPs and how they relate to domain names. Here is my situation..

I have a domain name which points to my local box, which has a dynamic IP. My question is, is it possible to have my IP directly related to the domain? Like if someone were to type 'resolveip xx.xx.xx.xx' it would return 'mydomain.com'? At the moment, it returns the dynamic hostname provided by my ISP.

Maybe someone could provide a little light on how this works, or how it doesn't work.

Thanks,
Cb

---

### Post by pingswept on 2005-11-18
Hi Invalid,

The process is something like this:
1. Register a domain name with a registrar like register.com (although I don't particularly recommend them).

2. Using your registrar's web interface, set their DNS to point that name at your IP.

This assumes you have a static IP. If you have a dynamic IP, which is likely, you need to set up something like ddclient that will update your IP with the DNS system. You might look at dyndns.org, which provides this service for free for a subset of domains.

---

### Post by invalid on 2005-11-18
Thanks for the reply.

However, I already have the domain set up, and it updates fine with a service from zoneedit. My question was, is it possible to resolve my IP now into "domain.com" instead of having it resolve into an ISP hostname "xx-xx-xx-xx.some-identifier-some.isp.com" 

For example, it would look like this:
```

beau@willow:~$ resolveip xx.xx.xx.xx
Host name of xx.xx.xx.xx is mydomain.com

```

Cb

---

### Post by pingswept on 2005-11-18
Sorry for the misunderstanding.

Is this for something involving MySQL-- log files or something?

In MySQL 5, resolveip uses the gethostbyaddr system call, but I'm not sure where that call gets its information.

Good luck.

---

### Post by invalid on 2005-11-18
resolveip is a mysql helper command, yes.
It should work similar as most other host resolving functions, such as found in php etc..

Cb

---

### Post by spade_shark on 2005-11-18
Talk to your ISP and request that they update / change their records for you.  They may or may not do it.  It is not uncommon for the isp to not do this (try calling cable company XYZ for your one entry :) ).  All you really need to worry about is correct dns records for your domain.  Computers will do the rest.

---

### Post by nagilum on 2005-11-20
You can ask your ISP to do that (as others mentioned) but I seriously doubt they will do it. Your ISP would have to track your IP and update their DNS system accordingly on every change, which would again lead to troubles since DNS records have a certain lifetime and other servers won't update their cached entry of your IP until the old one expires.
That's what static IPs are there for and if you intend to run a server a static IP is the only real choice anyway.

---

