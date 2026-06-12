---
title: "Problems with apt-get updating openSSL"
date: 2008-09-03
forum: Server Platforms
---

### Post by salbil on 2008-09-03
I am helping out some folks trying to update openssl to get a new certificate issued, based on an openSSL vulnerability in Ubuntu. When I run apt-get, I get the following. The openSSL remains 0.9.8c. Any help to fix this, or instructions on getting openSSL updated without using apt-get would be helpful. I have 6 days to rekey the certificate. I'm a redhat guy, so this apt-get thing makes me nervous...

apt-get -f upgrade openssl
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.20.3-ubuntu1-custom (2.6.20.3-ubuntu1-custom-10.00.Custom) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20.3-ubuntu1-custom
find: /lib/firmware/2.6.20.3-ubuntu1-custom: No such file or directory
find: /lib/firmware/2.6.20.3-ubuntu1-custom: No such file or directory
find: /lib/firmware/2.6.20.3-ubuntu1-custom: No such file or directory
find: /lib/firmware/2.6.20.3-ubuntu1-custom: No such file or directory
find: /lib/firmware/2.6.20.3-ubuntu1-custom: No such file or directory
find: /lib/firmware/2.6.20.3-ubuntu1-custom: No such file or directory
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.
The provided postinst hook script [/sbin/update-grub] could not be run.
dpkg: error processing linux-image-2.6.20.3-ubuntu1-custom (--configure):
 subprocess post-installation script returned error exit status 2
Setting up linux-image-2.6.20-17-server (2.6.20-17.39) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-17-server
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.
The provided postinst hook script [/sbin/update-grub] could not be run.
dpkg: error processing linux-image-2.6.20-17-server (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-2.6.20-17-server; however:
  Package linux-image-2.6.20-17-server is not configured yet.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 2.6.20.17.30); however:
  Package linux-image-server is not configured yet.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-amd64-server:
 linux-amd64-server depends on linux-server (= 2.6.20.17.30); however:
  Package linux-server is not configured yet.
dpkg: error processing linux-amd64-server (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.20-16-server (2.6.20-16.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-server
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.
The provided postinst hook script [/sbin/update-grub] could not be run.
dpkg: error processing linux-image-2.6.20-16-server (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-amd64-server:
 linux-image-amd64-server depends on linux-image-server (= 2.6.20.17.30); however:
  Package linux-image-server is not configured yet.
dpkg: error processing linux-image-amd64-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.20.3-ubuntu1-custom
 linux-image-2.6.20-17-server
 linux-image-server
 linux-server
 linux-amd64-server
 linux-image-2.6.20-16-server
 linux-image-amd64-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by windependence on 2008-09-04
[http://www.ubuntu.com/usn/usn-612-1](http://www.ubuntu.com/usn/usn-612-1)

The fix:

[http://www.ubuntugeek.com/fix-for-opensslsshvpn-vulnerability-in-ubuntu-704710804.html](http://www.ubuntugeek.com/fix-for-opensslsshvpn-vulnerability-in-ubuntu-704710804.html)

[http://ubuntu-tutorials.com/2008/05/13/openssh-openssh-vulnerabilities-confirm-fix-instructions/](http://ubuntu-tutorials.com/2008/05/13/openssh-openssh-vulnerabilities-confirm-fix-instructions/)

[http://www.ubuntuhacker.com/index.php/2008/05/14/how-to-patch-ubuntu-for-openssl-and-openssh-vulnerability/](http://www.ubuntuhacker.com/index.php/2008/05/14/how-to-patch-ubuntu-for-openssl-and-openssh-vulnerability/)

Hope this helps,

-Tim

---

### Post by salbil on 2008-09-05
Thank you for your response. Unfortunately, I think most of these articles assume that apt will successfully upgrade openssl and show the procedure to follow afterward. The issue I am having is that it is not upgrading and it looks like it doesn't think it should. 

After the apt-get update, when I do the apt-get upgrade or apt-get dist-upgrade, I get the following:

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y

But openSSl is still the same. Short of recompiling from source, does anyone know of any other thing I can check?

---

### Post by windependence on 2008-09-05
If you read what I posted, there are several there that tell you exactly what steps to take to make sure you have fixed the problem. Please re-read the articles. Not all of them tell you to just re-install. Even so, the repositories don't have the compromised version anymore. 

-Tim

---

### Post by salbil on 2008-09-05
OK, got it, the openssl package was screwed up. Thanks for your help, they articles were helpful once I got it updated.

---

### Post by windependence on 2008-09-05
Kewl. glad you got it fixed. Fortunately, this doesn't happen often.

-Tim

---

