---
title: "Ubuntu Server 10.10 Edition"
date: 2010-12-06
forum: Server Platforms
---

### Post by crab238 on 2010-12-06
I just downloaded a 64 bit server. I was trying to install the Joomla on the var/www folder that I fixed; but I wont be granted permission.
Can someone help me as I am new to this .......my aim is to use the machine as a multi site host.

---

### Post by HugoSerrano on 2010-12-06
type the commands with sudo

> $sudo cp /home/$user/joomla-version/* /var/www/

You need to give permissions to apache to read the folder:
> $sudo chown -R www-data:www-data /var/www/

restart apache and access to joomla :-)
> [http://ip.address.joomla.server/](http://ip.address.joomla.server/)this is only one example... based on the information you give.

Anyway, use Drupal instead of Joomla to avoid some security problems.

Regards!

---

### Post by crab238 on 2010-12-06
Hi HuggoSerano, 
 
 
I did the first sudo as adviced, but says "No such file or directory"
 
For your information I have the opt/var/www, so I dont know how the cp/home could connect?
sorry but am a begininer, imagine I uninstalled the windows server opting for Ubuntu...i hope its worthwhile finally. I was trying to follow the video: [http://www.youtube.com/watch?v=tXtumLjUbQA](http://www.youtube.com/watch?v=tXtumLjUbQA) 
 I am stuck at 3:14 of the video where I have to paste the downloaded joomla patch: it won't paste.......
You might have another approach that is more simple.

---

### Post by GDR! on 2010-12-06
crab238,

Try the following:
```

cd /var/www
sudo su

```
[enter your password]
```

wget -O - http://joomlacode.org/gf/download/frsrelease/13105/57238/Joomla_1.5.22-Stable-Full_Package.tar.bz2 | tar jxf -
chown -R www-data:www-data *
exit

```

---

### Post by crab238 on 2010-12-06
Thanx GDR & HugoSerrano. 
 
Skipped thru those hurdles...

---

### Post by crab238 on 2010-12-07
Guys,
 
I did the installation all nice and good, but cannot see the preview of the created page on local host.what went wrong?
 
What kind of dettings do I need to make my server able to host as many web sites as possible? Do I have to fix more www folders? can you help out on this issue too?
 
 
thanks for telling me about Drupal....I read its good in term of architecture, will try it out .

---

### Post by James78 on 2010-12-07
Anything helpful appearing in your logs (/var/log/apache2/error.log)? Do you have PHP/MySQL installed?
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by crab238 on 2010-12-07
@ James78, yes I have Mysql & PHP5 installed so also Apache2.
I was able to finish the installation. but could not preview the site. 
It has another server installed ..I think SAMBA rather than XAMPP, but I presume its the same?

---

### Post by James78 on 2010-12-07
Samba is basically a program to allow you to share non-Windows OS's with Windows by emulating Windows file shares (still useful for file sharing in general however, as you can still use Linux to browse the shares).

Their description of it:
"Samba is software that can be run on a platform other than Microsoft Windows, for example, UNIX, Linux, IBM System 390, OpenVMS, and other operating systems. Samba uses the TCP/IP protocol that is installed on the host server. When correctly configured, it allows that host to interact with a Microsoft Windows client or server as if it is a Windows file and print server."

Anyways, did you see anything interesting/useful/bad in your logs?

---

### Post by crab238 on 2010-12-08
@ james.
 
*Talking of interesting/useful/bad in my logs........I dont think I am the one to judge that since am new to Ubuntu server; It's all like  Greek to me.*
 
*So if you have any trick to help me get my job done ...spill it.*

---

### Post by James78 on 2010-12-08
> **crab238 said:**
> @ james.
 
*Talking of interesting/useful/bad in my logs........I dont think I am the one to judge that since am new to Ubuntu server; It's all like  Greek to me.*
 
*So if you have any trick to help me get my job done ...spill it.*
Please post your error log at /var/log/apache2/error.log, there may be something that points to the problem. ;)

---

### Post by GDR! on 2010-12-08
Are you sure you have started all services?

```

sudo /etc/init.d/apache2 start
sudo /etc/init.d/mysqld start

```

If you did, paste the error you see in browser (screenshot will be good)

---

### Post by crab238 on 2010-12-08
@ James : error Log
 
[FONT=Tahoma][Thu Dec 02 21:45:17 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9 with Suhosin-Patch configured -- resuming normal operations
[Fri Dec 03 00:07:35 2010] [notice] caught SIGTERM, shutting down
[Fri Dec 03 00:10:31 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9 with Suhosin-Patch configured -- resuming normal operations
[Fri Dec 03 00:39:16 2010] [notice] caught SIGTERM, shutting down
[Fri Dec 03 00:40:14 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9 with Suhosin-Patch configured -- resuming normal operations
[Fri Dec 03 01:08:07 2010] [notice] caught SIGTERM, shutting down
[Fri Dec 03 01:08:08 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Fri Dec 03 01:08:11 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
[Fri Dec 03 01:08:11 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Fri Dec 03 01:09:18 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
[Fri Dec 03 01:09:18 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Fri Dec 03 01:24:03 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Fri Dec 03 01:24:06 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Fri Dec 03 01:39:07 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Fri Dec 03 01:39:15 2010] [error] [client 127.0.0.1] File does not exist: /var/www/xampp
[Fri Dec 03 01:46:55 2010] [notice] caught SIGTERM, shutting down
[Sun Dec 05 11:55:57 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Sun Dec 05 12:19:51 2010] [notice] caught SIGTERM, shutting down
[Sun Dec 05 12:22:53 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Sun Dec 05 12:23:30 2010] [notice] caught SIGTERM, shutting down
[Sun Dec 05 12:28:20 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Sun Dec 05 22:50:04 2010] [notice] caught SIGTERM, shutting down
[Sun Dec 05 22:51:05 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Sun Dec 05 23:08:11 2010] [error] [client ::1] File does not exist: /var/www/favicon.ico
[Mon Dec 06 00:00:41 2010] [notice] caught SIGTERM, shutting down
[Mon Dec 06 00:02:43 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Mon Dec 06 01:10:11 2010] [notice] caught SIGTERM, shutting down
[Mon Dec 06 07:44:38 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Mon Dec 06 21:45:53 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Mon Dec 06 21:46:00 2010] [error] [client 127.0.0.1] File does not exist: /var/www/animalfarmer
[Mon Dec 06 21:52:00 2010] [error] [client 127.0.0.1] File does not exist: /var/www/animalfarmer
[Mon Dec 06 21:52:03 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Mon Dec 06 21:54:00 2010] [notice] caught SIGTERM, shutting down
[Wed Dec 08 08:48:13 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Wed Dec 08 09:08:14 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
[Wed Dec 08 09:08:14 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Wed Dec 08 09:42:17 2010] [notice] caught SIGTERM, shutting down
[Wed Dec 08 14:09:55 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations[/FONT]

---

### Post by crab238 on 2010-12-08
@ GDR
 
These were the results of using the command you recommended;
 
 
[FONT=Tahoma]$ sudo /etc/init.d/apache2 start 
 * Starting web server apache2         apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
httpd (pid 1332) already running


sudo /etc/init.d/mysql start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql start[/FONT]

---

### Post by James78 on 2010-12-08
> **crab238 said:**
> @ GDR
 
These were the results of using the command you recommended;
 
 
[FONT=Tahoma]$ sudo /etc/init.d/apache2 start 
** * Starting web server apache2         apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName**
httpd (pid 1332) already running


sudo /etc/init.d/mysql start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql start[/FONT]
Check your /etc/hosts file, in it you'll most likely see something like:
"127.0.1.1      localhost"

Change it to
"127.0.0.1 localhost"

If you don't see something that says exactly that, and don't know how to remedy it (just change 127.0.1.1 to 127.0.0.1), then just post your hosts file in here, and I'll whip up the correct one for you. Also, next time you post logs, code, etc, could you put them in CODE tags? ;)

(The above will fix the "Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName")

For the permissions issue... Can you post the output of "sudo ls -l /var" and "sudo ls -l /var/www"?

Oh, and on the first page where you said you didn't have permission, could you be a little more specific? Like, you can't extract Joomla to the folder because you get an access denied message, Apache gives you a 403 forbidden error, etc.

---

### Post by crab238 on 2010-12-08
@ James78
 
[FONT=Tahoma]The first command you gave me :[/FONT]
[FONT=Tahoma]sudo /etc/hosts
[sudo] password for admin: 
sudo: /etc/hosts: command not found[/FONT]
[FONT=Tahoma][/FONT] 
[FONT=Tahoma]The second command: [/FONT]
[FONT=Tahoma][FONT=Tahoma]sudo ls -l/var
ls: invalid option -- '/'
Try `ls --help' for more information.[/FONT]
[FONT=Tahoma]It appears that nothing is working or It's something am doing wrong.[/FONT]
[FONT=Tahoma]I also posted the error file can you have a look? [/FONT]
[FONT=Tahoma]Are you guys sure this is simpler than Windows Server?[/FONT]
[/FONT]

---

### Post by James78 on 2010-12-08
> **crab238 said:**
> @ James78
 
[FONT=Tahoma]The first command you gave me :[/FONT]
[FONT=Tahoma]sudo /etc/hosts
[sudo] password for admin: 
sudo: /etc/hosts: command not found[/FONT]
[FONT=Tahoma][/FONT] 
[FONT=Tahoma]The second command: [/FONT]
[FONT=Tahoma][FONT=Tahoma]sudo ls -l/var
ls: invalid option -- '/'
Try `ls --help' for more information.[/FONT]
[FONT=Tahoma]It appears that nothing is working or It's something am doing wrong.[/FONT]
[FONT=Tahoma]I also posted the error file can you have a look? [/FONT]
[FONT=Tahoma]Are you guys sure this is simpler than Windows Server?[/FONT]
[/FONT]
The first command to run would be "cat /etc/hosts", and the second ones, make sure you have a space between the options and the file path. "sudo ls -l /var"

Simpler? Maybe not. But what I can tell you, is that it's better.

---

### Post by HugoSerrano on 2010-12-09
> **James78 said:**
> The first command to run would be "sudo cat /etc/hosts", and the second ones, make sure you have a space between the options and the file path. "sudo ls -l /var"

Simpler? Maybe not. But what I can tell you, is that it's better.


And yes, it's simpler. The problem here is that you still learning to use Linux. With time you will see that you made the right choice. :-)

James78 pointed a file. /etc/hosts it's the location of the file.
**/etc/ ** its the directory, as c:/system/ in windows
**hosts** is the file, as c:/system/hosts.txt in windows.

the command you typed **$sudo /etc/hosts** don't work because it's a simple text file.

You need to use **cat**, that it's a reading program.

Some useful commands:
$cat <file> -> print the file to the console
$nano <file> -> file editor

There's other tools to do that, but this may be the best for you now.

Now, you are trying to connect to localhost. Localhost means the machine where you are. So if your trying to connect to your server, from a different machine, you need to insert the server IP Address.

In the server type:
$ifconfig eth0
You will get some information. The one you need if the numbers after **inet addr:** 
Now that you know where the information is, you can make a filter to see that without the other information. You can use **| grep "inet addr:"** so the final command should look like this:

> $ifconfig eth0 | grep "inet addr:"

You will get something like:
inet addr:**192.168.1.100**  Bcast:10.0.1.255  Mask:255.255.255.0

Now you go to your Desktop and in the browser you can type:
[http://192.168.1.100/](http://192.168.1.100/)

Regards!

---

### Post by James78 on 2010-12-09
> **HugoSerrano said:**
> And yes, it's simpler. The problem here is that you still learning to use Linux. With time you will see that you made the right choice. :-)
I'd have to agree with that. ;) Definitely the right choice. :)

---

