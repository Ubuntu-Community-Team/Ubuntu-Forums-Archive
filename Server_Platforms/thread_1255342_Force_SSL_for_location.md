---
title: "Force SSL for location"
date: 2009-09-01
forum: Server Platforms
---

### Post by Rever75 on 2009-09-01
Not sure if I am posting in the right spot or not and I do understand this is not Ubuntu specific. I have an Ubuntu Web Server running on my intern network. I would like to setup Virtual Host but with the same name and IP. The reason is I want to run SSL for a specific location and the rest of the site be regular http port 80. I have things working kind of but I can surf to the ssl site on regular port 80. Is there anyway to force https for that context path? 

Part of my httpd.conf
```

#
# Listen: Allows you to bind Apache to specific IP addresses and/or
# ports, instead of the default. See also the <VirtualHost>
# directive.
#
# Change this to Listen on specific IP addresses as shown below to 
# prevent Apache from glomming onto all bound IP addresses (0.0.0.0)
#
#Listen 12.34.56.78:80

Listen 80
Listen 443

#
# Dynamic Shared Object (DSO) Support
#
# To be able to use the functionality of a module which was built as a DSO you
# have to place corresponding `LoadModule' lines at this location so the
# directives contained in it are actually available _before_ they are used.
# Statically compiled modules (those listed by `httpd -l') do not need
# to be loaded here.
#
# Example:
# LoadModule foo_module modules/mod_foo.so
#
LoadModule jk2_module modules/mod_jk2.so
LoadModule auth_kerb_module modules/mod_auth_kerb.so
#LoadModule dav_module modules/mod_dav.so
#
# ExtendedStatus controls whether Apache will generate "full" status
# information (ExtendedStatus On) or just basic information (ExtendedStatus
# Off) when the "server-status" handler is called. The default is Off.
#
ExtendedStatus On

### Section 2: 'Main' server configuration
#
# The directives in this section set up the values used by the 'main'
# server, which responds to any requests that aren't handled by a
# <VirtualHost> definition.  These values also provide defaults for
# any <VirtualHost> containers you may define later in the file.
#
# All of these directives may appear inside <VirtualHost> containers,
# in which case these default settings will be overridden for the
# virtual host being defined.
#

<IfModule !mpm_winnt.c>
<IfModule !mpm_netware.c>
#
# If you wish httpd to run as a different user or group, you must run
# httpd as root initially and it will switch.  
#
# User/Group: The name (or #number) of the user/group to run httpd as.
#  . On SCO (ODT 3) use "User nouser" and "Group nogroup".
#  . On HPUX you may not be able to use shared memory as nobody, and the
#    suggested workaround is to create a user www and use that user.
#  NOTE that some kernels refuse to setgid(Group) or semctl(IPC_SET)
#  when the value of (unsigned)Group is above 60000; 
#  don't use Group #-1 on these systems!
#
User nobody
Group #-1
</IfModule>
</IfModule>

#
# ServerAdmin: Your address, where problems with the server should be
# e-mailed.  This address appears on some server-generated pages, such
# as error documents.  e.g. admin@your-domain.com
#
ServerAdmin me@homenet.com


#
# Each directory to which Apache has access can be configured with respect
# to which services and features are allowed and/or disabled in that
# directory (and its subdirectories). 
#
# First, we configure the "default" to be a very restrictive set of 
# features.  
#
<Directory />
    Options FollowSymLinks
    AllowOverride None
</Directory>

#
# Note that from this point forward you must specifically allow
# particular features to be enabled - so if something's not working as
# you might expect, make sure that you have specifically enabled it
# below.
#
ServerTokens Full
ServerSignature On
LogLevel warn
### Section 3: Virtual Hosts
#
# VirtualHost: If you want to maintain multiple domains/hostnames on your
# machine you can setup VirtualHost containers for them. Most configurations
# use only name-based virtual hosts so the server doesn't need to worry about
# IP addresses. This is indicated by the asterisks in the directives below.
#
# Please see the documentation at 
# <URL:http://httpd.apache.org/docs/2.0/vhosts/>
# for further details before you try to setup virtual hosts.
#
# You may use the command line option '-S' to verify your virtual host
# configuration.

#
# Use name-based virtual hosting.
#
#NameVirtualHost *:80
NameVirtualHost server:80
NameVirtualHost server.homenet.local:443
#
# VirtualHost example:
# Almost any Apache directive may go into a VirtualHost container.
# The first VirtualHost section is used for requests without a known
# server name.
#
<VirtualHost server:80>
    DocumentRoot /usr/local/apache2/htdocs
    ServerName server.homenet.local
	ErrorLog /var/log/apache2/error.log
	CustomLog /var/log/apache2/access_log common
	DirectoryIndex index.html index.html.var


</VirtualHost>
<VirtualHost server.homenet.local:443>
	DocumentRoot /usr/local/apache2/ssl
    ServerName server.homenet.local
	ErrorLog /var/log/apache2/ssl/error.log
	CustomLog /var/log/apache2/ssl/access_log common
	DirectoryIndex index.html index.html.var

	
Alias /icons/ "/usr/local/apache2/icons/"

<Location /test/ObjServer>
	AuthName  "Home Network Authentication"
	AuthType  Basic
	AuthUserFile "conf/passwd"
	Require  valid-user
	Order   deny,allow
	Deny from all
	Allow from 192.168.0.15, 192.168.0.16, 192.168.0.17
	Satisfy any
</Location>

<Directory "/usr/local/apache2/icons">
    Options Indexes MultiViews
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>
#   SSL Engine Switch:
        #   Enable/Disable SSL for this virtual host.
        SSLEngine on

        #   A self-signed (snakeoil) certificate can be created by installing
        #   the ssl-cert package. See
        #   /usr/share/doc/apache2.2-common/README.Debian.gz for more info.
        #   If both key and certificate are stored in the same file, only the
        #   SSLCertificateFile directive is needed.
        SSLCertificateFile    /usr/local/apache2/conf/ssl.crt/server.pem
        SSLCertificateKeyFile /usr/local/apache2/conf/ssl.crt/server.key
</VirtualHost>
```

---

### Post by terazen on 2009-09-01
I think RedirectPermanent may be what you are looking for.

<VirtualHost *:80>
<Directory /var/www/something>
       RedirectPermanent / [https://something.com/](https://something.com/)
</Directory>

<VirtualHost *:443>
<Directory /var/www/something>
       SSLRequireSSL
</Directory>

---

### Post by Rever75 on 2009-09-01
Thanks I actually came across something else that worked too. I am using the rewrite module. This actually works very well and allows me to fix miss typed addresses. I will also look into the redirect too. Thanks :D

---

