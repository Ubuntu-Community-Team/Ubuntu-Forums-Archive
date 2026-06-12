---
title: "does anyone in the world actually access phpmyadmin"
date: 2009-06-05
forum: The Cafe
---

### Post by kapi on 2009-06-05
after four days, numerous threads and endless nights of trying to gain access to phpmyadmin I have come to the conclusion that from a users perspective . . . how can I put this as politely as possible IT SUCKS!

I have installed it six times, had numerous help from others telling me to make sure there is symlinks or make new users within mySQL or reset the password or even just reinstall and make sure certain include files exist in etc/int.d

well I've had it! Sorry this is my rant, I studied software development at uni and have come to the conclusion that it should work straight out of the box not take a ridiculous amount of time to set it up, I have wasted more time than I can afford

Dont use this rubbish, i'll just have to try something else

---

### Post by Celauran on 2009-06-05
I use it every day from six different machines and have never had a single problem. Really haven't a clue why it's giving you such a hard time.

---

### Post by marshall.robert on 2009-06-05
Did you download it from the website of from the Ubuntu repositories?

```
sudo apt-get install phpmyadmin
```

That ensures that it is correctly set up too. With the added advantage of updating automatically.

---

### Post by albinootje on 2009-06-05
> **kapi said:**
>  I have installed it six times, had numerous help from others telling me to make sure there is symlinks or make new users within mySQL or reset the password or even just reinstall and make sure certain include files exist in etc/int.d


What I usually do is the following :

1) Remove /var/www/phpmyadmin symlink
2) Create directory /var/www/phpmyadmin directory
3) Mount it when I need it, as following :
```

sudo mount --bind /usr/share/phpmyadmin /var/www/phpmyadmin

```
4) open the url with the php defined, e.g. :
[http://localhost/phpmyadmin/index.php](http://localhost/phpmyadmin/index.php)
5) After usage : 
```

sudo umount /var/www/phpmyadmin

```

It's important to look at the authentication options that exist, and then configure which one you prefer to use.

And there's also a new project which has a similar name as phpmyadmin, but is a much simpler version.
Can't find it on [http://freshmeat.net](http://freshmeat.net) right now because I don't remember the exact name.

---

### Post by pluckypigeon on 2009-06-05
I ripped my hair out with it as well but when I got it to work it was very useful for me.

I uninstalled it from synaptic and just downloaded it from the site  and placed it in the www directory. If I remember rightly the default username was root and the password was just a blank field.

I don't really remember much more then that.

Hope you sort out your problems.

---

### Post by kapi on 2009-06-05
Hi again celauran, thanks for all your help. No neither have I. My user name is root and then I enter the mySQL password and nothing happens. In mySQL I can login using the root and password but with new added users it won't let me in. Dont know if thats of any significance

---

### Post by ddrichardson on 2009-06-05
Are you referring to the issue on some Ubuntu boxes where Firefox insists on downloading the index.php file rather than executing it? Sorry to make assumptions but you didn't state the problem.

Edit: Ignore that - others type faster than me ;-)

---

### Post by kapi on 2009-06-05
hi DDrichardson, no haven't had that it just seems to be that when I log in or try to that I get no response - not even a sorry mate you've got something wrong

---

### Post by pluckypigeon on 2009-06-05
> **kapi said:**
> Hi again celauran, thanks for all your help. No neither have I. My user name is root and then I enter the mySQL password and nothing happens. In mySQL I can login using the root and password but with new added users it won't let me in. Dont know if thats of any significance

I think phpmyadmin and mysql have different passwords

---

### Post by Celauran on 2009-06-05
> **kapi said:**
> Hi again celauran, thanks for all your help. No neither have I. My user name is root and then I enter the mySQL password and nothing happens. In mySQL I can login using the root and password but with new added users it won't let me in. Dont know if thats of any significance

I've never actually logged into phpmyadmin as root. The first thing I do on a new SQL install is set up my local users. If you've set up new MySQL users and aren't able to login with those, even via console, then that is troubling. Are you able to see the added users in mysql.user?

---

### Post by Celauran on 2009-06-05
> **pluckypigeon said:**
> I think phpmyadmin and mysql have different passwords

No, phpmyadmin is just a front end for MySQL. The users are the same.

---

### Post by albinootje on 2009-06-05
> **kapi said:**
> My user name is root and then I enter the mySQL password and nothing happens. 

I've seen that problem before I think. 
IIRC it worked for me to use the back button, and then forward, hit <enter> again.

And.. use the index.php in the url field.

---

### Post by albinootje on 2009-06-05
> **Celauran said:**
> No, phpmyadmin is just a front end for MySQL. The users are the same.

Yes, but.. that also depends on the authentication method that you use. If you use phpmyadmin with .htaccess as authentication layer, then the username could be different, but that's not the default.

---

### Post by xavierp94 on 2009-06-05
Wow, I love Phpmyadmin. Its works fine with me. ;)

---

### Post by Faceless79 on 2009-06-05
I use phpmyadmin for my web site nearly everyday without fail

---

### Post by kapi on 2009-06-05
OK got into mySQLAdmin and made new user, gave all permissions and then logged out. Tried to log in as new user but denied access, maybe thats related in root it has:

root
    @localhist

but in new user it has

kapi
    @%

---

### Post by Celauran on 2009-06-05
> **kapi said:**
> maybe thats related in root it has:

root
    @localhist

but in new user it has

kapi
    @%

I'm sorry, I don't understand what the above means. Are you able to login as the new user via commandline and not via phpmyadmin? Do you see the new user when you query mysql.user?

---

### Post by kapi on 2009-06-05
no

---

### Post by bodhi.zazen on 2009-06-05
phpmyadmin is in the repos or you can install from "source". Either way it takes me less then 5 minutes to get up and running.

I can not tell what problem you are having with it.

I would be more then happy to help if you would not mind stating the problem or perhaps stating what you have tried or perhaps a link to your other threads.


It the problem that you can not load the phpmyadmin page in your browser ?

If so, what url are you using ? 

Is the problem that you can not log in ? are you using the  correct user name and password ? Are you blocking cookies ?

---

### Post by kapi on 2009-06-08
the problem is this:

the login screen appears via [http://localhost/phpmyadmin](http://localhost/phpmyadmin) 
but when I input the user name which is 'root' and the password which is the same as the password for mySQLAdmin then nothing happens. the screen just seems to refresh and nothing else.

I have also tried making a new mySQL account called kapi but when I try to log in to mySQLAdmin I get password error, strange!

maybe it's mySQL thats the problem

kapi

---

### Post by bodhi.zazen on 2009-06-08
I believe the password for the log in screen is root's log in password.

Try first logging using the same username and log in you would to log into the server (ie your log in name).

If that fails, set a root password (not a mysql password) and log in the web server with root and root's log in password.

---

### Post by Celauran on 2009-06-08
> **kapi said:**
> 
I have also tried making a new mySQL account called kapi but when I try to log in to mySQLAdmin I get password error, strange!


```
mysql -u kapi -p
```
Does this work?

> I believe the password for the log in screen is root's log in password.
It's the password you specify when you configure MySQL and is unrelated to Linux's root account.

If necessary, the MySQL root password can be reset thus:

```
mysqladmin -u root -p password new_password_here
```

---

### Post by kapi on 2009-06-08
Hi again,

right, when I enter the commands to alter the password I can create the account ok but when I try to get access it doesn't seem to work. 

What I mean is when I try using mySQLAdmin and create a new user and password and try to access it via the terminal or the gui for mySQLadmin I get error

kapi@craig-laptop:~$ mysql -u kapi -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'kapi'@'localhost' (using password: YES)

---

### Post by billgoldberg on 2009-06-08
> **Celauran said:**
> I use it every day from six different machines and have never had a single problem. Really haven't a clue why it's giving you such a hard time.

Ditto.

The only problem I ever had with xammp on Linux, is that I had to change the apache config file before firefox would read my php code.

Phpmyadmin just worked like it should every time I installed it.

---

### Post by Celauran on 2009-06-08
> **kapi said:**
> 
What I mean is when I try using mySQLAdmin and create a new user and password and try to access it via the terminal or the gui for mySQLadmin I get error

```
kapi@craig-laptop:~$ mysql -u kapi -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'kapi'@'localhost' (using password: YES)
```

What if you create the new user from mysql rather than mysqladmin? Login to MySQL as root, then

```
GRANT CREATE, DROP, SELECT, UPDATE, INSERT, DELETE ON *.* TO 'kapi'@'localhost' IDENTIFIED BY 'whatever-password';
```

---

### Post by kapi on 2009-06-08
Sorry tried adding the command but got 

kapi@craig-laptop:~$ GRANT CREATE, DROP, SELECT, UPDATE, INSERT, DELETE ON *.* TO 'kapi'@'localhost' IDENTIFIED BY 'dad52'
bash: GRANT: command not found
kapi@craig-laptop:~$

---

### Post by Celauran on 2009-06-08
You need to first log in to MySQL as root. That was an SQL command I posted, not a shell command.

---

### Post by bodhi.zazen on 2009-06-08
Those are mysql commands, you need to log onto mysql first.

```
mysql -u root -p
```

Then enter root's mysql password, you will get a mysql prompt

> mysql>

If you do not know your root mysql password, you can reset it.

---

### Post by kapi on 2009-06-08
Ok logged in to mysql and apparently changed the password, logged out and then tried to log back in to kapi with new password but was denied access

kapi@craig-laptop:~$ mysql -u kapi -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'kapi'@'localhost' (using password: YES)
kapi@craig-laptop:~$

---

### Post by Celauran on 2009-06-08
Again as MySQL root, try:
```
UPDATE mysql.user SET Password = PASSWORD('new_password') WHERE user = 'kapi';
```

---

### Post by kapi on 2009-06-08
ran command but results still the same

kapi@craig-laptop:~$ mysql -u kapi -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'kapi'@'localhost' (using password: YES)
kapi@craig-laptop:~$

---

### Post by Celauran on 2009-06-08
At this point I'd delete the user, flush privileges, and create a new user.

---

### Post by kapi on 2009-06-08
really appreciate your help - I deleted the kapi user using the mySQLadmin then flushed the privileges and made a new user called oz 

tries accessing oz via terminal but again denied access

What gives? I must be doing something seriously wrong!

---

### Post by Celauran on 2009-06-08
You're creating the new user from within MySQL using the GRANT... I listed earlier?

---

### Post by kapi on 2009-06-08
done! user called oz now created and accessed in terminal,

tried the same in phpmyadmin login window but same original problem still remains, at least we're getting there.

Thanks

---

### Post by Celauran on 2009-06-08
So both root and oz can login via mysql -u name -p? If so, have you tried logging into phpMyAdmin as root? If not, what errors does that generate?

---

### Post by kapi on 2009-06-08
Yep both oz and root can be accessed via the terminal however neither are accessed vai the phpmyadmin login, I don't receive any errors it just sits there.

---

### Post by Celauran on 2009-06-08
Is your browser set to accept cookies from 127.0.0.1 and/or localhost?

---

### Post by kapi on 2009-06-08
checked firefox preferences/ privacy and show cookies and the local host and 127.0.0.1 are both there, so yes I guess it accepts cookies ok

---

### Post by albinootje on 2009-06-08
> **kapi said:**
> checked firefox preferences/ privacy and show cookies and the local host and 127.0.0.1 are both there, so yes I guess it accepts cookies ok

I just installed mysql + phpmyadmin on my Jaunty desktop. 
Set a password for mysql's root account (Tested it also with : mysql -u root -p). 
Tried it in Firefox with [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) and I could log in a root right away.

Can you try with another browser ? For example galeon or konqueror ?

---

### Post by kapi on 2009-06-08
this is weird, I opened opera and input root and nothing happened but when I tried oz and the password the screen flickered and for a split second I had access and then it went back to the login screen again

---

### Post by kapi on 2009-06-08
Still working away and wondered if anyone has any ideas on accessing phpmyadmin

---

### Post by albinootje on 2009-06-08
> **kapi said:**
> Still working away and wondered if anyone has any ideas on accessing phpmyadmin

Here's a list of package names of browsers to test with,

*) text-based :

lynx
links
elinks
links2
w3m

*) gui-based :

galeon
epiphany-browser
midori
arora
dillo
seamonkey
netsurf
konqueror
chromium-browser

Please report the result you have with those.
And what about your apache log files ? Are those saying anything interesting ?
```

tail -f /var/log/apache2/error.log
tail -f /var/log/apache2/access.log

```

---

### Post by kapi on 2009-06-08
tried epiphany, seamonkey, firefox and opera and they all respond the same

---

### Post by kapi on 2009-06-09
kapi@craig-laptop:~$ tail -f /var/log/apache2/error.log
[Mon Jun 08 09:30:22 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Mon Jun 08 16:27:14 2009] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Mon Jun 08 19:47:21 2009] [notice] caught SIGTERM, shutting down
[Mon Jun 08 19:47:22 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Mon Jun 08 19:48:21 2009] [error] [client 127.0.0.1] File does not exist: /usr/share/phpmyadmin/index
[Mon Jun 08 19:48:21 2009] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico, referer: [http://localhost/phpmyadmin/index](http://localhost/phpmyadmin/index)
[Mon Jun 08 19:54:18 2009] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico, referer: [http://127.0.0.1/](http://127.0.0.1/)
[Mon Jun 08 23:14:51 2009] [notice] caught SIGTERM, shutting down
[Tue Jun 09 10:37:38 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations

---

### Post by nandemonai on 2009-06-09
> **kapi said:**
> kapi@craig-laptop:~$ tail -f /var/log/apache2/error.log
[Mon Jun 08 09:30:22 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Mon Jun 08 16:27:14 2009] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Mon Jun 08 19:47:21 2009] [notice] caught SIGTERM, shutting down
[Mon Jun 08 19:47:22 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Mon Jun 08 19:48:21 2009] [error] [client 127.0.0.1] File does not exist: /usr/share/phpmyadmin/index
[Mon Jun 08 19:48:21 2009] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico, referer: [http://localhost/phpmyadmin/index](http://localhost/phpmyadmin/index)
[Mon Jun 08 19:54:18 2009] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico, referer: [http://127.0.0.1/](http://127.0.0.1/)
[Mon Jun 08 23:14:51 2009] [notice] caught SIGTERM, shutting down
[Tue Jun 09 10:37:38 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations

**index.php**

That's your problem right there it seems. Sounds more like a problem with apache that phpmyadmin or mysql.

---

### Post by kapi on 2009-06-09
sorry, so what do I do i am a bit new to this side of things

---

### Post by nandemonai on 2009-06-09
First, try [http://localhost/phpmyadmin/index.php](http://localhost/phpmyadmin/index.php)

Secondly, please post the output of this command:

```
cat /etc/apache2/conf.d/phpmyadmin.conf
```

Something funky is going on. Apache is calling and not finding the right index file:

```
[Mon Jun 08 19:48:21 2009] [error] [client 127.0.0.1] File does not exist: /usr/share/phpmyadmin/index
```

It should be looking at /usr/share/phpmyadmin/index.php

---

### Post by kapi on 2009-06-09
Input the command as requested here is the output

kapi@craig-laptop:~$ cat /etc/apache2/conf.d/phpmyadmin.conf
cat: /etc/apache2/conf.d/phpmyadmin.conf: No such file or directory
kapi@craig-laptop:~$

---

### Post by Celauran on 2009-06-09
Looks like there are phpmyadmin files missing. Purge, reinstall, and make sure you specify apache2 during the setup.

---

### Post by kapi on 2009-06-09
when setting up phpmyadmin should I select the dbconfig-common?

---

### Post by Celauran on 2009-06-09
I don't have that installed, so it certainly isn't required. I just uninstalled and reinstalled phpmyadmin.

```
sudo aptitude install phpmyadmin
```

gave me everything I needed. The only post-install choice I had to make was which web server to install for.

---

### Post by albinootje on 2009-06-09
> **kapi said:**
> 
cat: /etc/apache2/conf.d/phpmyadmin.conf: No such file or directory


Are you using apache2 or lighttpd or the older ?

Please post the output of :
```

dpkg -l|grep apache
dpkg -l|grep http

```

What choices did you make during the installation of phpmyadmin ?
In Ubuntu Jaunty I got the choice to use it for apache2 and/or lighttpd.
Did you get any errors during the phpmyadmin installation ?

---

### Post by kapi on 2009-06-09
got this when tried to purge phpmyadmin

kapi@craig-laptop:~$ sudo apt-get purge phpmyadmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  php5-gd libmcrypt4 php5-mcrypt dbconfig-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  phpmyadmin*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
kapi@craig-laptop:~$ 
kapi@craig-laptop:~$

---

### Post by albinootje on 2009-06-09
> **kapi said:**
> 
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory


Please close down Synaptic Package Manager, Add/Remove, Update Manager first, and then try again.

---

### Post by kapi on 2009-06-09
sorry feel stupid,

right reloaded phpmyadmin, tried it in browser and still have same problem.

I selected apache2 when loading phpmyadmin as suggested

---

### Post by kapi on 2009-06-09
kapi@craig-laptop:~$ dpkg -l|grep apache
ii  apache2                                    2.2.11-2ubuntu2                                            Apache HTTP Server metapackage
ii  apache2-mpm-prefork                        2.2.11-2ubuntu2                                            Apache HTTP Server - traditional non-threade
ii  apache2-utils                              2.2.11-2ubuntu2                                            utility programs for webservers
ii  apache2.2-common                           2.2.11-2ubuntu2                                            Apache HTTP Server common files
ii  libapache2-mod-auth-mysql                  4.3.9-11                                                   Apache 2 module for MySQL authentication
ii  libapache2-mod-php5                        5.2.6.dfsg.1-3ubuntu4.1                                    server-side, HTML-embedded scripting languag
ii  rapache                                    0.7-0ubuntu4                                               apache2 graphical configuration tool

---

### Post by kapi on 2009-06-09
kapi@craig-laptop:~$ dpkg -l|grep http
ii  apt-transport-https                        0.7.20.2ubuntu6                                            APT https transport
ii  libcrypt-ssleay-perl                       0.57-1                                                     Support for https protocol in LWP
kapi@craig-laptop:~$

---

### Post by kapi on 2009-06-09
Am just going to uninstall everything and try XAMP

---

### Post by Ozor Mox on 2009-06-09
I find it to be an excellent, easy to use piece of software. Admittedly though, I have only used it either with XAMPP for development or on an already configured server for deployment.

For PHP development, XAMPP is simply a fantastic product.

---

