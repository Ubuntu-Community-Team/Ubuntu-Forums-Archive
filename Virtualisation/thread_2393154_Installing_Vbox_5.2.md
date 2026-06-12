---
title: "Installing Vbox 5.2"
date: 2018-05-30
forum: Virtualisation
---

### Post by nooshinnr on 2018-05-30
Hi
I'm trying to install Vbox 5.2 on Ubuntu 16.04 but I keep receiving following error:

 E: Package 'virtualbox-5.2' has no installation candidate


what should I do?

---

### Post by howefield on 2018-05-30
What is the output from..

```
apt-cache policy virtualbox
```

Ubuntu 16.04 has Virtualbox version 5.0.18 as far as I can see and you'd need to have Ubuntu 18.04 to get version 5.2 or alternatively get the deb package from the Virtualbox website and install that.

Also, the package name is virtualbox.

---

### Post by SeijiSensei on 2018-05-30
If you use the Oracle repositories, the package name is "virtualbox-5.2".  It carries that name to avoid confusion with the "virtualbox" package in the Ubuntu repositories.  During installation of the -5.2 package, it will remove any existing virtualbox packages it finds.  The Oracle version will also download all the required headers and other code to compile the kernel module from scratch at installation and during any upgrades.

OP, follow the instructions here to add the repository and install VB from Oracle's repository: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

---

### Post by nooshinnr on 2018-05-30
The problem is solved. the previous version of Vbox was not completely removed. after I removed it the new version was installed.

Thank you

---

