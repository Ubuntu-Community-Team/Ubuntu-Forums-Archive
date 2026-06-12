---
title: "MySQL - installation problem"
date: 2006-12-26
forum: Server Platforms
---

### Post by Hoffmann on 2006-12-26
Hi:

When I try to install MySQL with:

sudo apt-get install mysql-server

I get the error:


/etc/init.d/mysql: line 122: /etc/mysql/debian-start: No such file or directory
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script killed by signal (Interrupt)
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

Could anyone, please, help me to solve this?

Thanks

---

### Post by Brazen on 2006-12-26
does this machine have internet access?  try "ping www.google.com" at a command line.

---

### Post by Hoffmann on 2006-12-26
> **Brazen said:**
> does this machine have internet access?  try "ping www.google.com" at a command line.

Yes. I do have Internet access.

---

### Post by nsleiman on 2006-12-26
try to: ´sudo dpkg --configure´ this will configure all previously installed packages.

---

### Post by Hoffmann on 2006-12-26
> **nsleiman said:**
> try to: ´sudo dpkg --configure´ this will configure all previously installed packages.

I still have problems. When I followed your suggestion, I got:


> sudo dpkg --configure mysql
dpkg: error processing mysql (--configure):
 no package named `mysql' is installed, cannot configure
Errors were encountered while processing:
 mysql

However, see what I have below:

> ~$ which mysql
/usr/bin/mysql 

---

### Post by not_cool on 2006-12-26
the package is mysql-server-5.0, not mysql

---

### Post by Hoffmann on 2006-12-26
> **not_cool said:**
> the package is mysql-server-5.0, not mysql

Once again, didn't work:

> sudo dpkg --configure mysql-server-5.0
Setting up mysql-server-5.0 (5.0.24a-9) ...
 * Stopping MySQL database server mysqld                                 [ ok ] 
 * Starting MySQL database server mysqld                                 [ ok ] 
/etc/init.d/mysql: line 122: /etc/mysql/debian-start: No such file or directory
invoke-rc.d: initscript mysql, action "start" failed.

Should I install MySQL from its source code?

---

### Post by Hoffmann on 2006-12-27
Ok...

Since, even from its source MySQL doesn't work at all. All I can do is to run it from my Windows XP partition. From Windows, MySQL works as a charm.

---

### Post by yesudeep on 2007-12-21
Have you checked /var/log/syslog?
Please paste the output of 

```

cat /var/log/syslog

```

and wait for a response.

Regards,
Yesudeep.

---

### Post by Select* on 2008-03-09
This should fix your MYSQL installation / reinstallation issues, if your getting "dpkg: error processing mysql-server-5.0 (--configure):
" or other similar error.

If you have downloaded an already tried to install make sure all your mysql packages are removed. This step can be skipped, but I found when I had this issue I tried many different installation commands and wanted to remove all. The following command will remove MYSQL and MYSQL 5.0.

sudo apt-get autoremove --purge mysql-server mysql-server-5.0 
(^if root remove sudo)

Now reinstall with the following command, which will install the latest MYSQL

sudo apt-get install mysql-server 
(^if root remove sudo)

You will probably get the same error again, but don't dispair. Change to directory /etc/mysql/ and edit the my.cnf file by doing the following.

cp my.cnf my.cnf.bak
vi my.cnf

Once you have the file open navigate down till you see the bind-address setting. You may see two but only one should be un-commented. Change the bind-address setting so it looks like bind-address = 0.0.0.0 and save the file.

Now we will finish configuration of MYSQL by using the following command.

sudo dpkg --configure -a
(^if root remove sudo)

This command will continue all unfinished software auto configurations, in this case MYSQL. The database should start this time.

Edit the my.cnf file again to change the bind-address to the IP address of choice (127.0.0.0 for local only) or external interface IP address. Issue command to restart MYSQL and you should be good to go.

sudo /etc/init.d/mysql restart
(^if root remove sudo)

---

### Post by rennen01 on 2008-03-16
This was helpful, Thanks.

mysql will restart with if I modify the my.cnf to any address other than 0.0.0.0

Any suggestions?

---

