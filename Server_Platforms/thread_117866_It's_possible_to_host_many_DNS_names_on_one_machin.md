---
title: "It's possible to host many DNS names on one machine, right?"
date: 2006-01-15
forum: Server Platforms
---

### Post by Zensunni on 2006-01-15
If I want to host two domain names, such as fishnfood.com and yohoo.com, can I do it with one machine and IP adress?

I want to start site-hosting and was wondering if it could be done with as little complication as possible. Many people have suggested I do one of two things: either use my own DNS server (eg: fishnfood.mydomain.com / yohoo.mydomain.com) or host the pages on my domain (eg: mydomain.com/fishnfood / mydomain.com/yohoo).

Neither of the two suggestions are viable because they involve compromise of the address. Is what I want possible or will I have to get a seperate IP adress and machine?

---

### Post by bobyang on 2006-01-15
Sure you can do that, just create virtual host in apache.

---

### Post by Mr_Grieves on 2006-01-15
*Edit* Aha.. look at the post below *Edit*

You need two IP-adresses to that machine in case you want to host two diffrent DNS names on it.

You don't need two fysical interfaces though, you can do with virtual ones.
eth0 - 123.4.5.6/my_domain.com
eth0:1 - 321.4.5.6/my_second_domain.com

If you want to run a webserver for these domains, you may use virtual hosts in Apache.

---

### Post by bobyang on 2006-01-15
[QUOTE=Mr_Grieves]You need two IP-adresses to that machine in case you want to host two diffrent DNS names on it.

You don't need two fysical interfaces though, you can do with virtual ones.
eth0 - 123.4.5.6/my_domain.com
eth0:1 - 321.4.5.6/my_second_domain.com

If you want to run a webserver for these domains, you may use virtual hosts in Apache.[/QUOTE]
I don't know why need two IP-address, you can bind two domain names to one IP-address

---

### Post by Zensunni on 2006-01-17
Bobyang,

When you say "bind two domains to one IP adress", do you mean that I would be able to have somebody type yohoo.com, then fishnfood.com in their browsers and get two different sites from my one IP adress and machine, or would the person have to type "yohoo.mydomain.com and fishnfood.mydomain.com"?

I haven't read up on this too much. So, when an ISP gives you two IP adresses, is there two physical wires that attach to your server, or is it virtual? My setup right now is a cable modem which plugs into a router, then the server hooks into the router. What would I need to change?

Thanks guys for the help. I'm using apache now and I'll be buying a book on it to  help me with the virtual hosting. I also realise this is a very unprofessional setup, but for now, I just want to get stuff working before I get my hands into real stuff.

---

### Post by admlv on 2006-01-17
Hi!
you can host as much webpages (every one with his own domain name example1.net exapmle2.net ....) as you need. simply define virtual hosts in your httpd.cong and make sure that these domain names ar pointed to your ip. Look in apashe documentation for correct syntax how to configure virtualhosts. 
If you want to have a mailserver foe multiplay domains then the easy way is set up postfix with mysql: [http://workaround.org/articles/ispmail-sarge/](http://workaround.org/articles/ispmail-sarge/) i have folowed this manual and it was easy.

---

### Post by bobyang on 2006-01-19
[QUOTE=Zensunni]Bobyang,

When you say "bind two domains to one IP adress", do you mean that I would be able to have somebody type yohoo.com, then fishnfood.com in their browsers and get two different sites from my one IP adress and machine, or would the person have to type "yohoo.mydomain.com and fishnfood.mydomain.com"?

I haven't read up on this too much. So, when an ISP gives you two IP adresses, is there two physical wires that attach to your server, or is it virtual? My setup right now is a cable modem which plugs into a router, then the server hooks into the router. What would I need to change?

Thanks guys for the help. I'm using apache now and I'll be buying a book on it to  help me with the virtual hosting. I also realise this is a very unprofessional setup, but for now, I just want to get stuff working before I get my hands into real stuff.[/QUOTE]

First, you need to apply two domain names, you can apply them on yahoo ([http://sbs.smallbusiness.yahoo.com/domains/)](http://sbs.smallbusiness.yahoo.com/domains/)), only $2.99/year now. Then you should set your ip address for your new domain on yahoo, both two domains record to the same ip address.
Second, on you local computer, execute "ping YOUR_DOMAIN_NAME", make sure you get the right destination ipaddress.
Third, create virtual hosts in apache's config file (httpd.conf)

If you still have question, you can send private message to me

---

### Post by jimwillsher on 2006-01-19
I have 12 websites hosted on my webserver, all on port 80. The DNS for each goes to the same IP.

My /etc/apache2/sites-available/default file looks like:

```
NameVirtualHost *:80

<VirtualHost *:80>
  ServerName www.jimwillsher.co.uk
  ServerAlias www.jwillsher.co.uk
  DocumentRoot /var/www/jimwillsher.co.uk
  ErrorLog /var/log/apache2/jimwillsher.co.uk/error_log
  CustomLog /var/log/apache2/jimwillsher.co.uk/access_log combined
  ErrorDocument 401 /Error401.html
  ErrorDocument 404 /Error404.html
  RewriteEngine on
  RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
  RewriteRule .* - [F]
</VirtualHost>

<VirtualHost *:80>
  ServerName www.bulkrenameutility.co.uk
  DocumentRoot /var/www/bulkrenameutility.co.uk
  ErrorLog /var/log/apache2/bulkrenameutility.co.uk/error_log
  CustomLog /var/log/apache2/bulkrenameutility.co.uk/access_log combined
  ErrorDocument 401 /Error401.html
  ErrorDocument 404 /Error404.html
  RewriteEngine on
  RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
  RewriteRule .* - [F]
</VirtualHost>

<VirtualHost *:80>
  ServerName www.chriswillsher.co.uk
  DocumentRoot /var/www/chriswillsher.co.uk
  ErrorLog /var/log/apache2/chriswillsher.co.uk/error_log
  CustomLog /var/log/apache2/chriswillsher.co.uk/access_log combined
  RewriteEngine on
  RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
  RewriteRule .* - [F]
</VirtualHost>

etc. etc. etc.

```

and this means all the serving is done by name not IP.

You can set up similar stuff for email using postfix and its virtual_domains stuff.

HTH,


Jim

---

### Post by jag164 on 2006-01-25
[QUOTE=bobyang]I don't know why need two IP-address, you can bind two domain names to one IP-address[/QUOTE]

You sure can, but if there would ever be a need to ensure a proper reverse dns lookup (some ssh, some mail server setups,etc...), you'd be better off setting up an IP per name.

---

### Post by MJN on 2006-01-25
'Better off setting an IP per name'? Clearly you've got a friendlier ISP than me as mine won't give me any more than one... ;)
 
In this situation, where we're talking about hosting a website, there's absolutely no reason why virtual server config will not suffice - this is what it was designed for and is in widespread use across the Internet.
 
JimWillsher, whilst your use of the /etc/apache2/sites-available/default file for all your virtual sites will technically work, you're really meant (in terms of Debian modularisation of these things) to have a seperate container within sites-available for each virtual site (these then being activated individually with a2ensite). You probably knew this already, but just pointing it out for interests sake really..
 
Mathew
 
P.S. Nice photos by the way!

---

### Post by jimwillsher on 2006-01-25
Hi Mathew,

Err...no, I didn't know this. My previous Apache setup had everything in the httpd.conf, so this sites-enabled folder is new to me. Should I split the file up? If so, where does the lonely little "NameVirtualHost *:80" line go - into each file, or somewhere else? For reference, here's the top of my file, with the remainder just more <virtualhsot> entries:

```

NameVirtualHost *:80

<VirtualHost *:80>
  ServerName www.jimwillsher.co.uk
  ServerAlias www.jwillsher.co.uk
  DocumentRoot /var/www/jimwillsher.co.uk
  ErrorLog /var/log/apache2/jimwillsher.co.uk/error_log
  CustomLog /var/log/apache2/jimwillsher.co.uk/access_log combined
  ErrorDocument 401 /Error401.html
  ErrorDocument 404 /Error404.html
  RewriteEngine on
  RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
  RewriteRule .* - [F]
</VirtualHost>

<VirtualHost *:80>
  ServerName www.bulkrenameutility.co.uk
  DocumentRoot /var/www/bulkrenameutility.co.uk
  ErrorLog /var/log/apache2/bulkrenameutility.co.uk/error_log
  CustomLog /var/log/apache2/bulkrenameutility.co.uk/access_log combined
  ErrorDocument 401 /Error401.html
  ErrorDocument 404 /Error404.html
  RewriteEngine on
  RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
  RewriteRule .* - [F]
</VirtualHost>

<VirtualHost *:80>
  ServerName www.broadband4blackford.co.uk
  DocumentRoot /var/www/broadband4blackford.co.uk
  ErrorLog /var/log/apache2/broadband4blackford.co.uk/error_log
  CustomLog /var/log/apache2/broadband4blackford.co.uk/access_log combined
  RewriteEngine on
  RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
  RewriteRule .* - [F]
</VirtualHost>

<VirtualHost *:80>
  ServerName www.braco-pylons.co.uk
  DocumentRoot /var/www/braco-pylons.co.uk
  ErrorLog /var/log/apache2/braco-pylons.co.uk/error_log
  CustomLog /var/log/apache2/braco-pylons.co.uk/access_log combined
  RewriteEngine on
  RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
  RewriteRule .* - [F]
</VirtualHost>

<VirtualHost *:80>
  ServerName www.braco-greenloaning.org.uk
  DocumentRoot /var/www/braco-greenloaning.org.uk
  ErrorLog /var/log/apache2/braco-greenloaning.org.uk/error_log
  CustomLog /var/log/apache2/braco-greenloaning.org.uk/access_log combined
  RewriteEngine on
  RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
  RewriteRule .* - [F]
</VirtualHost>


```


Jim

---

### Post by MJN on 2006-01-25
Hi Jim,
 
I know what you mean - I too had just about mastered the use of httpd.conf (at least as far as my needs required) and so the modularisation approach taken by Debian threw me a little and whilst it is possible to carry on as before (indeed there's no reason you can't stick everything in httpd.conf even - it's still parsed by default... for now ;)) it's sensible to go with the flow and align yourself with the way they've headed - who knows what tricks they've got round the corner.
 
So, in terms of your virtual sites config, it is important to remember that whilst the configuration files for these (and many other aspects e.g. what ports to listen on etc) may now be split up the main apache2.conf file (which is meant to cover general/overarching server configuration) now causes whatever is in the individual config files to also be parsed (this is done via the **INCLUDE** directives).
 
In response to your particular queries, the **NameVirtualHost:80[b] directive can go in either the apache2.conf or sites-available/default files. It's placed in the latter by default (I think) so keep it in there - it is thus assumed that the 'main' site will always be available/enabled. What's important is that it doesn't go inside a [B]<VirtualHost></VirtualHost>** container otherwise it would only be applicable to that one site (and thus non-sensicle in terms of its purpose).
 
As far as the per-site configuration for your virtual sites go there are many ways to skin this cat (including how you've done it, but it's not in keeping with the modular approach as discussed) however I would suggest creating files in sites-available named after your sites e.g. **sites-available/bulkrenameutility**, **sites-available/broadband4blackford** etc - call them what you like it doesn't really matter (within the constraints of file system naming rules of course). Then, inside each file you simply place the appropriate **<VirtualHost></VirtualHost>** container. Thus, at the end of it, your files in sites-available/ will each contain there own specific <VirtualHost> container applicable to that site (keep sites-available/default for your jimwillsher.co.uk config i.e. don't rename it - you could but no point in straying from the intended convention).
 
All that is left to do now is instruct Apache to enable all of your virtual sites. If you look in Apache2.conf you'll see it contains an INCLUDE statement referencing anything that appears **sites-enabled/**. Looking in **sites-enabled/** you'll see you've got a symlink called 00default (this is so named to ensure it's parsed first, and thus the config therein is used for all sites whose name doesn't match a specific virtualhost) which simply points to **sites-available/default**. You need to create similar symlinks to your other files in sites-available. You can do this manually although Apache has its own tools to accomplish this called a2ensite and a2dissite (I think you may need to run these from within sites-available/). For example, you'd run **a2ensite /etc/apache2/sites-available/bulkrenameutility** - this will add a symlink and ensure Apache includes the necessary config. Converseley, using a2dissite <file> will remove its configuration.
 
Remember to reload/restart Apache for the changes to take effect. Incidentally, the inclusion of modules has also been ..err.. modularised thus you'll see something similar going in in mods-available/ and mods-enabled/. In this case, a2enmod and a2dismod are used to manage these... but we'll leave this for another day! ;)
 
I haven't looked into why Debian have gone down the modular route however I suspect it may have something to do with the ever-increasing power and functionality of Apache and the associated problems of trying to configure an entire system within a single area. In a similar vein to programming methodology migrating to object-oriented programming, modularisation attempts to simplify things by narrowing down how much you have to do in one hit...
 
Hope that clarifies things a little. If not, or if you want me to take your config further with a specific example just shout.
 
Mathew

---

### Post by jimwillsher on 2006-01-25
Perfect, thank you!

I've now split my "default" as you suggested, and now have multiple files, one per site.

The a2ensite doesn't like the pathname, it just wants the filename (e.g. bulkrenameutility.co.uk) so that threw me, but all is working nicely now.

I must admit, I do like the modular route. My httpd.conf on RedHat was unweildy, and it took ages to find anything, but now it's all quite compact and well structured.

I suspect the ssl file would need the same, though I only have one ssl site defined so it's not an issue:

```

NameVirtualHost *:443
<VirtualHost *:443>
        ServerName www.jimwillsher.co.uk
        DocumentRoot /var/www/jimwillsher.co.uk
        ServerAdmin webmaster@jimwillsher.co.uk
        SSLEngine On
        SSLCertificateFile /path/to/apache.pem
</VirtualHost>

```

Thanks again!



Jim

---

### Post by MJN on 2006-01-25
[quote=jimwillsher]Perfect, thank you!
 
I've now split my "default" as you suggested, and now have multiple files, one per site.
 
The a2ensite doesn't like the pathname, it just wants the filename (e.g. bulkrenameutility.co.uk) so that threw me, but all is working nicely now.
[/quote]
 
Ah, okay - my bad.
 
> I must admit, I do like the modular route. My httpd.conf on RedHat was unweildy, and it took ages to find anything, but now it's all quite compact and well structured.
 
Yeah, once you get used to it you start to see the advantages. Certainly if you're working on one area (e.g. one virtual site) then it certainly does help not to be bogged down with irrelevant config in front of your eyes.
 
> I suspect the ssl file would need the same, though I only have one ssl site defined so it's not an issue:
 
Well.. it's funny you should say that. Believe it or not you're verging on opening a right can of worms there...
 
**It's impossible to use SSL with *multiple* virtual hosts.**
 
The reason being is that SSL operates at the Transport layer and hence all the handshaking and session establishment occurs before we get as far/high as HTTP. Thus, in order for Apache to know which certificates and configuration to use for a particular SSL session to be established it needs to know which site is being called for - this info is in the HTTP request header. However, HTTP is wrapped up inside SSL hence such info is only available once the SSL session has been established. Chicken and egg, and SSL has just shot your chicken... ;)
 
In your case, put your SSL config in the sites-available/default file (seperate <VirtualHost *:443> container as currently) as this'll be where Apache will look for the SSL config - remember as mentioned above sites-available/default, thanks to sites-enabled/00default referencing it, will be assumed the 'default' site - this applies to 443/SSL connections too. It also makes sense for you too given the logical benfit of having all jimwillsher.co.uk config together in the same bucket, regardless of what port your clients are coming in on.
 
All the best,
 
Mathew
 
P.S. I just checked out your [https://www.jimwillsher.co.uk/]("https://www.jimwillsher.co.uk/") site and whilst not wanting to come across as an eternal nit-picker (as I'm sure the setup suits your needs) it's not 'the norm' for your webserver to be carrying only the certificate of your Certificate Authority (even if they are the same machine). You would normally create a cert for your webserver and get this *signed* by your CA. Then your webserver would issue its own certificate to clients, along with a the certificate of your CA (i.e. it'd send both because, being private, your client can't get the CA cert from anywhere else). The end effect would be no different to now (i.e. the root CA, being untrusted, would throw up a warning) but this would allow your CA to have a 2048bit key whilst your web server uses a 512/1024bit key (as now) which is compatible with more browsers. Besides which, this is more in keeping with the modular approach you're now a supporter of... ;) If you look at my certificates at [https://secure.newtonnet.co.uk/]("https://secure.newtonnet.co.uk/") you should see what I mean...

---

### Post by MJN on 2006-01-27
Jim,
 
I dug out a nice miniHowTo with a walkthrough of server certs for webservers which I recommend taking a look at:
 
[http://www.vanemery.com/Linux/Apache/apache-SSL.html]("http://www.vanemery.com/Linux/Apache/apache-SSL.html")
 
Mathew

---

### Post by jimwillsher on 2006-01-27
Bookmarked!!!! Looks excellent, and the certificate-protection of a subfolder is something I've been after for a while, for my administration folder.

Thank you!


Jim

---

### Post by jimwillsher on 2006-02-22
Sorry to drag up an old thread, but...

All my virtual hosts stuff is working fine, with one exception. If I enter the IP address of my server intoa  browser I get the SECOND website displayed. What I really want dispalyed is a specific virtual host  (or mre precisely, I want a folder called "Default" to become the DocRoot).

My 000-default file contains

```
NameVirtualHost *:80
RewriteEngine on
RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
RewriteRule .* - [F]

```

and my other files contain normal stuff like:

```



<VirtualHost *:80>
  ServerName www.bulkrenameutility.co.uk
  DocumentRoot /var/www/bulkrenameutility.co.uk
  ErrorLog /var/log/apache2/bulkrenameutility.co.uk/error_log
  CustomLog /var/log/apache2/bulkrenameutility.co.uk/access_log combined
  ErrorDocument 401 /Error401.html
  ErrorDocument 404 /Error404.html
  RewriteEngine on
  RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
  RewriteRule .* - [F]
</VirtualHost>

```

How can I configure Apache2 so that access via direct IP address goes to a specific site?

Many thanks,


Jim

---

### Post by caraboy on 2006-02-23
I have another problem, I set up a server with bind and apache, and I am using virtual hosting to host up 2 domains. I am a master server, my domain registrant  forwards domain queries to my ns.myprimarydomain.com. But if i need to set up a subdomain I need to set it up in named.conf and reload the zones everytime I modify, add a subdomain, then I have to wait for the dns to refresh at my isp... until the domain can be accessed widely. So, how are isps doing, because, for example [www.lx.ro](www.lx.ro) (romanian hosting company) adds instantly a new subdomain, and is available right away (ex: name.lx.ro). I guess they are not refreshing bind everytime... or restart the server with every new registrant... So, how are they doing?

PS-> hope I made myself understood, with my enghlish. :P

---

### Post by WildTangent on 2006-04-10
[QUOTE=jimwillsher]Sorry to drag up an old thread, but...

All my virtual hosts stuff is working fine, with one exception. If I enter the IP address of my server intoa  browser I get the SECOND website displayed. What I really want dispalyed is a specific virtual host  (or mre precisely, I want a folder called "Default" to become the DocRoot).

My 000-default file contains

```
NameVirtualHost *:80
RewriteEngine on
RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
RewriteRule .* - [F]

```

and my other files contain normal stuff like:

```



<VirtualHost *:80>
  ServerName www.bulkrenameutility.co.uk
  DocumentRoot /var/www/bulkrenameutility.co.uk
  ErrorLog /var/log/apache2/bulkrenameutility.co.uk/error_log
  CustomLog /var/log/apache2/bulkrenameutility.co.uk/access_log combined
  ErrorDocument 401 /Error401.html
  ErrorDocument 404 /Error404.html
  RewriteEngine on
  RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
  RewriteRule .* - [F]
</VirtualHost>

```

How can I configure Apache2 so that access via direct IP address goes to a specific site?

Many thanks,


Jim[/QUOTE]

Sorry to dredge this up again...but I'm having the same problem as this guy, and another one: going to my secondary domain without specifying a filename or folder takes me to my normal webroot, like going to [www.otherdomain.tld](www.otherdomain.tld) takes me to [www.normaldomains.tld](www.normaldomains.tld) but [www.otherdomain.tld/index.html](www.otherdomain.tld/index.html) takes me to its normal place....

-Wild

---

### Post by jimwillsher on 2006-04-10
These are my site files (now that everything is working)

default:
<VirtualHost *:80>
  ServerName 82.152.114.61
  DocumentRoot /var/www/default
  ErrorLog /var/log/apache2/default/error_log
  CustomLog /var/log/apache2/default/access_log combined
  RewriteEngine on
  RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
  RewriteRule .* - [F]
</VirtualHost>


Site one:
<VirtualHost *:80>
  ServerName [www.bulkrenameutility.co.uk](www.bulkrenameutility.co.uk)
  ServerAlias bulkrenameutility.co.uk
  DocumentRoot /var/www/bulkrenameutility.co.uk
  ErrorLog /var/log/apache2/bulkrenameutility.co.uk/error_log
  CustomLog /var/log/apache2/bulkrenameutility.co.uk/access_log combined
  ErrorDocument 401 /Error401.html
  ErrorDocument 404 /Error404.html
  RewriteEngine on
  RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
  RewriteRule .* - [F]
</VirtualHost>

Site two:
<VirtualHost *:80>
  ServerName [www.jimwillsher.co.uk](www.jimwillsher.co.uk)
  ServerAlias jimwillsher.co.uk *.jimwillsher.co.uk
  DocumentRoot /var/www/jimwillsher.co.uk
  ErrorLog /var/log/apache2/jimwillsher.co.uk/error_log
  CustomLog /var/log/apache2/jimwillsher.co.uk/access_log combined
  ErrorDocument 401 /Error401.html
  ErrorDocument 404 /Error404.html
  RewriteEngine on
  RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
  RewriteRule .* - [F]
</VirtualHost>


etc

My apache2.conf contains (at the end)

# JRW Force virtual-hosts
NameVirtualHost *:80

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/[^.#]*





Everything works well for me now. Does this help?


Jim

---

### Post by WildTangent on 2006-04-10
I ended up getting it to work in the end, I forgot a / on the DocumentRoot attribute ](*,) 

-Wild

---

