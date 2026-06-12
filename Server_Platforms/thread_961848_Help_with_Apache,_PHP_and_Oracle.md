---
title: "Help with Apache, PHP and Oracle"
date: 2008-10-28
forum: Server Platforms
---

### Post by NewToLinuxAIR on 2008-10-28
Hi

I have Ubuntu 8.04 install on PC, and with the installation I have selected to install Apache and PHP, however, being rather new to Linux, I don't know where to find the folders for Apache and PHP along with the folders to store my static and dynamic web pages. Can someone tell me where to find them, please?

Further, I have also installed Oracle Express 10g, and which stored successfully. However, when I click on the link that takes you to the web page to login into Oracle, the page does not work. Does anyone know how to fix this problem, please? I am little confused on this problem though as I can get into SQLPlus!

Thanks

:confused:

---

### Post by bodhi.zazen on 2008-10-28
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

[http://www.pythian.com/blogs/654/installing-oracle-11g-on-ubuntu-linux-710-gutsy-gibbon](http://www.pythian.com/blogs/654/installing-oracle-11g-on-ubuntu-linux-710-gutsy-gibbon)

---

### Post by finite9 on 2008-10-29
the link for Oracle does not help.  just explains how to install oracle.

Do you mean that you're trying to login to the Enterprise Manager web interface?  In that case, the link usually points to http://<host.domain>:1158/em for example.  In some cases, the domain does not work so try [http://localhost:1158/em](http://localhost:1158/em)  You can check which port it is running on by looking at the $ORACLE_HOME/install/portlist.ini file.  If Oracle installed the Enterprise manager console in secure mode then you need to use [https://localhost:1158/em](https://localhost:1158/em) to access the login page.

---

