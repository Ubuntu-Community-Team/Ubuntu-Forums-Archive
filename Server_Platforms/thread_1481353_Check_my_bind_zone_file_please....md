---
title: "Check my bind zone file please..."
date: 2010-05-12
forum: Server Platforms
---

### Post by PryGuy on 2010-05-12
Good day everyone!
I've just clean installed Lucid server with my config files and it seems that Lucid's bind 9.7.0 became more severe on syntax errors my zone files had (as I learnt). I corrected it, but want to make sure that I was right this time.

So the setup is: I have a server that has mirrored Ubuntu repos. I redirect archive.ubuntu.com and ru.archive.ubuntu.com to server transparently. My zone file for that is:
```
$TTL    604800
@       IN      SOA     archive.ubuntu.com. root.archive.ubuntu.com. (
	4         ; Serial
	604800    ; Refresh
	86400     ; Retry
	2419200   ; Expire
	604800 )  ; Negative Cache TTL
		NS localhost.

	IN	A	192.168.0.1
ru	IN	A	192.168.0.1
```
Here an extract from named.conf that refers to this file:
```
  // http://archive.ubuntu.com forward zone
  zone "archive.ubuntu.com" {
    type master;
    file "/etc/bind/zones/forward/db.archive.ubuntu.com";
    allow-update{none;};
    notify no;
  };
```
Would you be so kind to check it out and correct if needed? Thank you in advance!

---

### Post by windependence on 2010-05-12
Looks OK to me. Just be sure to increment the serial each time you change it and restart bind or the changes won't apply.

-Tim

---

### Post by PryGuy on 2010-05-13
Thanks, pal! :)

---

