---
title: "Help with AppAmour.."
date: 2013-06-15
forum: Security
---

### Post by hopelessone on 2013-06-15
Hi,

Jun 16 09:18:00 someone kernel: [  776.698770] type=1400 audit(1371338280.446:47): apparmor="DENIED" operation="create" parent=1 profile="/usr/bin/amule" pid=14623 comm="amule" family="inet" sock_type="dgram" protocol=0

How can I get this back to normal?

Thanks

---

### Post by hopelessone on 2013-06-15
Hmmm...

sudo invoke-rc.d apparmor reload

seemed to work..
weird

---

### Post by hopelessone on 2013-06-18
AppArmour seems to be blocking all network ports?

How to undo?
Could not listen for external connections at 10.1.1.5:4712!

Thanks

---

### Post by hopelessone on 2013-06-18
apparmor="DENIED" operation="create" parent=1 profile="/usr/bin/amuled" pid=5503 comm="amuled" family="inet" sock_type="stream" protocol=0
Again!!??

How can I fix her up?

---

### Post by hopelessone on 2013-06-18
Of course the amule appamor profile is no where to be seen in /etc/appamor.d/ folder...!

*Sigh*

Any ideas how to fix?

---

### Post by wildmanne39 on 2013-06-18
*Thread moved to **Security Discussions**.*

---

