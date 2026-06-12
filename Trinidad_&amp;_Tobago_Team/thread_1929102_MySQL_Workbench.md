---
title: "MySQL Workbench"
date: 2012-02-21
forum: Trinidad &amp; Tobago Team
---

### Post by minisansana on 2012-02-21
MySQL Workbench is a neat cross-platform application that simplifies the tasks of being a MySQL DBA without having to install necessary software on your servers.

Description from mysql.com:

MySQL Workbench provides DBAs and developers an integrated tools environment for:  
[LIST]
[*]Database Design & Modeling
[*]SQL Development (replacing MySQL Query Browser)
[*]Database Administration (replacing MySQL Administrator)
[/LIST]


Currently it is not available in the ubuntu repositories, you have to download a deb from the vendor website. As of writing, the latest deb is meant for Ubuntu 11.04 but runs on 11.10 but is unstable.


Here are some links we are watching for developments:


Debian ITP:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=604174](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=604174)

Lucid Package
[https://launchpad.net/ubuntu/lucid/+source/mysql-gui-tools/5.0r14+openSUSE-2build1](https://launchpad.net/ubuntu/lucid/+source/mysql-gui-tools/5.0r14+openSUSE-2build1)

Ubuntu Package Request
[https://bugs.launchpad.net/ubuntu/+bug/53062](https://bugs.launchpad.net/ubuntu/+bug/53062)

Debian Trunk
[http://anonscm.debian.org/viewvc/pkg-mysql/mysql-workbench/trunk/](http://anonscm.debian.org/viewvc/pkg-mysql/mysql-workbench/trunk/)

Debian Mentors page
[http://mentors.debian.net/package/mysql-workbench](http://mentors.debian.net/package/mysql-workbench)

---

### Post by trinikrono on 2012-02-21
[Learn more about mysql workbench project]("http://www.mysql.com/products/workbench/")

---

### Post by hanishjadala on 2012-08-22
hi i am using ubuntu 11.04 and all of a sudden from today morning my MYSQL workbench is not working. it is not launching at all. can any one help me out how to fix it. i have uninstalled and re install but still it's not working.


Thanks in advance

---

### Post by trinikrono on 2013-04-21
did you get this fixed dude?

---

### Post by thomi_ch on 2013-05-15
Hey all

On 13.04 raring 64bit, installing latest MySQL-Workbench from [http://dev.mysql.com/downloads/tools/workbench/#downloads]("http://dev.mysql.com/downloads/tools/workbench/#downloads") will give errors, cause two dependencies are not installed and one of it is lost after Ubuntu Precise:

libctemplate0 (available only in precise)
python-pysqlite2 (still available in raring)

I downloaded and installed this deb package in my 13.04:
[http://packages.ubuntu.com/precise/libctemplate0]("http://packages.ubuntu.com/precise/libctemplate0")

Also installed above python-pysqlite2 and then the following package:
mysql-workbench-gpl-5.2.47-1ubu1204-amd64.deb

And all is ok ;)...

Yes, they should backport libctemplate0 so no manual install of a old package is needed...

Hope this help others to install MySQL-Workbench in Ubuntu Raring.

nice day
thomi

---

