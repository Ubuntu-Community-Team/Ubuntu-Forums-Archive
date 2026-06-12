---
title: "Webmin on edgy eft server 6.10"
date: 2008-07-29
forum: Server Platforms
---

### Post by iFRE4K on 2008-07-29
I'm trying to install webmin on my server, but I get the following error:

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package webmin is not available, but is referred to by another package.
This may mean the package is missing, has been obsoleted, or is only available from another source
E: Package webmin has no installation candidate

This is the code I type in:

sudo apt-get install webmin webmin-core

Thanks for any help given.

---

### Post by iFRE4K on 2008-08-04
Ok so still no help. Someone out there has to know something. Please.

---

### Post by braddcadd on 2008-08-23
I am running Hardy, and it is not in the repositories.

---

### Post by gjoellee on 2008-08-23
not in the repositories

---

### Post by windependence on 2008-08-23
First you need to install the following packages

```
sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl
```

Now download the latest webmin using the following command

```
wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.420_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.420_all.deb)
```

Now we have webmin_1.420_all.deb package install this package using the following command

```
sudo dpkg -i webmin_1.420_all.deb
```

This will complete the installation.

Ubuntu in particular doesn't allow logins by the root user by default. However, the user created at system installation time can use sudo to switch to root. Webmin will allow any user who has this sudo capability to login with full root privileges.

Now you need to open your web browser and enter the following

[https://your-server-ip:10000](https://your-server-ip:10000)

You should now see the login page.

-Tim

---

