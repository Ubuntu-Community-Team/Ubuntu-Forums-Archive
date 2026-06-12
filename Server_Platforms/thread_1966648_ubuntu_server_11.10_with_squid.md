---
title: "ubuntu server 11.10 with squid"
date: 2012-04-27
forum: Server Platforms
---

### Post by !! hack-back !! on 2012-04-27
hello mate
i installed ubuntu server 11.10 on my amd64 server
i want to install squid 
the default way apt-get install squid
but this will install squid 2.7
but now we have 3.1.19
and whats about lusca any one test it ?
):P

---

### Post by newbie-user on 2012-04-27
The repos don't always have the latest version. That's just the way it is. If you want the latest version, you have to directly to the developer, in this case [www.squid-cache.org](www.squid-cache.org).

Is there anything specific you need that's not in squid 2.7?

---

### Post by SeijiSensei on 2012-04-27
Version 3 of squid is packaged as [squid3]("http://packages.ubuntu.com/search?keywords=squid3").  The most recent version for 11.10 is 3.1.14; for 12.04 it's 3.1.19.

If you're running a server I recommend running "sudo do-release-upgrade" and upgrading to 12.04 since that has long-term support. I upgraded a server from 11.04 > 11.10 > 12.04 last night with no issues.

---

### Post by !! hack-back !! on 2012-04-27
but 12.04 is still beta version

---

### Post by Jonathan L on 2012-04-27
> **!! hack-back !! said:**
> but 12.04 is still beta version

It's the official release now, but you're right it's pretty new.
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuServer](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuServer)

Kind regards,
Jonathan.

---

### Post by !! hack-back !! on 2012-04-27
thanks sir ,
are you using squid3 ?

---

### Post by SeijiSensei on 2012-04-27
I'm using Squid 3 on CentOS 6 as a transparent proxy.  Works fine.  The biggest value to us of version 3 is the ability to use [SquidClamAV]("http://squidclamav.darold.net/") to scan all objects downloaded over the web.  We still have ACL rules for things like .exe files, but SquidClamAV covers the cases where an object is obfuscated in a ZIP or RAR archive.  We're using a pretty hefty [box]("http://www.dell.com/us/highered/p/poweredge-r410/pd") -- dual Xeons (equivalent of 16 CPUs) with 8 GB -- but the machine also runs MailScanner to perform virus and spam scanning on all inbound mail.  At busy times of day we can reach a load average of 1-2.  There are about 200 clients behind the proxy.

12.04 has been under testing for quite some time now, and most of the action takes place on the desktop side these days anyway.  Most server software is pretty mature.

---

### Post by !! hack-back !! on 2012-04-28
i installed squid 3.1.14
and every thing okay
but no zph local and zph mode and zph tos
what i should do i need to use zph to take the full speed lan

---

### Post by SeijiSensei on 2012-04-28
I've never used that, but the [developer]("http://zph.bratcheda.org/") says it's incorporated in Squid 3 and was working with Ubuntu 10.10.

---

### Post by !! hack-back !! on 2012-04-28
thanks sir
but you must to patch it and i have ubuntu 11.10
sir 1 more question .
can you give me the better refresh pattern to cache all files

---

### Post by SeijiSensei on 2012-04-28
I don't understand what you're asking.  What's a "refresh" pattern?  If it's something to do with that zph patch, I've never used it.

Usually Squid caches everything except for objects where caching is denied by the HTTP headers.  Are you asking how long the object should remain in the cache?  Usually I just use the defaults.

I've never really found performance to be a big issue with Squid, although I haven't run it on networks with more than a couple hundred clients.  On really large networks, I'd think you'd want to spread the load across multiple peered machines.

I know there are documents on the Web about performance tuning for Squid; I'd read those instead of asking here if you have specific issues.

---

### Post by !! hack-back !! on 2012-04-28
in refresh pattern you can put what extensions you want to cache 
like :


refresh_pattern -i \.(3gp|7z|ace|asx|bin|deb|divx|dvr-ms|ram|rpm|exe|inc|cab|qt)       10080 80% 10080 ignore-no-cache   override-expire override-lastmod reload-into-i$


and why i have alot tcp_refresh_unmodified 
in /var/log/squid3/access.log
and i dont have any tcp_refresh_hit

---

### Post by !! hack-back !! on 2012-04-28
also no zph enabled so i cant download files for tcp_hit with out limitation from mikrotik

---

