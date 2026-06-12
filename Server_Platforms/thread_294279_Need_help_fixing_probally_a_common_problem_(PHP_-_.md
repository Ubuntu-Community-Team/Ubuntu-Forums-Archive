---
title: "Need help fixing probally a common problem (PHP - Apache)"
date: 2006-11-06
forum: Server Platforms
---

### Post by coastdweller on 2006-11-06
I'm simply digging a bigger hole than existed so I'm turning to the forums for help.

I had a perfectly working dapper lamp.
I had the dotdeb sources enabled
After apt-get update and upgrade 5.2.0 was installed.
This broke Zend as its not supported (I must have zend).
After fiddling with removing and installing php4 and php5 several times I've completely broken php...

The consequence is I've also broken ssh some how.

If someone has some time to post how to fix these things:

ssh
php4
php5

It would be greatly appreciated.

We were in the middle of testing a new billing solution and all hell broke loose.

Some details:

The server is in the same room as us

I don't want to lose the databases on this machine and also the other configurations (NFS) so I'm turning to the forum.

---

### Post by coastdweller on 2006-11-06
Consider these very basic requests.

I need help getting ssh, php working again.

Thanks!

---

### Post by marianom on 2006-11-06
I can try to help you out with the php.
What's the error you get and when? 
When you start apache, when you execute a php page?

---

### Post by coastdweller on 2006-11-06
Hi, thanks for responding. Specifically its an incompatibility between php4 and php5 and I believe its because I let it upgrade to 5.2.0 and then shredded php trying to downgrade it.

After my wife recommended me try to use aptitude

This is my wife typing on my new keyboard >>>> "My wife is really smart and she was trying to help because I didn't know about dependancies" [/end tangent]

After my wife recommended me to try aptitude and I really didn't know what I was doing I think I removed some stuff, actually I had no choice it just did it. Now I can't connect to to the SSH server:

> whishup@whishup-desktop:~$ ping 192.168.0.99
PING 192.168.0.99 (192.168.0.99) 56(84) bytes of data.
64 bytes from 192.168.0.99: icmp_seq=1 ttl=64 time=3.69 ms
64 bytes from 192.168.0.99: icmp_seq=2 ttl=64 time=0.117 ms"

That obviously is another problem but apache will not load either, nor will it even pop up the phtml page noting it has a problem with php.

SO I've broke some things, but believe me, it's worth saving this server due to the amount of configuration and programs I've installed on that machine.

I appreciate your help.

The specific error on bootup now is:

> Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load: Cannot load /usr/lib/apache2/modules/libphp5.so into server: /usr/lib/apache2/modules/libphp5.so: cannot open shared object file: No such file or directory.

update: I reinstalled ssh through apt-get so now we can connect to it from anywhere.

update2: I just did a sudo apt-get upgrade and its finding a bunch of php5 stuff but I'm sure its still not going to work. WIll update again when its done.

Thanks

---

### Post by adamkane on 2006-11-06
If you want ssh, install xampp.

Otherwise install this way:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

* EDIT * I confused ssh with ssl. * END EDIT *

---

### Post by marianom on 2006-11-06
I'm kinda a "install php from source" guy so if you'd like to take a chance, I'll try to help. 
I have no php installed in this particular pc I'm using right now so we can try at the same time. Just let me know which modules are you using and I give it a shot.

Regarding adamkane suggestion it might be useful but as you mention you already had a database I would take extra care since you might lose mysql data (don't know if mysql reinstallation causes data lose, never did it myself). I suggest backing up the db files (after all it's easy: just copy+paste).

Last silly question: the apache conf file is trying to load libphp5.so. Do you have that file in your server? where?

I'll suscribing the thread and I will keep an eye in case I can help you. Just let me know.

Regards.

---

### Post by coastdweller on 2006-11-06
Got it! 

I installed ssh through apt-get and fixed that, then upgraded apt-get and it reinstalled php5 and bam... zend with apache mysql etc

[http://support.dotgig.com/support/app-modernbill-order/cart.php](http://support.dotgig.com/support/app-modernbill-order/cart.php)
That is it running.

---

### Post by adamkane on 2006-11-06
BTW, don't use dotdeb with Ubuntu as a rule.

---

### Post by coastdweller on 2006-11-06
Got ya, but its kinda too late =)

I've already fixed it,I simply had dependecy errors I've seemed to route them out =)

Thanks for the help, really

---

### Post by marianom on 2006-11-06
Cool. Congrats.

---

### Post by coastdweller on 2006-11-07
Just wanted to post again this: Knowing that someone had responded and was willing to help me solve this was a real big amount of support.

I have several databases and tons of data on that server and it is my compelling reason for developing inside ubuntu.

My faith restored =)

---

### Post by GlennB on 2007-04-11
Hi All,

resurrecting a way old thread, but I've just had an almost identical problem to this. My Dapper LAMP server was working perfectly, running Gallery, Drupal, Postfix etc. and then I somehow managed to bork the whole thing by pressing an (unknown) wrong key in Synaptic. I've no idea how I did it, but a long list of stuff got uninstalled.

Now, Apache still runs, but php does not. Mysql is still installed, but obviously the web server cannot connect to it. If I connect to the web server I get "Apache/2.0.55 (Ubuntu) server at [www.mydomain.co.uk](www.mydomain.co.uk) port 80 - no mention of php anywhere.

Can any kind soul point me in the right direction of how to troubleshoot this, and get php working again? I'll worry about the postfix problem once I have the web server back up and running...

Many thanks,

Glenn.

---

### Post by az on 2007-04-11
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Whatever you do, don't mix repositories - just use one source (not dapper and Edgy together, for example) and don't compile stuff from source.  The LAMP stack works perfectly fine and is easily installed and maintained using the package manger.  Compiling from source will only make your problems deeper.

---

### Post by GlennB on 2007-04-11
Hi,

Thanks for the lightning fast reply!

I've been through that page three times, but sadly it doesn't do the trick.

I can only guess that my little accident with aptitude has uninstalled some other dependency that I'm unaware of. I think I've actually made matters worse now, as previously Apache was working, but was asking me to download php / phtml pages rather than displaying them. After following the page, Apache is failing to reload completely. It fails with "cannot load /usr/lib/apache2/modules/libphp4.so into server" no such file or directory.
However running a2dismod on libphp4.so says "already disabled or does not exist".

Looks like I may have to strip out all the Apache , php, and mysql stuff and start again.

Thanks for the pointer though - I will follow that page when I reinstall.

Best regards,

Glenn.

---

### Post by GlennB on 2007-04-11
Wow. This just keeps getting weirder!

I backed up all my web data and databases, and then did what I thought was a full uninstall / reinstall of the lamp stack. Essentially this:

```
sudo aptitude purge apache2 php5-mysql libapache2-mod-php5 mysql-server

```

(Actually I did it in stages, and checked at each stage that the config files were gone).

I also hunted around for other php related packages, and purged those. Once I thought all traces of previous configs were gone, I reinstalled the LAMP stack afresh using the howto mentioned above . It didn't work. When I try to reload Apache2 with 

```
/etc/init.d/apache2 force-reload
``` 

I get:

```
Cannot load /usr/lib/apache2/modules/libphp4.so into server: /usr/lib/apache2/modules/libphp4.so: cannot open shared object file: No such file or directory
```

when I point a browser at the server I get an "unable to connect. Firefox cannot establish a connection" error. I have no idea where the reference to libphp4.so is coming from. Anyone have any ideas?

Many thanks,

Glenn.

---

### Post by marianom on 2007-04-11
A path problem? Do you actually have that file in your server?
Maybe a missing config value in your php.ini / httpd.conf

In my httpd.conf, I've got:

```
# Dynamic Shared Object (DSO) Support
#
# To be able to use the functionality of a module which was built as a DSO you
# have to place corresponding `LoadModule' lines at this location so the
# directives contained in it are actually available _before_ they are used.
# Please read the file http://httpd.apache.org/docs/dso.html for more
# details about the DSO mechanism and run `httpd -l' for the list of already
# built-in (statically linked and thus always available) modules in your httpd
# binary.
#
# Note: The order in which modules are loaded is important.  Don't change
# the order below without expert advice.
#
# Example:
# LoadModule foo_module libexec/mod_foo.so
LoadModule php5_module        libexec/libphp5.so

```

Since I installed and configure it manually I'm not sure if this step is taken care by the apt (I guess it should but who knows...)

---

### Post by GlennB on 2007-04-12
Panic over - it's fixed.

For some reason, when I ran

```
asdismod php4
```

the system reported "the module is already uninstalled or does not exist". However, when I checked it was still in mods-enabled. Go figure. I deleted the entries in mods-enabled relating to php4 and all is well.

---

