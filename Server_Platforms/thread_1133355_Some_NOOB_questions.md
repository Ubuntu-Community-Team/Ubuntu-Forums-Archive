---
title: "Some NOOB questions"
date: 2009-04-22
forum: Server Platforms
---

### Post by hanzgroove on 2009-04-22
Hi All,

I have some noobish questions to ask:

1. I'm running ubuntu server 8.10. Around this forum I have read that ubuntu 8.04 is the "LTS" version. I understand that it means "Long Term Support" Is there any difference in terms of the support you get for 8.10 vs 8.04? I'm not clear on this.

2. I have a server at 1and1 and it looks as though 1and1 tries to communicate with my server for DHCP puposes on port 67 & 68. Is this necessary? Can I just block those ports in my firewall? (Btw, no documentation from 1and1 on this)

3. I have moved my SSH connection port to a higher number, locked down the firewall to only use the essential ports, installed deny hosts, disabled root login, installed rkhunter and chrootkit. No mail server running. Only Apache and MySQL. Aside from the security of web apps, am I "SAFE" from a Linux perspective? Or rather, am I still "hackable"?

---

### Post by lavinog on 2009-04-22
LTS means that security updates will be available for 3 years (5 for servers) instead of 18 months.
This doesn't mean that the software in the repositories will be the latest versions.

I am not familiar with 1and1 but a quick search on google shows other users asking the same question...one response it has something to do with their recovery and reimage architecture.
does your box have a dhcp server?

You should just assume you are hackable unless you disconnect the network cable. (or wireless)
Keeping tabs on your activity logs will help point out any vunerabilities.
If you are hosting a website, you become a bigger target for the zombies.
watch your website logs for activity. Keep your webapps up to date.
also I find denying all website activity that doesn't use a legit url to help out alot (don't let them view your site by just using an ip address.)

---

### Post by hanzgroove on 2009-04-22
Thanks for the quick reply : )

> I am not familiar with 1and1 but a quick search on google shows other users asking the same question...one response it has something to do with their recovery and reimage architecture.
does your box have a dhcp server?I ran ps aux and extracted this line:

root      2748  0.0  0.0   6480   744 ?        Ss   Apr12   0:06 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/l

Does that mean I have a DHCP server running?

> also I find denying all website activity that doesn't use a legit url to help out alot (don't let them view your site by just using an ip address.)Awesome, I've been wondering if that was possible. I will try to google around for how to do it.

Thanks again for your help...

---

### Post by lavinog on 2009-04-22
> **hanzgroove said:**
> Thanks for the quick reply : )

I ran ps aux and extracted this line:

root      2748  0.0  0.0   6480   744 ?        Ss   Apr12   0:06 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/l

Does that mean I have a DHCP server running?

No that is the client.
I don't think the dhcp server is setup by default.

> 
Awesome, I've been wondering if that was possible. I will try to google around for how to do it.

Thanks again for your help...
I don't know how much help I can be, because my webserver has been through alot of changes, and I don't know what the normal setup is anymore.
If you are using apache:
in /etc/apache2 i have a folders named sites-enabled and sites-available
sites-available has config file for each site I host.
sites-enabled has symlinks pointing to those config files (this lets me easily disable sites)
say i have a site mysite.com:
I would have a config file /sites-available/mysite.com:
```

<VirtualHost *>
DocumentRoot /storage/websites/mysite.com/www
LogLevel debug
ServerName mysite.com
ServerAdmin me@mysite.com
ServerAlias www.mysite.com
Options  MultiViews
TransferLog /storage/websites/mysite.com/Access.log
ErrorLog /storage/websites/mysite.com/Error.log
</VirtualHost>

```

I also have /sites-available/default
```

<VirtualHost *>
#        ServerAdmin webmaster@localhost
	ServerName myserver
	ServerAlias myserver.homeip.net
	ServerAlias www.myserver.homeip.net

	DocumentRoot /storage/websites/default
        
	<Directory />
      	Options None
      	AllowOverride None
      	Order deny,allow
      	Deny from all
      	</Directory>

	<Directory "/storage/websites/default">
                Options -MultiViews FollowSymLinks
                AllowOverride None
		Order deny,allow
		deny from all
allow from myhome.homeip.net
allow from 192.168.1
TransferLog /storage/websites/default/Access.log
        ErrorLog /storage/websites/default/Error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel debug

#        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

        </Directory>


```
the "Order deny,allow" and "deny from all" prevents users from using the default page
these lines:
```

allow from myhome.homeip.net
allow from 192.168.1

```
allow me to access the site from my home or lan

now i make a symlink to the enabled folder, but like the rc?.d scripts I prefix the link name with a number to indicate the order I want it to load.
the config file with the lowest prefix will be the default site
```

lrwxrwxrwx 1 root root 33 2008-03-07 14:06 **10-default** -> ../sites-available/default
lrwxrwxrwx 1 root root 49 2008-08-23 18:05 **20-mysite.com** -> /etc/apache2/sites-available/mysite.com

```

---

### Post by hanzgroove on 2009-04-22
I was able to block access via IP address by using a stripped down version of your code in /etc/apache2/sites-available/default:

```
<VirtualHost *:80>
  
    <Directory />
    Options None
    AllowOverride None
    Order deny,allow
    Deny from all
    </Directory>

</VirtualHost>
```Result: 403 Forbidden when pulling up the IP address on a browser. I don't need any sort of access via IP so this works nicely.

Thanks again! I appreciate your help...

---

