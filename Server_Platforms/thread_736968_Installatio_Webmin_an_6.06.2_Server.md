---
title: "Installatio Webmin an 6.06.2 Server"
date: 2008-03-27
forum: Server Platforms
---

### Post by Teimi on 2008-03-27
Hello
So, i am new on Ubuntu an try to install Webmin 1.400 on a Ubuntu Server 6.06.2 Version.
I saw a lot of other threads, but the don't help me with my problem.

I tried to install it on two different ways.
1. Try to install with apt-get install webmin and get the following message
```

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  webmin: Depends: libauthen-pam-perl but it is not installable
          Depends: libmd5-perl but it is not installable
E: Broken packages

```

2. I tried it dpkg -i webmin_1.400_all.deb an get the following message
```

Selecting previously deselected package webmin.
(Reading database ... 16177 files and directories currently installed.)
Unpacking webmin (from webmin_1.400_all.deb) ...

dpkg: dependency problems prevent configuration of webmin:
 webmin depends on libauthen-pam-perl; however:
  Package libauthen-pam-perl is not installed.
 webmin depends on libmd5-perl; however:
  Package libmd5-perl is not installed.
dpkg: error processing webmin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 webmin

```


I dont find a way to install this two packeges:
Depends: libauthen-pam-perl but it is not installable
Depends: libmd5-perl but it is not installable

could someone help me please?

Thanks
Martin

---

### Post by volkswagner on 2008-03-27
You may need to edit /etc/apt/sources.lst
allow multiverse and universe by uncomment out the #.

---

### Post by Teimi on 2008-03-28
:KS WOW, that easy...

Thank you very much!!

---

