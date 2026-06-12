---
title: "Apache2 server on Ubuntu Server 10.10 Hacked!"
date: 2011-03-13
forum: Server Platforms
---

### Post by mixboy7 on 2011-03-13
Hi!
Yesterday, i installed ubuntu server 10.10 on an old IBM PC of mine. I set it up with an OpenSSH server for easy remote acces (with Public key Authentication ONLY!) . I also downloaded and installed apache2, making no changes to the configuration files whatsoever.

It was up for about a day and then, suddenly, at about 17.00 today, my website got REPLACED!

Instead of seeing the usual "It works!" default index.html, it had been replaced by a completely different webpage (a google replica).

Looking at the logs, i can see that four different external IPs have browsed my website , they' ve all made extremely weird URL requests,  e.g(copied from acces.log):

```

192.168.1.1 - - [13/Mar/2011:17:01:19 +0100] "GET /extern_js/f/CgJzdhICc2UgACswCjhBQB0sKzAOOAosKzAYOAQsKzAlOMmIASwrMCY4CCwrMCc4AiwrMEU4ACw/9XzpfbfYwig.js HTTP/1.1" 404 578 "http://facemash.hopto.org/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.15) Gecko/20110303 Ubuntu/9.10 (karmic) Firefox/3.6.15"

```I fail to see how someone could have been able to modify my web site since there's no possibility to interact with it (e.g no scripts in cgi-bin or any input forms). The only port that is open in my external firewall is port 80.

I've never seen this before, Apache getting hacked "out of the box", i mean, WTF?

Anyway, i've attached the log files and the modified index.html, (delete the .txt
extension.)

Regards,
Axel Z

[ATTACH]185955[/ATTACH]

[ATTACH]185956[/ATTACH]

[ATTACH]185957[/ATTACH]

---

### Post by samosamo on 2011-03-13
What version of Apache?  Do you have the "security" repo's enabled in your sources.list?  Are you sure you're telling us everything?

---

### Post by rubylaser on 2011-03-13
What are the permissions on /var/www and index.html? I assume you didn't change the path that Apache is serving from.

```
ls -la /var/ | grep www
```
```
ls -la /var/www/index.html
```
And paste in your /etc/apache2/apache2.conf file as well.

---

### Post by mixboy7 on 2011-03-13
@samosao: i set it up  to automatically download security updates, i also manually downloaded all updates from the "security" category in aptitude.

The permissions are set to:
 /var/www                       drwxr-xr-x   owner: axel
/var/www/index.html       -rw-r--r--     owner: axel

i didn't touch the configuration files at all, and judging from their timestamps no one else has either, but here they are (i also included the default site configuration file):

<b>apache2.conf</b>
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
# with "/", the value of ServerRoot is prepended -- so "foo.log"
# with ServerRoot set to "/etc/apache2" will be interpreted by the
# server as "/etc/apache2/foo.log".
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
# at <URL:http://httpd.apache.org/docs/2.2/mod/mpm_common.html#lockfile>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
#ServerRoot "/etc/apache2"

#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
LockFile ${APACHE_LOCK_DIR}/accept.lock

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
# ThreadLimit: ThreadsPerChild can be changed to this maximum value during a
#              graceful restart. ThreadLimit can only be changed by stopping
#              and starting Apache.
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
    Satisfy all
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
ErrorLog ${APACHE_LOG_DIR}/error.log

#
# LogLevel: Control the number of messages logged to the error_log.
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
#
LogLevel warn

# Include module configuration:
Include mods-enabled/*.load
Include mods-enabled/*.conf

# Include all the user configurations:
Include httpd.conf

# Include ports listing
Include ports.conf

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

# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include conf.d/

# Include the virtual host configurations:
Include sites-enabled/

```

<b>default:</b>
```

<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /var/www
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/>
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

```

do you think that i need to format the hard-drive and start all over again, just to be sure? how do i know if the damage is limited to DocumentRoot, or has the whole system been compromised?

//Axel Z

//
Axel Z

---

### Post by rubylaser on 2011-03-13
You don't know that for certain.  It's always a good practice to restore from backup in the case of a compromise.  What is the Group owner, and does that user have a password?  You might want to enable mod_security, and implement fail2ban.

---

### Post by wongo888 on 2011-03-13
If they are writing random stuff to your filesystem then wiping the drive and starting again is probably a good idea.

Check your other logs as they could have gotten in via another system vulnerability and just loaded stuff into your web root. They also might have wiped the logs.

---

### Post by SeijiSensei on 2011-03-14
If you reinstall, do not change the permissions on /var/www.  Figure out how to deal with the restricted permissions instead.  (Putting yourself in the www-data group is a good start.)  The www-data can write to only a very few directories on the machine for security reasons.

---

### Post by mixboy7 on 2011-03-14
i just set up the server and let it run "out of the box", although i did use vim (sudo vim) to change the title of my web page. But by changing my user group to www-data, how will that stop someone from editing my web page, since i assume that www is one of the few folders that this group has access to?

I doubt that this was a directed attack towards my website only, because i created it less than 24hrs prior to being hijacked, and since it is on "default settings", how come no-one else is getting their websites replaced?

One could think that SSH has something to do with it, but i specifically disabled password authentication, and it only accepts connections from the LAN, so i don't see how someone could have gotten in that way, but there is one thing that i noticed though: the attack ocurred at about the same time that i tried uploading my real website from my laptop (which was on the LAN and has a public key) to the server. This might be a coincidence, or not. how can i find the sshd-logs?

---

### Post by Sporkman on 2011-03-14
> **mixboy7 said:**
> how can i find the sshd-logs?

/var/log/auth.log

---

### Post by mixboy7 on 2011-03-14
I found nothing suspicious in auth.log, or in any other logs for that matter, about any traffic or changes that i couldn't recall making myself. i also changed my user group to www-data
So whats the next step, to prevent it from happening again?

---

### Post by SeijiSensei on 2011-03-14
> The permissions are set to:
/var/www drwxr-xr-x owner: axel
/var/www/index.html -rw-r--r-- owner: axel

That's not a default configuration.  /var/www is owned by user www-data and group www-data.  You, or someone else, changed the permissions on /var/www so user axel can write files there.

Does user axel have sudo permissions?  If so, one scenario is that someone obtained the login credentials for axel, logged in as that user, used sudo, and made some changes to the file system.

---

### Post by mixboy7 on 2011-03-15
during the initial ubuntu setup, i only created one user named axel, so if i take away that user's sudo permission, how can i manage to administrate my server if nobody has sudo permissions?

---

### Post by SeijiSensei on 2011-03-15
Reread my post.  I said that user axel appears to own /var/www which is contrary to the default configuration.  I also suggested that perhaps someone stole axel's credentials and exploited sudo.  I didn't suggest you shouldn't have a user with sudo rights.  I'm more concerned that someone may have obtained your password.  And was it you who changed the ownership on /var/www?  If you don't recall doing that, then it gives more credence to my theory that your credentials were stolen.

Do you ever transmit your password in clear-text like with telnet?  Do you get mail from remote servers?  Are you using secure protocols like TLS and IMAPS when you log into those servers?  How about a wifi router with weak security like WEP?  Anyone else know about this machine?  I'd start thinking about how someone could pretend to be you.

I'm going to be charitable and assume you had a strong password, one that includes a mix of upper- and lower-case characters, numbers, and a special character or two.  Weak passwords can be broken by brute-force methods.

---

### Post by mixboy7 on 2011-03-15
i wiped the hard-drive this afternoon and reinstalled ubuntu. i installed apache2 and set up OpenSSH with public key auth, i also backed up everything to an external hard-drive.

SeijiSensei:
> 
  Figure out how to deal with the restricted permissions instead.   (Putting yourself in the www-data group is a good start.)  The www-data  can write to only a very few directories on the machine for security  reasons. 	


do you mean that i should change my primary group to www-data, or just add the group to my secondary groups?

BTW /var/www is owned by user root, is that ok?

---

### Post by wongo888 on 2011-03-15
What is the purpose of this server and how valuable is it to you? If it is just a hobby box then, as long as you are sure that you're not misconfiguring sshd, just keep it patched and use the firewall.

If this is a business box full of confidential health info or you stand to lose clients, then maybe an IDS system makes sense.

[http://en.wikipedia.org/wiki/Intrusion_detection_system](http://en.wikipedia.org/wiki/Intrusion_detection_system)

[http://www.dasient.com/](http://www.dasient.com/)

Security is a process, not a product...the true cost of something is what you give up to get it...etc...etc...

---

### Post by mixboy7 on 2011-03-16
it's a just for fun hobby server, it should be fine now that the permissions are all right. anyways i've got a backup now, so it's all good.

thank you for all your support guys!:D:D

---

