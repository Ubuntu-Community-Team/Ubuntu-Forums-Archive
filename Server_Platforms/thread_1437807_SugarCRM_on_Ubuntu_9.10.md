---
title: "SugarCRM on Ubuntu 9.10"
date: 2010-03-24
forum: Server Platforms
---

### Post by satimis on 2010-03-24
Hi folks,

Ubuntu 9.10 64bit
SugarCRM Community Edition 5.5.1
[https://www.sugarcrm.com/crm/download/sugar-suite.html](https://www.sugarcrm.com/crm/download/sugar-suite.html)


I'm going to follow the old version of tutorial;
Installing SugarCRM Community Edition On Ubuntu 8.10
[http://www.howtoforge.com/installing-sugarcrm-community-edition-on-ubuntu-8.10](http://www.howtoforge.com/installing-sugarcrm-community-edition-on-ubuntu-8.10)

because no new version found there.  

The packages needed for Apache Webserver and PHP are;```

apache2 
apache2-doc 
apache2-mpm-prefork 
apache2-utils 
libexpat1 
libapache2-mod-php5 
php5-common 
php5-gd 
php5-idn 
php-pear 
php5-imap 
php5-mcrypt 
php5-mhash 
php5-mysql 
php5-sqlite 
php5-xmlrpc 
php5-xsl 
php5-curl

```

Where can I check their latest version?  TIA


B.R.
satimis

---

### Post by cdenley on 2010-03-24
> **satimis said:**
> 
Where can I check their latest version?

Check what version is the latest in the ubuntu 9.10 repository? Check that you have those installed and that they are the most current in the ubuntu 9.10 repository? Do you use a GUI? If so, use System>Administration>Synaptic Package Manager. If not, this will install those packages if they aren't installed, or upgrade if there is a more recent version.
```

sudo apt-get update
sudo apt-get install apache2 apache2-doc apache2-mpm-prefork apache2-utils libexpat1 libapache2-mod-php5 php5-common php5-gd php5-idn php-pear php5-imap php5-mcrypt php5-mhash php5-mysql php5-sqlite php5-xmlrpc php5-xsl php5-curl

```

---

### Post by satimis on 2010-03-24
> **cdenley said:**
> Check what version is the latest in the ubuntu 9.10 repository? Check that you have those installed and that they are the most current in the ubuntu 9.10 repository? Do you use a GUI? If so, use System>Administration>Synaptic Package Manager. If not, this will install those packages if they aren't installed, or upgrade if there is a more recent version.
```

sudo apt-get update
sudo apt-get install apache2 apache2-doc apache2-mpm-prefork apache2-utils libexpat1 libapache2-mod-php5 php5-common php5-gd php5-idn php-pear php5-imap php5-mcrypt php5-mhash php5-mysql php5-sqlite php5-xmlrpc php5-xsl php5-curl

```

Hi cdenley,

Thanks for your advice.

I haven't installed them yet.  I'm going to install a base Ubuntu 9.10 OS first without GUI.  Afterwards I'll install those packages.  Because I follow the howto which has been created for sometimes.  I don't know whether those packages are the latest version.  OR there are newer version replacing them.

B.R.
satimis

---

### Post by cdenley on 2010-03-24
> **satimis said:**
> Hi cdenley,

Thanks for your advice.

I haven't installed them yet.  I'm going to install a base Ubuntu 9.10 OS first without GUI.  Afterwards I'll install those packages.  Because I follow the howto which has been created for sometimes.  I don't know whether those packages are the latest version.  OR there are newer version replacing them.

B.R.
satimis

I believe all those packages are in the 9.10 repository. The versions in the 9.10 repository will be newer than the versions in the 8.10 repository of course, but I don't think any of them have been renamed or replaced. php5 is still available.

---

