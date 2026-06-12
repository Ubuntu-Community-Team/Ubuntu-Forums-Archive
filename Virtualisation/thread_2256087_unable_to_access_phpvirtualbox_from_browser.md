---
title: "unable to access phpvirtualbox from browser"
date: 2014-12-09
forum: Virtualisation
---

### Post by AnthonyHorner on 2014-12-09
Hi all,

A complete newbie here (although I may have logged on here several years ago when I first had a look at ubuntu), following the instructions to create a headless home server from this site [linux home server guide]("http://linuxhomeserverguide.com/")

I'm on this [page]("http://linuxhomeserverguide.com/server-config/phpVirtualBox.php") and at the bottom, the text prompts me to point to the hostname/phpvirtualbox/.  When I do this I get a 404 Not Found

[I]The requested URL /phpvirtualbox/ was not found on this server.

Apache/2.4.7 (Ubuntu) Server at server-main Port 80[/I]

I have the following installed:

Ubuntu 14.04.1 LTS
virtualbox-4.3.20
phpvirtualbox-4.2.6

According to [SourceForge Common Errors & Issues page]("https://sourceforge.net/p/phpvirtualbox/wiki/Common%20phpVirtualBox%20Errors%20and%20Issues/") not being able to connect to the host is due to 3 possible issues:
1)  Either the location setting in config.php is wrong,
2) vboxwebsrv is not running on the VirtualBox host,
3) SELinux is blocking access to vboxwebsrv

I don't have SELinux so it's between 1 and 2.  My config.php file (from following the instruction; so in this location /var/www/phpvirtualbox) contains:

[I]/* Username / Password for system user that runs VirtualBox */
var $username = 'vboxuser';
var $password = 'vbox';

/* SOAP URL of vboxwebsrv (not phpVirtualBox's URL) */
var $location = 'http://127.0.0.1:18083/';[/I]

Note: I've only ever changed the values for the username and password in this file.

The user is the same I set up in the /etc/default/virtualbox file:

*VBOXWEB_USER=vboxuser*

According to the errors and issues page from sourceforge page above, the location is set correctly, they also mention here in their basic configuration section that "If VirtualBox and phpVirtualBox are on the same physical host, you may leave the $location setting alone."

2) vboxwebsrv is not running on the VirtualBox host.  It is, I can see the apache2 "it works" page when I go to the hostname (Server-Main) from a browser,  also from the command line:

[I]anthony@Server-Main:/home/vboxuser$ sudo /etc/init.d/vboxweb-service status
Checking for VBox Web Service ...running
anthony@Server-Main:/home/vboxuser$ php5 -v
PHP 5.5.9-1ubuntu4.5 (cli) (built: Oct 29 2014 11:59:10)
Copyright (c) 1997-2014 The PHP Group
Zend Engine v2.5.0, Copyright (c) 1998-2014 Zend Technologies
    with Zend OPcache v7.0.3, Copyright (c) 1999-2014, by Zend Technologies
anthony@Server-Main:/home/vboxuser$ VBoxManage list extpacks
Extension Packs: 1
Pack no. 0:   Oracle VM VirtualBox Extension Pack
Version:      4.3.20
Revision:     96996
Edition:
Description:  USB 2.0 Host Controller, Host Webcam, VirtualBox RDP, PXE ROM with E1000 support.
VRDE Module:  VBoxVRDP
Usable:       true
Why unusable:
anthony@Server-Main:/home/vboxuser$
[/I]

Please can someone help to suggest what else I check.  The only difference I've made from following the instructions in the linux home server pages were to install the newer version of the packages specified.

Also please excuse the crummy formatting, it'll get better as I post more!

Thanks,

---

### Post by newbie-user on 2014-12-10
Did you move the phpvirtualbox folder to /var/www and the restart apache?
**mv phpvirtualbox-[current version] /var/www/phpvirtualbox**

Also, did you set the startup links?
[B]update-rc.d vboxweb-service defaults
/etc/init.d/vboxweb-service start[/B]


Here are my notes for my installations:

apt-get install apache2-mpm-prefork php5-suhosin libapache2-mod-php5 unzip

Install virtualbox and extension pack

 [INDENT]apt-get install dkms
 apt-get install virtualbox-[current version] --no-install-recommends
 wget [http://[latest](http://[latest) extension pack]
 vboxmanage extpack install [latest extension pack][/INDENT]

Add vbox user and add to vboxusers group
 [INDENT]
 adduser vbox
 adduser vbox vboxusers[/INDENT]

Create /etc/default/virtualbox file with the following content (used by SOAP API)

 [INDENT]VBOXWEB_USER=vbox[/INDENT]

Create startup links for vboxwebsrv

[INDENT] update-rc.d vboxweb-service defaults
 /etc/init.d/vboxweb-service start[/INDENT]

Download phpvirtualbox 

 [INDENT]wget [http://phpvirtualbox.googlecode.com/files/](http://phpvirtualbox.googlecode.com/files/)[current version][/INDENT]

Unzip and move to proper location with proper name

[INDENT] unzip phpvirtualbox-[current version].zip
 mv phpvirtualbox-[current version] /var/www/phpvirtualbox[/INDENT]

Go to /var/www/phpvirtualbox

[INDENT] cp config.php-example config.php
 nano config.php
  var $username = ‘vbox’;
  var $password = ‘[password]’;
  var $consoleHost = ‘[host ip address]’;[/INDENT]

Restart server, open browser to [http://[server]/phpvirtualbox](http://[server]/phpvirtualbox), log in as admin/admin

Set Remote Desktop port, then start guest OS, use RDP to view guest OS

---

### Post by AnthonyHorner on 2014-12-10
Hi,

Thanks for replying.  I was thinking about this today and (as the newbie cogs started whirring) I came to the conclusion that it had to be something to do with /var/www/phpvirtualbox/confi.php, that's because the "it works" page flashes up when I enter the hostname in the browser (so apache2 is running) and I can see the vboxwebsrvr is running by executing the following:


[I]anthony@Server-Main:/var/www/phpvirtualbox$ sudo /etc/init.d/vboxweb-service status
Checking for VBox Web Service ...running
anthony@Server-Main:/var/www/phpvirtualbox$[/I]

So I was interested with the line you put in the config.php file:

var $consoleHost = ‘[host ip address]’;

I tried this with the hostname ip address and also changed the $location (and then different permutations along with the VBOXBOX_HOST parameter in the virtuabox file, but no joy).

I have found another [thread]("http://ubuntuforums.org/archive/index.php/t-1716298.html") which resolved the problem and it mentioned to uncomment the noauth parameter in the config file again no joy for me also however I did get this back which was one of the checks asked:

[I]anthony@Server-Main:/var/www/phpvirtualbox$ ps aux | grep vbox
vboxuser   996  0.0  0.1 494552  6352 ?        Sl   21:55   0:00 /usr/lib/virtualbox/vboxwebsrv --background
vboxuser   998  0.0  0.1 127548  6280 ?        S    21:55   0:00 /usr/lib/virtualbox/VBoxXPCOMIPCD
vboxuser  1003  0.0  0.2 412596  9072 ?        Sl   21:55   0:00 /usr/lib/virtualbox/VBoxSVC --auto-shutdown
anthony   1297  0.0  0.0  11752   908 pts/0    S+   22:09   0:00 grep --color=auto vbox
anthony@Server-Main:/var/www/phpvirtualbox$ 
[/I]

If that means something to anybody, I'd love to find out.

Thanks

---

### Post by AnthonyHorner on 2014-12-11
A bit more hunting around and I've found that it is a common(-ish) problem [here]("http://sourceforge.net/p/phpvirtualbox/discussion/help/").  I've tried the various changes to no avail.

However one thing I would really appreciate information on is being able to switch on some form of logging/error logging. 

I don't know if it is switched on, where the log file would be or whether to try my luck with another web client, has anyone had any luck with VBoxHeadless?

---

### Post by newbie-user on 2014-12-15
> **AnthonyHorner said:**
> Hi,

Thanks for replying.  I was thinking about this today and (as the newbie cogs started whirring) I came to the conclusion that it had to be something to do with /var/www/phpvirtualbox/confi.php, that's because the "it works" page flashes up when I enter the hostname in the browser (so apache2 is running) and I can see the vboxwebsrvr is running by executing the following:


[I]anthony@Server-Main:/var/www/phpvirtualbox$ sudo /etc/init.d/vboxweb-service status
Checking for VBox Web Service ...running
anthony@Server-Main:/var/www/phpvirtualbox$[/I]

So I was interested with the line you put in the config.php file:

var $consoleHost = ‘[host ip address]’;

I tried this with the hostname ip address and also changed the $location (and then different permutations along with the VBOXBOX_HOST parameter in the virtuabox file, but no joy).

I have found another [thread]("http://ubuntuforums.org/archive/index.php/t-1716298.html") which resolved the problem and it mentioned to uncomment the noauth parameter in the config file again no joy for me also however I did get this back which was one of the checks asked:

[I]anthony@Server-Main:/var/www/phpvirtualbox$ ps aux | grep vbox
vboxuser   996  0.0  0.1 494552  6352 ?        Sl   21:55   0:00 /usr/lib/virtualbox/vboxwebsrv --background
vboxuser   998  0.0  0.1 127548  6280 ?        S    21:55   0:00 /usr/lib/virtualbox/VBoxXPCOMIPCD
vboxuser  1003  0.0  0.2 412596  9072 ?        Sl   21:55   0:00 /usr/lib/virtualbox/VBoxSVC --auto-shutdown
anthony   1297  0.0  0.0  11752   908 pts/0    S+   22:09   0:00 grep --color=auto vbox
anthony@Server-Main:/var/www/phpvirtualbox$ 
[/I]

If that means something to anybody, I'd love to find out.

Thanks

The "It Works" is a default apache2 webpage. It has nothing to do with virtualbox. To get to the phpvirtualbox login, you need to add /phpvirtualbox to the end of your server's FQDN or ip address: [http://your.server.com/phpvirtualbox](http://your.server.com/phpvirtualbox)

The consoleHost line is used to access your virtual machine while you are within phpvirtualbox. That should be the server's ip address from which you are accessing phpvirtualbox. For example, if you are accessing phpvirtualbox through your local network, it would be something like ```
var $consoleHost = ‘192.168.1.120’;
```

---

### Post by akshunj on 2014-12-22
Struggled with this issue for a couple of hours till I figured out that I had the phpvirtualbox directory in the wrong location.  All the install directions I have read for this put the directory at /var/www/phpvirtualbox, except for [this one]("https://www.liberiangeek.net/2014/09/install-virtualbox-headless-ubuntu-14-04-server-manage-phpvirtualbox/").  Here's the quote that caught my eye:

"Next, run the commands below to unzip the downloaded package

unzip phpvirtualbox*.zip

 

Next, create a root directory for phpVirtualBox.

sudo mv phpvirtualbox-4.3-1 /var/www/html/phpvirtualbox"

I promptly moved my directory into the html subfolder and everything started working right away.  Hope this helps someone.

--Akshun J

---

### Post by AnthonyHorner on 2015-01-02
> **akshunj said:**
> Struggled with this issue for a couple of hours till I figured out that I had the phpvirtualbox directory in the wrong location.  All the install directions I have read for this put the directory at /var/www/phpvirtualbox, except for [this one]("https://www.liberiangeek.net/2014/09/install-virtualbox-headless-ubuntu-14-04-server-manage-phpvirtualbox/").  Here's the quote that caught my eye:

"Next, run the commands below to unzip the downloaded package

unzip phpvirtualbox*.zip

 

Next, create a root directory for phpVirtualBox.

sudo mv phpvirtualbox-4.3-1 /var/www/html/phpvirtualbox"

I promptly moved my directory into the html subfolder and everything started working right away.  Hope this helps someone.

--Akshun J

Yes, it helped me!

I re-installed virtualbox into the location from the link you supplied and it worked.

I've finally got the log-in screen.  The only trouble is that the log-in doesn't work using admin/admin but that's another thread.


Many thanks

---

