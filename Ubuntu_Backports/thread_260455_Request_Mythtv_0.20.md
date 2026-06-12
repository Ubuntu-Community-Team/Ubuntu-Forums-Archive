---
title: "Request: Mythtv 0.20"
date: 2006-09-18
forum: Ubuntu Backports
---

### Post by mikedtemple on 2006-09-18
Been having a heckuva time finding quality mythtv builds.  Now that 0.20 made it into Edgy, any hope for a backport?  I'd love to upgrade my box from 0.18.1 and Breezy.

---

### Post by cowmix on 2006-09-19
Here are some Mythtv .20 dpkgs for Dapper..

[http://home.eng.iastate.edu/~superm1/dists/dapper/main/binary-i386/](http://home.eng.iastate.edu/~superm1/dists/dapper/main/binary-i386/)

I wonder if anyone has used them yet..

---

### Post by gitfiddler on 2006-09-21
I tried last night, and got an error concerning "myth-database", something about "package is not available". It was late, so I'll play with it again tonight.

---

### Post by Anthem on 2006-10-02
What's the latest?  Any hope of getting .20 in Dapper Backports?

---

### Post by dave1216 on 2006-10-12
Hi All,

Worked spiffin' my end.  Was literally a case of apt-get!

Oh, make a note of the mythconverg password it set's on the database, you will need to edit this in mysql.txt (or mythtv-setup)

:-D

---

### Post by superm1 on 2006-10-26
There is a request open, and a dupliate request open too.  We are just waiting on a MOTU to ack support in dapper that the package works.

[https://launchpad.net/products/dapper-backports/+bug/51680](https://launchpad.net/products/dapper-backports/+bug/51680)
[https://launchpad.net/products/dapper-backports/+bug/64884](https://launchpad.net/products/dapper-backports/+bug/64884)

---

### Post by stanwebber on 2007-01-14
is this close to being backported to dapper now?

---

### Post by superm1 on 2007-01-26
> **stanwebber said:**
> is this close to being backported to dapper now?
Yes.

The main package backport is completed, binaries are available:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=myth&searchon=names&subword=1&version=dapper-backports&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=myth&searchon=names&subword=1&version=dapper-backports&release=all)


The plugins just need an archive admin to ack the build, and they should hopefully be available shortly.

---

### Post by Hobgoblin on 2007-02-22
Any news on the plugins.:confused: Pleeeese

---

### Post by superm1 on 2007-03-25
Plugins are up in backports too now.

---

