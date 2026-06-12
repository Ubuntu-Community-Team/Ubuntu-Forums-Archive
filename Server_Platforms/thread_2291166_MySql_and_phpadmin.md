---
title: "MySql and phpadmin"
date: 2015-08-18
forum: Server Platforms
---

### Post by Rui_Brcia on 2015-08-18
Hi,

I'm trying to install mysql but i am having some problems installing it.
The package i'm installing are [B][FONT=Consolas-Bold][SIZE=3][FONT=Consolas-Bold][SIZE=3]mysql-server php5-mysql phpmyadmi
[/SIZE][/FONT][/SIZE][/FONT][/B]In the middle of the installation i find this error o describe bellow.
This is my 3 attempt to install it but every time i try i get errors.
I was able to enter in phpadmin but when i go to users i get another error #1064.
So what i am doing wrong ?


 An error occurred while installing the database:                                                                       &#9474;
 &#9474;                                                                                                                        &#9474;
 &#9474; mysql said: ERROR 1006 (HY000) at line 1: Can't create database 'phpmyadmin' (errno: 2)                                &#9474;
 &#9474;                                                                                                                        &#9474;
 &#9474; If at this point you choose "retry", you will be prompted with all the configuration questions once more and another   &#9474;
 &#9474; attempt will be made at performing the operation. "retry (skip questions)" will immediately attempt the operation      &#9474;
 &#9474; again, skipping all questions.  If you choose "abort", the operation will fail and you will need to downgrade,         &#9474;
 &#9474; reinstall, reconfigure this package, or otherwise manually intervene to continue using it.  If you choose "ignore",    &#9474;
 &#9474; the operation will continue, ignoring further errors from dbconfig-common.                                             &#9474;
 &#9474;                                                                                                                        &#9474;
 &#9474; Next step for database installation:                                                                                   &#9474;
 &#9474;                                                                                                                        &#9474;
 &#9474;                                                 abort                                                                  &#9474;
 &#9474;                                                 retry                                                                  &#9474;
 &#9474;                                                 retry (skip questions)                                                 &#9474;
 &#9474;                                                 ignore



Best Regards

---

### Post by cariboo on 2015-08-19
Did you set a mysql user name and password during the installation process?

---

### Post by LHammonds on 2015-08-20
Don't install phpmyadmin at the same time.  Install mysql 1st, make sure your database is running and THEN install phpmyadmin

---

