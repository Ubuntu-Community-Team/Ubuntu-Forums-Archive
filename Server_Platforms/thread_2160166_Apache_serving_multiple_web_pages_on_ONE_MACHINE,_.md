---
title: "Apache serving multiple web pages on ONE MACHINE, ONE IP ADDRESS. Help setting up"
date: 2013-07-05
forum: Server Platforms
---

### Post by JamesDonaldChilds on 2013-07-05
I have a SINGLE machine, I have a single IP address. It is running 12.04 server. I have apache running. I want to serve multiple websites from the single machine. I have been searching ALL over and have had little success in having this set up properly.

All help appreciated, but please don't post and tell me to "Set up virtual hosts".

Also, if you tell me to change any text inside any files, please specify WHAT files, this seems to be a big problem with this scenario is no one wants to specify. Thanks in advance!

---

### Post by 1clue on 2013-07-05
You need to set up name-based <you better not say it/>.

Frankly apache's documentation is extremely good, and nothing I can do is going to make it better.  Apache comes pretty much set up for it right out of the box, there's very little modification necessary.

[http://httpd.apache.org/docs/current/vhosts/name-based.html](http://httpd.apache.org/docs/current/vhosts/name-based.html)

Better yet, google on **apache2 name based virtual host example ubuntu** and add your ubuntu version on it, and it will probably give you exactly what files to edit.

---

### Post by JamesDonaldChilds on 2013-07-06
Ok, I've done that and followed the instructions to a tee, and it always directs to the main website. I can't get it to load the second website. I don't understand what I could be doing wrong as the multiple examples I've searched, which do it different ways, do not work.

---

### Post by JamesDonaldChilds on 2013-07-06
Ok, so I have tried completely removing apache2, with a purge as well. when trying to do things like service restart, start, and stop, it says apache does not exist or whatever. same with running commands to unistall. BUT! When I view services there is apache2 in the list with a + symbol AND my websites are still being hosted. This makes NO sense to me at all... Any help appreciated.

---

### Post by sandyd on 2013-07-06
If you post a list of domains you want to create, along with the directories they are supposed to serve from, I can generate an example configuration that you can build on.
Providing that it is a new install that is

```

sudo apt-get purge apache2*
apt-get install apache2
```

---

### Post by basicfreak on 2013-07-07
I don't know if you are still having any issues but here is my 2 cents...

httpd.conf example
```
Listen *:80
DocumentRoot "/var/www"


<VirtualHost *:80>
ServerName example.com
ServerAlias example.com *.example.com
DocumentRoot "/home/[username]/example.com"
HostNameLookups double
</VirtualHost>


<VirtualHost *:80>
ServerName example.net
ServerAlias example.net *.example.net example.info *.example.info
DocumentRoot "/home/[username]/example"
HostNameLookups double
</VirtualHost>


<VirtualHost *:80>
DocumentRoot "[path]"
ServerName [url]
ServerAlias [url] *.[url]
HostNameLookups double
</VirtualHost>

```

I learned the hard way to lookup the host name twice (otherwise it defaulted back to the main page for me)

as for restarting apache:

```
service apache2 stop
service apache2 start
```

or

```
service apache2 restart
```

or

```
ps aux | grep apache2
kill -9 [pid]
service apache2 start
```

forgive me if something is wrong this is off the top of my head

BASICFreak

---

### Post by newbie-user on 2013-07-08
Your virtual host declarations should go into their own files within the /etc/apache2/sites-available folder. For example, the file /etc/apache2/sites-available/example.com will contain only:
```
<VirtualHost *:80>
ServerName example.com
ServerAlias example.com *.example.com
DocumentRoot "/home/[username]/example.com"
HostNameLookups double
</VirtualHost>
```
Then the /etc/apache2/sites-available/example.net file will contain:
```
<VirtualHost *:80>
ServerName example.net
ServerAlias example.net *.example.net example.info *.example.info
DocumentRoot "/home/[username]/example"
HostNameLookups double
</VirtualHost>
```
Then you would enable each site using the file names from sites-available:
```
a2ensite example.com
a2ensite example.net

```
and then restart apache:
```

service apache2 restart

```
That should take care of it. You shouldn't have to touch httpd.conf at all for a basic setup.

---

### Post by CharlesA on 2013-07-08
> **newbie-user said:**
> Your virtual host declarations should go into their own files within the /etc/apache2/sites-available folder.

Technically you can throw them all in httpd.conf, but then it gets super messy.
I prefer to create a file for each site I am hosting and put it in sites-available - makes it much easier to manage and troubleshoot.

---

### Post by SeijiSensei on 2013-07-09
Plus a typo in one configuration doesn't block the rest of them from starting up.

---

