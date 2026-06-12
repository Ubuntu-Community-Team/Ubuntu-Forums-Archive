---
title: "Apache2.4 NameVirtualHost"
date: 2015-10-24
forum: Server Platforms
---

### Post by jaesun on 2015-10-24
Ubuntu 14.04 LTS Server

I am trying to figure out where to put the NameVirtualHost directive.  I check all the conf files, and I don't even see it declared anywhere.  I get no warnings when I start apache or reload/restart.

I don't have a /etc/apache2/httpd.conf file (as expected as per [https://help.ubuntu.com/lts/serverguide/httpd.html](https://help.ubuntu.com/lts/serverguide/httpd.html)).  

I checked ports.conf

```
Listen 80

<IfModule ssl_module>
        Listen 443
</IfModule>


<IfModule mod_gnutls.c>
        Listen 443
</IfModule>
```

I check all my sites .conf, nothing there either.

All my site .conf files are just wrapped around <VirtualHost *:80></VirtualHost>

Now, everything is working right now.  but so far I am only testing on a local network (so test.domain.com points to the server internally).  But when it goes live, I think I need to add the NameVirtualHost to account for both the internal and external IPs

```
 # Example from https://httpd.apache.org/docs/2.2/vhosts/examples.html
[COLOR=#000000][FONT=Courier New]NameVirtualHost 192.168.1.1[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]NameVirtualHost 172.20.30.40[/FONT][/COLOR]

[COLOR=#000000][FONT=Courier New]<VirtualHost 192.168.1.1 172.20.30.40>[/FONT][/COLOR][COLOR=#000000][FONT=Courier New]
ServerName test.domain.com
# everything else
[/FONT][/COLOR][COLOR=#000000][FONT=Courier New]</VirtualHost>[/FONT][/COLOR]
```

I don't see the declarations in apache2.conf, port.conf, conf-enabled, sites-enabled.

Am I missing something here?

---

### Post by TheFu on 2015-10-24
Most people create a new conf file for each virtual domain. That makes it easier to enable/disable each without impacting some other  virtual-domain.  They should be placed into the site-available/ directory.   Then when you want to enable it, create a softlink to that file in the sites-enabled/  directory.

---

### Post by SeijiSensei on 2015-10-24
NameVirtualHost refers to the server name portion of the URL.  Apache determines which site to serve up based on the URL so that many sites can coexist on a single IP address.  As TheFu says, you should create a separate servername.conf file in /etc/apache2/sites-available/ and enable it with either the command "sudo a2ensite servername" or by simply creating a symbolic link in /etc/apache2/sites-enabled pointing to the corresponding file.

Here's a representative virtual host configuration from one of my servers:
```

<VirtualHost *:80>
ServerName              www.example.com
ServerAlias             example.com demo.example.com
ServerAdmin             webmaster@example.com
TransferLog             logs/access_log-example.com
ErrorLog                logs/error_log-example.com
CustomLog               logs/referer_log-example.com "%h %{referer}i -> %U"
DocumentRoot            /path/to/the/website/root

<Directory "/path/to/the/website/root">

        AllowOverride           All
        Options                 Indexes FollowSymLinks 
        IndexOptions            FancyIndexing SuppressColumnSorting
        IndexOrderDefault       Descending Date

</Directory>

</VirtualHost>

```
Requests for [www.example.com](www.example.com), example.com, or demo.example.com will all be served with the files in /path/to/the/website/root.

If you've already modified any of the files in the /etc/apache2 directory, I suggest you uninstall Apache with the "--purge" option and reinstall it.  Then follow the procedure of using the /sites-available/ and /sites-enabled/ architecture.

---

### Post by jaesun on 2015-10-24
Yes, I understand that.  I have my site declarations in their own .conf file (I have 5 of them)

But I am wondering where the [COLOR=#000000][FONT=Courier New]**NameVirtualHost **directive goes.

Or do I not set the [/FONT][/COLOR]NameVirtualHost anymore?[COLOR=#000000][FONT=Courier New]

[/FONT][/COLOR]The server will have 2 IP address, 1 external, 1 internal, similar to as shown in the below example from the apache docs (bolded)

```
[B][COLOR=#000000][FONT=Courier New]NameVirtualHost 192.168.1.1[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]NameVirtualHost 172.20.30.40[/FONT][/COLOR][/B]

[COLOR=#000000][FONT=Courier New]<VirtualHost 192.168.1.1 172.20.30.40>[/FONT][/COLOR][COLOR=#000000][FONT=Courier New]
ServerName test.domain.com
# everything else
[/FONT][/COLOR][COLOR=#000000][FONT=Courier New]</VirtualHost>[/FONT][/COLOR]
```

I don't know where I put the [COLOR=#000000][FONT=Courier New]**NameVirtualHost **directive.  Do I put that in each site.conf file?  I don't see that set anywhere in my apache files.  I thought it would be port.conf[/FONT][/COLOR]

---

### Post by darkod on 2015-10-24
I'm not apache expert but I think you do not need that any more and that's confusing you. Many tutorials exist with the older syntax. Using the .conf files now is enough and you set the port and/or IP in there.

---

### Post by jaesun on 2015-10-24
> **darkod said:**
> I'm not apache expert but I think you do not need that any more and that's confusing you. Many tutorials exist with the older syntax. Using the .conf files now is enough and you set the port and/or IP in there.

That makes sense. everything seems to work fine right now at least on the internal network (site isn't public yet) so I figured it was set somewhere that I couldn't find.  But this would explain why

---

### Post by SeijiSensei on 2015-10-24
NameVirtualHost was removed in 2.4.  

"The NameVirtualHost directive no longer has any effect, other than to emit a warning. Any address/port combination appearing in multiple virtual hosts is implicitly treated as a name-based virtual host. "

[https://httpd.apache.org/docs/2.4/upgrading.html](https://httpd.apache.org/docs/2.4/upgrading.html)

---

### Post by TheFu on 2015-10-24
> **SeijiSensei said:**
> 

[https://httpd.apache.org/docs/2.4/upgrading.html](https://httpd.apache.org/docs/2.4/upgrading.html)

Reviewing the **upgrade notes** and **release notes** for any complex software prior to installation is definitely a **best practice.**

---

