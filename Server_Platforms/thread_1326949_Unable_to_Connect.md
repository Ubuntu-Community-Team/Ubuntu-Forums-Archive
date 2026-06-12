---
title: "Unable to Connect"
date: 2009-11-14
forum: Server Platforms
---

### Post by GolemdX on 2009-11-14
[SIZE="2"]Hi, I used to have Ubuntu Server 8.04 configured similar to this, but now with Ubuntu Server 9.10, I can't seem to get it to act the way it used to.

After installing the LAMP Server, visiting 192.168.2.11 gives the default 'It Works!' page.

**In short terms, I tried to use VirtualHosts to host multiple websites, but now I get an 'Unable to Connect' error for all the websites, including the previously working 192.168.2.11**

Sorry for all this formatting, but the long story's right down here.[/SIZE]

----------

I did this (as root)...

```
cd /var/www/

mkdir heliodore.info
mkdir heliodore.info/htdocs
mkdir heliodore.info/cgi-bin
mkdir heliodore.info/logs

mkdir zorban.info 
mkdir zorban.info/htdocs
mkdir zorban.info/logs
mkdir zorban.info/cgi-bin

mkdir liamyum.info 
mkdir liamyum.info/htdocs
mkdir liamyum.info/logs
mkdir liamyum.info/cgi-bin

mkdir underson.info 
mkdir underson.info/htdocs
mkdir underson.info/logs
mkdir underson.info/cgi-bin
```

because I want to host multiple websites with the same server...
Then I did this...

```
vi /etc/apache2/conf.d/virtual.conf
```
...and put in...
```
NameVirtualHost *
```

...and for each website I wanted I made a file for it in sites-available with contents similar to...

```
<VirtualHost *>
        ServerAdmin @website.info
        ServerName  website.info
        ServerAlias webiste.servehttp.com

        DirectoryIndex index.html
        DocumentRoot /var/www/website.info/htdocs/

        ScriptAlias /cgi-bin/ /var/www/website.info/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>

        ErrorLog  /var/www/website.info/logs/error.log
        CustomLog /var/www/website.info/logs/access.log combined
</VirtualHost>
```

...that. I used 'website.servehttp.com' because I have to use No-IP because I don't have a static external IP. I did a...

```
a2ensite website.info
```

...for each website to enable it, did a...

```
/etc/init.d/apache2 reload
```

...to restart Apache, and now I get 'Unable to Connect'.

---

### Post by Lars Noodén on 2009-11-16
Open another screen and watch the error log as you try to connect:

tail -f /var/www/website.info/logs/error.log

One guess might be that it objects to the way you've written the opening element for <Directory>

---

### Post by GolemdX on 2009-11-16
```
tail -f /var/www/heliodore.info/logs/error.log
tail: cannot open `/var/www/heliodore.info/logs/error.log' for reading: No such file or directory
tail: no files remaining
```

Looks like there are no logs at all.

---

### Post by Lars Noodén on 2009-11-17
> **GolemdX said:**
> 

Looks like there are no logs at all.


So it looks like your vhost is not running at all.  Try checking the syntax again.  

[INDENT][FONT="Courier New"]/usr/sbin/apache2ctl configtest[/FONT][/INDENT]

---

### Post by GolemdX on 2009-11-17
```
apache2: Could not reliably determine the server's fully qualified domain name, using 8.15.7.103 for ServerName
[Tue Nov 17 09:51:09 2009] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Tue Nov 17 09:51:09 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
Syntax OK
```

...is the output I get.

EDIT: Do I need to change my /etc/hosts file? Right now it is...
```
127.0.0.1       localhost       localhost.localdomain
127.0.1.1       dobeserver

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by masux594 on 2009-11-17
are u really sure that php doesen't run at all? .. i want to explain my little story.. i encounter in the same situation about 1-2 months ago.. Apache answer to me with "Unable to connect".. and i doesen't understand why.. and an evening, i thought about the sentence "Unable to connect".. And suddendly i understand that the error comes from php that wasn't able to connect to my own mysql database, and i wrote in the php connection page to raise this message if there was some errors.. So, i check the user and the password, changed it into the right ones and now everything work! Nothing similar? =)

Sysc, A

---

### Post by GolemdX on 2009-11-17
Hmm? I have no MySQL databases, it's a fresh install besides what I did above. I don't know if PHP could be a problem, or the username and password, but everything seems to be running fine on the server besides the error above.

Does the hostname have anything to do with it? It used to be 'leffaf12' on the old computer but now it's 'dobe-server'.

EDIT: Oh, and I can successfully SSH to the server from any location.

---

### Post by GolemdX on 2009-11-18
Well, it's working now, I didn't do anything except reboot.

---

### Post by GolemdX on 2009-11-18
Looks like I spoke too soon, all the websites point to /var/www/ instead of their respective folders. Uh-oh.

EDIT: Gah, the problem was I had it as <VirtualHost *> instead of <VirtualHost *:80>. I thought I had it set right...

---

### Post by Vegan on 2009-11-18
I have an article in my forum showing how to setup Apache for virtual hosts. See the LAMP section.

---

### Post by GolemdX on 2009-11-18
I looked at the article, but it didn't really seem to help. Now I'm back at the beginning, everything gives 'Unable to Connect', except '/usr/sbin/apache2ctl configtest' only gives:

```
apache2: Could not reliably determine the server's fully qualified domain name, using 8.15.7.103 for ServerName
Syntax OK
```

I don't really know what to set my hostname/ServerName to... as I have many domains I'm using.

EDIT: What the heck! It seems as if a simple apache2 reload won't do it, I restarted, and now everything is working fine with the websites, however I still get the error about the domain name. It would be nice to get an answer as to what I should set my hostname/ServerName to, but everything is working the way I want anyhow. So, see ya later.

---

### Post by Iowan on 2009-11-18
[Here]("https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20Apache") is one option - there's a cleaner way to do it, but I'll need to search for it...

---

### Post by GolemdX on 2009-11-21
Thanks! Worked easily.

---

