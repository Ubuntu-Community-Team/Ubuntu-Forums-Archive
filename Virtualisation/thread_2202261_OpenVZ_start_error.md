---
title: "OpenVZ start error"
date: 2014-01-28
forum: Virtualisation
---

### Post by francisco-pascual on 2014-01-28
Hi all

I hav virtualized Ubuntu 10   with OpenVZ, it was working until today, but when i try to start it now, i get this error: 

///////////////////////////////////////////////////////////////////////////////////

vzctl start 101
Starting container ...
Container is mounted
Adding IP address(es): xx.xx.xx.220
Setting CPU units: 1000
Setting CPUs: 1
Set hostname: xxxxx.onlinehome-server.info
/bin/bash: line 388: /etc/hostname: Input/output error
File resolv.conf was modified
Setting quota ugidlimit: 0
ln: accessing `/etc/mtab': Input/output error
Container start in progress...


//////////////////////////////////////////////////////////////////

I thought it was the quota problem and did a  "vzctl quotaoff 101"

Can anyone help me plz?

Regards

---

