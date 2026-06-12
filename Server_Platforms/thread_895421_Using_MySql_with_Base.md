---
title: "Using MySql with Base"
date: 2008-08-20
forum: Server Platforms
---

### Post by Pengwyn44 on 2008-08-20
I have followed the instructions given on the LinuxFormat cover disk LXFS11 to enable me to open a MySql database using OpenOffice Org Database as a front end. All goes well up to and including "Test Class". The problem arises when I "Test Connection". This fails and I get this error message.

"Error during query Unexpected Exception - java.io.CharConversionException - message given:null." Then follows a page full of information (all without meaning to me!).

My database is called 'mysql' and I can enter it instantly via the Terminal as root with a password. To be able to enter it via Base would be a big advantage. Please help if you can.
My OS is Ubuntu 8.04.
Pengwyn44

---

### Post by Ximbiot on 2008-08-20
a CharConversionException sounds like you are using a character set in your database (e.g., UTF8, LATIN1, etc.) that Base doesn't know how to convert to the local charset.  Have you tried googling your error message with "CharConversionException OO Base"?  I just did and found this [previous forum post which may solve your problem]("http://ubuntuforums.org/archive/index.php/t-503699.html").

---

### Post by Pengwyn44 on 2008-08-26
Thanks for the tip, I have copied the information from the 'bugs' site which says to "put 'useJvmCharsetConverters = true' in the JDBC connection URL properties".   However it doesn't say where I can find this file.
Is it /etc/mysql/my.cnf?
My knowledge of Linux is still somewhat basic.
Bryan

---

