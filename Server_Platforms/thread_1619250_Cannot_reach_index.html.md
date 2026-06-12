---
title: "Cannot reach index.html"
date: 2010-11-11
forum: Server Platforms
---

### Post by schmutztaucher on 2010-11-11
I am setting up a web server with Ubuntu Server 10.04 64bit.

I cannot reach my index.html via [www.mysite.com]("http://www.mysite.com"), mysite.com, or mysite.com:80. 
I can however reach it in my internal network by use of the internal_server_IP:80

I am using apache2 with a static public IP address. I attached my dns records, port forwarding, and a bonus pic! The bonus pic shows what happens when I put in my FQDN into the address bar.

ports.conf
```

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

"/etc/apache2/ports.conf"

```Apache2.conf
```

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
                                                                                                                                                                                   29,1          15%

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
                                                                                                                                                                                   82,1          44%

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

                                                                                                                                                                                   135,1         73%



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

# Define an access log for VirtualHosts that don't define their own logfile
CustomLog /var/log/apache2/other_vhosts_access.log vhost_combined


# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

```apache2/sites-available/mysite

```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        ServerName mysite.com
        ServerAlias *.mysite.com

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
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```Any and all help will be appreciated!

Thanks,
~S

---

### Post by wongo888 on 2010-11-11
Maybe your router is listening on port 80? Do you remotely manage your router from time to time? If so it is bound to port 80 on your external IP and you cannot forward requests into your LAN if your router is using the port. On my router, there is a checkbox to turn off the router from listening on the external IP.

Try binding a diff port like 8080 and point it to your internal server. Anything happen?

---

### Post by CharlesA on 2010-11-11
Could be that yer isp is blocking port 80.

check shield's up to see if it's actually open.

EDIT: Yeah, it looks like you have the router configured for remote management, if you disable that, you should be golden.

---

### Post by Whiteice on 2010-11-11
probley not the issue, I work for an ISP and from my knowledge its more hassel then its worth to block customer ports.

---

### Post by schmutztaucher on 2010-11-11
Thanks for the quick response guys!
 
Im at work and will try to fix it when i get back.
 
Thanks,
 
~s

---

### Post by schmutztaucher on 2010-11-12
After further review of the problem it still doesn't work. 

I turned off what I thought was the HTTP wan management port (see pic 1). 
After doing so I was still getting the configuration page via mysite.com. I get the router configuration page if HTTP is checked enabled or not.
So I did a hard reset on the router and reconfigured it to see if that would help but it didn't.

Interestingly enough when i went to forward port 80 to port 80 I got this message (see pic 2).
I thought that I would now be able to access my web page via mysite.com. But alas no dice cause I still get the configuration page.

Currently I have nothing checked in the access control services for WAN. Web traffic is forwarded to my servers internal IP address.

EDIT: I checked shield's up and port 80 was open

What is the next step to try?

---

### Post by CharlesA on 2010-11-12
Yay.

What model of router is it?

There should be a way to turn off remote management.

---

### Post by arrrghhh on 2010-11-12
> **CharlesA said:**
> Yay.

What model of router is it?

There should be a way to turn off remote management.

+1.  You should also be able to change the port so it's not using 80...

---

### Post by Vegan on 2010-11-12
I looked at the screen shots for router in use, man what a nightmare to manage compared to my old Linksys WRT54GL box.

My box is simple, it can manage any port and aim it to anywhere on the LAN. Real simple, forward only the ports you want. Rest are firewalled.

---

### Post by CharlesA on 2010-11-12
> **Vegan said:**
> I looked at the screen shots for router in use, man what a nightmare to manage compared to my old Linksys WRT54GL box.

My box is simple, it can manage any port and aim it to anywhere on the LAN. Real simple, forward only the ports you want. Rest are firewalled.

I know what you mean. That interface looks like a nightmare even compared to my Belkin router.

---

### Post by schmutztaucher on 2010-11-12
It is a Comtrend ADSL2+ CT-5361t
User Manual
[http://download.comtrend.com/CT5361T_A3.3.pdf](http://download.comtrend.com/CT5361T_A3.3.pdf)

I think i may need to buy a different aDSL modem.

---

### Post by CharlesA on 2010-11-12
Looks like you'd need to set it up under "virtual servers" which is what you did.

From reading the manual it looks like what you want to do would be listed under "management"

---

### Post by arrrghhh on 2010-11-12
Yea, may be in the cards.  You can disable WAN management it looks like, but it may always wreak havoc on your LAN...

---

### Post by schmutztaucher on 2010-11-12
VICTORY!!

Thanks for the help guys i hope it wasn't in vain.

I just went out upon the town for a bit and tried my site from a different network. [U]AND IT WORKED!

[/U]I am very perplexed at this moment. I came back to my server's lan and tried mydomain.com again and I got the router management page. ???

From what I can tell... putting  [www.FQDN.com](www.FQDN.com) into my browser on my lan yields my router configuration page. Putting [www.FQDN.com](www.FQDN.com) into my browser on a different network yields my /var/www/index.html page.

right now my WAN http service is off on the router and i am forwarding to port 80 from port 80.

I will do some more investigating.

Now to close some ufw ports...

---

### Post by CharlesA on 2010-11-12
Oh. If you are trying to access the machine from the external ip from inside the network, most routers don't know how to handle it.

---

### Post by arrrghhh on 2010-11-12
> **CharlesA said:**
> Oh. If you are trying to access the machine from the external ip from inside the network, most routers don't know how to handle it.

+1, your router doesn't know what to do with it.  Use the local IP locally, and the WAN IP... WANily?  No that just doesn't work.  When away :p  

Glad it's solved!

---

