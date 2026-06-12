---
title: "[SOLVED] [help] How to run 2 apache servers at the same time?"
date: 2008-02-19
forum: Server Platforms
---

### Post by sebkinne on 2008-02-19
Hello everyone. I am having the problem that i want to run a second http server (apache2) on the same machine as my primary webserver.
> sudo apt-get install apache2
right, so that is running since around a year now, but i really need another webserver running (on any other port, i would know how to change that, ports.conf)

Now my question is, if i can run another apache server at the same time. i guess it works, and i have seen it, but i have no idea how to get the second apache server up and running....

if anyone has any idea, i would really apreciate the help.

Best regards,

sebkinne

---

### Post by lespaul_rentals on 2008-02-19
Wouldn't it be better to just make a subdomain and use that instead?

---

### Post by sebkinne on 2008-02-19
no, it would if i wanted it to be an adress, but i need it for a game server, which requires a new adress that belongs to a domain name (basically if x.x.x.x is my private server, x.x.x.x:1111 cud be the game servers website, which would get a domain name)

---

### Post by lespaul_rentals on 2008-02-19
Why would you run a website on any port other than 80?  I'm just trying to understand here, sorry.

---

### Post by sebkinne on 2008-02-19
hehe, just a matter of matching it with a domain name.

yourdomain.com will redirect to my.dynamic.dns

newdomain.com: will redirect to my.dynamic.dns:1234

---

### Post by tubezninja on 2008-02-19
I guess what we're trying to say is, from what you're telling us, you clearly do not **need** another instance of apache.  All you need to do is set up a virtual host in your single instance of apache2 that would point to a different directory in /var/www.

In other words:

olddomain.com would use /var/www/olddomain as its home directory

newdomain.com would use /var/www/newdomain as **its** home directory.

That way, people visiting olddomain.com see the content for that web site, and newdomain.com users see the newdomain content.  Two sites on the same apache server, and users don't need to even be aware that more than one site runs on the same system. This is the method I use to  run more than one site on the same server, and it's also how various site hosting services do it as well.

[Here's a good rundown of how VirtualHost works]("http://www.tequilafish.com/2007/08/02/apache-virtualhost-on-ubuntu/") in ubuntu.

---

### Post by lncoll on 2008-02-19
Hi:

That you need is create a VirtualHost that listens in another port, in Apache documentation look for VirtualHost, is very easy.
Elsewhere here you have an example

```

Listen 1100

<VirtualHost *:1100>
        ServerAdmin webmaster@localhost
        ServerName example.org
        ServerAlias www.example.org        
        DocumentRoot /var/www/gameserver
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/gameserver/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ErrorLog /var/log/apache2/gameserver/error.log
        LogLevel warn
        CustomLog /var/log/apache2/gameserver/access.log combined
        ServerSignature Off
</VirtualHost>

```

This way the accesses to example.org in port 1100 can see the webpage in your /var/www/gameserver/ folder or where you set/config it.

---

### Post by sebkinne on 2008-02-19
Thank you very much for your help!

Ill thank you all :D

its running smoothly, thanks alot

---

