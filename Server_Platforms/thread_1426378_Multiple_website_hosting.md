---
title: "Multiple website hosting"
date: 2010-03-10
forum: Server Platforms
---

### Post by kernelnewbie1 on 2010-03-10
I wish to **host multiple website** on single apache server , please give me a step by step instruction 
on how to do it
_i tried a lot using google , but failed_
i want each website to have different ip address
--please help me --

---

### Post by Barriehie on 2010-03-10
> **kernelnewbie1 said:**
> I wish to **host multiple website** on single apache server , please give me a step by step instruction 
on how to do it
_i tried a lot using google , but failed_
i want each website to have different ip address
--please help me --

What you're going to need to do is setup IP-based virtual hosting.  This can be done with either multiple network connections or virtual interfaces.  Which are you planning to use?  I'ld suggest setting up one and then the rest will follow suit.  Do you have apache setup to where [http://localhost/](http://localhost/) works?

---

### Post by TwoWordz on 2010-03-10
Hello kernelnewbie1,

Hosting a bunch of websites on ubuntu is quite easy.

You need to create the site configuration in /etc/apache2/sites-available/

I create a configuration file for every site, calling it by it's FQDN. So I have site1.example.com, site2.example.com. 

In the configuration file, I define where the site is and where to log:


```
<VirtualHost *:80>
        DocumentRoot /var/www/site1.example.com
        ServerName site1.example.com
        ServerAlias site1
        ErrorLog /var/log/apache2/site1/site1.log
        LogLevel error
        CustomLog /var/log/apache2/site1/access.log combined
        ServerSignature On

<location>
site configuration ....
</location>

</VirtualHost>
```

Enable them with a2ensite site1.example.com

Do it for every site, then create alias (CNAME) records for all your sites in your DNS.

Apache will figure out where to send your visitors.

TW

---

### Post by kernelnewbie1 on 2010-03-10
> What you're going to need to do is setup IP-based virtual hosting. This can be done with either multiple network connections or virtual interfaces. Which are you planning to use? I'ld suggest setting up one and then the rest will follow suit. Do you have apache setup to where [http://localhost/](http://localhost/) works?I wish to use virtual interfaces.

================================

what i have done till now :

# mkdir  /var/www/site2

#sudo nano /etc/apache2/sites-enabled/site2.com
// below is that file
```

<VirtualHost *:80>
    ServerAdmin webmaster@localhost
        ServerName www.site2.com
    DocumentRoot /var/www/site2/
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/site2/>
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

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
  ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```// then ...
# cd /etc/apache2/sites-available/
# ln -s /etc/apache2/sites-enabled/site2.com

// wrote an entry in /etc/hosts
```

127.0.0.1       localhost
**[COLOR=Red]127.0.0.1       www.site2.com[/COLOR]**
127.0.1.1       intel

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```# /etc/init.d/apache2 restart
=========================
now [www.site2.com]("http://www.site2.com") works
but its ip is 127.0.0.1 , but i want it to be on some other ip
=========================

Qusetions :
1) Is my procedure correct ?

2) How do i change ip of site2

3) Are there any problems if i host multiple website on same ip

4)> create alias (CNAME) records for all your sites in your DNS.   how do i do this?

---

### Post by TwoWordz on 2010-03-11
With virtual interfaces you do not need multiple IP addresses. How many addresses do you have anyway?

You do not need site2 in the hosts file.

There are no problem hosting multiple sites on one IP. I run 4 websites on 1 server, single IP, in a demanding environment. 

I expect you have multiple domain names hosted on the same registrar? Is this a public website or just a website you want to run on a local network? If it's local, which DNS server are you using?

If it's only local, the simplest way it to put all the websites in /var/www and keep the default configuration. Then you can do [http://server/site](http://server/site).

---

### Post by i.r.id10t on 2010-03-11
I would use ISPConfig and I would follow the "perfect debian server set up" howto as prep to using ISPConfig.  Thin there is a similar guide for Ubuntu...

---

### Post by R.Bucky on 2010-05-20
I host over a dozen sites from my server without issue. I create a separate VirtualHost file for a each site. It provides more control rather than placing all the sites in one file. Here is the write-up ([http://rbucky.com/blog/hosting-2-domains-with-1-server/](http://rbucky.com/blog/hosting-2-domains-with-1-server/))

---

### Post by macmike on 2010-05-21
Mark:

I am wanting to host 3 sites:

[www.wilmingtoncoc.com](www.wilmingtoncoc.com)
[www.mikealrhughes.com](www.mikealrhughes.com)
[www.biblematters.net](www.biblematters.net)

The Wilmingtoncoc site will be either a myBB or a WordPress site.
The mikealrhughes.com site will be ftped with Dreamweaver generated files.
The biblematters.net site will be a mailman mailing list site.

I am having all kinds of trouble getting this going. I have installed Ubuntu 10.04, Webmin, Proftpd and WordPress I haven't been able to get any of this going. I get a warning of no Virtual Host *:80 and one  with my public ip and :80 no virtual host. Is there anyway for someone to get this setup for me and then make me an iso to install and just make changes like adding my ip and the program Dyndns.com wants to watch my DNS for me? I would love to get this to where I could remote into the server which I haven't been able to either.

My biggest complaint about most Linux tutorials is they assume you know the commands and location of files which I don't.

Thanks for any help.

Mike Hughes
mail (at) mikealrhughes (dot) com.

---

