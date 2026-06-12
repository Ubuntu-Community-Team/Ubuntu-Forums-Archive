---
title: "VirtualHosting problem:  &quot;ERROR: Site mysite.com does not exist!&quot;"
date: 2012-12-21
forum: Server Platforms
---

### Post by Toriku on 2012-12-21
I'm trying to set up Apache2 to use VirtualHosting.
But even after following tutorials online, I get an error...

 I've found the "apache2.conf" file, the "conf.d" folder and the "sites-enabled folder"; I've added the line:

> NameVirtualHost *

into a file called "virtual.conf" in the "conf.d" folder, I've added the file "mysite.com.conf" into the sites enabled folder, containing the following code:

> 
GNU nano 2.2.6                      File: mysite.com.conf

#
#  mysite.com (/etc/apache2/sites-available/mysite.com)
#
<VirtualHost *>
        ServerAdmin [email]webmaster@mysite.com[/email]
        ServerAlias [www.mysite.com](www.mysite.com)

        # Indexes + Directory Root.
        DirectoryIndex index.html
        DocumentRoot /var/www/mysite.com/

        # CGI Directory
        ScriptAlias /cgi-bin/ /home/www/mysite.com/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>


        # Logfiles
        ErrorLog  /var/www/mysite.com/logs/error.log
        CustomLog /var/www/mysite.com/logs/access.log combined
</VirtualHost>


however, when i run a2ensite I get the error that the website doesn't exist...
 I've added the entry to it in bind9, and I still can't get by this error...

> 
ERROR: Site mysite.com does not exist!


the tutorial I found is here [http://www.debian-administration.org/articles/412]("http://www.debian-administration.org/articles/412")

any help solving this problem would be greatly appreciated!

---

### Post by CharlesA on 2012-12-21
You need to create a file in /etc/apache2/sites-available and then enable it with a2ensite somesite.

Copy the default file, and change the contents as you wish and enable it.

---

### Post by Toriku on 2012-12-21
that's exactly what I've done, I don't understand why it doesn't work

---

### Post by CharlesA on 2012-12-21
Does /var/www/mysite.com exist?

If it does, check the name of the file you are trying to enable. That is the likely problem.

FWIW, I use the site names as my virtualhost names, so I know which is which. I have a file for my site in /etc/apache2/sites-available named charlesa.net, so I need to enable it by typing:

```
sudo a2ensite charlesa.net
```

---

### Post by sandyd on 2012-12-21
> **Toriku said:**
> I'm trying to set up Apache2 to use VirtualHosting.
But even after following tutorials online, I get an error...

 I've found the "apache2.conf" file, the "conf.d" folder and the "sites-enabled folder"; I've added the line:



into a file called "virtual.conf" in the "conf.d" folder, I've added the file "mysite.com.conf" into the sites enabled folder, containing the following code:



however, when i run a2ensite I get the error that the website doesn't exist...
 I've added the entry to it in bind9, and I still can't get by this error...



the tutorial I found is here [http://www.debian-administration.org/articles/412]("http://www.debian-administration.org/articles/412")

any help solving this problem would be greatly appreciated!

a few problems here:
1. ```

NameVirtualHost

```

is supposed to be already in ports.conf, and should include the port.

i.e.
```

NameVirtualHost *:80
```

2. You don't place your site in sites-enabled if you want to use a2ensite. You place it in sites-available

3. Your virtual host should have
```

<VirtualHost *:80>

```

instead of
```
<VirtualHost *>
```

In addition, unless that is the only site you are serving (that would defeat the purpose of Virtual Hosts right?)
you would need a 
```

 ServerName
```
in the Virtual host as well
i.e.
```

 ServerName content.sandyd.me
```

Note that instead of the * in 
```

<VirtualHost>
```
You can enter```

<VirtualHost <ip address>:80>
```

note that the above example listen on all ips, I removed the examples that listen on specific ips.

---

### Post by SeijiSensei on 2012-12-22
The file /etc/apache2/ports.conf already enables NameVirtualHost with a target of "*:80".  The <VirtualHost> declaration must match that target identically, i.e., "<VirtualHost *:80>".

Toriku, did you read the [relevant parts of the Ubuntu Server Guide]("https://help.ubuntu.com/12.04/serverguide/httpd.html")?

---

### Post by Toriku on 2013-01-03
its enabled now, I'm not sure what I did any different... Getting some other problems now, I can't access the site with its IP address and the DNS isn't working properly anymore, I can access sites hosted by other servers on the network, but not either of the two hosted on the virtual apache server (this machine also hosts the DNS).
 
thanks for your help guys,

---

### Post by Toriku on 2013-01-03
> **SeijiSensei said:**
> The file /etc/apache2/ports.conf already enables NameVirtualHost with a target of "*:80".  The <VirtualHost> declaration must match that target identically, i.e., "<VirtualHost *:80>".

Toriku, did you read the [relevant parts of the Ubuntu Server Guide]("https://help.ubuntu.com/12.04/serverguide/httpd.html")?


no I don't think I've read this one, I'll have a read through it today

---

### Post by volkswagner on 2013-01-03
> **Toriku said:**
> its enabled now, I'm not sure what I did any different... Getting some other problems now, I can't access the site with its IP address and the DNS isn't working properly anymore, I can access sites hosted by other servers on the network, but not either of the two hosted on the virtual apache server (this machine also hosts the DNS).
 
thanks for your help guys,

You don't have the ServerName directive listed in your vhost file.  This is described in the how to you listed.

For the "other problems" more description of symptoms will yield accurate help.

Can you ping the server by it's ip, hostname, and vhost domain name (after fixing vhost file "ServerName")?

Did you restart apache after making your changes?

To check you DNS run the following commands on both the server and a second lan machine.

```
host mysite.com
```
```
dig mysite.com
```

Are your lan machines set to use this server as DNS server?  Do you see it listed as NameServer?
```
cat /etc/resolv.conf
```

---

### Post by Toriku on 2013-01-03
> **volkswagner said:**
> You don't have the ServerName directive listed in your vhost file.  This is described in the how to you listed.

For the "other problems" more description of symptoms will yield accurate help.

Can you ping the server by it's ip, hostname, and vhost domain name (after fixing vhost file "ServerName")?

Did you restart apache after making your changes?

To check you DNS run the following commands on both the server and a second lan machine.

```
host mysite.com
```
```
dig mysite.com
```

Are your lan machines set to use this server as DNS server?  Do you see it listed as NameServer?
```
cat /etc/resolv.conf
```



From my windows PC I could ssh to the server, ping it, ftp... I just couldn't get a webpage up in my browser either with the domain or with IP address;
there are two servers on the local network and one remote one, each one running apache, and the 3rd server was hosting DNS and virtualhosting 2 apache sites I couldn't access, I've moved DNS over to the 2nd server and now everything seems to be working, I think there was something gone astray in the DNS, odd as it was working fine before christmas

---

### Post by Toriku on 2013-01-03
thanks again for your help guys, everything seems to be working, I do however get these errors and warnings when restarting apache:

>  * Restarting web server apache2
[Thu Jan 03 15:22:22 2013] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Thu Jan 03 15:22:22 2013] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Thu Jan 03 15:22:22 2013] [warn] NameVirtualHost *:80 has no VirtualHosts
... waiting [Thu Jan 03 15:22:23 2013] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Thu Jan 03 15:22:23 2013] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Thu Jan 03 15:22:23 2013] [warn] NameVirtualHost *:80 has no VirtualHosts


---

### Post by sandyd on 2013-01-03
> **Toriku said:**
> thanks again for your help guys, everything seems to be working, I do however get these errors and warnings when restarting apache:

make sure conf.d/virtual.conf is removed

---

