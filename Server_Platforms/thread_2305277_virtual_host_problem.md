---
title: "virtual host problem"
date: 2015-12-04
forum: Server Platforms
---

### Post by Joe67 on 2015-12-04
my vps host has merged with another company. today i was switched to another ip...

ive tryed updating my vitual hosts and nameservers etc, when i restart appache 2 i get the following:



[Fri Dec 04 17:46:05 2015] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Fri Dec 04 17:46:05 2015] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Fri Dec 04 17:46:05 2015] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Fri Dec 04 17:46:05 2015] [warn] VirtualHost IP REMOVED:80 overlaps with VirtualHost domainremoved.com:80, the first has precedence, perhaps you need a NameVirtualHost directive
[Fri Dec 04 17:46:05 2015] [warn] NameVirtualHost ipremoved:80 has no VirtualHosts


can anyone help?

everything was working before, only this to change is the ip as my host moved it all over

now getting

[Fri Dec 04 19:08:01 2015] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Fri Dec 04 19:08:01 2015] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Fri Dec 04 19:08:01 2015] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Fri Dec 04 19:08:01 2015] [warn] _default_ VirtualHost overlap on port 80, the first has precedence

---

### Post by darkod on 2015-12-04
It seems to be a conflict of two identical virtual hosts using the same port 80, so it complains. Are you sure there no two identical hosts?

Double check the sites-enabled and sites-available .conf files for the hosts to make sure there are no identical ones.

You might have more info in /var/log/apache2/error.log

---

### Post by Joe67 on 2015-12-04
all i done with the virutalhosts that were working fine before is update the ip and kept the same port as was already there, ive also updated the ip in other folders such as [COLOR=#000000][FONT=Calibri]ports.conf

no more info in error.log


ive since changed the virtual host from ip and port to [/FONT][/COLOR]<VirtualHost *:80>

---

### Post by darkod on 2015-12-04
Usually you don't need to put the IP in there, only VirtualHost. Is it working now after that change?

How many sites do you have, only one?

---

### Post by Joe67 on 2015-12-04
its not helped, have five websites, only the main one shows for all ips.. its got something to do with the switch over, i never used NameVirtualHost *80   before, though my host mentioned

"[COLOR=#212121][FONT=verdana]You will have a NameVirtualHost directive in one of your httpd.conf or included files, it will include your VPSs old IP. You must change that in addition to the VirtualHost blocks."

httpd.conf is empty[/FONT][/COLOR]

---

### Post by darkod on 2015-12-04
I don't think apache2 on ubuntu uses httpd. And according to some search results in google, the NameVirtualHost is not necessary too. However, there should not be a line related to any IP in /etc/apache2/ports.conf.

Can you post your ports.conf content and few of the sites .conf files? You can cover up any sepcific info if you don't want to publish it, just make sure you don't cover up too much. Someone might get an idea by checking out the files.

Also it might be relevant whether you are using the apache 2.4 or earlier. There were some changes done in 2.4.

You want the sites to be linked to a specific IP and show only for that one?

PS. In fact, upon further investigation it seems the NameVirtualHost option in ports.conf helps with this error. Make sure you have this in your ports.conf:
```
NameVirtualHost *:80
```

Restart apache after that and see if it still reports the error.

---

### Post by Joe67 on 2015-12-04
[COLOR=#000000][FONT=Times New Roman][I][B]its  apache 2.2.22

i had them setup with the ip and port before as it worked and it was all i knew at the time, it doesnt need to be.. heres how they are setup[/B]


```
[/I][/FONT][/COLOR]<VirtualHost *:80>       ServerAdmin soulfly@
	ServerName .com
       ServerAlias www..com


DocumentRoot /home/removed/public_html/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/removed/public_html/>
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


[COLOR=#000000][FONT=Times New Roman][I]
```

```
[/I][/FONT][/COLOR]<VirtualHost *:80>       ServerAdmin soulfly@.com
	ServerName .co.uk
       ServerAlias www.removed.co.uk


	DocumentRoot /home/removed/public_html/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/removed/public_html/>
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


[COLOR=#000000][FONT=Times New Roman][I]
```

```
[/I][/FONT][/COLOR]<VirtualHost *:80>    ServerAdmin joe@com
	ServerName .com
	ServerAlias www..com


DocumentRoot /home/removed/public_html/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/removed/public_html/>
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


[COLOR=#000000][FONT=Times New Roman][I]
```

```
[/I][/FONT][/COLOR]<VirtualHost *:80>       ServerAdmin joe.tk
	ServerName .tk
       ServerAlias www..tk


DocumentRoot /home/removed/public_html/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/removed/public_html/>
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


[COLOR=#000000][FONT=Times New Roman][I]
```


```
[/I][/FONT][/COLOR]<VirtualHost *:80>        ServerAdmin joe@.co.uk
        ServerName j.co.uk
        ServerAlias www..co.uk
        DocumentRoot /home/js/public_html/
        RewriteEngine on
        RewriteCond %{HTTP_HOST} !^www\.\.co.uk$ [NC]
        RewriteRule ^(.*)$ http://www..co.uk/$1 [R=301,L]
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /home/removed/public_html/>
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

</VirtualHost>[COLOR=#000000][FONT=Times New Roman][I]
```



[/I][/FONT][/COLOR]

---

### Post by darkod on 2015-12-04
I'm no apache expert but that looks good to me. Now only the ports.conf content is missing. See the PS in my previous post if you missed it, because I added it later. If that doesn't help I'm out of ideas right now...

---

### Post by Joe67 on 2015-12-04
i knew i missed something lol

here it is

```
# If you just change the port or add more ports here, you will likely also# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz


NameVirtualHost ipremoved:80
Listen 80


<IfModule mod_ssl.c>
    # If you add NameVirtualHost ipremoved:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost ipremoved:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>


<IfModule mod_gnutls.c>
    Listen 443
</IfModule>



```

---

### Post by darkod on 2015-12-04
> NameVirtualHost ip:80

That's the problem. You need to tell it to use virtual hosts on any ip. Set it to:
```
NameVirtualHost *:80
```

Restart apache.

---

### Post by Joe67 on 2015-12-04
well spotted mate, ive done that. those errors are gone now, websites still wont load, except the main one

i get this old error, dont think its anything to do with current problem, as it was there before

```
[Sat Dec 05 00:56:47 2015] [warn] The Alias directive in /etc/apache2/apache2.co                                                                                                                                                             nf at line 240 will probably never match because it overlaps an earlier Alias.


```

---

### Post by darkod on 2015-12-04
OK, step by step. :)

It's a silly question, but is the DNS modified after you changed IPs/provider? If you do nslookup or dig for those domains, does the result show the correct IP?

Otherwise, your ServerName and ServerAlias directives look correct.

If you want sites to be linked to specific public IP (except the main site), you could also try with this:
```
<VirtualHost 11.22.33.44:80>
```

If I'm not mistaken that should link that website to that IP and it should open only for that IP. But it should work as it is also... You don't actually need to link sites to single IP. But you do have to have the correct DNS record for the domain and the www.

PS. And make sure the ServerName and ServerAlias in each site config file are unique, they should have the value related to that site only. Unless you are trying something "special" with the configs... That error about Alias is probably related to that.

---

### Post by Joe67 on 2015-12-04
my domain names are with a different host, ive updated the ips to match new vps server ip... ive done a dns lookup, the ip is correct

roger that :D ill make sure all good



EDIT: not sure what you mean mate, my vps merged with another company, i was running on the same ip etc for a few more weeks and today they moved everything over to a new machine

vps host have asked for the domain names so they can check from monitering stations.. longer it takes the more seo damage :(

---

### Post by darkod on 2015-12-04
I meant the config files you posted in post #7. Each site has its own file in sites-available right? For example domain.com.conf. Inside this domain.com.conf the directives should be:
```
ServerName domain.com
ServerAlias www.domain.com
```

For domain2.com they would have different, unique values. Because the domain name is different, in its .conf file you should adjust the parameters accordingly.

That Alias message seems to say there is ServerAlias that repeats.

Depending how the provider has the VPS setup, could it be mixing it up from another customer? But that would be pretty rare, they need to make sure these things are separate and can't get mixed up between different customers.

If the DNS resolves good, I am running out of ideas... See with their support if it could be a result of the migration. You say they moved everything to a new machine. They might have done some "damage" in the process.

---

### Post by Joe67 on 2015-12-04
heres what i got


> [COLOR=#212121][FONT=verdana]The returned messages would indicate that the configuration is both correct and wrong at the same time. I still believe that your NameVirtualHost *:80 does not match the <VirtualHost ... declaration.[/FONT][/COLOR]

[COLOR=#212121][FONT=verdana]If this is a single IP (no port), then make sure the NameVirtualHost is the same, just the IP rather than :80 on the end. If it is an IP and port, then the exact IP and port must be used in the NameVirtualHost.[/FONT][/COLOR]


---

### Post by darkod on 2015-12-04
That makes no sense. The <VirtualHost declaration in your .conf files is identical. It's *:80 just like the NameVirtualHost.

Just a thought (in lack of other ideas), did you try to disable and again enable the sites that are not working. You know how to do that in apache, right? I believe 2.2 used the same commands as 2.4, the a2ensite and a2dissite commands.

Also, double check that sites-enabled looks OK (it contains symlinks for all the sites)...

---

### Post by Joe67 on 2015-12-04
haha, i was thinking the same, thought id get a second opinion

yes mate, i know how to do that, ill give it another try.. though if one is working the rest should, or atleast some lol.. nothing to loose

thanks for the help

---

### Post by Joe67 on 2015-12-04
went back to ip and port, seems to be working... who knows why *80 wouldnt...

---

### Post by darkod on 2015-12-05
Well, if it works... :)

Just to clarify when you say ip and port, you refer to the <VirtualHost> declaration in the .conf files?

---

### Post by Joe67 on 2015-12-05
i changed the ip in ports conf and the virtual host to match, same as 80..., just replaced * with the ip

---

