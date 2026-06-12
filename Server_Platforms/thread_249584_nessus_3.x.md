---
title: "nessus 3.x"
date: 2006-09-02
forum: Server Platforms
---

### Post by neil lehrer on 2006-09-02
hi,

i loaded nessus from the ubuntu repository, but it was the 2.6 release, not the current 3.0 release.  so i downloaded the debian ver from tenable and installed it.  no problems seen, but when i go to start nessus i get

root@nlehrer-laptop:/opt/nessus/sbin# /opt/nessus/sbin/nessusd-D
-bash: /opt/nessus/sbin/nessusd-D: No such file or directory
root@nlehrer-laptop:/opt/nessus/sbin# /opt/nessus/sbin/nessusd -D
/opt/nessus/sbin/nessusd: error while loading shared libraries: libssl.so.0.9.7: cannot open shared object file: No such file or directory

suggestions please. thanks.

---

### Post by seekyrr on 2006-09-08
I am having same problem is anyone knows a fix.

Thanks

Seek

---

### Post by yomimono on 2006-09-08
The problem is that nessus is expecting openssl version 0.9.7.  Dapper is currently in openssl version 0.9.8 (found in /usr/lib/ .)  You can install openssl 0.9.7 for compatibility with nessus [from universe](http://ubuntuguide.org/wiki/Dapper):
```
apt-get install libssl0.9.7
```
Or you can build nessus from source, with openssl 0.9.8 installed.  If you have not built packages from source before, I would recommend the first option.

OpenSSL 0.9.7k and OpenSSL 0.9.8c [offer comparable levels of security](http://www.openssl.org/news/announce.html), although OpenSSL 0.9.8c is [newer](http://www.openssl.org/source/).

---

### Post by seekyrr on 2006-09-11
I got the nessus server working well with apt-get install libssl0.9.7.

I don't see a client for .deb, just some for Redhat/SUSE and Fedora.

Anyone get one of these working under ubuntu?

Thanks

Seek

---

### Post by omenix on 2006-09-25
You need the NessusClient source from [www.nessus.org](www.nessus.org) and to build it you need  apt-get install libssl-dev and also apt-get install libgtk2.0-dev. Good luck! :)

---

