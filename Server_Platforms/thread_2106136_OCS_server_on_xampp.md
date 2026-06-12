---
title: "OCS server on xampp"
date: 2013-01-18
forum: Server Platforms
---

### Post by pmohankumar on 2013-01-18
Hi,

I installed ocs server on windows with the help of xampp. I searched related documents for ubuntu to install ocs server on xampp, i can't find. pls help me to install ocs server with the help of xampp.

Thanks,
Mohan

---

### Post by cariboo on 2013-01-18
Moved to Server Platforms.

Do you mean Microsoft Office Communication Server?

---

### Post by koenn on 2013-01-18
> **pmohankumar said:**
> Hi,

I installed ocs server on windows with the help of xampp. I searched related documents for ubuntu to install ocs server on xampp, i can't find. pls help me to install ocs server with the help of xampp.

Thanks,
Mohan

1- set up a LAMP server, eg with```
 sudo apt-get install apache2 mysql-server php5
```

2- ```
 sudo apt-get install ocsinventory-server ocsinventory-reports 
```

3- point your browser to the relevant URL

iirc, al the rest is managed inside ocs itself.


edit : more details jere :  [http://wiki.ocsinventory-ng.org/index.php/Documentation:Server](http://wiki.ocsinventory-ng.org/index.php/Documentation:Server)

---

### Post by koenn on 2013-01-18
> **cariboo907 said:**
> 
Do you mean Microsoft Office Communication Server?

I'm assuming he means
[http://www.ocsinventory-ng.org/en/](http://www.ocsinventory-ng.org/en/)

---

### Post by pmohankumar on 2013-01-22
Thanks koenn, i installed successfully using the following link:

[http://wiki.ocsinventory-ng.org/index.php/Documentation:Server](http://wiki.ocsinventory-ng.org/index.php/Documentation:Server)

---

### Post by koenn on 2013-01-22
you're welcome
&
have fun

---

