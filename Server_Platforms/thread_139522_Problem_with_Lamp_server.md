---
title: "Problem with Lamp server"
date: 2006-03-04
forum: Server Platforms
---

### Post by gumbl on 2006-03-04
Hi

For the record... I'm no expert whatsoever regardin Ubuntu or any other Linux distribution whatsoever

Though, I figured it would be nice to explore the capabilities with a lamp environment... But after installing the appropriate mods I still cannot get the server to act as it should.

I have installed the following (Sorry about the mess but I became a bit over the top of my head trying to get the environment to work)

1. Both Apache and apache2

the webserver itself works... almost as it should. I can view a webpage written in html with apache but not with apache2. If I stop the apache-service and start only the apache2-service the webserver returns as if no webserver are available on my machine.

2. php4 and php5.
Theese to seems not to be able to coexist. I have tried though only to have the php4 package installed. Ofcourse I have tried only to have the php5 instance installed also

3. The appropriate files for mysql and libapache-packages that seems to be a requirement for the phpaddon.

I read the articles here on the forum about parsing phpfiles and how to set up a lampserver. I have tried to follow these guidelinse after a system resetting using synaptic, so that I (as i believe have every time started from a fresh start),

I modified both the apache and apache2 php.ini so that mysql.so was enabled..

Nothing seems to be working.. 

Any help is appreciated!

Thanx!

---

### Post by knalle on 2006-03-04
[http://www.schlitt.info/applications/blog/archives/83_How_to_run_PHP4_and_PHP_5_prallel.html](http://www.schlitt.info/applications/blog/archives/83_How_to_run_PHP4_and_PHP_5_prallel.html)

try this, but i would say that there is no good reason to run both php4 and php5 on the same server except known bugs that has to be catered for. if you do this to fool around, just go with php4 or php5, not both

---

### Post by gumbl on 2006-03-04
I'm not interrested in running both php4 and php5 simultaneously. I want the thing to work at all.. that is ... I want it to parse php files =) I don't care wether it's php4 or php5 as long as I have some active php-parser machine =)

Thanx for the fast reply

---

### Post by oscar on 2006-03-04
apache and apache2 are different web servers, you probably just want apache2. I would completely remove all apache packages, and keep the apache2 ones. As you changed some config files it would probably be a good idea to reinstall apache2 just to start afresh. After that completely remove all of your php packages and install libapache2-mod-php5 .
To restart your apache2 server go:
```
sudo /etc/init.d/apache2 restart
```
or start if it is not yet running.
When you have done that any .php files in /var/www/ should be processed.
For mysql make sure you have the mysql-server package installed.

That should be it, a complete Lamp environment.

---

### Post by gumbl on 2006-03-07
Thanx for all the help! I did too many changes on my system (because Im anewbie =) so I was forced to reinstall the system ('caus I don't have the experience to solve my errors) now after installation though everything seems to work when I only install your recommended installationpackages!

thanx!

/GumbL

---

### Post by VinceDee on 2006-03-07
You can run PHP4 and PHP5 on the same machine (though in your case I think I'd just stick with one or the other):

[http://www.ubuntuwebservers.com/?q=node/55](http://www.ubuntuwebservers.com/?q=node/55)


Here are a couple of HOWTOs that tell about general Ubuntu web server installs:

[http://www.ubuntuwebservers.com/?q=node/51](http://www.ubuntuwebservers.com/?q=node/51)
[http://www.ubuntuwebservers.com/?q=node/30](http://www.ubuntuwebservers.com/?q=node/30)
[http://www.ubuntuwebservers.com/?q=node/86](http://www.ubuntuwebservers.com/?q=node/86)


Vince

---

