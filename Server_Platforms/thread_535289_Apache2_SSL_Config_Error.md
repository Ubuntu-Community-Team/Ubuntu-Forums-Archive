---
title: "Apache2 SSL Config Error"
date: 2007-08-26
forum: Server Platforms
---

### Post by mdsypr on 2007-08-26
Need help, last week I installed Apache2 and changed to port 8080 and got it working.  

I want to use WebDav but not without SSL so I just tried to install SSL and went through all the steps, setup a cert, answered questions, issues paraphrase, edited ssl.conf but I am stuck.

1) I have default.conf and ssl.conf in my sites-available ... I assume that is normal and it's ok if SSL lines are added to ssl.conf and NOT default.conf?

2) In both conf files above I added :8080 and :443 to their respective file at the end of the Virtual Host Name ... that was correct?

3) After I went through all the steps I restated apache2 and received the following error message:

[COLOR="Red"][B]Syntax error on line 9 of /etc/apache2/sites-enabled/ssl:
SSLCertificateFile: file '/etc/ssl/certs/server.crt' does not exist or is empty         [fail][/B][/COLOR]

Any idea why?

I think I don't have my server.crt file created but I went through the steps.  

Here is the how-to I followed; [https://help.ubuntu.com/6.10/ubuntu/serverguide/C/httpd.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/httpd.html)

I LOVE Ubuntu, have 3 machines sharing my music and video, enabled CUPS for a print server, can remote login (super cool) I just also need to figure out how to watch a DVD.

Please help ... I have spent over 3 days reading the boards and searching google but I don't know what I did wrong.

Here is my ssl.conf file:

NameVirtualHost *:443
<VirtualHost *:443>
	ServerAdmin [email]mdsypp@aol.com[/email]
	
	DocumentRoot /var/www/
	SSLEngine On
	SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
	
	SSLCertificateFile /etc/ssl/certs/server.crt
	SSLCertificateKeyFile /etc/ssl/private/server.key

	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
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

Thanks,
Mike

---

### Post by mdsypr on 2007-08-26
This part I solved ... for a newbie someone should make it EXPLICIT that you need to either send in to get you server.crt or sign your own.

Once I signed my own I copied to the right directory and I can now access my site with https ... I assume that means the connection is secured?

If it is I just need to figure out the following and I am good to go:

1) Install Webdav and make it work with a sign on.  Do I need Mysql installed for Webdav to work?

2) Figure out how to change the Document Root to point to my files that are on a windows formated hard drive.  I did change it in apache2.conf but it said I didn't have permissions.  Can't figure that one out.

Any help would be appreciated.

Thanks,
Mike

---

