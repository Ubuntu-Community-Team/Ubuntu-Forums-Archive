---
title: "Second Webserver User Site"
date: 2014-04-28
forum: Server Platforms
---

### Post by Jordan_Hickin on 2014-04-28
Hi guys

I have added a user to my webserver.

I have uploaded the index.html page to /var/www/webuser1

However when i type 192.168.0.7/webuser1 into my browser it can't find the page.

Hope you can help :)

---

### Post by volkswagner on 2014-04-28
Is that directory readable for Apache2?

What are the permissions?
```
ls -l /var/www/webuser1
```

---

### Post by Jordan_Hickin on 2014-04-29
> **volkswagner said:**
> Is that directory readable for Apache2?

What are the permissions?
```
ls -l /var/www/webuser1
```


I have done what you said and got this:
```
total 80
-rw-r--r-- 1 webuser1 webuser1 78416 Apr 28 20:42 index.html


```

???

---

### Post by nerdtron on 2014-04-29
What is the output of:
```
ls -l /var/www
```

And why is the user named webuser1? Isn't it that all files on the /var/www/ folder should be owned by www-data?

---

### Post by Lars Noodén on 2014-04-29
<digression>

> **nerdtron said:**
>  owned by www-data?

Files served by the web server only need to be readable by www-data.  o=rx for directories and o=r for files is enough.  Write access by www-data should not be enabled because it is intended to provide an unprivileged user for web server.  Giving it write access defeats that.  

</digression>

---

### Post by Jordan_Hickin on 2014-04-29
The results are as follows:

```

[B]total 20
drwxr-xr-x 2 root     root  4096 Apr 29 10:51 html
-rw-r--r-- 1 root     root 11479 Apr 28 21:48 index.html
drwxr-xr-x 3 webuser1 root  4096 Apr 28 21:47 webuser1
[/B]
```I am unsure of what this means.

---

### Post by SeijiSensei on 2014-04-29
Which Ubuntu version are you using?  If you have 14.04, the web site directory is now /var/www/html, not just /var/www.

Also take a look at /var/log/apache2/error.log to see if there are more details.  The logs should be your first source of information.

---

### Post by Jordan_Hickin on 2014-04-29
> **SeijiSensei said:**
> Which Ubuntu version are you using?  If you have 14.04, the web site directory is now /var/www/html, not just /var/www.

Also take a look at /var/log/apache2/error.log to see if there are more details.  The logs should be your first source of information.

I am using 14.04.. And i have my own website running. But i have added a web user. who should be able to place there website on the web server. 

my website at 192.168.0.7 is working as i want. How do i get the web users website up. Or can he only save files on it?

aka I want the additional web user to be able to upload his own website onto the server.

I will check the log

I found this:

[Mon Apr 28 19:25:29.052197 2014] [mpm_prefork:notice] [pid 1021] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4 configured -- resuming normal operations
[Mon Apr 28 19:25:29.052373 2014] [core:notice] [pid 1021] AH00094: Command line: '/usr/sbin/apache2'
[Mon Apr 28 23:31:32.122563 2014] [mpm_prefork:notice] [pid 1021] AH00169: caught SIGTERM, shutting down
[Mon Apr 28 23:32:35.194863 2014] [mpm_prefork:notice] [pid 1066] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4 configured -- resuming normal operations
[Mon Apr 28 23:32:35.207590 2014] [core:notice] [pid 1066] AH00094: Command line: '/usr/sbin/apache2'
[Mon Apr 28 23:33:03.964186 2014] [mpm_prefork:notice] [pid 1066] AH00169: caught SIGTERM, shutting down
[Tue Apr 29 10:42:39.151393 2014] [mpm_prefork:notice] [pid 1067] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4 configured -- resuming normal operations
[Tue Apr 29 10:42:39.164240 2014] [core:notice] [pid 1067] AH00094: Command line: '/usr/sbin/apache2'

I have no idea what that means.

All i want is the webuser to be able to display his own website from the server.

---

### Post by SeijiSensei on 2014-04-29
Well, did you remove the extraneous <Directory /> stanza?

All those entries just log that apache was stopped and restarted at three separate times.  Most Unix-style logs are pretty verbose, but if you just think about the entries for a few moments they should be reasonably clear.

```
[Mon Apr 28 19:25:29.052197 2014] [mpm_prefork:notice] [pid 1021] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4 configured -- resuming normal operations
[Mon Apr 28 19:25:29.052373 2014] [core:notice] [pid 1021] AH00094: Command line: '/usr/sbin/apache2'
[Mon Apr 28 23:31:32.122563 2014] [mpm_prefork:notice] [pid 1021] AH00169: caught SIGTERM, shutting down

```

The first line says that Apache was started at 19:25 on April 28th and is "resuming normal operations".  It was started with the command "/usr/sbin/apache2".  Then at 23:31 on the same day, Apache was shut down using the "[SIGTERM]("http://www.gnu.org/software/libc/manual/html_node/Termination-Signals.html")" signal.  This stops a process gracefully telling it to shut down any existing operations as soon as possible; "SIGKILL" is the less-graceful but sometimes more effective alternative.  If you used "service apache2 start|stop|restart" at these times, you're seeing their effects in the log.

---

### Post by Jordan_Hickin on 2014-04-29
> **SeijiSensei said:**
> Well, did you remove the extraneous <Directory /> stanza?

All those entries just log that apache was stopped and restarted at three separate times.  Most Unix-style logs are pretty verbose, but if you just think about the entries for a few moments they should be reasonably clear.

```
[Mon Apr 28 19:25:29.052197 2014] [mpm_prefork:notice] [pid 1021] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4 configured -- resuming normal operations
[Mon Apr 28 19:25:29.052373 2014] [core:notice] [pid 1021] AH00094: Command line: '/usr/sbin/apache2'
[Mon Apr 28 23:31:32.122563 2014] [mpm_prefork:notice] [pid 1021] AH00169: caught SIGTERM, shutting down

```

The first line says that Apache was started at 19:25 on April 28th and is "resuming normal operations".  It was started with the command "/usr/sbin/apache2".  Then at 23:31 on the same day, Apache was shut down using the "[SIGTERM]("http://www.gnu.org/software/libc/manual/html_node/Termination-Signals.html")" signal.  This stops a process gracefully telling it to shut down any existing operations as soon as possible; "SIGKILL" is the less-graceful but sometimes more effective alternative.  If you used "service apache2 start|stop|restart" at these times, you're seeing their effects in the log.

Thankyou for explaing that. it makes perfect sense.

As for the stanza i am confused. i was following this:

> 
	The basic ftp server is now up and running, and you should be able  to log into it with your non-root account. But we still need to set up  an account that will allow someone to upload their web pages without  having access to any other parts of the system.
 	First, switch to the /etc directory by typing cd /etc. We need to  edit the file called shells and add a new line that says /bin/false to  the file. Then, when we set up a new user account for our web user,  we’ll configure their account so that /bin/false is their command shell.  Because there’s no such shell, they won’t be able to log in with  telnet.
 	Type vi shells to edit the file. Use the cursor keys (h,j,k,l) to  move the cursor to the start of a new line, then press i to enter insert  mode. Press Return to insert a new line, and add /bin/false as a new  line in the file. Press Esc to leave insert mode, save the file with :w  then exit vi with :q and you’re done.
 	Each user has a home directory which contains their various files.  It’s like My Documents in Windows and normally it resides in the /home  directory. For web users, rather than setting their home directory to be  somewhere within /home we’ll put it under /var/www, which is the root  of the web server.
 	Let’s make an account for a user called webuser1 with a password of  flintstone.  These are the steps that you need to do for each web user  account you want to create:
 	cd /var/www
	mkdir webuser1
	useradd webuser1 –p xxxx –d /var/www/webuser1 –s /bin/false
	chown webuser1 webuser1
	passwd webuser1 and, when asked, choose flintstone as the password.
 	Note that xxxx above is your root password, not the one that you want to assign for the webuser1 account.
 	Also note the chown command which changes the ownership of the  webuser1 directory from root (which created it) to webuser1. If you  don’t do this, webuser1 won’t be able to upload files.
 	Just to make sure that everything is working, verify that you can’t telnet to the server using the webuser1 account.
 	Now create a simple index.html file and use ftp to upload it, using the webuser1/flintstone account.  Then surf to [http://192.168.1.10/webuser1](http://192.168.1.10/webuser1) from any machine on your LAN and you should see the uploaded page.



I did exactly as it asks.. but it isn't working....

---

### Post by volkswagner on 2014-04-29
> **SeijiSensei said:**
> Which Ubuntu version are you using?  If you have 14.04, the web site directory is now /var/www/html, not just /var/www.

Also take a look at /var/log/apache2/error.log to see if there are more details.  The logs should be your first source of information.

Don't skip over what SeijiSensei has mentioned.

I did not realize this was a change in Ubuntu 14.04, this makes perfect sense why you don't see the new site.

Please post contents of /etc/apache2/sites-enabled/default

---

### Post by Jordan_Hickin on 2014-04-29
There is nothing in that :/

---

### Post by Jordan_Hickin on 2014-04-29
> **volkswagner said:**
> Don't skip over what SeijiSensei has mentioned.

I did not realize this was a change in Ubuntu 14.04, this makes perfect sense why you don't see the new site.

Please post contents of /etc/apache2/sites-enabled/default

I didn't skip it.

My website found under /var/www/html is working fine.

What i can't get is the webusers website. I can't even work out how to get to them on the browser... 192.168.0.7/webuser1 doesn't work :/

---

### Post by SeijiSensei on 2014-04-29
> **SeijiSensei said:**
> Well, did you remove the extraneous <Directory /> stanza?

Sorry, I got confused between two different requests for advice about Apache this morning.

```
total 20
drwxr-xr-x 2 root     root  4096 Apr 29 10:51 html
-rw-r--r-- 1 root     root 11479 Apr 28 21:48 index.html
drwxr-xr-x 3 webuser1 root  4096 Apr 28 21:47 webuser1

```

So this other website's files appear to be stored in /var/www/webuser1?  If you want to reach them by [http://server/webuser1](http://server/webuser1), that directory needs to be below /var/www/html.  That's the root of the default website, so any other directories off that root need to be in the /var/www/html directory.

---

### Post by Jordan_Hickin on 2014-04-29
> **SeijiSensei said:**
> Sorry, I got confused between two different requests for advice about Apache this morning.

```
total 20
drwxr-xr-x 2 root     root  4096 Apr 29 10:51 html
-rw-r--r-- 1 root     root 11479 Apr 28 21:48 index.html
drwxr-xr-x 3 webuser1 root  4096 Apr 28 21:47 webuser1

```

So this other website's files appear to be stored in /var/www/webuser1?  If you want to reach them by [http://server/webuser1](http://server/webuser1), that directory needs to be below /var/www/html.  That's the root of the default website, so any other directories off that root need to be in the /var/www/html directory.

Thankyou so much.. i got it now :) so all websites will need to be under the html folder... each seperated by there own directory in the html directory.

I am so thankful.. Now time to work on my program for uploading files easily. Thanks again :))))))

---

### Post by SeijiSensei on 2014-04-29
That's only if you don't implement "[name-based virtual hosts]("https://httpd.apache.org/docs/2.2/vhosts/name-based.html")."  Then you can define any location you want for the website files as long as they are readable by the www-data user.  See this [guide to Apache on Ubuntu]("https://help.ubuntu.com/12.04/serverguide/httpd.html").

---

