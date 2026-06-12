---
title: "Relation between Apache &amp; Squid"
date: 2010-10-03
forum: Security
---

### Post by wacky_sung on 2010-10-03
Lately i just installed Ubuntu 10.10 and get my Squid installed.It work much superior than Polipo for cache but i do not understand why i got Apache installed after i installed Squid.Is there any co-relation between Apache and Squid?Does it gonna make me run my own web server?

---

### Post by bodhi.zazen on 2010-10-03
Ubuntu tends to "make things easy" for new users, and often this involved installing more dependencies then a package may need.

If you use another distro you may find a package will have less dpenedencies.

In your case, hard to know if apache is listed as a dependency of squid (I think not) or as a dependency for another package you installed another package that lists apache as a dependency.

Try apt-get or synaptic or aptitude or whatever tool you wish to identify dependencies of squid and other packages.

---

### Post by wacky_sung on 2010-10-04
I thought squid has to work in parallel with Apache because it uses Apache for networking to access squid or load balancing.Correct me if i am wrong.Thank.

---

### Post by bodhi.zazen on 2010-10-04
> **wacky_sung said:**
> I thought squid has to work in parallel with Apache because it uses Apache for networking to access squid or load balancing.Correct me if i am wrong.Thank.

Depends on what you are using squid for exactly, ie as a proxy server or as a reverse proxy.

But I do not see apache as a dependency for squid 

[http://packages.ubuntu.com/maverick/squid](http://packages.ubuntu.com/maverick/squid)

And I routinely run squid (as a paroxy) without apache.

Again I encourage you to learn to check dependencies for yourself and if you need assistance, perhaps more details about what you are doing would help.

---

### Post by wacky_sung on 2010-10-05
Seem like the HTTP proxy get the apache installed on both add-ons.Thank for your advise.

[IMG]http://img834.imageshack.us/img834/2330/screenshotubuntusoftwar.png[/IMG]

---

