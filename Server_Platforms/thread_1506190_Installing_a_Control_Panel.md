---
title: "Installing a Control Panel?"
date: 2010-06-10
forum: Server Platforms
---

### Post by thatryan on 2010-06-10
Just bought a new (ve) server at Media Temple, trying to install a control panel. Is webmin the one to use? What is recommended? 
I installed newest Ubuntu version, 10.04 and the only guide MT has for installing webmin is for 9.1
[http://wiki.mediatemple.net/index.php/Install_Webmin_on_Ubuntu_9.10](http://wiki.mediatemple.net/index.php/Install_Webmin_on_Ubuntu_9.10)
Is it all the same? I get errors when trying to install, it wont run the dpkg install process.

---

### Post by xerophyte on 2010-06-10
Depends on how are you going to use the server for 

for example if you are going to use only for personal server stuff like hosting your own website then webmins should be good. but if you are trying host for others you might want to consider DirectAdmin or Cpanel 


to help with your installation issue you need to give us more info and cut and paste the errors you are getting

---

### Post by thatryan on 2010-06-10
Thanks, yes mostly for now at least will just be my own websites. 

The error I am getting is here, 

```

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/
Last login: Thu Jun 10 01:06:50 2010 from astound-64-85-237-4.ca.astound.net
******:~# dpkg --install webmin_1.510_all.deb.2
(Reading database ... 41798 files and directories currently installed.)
Preparing to replace webmin 1.510 (using webmin_1.510_all.deb.2) ...
Unpacking replacement webmin ...
dpkg: dependency problems prevent configuration of webmin:
 webmin depends on libnet-ssleay-perl; however:
  Package libnet-ssleay-perl is not installed.
 webmin depends on libauthen-pam-perl; however:
  Package libauthen-pam-perl is not installed.
 webmin depends on libio-pty-perl; however:
  Package libio-pty-perl is not installed.
 webmin depends on libmd5-perl; however:
  Package libmd5-perl is not installed.
dpkg: error processing webmin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 webmin
******:~# 


```

---

### Post by spynappels on 2010-06-10
You need to run the following command:

```
sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl
```

This will install the packages that Webmin needs or depends on. When these are in place, the Webmin installation will complete.

---

### Post by thatryan on 2010-06-10
Hey thanks.

I tried running that command and got this, 

```


********:~# sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
perl is already the newest version.
openssl is already the newest version.
libpam-runtime is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  webmin: Depends: libmd5-perl but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
********:~# 


```

---

### Post by _Mark_ on 2010-06-10
Try this [http://woodel.com/index.html](http://woodel.com/index.html) you can obviously miss out the part about installing Debian and various other steps, the author assumes you will be administering the server from a windows machine and installs putty for SSH but if you are doing it from another linux box you can SSH from bash

---

