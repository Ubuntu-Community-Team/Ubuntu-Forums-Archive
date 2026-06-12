---
title: "Network usage resets"
date: 2008-02-04
forum: Server Platforms
---

### Post by frodemt on 2008-02-04
Hi, I have a Ubuntu server.

I was wonderinger why the network usage conter resets when it gets up to 10 GB?

---

### Post by cheahk on 2008-02-04
Urm... what network usage counter are you referring to?  SNMP?

---

### Post by frodemt on 2008-02-04
Sorry, dont know. The one that this script is using: [http://tviberg.gotdns.com/phpsysinfo/](http://tviberg.gotdns.com/phpsysinfo/)

---

### Post by cheahk on 2008-02-04
It's probably the variable type that is used, and rolls over to 0 once the value exceeds 2^32, or 4,294,967,296.

---

