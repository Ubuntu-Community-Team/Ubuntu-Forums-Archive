---
title: "Postfix Error"
date: 2013-04-29
forum: Server Platforms
---

### Post by Shadal on 2013-04-29
I am on a Linode VPS 1024 Server running Ubuntu 12.04.
Installed Software includes Apache2, PHP, MySQL, Postfix, Dovecot.

I recently upgraded my Linode and in the process had to switch my Kernel from 32bit to 64bit.

Around that time Postfix began throwing errors like
postfix/cleanup[17164]: warning: mysql:/etc/postfix/mysql_virtual_alias_maps.cf is unavailable. unsupported dictionary type: mysql

My mail.log is at [http://pastebin.com/zqGrwe2J](http://pastebin.com/zqGrwe2J)
Postconf -n [http://pastebin.com/zmd9rZHc](http://pastebin.com/zmd9rZHc)
Postconf -m [http://pastebin.com/gq3QHELv](http://pastebin.com/gq3QHELv)

I tried the Postfix IRC channel, but was told this was told
"Debian modifies postfix to allow them to dynamically load support for different DB types.  Postfix is saying in the logs that it doesn't support mysql, and yet according to postconf -m it does.  I can only conclude that this is affected by the code that debian has modified, and since it is modified by debian you will need to get support from the debian (or ubuntu) package maintainer for this issue." 


Can anyone help? Thanks!

---

### Post by SeijiSensei on 2013-04-30
Try installing the **postfix-mysql** package if it's not installed already.  Often features like this which rely on modules to interface with other software are packaged separately.  The same holds true for PHP5, which has a php5-mysql package to handle the same task for that software.

You can see all the packages with a given string in their names with the command "apt-cache search string".  I found postfix-mysql by running "apt-cache search postfix".

---

### Post by Shadal on 2013-05-03
> **SeijiSensei said:**
> Try installing the **postfix-mysql** package if it's not installed already.  Often features like this which rely on modules to interface with other software are packaged separately.  The same holds true for PHP5, which has a php5-mysql package to handle the same task for that software.

You can see all the packages with a given string in their names with the command "apt-cache search string".  I found postfix-mysql by running "apt-cache search postfix".

Yes, thank you.
apt-get reinstall install postfix-mysql corrected the postfix errors, then dovecot started throwing similar errors, a quick apt-get reinstall install dovecot-mysql corrected that error.

---

