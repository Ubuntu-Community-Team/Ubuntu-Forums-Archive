---
title: "Please help - how to recompile php5"
date: 2008-07-12
forum: Server Platforms
---

### Post by satimis on 2008-07-12
Hi folks,


Ubuntu LAMP 6.06 amd64
SugarCRM 5.0
Postfix
Apache2
php5


I have SugarCRM 5.0 running on this LAMP box.  But users can neither send nor receive emails. It comes to my notice that "Inbound Email cannot function without the IMAP c-client libraries enabled/compiled with the PHP module"


$ apt-cache policy php5-imap```

php5-imap:
  Installed: 5.1.2-1
  Candidate: 5.1.2-1
  Version table:
 *** 5.1.2-1 0
        500 http://archive.ubuntu.com dapper/universe Packages
        100 /var/lib/dpkg/status

```


$ apt-cache policy libc-client2002edebian```

libc-client2002edebian:
  Installed: 7:2002edebian1-13
  Candidate: 7:2002edebian1-13
  Version table:
 *** 7:2002edebian1-13 0
        500 http://archive.ubuntu.com dapper/universe Packages
        100 /var/lib/dpkg/status

```


I need to recompile php5 with;```

./configure' '---enable-mbstring' '--with-imap' '--with-imap-ssl' '--with-kerberos' '--with-curl'

```

However I can't find php5 source


$ sudo find / -name src -type d | grep php5
No printout


Also I need Debian package development tools:


$ apt-cache policy build-essential debhelper```

build-essential:
  Installed: (none)
  Candidate: 11.1
  Version table:
     11.1 0
        500 http://hk.archive.ubuntu.com dapper/main Packages
debhelper:
  Installed: (none)
  Candidate: 5.0.7ubuntu13
  Version table:
     5.0.7ubuntu13 0
        500 http://hk.archive.ubuntu.com dapper/main Packages

```


I suppose need to install them running;```

$ sudo apt-get install build-essential debhelper

```

and download php5 sourece;```

$ sudo apt-get source php5

```


plus all the dependencies for building PHP:```

$ sudo apt-get build-dep php5

```


Here I hesitate on which directory shall I run;```

./configure' '---enable-mbstring' '--with-imap' '--with-imap-ssl' '--with-kerberos' '--with-curl'

```


On "cd php5-xxx/debian" ???

Kinldy shed me some light assisting me to avoid making mistake.  TIA


B.R.
satimis

---

