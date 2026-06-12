---
title: "Strange behavior accessing website from WAN"
date: 2009-03-25
forum: Server Platforms
---

### Post by cje on 2009-03-25
Earlier I've password protected a web folder using .htpasswd. 

After I experienced problems with mysql sites using .htpasswd I removed both the .htpasswd and .htaccess files and removed the "AllowOverrideAll <directory>" in apache2.conf. And, restarted apache2.

But, when I try to access the site from WAN I still have problems with slow site rendering. The strange thing is that the web browser is looking for my LAN IP address!? ....how is that possible?
I'm running WP in this particular folder

Are there any wp settings which could be changes (by the way - I'm not able to access the admin panel due to the slow rendering)?

Thanks for any suggestions.

---

### Post by BkkBonanza on 2009-03-26
If your browser is trying to reach the LAN address then chances are you put the name in /etc/hosts (on the browser's machine) and it is finding it there. Maybe you forgot you did that sometime ago or someone else did. Check that file and if the name is there then remove it or set it to the correct address. This file has priority over the DNS lookup.

---

### Post by mrsteveman1 on 2009-03-26
Are you using a domain name?

There is in fact a wordpress setting that tells wordpress what the domain or IP is for the server it is running on, if you get it wrong or if it isn't globally available it'll direct you to pages incorrectly.

---

### Post by cje on 2009-03-26
Thanks for your suggestions.

There are no references in host.conf

Re. domain name
yes, I'm using a domain name. 
And, I tried to rename it .... bad idea!
Got problem with my web server running... had to disable some ports and restart apache2

So, how should I make this change w/o getting this problem?

---

### Post by mrsteveman1 on 2009-03-26
Ok, post your vhost config, or alternatively put your apache2.conf file or httpd.conf file (whichever has the config for this specific site) into a pastebin.

You don't have to post your domain or anything, but make sure it resolves to the right address, then make sure it is correctly listed in the vhost including anything such as [www.domain](www.domain) etc.

Also check your wordpress config, make sure it knows what the domain is and make sure it is set to use the domain name for generating page links.

---

### Post by cje on 2009-03-29
This is the vhost
(I see that I have a local addresse "www.site1.lan" which is not in use any more as I've deactivated bind9, anyway I don't believe it have any effect)

> 
<VirtualHost *>

	ServerAdmin ****@***.com

	ServerName [www.site1.com](www.site1.com)
	ServerAlias site1.com *.site1.com [www.site2.com](www.site2.com) site2.com *.site2.com [www.site1.lan](www.site1.lan)

	DocumentRoot /var/www2/site1/

	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www2/site1/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
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
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

I've also re-checked wordpress. 
Bellow, my apache2.conf file
> 
ServerRoot "/etc/apache2"
LockFile /var/lock/apache2/accept.lock
PidFile ${APACHE_PID_FILE}
Timeout 300
KeepAlive On
MaxKeepAliveRequests 100
KeepAliveTimeout 15
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

<IfModule mpm_worker_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}
AccessFileName .htaccess
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

DefaultType text/plain
HostnameLookups Off
<VirtualHost>
<VirtualHost>
ErrorLog /var/log/apache2/error.log
LogLevel warn
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf
Include /etc/apache2/httpd.conf
Include /etc/apache2/ports.conf
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent
ServerTokens Full
ServerSignature On
Include /etc/apache2/conf.d/
Include /etc/apache2/sites-enabled/

<Directory /var/www/aaa/img>
AllowOverride All
</Directory>

<Directory /var/www/aaa/supl>
AllowOverride All
</Directory>

ServerName bbbb-server


and httpd.conf is empty.

---

### Post by mrsteveman1 on 2009-03-29
I don't see anything really wrong with the configuration of apache, if the machine is fast it shouldn't have a problem executing php scripts. You are using mod_php and not CGI right? 

So to recap, if you are at a remote location, you type your domain name into a browser and the browser looks for a lan IP? That means either the domain server is set to the wrong IP, or the DNS server in use at this remote location (probably set with DHCP) is returning the wrong IP, or, it could be set manually in the /etc/hosts file (Even windows has one, though most people don't know where it is and don't edit it).

Those are the only reasons i can think of that typing a domain into a browser would return the wrong IP.

However, if accessing the site WORKS using the domain, but is slow, it could be your web browser, or the connection, or it could be that php isn't executing correctly on the server.

---

### Post by cje on 2009-03-29
re. mod vs cgi .... :-s ... seems like I've been missing something. 
I'll take a look at the help documents tomorrow 

re. recap;
yeah, when I'm outside my local network the broswer is looking up my server lan ip. But, I doesn't really catch what you mean; 

1) domain server is set to wrong ip; I don't believe this is the source as I'm running other websites which are working ok (remember; the problem started as I enabled .htpasswd for this folder - and didn't disappear when I removed the .htpasswd)

2) the dns server is in use at remote location; do you mean outside my local network? The browser is looking up my server IP at LAN - so it can't have to do with the dns at the remote network.... or do I not understand you? :-S
Anyway, I'll check at another location.

3) set the IP in the host file; you know what I should look for in the host file at the remote location?

So, back to the php execution; are there any think I could look for?

Thanks for your suggestions!

---

