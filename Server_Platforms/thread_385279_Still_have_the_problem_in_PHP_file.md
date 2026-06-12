---
title: "Still have the problem in PHP file"
date: 2007-03-15
forum: Server Platforms
---

### Post by jenhsun on 2007-03-15
This is my second post since no one can help me out my basic problem.

I have a clean install edgy server without LAMP or DNS package. Then follow the link [http://www.mysql-apache-php.com/](http://www.mysql-apache-php.com/)  to setup my server at home. 
This server (PC) is behind a router. I did set port forwarding 80 and also DMZ to the internal IP. 

Then I have a html file that I create in directoyroot /var/www , 
YES, I can see html from outside (internet), However, when I create a test.php follow by the manual it won't show anything. The browser just keep looping.

Then I test all of them from internal network (router) , I can see html and php both work perfect.

Then I check the permission:

-rw-r--r-- 1 root root 38 2007-03-16 00:03 test.html
-rw-r--r-- 1 root root 20 2007-03-15 08:16 test.php

It seems to be ok. 

What am I supposed to do? is that the apache2 server problem?

---

### Post by Nikron on 2007-03-15
Why did you DMZ your server?  I really don't see a need for it..

---

### Post by jenhsun on 2007-03-15
OK, I close the DMZ...but still can't see the php. 
I am very sure that my basic php test code is just fine.

I think my problem is very basic from the clean starting to install apache server in Ubuntu Linux behind router.

Anyone?

---

### Post by Mr. C. on 2007-03-15
What do your error logs show ?

A DMZ is a fine idea.  Providing an extra layer of security is wise.

MrC

---

### Post by jenhsun on 2007-03-15
My error.log only shows notice on configured, caught SIGTERM, shutting down and so on. I believe that's my initial installation.  
And my access.log shows some lines about "GET / HTTP ..." and the  "GET /test.php ...." Only the "GET"....is that normal?

I didn't change any inside the apache2.conf or the  /etc/apache2/sites-enabled/000-default  

By the way, I leave the test.php in /var/www
And it's supposed to be the initial installation and testing env. Is that possible that apache2 forbid the phpinfo() by default because of the security?
I didn't do any virtual host right now, just the simple testing. All I want is my php file can be viewed outside the router.

And Wow, I have Mr C response. I saw some of your threads about the network solution, that's great. 

Anyway, anyone have any idea about my problem? I think you can try to have a clean install and setup behind router same as me, you will find out what I am talking about. Please don't do any configuration first.

---

### Post by Mr. C. on 2007-03-15
I have no trouble running a test.php program remotely.

My code looks like:
```
$ cat test.php
<?php
phpinfo();
?> 
```

Show the access logs if you want me to interpret.  I can't tell from what you presented, as they are truncated.

MrC

---

### Post by jenhsun on 2007-03-15
The Access.log

59.125.8.168 - - [16/Mar/2007:08:35:31 +0800] "GET / HTTP/1.1" 200 38 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.2) Gecko/20060601 Firefox/2.0.0.2 (Ubuntu-edgy)"
59.125.8.168 - - [16/Mar/2007:08:35:36 +0800] "GET / HTTP/1.1" 304 - "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.2) Gecko/20060601 Firefox/2.0.0.2 (Ubuntu-edgy)"
59.125.8.168 - - [16/Mar/2007:08:35:37 +0800] "GET / HTTP/1.1" 304 - "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.2) Gecko/20060601 Firefox/2.0.0.2 (Ubuntu-edgy)"
59.125.8.168 - - [16/Mar/2007:08:35:43 +0800] "GET /test.php HTTP/1.1" 200 39632 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.2) Gecko/20060601 Firefox/2.0.0.2 (Ubuntu-edgy)"
59.125.8.168 - - [16/Mar/2007:08:35:43 +0800] "GET /test.php?=PHPE9568F34-D428-11d2-A769-00AA001ACF42 HTTP/1.1" 200 2524 "http://jenhsun.homeip.net/test.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.2) Gecko/20060601 Firefox/2.0.0.2 (Ubuntu-edgy)"
59.125.8.168 - - [16/Mar/2007:08:35:43 +0800] "GET /test.php?=PHPE9568F35-D428-11d2-A769-00AA001ACF42 HTTP/1.1" 200 2146 "http://jenhsun.homeip.net/test.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.2) Gecko/20060601 Firefox/2.0.0.2 (Ubuntu-edgy)"
59.125.8.166 - - [16/Mar/2007:08:36:07 +0800] "GET / HTTP/1.1" 200 38 "-" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.1.2) Gecko/20070219 Firefox/2.0.0.2"
59.125.8.166 - - [16/Mar/2007:08:36:14 +0800] "GET /test.php HTTP/1.1" 200 16421 "-" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.1.2) Gecko/20070219 Firefox/2.0.0.2"
59.125.8.166 - - [16/Mar/2007:08:41:04 +0800] "GET /test.php HTTP/1.1" 200 16421 "-" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.1.2) Gecko/20070219 Firefox/2.0.0.2"

And the error.log

[Fri Mar 16 08:30:31 2007] [notice] Apache/2.0.55 (Ubuntu) configured -- resuming normal operations
[Fri Mar 16 08:30:32 2007] [notice] caught SIGTERM, shutting down
[Fri Mar 16 08:30:33 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Fri Mar 16 08:35:21 2007] [notice] caught SIGTERM, shutting down
[Fri Mar 16 08:35:22 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations

---

### Post by Mr. C. on 2007-03-15
Your connections are returning OK status (200), but the sizes of the transfer continually vary.

```
HTTP/1.1" 200 39632
HTTP/1.1" 200 2524
HTTP/1.1" 200 2146
HTTP/1.1" 200 16421 
HTTP/1.1" 200 16421
```

I suppose your server is down; I get no response at all.

MrC

---

### Post by Nikron on 2007-03-15
As an aside, why is DMZing a server a good idea?  I always thought it was a bad idea.  Can you educate me on this matter?  Thanks

---

### Post by jenhsun on 2007-03-15
Weired... the webserver is still running. I didn't touch anything.
you can link to [http://jenhsun.homeip.net](http://jenhsun.homeip.net) first, you can see my initial html page
then try php file and so on.

You know what, I think it might be the design nature of apache2 which will block the server information from outside the world.
I think I better read apache2 book to setup a virtual host for testing the php file. I am afraid that I still can't see the simple php files.

---

### Post by Nikron on 2007-03-15
Oh don't worry, on a default LAMP install test.php works fine...

[www.nikron.net/test.php](www.nikron.net/test.php)

---

### Post by jenhsun on 2007-03-15
I did try the default LAMP package before. It's still the same.
The problem exist for several days now.

---

### Post by Mr. C. on 2007-03-15
> **Nikron said:**
> As an aside, why is DMZing a server a good idea?  I always thought it was a bad idea.  Can you educate me on this matter?  Thanks

Sure.  A DMZ allows publicly accessible servers to be outside of the LAN, while still being protected by the firewall.  Thus, if the publicly accessible server is compromised, there is still a firewall in between that server and the LAN.

Many corporations use DMZs, and larger ones use multiple layers of firewalls.

Make sense?
MrC

---

### Post by Mr. C. on 2007-03-15
> **jenhsun said:**
> Weired... the webserver is still running. I didn't touch anything.
you can link to [http://jenhsun.homeip.net](http://jenhsun.homeip.net) first, you can see my initial html page
then try php file and so on.

You know what, I think it might be the design nature of apache2 which will block the server information from outside the world.
I think I better read apache2 book to setup a virtual host for testing the php file. I am afraid that I still can't see the simple php files.

Your server is not responding to anything from me.  It has nothing to do with php.  The server is not acknowledging a connection attempt on port 80.

MrC

---

### Post by jenhsun on 2007-03-15
Mr C, that's new to me.
You mean you can't even view my html page?

---

### Post by Nikron on 2007-03-15
Actually, I do see his hello world index.html page, but can't load his test.php ...   Also, thanks for the info Mr. C...  I see no reason to put my home server into a DMZ zone however, since it's a.. home server =P

---

### Post by jenhsun on 2007-03-15
> **Nikron said:**
> Actually, I do see his hello world index.html page, but can't load his test.php ...   Also, thanks for the info Mr. C...  I see no reason to put my home server into a DMZ zone however, since it's a.. home server =P


Mr C is cool, Nikron. I saw some threads from him. He is the man.
I hope this community will have so many people like him really care about the problems from new ubuntu users.

---

### Post by Mr. C. on 2007-03-16
I can't say what's in the way.  I can only say nothing comes back:

$ telnet 59.125.8.166 80 
Trying 59.125.8.166...



No response. Nothing comes back.

MrC

---

### Post by jenhsun on 2007-03-16
Sorry, Mr C. could you try 59.125.8.168 ? That address is wrong.

---

### Post by Mr. C. on 2007-03-16
I see that you have both addresses in your apache logs (do you have two IP addresses ?).  I picked the last one.

Your index.html page is available.  The test.php does not complete:

```
wget http://59.125.8.168/test.php  
--10:16:16--  http://59.125.8.168/test.php
           => `test.php'
Connecting to 59.125.8.168:80... connected.
HTTP request sent, awaiting response... 

```

What happens when you run:

```
php -r 'phpinfo();'
```

from the command line ?

MrC

---

### Post by jenhsun on 2007-03-16
It really get me interesting.

in command terminal:

php -r phpinfo();
-bash: syntax error near unexpected token '('
if I do
php -r 'phpinfo();' 
-bash: php: command not found.

This is weird, I already install php5 and libapache2-mod-php5
However, I do can see the test.php from internal network.

I am sure my typing about the test.php is right

<?php 
phpinfo();
?>

---

### Post by Mr. C. on 2007-03-16
You need the quotes, as I showed the command.

Exactly which php-related packages are installed?  Search for php in the Synaptec Package Manager, and tell us which green boxes are checked.

MrC

---

### Post by jenhsun on 2007-03-16
> **Mr. C. said:**
> You need the quotes, as I showed the command.

Exactly which php-related packages are installed?  Search for php in the Synaptec Package Manager, and tell us which green boxes are checked.

MrC

I have the quotes. it only shows the command not find.
I used a command line without any Gnome or KDE installed. How do I check the php? 
By the way, I did install php5 and libapache2-mod-php5
Follow by this link  [http://www.mysql-apache-php.com/](http://www.mysql-apache-php.com/)
from clean edgy server installation without UI environment, without LAMP and DNS package.

---

### Post by Mr. C. on 2007-03-16
Sorry, I won't go chasing down various how to links.

Since you have no Synaptec, how about output from :

```
dpkg -l 'php*'
```

MrC

---

### Post by jenhsun on 2007-03-16
root@jenhsun:/etc/apache2# dpkg -l 'php*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-conf/Half-installed
|/Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/Name                        Version                          Description
+++-============================================
un php-pear             <none>                         (no description available)
ii   php5                    5.1.6-1ubuntu2             server-side, HTML-embedded scripting Language
uu php5-cgi             <none>                        (no description available)
ii   php5-common     5.1.6-1ubuntu2            Common files for packages built from the php
uu phpapi-2005102  <none>                       (no description available)



Mr C, I type them all from my server into my desktop. I don't know how to capture my server's terminal screen. Do you know which tools can capture terminal screen as a log?

---

### Post by Mr. C. on 2007-03-16
Your packages are older than mine

I have :
```
ii  libapache2-mod-php5                        5.1.6-1ubuntu2.3                     server-side, HTML-embedded scripting languag
ii  php5                                       5.1.6-1ubuntu2.3                     server-side, HTML-embedded scripting languag
ii  php5-common                                5.1.6-1ubuntu2.3                     Common files for packages built from the php
```

You can update with:

```
apt-get update
apt-get dist-upgrade php5 php5-common libapache2-mod-php5
```

To capture screen output, you can either redirect into a file as in :

dpkg -l 'php*' > /tmp/out.txt

and then transfer the file to your browsing system and copy/paste.

MrC

---

### Post by jenhsun on 2007-03-16
Sorry, I think we have the same version.
Here is my information again:

```
 Desired=Unknown/Install/Remove/Purge/Hold 
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed 
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad) 
||/ Name            Version          Description 
+++-===============-================-============================================ 
un  php-pear        <none>           (no description available) 
ii  php5            5.1.6-1ubuntu2.3 server-side, HTML-embedded scripting languag 
un  php5-cgi        <none>           (no description available) 
ii  php5-common     5.1.6-1ubuntu2.3 Common files for packages built from the php 
un  phpapi-20051025 <none>           (no description available)
```

by the way, I did follow the update to upgrade again
Here is the result:

apt-get dist-upgrade php5 php5-common libapache2-mod-php5

```
Reading package lists... 
Building dependency tree... 
Reading state information... 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```


```
 uname -r
2.6.17-10-server
```

---

### Post by jenhsun on 2007-03-16
By the way, I found my /etc/apache2/apache2.conf has this comment

```
#AddType application/x-httpd-php .php 
#AddType application/x-httpd-php-source .phps
```

Should I need to comment out? I try it before, it doesn't make different.

---

### Post by Mr. C. on 2007-03-16
You should already have:

```
$cat /etc/apache2/mods-enabled/php5.conf

<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>
```

This lack of response from php indicates to me a version mismatch somewhere.  Its not clear to me either why your system cannot find php for command line use.

MrC

---

### Post by jenhsun on 2007-03-16
Yes, Mr C. I did have that php5.conf

The problem that can't show the php file is external, not from internal.
I use a router to link pc together, so my desktop-edgy can ftp server-edgy without problem.

Here is my home's network:
I have a ADSL modem come with 3 fixed IP, I use one ip for my xp (Machine A), one goes to my router, the third one currently unused. 
In this router I have Machine A, B, C. 
Machine A (Windows XP) (has two ethernet card, one fixed ip is from ISP, another one ip is from router)
Machine B (Ubuntu Desktop) (only one ip from router)
Machine C (Ubuntu Server) (only one ip from router)


So when you link to my server, actually link to Machine C. 
I can do website editing in Machine A or B because I can transfer file by router. But I also can test the actual link use Machine A external ip goes out and back by [www.dyndns.org]("http://www.dyndns.org") to my Machine C because my router has dyndns service.

I don't know this network design is ok or not. All I want is just a secure and stable webserver at home for me to do my job.

---

### Post by Mr. C. on 2007-03-16
Are you saying your XP machine is connected to BOTH your router and your modem, and your router is connected to your modem also ?

If so, don't do that !

MrC

---

### Post by jenhsun on 2007-03-16
OK, Mr C, I unplug it now. Every PC will stay behind the router.

But how do I check my website going to the public or not?

If you were I want to setup a secure and home base server, what additional hardware I should have? I want to save some money on the hardware issue. 
Currently I only have a router as my firewall, that's it.
3 or maybe more pc for running services in the future if I do e-commence at home.

---

### Post by Mr. C. on 2007-03-16
How many Ethernet ports do you have on your modem ?   3?

The rule here is that you don't want to create a routing loop.  If you have 3 ports on your modem, you can place a PC on the modem and configure it with an external address; but don't connect that same PC to your LAN.  This will allow you to test external access.  Another method is to get a friend to test, or allow you remote access to their system, so that you can check your site from an external IP.  Alternatively, you can use a dialup modem connection and test that way.

One firewall/router appliance is fine for your needs for now.  Purchase and add additional hardware/software only as you need it.

MrC

---

### Post by jenhsun on 2007-03-16
The Ethernet ports on modem is 4.

I will do what your suggestion about the testing. No more money spending on the home based server is a great news to me, Mr C.

Anyway, I really don't know what if my current test.php can't be viewed outside, then the other future php site might be able to be published? LOL...
After all, I hope my future's php file can be showed to the public.

I better keep going on reading apache2 books now.

---

### Post by jelkimantis on 2007-03-17
A question I would ask, as it seems you're just learning about networking & apache, is why the no-gui server?  

It would seem to me that first one should install a GUI LAMP, then test out the server via localhost.  This way we can whittle down the problems.  If PHP works fine in localhost, but not remotely (at all) then that changes the whole problem.

But then, i'm not "the man..."

jsl

---

### Post by jenhsun on 2007-03-17
> **jelkimantis said:**
> A question I would ask, as it seems you're just learning about networking & apache, is why the no-gui server?  

It would seem to me that first one should install a GUI LAMP, then test out the server via localhost.  This way we can whittle down the problems.  If PHP works fine in localhost, but not remotely (at all) then that changes the whole problem.

But then, i'm not "the man..."

jsl

Thank you for response. 
Yes, the localhost and internel network testing are all ok. The problem is my html can be seen outside, but not php file.
You can follow the thread and test what I am talking about. Everything is started from a clean edgy server installation without LAMP and DNS package. Then I follow the [http://www.mysql-apache-php.com/](http://www.mysql-apache-php.com/) to install the apache2 only. Just that simple. I need to know which package that I install and total control the package.
Well, Testing from internal are all OK. Then test from external won't work. That's it.
I really think it might be the apache2 security nature for NOT to public the phpinfo to the world.

---

### Post by tturrisi on 2007-03-17
[http://jenhsun.homeip.net/test.php](http://jenhsun.homeip.net/test.php)
displays the php info just fine.

---

### Post by tturrisi on 2007-03-17
> **Mr. C. said:**
> Sure.  A DMZ allows publicly accessible servers to be outside of the LAN, while still being protected by the firewall.  Thus, if the publicly accessible server is compromised, there is still a firewall in between that server and the LAN.

Many corporations use DMZs, and larger ones use multiple layers of firewalls.

Make sense?
MrC
The downside of this is that the server box is open to any outside connection attempt whereas if you don't use the dmz and use only port forwarding then the router firewall is effective.  When placing a box in the dmz the router firewall is disabled for that box.  If an intruder gains access to the dmz box he can then access other lan boxes because most router firewalls do not filter local lan requests (the router does not consider other lan boxes to be external to any given lan box). To effectively use the dmz one MUST use multiple firewalls.

---

### Post by jenhsun on 2007-03-17
> **tturrisi said:**
> [http://jenhsun.homeip.net/test.php](http://jenhsun.homeip.net/test.php)
displays the php info just fine.

Really? That's a BIG surprise to me since this basic problem bother me  for several days.
You know what, I didn't even change anything except my hardware wiring.
Let me tell you the symptoms before and after following by what I did for the basic webserver setup.
 
My previous home networks is==>
there are three pc that I have and three fixed ip come from my isp.
these three pc OS is : Machine A (XP) with two ethenet card.
Machine B (Ubuntu Desktop) with one ethernet card
Machine C (Ubuntu Server) with one ethernet card
and a netgear router has dyndns.org service

Router get one fixed ip from ISP modem.
Machine A has one fixed ip from ISP's modem, one ip from router.
Machine B has only one ip from router.
Machine C has only one ip from router.

Then here is my installation and setup for server:
1. download edgy server iso and burn to cd
2. clean install to Machine C WITHOUT LAMP and DNS package, for package control purpose.
3. follow the link: [http://www.mysql-apache-php.com/](http://www.mysql-apache-php.com/) to setup the apache2 only
4. test php file (test.php)
5. Then I use internal network form Machine B to test Machine C, WORK.
6. Then I try external from Machine A to test Machine C by using dyndns....dead.

After several days passed, Mr C suggested me unplug the Machine A from ISP's modem and use router's ip only. I followed his suggestion and done. But still don't know how to solve the php problem. Well, your information is really a surprise to me.


So anyone know what exactly the problem is ? Is that the multi-linking problems  or is my modem problem?
And also, I am afraid that my XP was get hacked or be compromised before switching behind the router.

---

### Post by Mr. C. on 2007-03-17
> **tturrisi said:**
> The downside of this is that the server box is open to any outside connection attempt whereas if you don't use the dmz and use only port forwarding then the router firewall is effective.  When placing a box in the dmz the router firewall is disabled for that box.  If an intruder gains access to the dmz box he can then access other lan boxes because most router firewalls do not filter local lan requests (the router does not consider other lan boxes to be external to any given lan box). To effectively use the dmz one MUST use multiple firewalls.

This is not correct.

Some cheap routers implement a shoddy DMZ.  Let's not confuse a weak DMZ implementation from a robust one.  A robust DMZ is protected by the firewall as well.

MrC

---

### Post by Mr. C. on 2007-03-17
jenhsun,

First, your php is stil not accessible here.

If you believe that phpinfo() is blocked, use another statement instead, such as print.  If this also does not work, the problem is with your PHP setup.

If the print does work, then you can assume this is a problem with phpinfo(). 

One change in the recent PHP build (5.2.1) is :

> Added a meta tag to phpinfo() output to prevent search engines from indexing 
  the page. (Ilia)

Perhaps this is causing problems with your router or ISP.  I deb debug by removing any intermediate router(s) for a quick test, connecting your system directly to your modem.  I would also do a packet trace to see if your server is providing any response to the php commands (but the print test above may obviate the need for this test).

Here is the entire change list of PHP:

[http://www.php.net/ChangeLog-5.php](http://www.php.net/ChangeLog-5.php)

Here is the manual for phpinfo()
[http://us3.php.net/manual/en/function.phpinfo.php](http://us3.php.net/manual/en/function.phpinfo.php)

MrC

---

### Post by jenhsun on 2007-03-17
> **Mr. C. said:**
> jenhsun,

First, your php is stil not accessible here.

If you believe that phpinfo() is blocked, use another statement instead, such as print.  If this also does not work, the problem is with your PHP setup.

If the print does work, then you can assume this is a problem with phpinfo(). 

One change in the recent PHP build (5.2.1) is :



Perhaps this is causing problems with your router or ISP.  I deb debug by removing any intermediate router(s) for a quick test, connecting your system directly to your modem.  I would also do a packet trace to see if your server is providing any response to the php commands (but the print test above may obviate the need for this test).

Here is the entire change list of PHP:

[http://www.php.net/ChangeLog-5.php](http://www.php.net/ChangeLog-5.php)

Here is the manual for phpinfo()
[http://us3.php.net/manual/en/function.phpinfo.php](http://us3.php.net/manual/en/function.phpinfo.php)

MrC

Great, Mr C. I don't know why Tturrisi can see my test.php but not you.
I already do the code to:

```
<?php
phpinfo(INFO_LICENCE);
?>
```

So it will only show the php licence. I hope you can see it.
It's good to have your help and suggestion.

---

### Post by tturrisi on 2007-03-17
verified

---

### Post by tturrisi on 2007-03-17
> **Mr. C. said:**
> This is not correct.

Some cheap routers implement a shoddy DMZ.  Let's not confuse a weak DMZ implementation from a robust one.  A robust DMZ is protected by the firewall as well.

MrC
agreed!
the majority of home routers employ what is called a dmz host feature, not a true dmz.  (more of a marketing term than a real dmz)  dmz host allows lan connections from clients whereas a true dmz only allows connections to the wan or a designated external network.  Such routers usually also employ spi as well as editable rulesets and editable routing tables.

---

### Post by jenhsun on 2007-03-17
> **tturrisi said:**
> verified

Thank you, Tturrisi. How about you, Mr C?

---

### Post by Mr. C. on 2007-03-17
Nope.

---

### Post by jenhsun on 2007-03-17
> **Mr. C. said:**
> Nope.

I really don't know why. Can you see my html file?
What if yours or my ISP blocks the IP address?
I am really don't know.

---

### Post by Mr. C. on 2007-03-17
You are the only person who can tell if MY requests reach your server, and if YOUR server sends out all the correct data.  You need to trace the packets using something like tcpdump.

My ISP is not blocking php requests to or from your site.  I can see and retrieve your index.html.

I do not know if you have yet followed my advice to verify or reject your assumption that phpinfo() is being rejected or causing problems, or if a simple print within php works for everyone.

MrC

---

### Post by jenhsun on 2007-03-17
> **Mr. C. said:**
> You are the only person who can tell if MY requests reach your server, and if YOUR server sends out all the correct data.  You need to trace the packets using something like tcpdump.

My ISP is not blocking php requests to or from your site.  I can see and retrieve your index.html.

I do not know if you have yet followed my advice to verify or reject your assumption that phpinfo() is being rejected or causing problems, or if a simple print within php works for everyone.

MrC

OK, Mr C. 
I follow your suggestion about the dcpdump

```
tcpdump -vv port 80 > /var/log/tcplog.txt
```

I hope it is right.
Now you can test again. Sorry to bother your for me.
I will post to here after 30 mins

---

### Post by nix4me on 2007-03-17
Your php link does not work.  Are you sure you have php installed correctly?  Does the default apache show php enabled?

nix4me

---

### Post by jenhsun on 2007-03-17
Ok, here is my TCPDUMP log

```
03:21:39.456540 IP (tos 0x0, ttl  49, id 58679, offset 0, flags [DF], proto: TCP (6), length: 60) crawl-66-249-65-112.googlebot.com.55397 > jenhsun.homeip.net.www: S, cksum 0x9d52 (correct), 3436869932:3436869932(0) win 5720 <mss 1430,sackOK,timestamp 2491980827 0,nop,wscale 0>
03:21:39.459616 IP (tos 0x0, ttl  64, id 0, offset 0, flags [DF], proto: TCP (6), length: 60) jenhsun.homeip.net.www > crawl-66-249-65-112.googlebot.com.55397: S, cksum 0x5db4 (correct), 1197264533:1197264533(0) ack 3436869933 win 5792 <mss 1460,sackOK,timestamp 76082 2491980827,nop,wscale 2>
03:21:39.706920 IP (tos 0x0, ttl  49, id 58680, offset 0, flags [DF], proto: TCP (6), length: 52) crawl-66-249-65-112.googlebot.com.55397 > jenhsun.homeip.net.www: ., cksum 0x8caa (correct), 1:1(0) ack 1 win 5720 <nop,nop,timestamp 2491980852 76082>
03:21:39.707382 IP (tos 0x0, ttl  49, id 58681, offset 0, flags [DF], proto: TCP (6), length: 303) crawl-66-249-65-112.googlebot.com.55397 > jenhsun.homeip.net.www: P 1:252(251) ack 1 win 5720 <nop,nop,timestamp 2491980852 76082>
03:21:39.707400 IP (tos 0x0, ttl  64, id 59357, offset 0, flags [DF], proto: TCP (6), length: 52) jenhsun.homeip.net.www > crawl-66-249-65-112.googlebot.com.55397: ., cksum 0x9b3a (correct), 1:1(0) ack 252 win 1716 <nop,nop,timestamp 76107 2491980852>
03:21:39.708516 IP (tos 0x0, ttl  64, id 59358, offset 0, flags [DF], proto: TCP (6), length: 582) jenhsun.homeip.net.www > crawl-66-249-65-112.googlebot.com.55397: P 1:531(530) ack 252 win 1716 <nop,nop,timestamp 76108 2491980852>
03:21:39.964757 IP (tos 0x0, ttl  49, id 58682, offset 0, flags [DF], proto: TCP (6), length: 52) crawl-66-249-65-112.googlebot.com.55397 > jenhsun.homeip.net.www: ., cksum 0x86a1 (correct), 252:252(0) ack 531 win 6432 <nop,nop,timestamp 2491980878 76108>
03:21:39.968848 IP (tos 0x0, ttl  49, id 58683, offset 0, flags [DF], proto: TCP (6), length: 284) crawl-66-249-65-112.googlebot.com.55397 > jenhsun.homeip.net.www: P 252:484(232) ack 531 win 6432 <nop,nop,timestamp 2491980878 76108>
03:21:40.000672 IP (tos 0x0, ttl  64, id 59359, offset 0, flags [DF], proto: TCP (6), length: 1470) jenhsun.homeip.net.www > crawl-66-249-65-112.googlebot.com.55397: . 531:1949(1418) ack 484 win 1984 <nop,nop,timestamp 76137 2491980878>
03:21:40.000697 IP (tos 0x0, ttl  64, id 59360, offset 0, flags [DF], proto: TCP (6), length: 685) jenhsun.homeip.net.www > crawl-66-249-65-112.googlebot.com.55397: P 1949:2582(633) ack 484 win 1984 <nop,nop,timestamp 76137 2491980878>
03:21:40.280342 IP (tos 0x0, ttl  49, id 58684, offset 0, flags [DF], proto: TCP (6), length: 52) crawl-66-249-65-112.googlebot.com.55397 > jenhsun.homeip.net.www: ., cksum 0x6a4a (correct), 484:484(0) ack 2582 win 11344 <nop,nop,timestamp 2491980909 76137>
03:21:49.565031 IP (tos 0x0, ttl  49, id 58685, offset 0, flags [DF], proto: TCP (6), length: 52) crawl-66-249-65-112.googlebot.com.55397 > jenhsun.homeip.net.www: F, cksum 0x66a8 (correct), 484:484(0) ack 2582 win 11344 <nop,nop,timestamp 2491981838 76137>
03:21:49.565188 IP (tos 0x0, ttl  64, id 59361, offset 0, flags [DF], proto: TCP (6), length: 52) jenhsun.homeip.net.www > crawl-66-249-65-112.googlebot.com.55397: F, cksum 0x877b (correct), 2582:2582(0) ack 485 win 1984 <nop,nop,timestamp 77093 2491981838>
03:21:49.812847 IP (tos 0x0, ttl  49, id 58686, offset 0, flags [DF], proto: TCP (6), length: 52) crawl-66-249-65-112.googlebot.com.55397 > jenhsun.homeip.net.www: ., cksum 0x62d2 (correct), 485:485(0) ack 2583 win 11344 <nop,nop,timestamp 2491981863 77093>
03:44:57.401053 IP (tos 0x0, ttl  42, id 43583, offset 0, flags [DF], proto: TCP (6), length: 60) 29.85.33.65.cfl.res.rr.com.51097 > jenhsun.homeip.net.www: S, cksum 0x6c45 (correct), 2044062369:2044062369(0) win 5840 <mss 1460,sackOK,timestamp 16924830 0,nop,wscale 2>
03:44:57.418354 IP (tos 0x0, ttl  64, id 0, offset 0, flags [DF], proto: TCP (6), length: 60) jenhsun.homeip.net.www > 29.85.33.65.cfl.res.rr.com.51097: S, cksum 0x53d7 (correct), 2683776333:2683776333(0) ack 2044062370 win 5792 <mss 1460,sackOK,timestamp 215877 16924830,nop,wscale 2>
03:44:57.686975 IP (tos 0x0, ttl  42, id 43584, offset 0, flags [DF], proto: TCP (6), length: 52) 29.85.33.65.cfl.res.rr.com.51097 > jenhsun.homeip.net.www: ., cksum 0x9343 (correct), 1:1(0) ack 1 win 1460 <nop,nop,timestamp 16924901 215877>
03:44:57.694503 IP (tos 0x0, ttl  42, id 43585, offset 0, flags [DF], proto: TCP (6), length: 537) 29.85.33.65.cfl.res.rr.com.51097 > jenhsun.homeip.net.www: P 1:486(485) ack 1 win 1460 <nop,nop,timestamp 16924901 215877>
03:44:57.694526 IP (tos 0x0, ttl  64, id 26159, offset 0, flags [DF], proto: TCP (6), length: 52) jenhsun.homeip.net.www > 29.85.33.65.cfl.res.rr.com.51097: ., cksum 0x9041 (correct), 1:1(0) ack 486 win 1716 <nop,nop,timestamp 215906 16924901>
03:44:57.702543 IP (tos 0x0, ttl  64, id 26160, offset 0, flags [DF], proto: TCP (6), length: 489) jenhsun.homeip.net.www > 29.85.33.65.cfl.res.rr.com.51097: P 1:438(437) ack 486 win 1716 <nop,nop,timestamp 215907 16924901>
03:44:57.976603 IP (tos 0x0, ttl  42, id 43586, offset 0, flags [DF], proto: TCP (6), length: 52) 29.85.33.65.cfl.res.rr.com.51097 > jenhsun.homeip.net.www: ., cksum 0x8e36 (correct), 486:486(0) ack 438 win 1728 <nop,nop,timestamp 16924974 215907>
03:44:58.046666 IP (tos 0x0, ttl  42, id 43587, offset 0, flags [DF], proto: TCP (6), length: 399) 29.85.33.65.cfl.res.rr.com.51097 > jenhsun.homeip.net.www: P 486:833(347) ack 438 win 1728 <nop,nop,timestamp 16924990 215907>
03:44:58.047130 IP (tos 0x0, ttl  64, id 26161, offset 0, flags [DF], proto: TCP (6), length: 582) jenhsun.homeip.net.www > 29.85.33.65.cfl.res.rr.com.51097: P 438:968(530) ack 833 win 1984 <nop,nop,timestamp 215941 16924990>
03:44:58.322472 IP (tos 0x0, ttl  42, id 43588, offset 0, flags [DF], proto: TCP (6), length: 52) 29.85.33.65.cfl.res.rr.com.51097 > jenhsun.homeip.net.www: ., cksum 0x8944 (correct), 833:833(0) ack 968 win 1996 <nop,nop,timestamp 16925061 215941>
03:45:06.772104 IP (tos 0x0, ttl  42, id 43589, offset 0, flags [DF], proto: TCP (6), length: 476) 29.85.33.65.cfl.res.rr.com.51097 > jenhsun.homeip.net.www: P 833:1257(424) ack 968 win 1996 <nop,nop,timestamp 16927171 215941>
03:45:06.773900 IP (tos 0x0, ttl  64, id 26162, offset 0, flags [DF], proto: TCP (6), length: 1500) jenhsun.homeip.net.www > 29.85.33.65.cfl.res.rr.com.51097: . 968:2416(1448) ack 1257 win 2252 <nop,nop,timestamp 216814 16927171>
03:45:06.773923 IP (tos 0x0, ttl  64, id 26163, offset 0, flags [DF], proto: TCP (6), length: 655) jenhsun.homeip.net.www > 29.85.33.65.cfl.res.rr.com.51097: P 2416:3019(603) ack 1257 win 2252 <nop,nop,timestamp 216814 16927171>
03:45:07.052443 IP (tos 0x0, ttl  42, id 43590, offset 0, flags [DF], proto: TCP (6), length: 64) 29.85.33.65.cfl.res.rr.com.51097 > jenhsun.homeip.net.www: ., cksum 0x993b (correct), 1257:1257(0) ack 968 win 1996 <nop,nop,timestamp 16927242 215941,nop,nop,sack 1 {2416:3019}>
03:45:07.567323 IP (tos 0x0, ttl  64, id 26164, offset 0, flags [DF], proto: TCP (6), length: 1500) jenhsun.homeip.net.www > 29.85.33.65.cfl.res.rr.com.51097: . 968:2416(1448) ack 1257 win 2252 <nop,nop,timestamp 216893 16927242>
03:45:09.147262 IP (tos 0x0, ttl  64, id 26165, offset 0, flags [DF], proto: TCP (6), length: 1500) jenhsun.homeip.net.www > 29.85.33.65.cfl.res.rr.com.51097: . 968:2416(1448) ack 1257 win 2252 <nop,nop,timestamp 217051 16927242>
03:45:12.307149 IP (tos 0x0, ttl  64, id 26166, offset 0, flags [DF], proto: TCP (6), length: 1500) jenhsun.homeip.net.www > 29.85.33.65.cfl.res.rr.com.51097: . 968:2416(1448) ack 1257 win 2252 <nop,nop,timestamp 217367 16927242>
03:45:18.626915 IP (tos 0x0, ttl  64, id 26167, offset 0, flags [DF], proto: TCP (6), length: 1500) jenhsun.homeip.net.www > 29.85.33.65.cfl.res.rr.com.51097: . 968:2416(1448) ack 1257 win 2252 <nop,nop,timestamp 217999 16927242>
03:45:21.776892 IP (tos 0x0, ttl  64, id 26168, offset 0, flags [DF], proto: TCP (6), length: 52) jenhsun.homeip.net.www > 29.85.33.65.cfl.res.rr.com.51097: F, cksum 0x6cce (correct), 3019:3019(0) ack 1257 win 2252 <nop,nop,timestamp 218314 16927242>
03:45:22.042466 IP (tos 0x0, ttl  42, id 43591, offset 0, flags [DF], proto: TCP (6), length: 64) 29.85.33.65.cfl.res.rr.com.51097 > jenhsun.homeip.net.www: ., cksum 0x8a96 (correct), 1257:1257(0) ack 968 win 1996 <nop,nop,timestamp 16930990 215941,nop,nop,sack 1 {2416:3020}>
03:45:30.034265 IP (tos 0x0, ttl  42, id 43592, offset 0, flags [DF], proto: TCP (6), length: 64) 29.85.33.65.cfl.res.rr.com.51097 > jenhsun.homeip.net.www: F, cksum 0x82c7 (correct), 1257:1257(0) ack 968 win 1996 <nop,nop,timestamp 16932988 215941,nop,nop,sack 1 {2416:3020}>
03:45:30.034287 IP (tos 0x0, ttl  64, id 26169, offset 0, flags [DF], proto: TCP (6), length: 52) jenhsun.homeip.net.www > 29.85.33.65.cfl.res.rr.com.51097: ., cksum 0x5321 (correct), 3020:3020(0) ack 1258 win 2252 <nop,nop,timestamp 219140 16932988>
03:45:31.266454 IP (tos 0x0, ttl  64, id 26170, offset 0, flags [DF], proto: TCP (6), length: 1500) jenhsun.homeip.net.www > 29.85.33.65.cfl.res.rr.com.51097: . 968:2416(1448) ack 1258 win 2252 <nop,nop,timestamp 219263 16932988>
03:45:56.545532 IP (tos 0x0, ttl  64, id 26171, offset 0, flags [DF], proto: TCP (6), length: 1500) jenhsun.homeip.net.www > 29.85.33.65.cfl.res.rr.com.51097: . 968:2416(1448) ack 1258 win 2252 <nop,nop,timestamp 221791 16932988>
03:46:47.103679 IP (tos 0x0, ttl  64, id 26172, offset 0, flags [DF], proto: TCP (6), length: 1500) jenhsun.homeip.net.www > 29.85.33.65.cfl.res.rr.com.51097: . 968:2416(1448) ack 1258 win 2252 <nop,nop,timestamp 226847 16932988>
03:48:28.219967 IP (tos 0x0, ttl  64, id 26173, offset 0, flags [DF], proto: TCP (6), length: 1500) jenhsun.homeip.net.www > 29.85.33.65.cfl.res.rr.com.51097: . 968:2416(1448) ack 1258 win 2252 <nop,nop,timestamp 236959 16932988>
```

Mr C, Indeed some other people have the same problem as yours.
Could you help me take a look at the log?

I also create a single "hello world" php by [http://jenhsun.homeip.net/test2.php](http://jenhsun.homeip.net/test2.php)

```
<?php
echo "Hello World";
?>
```

Anyway please test my server and tell me you can see it or not.

---

### Post by jenhsun on 2007-03-17
> **nix4me said:**
> Your php link does not work.  Are you sure you have php installed correctly?  Does the default apache show php enabled?

nix4me

I think so. I can see the php from the other pc.
Help me solve the problem, please...

---

### Post by Nikron on 2007-03-17
I can see test2.php

---

### Post by jenhsun on 2007-03-17
> **Nikron said:**
> I can see test2.php

Thank you, Nikron.
Anyone?

---

### Post by Mr. C. on 2007-03-17
I can also receive your test2.php file.

MrC

---

### Post by jenhsun on 2007-03-17
> **Mr. C. said:**
> I can also receive your test2.php file.

MrC

Thank you, Mr C.
So what do you think about the problem on phpinfo()? Some testers said they can see my test.php, but some can't.
I am afraid that if my php file get more complicated in the future, people might not be able to see it.

---

### Post by Mr. C. on 2007-03-17
If you would like me to test your phpinfo script, I will tcpdump to be run  as:

```
tcpdump host 204.11.230.89  -i lo -w /tmp/tcpdump.out
```

If your WAN interface is not eth0, change the interface above to the correct interface.

Leave tcpdump running until I indicate that I have attempted the connection.  This configuration of tcpdump will only capture my traffic, so you do not have to worry about running tcpdump too long.

Once that capture is done, you can <Control>-C to stop it, and then you can send it to me via the address I leave in your private message.  Before you send it, gzip the file with :

gzip /tmp/tcpdump.out 

The new file name will be /tmp/tcpdump.out.gz

MrC

---

### Post by jenhsun on 2007-03-17
OK, Mr C
I do

```
tcpdump host 204.11.230.89 -i eth1 -w /var/log/tcpdump.out
```

I am ready.
Thank you, Mr C

---

### Post by Mr. C. on 2007-03-17
Ok, you can kill the tcpdump now. I have attempted the connection.

Be sure it says it captured some packets.  

If you can gzip and include in a PM that would work fine, should mail not work.

MrC

---

### Post by Mr. C. on 2007-03-17
Our packet captures show that after the initial connection and GET request, subsequent packets from your system are corrupt.  This is likely a NIC problem, or driver problem. 
Checksum: 0x78e4 [incorrect, should be 0xe357 (maybe caused by "TCP checksum offload"?)]

Your NIC may have the ability to perform TCP checksums in hardware.  If this is true, and it is not calculating the checksum correctly, you may need to disable this feature by passing certain options to your NIC driver.

You may need to update the driver for your NIC(s) (which may mean a kernel upgrade).

There is also a possibility that your NIC hardware is bad, but this seems less likely.

MrC

---

### Post by jenhsun on 2007-03-17
> **Mr. C. said:**
> Our packet captures show that after the initial connection and GET request, subsequent packets from your system are corrupt.  This is likely a NIC problem, or driver problem. 
Checksum: 0x78e4 [incorrect, should be 0xe357 (maybe caused by "TCP checksum offload"?)]

Your NIC may have the ability to perform TCP checksums in hardware.  If this is true, and it is not calculating the checksum correctly, you may need to disable this feature by passing certain options to your NIC driver.

You may need to update the driver for your NIC(s) (which may mean a kernel upgrade).

There is also a possibility that your NIC hardware is bad, but this seems less likely.

MrC

What if I change to eth0 now. That's my another ethernet card in my pc but doesn't plugin anything.
Anyway, I am switching now. Then you can testing it again.

---

### Post by jenhsun on 2007-03-17
OK, Mr C
I already switch to eth0, there is another Ethernet card in my pc server.
And I test from internal to [http://jenhsun.homeip.net/test.php](http://jenhsun.homeip.net/test.php), test2.php all ok.

And also I start tcpdump now for you.

By the way, that's a big surprise. I never thought that it was my kernel problem.
How professional to do the tcp checksum checking.

---

### Post by Mr. C. on 2007-03-17
Same problem.

Time to upgrade the firmware on your router.  Check your vendor's site for upgrades.

MrC

---

### Post by jenhsun on 2007-03-17
OK, Mr C.
I will try to fix the router problem, or maybe to buy a new one I think.
Anyway, Thank you so much for wasting time on testing my site.
After I fix all the other day, I will let you know that I am ok for you.
Thank you, Mr C

---

### Post by Mr. C. on 2007-03-17
This was a good challenge.  Let us know how it turns out.  I'm betting just a firmware upgrade will solve the problem.

Best of luck.,
MrC

---

### Post by tturrisi on 2007-03-18
I see the phpinfo just fine.

---

### Post by jenhsun on 2007-03-18
> **tturrisi said:**
> I see the phpinfo just fine.

Thank you, Tturrisi.
Currently I use the newest router that I bought today.
Previous router did have problem after Mr C had test with me.
He wanted me to use tcpdump and check the tcp packet checksum detail about how my router react. And that is so so so coool. He told me that might be the router's firmware problem. However, my firmware is newest one. And I also found some people talked about this router's question from some other hardware sites. So I decide to change to a new one. After that, I use my external link to my site is BINGO, everything is fine now. Days ago I even can't link to my site from my external link. 
Mr C is the man, trust me.

---

### Post by Mr. C. on 2007-03-18
jenhsun,

Please share with others the router model number, version, and firmware revision so that other's may benefit also.  Search engines will find these posts and the problem.

I believe your router is incorrectly handling TCP checksums when NAT is enabled.  This is why the problem appears only from outside.  NAT must recalculate the TCP checksum, since it changes some portions of the packet headers.  The router company will be able to determine exactly what is wrong, especially with your data.  They can (and hopefully will) provide updated firmware to resolve this.

Best wishes,
MrC

---

### Post by jenhsun on 2007-03-18
No Problem, Mr C.



ROUTER TYPE: Netgear WGT 624.v2
FIRMWARE: v.4.2.11
PROBLEM: Incorrectly handling TCP checksums when NAT is enabled.


If anyone who has trouble when sometimes people can visit to your server but sometimes can't. Not sure why your html page can be seen but not php file. It might be your router's firmware problem. Make sure your firmware up to date. And do a tcpdump with your friend for testing.

You can do this command in your testing server terminal:

```
tcpdump host yourfriendIP -i yournetworkinterface -s 0 -w yourlogfile.txt
```

Then do a checksum for your yourlogfile.txt

---

