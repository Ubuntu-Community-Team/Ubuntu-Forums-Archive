---
title: "#2002 Cannot log in to the MySQL server"
date: 2011-02-18
forum: Server Platforms
---

### Post by adeee on 2011-02-18
hay guys whenever i try to connect with phpmyadmin igot this error "#2002 Cannot log in to the MySQL server" 

how to recover this error?
can anybody help me?

---

### Post by HugoSerrano on 2011-02-18
Hi!

Is the service running?

Try to login in a command line.

Regards.

---

### Post by adeee on 2011-02-18
> **HugoSerrano said:**
> Hi!

Is the service running?

Try to login in a command line.

Regards.
yes its running. 
While just putting  only this command 
mysql

  error is

[B] ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

and in /var/run/mysqld/mysql.sock

[/B]There are any file of that type.

and when i put this command.

```
service mysql start
```output is 

**start: Rejected send message, 1 matched rules; type="method_call", sender=":1.61" (uid=1000 pid=3960 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))**

and putting this command is
[B]
sudo /etc/init.d/mysql start[/B]

massage is 

[B]Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start mysql
start: Job is already running: mysql[/B]

---

### Post by Qu4rk on 2011-03-21
Did you solve this?  I have the same exact problem?

---

### Post by SeijiSensei on 2011-03-21
Try "sudo service mysql restart".

---

### Post by Qu4rk on 2011-03-21
> **SeijiSensei said:**
> Try "sudo service mysql restart".

Nothing.  I've also tried multiple reboots.  Any other suggestions?

---

### Post by Java_Guy on 2011-07-05
I've been having the same problem, but I think I may have sorted it out..

Solution:
Assuming you used the setup.php file to setup phpMyAdmin, once you've finished configuring your mysql server and you've saved the changes, copy the config.inc.php file, auto-created in the config/ folder, out into the phpMyAdmin folder.. Make sure it's write-protected and delete the config/ folder.. Then refresh your browser..

Worked for me.. Hope it works for you too.

Cheers.

---

### Post by dafir06 on 2011-11-30
Try to install mysql server at synaptic package manager

---

