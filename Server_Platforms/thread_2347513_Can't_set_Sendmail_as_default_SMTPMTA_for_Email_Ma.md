---
title: "Can't set Sendmail as default SMTP/MTA for Email Marketing Automation"
date: 2016-12-26
forum: Server Platforms
---

### Post by keoz2 on 2016-12-26
Hello, :)
[B]
*** My material ***[/B]
A remote server (VPS) that has **LAMP** and distro **Ubuntu 16.04** installed.

***** OPENEMM install fails ******
OpenEMM (web based app) stands for : **Open Source E-Mail Marketing automation**.
I choosed to set **Sendmail SMTP** as its **default MTA** (Mail Transfer Agent), but **I can't pursue the installation** of OpenEMM because the terminal outputs **"command not found**" in reply to **command line** entry **"alternatives --set mta /usr/sbin/sendmail.sendmail"**.

This entry is shown on **page 5 (section 3.1)** of this [OpenEMM install guide]("http://docdro.id/Bur7vwj") 
And however I did correctly followed and executed the previous instructions (shown below), the terminal still outputs **"command not found"**

***** Install guide (previous steps) *****
username@vpsNUMBER:~# sudo service postfix stop
username@vpsNUMBER:~# sudo apt-get install sendmail

**Did someone else ever faced and solved this issue ?**
Awaiting for some help and guidance asap please !!! :mad:

KS

---

### Post by SeijiSensei on 2016-12-26
Did you read the 1.1 Requirements section?  The program is designed to run on RedHat, not Ubuntu or Debian.  You need to install [CentOS]("http://www.centos.org/"), the free respin of RedHat Enterprise Linux, if you want to follow that guide.

---

