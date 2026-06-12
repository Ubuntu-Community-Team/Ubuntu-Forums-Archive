---
title: "Apache2 says no sockets available"
date: 2007-10-30
forum: Server Platforms
---

### Post by segner on 2007-10-30
I'm trying to get Apache2 running. When I start it I get this error:

no listening sockets available, shutting down
Unable to open logs

I've done a lot of searching and can't find much. Most people seem to get this message in conjunction with error 98 (Address already in use....)  But what is especially bothersome to me is that it did work briefly and stopped without me changing the config files. I figure some other process must be the culprit, but I don't know how to find out what.

Any ideas? 

Thanks

---

### Post by HermanAB on 2007-10-30
This usually happens when Apache is already running and possibly crashed.  The result being that there is a dud process holding onto port 80.

Investigate with 'ps -e' and kill all running instances of httpd, then try to run it again:
$ sudo ps -e
$ sudo killall httpd

'Hope that helps!

Herman

---

### Post by segner on 2007-10-30
Thanks for the help. Unfortunately there weren't any httpd processes to be killed. Furthermore, I get the error no matter what port I tell Apache to listen to.

---

### Post by MJN on 2007-10-30
Apache now runs as 'apache2' so that's what you need to be checking for.

You are attempting to start it as root?

Check the output of **sudo lsof -i :<port>** where <port> is the port you're using (presumably 80) - this will show if anything else is already listening on it.

I take it from the wording in your post that it's never worked?

Mathew

---

### Post by segner on 2007-10-30
Thanks Matthew,

Yes, I am attempting to start it as root. Here is the command and result:

 $ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                                                                                          no listening sockets available, shutting down
Unable to open logs

I checked the output of** sudo lsof -i:80**. It doesn't print anything.

No, Apache2 did start several times and served the page I was tinkering with for a short time. Since being restarted it has always failed.

John

---

### Post by MJN on 2007-10-30
Post your Apache config (apache2.conf) and all files in /etc/apache2/sites-enabled/ and we can take a look.

If you could elaborate on this 'tinkering' it may also help! ;)

Mathew

---

### Post by netlogic on 2007-10-30
> **segner said:**
> Thanks Matthew,

Yes, I am attempting to start it as root. Here is the command and result:

 $ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                                                                                          no listening sockets available, shutting down
Unable to open logs

I checked the output of** sudo lsof -i:80**. It doesn't print anything.

No, Apache2 did start several times and served the page I was tinkering with for a short time. Since being restarted it has always failed.

John

hmm.... usually that errors means something is sharing the port 80.
This is probably irrelevant, but have you installed apache and apache2 together? however, lsof -i should have said something... yea, configs would be nice to look at.

---

### Post by segner on 2007-10-30
So what I'm trying to do is make a webpage with some TV shows on it available to my local network so that the Wii can play them. I had it working briefly. While I was messing with the filetypes that I wanted the videos in and showing it off to my buddy it stopped working.

When it was working the ServerName may have been SegnerOne, which is the name of my computer or it could have been my IP address, I can't remember. Both names produce the same error now, though. The config files are pretty much the defaults.

Thanks,

John

------------------------------------
This is the config file:
------------------------------------
ServerName SegnerOne:80

ServerRoot "/etc/apache2"

#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
#<IfModule !mpm_winnt.c>
#<IfModule !mpm_netware.c>
LockFile /var/lock/apache2/accept.lock
#</IfModule>
#</IfModule>

PidFile /var/run/apache2.pid

Timeout 300

KeepAlive On

MaxKeepAliveRequests 100
KeepAliveTimeout 15


# prefork MPM
serves
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# worker MPM
<IfModule mpm_worker_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

User www-data
Group www-data

AccessFileName .htaccess

<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

#
# DefaultType is the default MIME type the server will use for a document
# if it cannot otherwise determine one, such as from filename extensions.
# If your server contains mostly text or HTML documents, "text/plain" is
# a good value.  If most of your content is binary, such as applications
# or images, you may want to use "application/octet-stream" instead to
# keep browsers from trying to display binary files as though they are
# text.
#
DefaultType text/plain

HostnameLookups Off

ErrorLog /var/log/apache2/error.log

LogLevel warn

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf

# Include ports listing
Include /etc/apache2/ports.conf

#
# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
#
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

ServerTokens Full

ServerSignature On


# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/


---------------------------------
Here is the file in 'sites-enabled'
---------------------------------
NameVirtualHost SegnerOne
<VirtualHost SegnerOne>
	ServerAdmin webmaster@localhost
	ServerName SegnerOne
	DocumentRoot /var/www/
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

---

### Post by segner on 2007-10-30
I figured it out. I had accidentally removed the Listen directive. oops.

---

