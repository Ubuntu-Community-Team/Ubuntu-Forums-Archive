---
title: "Apache test server: using virtual hosts"
date: 2006-10-09
forum: Server Platforms
---

### Post by ImpelGD on 2006-10-09
I've installed XAMPP in Ubuntu, and am trying to get virtual hosts to work. I've followed [Apache's documentation]("http://httpd.apache.org/docs/2.2/vhosts/"), but I'm afraid my knowledge of the wider issues, such as DNS, is lacking and I'm at a standstill.

Here's what I want to be able to do: access the test web server including virtual hosts from *other computers on the LAN*.

Whether this is achieved using name-based or IP-based virtual hosts doesn't matter to me - I only have one ethernet card in my Ubuntu machine but have tried both methods (adding an IP address/alias in System > Administration > Networking).

Here's my hosts file:

```
127.0.0.1 localhost cabbage
127.0.1.1 cabbage

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.1.21 testsmk
```

My httpd.conf file:

```
#
# This is the main Apache HTTP server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See <URL:http://httpd.apache.org/docs/2.2> for detailed information.
# In particular, see 
# <URL:http://httpd.apache.org/docs/2.2/mod/directives.html>
# for a discussion of each configuration directive.
#
# Do NOT simply read the instructions in here without understanding
# what they do.  They're here only as hints or reminders.  If you are unsure
# consult the online docs. You have been warned.  
#
# Configuration and logfile names: If the filenames you specify for many
# of the server's control files begin with "/" (or "drive:/" for Win32), the
# server will use that explicit path.  If the filenames do *not* begin
# with "/", the value of ServerRoot is prepended -- so "logs/foo.log"
# with ServerRoot set to "/opt/lampp" will be interpreted by the
# server as "/opt/lampp/logs/foo.log".

#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# Do not add a slash at the end of the directory path.  If you point
# ServerRoot at a non-local disk, be sure to point the LockFile directive
# at a local disk.  If you wish to share the same ServerRoot for multiple
# httpd daemons, you will need to change at least LockFile and PidFile.
#
ServerRoot "/opt/lampp"

#
# Listen: Allows you to bind Apache to specific IP addresses and/or
# ports, instead of the default. See also the <VirtualHost>
# directive.
#
# Change this to Listen on specific IP addresses as shown below to 
# prevent Apache from glomming onto all bound IP addresses.
#
#Listen 12.34.56.78:80
Listen 80

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
LoadModule authn_file_module modules/mod_authn_file.so
LoadModule authn_dbm_module modules/mod_authn_dbm.so
LoadModule authn_anon_module modules/mod_authn_anon.so
LoadModule authn_dbd_module modules/mod_authn_dbd.so
LoadModule authn_default_module modules/mod_authn_default.so
LoadModule authz_host_module modules/mod_authz_host.so
LoadModule authz_groupfile_module modules/mod_authz_groupfile.so
LoadModule authz_user_module modules/mod_authz_user.so
LoadModule authz_dbm_module modules/mod_authz_dbm.so
LoadModule authz_owner_module modules/mod_authz_owner.so
LoadModule authnz_ldap_module modules/mod_authnz_ldap.so
LoadModule authz_default_module modules/mod_authz_default.so
LoadModule auth_basic_module modules/mod_auth_basic.so
LoadModule auth_digest_module modules/mod_auth_digest.so
LoadModule file_cache_module modules/mod_file_cache.so
LoadModule cache_module modules/mod_cache.so
LoadModule disk_cache_module modules/mod_disk_cache.so
LoadModule mem_cache_module modules/mod_mem_cache.so
# mod_dbd doesn't work in Apache 2.2.3: getting always heaps of "glibc detected *** corrupted double-linked list" on shutdown - oswald, 10sep06
#LoadModule dbd_module modules/mod_dbd.so
LoadModule bucketeer_module modules/mod_bucketeer.so
LoadModule dumpio_module modules/mod_dumpio.so
LoadModule echo_module modules/mod_echo.so
LoadModule case_filter_module modules/mod_case_filter.so
LoadModule case_filter_in_module modules/mod_case_filter_in.so
LoadModule ext_filter_module modules/mod_ext_filter.so
LoadModule include_module modules/mod_include.so
LoadModule filter_module modules/mod_filter.so
LoadModule charset_lite_module modules/mod_charset_lite.so
LoadModule deflate_module modules/mod_deflate.so
LoadModule ldap_module modules/mod_ldap.so
LoadModule log_config_module modules/mod_log_config.so
LoadModule logio_module modules/mod_logio.so
LoadModule env_module modules/mod_env.so
LoadModule mime_magic_module modules/mod_mime_magic.so
LoadModule cern_meta_module modules/mod_cern_meta.so
LoadModule expires_module modules/mod_expires.so
LoadModule headers_module modules/mod_headers.so
LoadModule ident_module modules/mod_ident.so
LoadModule usertrack_module modules/mod_usertrack.so
LoadModule unique_id_module modules/mod_unique_id.so
LoadModule setenvif_module modules/mod_setenvif.so
LoadModule proxy_module modules/mod_proxy.so
LoadModule proxy_connect_module modules/mod_proxy_connect.so
LoadModule proxy_ftp_module modules/mod_proxy_ftp.so
LoadModule proxy_http_module modules/mod_proxy_http.so
LoadModule proxy_ajp_module modules/mod_proxy_ajp.so
LoadModule proxy_balancer_module modules/mod_proxy_balancer.so
LoadModule mime_module modules/mod_mime.so
LoadModule dav_module modules/mod_dav.so
LoadModule status_module modules/mod_status.so
LoadModule autoindex_module modules/mod_autoindex.so
LoadModule asis_module modules/mod_asis.so
LoadModule info_module modules/mod_info.so
LoadModule suexec_module modules/mod_suexec.so
LoadModule cgi_module modules/mod_cgi.so
LoadModule cgid_module modules/mod_cgid.so
LoadModule dav_fs_module modules/mod_dav_fs.so
LoadModule vhost_alias_module modules/mod_vhost_alias.so
LoadModule negotiation_module modules/mod_negotiation.so
LoadModule dir_module modules/mod_dir.so
LoadModule imagemap_module modules/mod_imagemap.so
LoadModule actions_module modules/mod_actions.so
LoadModule speling_module modules/mod_speling.so
LoadModule userdir_module modules/mod_userdir.so
LoadModule alias_module modules/mod_alias.so
LoadModule rewrite_module modules/mod_rewrite.so
LoadModule apreq_module modules/mod_apreq2.so
LoadModule ssl_module modules/mod_ssl.so

<IfDefine JUSTTOMAKEAPXSHAPPY>
LoadModule php4_module        modules/libphp4.so
LoadModule php5_module        modules/libphp5.so
</IfDefine>

<IfModule !mpm_winnt_module>
<IfModule !mpm_netware_module>
#
# If you wish httpd to run as a different user or group, you must run
# httpd as root initially and it will switch.  
#
# User/Group: The name (or #number) of the user/group to run httpd as.
# It is usually good practice to create a dedicated user and group for
# running httpd, as with most system services.
#
User nobody
Group nogroup
</IfModule>
</IfModule>

# 'Main' server configuration
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

#
# ServerAdmin: Your address, where problems with the server should be
# e-mailed.  This address appears on some server-generated pages, such
# as error documents.  e.g. admin@your-domain.com
#
ServerAdmin me@here.com

#
# ServerName gives the name and port that the server uses to identify itself.
# This can often be determined automatically, but we recommend you specify
# it explicitly to prevent problems during startup.
#
# If your host doesn't have a registered DNS name, enter its IP address here.
#
#ServerName www.example.com:80
# XAMPP
ServerName localhost

#
# DocumentRoot: The directory out of which you will serve your
# documents. By default, all requests are taken from this directory, but
# symbolic links and aliases may be used to point to other locations.
#
DocumentRoot "/opt/lampp/htdocs"

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
    #XAMPP
    #Order deny,allow
    #Deny from all
</Directory>

#
# Note that from this point forward you must specifically allow
# particular features to be enabled - so if something's not working as
# you might expect, make sure that you have specifically enabled it
# below.
#

#
# This should be changed to whatever you set DocumentRoot to.
#
<Directory "/opt/lampp/htdocs">
    #
    # Possible values for the Options directive are "None", "All",
    # or any combination of:
    #   Indexes Includes FollowSymLinks SymLinksifOwnerMatch ExecCGI MultiViews
    #
    # Note that "MultiViews" must be named *explicitly* --- "Options All"
    # doesn't give it to you.
    #
    # The Options directive is both complicated and important.  Please see
    # http://httpd.apache.org/docs/2.2/mod/core.html#options
    # for more information.
    #
    #Options Indexes FollowSymLinks
    # XAMPP
    Options Indexes FollowSymLinks ExecCGI Includes


    #
    # AllowOverride controls what directives may be placed in .htaccess files.
    # It can be "All", "None", or any combination of the keywords:
    #   Options FileInfo AuthConfig Limit
    #
    #AllowOverride None
    # since XAMPP 1.4:
    AllowOverride All


    #
    # Controls who can get stuff from this server.
    #
    Order allow,deny
    Allow from all

</Directory>

#
# DirectoryIndex: sets the file that Apache will serve if a directory
# is requested.
#
<IfModule dir_module>
    #DirectoryIndex index.html
    # XAMPP
    DirectoryIndex index.html index.html.var index.php index.php3 index.php4
</IfModule>

#
# The following lines prevent .htaccess and .htpasswd files from being 
# viewed by Web clients. 
#
<FilesMatch "^\.ht">
    Order allow,deny
    Deny from all
</FilesMatch>

#
# ErrorLog: The location of the error log file.
# If you do not specify an ErrorLog directive within a <VirtualHost>
# container, error messages relating to that virtual host will be
# logged here.  If you *do* define an error logfile for a <VirtualHost>
# container, that host's errors will be logged there and not here.
#
ErrorLog logs/error_log

#
# LogLevel: Control the number of messages logged to the error_log.
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
#
LogLevel warn

<IfModule log_config_module>
    #
    # The following directives define some format nicknames for use with
    # a CustomLog directive (see below).
    #
    LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
    LogFormat "%h %l %u %t \"%r\" %>s %b" common

    <IfModule logio_module>
      # You need to enable mod_logio.c to use %I and %O
      LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\" %I %O" combinedio
    </IfModule>

    #
    # The location and format of the access logfile (Common Logfile Format).
    # If you do not define any access logfiles within a <VirtualHost>
    # container, they will be logged here.  Contrariwise, if you *do*
    # define per-<VirtualHost> access logfiles, transactions will be
    # logged therein and *not* in this file.
    #
    CustomLog logs/access_log common

    #
    # If you prefer a logfile with access, agent, and referer information
    # (Combined Logfile Format) you can use the following directive.
    #
    #CustomLog logs/access_log combined
</IfModule>

<IfModule alias_module>
    #
    # Redirect: Allows you to tell clients about documents that used to 
    # exist in your server's namespace, but do not anymore. The client 
    # will make a new request for the document at its new location.
    # Example:
    # Redirect permanent /foo http://www.example.com/bar

    #
    # Alias: Maps web paths into filesystem paths and is used to
    # access content that does not live under the DocumentRoot.
    # Example:
    # Alias /webpath /full/filesystem/path
    #
    # If you include a trailing / on /webpath then the server will
    # require it to be present in the URL.  You will also likely
    # need to provide a <Directory> section to allow access to
    # the filesystem path.

    #
    # ScriptAlias: This controls which directories contain server scripts. 
    # ScriptAliases are essentially the same as Aliases, except that
    # documents in the target directory are treated as applications and
    # run by the server when requested rather than as documents sent to the
    # client.  The same rules about trailing "/" apply to ScriptAlias
    # directives as to Alias.
    #
    ScriptAlias /cgi-bin/ "/opt/lampp/cgi-bin/"

</IfModule>

<IfModule cgid_module>
    #
    # ScriptSock: On threaded servers, designate the path to the UNIX
    # socket used to communicate with the CGI daemon of mod_cgid.
    #
    #Scriptsock logs/cgisock
</IfModule>

#
# "/opt/lampp/cgi-bin" should be changed to whatever your ScriptAliased
# CGI directory exists, if you have that configured.
#
<Directory "/opt/lampp/cgi-bin">
    AllowOverride None
    Options None
    Order allow,deny
    Allow from all
</Directory>

#
# DefaultType: the default MIME type the server will use for a document
# if it cannot otherwise determine one, such as from filename extensions.
# If your server contains mostly text or HTML documents, "text/plain" is
# a good value.  If most of your content is binary, such as applications
# or images, you may want to use "application/octet-stream" instead to
# keep browsers from trying to display binary files as though they are
# text.
#
DefaultType text/plain

<IfModule mime_module>
    #
    # TypesConfig points to the file containing the list of mappings from
    # filename extension to MIME-type.
    #
    TypesConfig etc/mime.types

    #
    # AddType allows you to add to or override the MIME configuration
    # file specified in TypesConfig for specific file types.
    #
    #AddType application/x-gzip .tgz
    #
    # AddEncoding allows you to have certain browsers uncompress
    # information on the fly. Note: Not all browsers support this.
    #
    #AddEncoding x-compress .Z
    #AddEncoding x-gzip .gz .tgz
    #
    # If the AddEncoding directives above are commented-out, then you
    # probably should define those extensions to indicate media types:
    #
    AddType application/x-compress .Z
    AddType application/x-gzip .gz .tgz

    #
    # AddHandler allows you to map certain file extensions to "handlers":
    # actions unrelated to filetype. These can be either built into the server
    # or added with the Action directive (see below)
    #
    # To use CGI scripts outside of ScriptAliased directories:
    # (You will also need to add "ExecCGI" to the "Options" directive.)
    #
    #AddHandler cgi-script .cgi
    # XAMPP, since LAMPP 0.9.8:
    AddHandler cgi-script .cgi .pl

    # For files that include their own HTTP headers:
    #AddHandler send-as-is asis

    # For server-parsed imagemap files:
    #AddHandler imap-file map

    # For type maps (negotiated resources):
    #AddHandler type-map var

    #
    # Filters allow you to process content before it is sent to the client.
    #
    # To parse .shtml files for server-side includes (SSI):
    # (You will also need to add "Includes" to the "Options" directive.)
    #
    # XAMPP
    AddType text/html .shtml
    AddOutputFilter INCLUDES .shtml
</IfModule>

#
# The mod_mime_magic module allows the server to use various hints from the
# contents of the file itself to determine its type.  The MIMEMagicFile
# directive tells the module where the hint definitions are located.
#
#MIMEMagicFile etc/magic

#
# Customizable error responses come in three flavors:
# 1) plain text 2) local redirects 3) external redirects
#
# Some examples:
#ErrorDocument 500 "The server made a boo boo."
#ErrorDocument 404 /missing.html
#ErrorDocument 404 "/cgi-bin/missing_handler.pl"
#ErrorDocument 402 http://www.example.com/subscription_info.html
#

#
# EnableMMAP and EnableSendfile: On systems that support it, 
# memory-mapping or the sendfile syscall is used to deliver
# files.  This usually improves server performance, but must
# be turned off when serving from networked-mounted 
# filesystems or if support for these functions is otherwise
# broken on your system.
#
EnableMMAP off
EnableSendfile off

# Supplemental configuration
#
# The configuration files in the etc/extra/ directory can be 
# included to add extra features or to modify the default configuration of 
# the server, or you may simply copy their contents here and change as 
# necessary.

# Server-pool management (MPM specific)
#Include etc/extra/httpd-mpm.conf

# Multi-language error messages
#Include etc/extra/httpd-multilang-errordoc.conf

# Fancy directory listings
Include etc/extra/httpd-autoindex.conf

# Language settings
#Include etc/extra/httpd-languages.conf

# User home directories
#Include etc/extra/httpd-userdir.conf

# Real-time info on requests and configuration
#Include etc/extra/httpd-info.conf

# Virtual hosts
Include etc/extra/httpd-vhosts.conf

# Local access to the Apache HTTP Server Manual
#Include etc/extra/httpd-manual.conf

# Distributed authoring and versioning (WebDAV)
#Include etc/extra/httpd-dav.conf

# Various default settings
Include etc/extra/httpd-default.conf

# Secure (SSL/TLS) connections
<IfModule ssl_module>
# XAMPP
<IfDefine SSL>
Include etc/extra/httpd-ssl.conf
</IfDefine>
</IfModule>
#
# Note: The following must must be present to support
#       starting without SSL on platforms with no /dev/random equivalent
#       but a statically compiled-in mod_ssl.
#
<IfModule ssl_module>
SSLRandomSeed startup builtin
SSLRandomSeed connect builtin
</IfModule>

# XAMPP
Include etc/extra/httpd-xampp.conf

```

My httpd-vhosts.conf file:

```
#
# Virtual Hosts
#
# If you want to maintain multiple domains/hostnames on your
# machine you can setup VirtualHost containers for them. Most configurations
# use only name-based virtual hosts so the server doesn't need to worry about
# IP addresses. This is indicated by the asterisks in the directives below.
#
# Please see the documentation at 
# <URL:http://httpd.apache.org/docs/2.2/vhosts/>
# for further details before you try to setup virtual hosts.
#
# You may use the command line option '-S' to verify your virtual host
# configuration.

#
# Use name-based virtual hosting.
#
NameVirtualHost *:80

#
# VirtualHost example:
# Almost any Apache directive may go into a VirtualHost container.
# The first VirtualHost section is used for all requests that do not
# match a ServerName or ServerAlias in any <VirtualHost> block.
#
#<VirtualHost *:80>
#    ServerAdmin webmaster@dummy-host.example.com
#    DocumentRoot /www/docs/dummy-host.example.com
#    ServerName dummy-host.example.com
#    ServerAlias www.dummy-host.example.com
#    ErrorLog logs/dummy-host.example.com-error_log
#    CustomLog logs/dummy-host.example.com-access_log common
#</VirtualHost>
#
#<VirtualHost *:80>
#    ServerAdmin webmaster@dummy-host2.example.com
#    DocumentRoot /www/docs/dummy-host2.example.com
#    ServerName dummy-host2.example.com
#    ErrorLog logs/dummy-host2.example.com-error_log
#    CustomLog logs/dummy-host2.example.com-access_log common
#</VirtualHost>

<VirtualHost *>
	DocumentRoot	/opt/lampp/htdocs
</VirtualHost>

<VirtualHost *>
	ServerName	testsmk
	DocumentRoot	/opt/lampp/htdocs/smk
</VirtualHost>

```

Using '192.168.1.21' or 'testsmk' from a different PC browser or with a browser on the server machine doesn't work. Using the machine name of 'cabbage' does work locally on the server machine, but on the other PC it doesn't.

Do I have to use actual real domain names which are pointed at me, or is it possible to simply use names/domains I make up? Do they need a domain extension (eg. .com)?

As you can tell, I'm lost...

I've a feeling I need to tell my other PC what to do with 'cabbage', perhaps via DNS? It's simply using DHCP defaults from my ADSL router at the moment.

Any guidance appreciated - please ask for more information if anything's not clear. Many thanks.

---

### Post by sonic2000gr on 2006-10-09
Delete this line from your hosts file:

```

127.0.1.1 cabbage

```

The line mentioning 127.0.0.1 is correct as is the 192.168.1.21 (if of course this is your ip address)

To use name based virtual hosting you need a

```

ServerName myname

```

for every virtual host. You already have ServerName testsmsk

In every other computer on the network, you need to add a line in the its own hosts file like this:

192.168.1.21 testsmsk

If the other machines are Windows based, you can find the hosts file at the following location:

```

c:\windows\system32\drivers\etc\hosts

```

Please make sure your network is working correctly and the IP address 192.168.1.21 is correct. Try a ping 192.168.1.21 from another machine on your network. You don't need dns or fully qualified names for your network, as long as you add your hostname to every hosts file.

---

### Post by ImpelGD on 2006-10-09
Thanks sonic.

The local IP address of the Ubuntu test server is 192.168.1.3 (have removed references to .21 as this was an IP-based virtual host experiment).

I've now got [http://testsmk/](http://testsmk/) pointing to the test server as per your instructions - the other machine is indeed a Windows one (thanks for the hosts file location).

My Ubuntu hosts file:

```
127.0.0.1 localhost cabbage

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.1.3 cabbage testsmk
```

However, using [http://testsmk/](http://testsmk/) doesn't result in the smk directory being served. Rather, the htdocs directory above it is.

Here's my httpd-vhosts.conf file (slightly modified from last time):

```
#
# Virtual Hosts
#
# If you want to maintain multiple domains/hostnames on your
# machine you can setup VirtualHost containers for them. Most configurations
# use only name-based virtual hosts so the server doesn't need to worry about
# IP addresses. This is indicated by the asterisks in the directives below.
#
# Please see the documentation at 
# <URL:http://httpd.apache.org/docs/2.2/vhosts/>
# for further details before you try to setup virtual hosts.
#
# You may use the command line option '-S' to verify your virtual host
# configuration.

#
# Use name-based virtual hosting.
#
NameVirtualHost *:80

#
# VirtualHost example:
# Almost any Apache directive may go into a VirtualHost container.
# The first VirtualHost section is used for all requests that do not
# match a ServerName or ServerAlias in any <VirtualHost> block.
#
#<VirtualHost *:80>
#    ServerAdmin webmaster@dummy-host.example.com
#    DocumentRoot /www/docs/dummy-host.example.com
#    ServerName dummy-host.example.com
#    ServerAlias www.dummy-host.example.com
#    ErrorLog logs/dummy-host.example.com-error_log
#    CustomLog logs/dummy-host.example.com-access_log common
#</VirtualHost>
#
#<VirtualHost *:80>
#    ServerAdmin webmaster@dummy-host2.example.com
#    DocumentRoot /www/docs/dummy-host2.example.com
#    ServerName dummy-host2.example.com
#    ErrorLog logs/dummy-host2.example.com-error_log
#    CustomLog logs/dummy-host2.example.com-access_log common
#</VirtualHost>

<VirtualHost *>
	ServerName	cabbage
	DocumentRoot	/opt/lampp/htdocs
</VirtualHost>

<VirtualHost *>
	ServerName	testsmk
	DocumentRoot	/opt/lampp/htdocs/smk
</VirtualHost>

```

---

### Post by sonic2000gr on 2006-10-09
Try modifying your 

```

<VirtualHost *>

```

lines to read:

```

<VirtualHost *:80>

```

your virtual hosts are not working, apache just servers the first site it finds.

---

### Post by ImpelGD on 2006-10-09
:KS You star! It's working now - thanks very much. I thought leaving the port number off would allow all ports.

All I need to do now is work out how to gain direct read and write access to the smk directory in question from the Windows machine. From what I can gather I'll do this using Samba... I'll leave that for tomorrow.

Thanks again.

---

### Post by sonic2000gr on 2006-10-09
Samba is a great idea if you only need to upload from the local network. Otherwise (or additionally) you could use ftp.

---

### Post by ImpelGD on 2006-10-09
> **sonic2000gr said:**
> Samba is a great idea if you only need to upload from the local network. Otherwise (or additionally) you could use ftp.
Does Samba not allow for downloading as well? I've got FTP access at the moment courtesy of the FTP server which came with XAMPP, but would rather not have to go through the process of transferring after each update and work directly on the server files if possible.

---

### Post by sonic2000gr on 2006-10-09
Sure, samba will of course work both ways. It is however a local network only service - it will be no good if you wish to upload / download files from a dial up (wan) connection.

---

### Post by ImpelGD on 2006-10-09
I see - Samba should do me very nicely if I can get it set up then.

Thanks again for all your help and advice sonic.

---

