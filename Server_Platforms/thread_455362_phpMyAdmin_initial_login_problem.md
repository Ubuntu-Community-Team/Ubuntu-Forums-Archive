---
title: "phpMyAdmin initial login problem"
date: 2007-05-26
forum: Server Platforms
---

### Post by JuicedJuice on 2007-05-26
I'm new to linux, installed Ubuntu a couple days ago. Ok, so I used the synaptic package manager to install apache, php, phpMyAdmin and mysql. Everything seems to be installed correctly (everything works) but i'm unsure of how to actually login to phpMyAdmin. I figured i'd create a mysql username/pass through terminal after logging into to mysql as root (GRANT ALL PRIVELEGES ON *.* TO 'admin'@'localhost' -> IDENTIFIED BY 'password' WITH GRANT OPTION; ) but I can't log into phpMyAdmin after doing so. How the heck do I initially get into phpMyAdmin, how do I create a user/pass for it!? I must be overlooking something simple. Thanks.

Im using ubuntu 7.04 64-bit

---

### Post by tturrisi on 2007-05-26
the default (initial) phpmyadmin login uses root & root's pw.
do:
~# mysql -u root -p

---

### Post by JuicedJuice on 2007-05-26
I thought I had to edit the config.inc.php file in /etc/phpmyadmin but I discovered out of frustration (by hitting enter over and over several times) that for some reason I can get logged in but only after a few quick consecutive attempts. Then, once I am logged in I get logged out at random! For example sometimes I can get maybe 6-8 clicks worth of work in before I get logged out but other times the first thing I click (and I mean anything I click on the phpmyadmin page) I get logged out. I can then log back in by quick consecutive login attempts but only to get logged out at random again and so on and so forth. It's making getting anything done pretty difficult.

---

### Post by mrcevic on 2007-07-21
I've got exactly the same problem. Read several post indicating how to reset the password for the root user (which I've done successfully several times) but still, I don't seem to be able to login through Phpmyadmin (except randomly after 6 o 5 clicks as you described).

I installed Phpmyadmin via apt-get (which probably wasn't a good idea) and the default config file reads 

I've checked the config file at /var/lib/phpmyadmin/config.inc.php and it looks like

[PHP]
/* Servers configuration */
$i = 0;

/* Server localhost (cookie) [1] */
$i++;
$cfg['Servers'][$i]['host'] = 'localhost';
$cfg['Servers'][$i]['connect_type'] = 'socket';
$cfg['Servers'][$i]['compress'] = false;
$cfg['Servers'][$i]['auth_type'] = 'cookie';
[/PHP]

Was wondering whether the cookie has something to do with the problem

Using Kubuntu 7.04 and phpMyAdmin 2.9.1.1-Debian-2ubuntu1

---

### Post by mrcevic on 2007-07-21
Here's how I solved the problem:

I edited config.inc.php and changed from the cookie authentication to the http one

[PHP]
$cfg['Servers'][$i]['auth_type'] = 'http';
$cfg['Servers'][$i]['user'] = 'USER';
$cfg['Servers'][$i]['password'] = 'PASSWORD';
[/PHP]

where the CAPITAL letters are the settings you edit.

That's it!

C

---

### Post by 4tro on 2007-07-25
i have this problem as well, even the above fix doesn't help.

it doesn't matter that much though because my own server is running dapper with xampp installation :P

---

### Post by Moobert on 2007-07-26
Was having the same problems with random logouts.

apt-get install php5-mcrypt

Getting that package fixed the issue.

---

### Post by ceke on 2007-08-03
Thanks dude! That saved my life!

Had another problem when trying to import a database previously exported from a windoze version of mysql (running an older version of phpMyAdmin). The database was too big to import. Compressing it with bzip2 and then importing did the job.

Just so that you know :)

---

### Post by mune on 2007-08-05
I tryed to set from 'cookie' to ìhttp' but I obtain a never ending loop anda the login never load.

my conf file is ```

/* Servers configuration */
$i = 0;

/* Server localhost (cookie) [1] */
$i++;
$cfg['Servers'][$i]['host'] = 'localhost';
$cfg['Servers'][$i]['connect_type'] = 'socket';
$cfg['Servers'][$i]['compress'] = false;
$cfg['Servers'][$i]['auth_type'] = 'cookie';

$cfg['Servers'][$i]['user'] = 'USER; 
$cfg['Servers'][$i]['password'] = 'PASSWORD'; 

/* End of servers configuration */

$cfg['blowfish_secret'] = 'KEY_THAT_CANNOT_BE_LEFT_EMPTY';
```
but when I try to login I get > #1045 - Access denied for user 'USER'@'localhost' (using password: YES) (USER is the one being in the conf file).

Any help, thanks?

Fede

---

### Post by WestCoastSuccess on 2007-08-06
Many thanks, Moobert! This issue has been driving me nuts for the past 6 months - it's literally taken me hours to make the most minor changes or repair broken tables in mythtv due to being thrown out of phpMyAdmin and repeatedly attempting to login - did apt-get install php5-mcrypt as you suggested and works like a charm!

What is the problem that php5-mycrypt solves?

Again, thanks!

---

### Post by mune on 2007-08-08
I don't know why, but MyPhpAdmin started  to work.

Thanks:)

---

### Post by Kanoa on 2007-08-16
I was experiencing the multiple try log-in and intermittent log out problems described in this thread.  I installed php5-mcrypt as suggested and it fixed the problem.  It really needs to be installed as a part of any LAMP installation. Thanks for the help...

---

### Post by lkpatir on 2007-08-29
thank u Mr. mrcevic, u r great!I had d same problem.i needed several attempts to login 2 d phpmyadmin auth. in between these attempts, "access deniied..." used to come sometimes or atleast once among those attempts for access.i just changed auth_type from  'cookie' to 'http' and d problem gone!!!
 plz can u help me, how can i post a new thread in this ubuntu forum, i dont see any option here to do that, but i wonder how people are posting new threads!!

---

