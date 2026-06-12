---
title: "Unable to install php5.6-fpm on Ubuntu 16.04"
date: 2021-08-23
forum: Server Platforms
---

### Post by kumar3314 on 2021-08-23
Hello All,

We are trying to install php5.6-fpm on Ubuntu 16.04 server but we unable to install. We are following the below steps to install.

sudo apt-get install python-software-properties
sudo add-apt-repository ppa:ondrej/php
sudo apt-get update

sudo apt-get install -y php5.6

**Error while installing:-**
$apt-get install php5.6-fpm
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package php5.6-fpm
E: Couldn't find any package by glob 'php5.6-fpm'
E: Couldn't find any package by regex 'php5.6-fpm'

Can someone help me with the possible solution to install php 5.6-fpm

---

### Post by Frogs Hair on 2021-08-23
16.04 reached end of life in April unless you have Extend Maintenance Security. That may explain why the package is not found. 
[https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)

---

### Post by kumar3314 on 2021-08-23
Hello Frogs,

Thanks for the update. We are using Ubuntu 16.04 in Azure from Canonical publisher which comes with Extended Maintenance Security. Is there anything to be done to get php5.6-fpm to be installed.

---

### Post by Frogs Hair on 2021-08-23
> **kumar3314 said:**
> Hello Frogs,

Thanks for the update. We are using Ubuntu 16.04 in Azure from Canonical publisher which comes with Extended Maintenance Security. Is there anything to be done to get php5.6-fpm to be installed.

I can't tell you tell you what package repositories other than security are available with EMS. The Ubuntu old repositories are available, but mainly for distribution upgrade purposes.

---

### Post by slickymaster on 2021-08-24
*Thread moved to **Server Platforms**.*

---

### Post by MAFoElffen on 2021-08-24
LOL

You need to add this PPA . He does have a note about end-of release Ubuntu, but worth a try. He is the main maintainer for the PHP packages...
```
sudo add-apt-repository ppa:ondrej/php
sudo apt-get update
sudo apt-get install php5.6-fpm

```
Enjoy...

---

