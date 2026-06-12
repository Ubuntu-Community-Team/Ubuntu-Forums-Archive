---
title: "Cannot connect to proftpd after frequent file transfer"
date: 2013-02-10
forum: Server Platforms
---

### Post by jereiard on 2013-02-10
Hello.

I set up ubuntu 12.04 LTS server with default options last week, and I'm in trouble.

I installed proftpd using apt-get.
Ufw is inactive and iptables has no rules.

Using filezilla on my windows laptop, I can connect to my server and use ftp service. But, when I upload or download small files(about 1kb size) to/from server, transfer stopped after just a moment and I get 'connection timeout'. Then I can't connect to every services on my server such as SSH, ftp, apache..

That moment, if I change my laptop ip, I can use all services normally.

I'm newbie in linux and this problem is so hard to me..

Please help me solve..

Thanks in advance.

---

### Post by ali abry on 2013-02-12
check log files like : 
```
/var/log/syslog
```

---

