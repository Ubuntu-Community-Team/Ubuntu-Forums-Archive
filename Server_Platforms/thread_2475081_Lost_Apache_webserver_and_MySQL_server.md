---
title: "Lost Apache webserver and MySQL server"
date: 2022-05-16
forum: Server Platforms
---

### Post by eduardoeltortuga2 on 2022-05-16
I. I have lost Apache Webserver and MySQL Database Server. They won't start. Don't know what could have happened.
Local server. 
Ubuntu 20.04.4
Webmin 1.991
Virtualmin7.04

I gathered some info from the logs:
 1.Job for apache2.service failed because the control process exited with error code.
    See "systemctl status apache2.service" and "journalctl -xe" for details.

 
When I try to restart Apache with command line I get this message.
 Restarting apache2 (via systemctl): apache2.serviceJob for apache2.service failed because the control process exited with error code.
 See "systemctl status apache2.service" and "journalctl -xe" for details.

This is the info I get for MySQL
 Error!  MySQL is not running on your system - database list could not be retrieved.
/usr/bin/mysqlshow: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Image of server status on Webmin.
[IMG]https://s3.us-west-1.amazonaws.com/mymedia.bucket/Lost+Servers.PNG[/IMG]

I found this help online using
apache2ctl configtest

edword@ubuntu:~$ cd /etc/apache2
edword@ubuntu:/etc/apache2$ apache2ctl configtest
AH00526: Syntax error on line 2 of /etc/apache2/sites-enabled/*?*.com.conf:
SuexecUserGroup configured, but suEXEC is disabled: Invalid owner or file mode for /usr/lib/apache2/suexec
Action 'configtest' failed.
The Apache error log may have more information.


Using this command "systemctl status apache2.service"

May 16 07:12:19 ubuntu systemd[1]: Starting The Apache HTTP Server...
May 16 07:12:19 ubuntu apachectl[32851]: AH00526: Syntax error on line 81 of /etc/apache2/sites-enabled/*?*.com.conf:
May 16 07:12:19 ubuntu apachectl[32851]: Invalid command 'php_admin_value', perhaps misspelled or defined by a module not included in >
May 16 07:12:19 ubuntu apachectl[32840]: Action 'start' failed.
May 16 07:12:19 ubuntu apachectl[32840]: The Apache error log may have more information.
May 16 07:12:19 ubuntu systemd[1]: apache2.service: Control process exited, code=exited, status=1/FAILURE
May 16 07:12:19 ubuntu systemd[1]: apache2.service: Failed with result 'exit-code'.
May 16 07:12:19 ubuntu systemd[1]: Failed to start The Apache HTTP Server.
lines 1-14/14 (END)


[SIZE=3][SIZE=2]II. My SQL server info:
     Error!  MySQL is not running on your system - database list could not be retrieved.

    MySQL error message
    The full MySQL error message was : DBI connect failed : Can't connect  to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

When I try to start MySQL server:
/usr/bin/mysqlshow: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)[/SIZE]
[/SIZE]




I could easily uninstall this particular website and reinstall if that would fix the issue.

Thank you for any help
Eddie

---

### Post by LHammonds on 2022-05-16
```
ls -l /etc/apache2/sites-enabled/
```
Is there an actual *?*.com.conf file sitting in there?  I bet there is an empty file in there as a result of a messed up command-line that was issued.

All entries in the "sites-enabled" folder should just be symbolic links to files in the "sites-available" folder.

The owner/group on my config files in the "sites-available" folder are root:root with permissions of 0600.

You need to resolve the config file issues BEFORE you can start the Apache web service.  In other words, you need to see "**Syntax OK**" when issuing the command below.

I think "sudo" is required to run this command in order to get accurate results:
```
$ sudo apache2ctl configtest
Syntax OK
```

Once you get Apache squared away, then take a look at your database service.

Also, was this site running before and stopped working without anyone accessing and changing things via console/SSH?   If it broke without admin interaction (and the file system is not full) then you might have want to see if you've been hacked.  If this is a new setup, then we are just looking at setup/config issues.

LHammonds

---

### Post by eduardoeltortuga2 on 2022-05-16
"Is there an actual *?*.com.conf file sitting in there?  I bet there is  an empty file in there as a result of a messed up command-line that was  issued."
No, sorry. I just edited it out.
Here is the actual line:
May 16 07:12:19 ubuntu apachectl[32851]: AH00526: Syntax error on line 81 of /etc/apache2/sites-enabled/acebookfay.com.conf:

It was working. Maybe I was hacked. I might have done an update, but i don't remember. 
If I delete the problem website will it solve the issue? I can always reinstall.

Thanks for the quick response!
Eddie

---

### Post by LHammonds on 2022-05-17
> **eduardoeltortuga2 said:**
> Syntax error on line 81 of /etc/apache2/sites-enabled/acebookfay.com.conf:
This means your configuration file "acebookfay.com.conf" has a syntax error.  It says it is on line 81 which may or may not be true...sometimes syntax errors can confuse where the actual syntax issue is located but look there first.

The below command will show when that file was last modified and who has what access to that file:
```
ls -l /etc/apache2/sites-available/
```

LHammonds

---

### Post by eduardoeltortuga2 on 2022-05-18
Thank you my friend. You are always a big help!
Eddie

---

