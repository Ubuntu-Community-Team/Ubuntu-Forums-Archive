---
title: "Strange problem with Apache2"
date: 2009-12-03
forum: Server Platforms
---

### Post by tapas_mishra on 2009-12-03
I am having a strange problem with Apache2 I have apache2 and phpmyadmin installed
in apache2 is denying me to access / of a file but when I do uninstall apache2
by ```

aptitude remove apache2

```
 everything is working fine but phpmyadmin stops working
if I install apache2
```

aptitude install apache2

```
then again I have the same problem but phpmyadmin starts working here

---

### Post by cdenley on 2009-12-03
The package "apache2" doesn't provide anything important. It is basically just a meta-package. Removing it shouldn't fix or create any problems. If you want help with your permissions problem, you will need to give more details.

---

### Post by munky99999 on 2009-12-03
> I am having a strange problem with Apache2 I have apache2 and phpmyadmin installed
So you have php and mysql running also.

> in apache2 is denying me to access / of a file but when I do uninstall apache2
by 
time for chmod. Not uninstall.

> everything is working fine but phpmyadmin stops working
If it stops working. It's not working fine.

chmod whatever you dont have access to. That should fix the problem I suspect.

---

### Post by Hypnoz on 2009-12-03
Is the document root /var/www?
Is the file you want in /var/www?
Can you ls -l /var/www/filename and post the results?
Can you "echo Test >> /var/www/index.html" and see the results in a web browser?
Check your /etc/apache2/sites-enabled/000-default
Does everything look ok in that file. Are you trying to get a directory index by removing the index.html file or just access a file in that directory through the web browser?

---

### Post by tapas_mishra on 2009-12-04
I checked the log and this error was repeatedly there ```

[client 127.0.0.1] (13)Permission denied: /home/tapas/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable



[Fri Dec 04 01:28:59 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.2 with Suhosin-Patch mod_ruby/1.2.6 Ruby/1.8.7(2008-08-11) configured -- resuming normal operations

```

What is noticeable  .htaccess is not present since this is a small PHP project which some one is making to learn PHP.So absolute basic questions.


> **cdenley said:**
> The package "apache2" doesn't provide anything important. It is basically just a meta-package. Removing it shouldn't fix or create any problems. If you want help with your permissions problem, you will need to give more details.
What details should I post here  let me know I will post it here.


> **munky99999 said:**
> So you have php and mysql running also.


time for chmod. Not uninstall.


If it stops working. It's not working fine.

chmod whatever you dont have access to. That should fix the problem I suspect.
Yes I have PHP and MySql running also ,hmmm well where exactly do you suggest I need to go for chmod is it the files in /var/www or the the sites I am having in home directories of users.

> **Hypnoz said:**
> Is the document root /var/www?
Is the file you want in /var/www?
Can you ls -l /var/www/filename and post the results?
Can you "echo Test >> /var/www/index.html" and see the results in a web browser?
Check your /etc/apache2/sites-enabled/000-default
Does everything look ok in that file. Are you trying to get a directory index by removing the index.html file or just access a file in that directory through the web browser?

Well the index.html page you suggested is default page which is working when I do [http://localhost](http://localhost) then I get a message it works Document root is /var/www 
ls -l 
```

root@tapas-laptop:/var/www# ls -l
total 44
drwxr-xr-x 2 root root 4096 2009-12-04 01:18 ab
-rw-r--r-- 1 root root   27 2009-11-24 13:24 hello.html
-rw-r--r-- 1 root root   45 2009-11-09 00:43 index.html
drwxr-xr-x 2 root root 4096 2009-12-04 01:18 newsite
drwxr-xr-x 7 root root 4096 2009-12-03 22:52 project_1
drwxr-xr-x 2 root root 4096 2009-12-04 01:02 ubuntu
drwxr-xr-x 2 root root 4096 2009-11-24 13:20 web admin

```I have tried both If I am accessing the file by browser like open hello.html in firefox then it is showing correctly but if I do it [http://localhost/hello.html](http://localhost/hello.html)
and assuming that hello.html is in Document Root then I am not able to see and get a message directory listing / denied I googled  this and found this is a common problem when you set Apache 
[http://httpd.apache.org/docs/1.3/misc/FAQ.html#forbidden](http://httpd.apache.org/docs/1.3/misc/FAQ.html#forbidden)
but when I check httpd.conf it is blank I do not wether this is a usual case with Apache2 since I have used Apache in Fedora not apache2 and I am not familiar if the file configuration is different in Ubuntu which I think should not be the case.

---

### Post by Lars Noodén on 2009-12-04
> **tapas_mishra said:**
>  then I am not able to see and get a message directory listing / denied I googled  this and found this is a common problem when you set Apache 


Does the relevant Options directive have Indexes?
[http://httpd.apache.org/docs/2.2/mod/core.html#options](http://httpd.apache.org/docs/2.2/mod/core.html#options)

Do you have at least one DirectoryIndex specified? 
 e.g. index.html index.php 
[http://httpd.apache.org/docs/2.2/mod/mod_dir.html#directoryindex](http://httpd.apache.org/docs/2.2/mod/mod_dir.html#directoryindex)

---

### Post by cdenley on 2009-12-04
> **tapas_mishra said:**
> I checked the log and this error was repeatedly there ```

[client 127.0.0.1] (13)Permission denied: /home/tapas/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable



[Fri Dec 04 01:28:59 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.2 with Suhosin-Patch mod_ruby/1.2.6 Ruby/1.8.7(2008-08-11) configured -- resuming normal operations

```

What is noticeable  .htaccess is not present since this is a small PHP project which some one is making to learn PHP.So absolute basic questions.


```

ls -la /home/tapas

```

---

### Post by sanjuro on 2009-12-04
I am getting the same problem since upgrading to Karmic. The exactly same setup works fine in Hardy and Jaunty. I have a virtual host for /home/<user>/project. You notice that the message reports the permission problem for /home/<user> folder, not the folder actually in host config. I then changed the host config to point to something one level deeper, the error is still the same. As an experiment, I changed the permission of the entire folder to 0777, with the same result.

The default host runs fine.

[EDIT] Apparently this is [not a new problem]("http://newyork.ubuntuforums.org/showthread.php?t=1307475").

---

### Post by cdenley on 2009-12-04
If you're getting permissions problems with apache, post this output, replacing "/var/www/index.html" with the path to the file apache fails to access.
```

webfile="/var/www/index.html"
ls -l "$webfile"
while [ "$webfile" != "/" ]
do
    webfile=`dirname "$webfile"`
    ls -ld "$webfile"
done

```

---

### Post by The Zezima of &#370;buntu on 2009-12-04
I was having similar problems yesterday after installing apache2, mysql, and php. And after 3 or 4 hours of searching for a solution I figured I'd just install Xampp. Which fixed everything and I have a nice interface to work with the mysql database.

Before you install Xampp you'll want to get rid of the apache, mysql, and php you already have installed. Xampp comes with all of those and changes your www webroot folder to "opt\LAMPP\htdocs\".

---

### Post by sanjuro on 2009-12-06
@cdenley, thank you for your reply.

> -rwxr-xr-x 1 sanjuro sanjuro 19 2009-12-07 09:38 /home/sanjuro/project/vhostdir/phpinfo.php
drwxr-xr-x 2 sanjuro sanjuro 4096 2009-12-07 09:38 /home/sanjuro/project/vhostdir
drwxr-xr-x 8 sanjuro sanjuro 4096 2009-12-07 09:50 /home/sanjuro/project
drwx------ 56 sanjuro sanjuro 16384 2009-12-07 09:30 /home/sanjuro
drwxr-xr-x 4 root root 4096 2009-11-24 23:05 /home
drwxr-xr-x 23 root root 4096 2009-12-07 09:30 /

However, I don't think you understand the problem. Apache shows a '403 Forbidden' for anything under the host, not any specific file. The error log shows
> [Mon Dec 07 09:48:35 2009] [crit] [client 127.0.0.1] (13)Permission denied: /home/sanjuro/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable
Note that the error is not for the folder actually in the host configuration, it's the user home folder.

---

### Post by tapas_mishra on 2009-12-07
> **cdenley said:**
> If you're getting permissions problems with apache, post this output, replacing "/var/www/index.html" with the path to the file apache fails to access.
```

webfile="/var/www/index.html"
ls -l "$webfile"
while [ "$webfile" != "/" ]
do
    webfile=`dirname "$webfile"`
    ls -ld "$webfile"
done

```
Output of the script
tapas@tapas-laptop:~/$ ./index.html 
total 64
drwxrwxrwx 7 tapas tapas  4096 2009-11-04 18:18 admin
-rwxrwxrwx 1 tapas tapas  3241 2009-11-03 21:29 admin.php
drwxrwxrwx 2 tapas tapas 16384 2009-11-04 12:09 images
-rwxr-xr-x 1 tapas tapas   149 2009-12-07 13:29 index.html
drwxrwxrwx 2 tapas tapas  4096 2009-11-04 12:09 javascript
-rwxrwxrwx 1 tapas tapas  2398 2009-11-03 16:28 login.php
drwxrwxrwx 3 tapas tapas  4096 2009-11-02 15:52 html_pages
-rwxrwxrwx 1 tapas tapas  1132 2009-10-27 22:14 searchgo.gif
drwxrwxrwx 3 tapas tapas  4096 2009-11-04 18:56 scripts
drwxr-xr-x 5 tapas tapas 4096 2009-12-07 11:33 /home/tapas/L
drwx------ 63 tapas tapas 8192 2009-12-07 13:29 /home/tapas
drwxr-xr-x 6 root root 4096 2009-11-25 22:25 /home
drwxr-xr-x 25 root root 4096 2009-12-07 13:06 /

---

### Post by cdenley on 2009-12-07
> **sanjuro said:**
> However, I don't think you understand the problem. Apache shows a '403 Forbidden' for anything under the host, not any specific file. The error log shows

Note that the error is not for the folder actually in the host configuration, it's the user home folder.

It's failing to read a file (/home/sanjuro/.htaccess), so tell us what the permissions are by posting the output I requested!

---

### Post by cdenley on 2009-12-07
> **tapas_mishra said:**
> Output of the script
tapas@tapas-laptop:~/$ ./index.html 
total 64
drwxrwxrwx 7 tapas tapas  4096 2009-11-04 18:18 admin
-rwxrwxrwx 1 tapas tapas  3241 2009-11-03 21:29 admin.php
drwxrwxrwx 2 tapas tapas 16384 2009-11-04 12:09 images
-rwxr-xr-x 1 tapas tapas   149 2009-12-07 13:29 index.html
drwxrwxrwx 2 tapas tapas  4096 2009-11-04 12:09 javascript
-rwxrwxrwx 1 tapas tapas  2398 2009-11-03 16:28 login.php
drwxrwxrwx 3 tapas tapas  4096 2009-11-02 15:52 html_pages
-rwxrwxrwx 1 tapas tapas  1132 2009-10-27 22:14 searchgo.gif
drwxrwxrwx 3 tapas tapas  4096 2009-11-04 18:56 scripts
drwxr-xr-x 5 tapas tapas 4096 2009-12-07 11:33 /home/tapas/L
**drwx------ 63 tapas tapas 8192 2009-12-07 13:29 /home/tapas**
drwxr-xr-x 6 root root 4096 2009-11-25 22:25 /home
drwxr-xr-x 25 root root 4096 2009-12-07 13:06 /

There is your problem. The user apache runs as (www-data) has no access permissions to /home/tapas, so it cannot access any files or subdirectories within that directory.
```

sudo chmod a+rx /home/tapas

```

---

### Post by tapas_mishra on 2009-12-07
> **cdenley said:**
> There is your problem. The user apache runs as (www-data) has no access permissions to /home/tapas, so it cannot access any files or subdirectories within that directory.
```

sudo chmod a+rx /home/tapas

```
Oh wow !!! thanks  **It works!!**

---

### Post by tapas_mishra on 2009-12-07
> **Lars Noodén said:**
> Does the relevant Options directive have Indexes?
[http://httpd.apache.org/docs/2.2/mod/core.html#options](http://httpd.apache.org/docs/2.2/mod/core.html#options)

Do you have at least one DirectoryIndex specified? 
 e.g. index.html index.php 
[http://httpd.apache.org/docs/2.2/mod/mod_dir.html#directoryindex](http://httpd.apache.org/docs/2.2/mod/mod_dir.html#directoryindex)
Well thanks for these links Lars seems after a lot of internet blogs some where I found relevant information

---

