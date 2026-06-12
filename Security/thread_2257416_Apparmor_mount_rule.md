---
title: "Apparmor mount rule"
date: 2014-12-19
forum: Security
---

### Post by srhadden on 2014-12-19
from /var/log/kern.log

 4547.931711] type=1400 audit(1419014330.215:727): apparmor="DENIED" operation="mount" info="failed type match" error=-13 parent=19948 profile="lxc-mytest" 
name="/var/lib/docker/devicemapper/" pid=19949 comm="docker" srcname="/var/lib/docker/devicemapper/" flags="rw, bind"

What apparmor rule would allow this? 

Thanks for any ideas.

---

