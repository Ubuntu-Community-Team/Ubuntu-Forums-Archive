---
title: "pdflib: Installation"
date: 2011-07-07
forum: Server Platforms
---

### Post by smmnazar on 2011-07-07
Hello, I tried to install pdflib following by the steps in this URL [http://www.atforumz.com/archive/index.php/t-297404.html](http://www.atforumz.com/archive/index.php/t-297404.html)
but I am not able to install pdflib using this command "sudo pecl install pdflib" and the installation is ended like below.

netable@ubuntu:~$ sudo pecl install pdflib
sudo: unable to resolve host ubuntu
downloading pdflib-2.1.8.tgz ...
Starting to download pdflib-2.1.8.tgz (55,797 bytes)
.............done: 55,797 bytes
netable@ubuntu:~$

Please advise why it stopped like this.

Thank you,

---

### Post by flickerfly on 2011-11-16
sounds like the problem is that your /etc/hosts file doesn't have a line for your machine name. Trying adding the line "yo.ur.ip.ad ubuntu" where yo.ur.ip.ad is your machines external IP address.

---

