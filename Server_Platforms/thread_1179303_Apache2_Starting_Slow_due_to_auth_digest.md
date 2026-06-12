---
title: "Apache2 Starting Slow due to auth_digest"
date: 2009-06-05
forum: Server Platforms
---

### Post by Eoin Miller on 2009-06-05
We found that Apache2 will start extremely slow (sometimes NEVER start) when mod auth_digest is enabled. Unfortunately this module is enabled by default with Apache2 running on 8.04.2:

```
#more /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.2"

``````
# uname -a
Linux <hostname> 2.6.24-24-server #1 SMP Wed Apr 15 15:41:09 UTC 2009 x86_64 GNU/Linux
```
Starting fine:
```
[Fri Jun 05 12:49:36 2009] [notice] Digest: generating secret for digest authentication ...
[Fri Jun 05 12:49:36 2009] [notice] Digest: done
```Not starting after 3+ minutes:
```
[Fri Jun 05 12:50:53 2009] [notice] Digest: generating secret for digest authentication ...
[Fri Jun 05 12:54:55 2009] [notice] Digest: generating secret for digest authentication ...
```We have just removed the symbolic link /etc/apache2/mods-enabled/auth_digest that points to the /etc/apache2/mods-available/auth_digest.load file. This may help others, but if you do use auth_digest, you would still be at the mercy of the random start if we feel like it behavior.

---

