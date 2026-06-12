---
title: "apache2 problem"
date: 2008-10-19
forum: Server Platforms
---

### Post by trevelyn on 2008-10-19
HI, this is Trevelyn from WeakNet Labs.  Recently I started working on a customized OS for our group and decided to use Ubuntu cos everyone here at the Lab loves Ubuntu.  We focus on network and social security and work soley within our lab here. - sorry for the disclaimer. heh.  Well, I tried all of the remastering programs and only found ONE to work, - Remastersys

I have Apache2 and PHP-5 installed cos I have a webpage that can be started and worked with, that refers to php scripts, but built on html.  

My problem is, the box that i am developing on (writing the code, installing things, etc) works great! I have referrers to scripts that start and stop the apache2 server in the applications menu.  But after the Remastersys process, I send the ISO to another machine, burn it, and then boot into it on the other machine.  Then start the Apache2 server, it starts up fine, nmap shows the port open and all on 127.0.0.1 (even though it says i have a screwy hostname and is using 127.0.1.1) ps aux shows the process running as "apache2ctrl -k start" and i can even browse to it via firefox and not get any error page.  

but that's just the thing, i don't get anything at all!  Its a blank page!
Im not sure what the issue could be i have compared th error logs between the development box and the live cd.

Here is the output of my /var/log/apache2/error.log 
========================================================
[Sun Oct 19 02:33:00 2008] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Sun Oct 19 02:33:18 2008] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Sun Oct 19 02:33:21 2008] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Sun Oct 19 02:39:13 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sun Oct 19 02:39:18 2008] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Sun Oct 19 02:39:19 2008] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sun Oct 19 02:39:19 2008] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Sun Oct 19 02:40:24 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sun Oct 19 02:40:27 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Sun Oct 19 02:40:42 2008] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Sun Oct 19 02:40:42 2008] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Sun Oct 19 02:41:23 2008] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Sun Oct 19 02:41:23 2008] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Sun Oct 19 02:41:25 2008] [error] [client 127.0.0.1] File does not exist: /var/www/phishing/google_transparent.gif, referer: [http://127.0.0.1/phishing/gmail.html](http://127.0.0.1/phishing/gmail.html)
[Sun Oct 19 02:41:54 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sun Oct 19 02:42:12 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Sun Oct 19 15:27:28 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Sun Oct 19 15:28:00 2008] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Sun Oct 19 15:28:03 2008] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Sun Oct 19 15:29:35 2008] [notice] caught SIGWINCH, shutting down gracefully
===========================================================

/etc/apache2/httpd.conf is blank.

/etc/apache2/ports.conf:
===========================================================
Listen 80

<IfModule mod_ssl.c>
    Listen 443
</IfModule>
============================================================

What I want is the user to be able to start the Apache2 server from the main menu, I have tried sudo, su, etc.. all turns out BLANK.

EDIT: 
Oh! another thing i want to add!! If i do this:
> 
cp -R /var/www/* /home/assistant/Desktop/backup-www/
rm -rf /var/www/*
touch /var/www/index.html
echo LOL HI MAN > /var/www/index.html

then browse to it in firefox,
I can see "LOL HI MAN" on [http://127.0.0.1/](http://127.0.0.1/) 
!!

EDIT:
I found something else particularly interesting!  I can do:

> firefox index.html

from the /var/www/ directory and it comes up fine!!

Thanks in advance - Trevelyn.

---

### Post by trevelyn on 2008-10-19
ufw disbaled, checked iptables the policies are all set to ACCEPT.


if i remove all of the html tags and make it a txt file, firefox STILL will not show it, ... if i create a new file and put html in it, it's fine.  if i copy html from a website and echo the source into the index.html > overwriting it all, the same thing happens, - blank pages. ??? i cant figure this out, i have searched google for too long, ive compared config files with the development box and the live cd, i just dont get it.. why would
> firefox index.html
be different from 
> firefox [http://127.0.0.1](http://127.0.0.1)
?
and why would the server not report errors in the log as i try to surf to it??  i feel like im in the remastersys twilight zone!! D:

---

### Post by bodhi.zazen on 2008-10-19
Seems to bw working normally as far as I can tell from what you posted.

See if this helps :

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by trevelyn on 2008-10-19
thanks for the link:
> /etc/php5/apache2/php.ini  
resource is set to 64MB
> sudo nano /etc/apache2/conf.d/fqdn
now contains "Servername localhost" that solves the 127.0.1.1 complaint :D
> Search both the strings starting by "User" and "Group", and change the names by the current username and groupname you are using. Then you'll need to restart Apache. (look at the next chapter concerning apache commands)
should that say www-data, or my user anem (assistant), or ${APACHE_RUN_USER}?
> rm index.html && echo ' <?php phpinfo(); ?>' > index.php
works fine, shows a cool php info page


Here's my HTML
> <html><body><h1>WeakNet Linux Apache2 Is Up :-)</h1></body></html>
<br>WeakNet Linux's Built-In Apache2 Server!<br>
To Edit this page and put something fancy, sneaky, or sexy<br>
Edit the file "/var/www/index.html" as root or use "sudo" :-) <br><br><br><br>
Categories of built in sites:
<h1> WeakNet Labs' Web-Hacking Portal </h1><br>
Click <a href="http://127.0.0.1/phishing/index.html">Here</a> to enter the Web Hacking Portal, Please, see the disclaimer at the bottom of the page!
<br><br><br>

2008/2009 WeakNet Labs <a href="http://weaknetLabs.com">WeakNetLabs.com</a><br> 

This code works great! ..on the installed system, but not at all on the live cd after running remastersys.
the code is the same. i don't see how anything could have changed..

i will keep bashing away at it, no pun intended.  please if you have any more ideas, feel free to send them here! 

- thanks - trevelyn.

Oh, not sure if this helps: i did
find . * | grep rc | grep -i apache
in /etc and removed all of the entries, because i dont want the webserver to start automatically, was i not supposed to do that? i thought the rcN.XNNapache2 files were just for starting up automatically.
and this hasn't affected the development box (at all after several reboots)
thanks.

---

### Post by trevelyn on 2008-10-19
okay something new has come up
I started writing the index.html file line by line and checking the web page   as i go along, 

as it turns out, everything is fine, until i hit line 5.  Then, the page goes blank!!!

EDIT:
scratch that!  The file can only be 256k in size :( (i kept adding 1 char to it until it died) what's going on!?

---

### Post by ju2wheels on 2008-10-19
> **trevelyn said:**
> ufw disbaled, checked iptables the policies are all set to ACCEPT.


if i remove all of the html tags and make it a txt file, firefox STILL will not show it, ... if i create a new file and put html in it, it's fine.  if i copy html from a website and echo the source into the index.html > overwriting it all, the same thing happens, - blank pages. ??? i cant figure this out, i have searched google for too long, ive compared config files with the development box and the live cd, i just dont get it.. why would

be different from 

?
and why would the server not report errors in the log as i try to surf to it??  i feel like im in the remastersys twilight zone!! D:

I think you are misunderstanding how the web server works.

You should never check how your web pages are working by loading the files locally (aka running 'firefox index.html'), especially if they have scripted code like php. 

The reason is that these files will never be sent through Apache for processing. In order for this to happen you have to access them through Apache by requesting it from port 80 (aka accessing it from [http://127.0.0.1](http://127.0.0.1) only if you are on the machine running Apache or the actual IP of the machine running Apache if you are on another computer on the network).

If you are trying to run a page with PHP code in it and get a blank page, then you have an error in your code most likely. Be sure to enable the error log in the PHP config file in order to be able to track down the error. I dont think theres anything wrong with your Apache setup, but rather a problem with how you are trying to access the files.

---

### Post by ju2wheels on 2008-10-19
> **trevelyn said:**
> thanks for the link:
  </body></html>
resource is set to 64MB

now contains "Servername localhost" that solves the 127.0.1.1 complaint :D

should that say www-data, or my user anem (assistant), or ${APACHE_RUN_USER}?

works fine, shows a cool php info page


Here's my HTML


This code works great! ..on the installed system, but not at all on the live cd after running remastersys.
the code is the same. i don't see how anything could have changed..

i will keep bashing away at it, no pun intended.  please if you have any more ideas, feel free to send them here! 

- thanks - trevelyn.

Oh, not sure if this helps: i did
find . * | grep rc | grep -i apache
in /etc and removed all of the entries, because i dont want the webserver to start automatically, was i not supposed to do that? i thought the rcN.XNNapache2 files were just for starting up automatically.
and this hasn't affected the development box (at all after several reboots)
thanks.

This html is incorrectly written. Here is the corrected version:
```

<html>
   <body>
     <h1>WeakNet Linux Apache2 Is Up :-)</h1>
     <br />WeakNet Linux's Built-In Apache2 Server!<br />
To Edit this page and put something fancy, sneaky, or sexy<br />
Edit the file "/var/www/index.html" as root or use "sudo" :-) <br /><br /><br /><br />
Categories of built in sites:
<h1> WeakNet Labs' Web-Hacking Portal </h1><br />
Click <a href="http://127.0.0.1/phishing/index.html">Here</a> to enter the Web Hacking Portal, Please, see the disclaimer at the bottom of the page!
<br /><br /><br />

2008/2009 WeakNet Labs <a href="http://weaknetLabs.com">WeakNetLabs.com</a><br /> 
</body></html>
```

Also be aware that when you browse to [http://127.0.0.1/](http://127.0.0.1/) or any subfolder, the first file that gets loaded by default is the index.html file in that folder, so if that is empty, you will see a blank page.

---

### Post by trevelyn on 2008-10-19
no no, i completely understand, look this is what happens ready?

machine 1: Ubuntu Live CD 8.04 
> ifconfig | grep "inet addr"
 10.10.10.24
apt-get update (after uncommenting out the lines in sources.list)
apt-get install apache2 libapache2-mod-php5
cd /var/www/ && cat index.html
>   It Works!

Computer 2: ANYTHING
open firefox surf to 10.10.10.24
and see > "It Works!"

Machine 1: Ubuntu with Apache 8.04
> echo <a href="http://google.com">Click Here for Google!</a> >> index.html

Machine 2: F5 Refresh, see "It Works!" and 1 link

Machine 1: Ubuntu with Apache 8.04
> echo <a href="http://google.com">Click Here for Google!</a> >> index.html

Machine 2: F5 Refresh, see "It Works!" and 2 links

> echo <a href="http://google.com">Click Here for Google!</a> >> index.html

Machine 2: F5 Refresh, see "It Works!" and 3 links

> echo <a href="http://google.com">Click Here for Google!</a> >> index.html

Machine 2: F5 Refresh, see **NOTHING.** No source code when Ctrl+U either

is that more clear?

---

### Post by ju2wheels on 2008-10-19
Ive never had this happen before but found a similar old thread here [http://www.webmasterworld.com/forum92/2894.htm](http://www.webmasterworld.com/forum92/2894.htm) .

What is your /etc/apache2/apache2.conf configured to and what files are listed in /etc/apache2/sites-enabled and /etc/apache2/mods-enabled. Did you customize any files in /etc/apache2 at all?

---

### Post by trevelyn on 2008-10-19
> **ju2wheels said:**
> Ive never had this happen before but found a similar old thread here [http://www.webmasterworld.com/forum92/2894.htm](http://www.webmasterworld.com/forum92/2894.htm) .

What is your /etc/apache2/apache2.conf configured to and what files are listed in /etc/apache2/sites-enabled and /etc/apache2/mods-enabled. Did you customize any files in /etc/apache2 at all?

no, not in the live cd and not after the live cd install.  The live cd install works flawlessly. im banging my head on the desk now. i mean, im going to the link you posted...

---

### Post by trevelyn on 2008-10-19
i guess what i could do is take it off of the package list and leave my php and html scripts in the /var/www directory.  And tell them they can use them on the OS once it has been installed, or on anyother installed system, just not the live system.  If all else fails i could just do that.  kind of a bummer.  There's other security themed distros out there that have apache that runs from the live disk, like BT3, but BT3 is Slax based.  

one question though, i noticed when i 

```
apt-get remove --purge apache2 libapache2-mod-php
```

that the config files stay all over the place esp. in /etc/apache/, will that muck up someone else's install? if they install from the live cd and use aptitude to install apache2?  

and hey, :neutral: thanks for all the help man.

---

### Post by ju2wheels on 2008-10-19
You should be able to uninstall the leftover config files from synaptic, it typically has them listed under their own category (I think its called residual config, I dont remember). 

If not I dont see it being much of a problem, if those files are not overwritten when they install apache then you can just run a dpkg-reconfigure on it.

---

### Post by trevelyn on 2008-10-27
well, my friend godot fixed the issue, turns out that the line

> EnableSendFile Off

needed to be in the apache2 configuration file, now they both work fine even from the Live CD.  Thanks for all your help.  I built WeakNet Linux off of Hardy and used the regular repos provided to install apache2, so if anyone else ever see's this issue, that's how we fixed it. :)

---

