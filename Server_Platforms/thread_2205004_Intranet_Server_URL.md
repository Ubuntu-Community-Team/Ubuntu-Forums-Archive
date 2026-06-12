---
title: "Intranet Server URL"
date: 2014-02-11
forum: Server Platforms
---

### Post by dustin8 on 2014-02-11
Hi Folks, 

I'm a bit confused with all of the different topics saying this is the fix for my particular issue. 

I have a Ubuntu Server hosting multiple INTRANET websites. 

I can get to the website from the server using "LOCALHOST"

Or from any network'd machine using ubuntu/  or the ip address 192.168.100.197

What happens though is that when you resolve to any of the sub-sites "ubuntu/eagle" the url changes from ubuntu/eagle to 192.168.100.197/eagle

Where can I correct this, so that the internal domain name, stays "ubuntu/eagle"?

Thanks in advance

---

### Post by brokenhachi on 2014-02-11
Have you tried using the FQDN? Does it still give the ip address in the bar?

---

### Post by dustin8 on 2014-02-11
It doesn't resolve as the Ubuntu machine is not a part of the Windows Domain

---

### Post by brokenhachi on 2014-02-11
are you using apache2? If so, what does the virtualhost say in /etc/apache2/sites-available/default?

How are you handling dns to the server since it isnt part of the domain? 


check here maybe: [http://ubuntuforums.org/showthread.php?t=1728585](http://ubuntuforums.org/showthread.php?t=1728585)

---

### Post by dustin8 on 2014-02-11
This is the virtualhost file

<VirtualHost *:80>
	ServerAdmin webmaster@localhost


	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>


	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>


	ErrorLog ${APACHE_LOG_DIR}/error.log


	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn


	CustomLog ${APACHE_LOG_DIR}/access.log combined


    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>


</VirtualHost>


I have a static IP assigned to the machine, and my domain controller has a static DNS record for the ubuntu server

---

### Post by dustin8 on 2014-02-12
Anyone able to help me pinpoint what I need to change?

---

### Post by volkswagner on 2014-02-12
Provided local DNS is working, from Windows client:
```
nslookup ubuntu
```
Should return ip of your local server.

Simply adding:
```
ServerName ubuntu
```
To your host file plus verify namedVirtualhost is enabled in ports.conf, reload apache all should be well.

---

### Post by dustin8 on 2014-02-12
Awesome thank you

---

### Post by dustin8 on 2014-02-12
It worked, and then it stopped. 

Well at least I'm on the right track. 

Thanks

---

### Post by brokenhachi on 2014-02-12
what does /etc/hosts look like?

---

### Post by volkswagner on 2014-02-12
> **dustin8 said:**
> It worked, and then it stopped. 

Well at least I'm on the right track. 

Thanks

Other things to consider:

Clear browser cache.

Verify if certain web pages or server software packages (drupal, wordpress, html links, etc.) are causing the break.
Are all your links, relative links?

Are all lan machines able to resolve ubuntu?
[Windows]
```
nslookup ubuntu
``` 

[Linux]
```
host ubuntu
```
```
dig ubuntu
```

Can they ping Ubuntu server?
```
ping ubuntu
```

---

### Post by brokenhachi on 2014-02-12
Just to clarify, the issue is that when going to [http://ubuntu](http://ubuntu), it resolves but changes the URL to [http://IP.ADD.RES.S](http://IP.ADD.RES.S), or no?

do you have ```
ip.add.re.ss hostname hostname
``` added to /etc/hosts? (i.e. not only 127.0.0.1, but also the interface ip)

---

### Post by brokenhachi on 2014-02-12
.... :(

---

### Post by dustin8 on 2014-02-13
Sorry for the late reply, just got the chance to look at this again. Here's the hosts file

127.0.0.1   localhost
127.0.1.1   ubuntu

# The following lines are desirable for IPv6 capable host
::1       ip6-localhost    ip6-loopback
fe:00:0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

---

### Post by dustin8 on 2014-02-14
> **brokenhachi said:**
> Just to clarify, _**the issue is that when going to [http://ubuntu](http://ubuntu), it resolves but changes the URL to [http://IP.ADD.RES.S](http://IP.ADD.RES.S), **_or no?

do you have ```
ip.add.re.ss hostname hostname
``` added to /etc/hosts? (i.e. not only 127.0.0.1, but also the interface ip)


Correct, the bold and unlined portion is what happens, but only when going to a subsite " http://ubuntu/eagle" does it rename the url to "http://192.168.100.197/eagle" 

I've tested from several windows machines for nslookup, and ping to ubuntu, and they all resolve properly.

---

### Post by dustin8 on 2014-02-14
The first image is when going to [http://ubuntu](http://ubuntu)[URL="http://postimg.org/image/jbfppt88v/"]
http://postimg.org/image/jbfppt88v/[/URL]

and then this when I go to a subdomain

[http://postimg.org/image/99r84fr9n/](http://postimg.org/image/99r84fr9n/)


Here's the Dig and nslookup for "Ubuntu" 
[http://postimg.org/image/lyfy24i71/](http://postimg.org/image/lyfy24i71/)
[http://postimg.org/image/sy9tga8x9/](http://postimg.org/image/sy9tga8x9/)

Hosts files
[http://postimg.org/image/tze20yeu3/](http://postimg.org/image/tze20yeu3/)


I've added:

"192.168.100.197 ubuntu" to the hosts   file and the issue remains the same

---

### Post by volkswagner on 2014-02-14
This is not a problem with Apache.  It has to do with the software running in directory /eagle.

Im not sure what software you are running, but there should be a setting for site name or valid urls.

I mentioned this in post 11.

Cheers!

---

### Post by dustin8 on 2014-02-14
The folders and files within /var/www do not run the web-server. It's basically a file dump for the content that is loaded onto the page. 

There isn't anything configured within these drives that I know of to change to resolve this issue.

---

### Post by dustin8 on 2014-02-14
I've got it fixed, after some digging

---

### Post by volkswagner on 2014-02-14
> **dustin8 said:**
> The folders and files within /var/www do not run the web-server. It's basically a file dump for the content that is loaded onto the page. 

There isn't anything configured within these drives that I know of to change to resolve this issue.

It appears you have some sort of wiki engine, at least php which is likely rewriting URLs.

Please offer your solution so the entire community can prosper.

---

### Post by dustin8 on 2014-02-17
> **volkswagner said:**
> It appears you have some sort of wiki engine, at least php which is likely rewriting URLs.

Please offer your solution so the entire community can prosper.


The solution is a 2 part solution. 

1) On my DNS server, add a record for the preferred domain name, in my case "ubuntu" and "eaglewiki"

2) The second part of this solution is to edit _/var/www/**sitefolder**/LocalSettings.php_ to have 

```
## The protocol and server name to use in fully qualified URLs 
## $wgServer = "http://192.168.100.197";
$wgServer = "http://ubuntu";
$wgServer = "http://eaglewiki";

```

I suppose I could leave [http://192.168.100.197](http://192.168.100.197) as a fall back incase my dns server fails, but if that happens I've got bigger issues than the wiki server. 
It doesn't appear to matter on the order for the fully qualified URLs either.

That is all that was needed, for each separate site /var/www/newsitename, add a new dns record, change the appropriate settings in the above file, and like magic it's all set.

And correct this is a Wiki server, these are the version details. 

[TABLE="class: wikitable plainlinks"]
[TR]
[TH="bgcolor: #F2F2F2, align: center"]Product[/TH]
[TH="bgcolor: #F2F2F2, align: center"]Version[/TH]
[/TR]
[TR]
[TD][MediaWiki]("https://www.mediawiki.org/")[/TD]
[TD][1.22alpha]("https://www.mediawiki.org/wiki/MediaWiki_1.22") [(0ee8d69)]("https://git.wikimedia.org/commit/mediawiki%2Fcore.git/0ee8d69777ec70b1b6cc4c30dbd41129e421a130")[/TD]
[/TR]
[TR]
[TD][PHP]("http://www.php.net/")[/TD]
[TD]5.3.10-1ubuntu3.8 (apache2handler)[/TD]
[/TR]
[TR]
[TD][MySQL]("http://www.mysql.com/")[/TD]
[TD]5.5.29-0ubuntu0.12.04.1[/TD]
[/TR]
[/TABLE]

---

