---
title: "Apache 2.4 is ready for you!"
date: 2012-06-27
forum: Server Platforms
---

### Post by ptn107 on 2012-06-27
! Please move thread to Server Platforms ! (my mistake)

The latest stable apache web server 2.4.2 is available for both 12.04 LTS and Quantal Quetzal [1]!  Test away!  Current apache 2.2 users please backup your stuff beforehand!

```
apt-add-repository ppa:ptn107/apache
apt-get update
apt-get install apache2
```

[1]https://launchpad.net/~ptn107/+archive/apache

---

### Post by EssBee on 2012-07-03
On a standard 12.04LTS build, which modules will need to be replaced?

Main concerns are php5_module, ldap_module and authnz_ldap_module

I'm assuming that authnz_ldap_module will need to be recompiled.

Or am I overthinking this and the 2.4.2 build is a drop-in, like-for-like upgrade from stock 2.2.22

---

### Post by hgurol on 2012-08-15
No, php5 module is not available upon installation and copying the module files from another apache 2.2 system into the current installation does not work.

I have also tried to follow the guide here at [http://edin.no-ip.com/blog/hswong3i/apache-2-4-php5-4-pdo-oci-ubuntu-12-04-howto](http://edin.no-ip.com/blog/hswong3i/apache-2-4-php5-4-pdo-oci-ubuntu-12-04-howto) which also didnt work for me very well.

Considering that the apache 2.4.x version is not even in the debian unstable repository yet, its gonna take quite a long time to see it in an official ubuntu release I believe.

> **EssBee said:**
> On a standard 12.04LTS build, which modules will need to be replaced?

Main concerns are php5_module, ldap_module and authnz_ldap_module

I'm assuming that authnz_ldap_module will need to be recompiled.

Or am I overthinking this and the 2.4.2 build is a drop-in, like-for-like upgrade from stock 2.2.22

---

### Post by dffk on 2012-11-24
Hi
I installed Apache 2.4 using the information from the first message. And now I want to install the old Apache.
I removed the Apache 2.4 and removed repository  from the source.
When trying to install Apache - error.

```

apt-get install apache2
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 apache2 : Depends: apache2-mpm-worker (= 2.2.22-1ubuntu1.2) but it is not going to be installed or
                    apache2-mpm-prefork (= 2.2.22-1ubuntu1.2) but it is not going to be installed or
                    apache2-mpm-event (= 2.2.22-1ubuntu1.2) but it is not going to be installed or
                    apache2-mpm-itk (= 2.2.22-1ubuntu1.2) but it is not going to be installed
           Depends: apache2.2-common (= 2.2.22-1ubuntu1.2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```
I tried using:
sudo apt-get -f install
sudo apt-get clean all
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
but it did not help

---

