---
title: "HTTPS only works on local network..."
date: 2008-11-20
forum: Server Platforms
---

### Post by frmdstryr on 2008-11-20
I created a self-signed certificate and got it working with ssl/https.  When I type [https://www.*******.com/](https://www.*******.com/) (my server) it works on computers in my local network.  I have apache2 on my ubuntu desktop, connected to a router that has 3 other computers.  I enabled port 444 and have port 444 set to be forwarded by my router (443 is blocked by my ip).  As I said before it works with my local computers but if I try to access it out of my network by [https://www.*******.com:444/](https://www.*******.com:444/)  it will connect but say "this page cannot be displayed, you may not have permission or the site may require you to login" (I think it is error 403). Nothing pops up about being a self signed certificate, any ideas? Thanks.

---

### Post by Thirtysixway on 2008-11-20
Which browser are you using?  Some browsers handle lan security differently than internet.

---

### Post by frmdstryr on 2008-11-20
I tried it in both IE and Firefox.

---

### Post by cariboo on 2008-11-20
Have you had someone from outside your network try to access the server? Have you made sure that port 444 is open to the outside world. Go [ here]("http:///www.canyouseeme.org/") to check if the ports are open.

Jim

---

### Post by MJN on 2008-11-21
> **frmdstryr said:**
> I created a self-signed certificate and got it working with ssl/https. When I type [https://www.*******.com/](https://www.*******.com/) (my server) it works on computers in my local network. I have apache2 on my ubuntu desktop, connected to a router that has 3 other computers. I enabled port 444 and have port 444 set to be forwarded by my router (443 is blocked by my ip). As I said before it works with my local computersNo, you've said it works on port 443 (i.e. the default when not specified as part of the URL). Does the site work locally using port 444? (e.g. [https://localhost:444/](https://localhost:444/) on the server, ignoring any certificate mismatch errors)
 
You have not said if Apache is listening on port 443, or port 444. If the former then presumably you have set your router to map 444->443?
 
Is there a non-SSL site on the server? If so, does that work from the WAN?
 
Given you have obfuscated your domain name we are very limited in how we can help given diagnosis from our end is impossible without it.
 
Your Apache site configuration is also critical to faulfinding the issue.
 
Mathew

---

### Post by frmdstryr on 2008-11-25
Can you see me says success on port 444.  I've tried to access it two places outside of my network, both of them connect but recieve an error that stops them from viewing the pages and it brings up an error.  Thanks for the help so far!

---

### Post by MJN on 2008-11-26
Did you miss my post?
 
We need your URL and Apache config if we are to stand any chance of helping you.
 
Mathew

---

### Post by frmdstryr on 2008-11-26
Sorry I did miss that... the url is [https://frmdstryr.dnsalias.com:444](https://frmdstryr.dnsalias.com:444) or [http://frmdstryr.dnsalias.com:81](http://frmdstryr.dnsalias.com:81). 

Here is the apache.conf...

```
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
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

ServerName frmdstryr.dnsalias.com
```


Here is my sites-enabled link...

```
NameVirtualHost *:80
NameVirtualHost *:81
NameVirtualHost *:443
NameVirtualHost *:444

<VirtualHost *:80 >
	ServerName frmdstryr.dynalias.com
	ServerAlias *.frmdstryr.dynalias.com
	ServerAdmin frmdstryr@gmail.com
	DocumentRoot Projects/www/
</VirtualHost>

<VirtualHost *:81 >
	ServerName frmdstryr.dynalias.com
	ServerAlias *.frmdstryr.dynalias.com
	ServerAdmin frmdstryr@gmail.com
	DocumentRoot Projects/www/
</VirtualHost>

<VirtualHost *:443 >
	ServerName localhost
	ServerAlias *.frmdstryr.dynalias.com
	ServerAdmin frmdstryr@gmail.com
	DocumentRoot Projects/www/
	SSLEngine on
	SSLCertificateFile /etc/apache2/apache.pem
</VirtualHost>

<VirtualHost *:444 >
	ServerName localhost
	ServerAlias *.frmdstryr.dynalias.com
	ServerAdmin frmdstryr@gmail.com
	DocumentRoot Projects/www/
	SSLEngine on
	SSLCertificateFile /etc/apache2/apache.pem
</VirtualHost>
```

Thanks!

---

### Post by MJN on 2008-11-26
That's much better!

However, [https://frmdstryr.dnsalias.com:444](https://frmdstryr.dnsalias.com:444) works fine for me (screenshot attached). Of course, the self-signed certificate throws a warning but aside from that there's no issue.

I'd suggest changing clients and/or testing method.

Mathew

---

### Post by frmdstryr on 2008-11-26
Wow, okay, I just installed some updates for ubuntu, perhaps one of those fixed it..  Thanks!

---

### Post by itilious on 2011-05-14
I was JUST about to reply saying that I had the same issue and then at the last moment I realized I had not setup port 443 to be forwarded to my web server machine,,,, oops

Still learned some new ssl stuff from this thread, being a novice linux user,,,, just thought I'd state the obvious for anyone who might have made this mistake as well :)

---

