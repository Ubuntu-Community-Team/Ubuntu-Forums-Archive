---
title: "apt-get update fails to fetch from repo but wget works"
date: 2006-10-17
forum: Repositories &amp; Backports
---

### Post by no_mayl on 2006-10-17
I'm seeing fetch errors both from synaptics and sudo apt-get update.

sudo apt-get update shows:
```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Connection failed [IP: 146.137.96.15 80]

```
But if I wget that same url, no problems:
```
wget -O - http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg
--21:40:47--  http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg
           => `-'
Resolving us.archive.ubuntu.com... 146.137.96.15, 146.137.96.7
Connecting to us.archive.ubuntu.com|146.137.96.15|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 189 [text/plain]

 0% [                                                                                                                          ] 0             --.--K/s             -----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.1 (GNU/Linux)

iD8DBQBEfegyQJdur0N9BbURAqolAJ9iJ/U2GV6O1s7/U4lA/ALCEMZ9OwCfXx1d
WaT9VElYazKOfHUydYtaoeg=
=Wwyu
-----END PGP SIGNATURE-----

```

I can put the apt-get update in a loop, it always fails while at the same time a wget in a loop never fails.

I'm a missing some magic config that is prevent synaptic and apt-get update from working?
Because it sure does not look like a network problem.
--
jpa

---

### Post by no_mayl on 2006-10-17
doh. dumb config|user.

[http://www.ubuntuforums.org/showpost.php?p=1107990&postcount=5](http://www.ubuntuforums.org/showpost.php?p=1107990&postcount=5)

```
--- /etc/apt/apt.conf.20061016  2006-10-16 21:51:40.000000000 -0700
+++ /etc/apt/apt.conf   2006-10-16 21:57:13.000000000 -0700
@@ -1 +0,0 @@
-Acquire::http::Proxy "false";
```

Removing that line worked just fine.

You would expect that "false" means "don't do anything" but apparently not in this case. And, why does it work for some repos and not others?

---

