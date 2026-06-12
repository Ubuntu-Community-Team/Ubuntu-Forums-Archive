---
title: "libapache2-mod-php4 doesn't install all files"
date: 2005-03-30
forum: Server Platforms
---

### Post by Stephen-I-M on 2005-03-30
I don't see these two files:

   /etc/apache2/mods-available/php4.load
   /etc/apache2/mods-available/php4.conf

after reinstalling libapache2-mod-php4. How can I get them to install? Thanks.

Stephen

Install log:

# aptitude reinstall libapache2-mod-php4
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
The following packages have been kept back:
[snip lots of kde stuff]
The following packages will be REINSTALLED:
  libapache2-mod-php4
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 59 not upgraded.
Need to get 0B/1590kB of archives. After unpacking 0B will be used.
Writing extended state information... Done

Preconfiguring packages ...
(Reading database ... 99870 files and directories currently installed.)
Preparing to replace libapache2-mod-php4 4:4.3.10-2ubuntu4 (using .../libapache2-mod-php4_4%3a4.3.10-2ubuntu4_i386.deb) ...
Unpacking replacement libapache2-mod-php4 ...
Setting up libapache2-mod-php4 (4.3.10-2ubuntu4) ...

Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done

---

### Post by defkewl on 2005-04-03
Did you try apt-get install?
Please state your problems more detail please.

---

### Post by daniels on 2005-04-04
dpkg -i --force-confmiss /var/cache/apt/archives/libapache2-mod-php4_*.deb

---

### Post by anggarda on 2005-05-06
I've got the same problem with the same app. 

It is something that should be reported as a bug?

---

