---
title: "Setting up Piwik on a 14.04 remotehost"
date: 2015-10-17
forum: Server Platforms
---

### Post by Drone4four on 2015-10-17
I've got a basic DigitalOcean VPS with Ubuntu 14.04.  I've got LAMP installed, along with a vhost, DNS set up.  I've also got some of my Lorem Ipsum content up and accessible.  

Now I'm trying to establish an analytics engine to monitor web traffic.  

I've been following two guides.  On DigitalOcean I found guide titled, “[How To Install Piwik on an Ubuntu 12.04 Cloud Server]("https://www.digitalocean.com/community/tutorials/how-to-install-piwik-on-an-ubuntu-12-04-cloud-server")”. It was written for 12.04, so it is slightly out dated.  One commenter suggested that the only step that needs to be changed is is swapping out /var/www/ for /var/www/html/ .  This suggestion matches a different guide I found on Google which is specific to 14.04 titled, “[How To Install PIWIK On Ubuntu 14.04]("https://www.howtoforge.com/how-to-install-piwik-on-ubuntu-14.04")”

Notice the second guide recommends inputting these instructions to create a new database:

```

CREATE DATABASE piwikdb;
CREATE USER piwikadmin@localhost IDENTIFIED BY 'piwikpassword';
GRANT ALL PRIVILEGES ON piwikdb.* TO piwikadmin@localhost;
FLUSH PRIVILEGES;
exit

```

The first guide doesn't include this.  I obviously exchanged all the variables for my own.  Like instead of piwikadmin@localhost I used my web content user and domainmame.

Both guides recommend using a www-data user and www-data group.  I tried that first.  But when I got a 404 when navigating to  [www.DN.info/piwik](www.DN.info/piwik), I thought I would try a different permission scheme to match the one I have implemented on my server.  On my server I have 2 users (one for each vhost) along with 2 separate groups for content.  So in setting up piwik I assigned the piwik folder in /var/www/html to one of the users and corresponding content groups.  I thought I would try this setting but it turns out that this didn't help me overcome the 404 message.  

Thoughts?

---

### Post by volkswagner on 2015-10-19
When creating the database user, you should use localhost as in the tutorial.  Using your domain name will only
work if your server resolves itself as your domain name. Still, localhost is best practice.

To help with permissions, please post your apache config file and out put of:
```
ls -l /var/www/html
```

Please also check apache error.log for more detailed info.

When navigating to [www.DN.info](www.DN.info) what happens? Are you certain that [www.DN.info](www.DN.info) goes to /var/www/html?

---

### Post by Drone4four on 2015-10-20
```

$ ls -l /var/www/html
total 15848
drwxr-xr-x  5 $user1  $user1-cont     4096 Jul 30 21:47 DN1.info
-rw-r--r--  1 root  root              336 Aug  5 21:13 How to install Piwik.html
-rw-r--r--  1 root  root         16210130 Aug  5 15:13 latest.zip
drwxr-xr-x 12 $user1 $user1-cont     4096 Aug  5 21:13 piwik
drwxr-xr-x  4 root  root             4096 Sep  1 17:31 DN2.coffee
$

```

Notice the owner and group for DN2.coffee are both root.  I will eventually change that to a regular user who will be adding content within that directory.  

Here are the contents of my  /var/www/html/DN1.info/logs/error.log : [http://pastebin.com/7pNP0hTM](http://pastebin.com/7pNP0hTM)

Here are the contents of my apache2.conf:

```

# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See http://httpd.apache.org/docs/2.4/ for detailed information about
# the directives and /usr/share/doc/apache2/README.Debian about Debian specific
# hints.
#
#
# Summary of how the Apache 2 configuration works in Debian:
# The Apache 2 web server configuration in Debian is quite different to
# upstream's suggested way to configure the web server. This is because Debian's
# default Apache2 installation attempts to make adding and removing modules,
# virtual hosts, and extra configuration directives as flexible as possible, in
# order to make automating the changes and administering the server as easy as
# possible.

# It is split into several files forming the configuration hierarchy outlined
# below, all located in the /etc/apache2/ directory:
#
#	/etc/apache2/
#	|-- apache2.conf
#	|	`--  ports.conf
#	|-- mods-enabled
#	|	|-- *.load
#	|	`-- *.conf
#	|-- conf-enabled
#	|	`-- *.conf
# 	`-- sites-enabled
#	 	`-- *.conf
#
#
# * apache2.conf is the main configuration file (this file). It puts the pieces
#   together by including all remaining configuration files when starting up the
#   web server.
#
# * ports.conf is always included from the main configuration file. It is
#   supposed to determine listening ports for incoming connections which can be
#   customized anytime.
#
# * Configuration files in the mods-enabled/, conf-enabled/ and sites-enabled/
#   directories contain particular configuration snippets which manage modules,
#   global configuration fragments, or virtual host configurations,
#   respectively.
#
#   They are activated by symlinking available configuration files from their
#   respective *-available/ counterparts. These should be managed by using our
#   helpers a2enmod/a2dismod, a2ensite/a2dissite and a2enconf/a2disconf. See
#   their respective man pages for detailed information.
#
# * The binary is called apache2. Due to the use of environment variables, in
#   the default configuration, apache2 needs to be started/stopped with
#   /etc/init.d/apache2 or apache2ctl. Calling /usr/bin/apache2 directly will not
#   work with the default configuration.


# Global configuration
#

#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the Mutex documentation (available
# at <URL:http://httpd.apache.org/docs/2.4/mod/core.html#mutex>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
#ServerRoot "/etc/apache2"

#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
Mutex file:${APACHE_LOCK_DIR} default

#
# PidFile: The file in which the server should record its process
# identification number when it starts.
# This needs to be set in /etc/apache2/envvars
#
PidFile ${APACHE_PID_FILE}

#
# Timeout: The number of seconds before receives and sends time out.
#
Timeout 300

#
# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.
#
KeepAlive On

#
# MaxKeepAliveRequests: The maximum number of requests to allow
# during a persistent connection. Set to 0 to allow an unlimited amount.
# We recommend you leave this number high, for maximum performance.
#
MaxKeepAliveRequests 100

#
# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.
#
KeepAliveTimeout 5


# These need to be set in /etc/apache2/envvars
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

#
# HostnameLookups: Log the names of clients or just their IP addresses
# e.g., www.apache.org (on) or 204.62.129.132 (off).
# The default is off because it'd be overall better for the net if people
# had to knowingly turn this feature on, since enabling it means that
# each client request will result in AT LEAST one lookup request to the
# nameserver.
#
HostnameLookups Off

# ErrorLog: The location of the error log file.
# If you do not specify an ErrorLog directive within a <VirtualHost>
# container, error messages relating to that virtual host will be
# logged here.  If you *do* define an error logfile for a <VirtualHost>
# container, that host's errors will be logged there and not here.
#
ErrorLog ${APACHE_LOG_DIR}/error.log

#
# LogLevel: Control the severity of messages logged to the error_log.
# Available values: trace8, ..., trace1, debug, info, notice, warn,
# error, crit, alert, emerg.
# It is also possible to configure the log level for particular modules, e.g.
# "LogLevel info ssl:warn"
#
LogLevel warn

# Include module configuration:
IncludeOptional mods-enabled/*.load
IncludeOptional mods-enabled/*.conf

# Include list of ports to listen on
Include ports.conf


# Sets the default security model of the Apache2 HTTPD server. It does
# not allow access to the root filesystem outside of /usr/share and /var/www.
# The former is used by web applications packaged in Debian,
# the latter may be used for local directories served by the web server. If
# your system is serving content from a sub-directory in /srv you must allow
# access here, or in any related virtual host.
<Directory />
	Options FollowSymLinks
	AllowOverride None
	Require all denied
</Directory>

<Directory /usr/share>
	AllowOverride None
	Require all granted
</Directory>

<Directory /var/www/>
	Options Indexes FollowSymLinks
	AllowOverride None
	Require all granted
</Directory>

#<Directory /srv/>
#	Options Indexes FollowSymLinks
#	AllowOverride None
#	Require all granted
#</Directory>




# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#
AccessFileName .htaccess

#
# The following lines prevent .htaccess and .htpasswd files from being
# viewed by Web clients.
#
<FilesMatch "^\.ht">
	Require all denied
</FilesMatch>


#
# The following directives define some format nicknames for use with
# a CustomLog directive.
#
# These deviate from the Common Log Format definitions in that they use %O
# (the actual bytes sent including headers) instead of %b (the size of the
# requested file), because the latter makes it impossible to detect partial
# requests.
#
# Note that the use of %{X-Forwarded-For}i instead of %h is not recommended.
# Use mod_remoteip instead.
#
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
IncludeOptional conf-enabled/*.conf

# Include the virtual host configurations:
IncludeOptional sites-enabled/*.conf

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet

# courtesy of https://www.linode.com/docs/websites/lamp/lamp-server-on-ubuntu-14-04 on 6 March 2015 :

<IfModule mpm_prefork_module>
StartServers 2
MinSpareServers 6
MaxSpareServers 12
MaxClients 30
MaxRequestsPerChild 3000
</IfModule>

# courtesy of http://nixtechnica.blogspot.ca/2007/05/how-and-why-to-disable-apache-server.html on 6 March 2015
ServerSignature Off
ServerTokens Prod

```

Here are the contents of 000-default.conf:
```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	DocumentRoot /var/www
	<Directory>
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
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

```

Here are the contents of DN1.info.conf:
```

# domain: DN1.info
# public: /home/$user/public/DN1.info

#<VirtualHost *:80>
  # Admin email, Server Name (domain name), and any aliases
#  ServerAdmin webmaster@DN1.info
#  ServerName  www.DN1.info
#  ServerAlias DN1.info

  # Index file and Document Root (where the public files are located)
#  DirectoryIndex index.html
#  DocumentRoot /home/$user/public/DN1.info/public

  # Log file locations
#  LogLevel warn
#  ErrorLog  /home/$user/public/DN1.info/log/error.log
#  CustomLog /home/$user/public/DN1.info/log/access.log combined
# </VirtualHost>

<VirtualHost *:80>
        
        ServerAdmin webmaster@DN1.info
        ServerName  www.DN1.info
        ServerAlias DN1.info
        DocumentRoot /var/www/html/DN1.info/public_html/
        ErrorLog /var/www/html/DN1.info/logs/error.log 
        CustomLog /var/www/html/DN1.info/logs/access.log combined

     <Directory /var/www/html/DN1.info/public_html/>
	Order allow,deny
	Allow from all
     </Directory>

</VirtualHost>


```

And the contents of DN2.conf:
```

# domain: DN2.coffee
# public: /home/$user/public/DN2.coffee

#<VirtualHost *:80>
  # Admin email, Server Name (domain name), and any aliases
#  ServerAdmin webmaster@DN2.coffee
#  ServerName  www.DN2.coffee
#  ServerAlias DN2.coffee

  # Index file and Document Root (where the public files are located)
#  DirectoryIndex index.html
#  DocumentRoot /home/$user/public/DN2.coffee/public

  # Log file locations
#  LogLevel warn
#  ErrorLog  /home/$user/public/DN2.coffee/log/error.log
#  CustomLog /home/$user/public/DN2.coffee/log/access.log combined
# </VirtualHost>

<VirtualHost *:80>
        
        ServerAdmin webmaster@DN2.coffee
	ServerName  www.DN2.coffee
        ServerAlias DN2.coffee
        DocumentRoot /var/www/html/DN2.coffee/public_html/
        ErrorLog /var/www/html/DN2.coffee/logs/error.log 
        CustomLog /var/www/html/DN2.coffee/logs/access.log combined

     <Directory /var/www/html/DN2.coffee/public_html/>
	Order allow,deny
	Allow from all
	Options -Indexes
	ErrorDocument 404 /notfound.html
     </Directory>

</VirtualHost>


# <Directory /var/www/html/>
# Options Indexes FollowSymLinks
# AllowOverride All
# </Directory>

```

Thanks for your attention, **volkswagner**.

---

### Post by volkswagner on 2015-10-21
It's important to answer questions asked by those trying to help.

If you investigated my question: "Are you certain that [www.DN.info](www.DN.info) goes to /var/www/html?", you may have discovered your problem.

Firstly 404 error should not lead you to checking permissions, as it is "page or file not found error".

You have configured site [www.DN.info](www.DN.info) to have 
```
DocumentRoot /var/www/html/DN1.info/public_html/
```

So when you navigate to [www.DN.info/piwik](www.DN.info/piwik), your server will try to serve content from a directory that does not exist ie: /var/www/html/DN1.info/public_html/piwik.

Since /var/www/html/DN1.info/public_html/ is the root directory of the domain adding "piwik" to the root is the same as adding it to the document root in the config file.
If you want [www.DN.info/piwik](www.DN.info/piwik) to be the way you access the site, you'll need to move the directory. A second option would be to create a subdomain like piwik.dn.info.

Well now I'm confused, as you posted vhost files for two domains, neither of which are [www.dn.info](www.dn.info).

Do you have a config file for [www.dn.info?](www.dn.info?) Is there a third domain config file, or are you expecting your 000-default.conf file to serve [www.dn.info/piwik?](www.dn.info/piwik?) If it's the
latter then you'll need to write the url as [www.dn.info/html/piwik](www.dn.info/html/piwik) (provided your 000-default.conf is working). Lastly you could move piwik up one level to /var/www/piwik.

---

### Post by Drone4four on 2015-10-22
> **volkswagner said:**
> It's important to answer questions asked by those trying to help. 
Thank you for your help, **volkswagner**.  I do sometimes get lost in my own little world.  Forgive my folly.  Thank you for your continued patience.

> If you investigated my question: "Are you certain that [www.DN.info](www.DN.info) goes to /var/www/html?", you may have discovered your problem. 
Yes I did investigate this.  I  copied the listed the contents of  /var/www/html in my previous post.  But I went off on a tangent about my permissions.  The contents of /var/www/html remain:
```
DN1.info          
latest.zip  
DN2.coffee
How to install Piwik.html  piwik
```

> So when you navigate to [www.DN.info/piwik](www.DN.info/piwik), your server will try to serve content from a directory that does not exist ie: /var/www/html/DN1.info/public_html/piwik. I see what you are saying there.  I get that.  What I sort of don't understand is what you say next: 

> Since /var/www/html/DN1.info/public_html/ is the root directory of the domain adding "piwik" to the root is the same as adding it to the document root in the config file. If you want [www.DN.info/piwik](www.DN.info/piwik) to be the way you access the site, you'll need to move the directory. A second option would be to create a subdomain like piwik.dn.info.   

Rather than creating a subdomain, I'll move piwiki or change a line or two in my conf files  - - something which you explained but which I don't understand.  The problem is not your explanation.  I'm just a little daft.  

I'm grappling with the distinction between root and DocumentRoot.  There is a root user or super user who has access to every system file and can do anything a  *nix system.  The root directory is / which is the top level directory on any *nix operating system.  And in the case of an apache webserver, the DocumentRoot is the parent directory of all the content accessible by visitors.  grep tells me this is my document root: 

```
$ grep -i 'Root' /etc/apache2/sites-available/DN2.conf   
#Index file and Document Root (where the public files are located)   
DocumentRoot /var/www/html/DN2.coffee/public_html/
$ 
```

The content (index.html) of public_html/ is my homepage.  You said: &#8220;If you want [www.DN.info/piwik](www.DN.info/piwik) to be the way you access the site, you'll need to move the directory.&#8221;  Move to where? Into public_html (my DocumentRoot)? No, this can't be what you're saying because the guides I'm working with don't say that.  

> Lastly you could move piwik up one level to /var/www/piwik.  

Are you sure that's workable? That what the guide says for 12.04.  In 12.04 they say put piwik into /var/www/ but the newer guide says that for 14.04 piwik should be put into /var/www/html .

>  Do you have a config file for [www.dn.info?](www.dn.info?)  

I have a config file for both domain names.  One is named DN1.info.conf and the other is DN2.conf.  I shared the contents of both those configuration files in my previous post.

> Is there a third domain config file, or are you expecting your 000-default.conf file to serve [www.dn.info/piwik?](www.dn.info/piwik?) If it's the latter then you'll need to write the url as [www.dn.info/html/piwik](www.dn.info/html/piwik) (provided your 000-default.conf is working).  
I believe  000-default.conf is working.  Is there a way to determine this for sure?  If it is being used by properly by apache, where  in 000-default.conf should I make that change, like what line?

Thanks again, **volkswagner**.

---

### Post by volkswagner on 2015-10-23
Let's try to clear up the confusion.

You have three domains in your question: dn1.info, dn.info, and dn2.coffee.  Are these all correct?
In order for me to help, I'll need to see the config file for dn.info so I can tell you where the piwik folder should go, or you'll need to confirm
there is no config file for dn.info and you are expecting the 000-default to handle this non-configured domain.

If your not sure how the 000-default works, I'll try to explain.  Apache2 virtual hosts works like this: Apache will resolve a domain by matching the domain name to the first config file which contains the "ServerName" matching the requested domain. Apache searches /etc/apache2/sites-enabled in alphaNumeric order. This is why we name
default as 000-default so it should always be served first if there's no domain match in other files. So if you have a config file dn.info.conf enabled and it contains,
```
ServerName dn.info
ServerAlias www.dn.info
```
This file will be used to display sites requested as dn.info or [www.dn.info](www.dn.info), which would include dn.info/piwik.

If the config file has:
```
DocumentRoot /var/www/html
```

You would need your piwik file located in /var/www/html/piwik. This means you can have other content with index.html in /var/www/html, so the url dn.info will
display content from /var/www/html.

So what ever is in documentRoot will be displayed when no directory is added to the url ie: dn.info/ or [www.dn.info/](www.dn.info/) When you add  a directory to the url such as dn.info/myFolder, this directory needs to live in the documentRoot's folder to be served.

Please don't confuse /root , filesystem root = "/", root user, or DocumentRoot config for Apache. They are five unique items.

As of now I still am not sure if you actually have the three domains I listed above, or if your original question with [COLOR="#FF0000"]dn1[/COLOR].info/piwik is a typo and should actually be [COLOR="#FF0000"]dn[/COLOR].info/piwik.

---

### Post by Drone4four on 2015-10-23
**volkswagner** : There is no [www.DN.info](www.DN.info).  I meant to say [www.DN1.info](www.DN1.info) and [www.DN2.coffee](www.DN2.coffee).  Again the source of the confusion was my mistake.  Sorry, man.  I will try everything else you suggested later today at my earlierst opportunity.  Thank-you for your continued patience.

---

### Post by Drone4four on 2015-10-23
> **volkswagner said:**
> You have three domains in your question: dn1.info, dn.info, and dn2.coffee.  Are these all correct?

I have two domains: [www.DN1.info](www.DN1.info) and [www.DN2.coffee](www.DN2.coffee) .  These are the only two I have installed.

> If your not sure how the 000-default works, I'll try to explain.  Apache2 virtual hosts works like this: Apache will resolve a domain by matching the domain name to the first config file which contains the "ServerName" matching the requested domain. Apache searches /etc/apache2/sites-enabled in alphaNumeric order. This is why we name
default as 000-default so it should always be served first if there's no domain match in other files. So if you have a config file dn.info.conf enabled and it contains,
```
ServerName dn.info
ServerAlias www.dn.info
```

Your 000-default explanation makes sense. Apache searches for files within /etc/apache2/stes-available/ for files which contact ServerName dn1.info and ServerAlias [www.dn1.info](www.dn1.info) and if it matches the DNS record, serves it out to the web visitors.  If there are no DN.TLD.conf in sites-availalbe, it serves up the default.  I gather that 000-default.conf is the original file which my other two DN files are based on.   So when I set up my webserver in the beginning, I copied over 000-default and populated the copy with my DN information, and renamed that file DN1.info.conf. That's my attempt at paraphrasing your explanation and putting it in the context of what I am trying to do here.  I might be off a little, but I get the general sense as to what's going on with 000-default (at least I hope I do).

> If the config file has:
```
DocumentRoot /var/www/html
```

You would need your piwik file located in /var/www/html/piwik. This means you can have other content with index.html in /var/www/html, so the url dn.info will
display content from /var/www/html.

So you're now suggesting that I add DN1.info/piwik somewhere in my DN1.info.conf?

I have 3 configuration files:
1.  000-default.conf
2.  DN1.info.conf
3.  DN2.conf
The DocumentRoot for 000-default is declared as /var/www
The DocumentRoot for DN1.info.conf is declared as /var/www/html/DN1.info/public_html/
The DocumentRoot for DN2.conf is declared as /var/www/html/DN2.coffee/public_html/
You can see this in the configuration files which I posted earlier in this thread.

The contents of /var/www/html/ (which is specified to be DocumentRoot in the second and third configuration file) include:
```

DN1.info
How to install Piwik.html
latest.zip
piwik
DN2.coffee

```

---

### Post by volkswagner on 2015-10-23
For what ever reason you keep bypassing my emphasis on dn.info vs dn1.info.

You are trying to reach dn.info/piwik.

Can we address this first.

No, I am not telling you to add anything to any config file. I'm asking to identify how you want to access your piwik site.

When you write dn.info/piwik, is this a typo and should read dn1.info? We really need to get past this before proceeding.

You are trying to access your piwik site from a domain name not configured, is this on purpose or is it a typo?

> **Drone4four said:**
> I have two domains: [www.DN1.info](www.DN1.info) and [www.DN2.coffee](www.DN2.coffee) .  These are the only two I have installed.

then why are you tying to access your piwik site from [www.DN.info?](www.DN.info?)

---

### Post by Drone4four on 2015-10-24
I'm not trying to access piwik from [www.DN.info](www.DN.info). that was a typo in my original post. All along I have been trying to access piwik from [www.DN1.info/piwik](www.DN1.info/piwik)

---

### Post by volkswagner on 2015-10-24
Thanks for clearing that up.  So as previously mentioned one way to fix this is to move the directory "piwik" to the root of your domain.

Since DocumentRoot for dn1.info = DocumentRoot /var/www/html/DN1.info/public_html/

You can move the directory with the following command.
```
sudo mv /var/www/html/piwik /var/www/html/DN1.info/public_html/
```

The above is how I suggest you accomplish your goal. As always with Linux, there's more than one way to accomplish this.  You could also add a [directory alias]("https://httpd.apache.org/docs/2.2/mod/mod_alias.html") to your site config file then restart Apache.

---

### Post by Drone4four on 2015-10-24
Eureka! That worked! I moved piwik and its contents into my public_html folder, played around with the permissions and Voila! The piwiki installer is now available when I navigate to  [www.DN1.info/piwik](www.DN1.info/piwik) in my web-browser.  The installer looks pretty simple.  I've already encountered a new error involving a 500: "GET request to piwik.php failed" message.  I did some Googling around and found some relevant forum posts.  I also noticed that the official website is down, so I can't access the faqs for the moment.  If I can't find a solution after digging around then I'll be sure to report back here with my questions.

Thank-you **volkswagner** for your help and for your patience.

---

### Post by volkswagner on 2015-10-25
Your welcome.  

If you have issues connecting to the database, you may want to change your user's access from "yourdomain.info" to localhost as
localhost is typical for this setting.

---

