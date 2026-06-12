---
title: "Installation of PostgreSQL 9.3 &amp; postgis 2.1 at 16.04"
date: 2017-05-09
forum: Server Platforms
---

### Post by nyxteridas on 2017-05-09
Hello guys,
I have recently upgraded from 14.04 server edition to 16.04.
The system automatically updated my existing postgreSQL version to 9.5 but I needed to use 9.3.
So, I purged the 9.5 and reinstalled the 9.3. The problem is that I cannot find a way to install postgis 2.1.
I tried to reference repositories from past versions but I got some errors
e.g:
```
postgresql-9.3-postgis-2.1 : Depends: libgdal1h (>= 1.9.0) but it is not installable
                              Depends: libgeos-c1 (>= 3.4.2) but it is not going to be installed
                              Depends: liblwgeom-2.1.8 (>= 2.1.6) but it is not going to be installed
                              Depends: libproj0 (>= 4.8.0-1) but it is not installable
```

Is there any workaround for this, or do you know if the latest version of postgis works also with postgres 9.3?

Thank you in advance

---

### Post by slickymaster on 2017-05-09
See if this Ask Ubuntu thread applies to your issue: [https://askubuntu.com/questions/636101/how-can-i-slove-postgresql-9-3-postgis-2-1-unmet-dependencies-ubuntu-14-04](https://askubuntu.com/questions/636101/how-can-i-slove-postgresql-9-3-postgis-2-1-unmet-dependencies-ubuntu-14-04)

---

### Post by nyxteridas on 2017-05-10
Actually the link didn't help me a lot.
So I decided to try migrating my data to the newest version :)
Thank you anyway for the answer!

---

