---
title: "Add canon ip1500 printer drivers"
date: 2007-10-20
forum: Ubuntu Brainstorm
---

### Post by pdlethbridge on 2007-10-20
The addition of canon pixma ip1500 printer drivers should be done by default.

---

### Post by Twintop on 2007-10-22
Do drivers for this printer already exist, or are you asking for them to be created? Also if they do exist, are they already available through apt-get? If they are, then it might be a space-vs-usage argument about including them on the CD.

---

### Post by pdlethbridge on 2007-10-22
drivers exist, this has to be added to your source list
deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./

---

### Post by thushw on 2008-09-20
this works on ubuntu 8.04 / kernel 2.6.24 

thushara@gini-sisila:~$ uname -r
2.6.24-19-generic

thushara@gini-sisila:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

---

