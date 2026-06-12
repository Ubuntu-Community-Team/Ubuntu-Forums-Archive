---
title: "PCI scan on 18.04 LTS and Apache 2.4.29"
date: 2020-02-13
forum: Security
---

### Post by gkozuch on 2020-02-13
HI All

We are starting to cooperate with ext vendor, that is using Apache 2.4.29 We scanned his IP before we start using API in production, but scan fails, due to outdated version of Apache. Vendor guys, says he is maintaining this version of Apache and is patching it with OS  patches , and does not have to update Apache version to the latest to cover security. Is this true? The PCI scan is failing, and I got this strange answer from him. Please advice!

Thanks a lot
Greg

---

### Post by EuclideanCoffee on 2020-02-13
The latest is 2.4.41: [https://httpd.apache.org/](https://httpd.apache.org/)

However 2.4.29 is the most recent version for Ubuntu 18.04 LTS. You can check here to confirm. [https://packages.ubuntu.com/bionic/apache2](https://packages.ubuntu.com/bionic/apache2).

You can find the announcement here: [http://www.apache.org/dist/httpd/CHANGES_2.4.41](http://www.apache.org/dist/httpd/CHANGES_2.4.41)

Compare it with changes here: [http://changelogs.ubuntu.com/changelogs/pool/main/a/apache2/apache2_2.4.29-1ubuntu4.11/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/a/apache2/apache2_2.4.29-1ubuntu4.11/changelog)

You may find that all the security updates have been applied to the Ubuntu package. This is known as security packaging, which is different from regular releases.

Focal does currently have a more recent version (this is 20.04 LTS, not yet released).

Since LTS normally only supplies security patches, it is likely your security patches are being applied with OS updates. But as soon as Ubuntu LTS ends in a few years, you will need to upgrade your operating system for continued support unless you purchase support from Ubuntu or a third-party who can install the latest versions of Apache2 regularly.

---

