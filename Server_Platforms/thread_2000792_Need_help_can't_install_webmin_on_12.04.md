---
title: "Need help: can't install webmin on 12.04"
date: 2012-06-10
forum: Server Platforms
---

### Post by echo15 on 2012-06-10
Hi,

Hope someone could help me.  I did a new install of Ubuntu server edition 12.04 and am trying to install webmin to help in managing it.

I tried using the apt-get install procedure outlined in their website but keep getting error:
> Get:1 [http://download.webmin.com/download/repository/](http://download.webmin.com/download/repository/) sarge/contrib webmin all 1.580 [15.8 MB]
Fetched 15.8 MB in 3min 6s (84.7 kB/s)
Failed to fetch [http://download.webmin.com/download/repository/pool/contrib/w/webmin/webmin_1.580_all.deb](http://download.webmin.com/download/repository/pool/contrib/w/webmin/webmin_1.580_all.deb)  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I tried apt-get update and --fix-missing and still get the same error.

I then tried getting the deb file and installing via dpkg.  I get the following error with dpgk:
> (Reading database ... 55896 files and directories currently installed.)
Unpacking webmin (from webmin_1.580_all.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: invalid block type'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing webmin_1.580_all.deb (--install):
 short read on buffer copy for backend dpkg-deb during `./usr/share/webmin/acl/lang/ca'
Processing triggers for ureadahead ...
Errors were encountered while processing:
 webmin_1.580_all.deb

I'm new to this and don't even know where to start.  Hope someone could help.

Thanks!


**Solved:**
Turns out my router was the issue. Downloads kept getting corrupted that's why installation kept failing. Changed router and everything's okay now.

Thanks!

---

### Post by sanderj on 2012-06-10
[https://help.ubuntu.com/community/WebMin](https://help.ubuntu.com/community/WebMin) ?

---

### Post by brent1975 on 2012-06-10
I used webmin for the first week when I was first learning the server platform. But to be honest getting away from that really helps you learn how the server works.

This is a great community for folks that are starting out.  I would suggest staying away from webmin figure out what it is that you are wanting your server to do. Google your question with Ubuntu + version in the search. It's amazing the hits you are getting..

Just curious what are you wanting your server to do?

---

