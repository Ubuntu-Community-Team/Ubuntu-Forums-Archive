---
title: "Creating my first web server"
date: 2010-06-29
forum: Server Platforms
---

### Post by Lenny212 on 2010-06-29
Hi, I am a beginner web programmer.
I run this command in Terminal (sudo /opt/lampp/lampp start)
I get this message: 
Starting XAMPP for Linux 1.7.3a...
XAMPP: Another web server daemon is already running

How do I stop daemon (is this dangerous)
Then how do I set up website files for use by [http://localhost](http://localhost)

Thanks for your help
Remember, I am an amateur so keep instructions simple

---

### Post by lisati on 2010-06-29
Moved to "server platforms"

Some useful information can be found at [https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

---

### Post by Leppie on 2010-06-29
what happens if you go to the [http://localhost](http://localhost) address in a browser?

---

### Post by Lenny212 on 2010-06-29
Response is:
It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.


However, XAMPP seemed to be the preferred system online.
I have some basic html files but want to do some ASP. I have some ideas for a small project. Where do I copy files to to get them to run on web server?

Thanks for you reply

---

### Post by Lenny212 on 2010-06-29
Thanks lisati, I will do some reading tomorrow night :-k

---

### Post by okplayer02 on 2010-06-29
> **Lenny212 said:**
> Response is:
It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.


However, XAMPP seemed to be the preferred system online.
I have some basic html files but want to do some ASP. I have some ideas for a small project. Where do I copy files to to get them to run on web server?

Thanks for you reply
 you put your document into the root directory of your server the default directory for ubuntu is 

/var/www/

---

### Post by Leppie on 2010-06-29
> **Lenny212 said:**
> Response is:
It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.


However, XAMPP seemed to be the preferred system online.
"It works!" is the typical response from the Apache web server. the A in XAMPP stands for Apache, so basically it's working ;)

if you want to see the xampp stuff, i believe you have to put /xampp after localhost:
[http://localhost/xampp](http://localhost/xampp)

---

### Post by grpace on 2010-06-29
I got basically the same thing when I had XAMPP installed...  BUT NOT RUNNING...  And then installed Drupal.

All I can figure is that...
Because the MySQL part of XAMPP was not running, Drupal decided there was no database installed, and installed MySQL as a service in a different location.  I haven't yet figured out where Drupal installed it.

What I have to to (until I figure out how to stop it from happening... I'm newbie, too):

1) Reboot.
2) Open a Terminal window.
3) Type in 'service --status-all' [ENTER] (displays all services running).

Look in the list.  I saw apache2 and MySQL running when XAMPP WASN'T !
I could not get XAMPP to start correctly with these daemons already running.

4) Type in 'sudo service apache2 stop' [ENTER] (stops the Apache server).
5) Type in 'sudo service mysql stop' [ENTER] (stops the mysql server Drupal installed).

Then do XAMPP start.

Again, I'm a newbie... I don't know where Drupal put this stuff... And even after removing Drupal and re-booting, the services STILL appear on boot-up.

If someone can shed some light on this, it would be GREATLY appreciated.

grpace

---

### Post by grpace on 2010-06-29
OK...
Just got a response from Drupal.
The text follows.

-----

During the installation, Drupal asked me  for a password for the user 'root' on the MySQL database.
-----
That doesn't sound like Drupal, it never asks for your root password.
 Drupal PHP web scripts do not attempt to install or configure Apache  or MySQL for you.
 You must have already had Apache running *anyway* to even see  the first Drupal install screen, so the Drupal scripts can't have done  that for you.
 I think you may be confused.
Did you run apt-get install apache2 or something like that  yourself? Because *that* is how Apache gets onto your system.
Could it be that you tried some other unknown, unsupported way to  install Drupal? (And its dependencies?) I've heard rumors about a Debian  package, but that's out-of-date I think.


----


Full Quote-and Response:


-----


The install of Drupal came directly through Ubuntu Software  Repository.
And... Yes!  During the install it asked for a password !


 Quote:
Drupal PHP web scripts do not attempt to install or configure Apache or  MySQL for you.
 

Response:
Well, SOMETHING sure did during the install !  And the Drupal install  was the ONLY thing running at the time.  Look, man...  I'm not  dreaming...  I'm not on drugs !
 

Quote:
You must have already had Apache running anyway to even see the first  Drupal install screen, so the Drupal scripts can't have done that for  you.
 

Response:
Not true when initially downloading and installing from Ubuntu.  Again, I  have XAMPP installed, but IT WAS NOT RUNNING when the install took  place.
 

Quote:
Did you run apt-get install apache2 or something like that yourself?  Because that is how Apache gets onto your system.
 

Response:
Used the XAMPP install (gzip for Linux), and XAMPP started correctly on  demand.  Not doing it since I tried to install Drupal.  Since then,  XAMPP, upon start, complains about apache and mysql daemons already  running.
 

A simple:
sudo service --status-all
Reveals that, yes, in fact, the daemons are running as a service upon  start-up.
 

Quote:
Could it be that you tried some other unknown, unsupported way to  install Drupal? (And its dependencies?) I've heard rumors about a Debian  package, but that's out-of-date I think.
 

Response:
Again...  Directly from the Ubuntu Repositories.


 OK...
I don't want to get into a flame-throwing thing with you.
 

If it WAS NOT Drupal...
Can you tell me how to stop the daemon services on start-up ?
 

And again...
If XAMPP is running...
Will Drupal see it ?
 

-----

Waiting on a response...

---

### Post by Lenny212 on 2010-06-29
Hi, thanks for your replies. I am not making much progress.
I have managed to copy my Test.html file to /var/www/Web folder using Terminal. Nautilus wouldn't allow me to do this.
In Firefox I type address: [http://localhost/Web/Test.html](http://localhost/Web/Test.html) and get the response:
Object not found!

The requested URL was not found on this server. If you entered the URL manually please check your spelling and try again.

If you think this is a server error, please contact the webmaster.
Error 404
localhost
Wed 30 Jun 2010 09:26:13 EST
Apache/2.2.14 (Unix) DAV/2 mod_ssl/2.2.14 OpenSSL/0.9.8l PHP/5.3.1 mod_apreq2-20090110/2.7.1 mod_perl/2.0.4 Perl/v5.10.1 

I know I am asking basic questions but your help would be really appreciated and help get a small community website project started.
Thanks

---

### Post by Leppie on 2010-06-29
check the permission on the Web folder.
normally apache web pages are accessed using the www-data account. so this account normally should have at least group permissions.
you can check the permissions like this:
```
ls -al /var/www
total 4
drwxr-xr-x  3 root     root       16 2010-06-30 02:02 .
drwxr-xr-x 16 root     root     4096 2010-06-24 18:34 ..
drwxr-xr-x  2 www-data www-data    6 2010-06-30 02:02 Web

```

---

### Post by Lenny212 on 2010-06-29
This is what I get:

lenny212@lenny212-ubuntu:~$ ls -al /var/www
total 16
drwxr-xr-x  3 root     root     4096 2010-06-30 09:25 .
drwxr-xr-x 17 root     root     4096 2010-05-24 19:50 ..
-rw-r--r--  1 root     root      177 2010-05-10 19:58 index.html
drwxr-xr-x  5 lenny212 lenny212 4096 2010-06-29 20:47 Web

---

### Post by Leppie on 2010-06-29
ok, set the folder owner to www-data: ```
sudo chown www-data:www-date /var/www/Web
```  then try to access the page again.

---

### Post by Lenny212 on 2010-06-30
Thank you so much Leppie,
With localhost working and my basic knowledge of html, javascript and vbscript I will be able to make progress on this project - and continue to learn as I go.
I really appreciate your help

---

### Post by Lenny212 on 2010-06-30
New problem!
I can view .html pages in [http://localhost/Web](http://localhost/Web)
I cannot view .asp pages, I just see the raw code.
Hopefully this is something obvious.

---

### Post by Leppie on 2010-06-30
asp is a windows platform and therefore isn't enabled by default in apache. you can install the asp for perl module like this:
 ```
perl -MCPAN -e shell
install CPAN
install Bundle::Apache::ASP
install Bundle::Apache::ASP::Extra
```
 this will also install support for FormFill, XSLT, and SSI.

---

### Post by Leppie on 2010-06-30
> **grpace said:**
> Waiting on a response...

grpace, please start a new thread.

---

