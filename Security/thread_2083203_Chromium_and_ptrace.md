---
title: "Chromium and ptrace?"
date: 2012-11-11
forum: Security
---

### Post by Stonecold1995 on 2012-11-11
Every day I check the syslog for AppArmor related errors, and recently I've been getting a huge amount.  It seems like Chromium is trying to ptrace some process and AppArmor is blocking that.

```
root@kubuntu:~# grep DENIED < /var/log/syslog | tail -5
Nov 11 16:39:29 kubuntu kernel: [45709.837036] type=1400 audit(1352680769.982:8613): apparmor="DENIED" operation="ptrace" parent=2966 profile="/usr/lib/chromium-browser/chromium-browser" pid=6267 comm="BrowserBlocking" target=A002801E0488FFFFA002801E0488FFFFB301
Nov 11 16:39:29 kubuntu kernel: [45709.837125] type=1400 audit(1352680769.982:8614): apparmor="DENIED" operation="ptrace" parent=2966 profile="/usr/lib/chromium-browser/chromium-browser" pid=6267 comm="BrowserBlocking" target=A002801E0488FFFFA002801E0488FFFFB301
Nov 11 16:39:29 kubuntu kernel: [45709.837212] type=1400 audit(1352680769.982:8615): apparmor="DENIED" operation="ptrace" parent=2966 profile="/usr/lib/chromium-browser/chromium-browser" pid=6267 comm="BrowserBlocking" target=A002801E0488FFFFA002801E0488FFFFB301
Nov 11 16:39:29 kubuntu kernel: [45709.837302] type=1400 audit(1352680769.982:8616): apparmor="DENIED" operation="ptrace" parent=2966 profile="/usr/lib/chromium-browser/chromium-browser" pid=6267 comm="BrowserBlocking" target=A002801E0488FFFFA002801E0488FFFFB301
Nov 11 16:39:29 kubuntu kernel: [45709.837388] type=1400 audit(1352680769.982:8617): apparmor="DENIED" operation="ptrace" parent=2966 profile="/usr/lib/chromium-browser/chromium-browser" pid=6267 comm="BrowserBlocking" target=A002801E0488FFFFA002801E0488FFFFB301

root@kubuntu:~# grep DENIED < /var/log/syslog | wc -l
4032

root@kubuntu:~# grep sys_ptrace < /var/log/syslog
Nov 11 15:11:29 kubuntu kernel: [40437.557242] type=1400 audit(1352675489.946:1317): apparmor="DENIED" operation="capable" parent=2966 profile="/usr/lib/chromium-browser/chromium-browser" pid=6267 comm="BrowserBlocking" pid=6267 comm="BrowserBlocking" capability=19  capname="sys_ptrace"
Nov 11 15:13:29 kubuntu kernel: [40557.441709] type=1400 audit(1352675609.946:1452): apparmor="DENIED" operation="capable" parent=2966 profile="/usr/lib/chromium-browser/chromium-browser" pid=6450 comm="BrowserBlocking" pid=6450 comm="BrowserBlocking" capability=19  capname="sys_ptrace"
Nov 11 15:15:29 kubuntu kernel: [40677.324664] type=1400 audit(1352675729.950:1587): apparmor="DENIED" operation="capable" parent=2966 profile="/usr/lib/chromium-browser/chromium-browser" pid=6450 comm="BrowserBlocking" pid=6450 comm="BrowserBlocking" capability=19  capname="sys_ptrace"
Nov 11 15:19:29 kubuntu kernel: [40916.978817] type=1400 audit(1352675969.948:1838): apparmor="DENIED" operation="capable" parent=2966 profile="/usr/lib/chromium-browser/chromium-browser" pid=6267 comm="BrowserBlocking" pid=6267 comm="BrowserBlocking" capability=19  capname="sys_ptrace"
Nov 11 15:23:29 kubuntu kernel: [41156.622630] type=1400 audit(1352676209.948:2095): apparmor="DENIED" operation="capable" parent=2966 profile="/usr/lib/chromium-browser/chromium-browser" pid=6450 comm="BrowserBlocking" pid=6450 comm="BrowserBlocking" capability=19  capname="sys_ptrace"
Nov 11 15:25:29 kubuntu kernel: [41276.444949] type=1400 audit(1352676329.948:2224): apparmor="DENIED" operation="capable" parent=2966 profile="/usr/lib/chromium-browser/chromium-browser" pid=6267 comm="BrowserBlocking" pid=6267 comm="BrowserBlocking" capability=19  capname="sys_ptrace"
Nov 11 15:41:29 kubuntu kernel: [42235.024442] type=1400 audit(1352677289.956:3386): apparmor="DENIED" operation="capable" parent=2966 profile="/usr/lib/chromium-browser/chromium-browser" pid=6267 comm="BrowserBlocking" pid=6267 comm="BrowserBlocking" capability=19  capname="sys_ptrace"

root@kubuntu:~# chromium-browser --version
Chromium 24.0.1312.2 Ubuntu 12.10
```

How do I prevent this?  It seemed to start happening after I installed an update of Chromium.

---

### Post by Hungry Man on 2012-11-11
Chromium needs the the capability sys_ptrace. It's unfortunate but it's in the default profile. You should add it in.

---

### Post by Stonecold1995 on 2012-11-14
Thank you!  But how come suddenly after an update Chromium requires sys_ptrace when before it didn't?

---

### Post by Hungry Man on 2012-11-14
It has always required it, it just wasn't logging for some reason or something else wasn't happening. But it's always needed it.

---

