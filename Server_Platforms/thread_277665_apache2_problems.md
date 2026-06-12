---
title: "apache2 problems"
date: 2006-10-15
forum: Server Platforms
---

### Post by peanut butter on 2006-10-15
i can access my website by going to [www.paulhost.net](www.paulhost.net) but not with just [http://paulhost.net](http://paulhost.net)
the following is my vhost config.
```
<VirtualHost *:80>
ServerName paulhost.net
DocumentRoot /home/paulhost.net
ServerAlias www.paulhost.net
</VirtualHost>

```
any help would be greatly appreciated.:)

---

### Post by tartetatin on 2006-10-15
How does your /etc/hosts looks like ?
Maybe try to add this line in it
```
192.168.0.1 www.paulhost.net paulhost paulhost.net
```
with 192.168.0.1 to replace with the local IP adress of your web server

---

### Post by peanut butter on 2006-10-15
my server is rilly a vps so it dosnt have an internal ip. i tried both 127.0.0.1 and its public ip but neither helped.:( .
Maby apache thinks paulhost.net is the FQDN. I had this problem before with another domain too.](*,)

---

### Post by Avarus on 2006-10-15
Is this what you are looking for or am I just thinking on a lower level?

> The ServerName directive is optional and specifies what FQDN your site should answer to. The default virtual host has no ServerName directive specified, so it will respond to all requests that do not match a ServerName directive in another virtual host. If you have just acquired the domain name ubunturocks.com and wish to host it on your Ubuntu server, the value of the ServerName directive in your virtual host configuration file should be ubunturocks.com. Add this directive to the new virtual host file you created earlier (/etc/apache2/sites-available/mynewsite). 

You may also want your site to respond to [www.ubunturocks.com](www.ubunturocks.com), since many users will assume the www prefix is appropriate. Use the ServerAlias directive for this. You may also use wildcards in the ServerAlias directive. For example, ServerAlias *.ubunturocks.com will cause your site to respond to any domain request ending in .ubunturocks.com. 

---

### Post by peanut butter on 2006-10-15
thanks for the idea but i alredy have it in the config.

Edit: I think i will give lighttpd another try.:)
EDIT2. follow this [http://trac.lighttpd.net/trac/wiki/TutorialLighttpdAndPHP](http://trac.lighttpd.net/trac/wiki/TutorialLighttpdAndPHP)

---

### Post by peanut butter on 2006-10-16
Bump?

edit: it happens with lightpd also. any ideas?

---

### Post by fatbastard spice on 2006-10-16
Does the server name actually tell Apache to respond to headers with that address, or is it just the VirtualHost and ServerAlias tags that do that? Well that's my guess, and if it's right try replacing <VirtualHost *:80> with <VirtualHost paulhost.net:80>

If that doesn't work the other guess is to add a second ServerAlias tag pointing to paulhost.net

---

### Post by pppetter on 2006-10-16
Since your alias doesn't work, just try and create another virtualhost like this:

<VirtualHost *:80>
ServerName paulhost.net
DocumentRoot /home/paulhost.net
</VirtualHost>
<VirtualHost *:80>
ServerName [www.paulhost.net](www.paulhost.net)
DocumentRoot /home/paulhost.net
</VirtualHost>

Donno if it will work, but trying doesn't hurt ;)

---

### Post by Texan Impeacher on 2006-11-29
Try changing:
```
<VirtualHost *:80>
ServerName paulhost.net
DocumentRoot /home/paulhost.net
ServerAlias www.paulhost.net
</VirtualHost>

```

to 

```
<VirtualHost *:80>
ServerName paulhost.net
ServerAlias www.paulhost.net
DocumentRoot /home/paulhost.net
ServerAlias www.paulhost.net
</VirtualHost>

```

---

### Post by MJN on 2006-11-30
There's no need for two ServerAlias directives... indeed the second will just override the first.
 
However, both [www.paulhost.net]("http://www.paulhost.net") and paulhost.net work fine from here so is there still a problem? I was going to suggest a DNS issue (i.e. no A record for paulhost.net) but as it's now working...
 
Mathew

---

