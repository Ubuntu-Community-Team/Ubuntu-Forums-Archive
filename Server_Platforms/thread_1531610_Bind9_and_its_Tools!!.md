---
title: "Bind9 and its Tools!?!?"
date: 2010-07-15
forum: Server Platforms
---

### Post by nvcnvn on 2010-07-15
I have searched some about Bind9 and have it installed in my server. Now I'm looking for a Tools like [mysqlBind]("http://openisp.net/openisp/mysqlBind") and i found [unxsBind]("http://openisp.net/unxsBind/") is the next version of mysqlBind (These tools help you config BIND DNS with MySQL). But the issue is: I don't know how to Install it in Ubuntu - there just say how to install with Centos (and I'm a Ubuntu newbie! From 1-->17 i just know Window, now, I'm 18 and I love Ubuntu!)

Please help me!
Thanks all of you!

---

### Post by endotherm on 2010-07-15
well since they use yum repos, you will need to get the rpm package downloaded first. there should be a download available on their site. BTW if the old package (mssqlbind) is available in the ubuntu repos, I would use it instead of the new one. 

since ubuntu doesn't use rpm's or yum, we need to convert the package to a .deb so that dpkg can work with it. to do this usually you use a utility called 'alien'

[http://www.howtoforge.com/converting_rpm_to_deb_with_alien](http://www.howtoforge.com/converting_rpm_to_deb_with_alien)

my recommendation is that once you have the rpm file, run a line like:
```

sudo alien -k -i <path to rpm>

```this will convert the .rpm to a .deb and install it using dpkg all in one step assuming all the dependencies are met.

---

### Post by nvcnvn on 2010-07-16
Oh, thanks you! I just done it!

---

