---
title: "Webmin install on 8.04 LTS"
date: 2009-07-18
forum: Server Platforms
---

### Post by hank122s on 2009-07-18
Greetings,
I'm trying out an Ubuntu server version 8.04 LTS on my VPS and I'm fairly new to the package management system.
It seems Webmin is available as a .deb package for Ubuntua and Debian. I'm having trouble with dependencies whether I use aptitude or dpkg commands. The latest error is saying;
 
"The following packages have unmet dependencies:
webmin: Depends: libnet-ssleay-perl but it is not installable
Depends: libauthen-pam-perl but it is not installable
Depends: libio-pty-perl but it is not installable
Depends: libmd5-perl but it is not installable"
 
Not sure how those can be "not installable" ? I've spent many hours on CentOS and always had luck with commands such as;
 
'yum install php-*' or 
'yum install perl-*'
 
That covers alot of dependencies. Is there some way to do that with apt-get?
 
tia
hank.

---

### Post by ktrnka on 2009-07-19
Sure apt is very easy to use. Similar to yum.

```
sudo apt-get install libauthen-pam-perl libio-pty-perl libmd5-perl 
```

Need to find a package
```
sudo apt-cache search packagename
```

---

### Post by hank122s on 2009-07-19
> **ktrnka said:**
> Sure apt is very easy to use. Similar to yum.

```
sudo apt-get install libauthen-pam-perl libio-pty-perl libmd5-perl 
```Need to find a package
```
sudo apt-cache search packagename
```


That did it, thanks for the help.

Hank.

---

### Post by ktrnka on 2009-07-19
Glad to help.

---

