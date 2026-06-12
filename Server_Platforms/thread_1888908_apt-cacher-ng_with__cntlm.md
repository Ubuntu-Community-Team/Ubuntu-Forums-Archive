---
title: "apt-cacher-ng with  cntlm"
date: 2011-11-30
forum: Server Platforms
---

### Post by riky67 on 2011-11-30
excuse my English
 I have an ISA server connected server ubuntu 10.04
 
i have install cntlm and setting
 export http_proxy = [http://apt-proxy:3128]("http://apt-proxy:3128/")
 export ftp_proxy = [ftp://apt-proxy:3128]("ftp://apt-proxy:3128/")
apt-gat update works fast
 installing apt-cache and adding / etc/apt/apt.d/02proxy
Acquire:: http::razz:roxy "[http://myapt-proxy:3142/]("http://apt-proxy:3142/")";
 apt-update is very slow and many (not all) of connection time out error 503
 apt-upgrade does not work
 you can help me
how to configure apt-cache-ng with cntlm??

---

