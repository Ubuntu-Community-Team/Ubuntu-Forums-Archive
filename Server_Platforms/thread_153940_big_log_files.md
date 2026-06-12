---
title: "big log files"
date: 2006-04-02
forum: Server Platforms
---

### Post by wfx on 2006-04-02
hi, 
short - brezzy:
-rw-r-----  1 root  adm  891K 2006-04-02 10:58 daemon.log
-rw-r-----  1 root  adm  1,7G 2006-04-02 06:27 daemon.log.0
-rw-r-----  1 root  adm  3,2M 2006-04-01 06:27 daemon.log.1.gz
-rw-r-----  1 root  adm  5,3M 2006-03-31 06:28 daemon.log.2.gz
-rw-r-----  1 root  adm  8,9M 2006-03-30 06:27 daemon.log.3.gz
-rw-r-----  1 root  adm  5,0M 2006-03-29 06:25 daemon.log.4.gz
-rw-r-----  1 root  adm  2,6M 2006-03-28 06:25 daemon.log.5.gz
-rw-r-----  1 root  adm  3,5M 2006-03-27 06:26 daemon.log.6.gz

Wow 1.7GIG maybe nice read in bed :-)
So what is in:
...millions of line with...
Apr  2 11:03:05 philoctetes pptp[5725]: anon log[decaps_gre:pptp_gre.c:395]: discarding duplicate or old packet 7350 (expecting 32826)
Apr  2 11:03:07 philoctetes pptp[5725]: anon log[decaps_gre:pptp_gre.c:395]: discarding duplicate or old packet 7351 (expecting 32826)
Apr  2 11:03:07 philoctetes pptp[5725]: anon log[decaps_gre:pptp_gre.c:395]: discarding duplicate or old packet 7352 (expecting 32826)
Apr  2 11:03:09 philoctetes pptp[5725]: anon log[decaps_gre:pptp_gre.c:395]: discarding duplicate or old packet 7353 (expecting 32826)

How can i tell the pptp deamon to log not so mutch?
This way does not work:
iface ppp0 inet ppp
      provider telekom --loglevel 0


thx

---

