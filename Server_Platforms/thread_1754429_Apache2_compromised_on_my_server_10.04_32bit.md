---
title: "Apache2 compromised on my server 10.04 32bit"
date: 2011-05-10
forum: Server Platforms
---

### Post by clmbngbkng on 2011-05-10
I seem to have problems with my Ubuntu installation when it comes to Apache2. Up until last week everything seemed to be fine and then my internet usage went through the roof, barely letting anything in and out of our LAN.

I have tracked down the problem, or part of the problem, to be me not configuring mod_proxy in Apache2 to not allow requests. I have turned that off and the network usage has dropped dramatically.

My problem now is that I'm wondering if there was something done to my system that causes Apache to still try to run out to the web. Now that proxy requests are turned off it seems that it can only do half of what it was modified to do. (I notice all of this by the network usage when Apache is started and stopped on the system.)

I'll be attaching some of the logs and if I didn't explain anything well please ask me to elaborate.
Thanks!

Access Log
```
117.41.186.191 - - [09/May/2011:23:56:41 -0700] "GET http://media.fastclick.net/w/get.media?sid=56236&tp=5&d=j&t=n HTTP/1.0" 404 535 "http://www.gvvu.com" "Mozilla/4.0 (compatible; MSIE 5.5; Windows 95)"
61.147.99.90 - - [09/May/2011:23:56:41 -0700] "GET http://ad2games.com/slave.php?w=13635_917923057 HTTP/1.0" 404 526 "http://www.nqnp.com" "Mozilla/4.0 (compatible; MSIE 5.0; Windows 98; DigExt)"
60.173.11.71 - - [09/May/2011:23:56:41 -0700] "GET http://ad.yieldads.com/st?ad_type=iframe&ad_size=300x250&section=1870386 HTTP/1.0" 404 522 "http://pagamepa.com/?m=201104" "Mozilla/4.0 (compatible; MSIE 5.01; Windows 98; Alexa Toolbar)"
117.41.186.149 - - [09/May/2011:23:56:42 -0700] "GET http://ad.reduxmedia.com/st?ad_type=iframe&ad_size=728x90&section=1531638 HTTP/1.0" 404 524 "http://www.sukpatch.com" "Mozilla/4.0 (compatible; MSIE 5.01; Windows 98; Alexa Toolbar)"
92.101.136.61.ha.cnc - - [09/May/2011:23:56:48 -0700] "GET http://ad.yieldads.com/st?ad_type=iframe&ad_size=728x90&section=1708675 HTTP/1.0" 404 522 "http://www.allreaders.com/" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.7) Gecko/20040626 Firefox/0.9.1"
117.41.186.217 - - [09/May/2011:23:56:43 -0700] "GET http://ad.xtendmedia.com/st?ad_type=iframe&ad_size=728x90&section=1517156 HTTP/1.0" 404 524 "http://www.xejv.com" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.6) Gecko/20040206 Firefox/0.8"
117.41.186.217 - - [09/May/2011:23:56:43 -0700] "GET http://ad.reduxmedia.com/st?ad_type=iframe&ad_size=300x250&section=1562838 HTTP/1.0" 404 524 "http://www.fifig.com" "Mozilla/4.0 (compatible; MSIE 5.0; Windows 98; DigExt)"
9.204.154.61.board.xm.fj.dynamic.163data.com.cn - - [09/May/2011:23:56:49 -0700] "GET http://www.advertise.com/cgi-bin/search/mxml.fcgi?Terms=marlboro+cigarettes&affiliate=WIGGLYTE&subid=WIGGLYTE&ip=75%2E25%2E158%2E41&Hits_Per_Page=10&ua=Mozilla/4.0%20(compatible;%20MSIE%205.5;%20Windows%2095)&serveurl=http%3A%2F%2Fwww.teamwiggly.com HTTP/1.0" 404 546 "-" "Mozilla/4.0 (compatible; MSIE 5.5; Windows 95)"
117.41.186.149 - - [09/May/2011:23:56:44 -0700] "GET http://ad.xtendmedia.com/st?ad_type=iframe&ad_size=728x90&section=1517156 HTTP/1.0" 404 524 "http://www.xejv.com" "Mozilla/4.0 (compatible; MSIE 6.01; Windows 98; Alexa Toolbar)"
61.147.99.98 - - [09/May/2011:23:56:44 -0700] "GET http://ad.bharatstudent.com/st?ad_type=iframe&ad_size=728x90&section=722163 HTTP/1.0" 404 527 "http://www.gameairport.com" "Mozilla/4.76 [en] (Win98; U)"
61.147.99.90 - - [09/May/2011:23:56:44 -0700] "GET http://ad2games.com/slave.php?w=13629_1991568780 HTTP/1.0" 404 526 "http://www.siika.com" "Mozilla/4.0 (compatible; MSIE 5.5; Windows NT 4.0)"
114.244.69.143 - - [09/May/2011:23:56:46 -0700] "GET http://network.realmedia.com/RealMedia/ads/adstream_jx.ads/gamezone2/ros/728x90/jx/ss/a/1807349596@Top1 HTTP/1.0" 404 562 "http://www.gamezone.com/" "mozilla/5.0 (windows; u; windows nt 5.1; fr; rv:1.8.0.7) gecko/20060909 firefox/1.5.0.7"
hn.kd.ny.adsl - - [09/May/2011:23:56:51 -0700] "GET http://ad.yieldads.com/st?ad_type=iframe&ad_size=300x250&section=1618147 HTTP/1.0" 404 522 "http://www.airfares.com.sg" "Mozilla/4.08 [en] (WinNT; U)"
61.147.112.243 - - [09/May/2011:23:56:46 -0700] "GET http://ad.bharatstudent.com/st?ad_type=iframe&ad_size=728x90&section=667239 HTTP/1.0" 404 527 "http://www.physicalbenefits.com" "Mozilla/4.0 (compatible; MSIE 5.5; AOL 6.0; Windows 98; Win 9x 4.90)"
117.41.186.137 - - [09/May/2011:23:56:47 -0700] "GET http://ad.xtendmedia.com/st?ad_type=iframe&ad_size=728x90&section=1764024 HTTP/1.0" 404 524 "http://www.iyens.com" "Mozilla/4.0 (compatible; MSIE 5.5; Windows 95; Alexa Toolbar)"
117.41.186.191 - - [09/May/2011:23:56:47 -0700] "GET http://ad.reduxmedia.com/st?ad_type=iframe&ad_size=728x90&section=1531638 HTTP/1.0" 404 524 "http://www.sukpatch.com" "Mozilla/3.0 WebTV/1.2 (compatible; MSIE 2.0)"
114.244.35.152 - - [09/May/2011:23:56:52 -0700] "GET http://network.realmedia.com/RealMedia/ads/adstream_jx.ads/gamezone2/ros/728x90/jx/ss/a/1315073438@Top1 HTTP/1.1" 404 499 "http://www.gamezone.com/" "mozilla/4.0 (compatible; msie 6.0; windows nt 5.1; sv1; tencenttraveler )"
61.147.112.243 - - [09/May/2011:23:56:48 -0700] "GET http://ads.smowtion.com/ad.js HTTP/1.0" 404 526 "http://www.nzuy.com" "Mozilla/4.0 (compatible; MSIE 5.5; Windows NT 5.0; Alexa Toolbar)"
```


Error Log 
```
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Mon May 09 23:46:56 2011] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.9 with Suhosin-Patch configured -- resuming normal operations
[Mon May 09 23:46:57 2011] [error] [client 61.147.99.98] File does not exist: /var/www/w, referer: http://www.gvvu.com
[Mon May 09 23:46:57 2011] [error] [client 61.147.99.98] File does not exist: /var/www/addyn, referer: http://www.abundancegames.com
[Mon May 09 23:46:57 2011] [error] [client 61.147.99.98] File does not exist: /var/www/st, referer: http://www.adagiogame.com
[Mon May 09 23:46:58 2011] [error] [client 117.41.186.217] File does not exist: /var/www/st, referer: http://www.xejv.com
[Mon May 09 23:46:58 2011] [error] [client 114.244.69.143] File does not exist: /var/www/RealMedia, referer: http://www.gamezone.com/
[Mon May 09 23:46:58 2011] [error] [client 61.147.112.243] File does not exist: /var/www/st, referer: http://www.physicalbenefits.com
[Mon May 09 23:46:59 2011] [error] [client 61.147.99.102] File does not exist: /var/www/w, referer: http://www.gvvu.com
[Mon May 09 23:46:59 2011] [error] [client 117.41.186.191] File does not exist: /var/www/st, referer: http://www.fcreview.com
[Mon May 09 23:46:59 2011] [error] [client 114.244.34.236] File does not exist: /var/www/RealMedia, referer: http://www.firerescue1.com/
[Mon May 09 23:46:59 2011] [error] [client 114.246.109.156] File does not exist: /var/www/RealMedia, referer: http://www.gamezone.com/
[Mon May 09 23:47:00 2011] [error] [client 61.147.112.243] File does not exist: /var/www/st, referer: http://www.nzuy.com
[Mon May 09 23:47:01 2011] [error] [client 122.228.236.202] File does not exist: /var/www/st, referer: http://www.bollywoodhott.com/celebrities/shahid-kapoor-the-latest-perfectionist-in-bollywood/
[Mon May 09 23:47:01 2011] [error] [client 222.186.44.23] script not found or unable to stat: /usr/lib/cgi-bin/search
[Mon May 09 23:47:02 2011] [error] [client 117.41.186.149] File does not exist: /var/www/w, referer: http://www.gvvu.com
```

---

### Post by satanselbow on 2011-05-10
Looks like you've managed to create an IP clash, certainly has attacted the ad farms - which is pretty impressive :popcorn:

It looks like there are sites attempting to access your server to deliver advertising content? or ad tracking of some description. The files are obviously not on your server - hence all the 404 errors :(

Do you use some sort of ad blocking in your hosts file? Without having more detail about how you have your particular server / virtual hosts / external address (dynamic dns service?) etc are setup we can't help much further ;)

---

### Post by clmbngbkng on 2011-05-10
Hehe this is not something I am proud of. As of now I have nothing but the standard stuff in my current default host file. I do have one subdomain that uses the proxy pass to get to my MythTV box.

Would you like me to paste them here?

---

### Post by satanselbow on 2011-05-10
Yeah conf files would be good ;)

You must have a catchall or wildcard set up somehwere that is attracting the flies. Anything that does not point to a specific domain or has unlimited scope is a likely suspect. If you have a proxy in your setup you will need to look at the permissions there as well ;)

---

### Post by clmbngbkng on 2011-05-10
Apache2.conf
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
HostnameLookups On

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
```

Default site
```
#NameVirtualHost *:80
<VirtualHost *:80>
	ServerName theclaussens.net
	ServerAlias www.theclaussens.net
	ServerAdmin webmaster@theclaussens.net
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options -Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		Allow from all
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

#    Alias /doc/ "/usr/share/doc/"
#    <Directory "/usr/share/doc/">
#        Options Indexes MultiViews FollowSymLinks
#        AllowOverride None
#        Order deny,allow
#        Deny from all
#        Allow from 127.0.0.0/255.0.0.0 ::1/128
#    </Directory>

#    Alias /Microsoft-Server-ActiveSync /var/www/z-push/index.php 

</VirtualHost>
```

Proxy.conf
```
<IfModule mod_proxy.c>
        #turning ProxyRequests on and allowing proxying from all may allow
        #spammers to use your proxy to send email.

        ProxyRequests Off

#        <Proxy *>
#                AddDefaultCharset off
#                Order deny,allow
#                Allow from all
#		#Deny from all
#                #Allow from 192.168.1
#        </Proxy>

<Proxy *>
Order Deny,Allow
Deny from all
Allow from 192.168.1
</Proxy> 

        # Enable/disable the handling of HTTP/1.1 "Via:" headers.
        # ("Full" adds the server version; "Block" removes all outgoing Via: headers)
        # Set to one of: Off | On | Full | Block

        ProxyVia On
</IfModule>
```


I do have a wildcard in my bind9 settings but that is only in place for Wordpress to do its multi-site thing. I can post that as well if need be.
Thanks!


EDIT: Even with mod_proxy turned off all night my logs still grew with them trying to abuse my setup. Similar stuff is showing up in error.log and access.log.

---

### Post by clmbngbkng on 2011-05-11
Bump! Any suggestions?

---

### Post by SeijiSensei on 2011-05-12
I don't see why you think changing your configuration will somehow stop automated processes from attacking your site.  From the access.log it looks like these are all getting 404 replies, so nothing is being transferred in response to these requests.  Perhaps they'll die off over time, but for now it's just something you'll need to live with.

---

### Post by stmiller on 2011-05-12
Welcome to web hosting. :)

All web servers are constantly poked, scanned, and such. Just keep up with security updates, don't run any sketchy code, and keep an eye on your logs.

---

### Post by clmbngbkng on 2011-05-13
@SeijiSensei: Yes you are right that there is nothing I can configure on my end to prevent them from contacting my server. I'm just wondering if it is from my end. Explained more below.

One thing I was wondering about is, do you think they put any script on my server? I haven't seen anything other than how they were taking advantage of my open proxy. I just find it odd that my network usage goes up when I turn apache2 on and it drops when it is off. I would expect the "spammers" to try to still be contacting the server even with apache off and they just wouldn't get a response. 

Any suggestions on how to check for that? Or am I just being paranoid? I'm just trying to learn how to handle stuff like this in the future.


Thank you for the continued help!

---

### Post by clmbngbkng on 2011-05-15
Bump one more time.

---

### Post by SeijiSensei on 2011-05-15
> **clmbngbkng said:**
> I just find it odd that my network usage goes up when I turn apache2 on and it drops when it is off.

Well, Apache does have to deal with all those requests when it's running, so network traffic is bound to increase.  When you say your network usage goes up, by how much?  Are you suddenly seeing megabytes of traffic suddenly moving over your connection, or just a small increase?

---

### Post by clmbngbkng on 2011-05-15
It only goes up a little bit from 10kbps to about 70 kbps at most while averaging about 40 kbps.

EDIT: After disconnecting the internet the wan port on the router I did see the usage drop to nothing which leads me to believe that the traffic in and out was all from responses to the server and not a file on the server itself.

I have also attached some of the PNGs from webalizer which show that the usage has been dropping.

---

