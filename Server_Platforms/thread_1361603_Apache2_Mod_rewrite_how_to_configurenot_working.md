---
title: "Apache2 Mod rewrite how to configure/not working"
date: 2009-12-22
forum: Server Platforms
---

### Post by tapas_mishra on 2009-12-22
Hi,
I have apache2 on Jaunty I checked
```

root@tapas-laptop:/etc/apache2# apache2ctl -l
Compiled in modules:
  core.c
  mod_log_config.c
  mod_logio.c
  prefork.c
  http_core.c
  mod_so.c

```
Mod rewrite did not showed me 
then I tried to enable it via 
```

a2enmod rewrite

```

I checked again 
```

root@tapas-laptop:/etc/apache2# apache2ctl -l
Compiled in modules:
  core.c
  mod_log_config.c
  mod_logio.c
  prefork.c
  http_core.c
  mod_so.c

```
mode rewrite was not available 
here now  
```

root@tapas-laptop:/usr/lib/apache2/modules# a2enmod rewrite
Enabling module rewrite.
Run '/etc/init.d/apache2 restart' to activate new configuration!


```

I checked via 
```

root@tapas-laptop:/etc/apache2# apache2 -M
apache2: bad user name ${APACHE_RUN_USER}

```
Still of no use 
```

root@tapas-laptop:/etc/apache2# apache2ctl -l
Compiled in modules:
  core.c
  mod_log_config.c
  mod_logio.c
  prefork.c
  http_core.c
  mod_so.c

```
So finally how should I proceed on to enable mod rewrite on my machine it is Ubuntu 9.04 
do i need to install some thing else to be able to do so I checked

```

root@tapas-laptop:/usr/lib/apache2/modules# ls
httpd.exp               mod_cgid.so          mod_mem_cache.so
libphp5.so              mod_cgi.so           mod_mime_magic.so
mod_actions.so          mod_charset_lite.so  mod_mime.so
mod_alias.so            mod_dav_fs.so        mod_negotiation.so
mod_asis.so             mod_dav_lock.so      mod_proxy_ajp.so
mod_auth_basic.so       mod_dav.so           mod_proxy_balancer.so
mod_auth_digest.so      mod_dbd.so           mod_proxy_connect.so
mod_authn_alias.so      mod_deflate.so       mod_proxy_ftp.so
mod_authn_anon.so       mod_dir.so           mod_proxy_http.so
mod_authn_dbd.so        mod_disk_cache.so    mod_proxy.so
mod_authn_dbm.so        mod_dumpio.so        mod_rewrite.so
mod_authn_default.so    mod_env.so           mod_ruby.so
mod_authn_file.so       mod_expires.so       mod_setenvif.so
mod_authnz_ldap.so      mod_ext_filter.so    mod_speling.so
mod_authz_dbm.so        mod_file_cache.so    mod_ssl.so
mod_authz_default.so    mod_filter.so        mod_status.so
mod_authz_groupfile.so  mod_headers.so       mod_substitute.so
mod_authz_host.so       mod_ident.so         mod_suexec.so
mod_authz_owner.so      mod_imagemap.so      mod_unique_id.so
mod_authz_user.so       mod_include.so       mod_userdir.so
mod_autoindex.so        mod_info.so          mod_usertrack.so
mod_cache.so            mod_ldap.so          mod_version.so
mod_cern_meta.so        mod_log_forensic.so  mod_vhost_alias.so

```
and mod_rewrite.so
is available here so I don't think that I need to install any thing else just some thing is missing some where 

I am posting my apache2.conf here which probably should give a clue
```

#
# Based upon the NCSA server configuration files originally by Rob McCool.
#
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See http://httpd.apache.org/docs/2.2/ for detailed information about
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
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75
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
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

#
# Define an access log for VirtualHosts that don't define their own logfile
# Define an access log for VirtualHosts that don't define their own logfile
CustomLog /var/log/apache2/other_vhosts_access.log vhost_combined

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
# Putting this all together, we can internationalize error responses.
#
# We use Alias to redirect any /error/HTTP_<error>.html.var response to
# our collection of by-error message multi-language collections.  We use 
# includes to substitute the appropriate text.
#
# You can modify the messages' appearance without changing any of the
# default HTTP_<error>.html.var files by adding the line:
#
#   Alias /error/include/ "/your/include/path/"
#
# which allows you to create your own set of files by starting with the
# /usr/share/apache2/error/include/ files and copying them to /your/include/path/, 
# even on a per-VirtualHost basis.  The default include files will display
# your Apache version number and your ServerAdmin email address regardless
# of the setting of ServerSignature.
#
# The internationalized error documents require mod_alias, mod_include
# and mod_negotiation.  To activate them, uncomment the following 30 lines.
#    Alias /error/ "/usr/share/apache2/error/"
#
#    <Directory "/usr/share/apache2/error">
#        AllowOverride None
#        Options IncludesNoExec
#        AddOutputFilter Includes html
#        AddHandler type-map var
#        Order allow,deny
#        Allow from all
#        LanguagePriority en cs de es fr it nl sv pt-br ro
#        ForceLanguagePriority Prefer Fallback
#    </Directory>
#
#    ErrorDocument 400 /error/HTTP_BAD_REQUEST.html.var
#    ErrorDocument 401 /error/HTTP_UNAUTHORIZED.html.var
#    ErrorDocument 403 /error/HTTP_FORBIDDEN.html.var
#    ErrorDocument 404 /error/HTTP_NOT_FOUND.html.var
#    ErrorDocument 405 /error/HTTP_METHOD_NOT_ALLOWED.html.var
#    ErrorDocument 408 /error/HTTP_REQUEST_TIME_OUT.html.var
#    ErrorDocument 410 /error/HTTP_GONE.html.var
#    ErrorDocument 411 /error/HTTP_LENGTH_REQUIRED.html.var
#    ErrorDocument 412 /error/HTTP_PRECONDITION_FAILED.html.var
#    ErrorDocument 413 /error/HTTP_REQUEST_ENTITY_TOO_LARGE.html.var
#    ErrorDocument 414 /error/HTTP_REQUEST_URI_TOO_LARGE.html.var
#    ErrorDocument 415 /error/HTTP_UNSUPPORTED_MEDIA_TYPE.html.var
#    ErrorDocument 500 /error/HTTP_INTERNAL_SERVER_ERROR.html.var
#    ErrorDocument 501 /error/HTTP_NOT_IMPLEMENTED.html.var
#    ErrorDocument 502 /error/HTTP_BAD_GATEWAY.html.var
#    ErrorDocument 503 /error/HTTP_SERVICE_UNAVAILABLE.html.var
#    ErrorDocument 506 /error/HTTP_VARIANT_ALSO_VARIES.html.var



# Include of directories ignores editors' and dpkg's backup files,
                                                                                                                                                      239,1         95%
# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

#Following line was added by me
#Include /etc/phpmyadmin/apache.conf
#NameVirtualHost 127.0.0.1:80
~                                

```
What next should I try ?

---

### Post by oneloveamaru on 2009-12-22
Did you actually restart Apache after you enabled this module? If you don't, Apache won't pick it up.

When you enable mod_rewrite, it's just a symlink between /etc/apache2/mods-available/rewrite.load going to /etc/apache2/mods-enabled/rewrite.load

Did you check to make sure the sym link exists?

 rewrite.load -> ../mods-available/rewrite.load

---

### Post by tapas_mishra on 2009-12-22
> **oneloveamaru said:**
> Did you actually restart Apache after you enabled this module? If you don't, Apache won't pick it up.

Yes I had restarted Apache2 but it did not helped.

> **oneloveamaru said:**
> 
When you enable mod_rewrite, it's just a symlink between /etc/apache2/mods-available/rewrite.load going to /etc/apache2/mods-enabled/rewrite.load

Did you check to make sure the sym link exists?

 rewrite.load -> ../mods-available/rewrite.load
Well the sym link does not exists here is the out put 
```

root@tapas-laptop:/etc/apache2/mods-available# ls -l rewrite.load 
-rw-r--r-- 1 root root 66 2009-08-18 19:54 rewrite.load
root@tapas-laptop:/etc/apache2/mods-available# vi rewrite.load 

```So there is no symlink 
though the file inside it has following line 
```

LoadModule rewrite_module /usr/lib/apache2/modules/mod_rewrite.so

```

I have a question also in the above message in apache2.conf should there be any line like 
<IfModule>
Some thing about rewrite here .....correct me if I am wrong.

---

### Post by oneloveamaru on 2009-12-22
No, there does not need to be any <ifModule> statement in apache2.conf for mod_rewrite.

To load the modules, you need this in apache2.conf though, which you do have in the one you posted:

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

Also, in my first reply, I stated:
"it's just a symlink between /etc/apache2/mods-available/rewrite.load going **to** /etc/apache2/mods-enabled/rewrite.load" 

AND

"rewrite.load -> ../mods-available/rewrite.load"

Anyways, ALL the sym links for enabled modules will be located in /etc/apache2/mods-enabled/. You are looking for it in /etc/apache2/mods-available, which is where all of the modules are located, whether they are enabled or not.

I missed this before but this is probably your problem.

[COLOR="Red"]root@tapas-laptop:/etc/apache2# apache2 -M
apache2: bad user name ${APACHE_RUN_USER}[/COLOR]

Check /etc/apache2/envvars for these three lines:
export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data
export APACHE_PID_FILE=/var/run/apache2.pid

The error says "bad user name" so either you are trying to run Apache as someone else or the username is wrong. I would suggest using the default "www-data" user.

If it does say www-data, check /etc/passwd to make sure the user exists still.

---

### Post by tapas_mishra on 2009-12-22
> **oneloveamaru said:**
> 
"rewrite.load -> ../mods-available/rewrite.load"

Ok this is present 
```

root@tapas-laptop:/etc/apache2/mods-enabled# ls -l rewrite.load 
lrwxrwxrwx 1 root root 30 2009-12-22 16:26 rewrite.load -> ../mods-available/rewrite.load

```

> **oneloveamaru said:**
> 
[COLOR=Red]root@tapas-laptop:/etc/apache2# apache2 -M
apache2: bad user name ${APACHE_RUN_USER}[/COLOR]

Check /etc/apache2/envvars for these three lines:
export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data
export APACHE_PID_FILE=/var/run/apache2.pid

The error says "bad user name" so either you are trying to run Apache as someone else or the username is wrong. I would suggest using the default "www-data" user.

I am not clear on this part you mean to say I should do
su www-data
and then do what ever you suggested

> **oneloveamaru said:**
> 
If it does say www-data, check /etc/passwd to make sure the user exists still.
Yes the user www-data exists

---

### Post by oneloveamaru on 2009-12-22
Dude, open /etc/apache2/envvars with your favorite editor and make sure these three lines exist and they are spelled correctly:


export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data
export APACHE_PID_FILE=/var/run/apache2.pid

Then run "apache2ctl -M"

And when you run that and see something like this... you'll know everything is now working...

Loaded Modules:
 core_module (static)
 log_config_module (static)
 logio_module (static)
 mpm_worker_module (static)
 http_module (static)
 so_module (static)
 alias_module (shared)
 auth_basic_module (shared)
 authn_file_module (shared)
 authz_default_module (shared)
 authz_groupfile_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 cgid_module (shared)
 dir_module (shared)
 env_module (shared)
 jk_module (shared)
 mime_module (shared)
 negotiation_module (shared)
 rewrite_module (shared)
 setenvif_module (shared)
 ssl_module (shared)
 status_module (shared)
Syntax OK

---

### Post by tapas_mishra on 2009-12-23
> **oneloveamaru said:**
> Dude, open /etc/apache2/envvars with your favorite editor and make sure these three lines exist and they are spelled correctly:


export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data
export APACHE_PID_FILE=/var/run/apache2.pid

Yes these lines exist as you have mentioned here

> **oneloveamaru said:**
> 
Then run "apache2ctl -M"

And when you run that and see something like this... you'll know everything is now working...

Loaded Modules:
 core_module (static)
 log_config_module (static)
 logio_module (static)
 mpm_worker_module (static)
 http_module (static)
 so_module (static)
 alias_module (shared)
 auth_basic_module (shared)
 authn_file_module (shared)
 authz_default_module (shared)
 authz_groupfile_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 cgid_module (shared)
 dir_module (shared)
 env_module (shared)
 jk_module (shared)
 mime_module (shared)
 negotiation_module (shared)
 rewrite_module (shared)
 setenvif_module (shared)
 ssl_module (shared)
 status_module (shared)
Syntax OK
and this is the output as you have said 
and is matching 
```

root@tapas-laptop:~# apache2ctl -M
Loaded Modules:
 core_module (static)
 log_config_module (static)
 logio_module (static)
 mpm_prefork_module (static)
 http_module (static)
 so_module (static)
 actions_module (shared)
 alias_module (shared)
 auth_basic_module (shared)
 authn_file_module (shared)
 authz_default_module (shared)
 authz_groupfile_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 cgi_module (shared)
 deflate_module (shared)
 dir_module (shared)
 env_module (shared)
 mime_module (shared)
 negotiation_module (shared)
 php5_module (shared)
 rewrite_module (shared)
 ruby_module (shared)
 setenvif_module (shared)
 status_module (shared)
 userdir_module (shared)
Syntax OK

```
So does that means mode rewrite is enabled on my system.

---

### Post by tapas_mishra on 2009-12-23
> **oneloveamaru said:**
> Dude, open /etc/apache2/envvars with your favorite editor and make sure these three lines exist and they are spelled correctly:


export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data
export APACHE_PID_FILE=/var/run/apache2.pid

Yes these lines exist as you have mentioned here

> **oneloveamaru said:**
> 
Then run "apache2ctl -M"

And when you run that and see something like this... you'll know everything is now working...

Loaded Modules:
 core_module (static)
 log_config_module (static)
 logio_module (static)
 mpm_worker_module (static)
 http_module (static)
 so_module (static)
 alias_module (shared)
 auth_basic_module (shared)
 authn_file_module (shared)
 authz_default_module (shared)
 authz_groupfile_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 cgid_module (shared)
 dir_module (shared)
 env_module (shared)
 jk_module (shared)
 mime_module (shared)
 negotiation_module (shared)
 rewrite_module (shared)
 setenvif_module (shared)
 ssl_module (shared)
 status_module (shared)
Syntax OK
and this is the output as you have said 
and is matching 
```

root@tapas-laptop:~# apache2ctl -M
Loaded Modules:
 core_module (static)
 log_config_module (static)
 logio_module (static)
 mpm_prefork_module (static)
 http_module (static)
 so_module (static)
 actions_module (shared)
 alias_module (shared)
 auth_basic_module (shared)
 authn_file_module (shared)
 authz_default_module (shared)
 authz_groupfile_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 cgi_module (shared)
 deflate_module (shared)
 dir_module (shared)
 env_module (shared)
 mime_module (shared)
 negotiation_module (shared)
 php5_module (shared)
 rewrite_module (shared)
 ruby_module (shared)
 setenvif_module (shared)
 status_module (shared)
 userdir_module (shared)
Syntax OK

```To be sure enough 
I made a php file and used following 
```

<?php
phpinfo();
?>

```and in the page there was a section 
**[FONT=Georgia][SIZE=2]apache2handler[/SIZE][/FONT]**





and in subsection Loaded Modules I saw 
```

core 
mod_log_config
 mod_logio prefork
 http_core mod_so 
mod_actions 
mod_alias 
mod_auth_basic mod_authn_file 
mod_authz_default 
mod_authz_groupfile 
mod_authz_host 
mod_authz_user 
mod_autoindex 
mod_cgi 
mod_deflate 
mod_dir 
mod_env 
mod_mime 
mod_negotiation 
mod_php5
**mod_rewrite** 
mod_ruby 
mod_setenvif 
mod_status 
mod_userdir

```
You can see I have bolded mod_rewrite
So does that means mode rewrite is enabled on my system.

---

### Post by oneloveamaru on 2009-12-23
Yes that means it's enabled on the system.

Turn it on in a virtual host and restart apache. See if it errors out.

RewriteEngine On <-- put that in one of your virtual hosts.

---

### Post by tapas_mishra on 2009-12-23
> **oneloveamaru said:**
> Yes that means it's enabled on the system.

Turn it on in a virtual host and restart apache. See if it errors out.

RewriteEngine On <-- put that in one of your virtual hosts.
Okay thanks a lot.

---

