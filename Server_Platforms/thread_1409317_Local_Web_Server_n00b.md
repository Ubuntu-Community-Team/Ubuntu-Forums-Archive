---
title: "Local Web Server n00b"
date: 2010-02-17
forum: Server Platforms
---

### Post by MachineWarehouse on 2010-02-17
Hi everyone. I am a n00b to ubuntu and linx.

I want to use this as a local development web server.  I have already install Apache2, PHP5, MySQL and they are running fine.

I want to use this desktop as a testing server for websites I build.  I want to be able to type into my web browser on my Win7 computer "http://myserverip/site1" and this will be a virtual site located at /var/www/site1 and be a complete seperate site with it's own .htaccess.

I then want to be able to have "http://myserverip/site2" and this will be a virtual site located at /var/www/site2.

I have install proftpd and have it setup so I can connect and upload to /var/www/.  I will be using dreamweaver to develop these sites and then upload them to the server into their respective directories.  I then want to test them in a web browser on my Win7 computer to see if the look and function correctly.

I have enabled mod_rewrite using the a2enmod rewrite.load as one of my sites is using the rewrite command in it's own .htaccess.

Any help would be greatly appreciated.

---

### Post by kamaji792 on 2010-02-17
Do you have a problem or are you just looking for advice?

I don't tend to use sub-domains when testing.  I just have separate directories in the /var/www directory.  Then I set up SAMBA to allow me to edit the site files from my WinXP box.

atb

---

### Post by MachineWarehouse on 2010-02-17
I am new to this and would like to setup an apache server that I can use to test my websites.  Right now I can ftp in and upload my files.  I don't mind doing SAMBA. I just don't know how to set that up.  But my biggest concern is getting it to be able to view the different sites from my Win7 box as they would run on an actual host.  One of my sites is using mod_rewrite and I don't want this to affect my other sites.  Any help on how to setup the server for my application?

---

### Post by tlsarles on 2010-02-18
I think what you are looking for is virtual hosts. In order to do this, your also going to need a DNS Server, as your going to have to create records for site1.com and site2.com, which both point to the IP of your apache server ( Could be the same box ). Then you need to setup virtual hosts in apache.

I don't recall the syntax... but its something like... you go to
/etc/apache2/sites-available ?

And for each VHost, there will be a config file. Look at the existing one for some idea of how it works.... ok, now copy that file, and tweak the settings...

Ok, after you save the new VHost config, you need to enable it... I think the command is a2ensite .... something like that...

try it... google it...

---

### Post by lykwydchykyn on 2010-02-18
Unless I vastly misunderstand you original post, what you want does not require either mod rewrite or virtual hosts.

Just put one site in /var/www/site1 and the other in /var/www/site2.

Does that not do what you wish to accomplish?

---

### Post by KnottyMars on 2010-02-18
No problem doing that at all. On your Win7 machine, you would need to edit your host file (not sure where it is in 7, but in XP, its in C:\WINDOWS\system32\drivers\etc\hosts) You can edit this file and enter the fake domain you want to use, then the IP addy of the LAMP server you are running. 

What you need to setup is virtual hosting with apache so that you can specify different folders for different sites. I patched together a bunch of instructions on how to get this setup and here is a snippet of it that should allow you to create virtual hosting on your server. Hope this helps

_____________________________________________________________________________________________________

Create the webspace folders, first browse to your webspace folder
	cd /var/www

Then make a vhosts folder to house your websites
	sudo mkdir vhosts
	cd /var/www/vhosts
Now make the webspace folders for the domains you want with some default sub folders
	sudo mkdir -p [name of domain]/{public,private,log,cgi-bin,backup}

Rinse and repeat for as many domains as needed.  replace [NOD] with the domain name
You can create a simple html index file to verify that the domains are working when they 
are enabled and activated. (OPTIONAL)

Now we need to setup apache2 so that we can serve multiple domains instead of just one
	cd /etc/apache2
	sudo nano sites-available/default

Delete the 'NameVirtualHost *' line and change the next lines text to read:
	<VirtualHost *:80>
		ServerAdmin webmaster@locahost
		DocumentRoot /var/www
Ctrl+O, then press enter to save. Then Ctrl+X to exit the editor

Now we need to adjust the main apache2 conf file
	sudo nano apache2.conf 

At the very bottom of the file, add the following:
	NameVirtualHost *:80

	<IfModule mod_ssl.c>
		NameVirtualHost *:443
	</IfModule>
Ctrl+O, then press enter to save. Then Ctrl+X to exit the editor

Now reload the apache2 conf file
	sudo /etc/init.d/apache2 reload

Add a new user and set ownership and write privileges to the folder path, each user will be specific to each domain path. 
	sudo useradd [your username]
	sudo passwd [your username] (then assign the password)
	sudo chown -R [your username] /var/www/vhosts/[name of domain]
	sudo chmod -R 775 /var/www/vhosts/[name of domain]

You should get no errors or warnings, if you did, make sure that the adjustments to apache2.conf
and the default file in sites-available were saved. 
Now we need to create a vhost file for the domains that were added 
	sudo nano /etc/apache2/sites-available/[name of domain]

This will be a new file so it will be blank, you will need to type all of the following in: 

#Place any notes or comments here
#It will make any custom setup easier to understand later
#
#domain: [name of domain]
#public: /var/www/vhosts/[name of domain]/public

<VirtualHost *:80>
#Admin email, Server Name, (domain name) and any aliases
Server Admin webmaster@[name of domain]
ServerName [name of domain]
ServerAlias [www.[name](www.[name) of domain]

#Index file and document root (where the public files are)
DirectoryIndex index.php index.html
DocumentRoot /var/www/vhosts/[name of domain]/public

#Custom log file locations
LogLevel warn
ErrorLog /var/www/vhosts/[name of domain]/log/error.log
CustomLog /var/www/vhosts/[name of domain]/log/access.log combined

</VirtualHost>

The site needs to be enabled. If you added multiple sites, each one will need to be activated
	sudo a2ensite [name of domain]

Disable the default site
	sudo a2dissite default

Reload the apache2 conf file
	sudo /etc/init.d/apache2 reload

---

### Post by MachineWarehouse on 2010-02-24
Thank you. I have successfully setup a virtual server.  When I try it from the ubuntu box it works fine.

However when I try to access the site remotely via "http://myip/site1/"

it is looking for all the files via the vase directory of "/var/www/" I want it to look in the directory of "/var/www/tmw/" for the files.

I am referring to files referenced from my index.php, etc.

I have a .htaccess file that is written as follows:
<IfModule mod_rewrite.c>
  RewriteEngine On
  RewriteBase /
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteRule ^(.*) index.php/$1 [L]
</IfModule>

This file and my site works fine on GoDaddy with linux hosting. So I know my problem isn't my site. I have tried to change the "Rewritebase /" rule to "Rewritebase /site1/" and this doesn't work.  The .htaccess file is located in: "/var/www/site1/".

Any help would be appreciated.

---

### Post by lykwydchykyn on 2010-02-24
mod_rewrite is totally unnecessary for this.  You just need to add an alias.

Just create a file in /etc/apache/conf.d/  Call it whatever you want, maybe "site1.conf".

Put this in the file:
```

Alias /site1 /var/www/tmw

```

Restart apache and you're done.

EDIT: I should add, if /var/www/site1 exists, you'll need to remove it first (I think).

---

### Post by MachineWarehouse on 2010-02-24
If I remove this file on my GoDaddy account, my site no longer works.

The reason I am using a .htaccess for site1 is that all my sub directories don't exist. It rewrites them to the index and then I use php to explode the $_SERVER['REQUEST_URI'].

Like I said this works fine on GoDaddy.

When I pull up my site using the virtual host name the site pulls up and is able to read the images from /images directory and etc. However I check the error log and I get File does not exist: /usr/shar/javascript/jquery.js, referer: [http://virtualhost/](http://virtualhost/)

But my links work except for the first directory.  I have one link that is /woodworking/ and this end's up pulling up my sites tmw.css with is the last file successfully loaded from index.php.

but when it goes 2 directories deep: /woodworking/cnc-router/ this works fine and pulls up everything.

Any ideas?

---

### Post by MachineWarehouse on 2010-02-24
When I try [http://myip/site1/](http://myip/site1/) in loads the index.php, however all the links inside of there to css, images, etc. don't work because it keeps looking in the /var/www/ directory and not the /var/www/site1/

---

### Post by MachineWarehouse on 2010-02-24
This is my site1 sites-enable file:
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName virtmw

    DocumentRoot /var/www/tmw
    #<Directory />
    #    Options FollowSymLinks
    #    AllowOverride All
    #</Directory>
    <Directory /var/www/tmw>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>

    ErrorLog /var/log/apache2/tmw-error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/tmw-access.log combined

</VirtualHost>

default sites-enable file:
<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /var/www
    <Directory />
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
        Allow from all
    </Directory>

</VirtualHost>

my apache2.conf file:
#
# Based upon the NCSA server configuration files originally by Rob McCool.
#
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See [http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/) for detailed information about
# the directives.
#
# Do NOT simply read the instructions in here without understanding
# what they do.  They're here only as hints or reminders.  If you are unsure
# consult the online docs. You have been warned.  
#
# The configuration directives are grouped into three basic sections:
#  1. Directives that control the operation of the Apache server process as a
#     whole (the 'global environment').
#  2. Directives that define the parameters of the 'main' or 'default' server,
#     which responds to requests that aren't handled by a virtual host.
#     These directives also provide default values for the settings
#     of all virtual hosts.
#  3. Settings for virtual hosts, which allow Web requests to be sent to
#     different IP addresses or hostnames and have them handled by the
#     same Apache server process.
#
# Configuration and logfile names: If the filenames you specify for many
# of the server's control files begin with "/" (or "drive:/" for Win32), the
# server will use that explicit path.  If the filenames do *not* begin
# with "/", the value of ServerRoot is prepended -- so "/var/log/apache2/foo.log"
# with ServerRoot set to "" will be interpreted by the
# server as "//var/log/apache2/foo.log".
#

### Section 1: Global Environment
#
# The directives in this section affect the overall operation of Apache,
# such as the number of concurrent requests it can handle or where it
# can find its configuration files.
#

#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the LockFile documentation (available
# at <URL:http://httpd.apache.org/docs-2.1/mod/mpm_common.html#lockfile>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
ServerRoot "/etc/apache2"

#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
#<IfModule !mpm_winnt.c>
#<IfModule !mpm_netware.c>
LockFile /var/lock/apache2/accept.lock
#</IfModule>
#</IfModule>

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
KeepAliveTimeout 15

##
## Server-Pool Size Regulation (MPM specific)
## 

# prefork MPM
# StartServers: number of server processes to start
# MinSpareServers: minimum number of server processes which are kept spare
# MaxSpareServers: maximum number of server processes which are kept spare
# MaxClients: maximum number of server processes allowed to start
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# worker MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_worker_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# event MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_event_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

# These need to be set in /etc/apache2/envvars
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

#
# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#

AccessFileName .htaccess

#
# The following lines prevent .htaccess and .htpasswd files from being 
# viewed by Web clients. 
#
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


#
# HostnameLookups: Log the names of clients or just their IP addresses
# e.g., [www.apache.org](www.apache.org) (on) or 204.62.129.132 (off).
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
ErrorLog /var/log/apache2/error.log

#
# LogLevel: Control the number of messages logged to the error_log.
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
#
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
# If you are behind a reverse proxy, you might want to change %h into %{X-Forwarded-For}i
#
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

#
# Define an access log for VirtualHosts that don't define their own logfile
CustomLog /var/log/apache2/other_vhosts_access.log vhost_combined


# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

#Include the phpmyadmin configurations
#Include /etc/phpmyadmin/apache.conf

---

### Post by lykwydchykyn on 2010-02-24
I've reread all your posts, and I'm sorry to say I can't fathom why you are taking such a complicated approach.  I assume you have reasons that are perfectly clear to you, but from what you've described I just don't see why you'd mess with all that rewrite business.

Anyway, my only guess is that something in the index.php isn't creating paths that work on your local network.  If the files aren't accessible, there should be an error in /var/log/apache2/error_log about it, and that will give you an indication of where the browser is being told to find the files.

Are you using something like codeigniter, or is the index.php in question something of your own design?

---

### Post by MachineWarehouse on 2010-02-24
the index.php is my own design. I am doing it this complicated so that my php files don't use a ?id=xxx type of variable. Instead I am using a /id/category/ and the php file if using these as the get type of variables. This is so I can have virtual .html files for google indexing with my mysql database.

the error in the error log I am getting is:
[error] [client 127.0.0.1] File does not exist: /usr/share/javascript/jquery.js, referer: [http://virtmw/](http://virtmw/)

Like I said, my site is working fine on GoDaddy:
[http://www.themachinewarehouse.com](http://www.themachinewarehouse.com)

I want a local copy of my site as it is so that I can make changes and test how they work. But I also want to work on other websites locally that may work differently then my own site.

I am doing the same function as a rewrite rule that takes a /id/category/ would -> ?id=xxx&cat=xxx

Originally I had trouble getting this to work and ended up just sending everything to index.php and user the SERVER_URI command and this solved all my problems.

But I want to set my site up on a local server for testing.  The only thing is that I also want to setup other sites on here for testing so I need to use virtualhosts.  This is working fine like I said.  However according to the error log, apache is looking in the /usr/share/ folder for certain files and I don't know how to fix this.

---

### Post by lykwydchykyn on 2010-02-25
So the godaddy site is hosted on a separate server.  jquery is a pretty common javascript library; chances are they have it installed under /usr/share on that server, and it's aliased somehow in the configuration or in the .htaccess files.  

Try installing libjs-jquery on your server and see if that helps.

---

### Post by MachineWarehouse on 2010-02-25
I can understand what you are saying. But a problem I run into is the server can't find my own custom .js file.  On my website, I am putting all my .js files in a javascript directory that is /var/www/site1/javascript/ and for some reason after the web page is loaded locally, it is successfully finding my: /reset.css and /site1.css file in my head of my html.  How ever under the <script type="text/javascript" src="/javascript/jquery.js"></script> it is looking in the /usr/share/ directory.  I must have something wrong in my setup that it is looking for these scripts in a different directory.

I also checked my Synaptic Package Manager and libjs-jquery is already installed along with javascript-common.

I think the only final problem I am having is when apache is trying to serve a javascript file that is using the <script> and src in the html. For some reason it is looking in the /usr/share/ directory and not the directory of my site.

Where can I change this?

---

### Post by MachineWarehouse on 2010-02-25
Update.  I want to thank everyone for their help.  But I finally found my last problem.  Apparently Apache has a small problem in one of it's configurations files.  The javascript-common.conf located in /etc/javascript-common that is called fron the /etc/apache2/conf.d directory.  In this file there is:

Alias /javascript /user/share/javascript/

<Directory "/user/share/javascript/">
    Options FollowSymLinks MultiViews
</Directory>

I ended up creating a Alias /javascript /var/www/site1/javascript and reloaded apache.  Now everything is working fine.

Is this the correct way of fixing this for the future?

Are there any other ways of fixing this?

Thank you.

---

