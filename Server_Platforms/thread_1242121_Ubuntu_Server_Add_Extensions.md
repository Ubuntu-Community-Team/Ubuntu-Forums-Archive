---
title: "Ubuntu Server Add Extensions"
date: 2009-08-16
forum: Server Platforms
---

### Post by HighCommander540 on 2009-08-16
Hello, so I have had my Ubuntu Apache server for a long time and before that I started on an Apache server on windows.

There is one thing that I just realized and looked for, but couldn't find in the Ubuntu build of it.

I can't find either the line that adds PHP as a file extension for Apache to process, or the DirectoryIndex command. Which would let me specific what I want to be displayed as an index.

Can anyone help me with this? Doesn't apache need the add file extension line for PHP to work?

---

### Post by windependence on 2009-08-17
**Troubleshooting PHP 5**

 Does your browser ask if you want to **download the php** file instead of displaying it?  If Apache is not actually parsing the php after you restarted it, install libapache2-mod-php5.  It is installed when you install the php5 package, but may have been removed inadvertently by packages which need to run a different version of php. 
You may also need to actually enable it, by doing sudo a2enmod php5 followed by sudo /etc/init.d/apache2 restart.  If sudo a2enmod php5 returns "$ This module does not exist!", you should purge (not just remove) the libapache2-mod-php5 package and reinstall it. 
Be sure to clear your browser's cache before testing your site again.

[https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20PHP%205)

-Tim

---

