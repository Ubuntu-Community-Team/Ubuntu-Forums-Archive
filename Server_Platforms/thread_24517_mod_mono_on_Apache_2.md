---
title: "mod_mono on Apache 2"
date: 2005-04-07
forum: Server Platforms
---

### Post by jo_vermeulen on 2005-04-07
Hello! 

I was wondering if it's possible to run mod_mono on Apache 2?
When I want to install mono-apache-server, it has a dependency on apache (1.3), while I'm using Apache 2 (and want to keep using it) as my webserver.

Thanks in advance!

---

### Post by goofrider on 2005-04-14
[QUOTE=jo_vermeulen]Hello! 

I was wondering if it's possible to run mod_mono on Apache 2?
When I want to install mono-apache-server, it has a dependency on apache (1.3), while I'm using Apache 2 (and want to keep using it) as my webserver.

Thanks in advance![/QUOTE]
 Yeah I'd love to see mod_mono for Apache2 in Ubuntu also.

According to the [Mono for Debian](http://pkg-mono.alioth.debian.org/) homepage, there's indeed a mod_mono for Apache2 in development. You can try to fetch it by adding this to your soruces.list.

```

deb http://debian.pablo.com.mx ./

```

Please note that thse are prerelease packages for Debian Sid, so use them at your own risk.

---

