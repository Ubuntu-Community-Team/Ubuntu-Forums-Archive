---
title: "Apache Virtual Host help needed"
date: 2008-08-14
forum: Server Platforms
---

### Post by andyd34 on 2008-08-14
I have set up apache2 on my server and added a couple of sites. When I type the URL [http://192.168.1.100](http://192.168.1.100) (My Server IP) I get the default site but how do I test the other sites. I have tried [http://192.168.1.100/site2](http://192.168.1.100/site2) [http://192.168.1.100/~site2](http://192.168.1.100/~site2) but am getting a dead link. Can someone please help

---

### Post by skunkbad on 2008-08-15
this helped me:

[http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/]("http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/")

---

### Post by windependence on 2008-08-15
Are you using IP based virtual hosts or name based virtual hosts?

-Tim

---

### Post by y@w on 2008-08-15
You'll need to setup name-based hosts in Apache. I'd recommend [Webmin]("http://webmin.com") as an easy way to administer the sites :)

---

### Post by andyd34 on 2008-08-16
Thanks for all your replies, I have now installed webmin but all its done is add to my confusion. 

Here is what I have done and what I have.

Installed & Configured Lamp-Server (with help from google)
Installed & Configured Bind9 (with help from google)

Created 2 sites and enabled them 
Restarted Apache

**file:/etc/apache2/sites-available/site1**
> 
NameVirtualHost *

    <VirtualHost *>
    ServerName [www.site1.co.uk](www.site1.co.uk)
    DocumentRoot /home/site1/htdocs/www/
    </VirtualHost>


**file:/etc/apache2/sites-available/site2**
> 
    <VirtualHost *>
    ServerName [www.site2.co.uk](www.site2.co.uk)
    DocumentRoot /home/site2/htdocs/www/
    </VirtualHost>


These sites are showing in
**/etc/apache2/sites-enabled**

Bind9
**file: /etc/bind/named.conf.local**
> 
zone "site1.co.uk" {
type master;
file "/etc/bind/zones/site1.co.uk.db";
};

zone "1.168.192.in-addr.arpa" {
type master;
file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";
};


**file: /etc/bind/named.conf.options**
> 
options {
	directory "/var/cache/bind";

	// If there is a firewall between you and nameservers you want
	// to talk to, you might need to uncomment the query-source
	// directive below.  Previous versions of BIND always asked
	// questions using port 53, but BIND 8.1 and later use an unprivileged
	// port by default.

	// query-source address * port 53;

	// If your ISP provided one or more IP addresses for stable 
	// nameservers, you probably want to use them as forwarders.  
	// Uncomment the following block, and insert the addresses replacing 
	// the all-0's placeholder.

	forwarders {
		194.168.4.100;
		194.168.8.100;
	};

	auth-nxdomain no;    # conform to RFC1035
	listen-on-v6 { any; };
};


I created the folder
**/etc/bind/zones**

and added

**file: /etc/bind/zones/rev.1.168.192.in-addr.arpa **
> 
@ IN SOA ns1.site1.co.uk. site1.co.uk. (
2007031001;
28800;
604800;
604800;
86400
)

IN NS ns1.site1.co.uk
100 IN PTR site1.co.uk


**file: /etc/bind/zones/site1.co.uk.db **
> 
site1.co.uk. IN SOA ns1.site1.co.uk. admin.site1.co.uk. (

2007031001
28800
3600
604800
38400
)


site1.co.uk. IN NS ns1.site1.co.uk.
site1.co.uk. IN MX 10 mail.site1.co.uk.

www IN A 192.168.1.100
mta IN A 192.168.1.100
ns1 IN A 192.168.1.100


restarted bind9

when i dig site1.co.uk in terminal i get
> 
; <<>> DiG 9.4.2-P1 <<>> site1.co.uk
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 11750
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;site1.co.uk.			IN	A

;; Query time: 0 msec
;; SERVER: 192.168.1.100#53(192.168.1.100)
;; WHEN: Sat Aug 16 12:13:25 2008
;; MSG SIZE  rcvd: 32



When I type [http://www.site1.co.uk](http://www.site1.co.uk) or [http://www.site2.co.uk](http://www.site2.co.uk) in a browser it opens the same site site2

Please can someone shed some light on what I have done wrong

---

### Post by windependence on 2008-08-16
Well I don't know crap about BIND9 because I don't run my own nameserver. It isn't necessary unless you have a large number of computers on your LAN and then it's only necessary to resolve the names locally. It has NOTHING to do with resolving your domain from the outside. Running your own probably just adds to your complexity and makes it more difficult. If you have less than 10 machines on your network, you would be better off just editing the hosts file on each machine. After the first one you can just cut and paste anyway.

Remember, on the inside of your network, your domains are resolved differently than from the outside.

-Tim

---

### Post by andyd34 on 2008-08-16
Thanks for your prompt reply.

When I have googled the subject people are always recommending a named based virtual host rather than an ip based. So if I set up a named based virtual host surely I would require a DNS server

---

### Post by windependence on 2008-08-16
No, actually that is another myth. Apache takes care of deciding what name has what document root. I have vhosts on a production server running right now and I have NO DNS server and never have. Outside your LAN, you don't need name resolution because the thousands of DNS servers on the web take care of that for you. Your domain registrar probably has a control panel where you can set up your DNS and A record, MX records etc. There, you point your doamin at your server IP and set up your nameservers using THEIR nameservers. Each new domain gets ointed at your one unique external IP and Apache gets the requests and parses the packet headers to figure out what site requested the packet. Nothing else necessary on your side.

On your private LAN, it's a different story. There, in  order for your computers to know what server name goes with what internal address, you need to add an alias to the hosts file on each of the computers on your LAN so they know that server1 is on IP 192.168.0.5 or whatever.

Here is a good article on DNS to help you better understand what's going on:

[http://www.debianhelp.co.uk/dnsrecords.htm](http://www.debianhelp.co.uk/dnsrecords.htm)

-Tim

---

### Post by andyd34 on 2008-08-16
I think I do understand now. Basically you adding a name to each Servers IP in the host file.

I'll do a clean install and give it a go

---

### Post by MJN on 2008-08-16
You have confirmed your DNS is fine by virtue of both [www.site1.co.uk]("http://www.site1.co.uk") and [www.site2.co.uk]("http://www.site2.co.uk") both resolving to the same IP. The only problem is that Apache is not serving up site1's config/files as appropriate.

I strongly suggest posting your virtualhost configs verbatim - do not translate them for 'privacy' as chances are in doing so you are masking the true cause of the problem.

Mathew

---

### Post by windependence on 2008-08-16
Don't reinstall, that't the Windoze way :)

Do what Mathew said and post your vhosts config file. We can fix this.

-Tim

---

### Post by andyd34 on 2008-08-16
To late, reinstalled. Its giving me a bit of practice with Ubuntu, I don't have to google as much now.

I now have Lamp Install as well as webmin, thats it

I've disabled the default site and added 2 virtual hosts through webmin but am still stuck with the same problem

[B]
file: /etc/apache2/sites-available/combiman.conf[/B]
> 
<VirtualHost *>
DocumentRoot "/media/disk/home/combiman/www"
ServerName combiman
<Directory "/media/disk/home/combiman/www">
allow from all
Options +Indexes
</Directory>
</VirtualHost>



[B]
file: /etc/apache2/sites-available/theukhub.conf[/B]
> 
<VirtualHost *>
DocumentRoot "/media/disk/home/theukhub/www"
ServerName theukhub
<Directory "/media/disk/home/theukhub/www">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

---

### Post by andyd34 on 2008-08-16
the url [http://www.combiman.co.uk](http://www.combiman.co.uk) isn't pointing to my server as yet but the url [http://www.theukhub.co.uk](http://www.theukhub.co.uk) is!!

---

### Post by MJN on 2008-08-16
The problem is you haven't put the fully qualified name on the Servername directives i.e. you didn't put the .co.uk on the end!

This is **EXACTLY** why you shouldn't munge your config files when posting them on a forum as you run the risk of getting it wrong!!! Your original munged file showed .co.uk entensions yet your true config doesn't!!

You might also want to add ServerAlias directives too (to catch the www. prefix)

Mathew

P.S. If you want your DNS to resolve the names for the rest of the world then you will need to delegate the authority to your server (they are currently pointing at 000webhost.com and hosteurope.com) however, as Tim suggested, I would leave that if I were you and stick to getting the Apache config right first! :)

---

### Post by windependence on 2008-08-16
Your server names should be the fully qualified domain name:

```
ServerName [www.virtual-host.net](www.virtual-host.net)

```

Apache doesn't know what site to send the requests to.

-Tim

---

### Post by windependence on 2008-08-16
Mathew, looks like I was writing my post while you posted yours. Same solution though! ;)

-Tim

---

### Post by MJN on 2008-08-16
No worries, I had to change mine half way through as we got the added info re the true domains names!

---

### Post by andyd34 on 2008-08-16
This was how webmin set them up not me. The origional config was and has been changed to


> 
<VirtualHost *>
ServerName [www.combiman.co.uk](www.combiman.co.uk)
DocumentRoot /media/disk/home/combiman/www
</VirtualHost> 


> 
NameVirtualHost *

<VirtualHost *>
ServerName [www.theukhub.co.uk](www.theukhub.co.uk)
DocumentRoot /media/disk/home/theukhub/www
</VirtualHost> 

But still the same thing happening

---

### Post by MJN on 2008-08-16
Talk about moving the goalposts!

Okay, so now we've got a clean config let's look at it again...

Firstly, we cannot proceed without you having a consistent DNS. Post the output of **dig [www.combiman.co.uk]("http://www.combiman.co.uk")** **A** and **dig [www.theukhub.co.uk]("http://www.theukhub.co.uk") A**

Also tell us the WAN IP address of your server / Internet connection.

The rest of the world resolves [www.combiman.co.uk]("http://www.combiman.co.uk") to 64.191.3.101 and [www.theukhub.co.uk]("http://www.theukhub.co.uk") to 194.154.164.82. How about you?

Given your sites supposedly sits on the one server we already have a problem with that inconsistency alone.

Mathew

---

### Post by andyd34 on 2008-08-16
Here are the outputs from the digs

> 
; <<>> DiG 9.4.2-P1 <<>> [www.theukhub.co.uk](www.theukhub.co.uk) A
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 18472
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;[www.theukhub.co.uk](www.theukhub.co.uk).		IN	A

;; ANSWER SECTION:
[www.theukhub.co.uk](www.theukhub.co.uk).	85891	IN	A	194.154.164.82

;; Query time: 33 msec
;; SERVER: 192.168.1.2#53(192.168.1.2)
;; WHEN: Sat Aug 16 17:39:27 2008
;; MSG SIZE  rcvd: 52


andy@server:~$ dig [www.combiman.co.uk](www.combiman.co.uk)

; <<>> DiG 9.4.2-P1 <<>> [www.combiman.co.uk](www.combiman.co.uk) A
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 24061
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;[www.combiman.co.uk](www.combiman.co.uk).		IN	A

;; ANSWER SECTION:
[www.combiman.co.uk](www.combiman.co.uk).	14400	IN	CNAME	combiman.co.uk.
combiman.co.uk.		86400	IN	A	64.191.3.101

;; Query time: 219 msec
;; SERVER: 192.168.1.2#53(192.168.1.2)
;; WHEN: Sat Aug 16 17:40:36 2008
;; MSG SIZE  rcvd: 66

andy@server:~$ 



With regards to the domains. I have 4 domains registered with Lycos but it takes them around a month to update. I have started transfering them to another company but as yet only one has transfered (theukhub.co.uk) which has updated and is pointed to my server.

With regards to the 194.154.164.82 address I think this may something to do with my internet providers DNS IP which is 194.168.4.100 & 194.168.8.100


My Server IP is 192.168.1.100 my Gateway is 192.168.1.2

**file: /etc/network/interfaces**

> 
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.2


auto eth0



I have changed the ServerName in /etc/apache2/apache2.conf to theukhub.co.uk

---

### Post by MJN on 2008-08-16
> **andyd34 said:**
> Here are the outputs from the digs

There's your problem. The DNS for the domains is pointing to completely different places hence only one of them is actually reaching your server. Given you have apparently configured one of the domains correctly, do the rest the same.

In the meantime if you want to check your Apache config is correct ready for when your DNS is sorted do the following:

1. Remove BIND

2. Add the following to /etc/hosts

```
192.168.1.100 www.combiman.co.uk www.ukhub.co.uk
```3. Ensure that each of your virtualhosts has the correct Servername (e.g. [www.combiman.co.uk]("http://www.combiman.co.uk")) and whilst your at it add a Serveralias (i.e. combiman.co.uk)

4. Restart Apache

5. Restart your browser(s) and give it a shot!

Step 2 effectively hard wires your URLs to the internal IP address and hence will mean your server is unaffected by your broken DNS configuration out on the Internet.

> I have changed the ServerName in /etc/apache2/apache2.conf to theukhub.co.ukThat's great. Now change it back. If you keep taking random pot shots at your config rather than following a methodical analysis of the cause of the problem then you really won't get anywhere. The only thing you'll learn is that stabbing in the dark just doesn't work.

Mathew

---

### Post by andyd34 on 2008-08-16
The ip address 192.168.1.2 is a quad WAN router not a PC also regardsding the ServerName this is one of your earlier replies

> 
 Re: Apache Virtual Host help needed
Your server names should be the fully qualified domain name:

Code:

ServerName [www.virtual-host.net](www.virtual-host.net)

Apache doesn't know what site to send the requests to.

-Tim


---

### Post by MJN on 2008-08-16
:confused:

> **andyd34 said:**
> The ip address 192.168.1.2 is a quad WAN router not a PC

Who said anything about 192.168.1.2? We don't need to be concerned with that address.

> also regardsding the ServerName this is one of your earlier repliesYes, but then in post #18 you said you'd now set it to be fully qualified (which is good) but then on post #20 you've now dropped the hostname.

Have you followed the suggested steps? If so, how's it looking?

Mathew

---

### Post by andyd34 on 2008-08-16
Its still the same, I'll post all the files I have

**apache2.conf**
> 
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
ServerName localhost
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
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

#
# ServerTokens
# This directive configures what you return as the Server HTTP response
# Header. The default is 'Full' which sends information about the OS-Type
# and compiled in modules.
# Set to one of:  Full | OS | Minor | Minimal | Major | Prod
# where Full conveys the most information, and Prod the least.
#
ServerTokens Full

#
# Optionally add a line containing the server version and virtual host
# name to server-generated pages (internal error documents, FTP directory 
# listings, mod_status and mod_info output etc., but not CGI generated 
# documents or custom error documents).
# Set to "EMail" to also include a mailto: link to the ServerAdmin.
# Set to one of:  On | Off | EMail
#
ServerSignature On



#
# Customizable error responses come in three flavors:
# 1) plain text 2) local redirects 3) external redirects
#
# Some examples:
#ErrorDocument 500 "The server made a boo boo."
#ErrorDocument 404 /missing.html
#ErrorDocument 404 "/cgi-bin/missing_handler.pl"
#ErrorDocument 402 [http://www.example.com/subscription_info.html](http://www.example.com/subscription_info.html)
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
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/


**sites-enabled/www.combiman.co.uk**
> 
<VirtualHost *>
ServerName [www.combiman.co.uk](www.combiman.co.uk)
DocumentRoot /media/disk/home/combiman/www
</VirtualHost> 


**sites-enabled/www.theukhub.co.uk**
> 
NameVirtualHost *

<VirtualHost *>
ServerName [www.theukhub.co.uk](www.theukhub.co.uk)
DocumentRoot /media/disk/home/theukhub/www
</VirtualHost> 


**hosts**
> 
127.0.0.1	localhost
127.0.1.1	server
192.168.1.100 [www.combiman.co.uk](www.combiman.co.uk) [www.ukhub.co.uk](www.ukhub.co.uk)

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


---

### Post by MJN on 2008-08-16
That's a bugger, not least given I'm losing the will to live on this one!

What's your IP address so I can connect from here?

And what should I be seeing when connecting to each URL?

Mathew

---

### Post by andyd34 on 2008-08-16
This is all thats in the index file for [www.theukhub.co.uk](www.theukhub.co.uk)

<?=phpinfo()?>

ip is 86.5.18.96

---

### Post by andyd34 on 2008-08-16
ive edited the hosts file cause i just copied and pasted your before

192.168.1.100 [www.combiman.co.uk](www.combiman.co.uk) [www.ukhub.co.uk](www.ukhub.co.uk)

to

192.168.1.100 [www.combiman.co.uk](www.combiman.co.uk) [www.theukhub.co.uk](www.theukhub.co.uk)


When I type [http://www.theukhub.co.uk](http://www.theukhub.co.uk) from the server I'm getting the right page. When I type it from another PC i'm not

---

### Post by MJN on 2008-08-16
The hosts files only affects lookups from that machine alone.

When I connect I also get the same site for both - a combiman website with 'Test!!!' written on it.

Please post the access logs for the last 10 minutes and we can see how things appeared at your end.

Mathew

---

### Post by andyd34 on 2008-08-16
access.log
> 
127.0.0.1 - - [16/Aug/2008:14:53:48 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [16/Aug/2008:14:53:48 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [16/Aug/2008:14:53:48 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [16/Aug/2008:14:53:48 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [16/Aug/2008:14:53:48 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [16/Aug/2008:14:54:23 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [16/Aug/2008:14:54:23 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [16/Aug/2008:14:54:23 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [16/Aug/2008:14:54:23 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [16/Aug/2008:14:54:23 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) (internal dummy connection)"


error.log
> 
[Sat Aug 16 14:53:47 2008] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Sat Aug 16 14:53:48 2008] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sat Aug 16 14:53:48 2008] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Sat Aug 16 14:54:23 2008] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sat Aug 16 14:54:23 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Sat Aug 16 14:54:29 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sat Aug 16 14:54:39 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Sat Aug 16 14:56:58 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sat Aug 16 14:57:08 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Sat Aug 16 15:07:29 2008] [notice] Graceful restart requested, doing restart
[Sat Aug 16 15:07:29 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Sat Aug 16 15:07:31 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sat Aug 16 15:07:35 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Sat Aug 16 15:30:38 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sat Aug 16 15:30:48 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Sat Aug 16 15:32:44 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sat Aug 16 15:32:54 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Sat Aug 16 16:58:11 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sat Aug 16 16:58:21 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Sat Aug 16 17:30:04 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sat Aug 16 17:30:14 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Sat Aug 16 17:53:33 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/chat
[Sat Aug 16 17:53:33 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/chat
[Sat Aug 16 17:53:33 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/chat
[Sat Aug 16 17:53:33 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/chat
[Sat Aug 16 17:53:34 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/phpchat
[Sat Aug 16 17:53:34 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/phpchat
[Sat Aug 16 17:53:34 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/PhpMyChat
[Sat Aug 16 17:53:35 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/PhpMyChat
[Sat Aug 16 17:53:35 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/chatroom
[Sat Aug 16 17:53:35 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/chats
[Sat Aug 16 17:53:35 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/chatroom
[Sat Aug 16 17:53:35 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/chats
[Sat Aug 16 17:53:35 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/forum
[Sat Aug 16 17:53:36 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/php
[Sat Aug 16 17:53:36 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/forum
[Sat Aug 16 17:53:36 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/phpMyChat-0.14.2
[Sat Aug 16 17:53:36 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/php
[Sat Aug 16 17:53:36 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/phpMyChat-0.14.2
[Sat Aug 16 17:53:36 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/phpMyChat-0.14.5
[Sat Aug 16 17:53:36 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/phpMyChat
[Sat Aug 16 17:53:37 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/phpMyChat-0.14.5
[Sat Aug 16 17:53:37 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/phpMyChat-0.14.3
[Sat Aug 16 17:53:37 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/phpMyChat
[Sat Aug 16 17:53:37 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/phpMyChat-0.14.4
[Sat Aug 16 17:53:37 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/phpMyChat-0.14.3
[Sat Aug 16 17:53:37 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/chat1
[Sat Aug 16 17:53:38 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/phpMyChat-0.14.4
[Sat Aug 16 17:53:38 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/forums
[Sat Aug 16 17:53:38 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/chat1
[Sat Aug 16 17:53:38 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/chat2
[Sat Aug 16 17:53:38 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/forums
[Sat Aug 16 17:53:38 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/chat3
[Sat Aug 16 17:53:38 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/chat2
[Sat Aug 16 17:53:38 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/community
[Sat Aug 16 17:53:38 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/chat3
[Sat Aug 16 17:53:38 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/community
[Sat Aug 16 17:53:55 2008] [error] [client 83.235.24.110] script '/media/disk/home/combiman/www/xmlrpc.php' not found or unable to stat
[Sat Aug 16 17:53:55 2008] [error] [client 83.235.24.110] script '/media/disk/home/combiman/www/xmlrpc.php' not found or unable to stat
[Sat Aug 16 17:53:55 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/xmlrpc
[Sat Aug 16 17:53:55 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/xmlrpc
[Sat Aug 16 17:53:55 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/xmlsrv
[Sat Aug 16 17:53:55 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/xmlsrv
[Sat Aug 16 17:53:56 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/blog
[Sat Aug 16 17:53:56 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/blog
[Sat Aug 16 17:53:56 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/drupal
[Sat Aug 16 17:53:56 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/drupal
[Sat Aug 16 17:53:56 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/community
[Sat Aug 16 17:53:57 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/community
[Sat Aug 16 17:53:57 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/blogs
[Sat Aug 16 17:53:57 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/blogs
[Sat Aug 16 17:53:57 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/blogs
[Sat Aug 16 17:53:57 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/blog
[Sat Aug 16 17:53:57 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/blogs
[Sat Aug 16 17:53:58 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/blogtest
[Sat Aug 16 17:53:58 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/blog
[Sat Aug 16 17:53:58 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/b2
[Sat Aug 16 17:53:58 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/blogtest
[Sat Aug 16 17:53:58 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/b2evo
[Sat Aug 16 17:53:58 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/b2
[Sat Aug 16 17:53:58 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/wordpress
[Sat Aug 16 17:53:58 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/b2evo
[Sat Aug 16 17:53:58 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/phpgroupware
[Sat Aug 16 17:53:58 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/wordpress
[Sat Aug 16 17:53:59 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/phpgroupware
[Sat Aug 16 17:54:14 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/awstats.pl
[Sat Aug 16 17:54:14 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/cgi-bin
[Sat Aug 16 17:54:14 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/awstats.pl
[Sat Aug 16 17:54:14 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/scgi-bin
[Sat Aug 16 17:54:14 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/cgi-bin
[Sat Aug 16 17:54:14 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/awstats
[Sat Aug 16 17:54:14 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/scgi-bin
[Sat Aug 16 17:54:14 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/cgi-bin
[Sat Aug 16 17:54:14 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/awstats
[Sat Aug 16 17:54:15 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/scgi-bin
[Sat Aug 16 17:54:15 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/cgi-bin
[Sat Aug 16 17:54:16 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/cgi
[Sat Aug 16 17:54:16 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/scgi-bin
[Sat Aug 16 17:54:16 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/scgi
[Sat Aug 16 17:54:16 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/cgi
[Sat Aug 16 17:54:16 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/scripts
[Sat Aug 16 17:54:16 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/scgi
[Sat Aug 16 17:54:16 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/cgi-bin
[Sat Aug 16 17:54:16 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/scripts
[Sat Aug 16 17:54:16 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/scgi-bin
[Sat Aug 16 17:54:17 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/cgi-bin
[Sat Aug 16 17:54:17 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/cgi-bin
[Sat Aug 16 17:54:17 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/scgi-bin
[Sat Aug 16 17:54:17 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/scgi-bin
[Sat Aug 16 17:54:17 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/stats
[Sat Aug 16 17:54:17 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/cgi-bin
[Sat Aug 16 17:54:17 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/scgi-bin
[Sat Aug 16 17:54:18 2008] [error] [client 83.235.24.110] File does not exist: /media/disk/home/combiman/www/stats
[Sat Aug 16 18:22:36 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sat Aug 16 18:22:46 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Sat Aug 16 18:24:33 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sat Aug 16 18:24:43 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Sat Aug 16 18:28:34 2008] [error] [client 74.6.8.117] File does not exist: /media/disk/home/combiman/www/robots.txt
[Sat Aug 16 18:39:57 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sat Aug 16 18:40:46 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Sat Aug 16 18:41:01 2008] [error] [client 192.168.1.2] File does not exist: /media/disk, referer: [http://www.theukhub.co.uk](http://www.theukhub.co.uk)
[Sat Aug 16 18:41:04 2008] [error] [client 192.168.1.2] File does not exist: /media/disk, referer: [http://www.theukhub.co.uk](http://www.theukhub.co.uk)
[Sat Aug 16 18:41:06 2008] [error] [client 192.168.1.2] File does not exist: /media/disk, referer: [http://www.theukhub.co.uk](http://www.theukhub.co.uk)
[Sat Aug 16 18:41:09 2008] [error] [client 192.168.1.2] File does not exist: /media/disk, referer: [http://www.theukhub.co.uk](http://www.theukhub.co.uk)
[Sat Aug 16 18:41:10 2008] [error] [client 192.168.1.2] File does not exist: /media/disk, referer: [http://www.theukhub.co.uk](http://www.theukhub.co.uk)
[Sat Aug 16 18:41:10 2008] [error] [client 192.168.1.2] File does not exist: /media/disk, referer: [http://www.theukhub.co.uk](http://www.theukhub.co.uk)
[Sat Aug 16 18:41:18 2008] [error] [client 192.168.1.2] File does not exist: /media/disk, referer: [http://www.theukhub.co.uk](http://www.theukhub.co.uk)
[Sat Aug 16 18:41:19 2008] [error] [client 192.168.1.2] File does not exist: /media/disk, referer: [http://www.theukhub.co.uk](http://www.theukhub.co.uk)
[Sat Aug 16 19:07:36 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sat Aug 16 19:07:46 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Sat Aug 16 19:08:10 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sat Aug 16 19:09:01 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Sat Aug 16 19:09:05 2008] [error] [client 77.103.161.36] File does not exist: /media/disk
[Sat Aug 16 19:09:10 2008] [error] [client 77.103.161.36] File does not exist: /media/disk
[Sat Aug 16 19:09:12 2008] [error] [client 77.103.161.36] File does not exist: /media/disk
[Sat Aug 16 19:09:13 2008] [error] [client 77.103.161.36] File does not exist: /media/disk
[Sat Aug 16 19:09:24 2008] [error] [client 77.103.161.36] File does not exist: /media/disk
[Sat Aug 16 19:09:28 2008] [error] [client 77.103.161.36] File does not exist: /media/disk
[Sat Aug 16 19:09:43 2008] [error] [client 192.168.1.100] File does not exist: /media/disk/home/theukhub/www/favicon.ico


---

### Post by MJN on 2008-08-16
That access.log is not the right one - it only goes up to 2:55pm. Please post the access log showing accesses in the last 10 minutes.

Can you create a simple text file in the root of your combiman site with the word 'combiman' in it. Do the same with your theukhub site, with a differet word in it, and tell me the URLs?

Mathew

---

### Post by MJN on 2008-08-16
Scrap that - it's all working now.

Tell us what you did and we can all move on!

(Remember to sort your DNS out - it's screwed)

Mathew

---

### Post by andyd34 on 2008-08-16
thats the only log file i have. I've modified the sites-available file

<VirtualHost *>
ServerName [www.theukhub.co.uk](www.theukhub.co.uk)
DocumentRoot /media/disk/home/theukhub/www

ErrorLog  /media/disk/home/theukhub/log/error.log
CustomLog /media/disk/home/theukhub/log/access.log combined
</VirtualHost> 

just to get you a log

---

### Post by MJN on 2008-08-16
(See my post above yours - it's working!!)

---

### Post by andyd34 on 2008-08-16
Its still the same for me

---

### Post by andyd34 on 2008-08-16
from the server everything is fine. from another pc on my network its not, from your end its fine. 

Is this the DNS problem!!!

As I said earlier I completely wiped my system, reinstalled ubuntu with LAMP

I didn't re install bind9 as you suggested

---

### Post by MJN on 2008-08-16
I didn't say reinstall BIND - I said remove it.

The problem is the DNS configuration out on the Internet - the domains are not configured the same - you saw it yourself in post #20!

As things currently stand it will only work for those that have hardwired a consistent mapping in their hosts file. So far that's you and me. Convincing everyone else to do it won't cut it so get in touch with your domain/DNS providers to point the domains at 86.5.18.96 !

Mathew

---

### Post by andyd34 on 2008-08-16
Will do, Thanks for all your help

---

