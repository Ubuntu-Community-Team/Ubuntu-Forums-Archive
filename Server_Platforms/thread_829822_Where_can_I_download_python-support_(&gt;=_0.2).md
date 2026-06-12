---
title: "Where can I download python-support (&gt;= 0.2)"
date: 2008-06-15
forum: Server Platforms
---

### Post by satimis on 2008-06-15
Hi folks,


Ubuntu LTS 6.06 amd64


On installing 'ajaxterm_0.9-2_all.deb'


$ sudo dpkg -i ajaxterm_0.9-2_all.deb ```

Selecting previously deselected package ajaxterm.
(Reading database ... 24405 files and directories currently installed.)
Unpacking ajaxterm (from ajaxterm_0.9-2_all.deb) ...
dpkg: dependency problems prevent configuration of ajaxterm:ap
 ajaxterm depends on python-support (>= 0.2); however:
  Version of python-support on system is 0.1.1ubuntu1.
dpkg: error processing ajaxterm (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ajaxterm

```

It needs python-support (>= 0.2).


$ apt-cache policy python-support```

python-support:
  Installed: 0.1.1ubuntu1
  Candidate: 0.1.1ubuntu1
  Version table:
 *** 0.1.1ubuntu1 0
        500 http://archive.ubuntu.com dapper/universe Packages
        100 /var/lib/dpkg/status

```


I can't find it on repo.  Please advise where can I download it.  TIA


B.R.
satimis

---

