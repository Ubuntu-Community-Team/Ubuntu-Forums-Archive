---
title: "[warn] module php5_module is already loaded"
date: 2008-06-18
forum: Server Platforms
---

### Post by satimis on 2008-06-18
Hi folks,


Ubuntu 7.04 server amd64


$ sudo /etc/init.d/apache2 restart```

 * Forcing reload of web server (apache2)...                                    [Wed Jun 18 18:01:49 2008] [warn] module php5_module is already loaded, skipping
[Wed Jun 18 18:01:59 2008] [warn] module php5_module is already loaded, skipping
                                                                         [ OK ]

```


$ cat /etc/apache2/httpd.conf | grep php5```

LoadModule php5_module modules/libphp5.so

```


$ cat /etc/apache2/httpd.conf | grep LoadModule```

LoadModule php5_module modules/libphp5.so

```
Only one line there.


$ sudo find / -name *.conf```

/usr/lib/vmware-mui/apache/conf/httpd.conf
/usr/lib/vmware-mui/src/apache/conf/httpd.conf
/usr/local/src/vmware-mui-distrib-1.0.4-56528/mui/apache/conf/httpd.conf
/usr/local/src/vmware-mui-distrib-1.0.4-56528/mui/src/apache/conf/httpd.conf
/home/satimis/ShareData/Ubuntu_704_Server_Work/httpd.conf
/home/satimis/ShareData/Ubuntu_704_server/httpd.conf
/home/satimis/httpd.conf
/etc/apache2/httpd.conf

```


I suppose Apache starts twice.


VMware server is running on this box with Ubuntu as host OS and CentOS as guest OS.  


Please advise how to fix this problem?  TIA


B.R.
satimis

---

### Post by windependence on 2008-06-18
So why are you running Apache on the host box? You should not be running anything but VMware on the host and your applications should be on guests.

Can you post the output of 

```
cat /etc/init.d/apache2
```

-Tim

---

### Post by satimis on 2008-06-18
> **windependence said:**
> So why are you running Apache on the host box? You should not be running anything but VMware on the host and your applications should be on guests.
Hi Tim,


Theis is a mail server runing postfix.  SquirrelMail is also running on it.  Later I installed VMWare and ran CentOS 5 on it as guest.  My then plan was to run a web server on the Guest retaining Postfix running on the host.  Because both SM on the host and the web server on the guest need Apache.  So both of them need port 80 to run.  I failed to backport port 80 to the host.  I just stopped there not proceeding the test further (This is a test).  

At the beginning Apache was running on VMware.  It worked w/o problem.  Until an hour ago I restarted Apache2 discovering this problem.  I suppose it was caused by running update on repo.  I did not notice it.  The mail server is working w/o problem.


> 
Can you post the output of 

```
cat /etc/init.d/apache2
```
$ cat /etc/init.d/apache2 ```

#!/bin/sh -e
#
# apache2               This init.d script is used to start apache2.
#                       It basically just calls apache2ctl.

ENV="env -i LANG=C PATH=/usr/local/bin:/usr/bin:/bin"

#[ `ls -1 /etc/apache2/sites-enabled/ | wc -l | sed -e 's/ *//;'` -eq 0 ] && \
#echo "You haven't enabled any sites yet, so I'm not starting apache2." && \
#echo "To add and enable a host, use addhost and enhost." && exit 0

#edit /etc/default/apache2 to change this.
NO_START=0

set -e
if [ -x /usr/sbin/apache2 ] ; then
        HAVE_APACHE2=1
else
        echo "No apache MPM package installed"
        exit 0
fi

. /lib/lsb/init-functions

test -f /etc/default/rcS && . /etc/default/rcS
test -f /etc/default/apache2 && . /etc/default/apache2
if [ "$NO_START" != "0" -a "$1" != "stop" ]; then 
        [ "$VERBOSE" != no ] && log_warning_msg "Not starting apache2 - edit /et
c/default/apache2 and change NO_START to be 0.";
        exit 0;
fi

APACHE2="$ENV /usr/sbin/apache2"
APACHE2CTL="$ENV /usr/sbin/apache2ctl"

pidof_apache() {
    # if pidof is null for some reasons the script exits automagically
    # classified as good/unknown feature


    PIDS=`pidof apache2` || true
    
    PID=""
    
    # let's try to find the pid file
    # apache2 allows more than PidFile entry in the config but only
    # the last found in the config is used
    for PFILE in `grep ^PidFile /etc/apache2/* -r | awk '{print $2}'`; do
        if [ -e $PFILE ]; then
            cat $PFILE
            return 0
        fi
    done
    REALPID=0
    # if there is a pid we need to verify that belongs to apache2
    # for real
    for i in $PIDS; do
        if [ "$i" = "$PID" ]; then
            # in this case the pid stored in the
            # pidfile matches one of the pidof apache
            # so a simple kill will make it
            echo $PID
            return 0
        fi
    done
    return 1
}

apache_stop() {
        if `apache2 -t > /dev/null 2>&1`; then
                # if the config is ok than we just stop normaly
                $APACHE2 -k stop
        else
                # if we are here something is broken and we need to try
                # to exit as nice and clean as possible
                PID=$(pidof_apache)

                if [ "${PID}" ]; then
                        # in this case it is everything nice and dandy
                        # and we kill apache2
                        kill $PID
                elif [ "$(pidof apache2)" ]; then
                        if [ "$VERBOSE" != no ]; then
                                echo " ... failed!"
                                echo "You may still have some apache2 processes 
running.  There are"
                                echo "processes named 'apache2' which do not mat
ch your pid file,"
                                echo "and in the name of safety, we've left them
 alone.  Please review"
                                echo "the situation by hand."
                        fi
                        return 1
                fi
        fi
}

# Stupid hack to keep lintian happy. (Warrk! Stupidhack!).
case $1 in
        start)
                [ -f /etc/apache2/httpd.conf ] || touch /etc/apache2/httpd.conf
                [ -d /var/run/apache2 ] || mkdir -p /var/run/apache2
                [ -d /var/lock/apache2 ] || mkdir -p /var/lock/apache2
                chown www-data /var/lock/apache2
                #ssl_scache shouldn't be here if we're just starting up.
                [ -f /var/run/apache2/ssl_scache ] && rm -f /var/run/apache2/*ss
l_scache*
                log_begin_msg "Starting web server (apache2)..."
                if $APACHE2CTL start; then
                        log_end_msg 0
                else
                        log_end_msg 1
                fi
        ;;
        stop)
                log_begin_msg "Stopping web server (apache2)..."
                if apache_stop; then
                        log_end_msg 0
                else
                        log_end_msg 1
                fi
        ;;
        reload)
                if ! $APACHE2CTL configtest > /dev/null 2>&1; then
                    $APACHE2CTL configtest || true
                    log_end_msg 1
                    exit 1
                fi
                log_begin_msg "Reloading web server config..."
                if pidof_apache; then
                    if $APACHE2CTL graceful $2 ; then
                        log_end_msg 0
                    else
                        log_end_msg 1
                    fi
                fi
        ;;
        restart | force-reload)
                log_begin_msg "Forcing reload of web server (apache2)..."
                if ! apache_stop; then
                        log_end_msg 1
                fi
                sleep 10
                if $APACHE2CTL start; then
                        log_end_msg 0
                else
                        log_end_msg 1
                fi
        ;;
        *)
                log_success_msg "Usage: /etc/init.d/apache2 {start|stop|restart|
reload|force-reload}"
        ;;
esac

```

Thanks


B.R.
satimis

---

### Post by cdenley on 2008-06-18
Doesn't apache2 in feisty use the modular configuration?
```

sudo cat /etc/apache2/apache2.conf|grep Include|grep -v \#
sudo cat /etc/apache2/mods-enabled/*.conf|grep php5
sudo cat /etc/apache2/mods-enabled/*.load|grep php5

```
httpd.conf isn't used anymore.

---

### Post by satimis on 2008-06-18
> **cdenley said:**
> Doesn't apache2 in feisty use the modular configuration?
```

sudo cat /etc/apache2/apache2.conf|grep Include|grep -v \#
sudo cat /etc/apache2/mods-enabled/*.conf|grep php5
sudo cat /etc/apache2/mods-enabled/*.load|grep php5

```

$ sudo cat /etc/apache2/apache2.conf|grep ```
Include|grep -v \#
Password:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf
Include /etc/apache2/httpd.conf
Include /etc/apache2/ports.conf
Include /etc/apache2/conf.d/
Include /etc/apache2/sites-enabled/

```
$ sudo cat /etc/apache2/mods-enabled/*.conf|grep php5```

<IfModule mod_php5.c>

```


$ sudo cat /etc/apache2/mods-enabled/*.load|grep php5```

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
```


> 
httpd.conf isn't used anymore.
Noted with thanks


B.R.
satimis

---

### Post by cdenley on 2008-06-18
Do you see from the output you posted how it works? Just clear httpd.conf, and it should be fine. If apache2 module packages are installed, they should have their configuration files in /etc/apache2/mods-available. When they are enabled with the a2enmod command, links to them are created in /etc/apache2/mods-enabled. The apache2.conf file "includes" everything in that directory. The vhost/site configuration works the same (a2ensite/a2dissite).

---

### Post by satimis on 2008-06-18
> **cdenley said:**
> Do you see from the output you posted how it works? Just clear httpd.conf, and it should be fine.

Hi cdenley,


Thanks for your advice.


$ sudo nano /etc/apache2/httpd.conf
comment out the line```

LoadModule php5_module modules/libphp5.so

```

$ sudo /etc/init.d/apache2 restart```

 * Forcing reload of web server (apache2)...                             [ OK ] 

```

Problem gone now.  Thanks.


> 
 If apache2 module packages are installed, they should have their configuration files in /etc/apache2/mods-available. 

$ apt-cache pkgnames libapache2```

libapache2-mod-ldap-userdir
libapache2-mod-speedycgi
libapache2-redirtoservername
libapache2-mod-musicindex
libapache2-mod-chroot
libapache2-mod-ngobjweb
libapache2-mod-annodex
libapache2-mod-auth-sys-group
libapache2-webkdc
libapache2-mod-auth-pgsql
libapache2-mod-mono
libapache2-mod-auth-plain
libapache2-webauth
libapache2-mod-encoding
libapache2-mod-apreq2
libapache2-mod-php4
libapache2-mod-php5
libapache2-mod-python-doc
libapache2-mod-macro
libapache2-mod-auth-mysql
libapache2-mod-auth-pam
libapache2-mod-cband
libapache2-mod-fcgid
libapache2-mod-scgi
libapache2-mod-suphp
libapache2-mod-shib
libapache2-mod-rpaf
libapache2-mod-ifier
libapache2-mod-python
libapache2-mod-python2.2
libapache2-mod-python2.3
libapache2-mod-python2.4
libapache2-mod-python2.5
libapache2-mod-vhost-ldap
libapache2-mod-bt
libapache2-modxslt
libapache2-mod-jk
libapache2-mod-mime-xattr
libapache2-mod-ruby
libapache2-svn
libapache2-mod-perl2
libapache2-mod-dnssd
libapache2-mod-removeip
libapache2-modbt-perl
libapache2-mod-xmlrpc2
libapache2-request-perl
libapache2-mod-fastcgi
libapache2-redirtoservname
libapache2-mod-layout
libapache2-mod-perl2-dev
libapache2-mod-vhost-hash-alias
libapache2-mod-perl2-doc
libapache2-mod-bt-dev
libapache2-mod-auth-kerb
libapache2-mod-proxy-html
libapache2-mod-jk2
libapache2-mod-geoip

```


$ dpkg --print-avail libapche2-mod-*```

Package `libapche2-mod-*' is not available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
```

$ dpkg --print-avail libapche2-mod-```

Package `libapche2-mod-' is not available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

```
Which command can be used to find the apache2 modules installed on the box collectively?


> 
When they are enabled with the a2enmod command, links to them are created in /etc/apache2/mods-enabled. The apache2.conf file "includes" everything in that directory. The vhost/site configuration works the same (a2ensite/a2dissite).
Could you please explain it in more detail?


TIA


B.R.
satimis

---

### Post by cdenley on 2008-06-18
An easy way to see all apache2 modules installed (enabled or not)...
```

a2enmod

```
This lists all modules, including the ones from apache2.2-common. You could also do
```

ls /etc/apache2/mods-available/*.load|cut -d / -f 5|cut -d . -f 1

```

The file httpd.conf is replaced with apache2.conf. These two lines from your apache2.conf file read all *.conf and *.load files in your mods-enabled directory, and includes the lines from all those files as if they are in your apache2.conf.
```

Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

```

As you can see, for the php5 configuration in the mods-enabled (and any other modules), they are links to the configuration files in mods-available.
```

sudo ls -l /etc/apache2/mods-enabled/php5.*

```

If you want to disable the php5 modules, you would run this command
```

sudo a2dismod php5

```

Now, the links you saw before will be deleted. Since the "Include" statement above only includes configurations in mods-enabled, and php5's configuration is no longer in that directory, php5 will not be loaded.
```

sudo ls -l /etc/apache2/mods-enabled/php5.*

```

To enable it again, and see the links which got created again...
```

sudo a2enmod php5
sudo ls -l /etc/apache2/mods-enabled/php5.*

```

---

### Post by satimis on 2008-06-18
> **cdenley said:**
> An easy way to see all apache2 modules installed (enabled or not)...
```

a2enmod

```
This lists all modules, including the ones from apache2.2-common. 

$ sudo a2enmod```

Password:
Which module would you like to enable?
Your choices are: actions alias asis auth_basic auth_digest authn_alias authn_an
on authn_dbd authn_dbm authn_default authn_file authnz_ldap authz_dbm authz_defa
ult authz_groupfile authz_host authz_owner authz_user autoindex cache cern_meta 
cgid cgi charset_lite dav_fs dav dav_lock dav_svn dbd deflate dir disk_cache dum
p_io env expires ext_filter file_cache filter headers ident imagemap include inf
o ldap log_forensic mem_cache mime mime_magic negotiation php5 proxy_ajp proxy_b
alancer proxy_connect proxy_ftp proxy_http proxy rewrite setenvif speling ssl st
atus suexec unique_id userdir usertrack version vhost_alias
Module name? 


```
Are they all apache2 modules?  man found a2enmod for enable apache2 modules and a2dismod for disable its modules.


> 
You could also do
```

ls /etc/apache2/mods-available/*.load|cut -d / -f 5|cut -d . -f 1

```


$ sudo /etc/apache2/mods-available/*.load|cut -d / -f 5|cut -d . -f 1```

sudo: /etc/apache2/mods-available/actions.load: command not found

```


$ ls /etc/apache2/mods-available/ | grep load```

actions.load

```
It is there.


> 
The file httpd.conf is replaced with apache2.conf. These two lines from your apache2.conf file read all *.conf and *.load files in your mods-enabled directory, and includes the lines from all those files as if they are in your apache2.conf.
```

Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

```

As you can see, for the php5 configuration in the mods-enabled (and any other modules), they are links to the configuration files in mods-available.
```

sudo ls -l /etc/apache2/mods-enabled/php5.*

```

If you want to disable the php5 modules, you would run this command
```

sudo a2dismod php5

```

Now, the links you saw before will be deleted. Since the "Include" statement above only includes configurations in mods-enabled, and php5's configuration is no longer in that directory, php5 will not be loaded.
```

sudo ls -l /etc/apache2/mods-enabled/php5.*

```

To enable it again, and see the links which got created again...
```

sudo a2enmod php5
sudo ls -l /etc/apache2/mods-enabled/php5.*

```
To comment out or to delete the line```

LoadModule php5_module modules/libphp5.so

```
on /etc/apache2/httpd.conf, is it the correct way to solve my problem?  Whether there is another way?


Do I still need /etc/apache2/httpd.conf file?  To remove it Apache2 can't be started.


B.R.
satimis

---

### Post by cdenley on 2008-06-18
Yes, those are all apache2 modules.
[http://httpd.apache.org/docs/2.2/mod/](http://httpd.apache.org/docs/2.2/mod/)

> 
$ sudo /etc/apache2/mods-available/*.load|cut -d / -f 5|cut -d . -f 1

You typed that command wrong.
```

ls /etc/apache2/mods-available/*.load|cut -d / -f 5|cut -d . -f 1

```
It's just another command to list your apache2 modules.

You can delete the lines in httpd.conf or comment them out. It will probably work if you delete the file. The only reason the file is there is in case a script you run expects the old apache configuration type.

---

### Post by satimis on 2008-06-18
> **cdenley said:**
> Yes, those are all apache2 modules.
[http://httpd.apache.org/docs/2.2/mod/](http://httpd.apache.org/docs/2.2/mod/)

Thanks


> 
You typed that command wrong.
```

ls /etc/apache2/mods-available/*.load|cut -d / -f 5|cut -d . -f 1

```
It's just another command to list your apache2 modules.

Oh, sorry.


$ sudo ls /etc/apache2/mods-available/*.load | cut -d / -f 5|cut -d . -f 1 | grep apache2.2-common
No printout


$ sudo ls /etc/apache2/mods-available/*.load | cut -d / -f 5|cut -d . -f 1```

actions
alias
asis
auth_basic
auth_digest
authn_alias
authn_anon
authn_dbd
authn_dbm
authn_default
authn_file
authnz_ldap
authz_dbm
authz_default
authz_groupfile
authz_host
authz_owner
authz_user
autoindex
cache
cern_meta
cgid
cgi
charset_lite
dav_fs
dav
dav_lock
dav_svn
dbd
deflate
dir
disk_cache
dump_io
env
expires
ext_filter
file_cache
filter
headers
ident
imagemap
include
info
ldap
log_forensic
mem_cache
mime
mime_magic
negotiation
php5
proxy_ajp
proxy_balancer
proxy_connect
proxy_ftp
proxy_http
proxy
rewrite
setenvif
speling
ssl
status
suexec
unique_id
userdir
usertrack
version
vhost_alias

```


> 
You can delete the lines in httpd.conf or comment them out. It will probably work if you delete the file. The only reason the file is there is in case a script you run expects the old apache configuration type.
I tried before.  It did not work.  Apache2 can't start.


$ sudo mv /etc/apache2/httpd.conf /etc/apache2/httpd.conf.old
No complaint


$ sudo /etc/init.d/apache2 restart```

 * Forcing reload of web server (apache2)...                                                     
apache2: Syntax error on line 189 of /etc/apache2/apache2.conf: Could not open configuration file
 /etc/apache2/httpd.conf: No such file or directory
                                                                                          [fail]

```


$ cat /etc/apache2/httpd.conf```

Alias /mail /usr/local/squirrelmail/www
<Directory /usr/local/swuirrelmail/www>
Order allow,deny
Allow from all
</Directory>

## Location of the DavLock file
DavLockDB /usr/share/apache2/var/DavLock
       
## Set up the bookmarks directory to use WebDAV and authentication
<Directory "/var/www/bookmarks/">
        Dav On
        AuthName "WebDAV Login"
        AuthType Basic
        AuthUserFile /var/www/bookmarks/.htpasswd
        ## Limit access for enhanced security
        <LimitExcept GET HEAD OPTIONS POST>
                require valid-user
        </LimitExcept>
        Order allow,deny
        Allow from all
</Directory>

# Edit your httpd.conf to load the PHP module
#LoadModule php5_module modules/libphp5.so

```


$ cat /etc/apache2/apache2.conf```

### Section 1: Global Environment

LockFile /var/lock/apache2/accept.lock

PidFile /var/run/apache2.pid

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

User www-data
Group www-data

# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#

AccessFileName .htaccess

# The following lines prevent .htaccess and .htpasswd files from being 
# viewed by Web clients. 
#
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

TypesConfig /etc/mime.types


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

# Include generic snippets of statements
Include /etc/apache2/conf.d/

#
# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
#
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

# ServerTokens

ServerTokens Full

ServerSignature On

<IfModule alias_module>
    #
    # Aliases: Add here as many aliases as you need (with no limit). The format is 
    # Alias fakename realname

    Alias /icons/ "/usr/share/apache2/icons/"

    <Directory "/usr/share/apache2/icons">
        Options Indexes MultiViews
        AllowOverride None
        Order allow,deny
        Allow from all
    </Directory>

</IfModule>

#
# Directives controlling the display of server-generated directory listings.
#
<IfModule mod_autoindex.c>

    #
    # IndexOptions: Controls the appearance of server-generated directory
    # listings.
    #
    IndexOptions FancyIndexing VersionSort HTMLTable NameWidth=*

    #
    # AddIcon* directives tell the server which icon to show for different
    # files or filename extensions.  These are only displayed for
    # FancyIndexed directories.
    #
    AddIconByEncoding (CMP,/icons/compressed.gif) x-compress x-gzip

    AddIconByType (TXT,/icons/text.gif) text/*
    AddIconByType (IMG,/icons/image2.gif) image/*
    AddIconByType (SND,/icons/sound2.gif) audio/*
    AddIconByType (VID,/icons/movie.gif) video/*

    AddIcon /icons/binary.gif .bin .exe
    AddIcon /icons/binhex.gif .hqx
    AddIcon /icons/tar.gif .tar
    AddIcon /icons/world2.gif .wrl .wrl.gz .vrml .vrm .iv
    AddIcon /icons/compressed.gif .Z .z .tgz .gz .zip
    AddIcon /icons/a.gif .ps .ai .eps
    AddIcon /icons/layout.gif .html .shtml .htm .pdf
    AddIcon /icons/text.gif .txt
    AddIcon /icons/c.gif .c
    AddIcon /icons/p.gif .pl .py
    AddIcon /icons/f.gif .for
    AddIcon /icons/dvi.gif .dvi
    AddIcon /icons/uuencoded.gif .uu
    AddIcon /icons/script.gif .conf .sh .shar .csh .ksh .tcl
    AddIcon /icons/tex.gif .tex
    AddIcon /icons/bomb.gif core

    AddIcon /icons/back.gif ..
    AddIcon /icons/hand.right.gif README
    AddIcon /icons/folder.gif ^^DIRECTORY^^
    AddIcon /icons/blank.gif ^^BLANKICON^^

    #
    # DefaultIcon is which icon to show for files which do not have an icon
    # explicitly set.
    #
    DefaultIcon /icons/unknown.gif

    #
    # AddDescription allows you to place a short description after a file in
    # server-generated indexes.  These are only displayed for FancyIndexed
    # directories.
    # Format: AddDescription "description" filename
    #
    #AddDescription "GZIP compressed document" .gz
    #AddDescription "tar archive" .tar
    #AddDescription "GZIP compressed tar archive" .tgz

    #
    # ReadmeName is the name of the README file the server will look for by
    # default, and append to directory listings.
    #
    # HeaderName is the name of a file which should be prepended to
    # directory indexes. 
    ReadmeName README.html
    HeaderName HEADER.html

    #
    # IndexIgnore is a set of filenames which directory indexing should ignore
    # and not include in the listing.  Shell-style wildcarding is permitted.
    #
    IndexIgnore .??* *~ *# RCS CVS *,v *,t 
</IfModule>

<IfModule mod_mime.c>

    #AddType application/x-gzip .tgz
    #
    AddType application/x-compress .Z
    AddType application/x-gzip .gz .tgz

    #
    # DefaultLanguage and AddLanguage allows you to specify the language of 
    # a document. You can then use content negotiation to give a browser a 

    AddLanguage ca .ca
    AddLanguage cs .cz .cs
    AddLanguage da .dk
    AddLanguage de .de
    AddLanguage el .el
    AddLanguage en .en
    AddLanguage eo .eo
    AddLanguage es .es
    AddLanguage et .et
    AddLanguage fr .fr
    AddLanguage he .he
    AddLanguage hr .hr
    AddLanguage it .it
    AddLanguage ja .ja
    AddLanguage ko .ko
    AddLanguage ltz .ltz
    AddLanguage nl .nl
    AddLanguage nn .nn
    AddLanguage no .no
    AddLanguage pl .po
    AddLanguage pt .pt
    AddLanguage pt-BR .pt-br
    AddLanguage ru .ru
    AddLanguage sv .sv
    AddLanguage zh-CN .zh-cn
    AddLanguage zh-TW .zh-tw
</IfModule>

<IfModule mod_negotiation.c>
    #
    # LanguagePriority allows you to give precedence to some languages
    # in case of a tie during content negotiation.

    LanguagePriority en ca cs da de el eo es et fr he hr it ja ko ltz nl nn no pl pt pt-BR ru sv zh-CN zh-TW

    #
    # ForceLanguagePriority allows you to serve a result page rather than
    # MULTIPLE CHOICES (Prefer) [in case of a tie] or NOT ACCEPTABLE (Fallback)
    # [in case no accepted languages matched the available variants]
    #
    ForceLanguagePriority Prefer Fallback

</IfModule>

<IfModule mod_mime.c>

    AddCharset us-ascii    .ascii .us-ascii
    AddCharset ISO-8859-1  .iso8859-1  .latin1
    AddCharset ISO-8859-2  .iso8859-2  .latin2 .cen
    AddCharset ISO-8859-3  .iso8859-3  .latin3
    AddCharset ISO-8859-4  .iso8859-4  .latin4
    AddCharset ISO-8859-5  .iso8859-5  .cyr .iso-ru
    AddCharset ISO-8859-6  .iso8859-6  .arb .arabic
    AddCharset ISO-8859-7  .iso8859-7  .grk .greek
    AddCharset ISO-8859-8  .iso8859-8  .heb .hebrew
    AddCharset ISO-8859-9  .iso8859-9  .latin5 .trk
    AddCharset ISO-8859-10  .iso8859-10  .latin6
    AddCharset ISO-8859-13  .iso8859-13
    AddCharset ISO-8859-14  .iso8859-14  .latin8
    AddCharset ISO-8859-15  .iso8859-15  .latin9
    AddCharset ISO-8859-16  .iso8859-16  .latin10
    AddCharset ISO-2022-JP .iso2022-jp .jis
    AddCharset ISO-2022-KR .iso2022-kr .kis
    AddCharset ISO-2022-CN .iso2022-cn .cis
    AddCharset Big5        .Big5       .big5 .b5
    AddCharset cn-Big5     .cn-big5
    # For russian, more than one charset is used (depends on client, mostly):
    AddCharset WINDOWS-1251 .cp-1251   .win-1251
    AddCharset CP866       .cp866
    AddCharset KOI8      .koi8
    AddCharset KOI8-E      .koi8-e
    AddCharset KOI8-r      .koi8-r .koi8-ru
    AddCharset KOI8-U      .koi8-u
    AddCharset KOI8-ru     .koi8-uk .ua
    AddCharset ISO-10646-UCS-2 .ucs2
    AddCharset ISO-10646-UCS-4 .ucs4
    AddCharset UTF-7       .utf7
    AddCharset UTF-8       .utf8
    AddCharset UTF-16      .utf16
    AddCharset UTF-16BE    .utf16be
    AddCharset UTF-16LE    .utf16le
    AddCharset UTF-32      .utf32
    AddCharset UTF-32BE    .utf32be
    AddCharset UTF-32LE    .utf32le
    AddCharset euc-cn      .euc-cn
    AddCharset euc-gb      .euc-gb
    AddCharset euc-jp      .euc-jp
    AddCharset euc-kr      .euc-kr
    #Not sure how euc-tw got in - IANA doesn't list it???
    AddCharset EUC-TW      .euc-tw
    AddCharset gb2312      .gb2312 .gb
    AddCharset iso-10646-ucs-2 .ucs-2 .iso-10646-ucs-2
    AddCharset iso-10646-ucs-4 .ucs-4 .iso-10646-ucs-4
    AddCharset shift_jis   .shift_jis .sjis

    # For type maps (negotiated resources):
    # (This is enabled by default to allow the Apache "It Worked" page
    #  to be distributed in multiple languages.)
    #
    AddHandler type-map var

    # To parse .shtml files for server-side includes (SSI):
    # (You will also need to add "Includes" to the "Options" directive.)
    #
    AddType text/html .shtml
    AddOutputFilter INCLUDES .shtml
</IfModule>


<IfModule mod_setenvif.c>
    #
    # The following directives modify normal HTTP response behavior to
    # handle known problems with browser implementations.
    #
    BrowserMatch "Mozilla/2" nokeepalive
    BrowserMatch "MSIE 4\.0b2;" nokeepalive downgrade-1.0 force-response-1.0
    BrowserMatch "RealPlayer 4\.0" force-response-1.0
    BrowserMatch "Java/1\.0" force-response-1.0
    BrowserMatch "JDK/1\.0" force-response-1.0

    #
    # The following directive disables redirects on non-GET requests for
    # a directory that does not include the trailing slash.  This fixes a 
    # problem with Microsoft WebFolders which does not appropriately handle 
    # redirects for folders with DAV methods.
    # Same deal with Apple's DAV filesystem and Gnome VFS support for DAV.
    #
    BrowserMatch "Microsoft Data Access Internet Publishing Provider" redirect-carefully
    BrowserMatch "MS FrontPage" redirect-carefully
    BrowserMatch "^WebDrive" redirect-carefully
    BrowserMatch "^WebDAVFS/1.[012]" redirect-carefully
    BrowserMatch "^gnome-vfs/1.0" redirect-carefully
    BrowserMatch "^XML Spy" redirect-carefully
    BrowserMatch "^Dreamweaver-WebDAV-SCM1" redirect-carefully
</IfModule>

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

```


satimis

---

