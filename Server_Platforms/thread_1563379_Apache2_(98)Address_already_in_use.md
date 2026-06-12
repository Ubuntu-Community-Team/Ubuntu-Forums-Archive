---
title: "Apache2 (98)Address already in use"
date: 2010-08-29
forum: Server Platforms
---

### Post by Bluetickle on 2010-08-29
Greetings fellow Ubuntu Users,

I am using Ubuntu Server 10.04 64bit. I am getting an Apache2 start up error after I setup my certificates and configure Apache2 for HTTPS. At the point on start up where I need to type in my certificate pass code I get a lockup due to the Apache2 process being in a hung state. I reboot if needed and switch to console tty2. When I type in the command.

```
sudo /etc/init.d/apache2 restart
```

I get the following error.

```
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:443 no listening sockets available, shutting down
```

To correct the problem I do this. 

```
sudo lsof -i TCP | grep LISTEN
```

From the output of the command above I look for the apache2 process and make note of its process ID. Then, I kill that process ID. For example, the command below has an apache2 process ID of 1131.

```
sudo kill -9 1311
```

Next, when I run this command.

```
sudo /etc/init.d/apache2 start
```

The apache2 server starts up and asks for my certificate password,  accepts it when I type it in, and runs perfectly fine afterward.

Fortunately this instance of Ubuntu Server is running inside a VMWare virtual machine. I can just "pause" the virtual machine if I need to rather than going through this crude and tedious start up process too frequently.

Crude and tedious are feelings I'm having too frequently lately with Ubuntu Server.

I would like to resolve this issue for the greater good. What information can I provide to help find a solution?

Thanks,

Bluetickle

---

### Post by thepoplin on 2010-10-07
This saved my rear countless times. Kudos!

---

### Post by volkswagner on 2010-10-08
Do you have a reference to port 443 in ports.conf?

Such as the following or similar?

```
Listen 80

[COLOR="Blue"]<IfModule mod_ssl.c>
    Listen 443
</IfModule>[/COLOR]
```

Also if using virtual hosts, you may want to add an entry in httpd.conf such as the following.

```
NameVirtualHost *
[COLOR="Blue"]NameVirtualHost *:443[/COLOR]
AddHandler cgi-script .pl
RewriteEngine On

```

---

### Post by Bluetickle on 2010-11-04
Re: volkswagner

Yes I a reference to port 443 in ports.conf and yes I have apache2.conf with NameVirtualHost *:443

---

### Post by killboymota on 2010-11-30
thank you, this helped me! now i can browse me site files but each time i enter only directory it says "not found" :(

---

### Post by oshunluvr on 2011-01-29
Bluetickle:

Did you ever find a fix for this???

---

### Post by Bluetickle on 2012-01-29
I have not found any fixes or solutions... I just avoid rebooting as much as possible. I hope to not have this issue when I meticulously rebuild my server with the next Ubuntu Server LTS.

---

### Post by ddench on 2012-08-06
Disclaimer, I'm a CentOS user so the file names and paths are from CentOS, but I think the below is pertinent to the problem.

If you have a conf.d folder under the apache root (/etc/httpd/conf.d/...), make sure there are no entries in the subfiles that are ssl specific, if there are, then in the main httpd.conf file (Apache config file) make sure there are no conflicting entries.

In short when apache starts the main httpd.conf file includes the conf.d/ folder and all *.conf files are loaded before apache gets to your VirtualHost and Listen config options. As such, if you have ssl configured in one of these conf.d/... folders, Apache will bomb out once it reaches your ssl config.

So the solution is to make sure there are no confilcting entries in any conf.d/ssl.conf file vs conf/httpd.conf.

On CentOS it looks like this


/etc/httpd/conf/httpd.conf (around li 222 is Include conf.d/*.conf - telling apache to look at these files next)
/etc/httpd/conf.d/ssl.conf (this file have params for the main config as well as any VirtualHosts that require SSL)

If you've got this, you may want to check the paths for the key and crt files too...

Hope this helps, and sorry i can't put in Ubuntu specific naming/directories. I've been struggling with SSL and DNS all day, got this issue resolved, so thought I'd share.

---

