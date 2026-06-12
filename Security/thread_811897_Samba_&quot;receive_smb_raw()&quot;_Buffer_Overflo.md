---
title: "Samba &quot;receive_smb_raw()&quot; Buffer Overflow Vulnerability"
date: 2008-05-29
forum: Security
---

### Post by plun on 2008-05-29
[http://secunia.com/advisories/30228/](http://secunia.com/advisories/30228/)

Critical:   	
***Highly critical***
Impact: 	System access
Where: 	From remote
Solution Status: 	Vendor Patch 


> The vulnerability is caused due to a boundary error within the "receive_smb_raw()" function in lib/util_sock.c when parsing SMB packets. This can be exploited to cause a heap-based buffer overflow via an overly large SMB packet received in a client context.

Successful exploitation allows execution of arbitrary code by tricking a user into connecting to a malicious server (e.g. by clicking an "smb://" link) or by sending specially crafted packets to an "nmbd" server configured as a local or domain master browser.

The vulnerability is confirmed in versions 3.0.28a and 3.0.29. Prior versions may also be affected.

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=samba](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=samba)

:confused:

---

### Post by lonedawg on 2008-06-03
Bump.  Is an updated package being worked on or should I compile the latest version from source?

---

