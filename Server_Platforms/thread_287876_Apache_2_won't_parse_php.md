---
title: "Apache 2 won't parse php"
date: 2006-10-29
forum: Server Platforms
---

### Post by mwagena on 2006-10-29
I followed the [wiki page]("https://help.ubuntu.com/community/ApacheMySQLPHP") on lamp for installing Apache2, php5 & mysql on dapper server. 

The problem is that php files are not being parsed. Instead they are offered for a download. 

The wiki has this to say about this problem:> Does your browser ask if you want to download the php file instead of displaying it? If Apache is not actually parsing the php after you restarted it, install libapache2-mod-php5. It is installed when you install the php5 package, but may have been removed inadvertently by packages which need to run a different version of php. You may also need to actually enable it, by doing sudo a2enmod php5 followed by sudo /etc/init.d/apache2 restart

Problem is, de module IS actually running (ie: if you try to run it it says it;s already running) an has correctly been set-up (correct symlinks in mods-enabled etcetera). 

It also states: 
Apache/2.0.55 (Ubuntu) PHP/5.1.2 Server at anonymous.com Port 80
If you surf to the site.

Everything seems to be ok but php files are not being parsed, any help would be much appreciated.

---

### Post by DaveBorealis on 2006-10-29
Sorry,
I can't help with your problem per se, but do you know that if you set up the following file```
/usr/local/www/data/info.php
``` you'll get a nice print out of information relevant to apache and php?  (/usr/local/www/data is where my FreeBSD server keeps the web pages.)

In fact it gives out *too* much info, so if you use it, either remove the page once you save it or (as I do) ```
chmod 000 info.php
```.

Hope this helps.  Maybe it'll offer a clue or two to solving the issue.
Dave

[EDIT] DOH!  It just occured to me that if you can't get php working, you can't view the info.php!  Well if you do get it running, it'll have some good info for ya.

---

### Post by MJN on 2006-10-29
Do you have the following in your **/etc/apache2/mods-available/php.conf** ?

```
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps
```I seem to recall that when I had similar issues some time back (on Breezy, but still Apache2) I found that the SetInput/OutputFilter directives in php.conf were no longer supported by Apache2.

Mathew

---

### Post by robin.w on 2006-10-29
Hello everybody,

when I reinstalled my Kubuntu 6.06 and I run Apache2+PHP5+MySQL and the strange thing has occured. I cannot open any php file on HTTP server. I checked everything, extension, modules, logs and the result = nothing. It seems to be fine but it's not.

---

### Post by paulhoy on 2006-10-29
I'm experiencing the same problem with Edgy. 

Never had a problem with Dapper.

---

### Post by MJN on 2006-10-30
What do your **/etc/apache2/mods-available/php.conf** files look like?

---

### Post by robin.w on 2006-10-30
I found the solution of someone here. Instead localhost or IP 127.0.0.1 use IP 127.0.1.1. It's really working good.

Anyway all modules are loaded properly. I just added links on php5.conf and php5.load located in folder **mods-available** to the folder **mods-enable** but I'm not sure if it was really necessary :) .

```
cd /etc/apache2/mods-enable
sudo ln -s /etc/apache2/mods-available/php5.conf ./php5.conf
sudo ln -s /etc/apache2/mods-available/php5.load ./php5.load

```

---

### Post by MJN on 2006-10-30
You're meant to be using **a2enmod php5** which will effectively perform those symlinks for you. If you hadn't done this then your PHP5 module wasn't loaded prior to you doing it manually - hence why you'll have been having difficulties.
 
Mathew

---

### Post by mwagena on 2006-10-30
Ok, my solution was really ugly. The solution was the non-existence of the problem ;)

After I asked somebody else to lookup a PHP page from my server all went well. The problem was actually my firefox who was doing something wrong. I just updated to edgy (my desktop that is, not the server) and my firefox apprantly broke with the update to 2.0. To doublechek I installed opera and all was well. 

Doh...

---

### Post by drjnet on 2006-12-30
Well im on dapper and I have the same problem. These are all ok

- mods_enabled - php.conf and .load are there and they contain the appropriate headers/module info
- /etc/mime-types - php mime types are active
- php5 module - definately enabled with a2enmod php5

I've restarted (force reloaded) apache many times but still my test.php file just displays in the browser as html rather than actually parsing the php. The file contains:
```

<?php
phpinfo();
?>

```

I've set the server to list files in a directory if there is no index file and the icon next to the test.php file shows a question mark so I don't think apache2 is recognising the php file (hence not parsing it).

Im stumped with this problem to be honest, I've tried everything and checked it all and just cant see any problem.

PLEASE help someone its doing my nut right in.....

---

### Post by pokemoen on 2007-06-06
For me the problem was duplicate entries of AddType and AddHandler in apache2.conf.
If your modules-enabled is set-up correctly it has those entries already and you don't  need them in apache2.conf.

HTH
Alex

---

### Post by Bionic_Beefpile on 2007-06-14
Somehow on my Feisty installation I had both Apache and Apache2 installed.  Using Synaptic to uninstall Apache fixed the PHP parsing problem.

Not sure if this is broadly applicable, but it might not hurt to check

---

### Post by Doug$ on 2007-10-14
Same as  Bionic_Beefpile: On my Feisty installation I had both Apache and Apache2 installed. Using Synaptic to uninstall Apache fixed the PHP parsing problem.

---

### Post by jazzgossen on 2008-01-07
I'm having the same problem, using 7.10.


[LIST]
[*]I have apache2 and php5 installed (and libapache2-mod-php5 apache2-mpm-prefork got installed with them).
[*]I have no AddType and AddHandler in apache2.conf, just the ones in mods-enabled/php5.conf.
[*]I have restarted apache2 since I installed php.
[*]I don't have "apache" installed, and I can't find any other apache version than apache2 in the 7.10 repositories.
[*]I have checked both with Firefox and Opera. The html content shows fine, but not the php content (though I can't see why that would make a difference, since the php should be parsed by the server, right?).
[/LIST]

My test page looks like below.

What else can be wrong?

[HTML]<html>

<head>
<title>Temperaturmonitor</title>
<meta http-equiv="Content-Type" content="text/html;charset=iso-8859-1" />
<link rel="stylesheet" type="text/css" href="" />
</head>

<body>

<h1>Temperaturmonitor</h1>

<p>
  <?
     phpinfo();
  ?>
 
</p>

</body>

</html>
[/HTML]

---

### Post by jazzgossen on 2008-01-08
I have also rebooted the computer, and tried changing the <? tag to <?php

Still, apache2 spits out the naked php code, without parsing it.

The file I'm testing is /var/www/index.php. I'm looking at it by pointing my browser to [http://localhost/](http://localhost/)

---

### Post by pumahalen on 2008-01-09
Background:

I have i 6.06 server and it works flawlesssly. Since I have been in the business since 1981, I'm used to command-line systems. However, I needed a test-machine and wanted that to be a desktop, so I chose 7.1, desktop, imagining that it would be easier to inslatt the LAMP-option on a desktop than the other way around. (I have until recently used Fedora). But, then, after installing Apache2, I am stuck with the "php not parsing"-problem. 

I svear, I have kept my hands off the keyboard regarding any steps outside what the guides tells me, as if someone has been pointing a gun at me! This is my fifth reinstall... 

Now, for the test I made the hello.php like this: < ?php echo "Hello World"; ?>, but it shows the code as is. Next, i made the phpinfo.php like this: <?php phpinfo (); ?> and that works! So, back to the hello.php, renaming it to index.php, but no luck. Renaming phpinfo.php to index.php made no difference, it works. 

"Google is your friend", but on this third day, no results have come up.  To the answers asked in this forum it is to say that  I have tested them all (hence all the reinstallations :) .)!

It looks to be such a simple thing! I can not accept to back down to such a silly problem! Installing a 6.06 Desktop would be to accept a defeat from a simple stupid nonsense thing of a problem! 

Anyone?

Thanks for your attention! :)

---

### Post by MJN on 2008-01-09
To cover all bases in one go, let's have a look at the output of all the following:

[B]cat /etc/apache2/apache2.conf
cat /etc/apache2/mods-available/php*
ls /etc/apache2/mods-enabled/[/B]

Is the server publicly accessible? Got a URL?

Mathew

---

### Post by pumahalen on 2008-01-09
Thank you for your interest, sorry for the delay.

I have set up a small ftp-service at [ftp://hale.pumahalen.com](ftp://hale.pumahalen.com), username = your nick, password = ubunto (not that it matters, but anyhow). There you will find the requested files.

Reg

Jack.

---

### Post by MJN on 2008-01-09
Do you have a PHP URL that we can see?

(I note your Squirrelmail pages are parsing fine)

Mathew

---

### Post by pumahalen on 2008-01-10
Well, it is the 6.06-server that is serving on the net at the moment, and is really doing a great job. I'll hook up the Feisty 7.10  during the day, and let you have a look. (Closing the ftp for now...). Thanks,

Jack

---

### Post by jazzgossen on 2008-01-10
In order not to paste a huge chunk of text here, I did the following:

~> grep -n php /etc/apache2/apache2.conf /etc/apache2/mods-enabled/php5.* 
/etc/apache2/mods-enabled/php5.conf:1:<IfModule mod_php5.c>
/etc/apache2/mods-enabled/php5.conf:2:  AddType application/x-httpd-php .php .phtml .php3
/etc/apache2/mods-enabled/php5.conf:3:  AddType application/x-httpd-php-source .phps
/etc/apache2/mods-enabled/php5.load:1:LoadModule php5_module /usr/lib/apache2/modules/libphp5.so

Does that say anything?

---

### Post by pumahalen on 2008-01-10
Indeed it does, it says:

grep -n php /etc/apache2/apache2.conf /etc/apache2/mods-enabled/php5.*
/etc/apache2/apache2.conf:338:#AddType application/x-httpd-php .php
/etc/apache2/apache2.conf:339:#AddType application/x-httpd-php-source .phps
/etc/apache2/mods-enabled/php5.conf:1:<IfModule mod_php5.c>
/etc/apache2/mods-enabled/php5.conf:2:  AddType application/x-httpd-php .php .phtml .php3
/etc/apache2/mods-enabled/php5.conf:3:  AddType application/x-httpd-php-source .phps
/etc/apache2/mods-enabled/php5.load:1:LoadModule php5_module /usr/lib/apache2/modules/libphp5.so

I notice the diff in apache2.conf, but can hardly see its importance.

Please have a  look at [www.nereid.no](www.nereid.no), try the hello.php and the helloagain.php

Thanks!

---

### Post by jazzgossen on 2008-01-10
Just to say that I have the same problem as you, so my post was not a suggested solution. And you're right, the difference in apache2.conf can't be significant, since you have the lines commented out, and I don't have them at all.

I can't find [http://www.nereid.no/hello.php](http://www.nereid.no/hello.php) or helloagain.php.

---

### Post by SteveHillier on 2008-01-10
> **mwagena said:**
> Ok, my solution was really ugly. The solution was the non-existenc
After I asked somebody else to lookup a PHP page from my server all went well. The problem was actually my firefox who was doing something wrong. I just updated to edgy (my desktop that is, not the server) and my firefox apprantly broke with the update to 2.0. 


I set up an Apache 2 server Ok under Dapper.  When I tried it with Edgy I had a lot of Samba problems which meant I could or may could not look at network locations..

Just thought you might need to be aware

---

### Post by pumahalen on 2008-01-10
Sorry for the mess, se my edit, it's under apache2-default. Yoy did find [www.nereid.no](www.nereid.no) ?

Jack

---

### Post by jazzgossen on 2008-01-10
> **pumahalen said:**
> Sorry for the mess, se my edit, it's under apache2-default. Yoy did find [www.nereid.no](www.nereid.no) ?

Do you mean it's at [http://www.nereid.no/apache2-default/](http://www.nereid.no/apache2-default/) ?
I get an error 404 there, too. [http://www.nereid.no](http://www.nereid.no) loads OK though, and shows a Squirrelmail login page.

---

### Post by pumahalen on 2008-01-10
> **jazzgossen said:**
> Do you mean it's at [http://www.nereid.no/apache2-default/](http://www.nereid.no/apache2-default/) ?
I get an error 404 there, too. [http://www.nereid.no](http://www.nereid.no) loads OK though, and shows a Squirrelmail login page.

Sorry about that, please try port 8080. (Poor router got confused..)

Jack

---

### Post by jazzgossen on 2008-01-10
I just can't seem to find any pages other than the Squirrelmail login. Please post a full URL that we can try.

---

### Post by MJN on 2008-01-10
> **pumahalen said:**
> Sorry about that, please try port 8080. (Poor router got confused..)

There's nothing there on port 8080.

Mathew

---

### Post by pumahalen on 2008-01-10
> **MJN said:**
> There's nothing there on port 8080.

Mathew

Thanks for your time. I'll go and have a serious talk with the router, posting again after verifying that access is OK.

Jack

---

### Post by jazzgossen on 2008-01-11
In the meantime, can anybody see a problem with the output of our grep commands in posts #21 and #22? Or any other ideas? I posted my index.php in #14. Could there be a problem with that? (Except for the short php tags?)

---

### Post by MJN on 2008-01-11
> **jazzgossen said:**
> In the meantime, can anybody see a problem with the output of our grep commands in posts #21 and #22? Or any other ideas? I posted my index.php in #14. Could there be a problem with that? (Except for the short php tags?)

The code is fine.

Do you have a URL we can test against?

Mathew

---

### Post by pumahalen on 2008-01-11
I am really sorry (and this is not ironically meant!) to tell you that the  problem "solved itsef", after I went ahead and installed mysql and  rebooting. It reallly gets at me that problems "disappear" in this way, not only because occasional learning is lost, but also because of the lack of your own feeling of "mind over matter" :grin: .

Anyway, I've got a 7.10 Feisty test server with desktop flying, so I'm happy. 

I am  thankful for your interest and time. If I DO find the reason, I'll surely post it.

Keep up the good work!

R,

Jack

---

### Post by MJN on 2008-01-11
It's actually a relief as I wasn't sure where we were going to head next anyway!
 
Cheers,
 
Mathew

---

### Post by jazzgossen on 2008-01-13
> **pumahalen said:**
> I am really sorry (and this is not ironically meant!) to tell you that the  problem "solved itsef", after I went ahead and installed mysql and  rebooting. 

Which mysql packages did you install? I tried installing mysql-server and php5-mysql and then restarted apache2 (though I haven't tried rebooting). That didn't help. Did you install anything else?

---

### Post by jazzgossen on 2008-01-17
Oh, and if you want an URL to try, you can use [http://hem.eyra.se](http://hem.eyra.se) (though it only works when the computer is on, which is not always).

---

### Post by bernardfrancois on 2008-01-20
I had the same problem, but it was fixed automatically when I installed the package 'phpmyadmin', which I needed anyway.

Hope this helps some people :-)

---

### Post by slamdunk on 2008-01-20
Hi,

i'm using gutsy and found same problem reported in this thread (I guess).

I have installed php-mod, apache2 and mysql.

Strange thing is that I can install locally joomla (php+mysql), phpbb(php+mysql) and other thing to get them work perfectly in my "localhost". But a simple page like this:

<html><head></head><body>
test : <?php echo "OK"; ?>
</body></html>

not works!

Have you any idea????

Thanks

---

### Post by jazzgossen on 2008-01-20
> **bernardfrancois said:**
> I had the same problem, but it was fixed automatically when I installed the package 'phpmyadmin', which I needed anyway.


Didn't work for me. 

One thing I've noticed is that apache2 says "apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName" when it is restarted. Could that have anything to do with the problem?

---

### Post by MJN on 2008-01-20
No, that's just tell you that in the absence if you telling it what it's called (using the ServerName directive) it's deciding for itself. It's more of a warning, if that, although you are better off setting ServerName as it can help with redirects and various other functions.

Mathew

---

### Post by mario.kostelac on 2008-01-21
So... I have had the same problem since 5minutes before :D.. I have just removed all packages (with purge option) and directory /etc/apache2.
After that, i installed lamp with apt-get and everything works fine.

```
sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql
```

---

### Post by jazzgossen on 2008-01-31
I reinstalled the packages mario kostelac mentioned, but that didn't help. Not immediately, at least. But now I have rebooted, and now it works. Very very strange...

---

### Post by UnCola on 2008-02-23
Same problem, same solution for me - after umpteen re-installs and permission checks without success, rebooted and suddenly it worked.  Only real difference is at this point I do not have phpmyadmin installed, and  before reboot I installed something called php-config hoping it would help.

Very time consuming and unexpected, as MySQL, php admin, and Apache were all working well. I just hope it works after the next reboot, if not its time for total reinstall of 7.4, since  I have tried every available solution that I can find.

---

### Post by faulkes on 2008-02-23
There is a listed bug for apache/php/mysql in the ubuntu server team bug list.

[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/104270](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/104270)

When you install these packages (and depending on order) or if apache is
already installed and php5 is then added, the apache process must be restarted.

This is currently not done automatically and there is no notification that the
admin is required to do so.

A reboot would solve the issue as all services would be restarted. 

The appropriate way to handle this until the bug is resolved is to restart
the apache process manually after you have installed php5.

/etc/init.d/apache2 restart

Faulkes

---

### Post by cdawg on 2008-06-10
Confirmed,

Installing php-config and it's dependencies along with apache2 and libapache2-mod-php5 and their dependencies it works now.

Thanks guys.

---

### Post by supernova_hq on 2008-06-21
Also Confirmed:

After NUMEROUS checks, apache restarts, etc.
> sudo apt-get install php-config
did the trick!


-supernova_hq

---

