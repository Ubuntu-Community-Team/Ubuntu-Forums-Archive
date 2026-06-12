---
title: "Network Timeout with Apache and SSH"
date: 2009-06-24
forum: Server Platforms
---

### Post by davidjohns on 2009-06-24
Apache will work good for about 5-10 minutes, then I'll click on a link and FireFox will show "Connecting to xxx.xxx.xxx.xxx" at the bottom left hand side, then I get:

Page Load Error
Network Timeout
The server at xxx.xxx.xxx.xxx is taking too long to respond.

I try to refresh the page, click on Try Again, click on other links, but nothing works... all I get is "Connecting to xxx.xxx.xxx.xxx" and the Network Timeout page.

I will receive the Network Timeout for about 1-2 minutes, then everything will start working good for 5-10 minutes, then I receive the Network Timeout error for 1-2 minutes again.

This problem also happens when using SSH. I use Putty to SSH to my Ubuntu server. Everything will be working good, then putty will freeze and say Putty Fatal Error. Network error: Software caused connection abort. If I try to reconnect, putty will say Network error: Connection timed out for about 1-2 minutes... then I'm able to reconnect again for 5-10 minutes.

I use Ubuntu 9.04 Server Edition

My network setup:
Westell 327W DSL Modem (its a DSL modem, 4 port router, and wireless which i have disabled), from the 327W to Ubuntu 9.04 Server, and from 327W to Windows XP computer.

I have the firewall on the 327W modem/router disabled. I also have my Ubuntu server as DMZ host.

I use UFW on my Ubuntu Server...

Here's the UFW Status:
```

root@honda:~# ufw status verbose
Status: active
Logging: on (low)
Default: deny
New profiles: skip

To                         Action  From
--                         ------  ----
10000/tcp                  ALLOW   192.168.1.45
22/tcp                     ALLOW   192.168.1.45
80/tcp                     ALLOW   Anywhere

```

Here is the iptables -L :
```

root@honda:~# iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination
ufw-before-logging-input  all  --  anywhere             anywhere
ufw-before-input  all  --  anywhere             anywhere
ufw-after-input  all  --  anywhere             anywhere
ufw-after-logging-input  all  --  anywhere             anywhere
ufw-reject-input  all  --  anywhere             anywhere

Chain FORWARD (policy DROP)
target     prot opt source               destination
ufw-before-logging-forward  all  --  anywhere             anywhere
ufw-before-forward  all  --  anywhere             anywhere
ufw-after-forward  all  --  anywhere             anywhere
ufw-after-logging-forward  all  --  anywhere             anywhere
ufw-reject-forward  all  --  anywhere             anywhere

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ufw-before-logging-output  all  --  anywhere             anywhere
ufw-before-output  all  --  anywhere             anywhere
ufw-after-output  all  --  anywhere             anywhere
ufw-after-logging-output  all  --  anywhere             anywhere
ufw-reject-output  all  --  anywhere             anywhere

Chain ufw-after-forward (1 references)
target     prot opt source               destination

Chain ufw-after-input (1 references)
target     prot opt source               destination
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-ns
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-dgm
RETURN     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn
RETURN     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds
RETURN     udp  --  anywhere             anywhere            udp dpt:bootps
RETURN     udp  --  anywhere             anywhere            udp dpt:bootpc
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination

Chain ufw-after-output (1 references)
target     prot opt source               destination

Chain ufw-before-forward (1 references)
target     prot opt source               destination
ufw-user-forward  all  --  anywhere             anywhere

Chain ufw-before-input (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID
DROP       all  --  anywhere             anywhere            state INVALID
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc
ufw-not-local  all  --  anywhere             anywhere
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4
ufw-user-input  all  --  anywhere             anywhere

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination

Chain ufw-before-output (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED
ufw-user-output  all  --  anywhere             anywhere

Chain ufw-logging-allow (0 references)
target     prot opt source               destination

Chain ufw-logging-deny (2 references)
target     prot opt source               destination

Chain ufw-not-local (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10
DROP       all  --  anywhere             anywhere

Chain ufw-reject-forward (1 references)
target     prot opt source               destination

Chain ufw-reject-input (1 references)
target     prot opt source               destination

Chain ufw-reject-output (1 references)
target     prot opt source               destination

Chain ufw-user-forward (1 references)
target     prot opt source               destination

Chain ufw-user-input (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  david                anywhere            tcp dpt:webmin
ACCEPT     tcp  --  david                anywhere            tcp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www

Chain ufw-user-limit (0 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] '
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination

Chain ufw-user-output (1 references)
target     prot opt source               destination

```

Here's my apache config file:
```

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
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

```

---

### Post by Kareeser on 2009-06-24
Hm, this will be difficult if your SSH sessions are on the fritz as well, but it looks like the problem is related to both symptoms.

SSH into the server using PuTTY, and run this command:
```
tail -F /var/log/syslog
```

Now, let it sit until the session drops. What was the last message?

---

### Post by davidjohns on 2009-06-25
Thanks for the reply!

The last messages when the session drops:
```

Jun 25 00:49:07 141 dhclient: DHCPREQUEST of 141.xxx.xxx.xxx on eth0 to 192.168.1.1 port 67
Jun 25 00:49:07 141 dhclient: DHCPACK of 141.xxx.xxx.xxx from 192.168.1.1
Jun 25 00:49:07 141 dhclient: bound to 141.xxx.xxx.xxx -- renewal in 138 seconds.
Jun 25 00:50:01 141 /USR/SBIN/CRON[24726]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun 25 00:51:25 141 dhclient: DHCPREQUEST of 141.xxx.xxx.xxx on eth0 to 192.168.1.1 port 67
Jun 25 00:51:25 141 dhclient: DHCPACK of 141.xxx.xxx.xxx from 192.168.1.1
Jun 25 00:51:25 141 dhclient: bound to 141.xxx.xxx.xxx -- renewal in 124 seconds.
Jun 25 00:53:29 141 dhclient: DHCPREQUEST of 141.xxx.xxx.xxx on eth0 to 192.168.1.1 port 67
Jun 25 00:53:29 141 dhclient: DHCPACK of 141.xxx.xxx.xxx from 192.168.1.1
Jun 25 00:53:29 141 dhclient: bound to 141.xxx.xxx.xxx -- renewal in 127 seconds.
Jun 25 00:55:36 141 dhclient: DHCPREQUEST of 141.xxx.xxx.xxx on eth0 to 192.168.1.1 port 67
Jun 25 00:55:36 141 dhclient: DHCPACK of 141.xxx.xxx.xxx from 192.168.1.1
Jun 25 00:55:36 141 dhclient: bound to 141.xxx.xxx.xxx -- renewal in 127 seconds.

```

* I did hide my real IP with 141.xxx.xxx.xxx

---

### Post by davidjohns on 2009-06-25
I think it has something to do with the DMZ Host on my DSL modem/router.

This problem occurs when I have the Ubuntu server as the DMZ host. Im thinking its my hostname, localdomain, and/or routing.

I receive no errors in the /var/log/auth.log, /var/log/syslog, or the /var/log/apache2/error.log.

If I SSH to the Ubuntu server using only the hostname (not the IP), putty connects to MYHOSTNAME.myhome.westell.com ??

---

### Post by realloc on 2009-09-24
I am seeing the same issue, but in a slight different setup.  I have a firewall (8.04) running ufw.  I manually set up port forwarding on the firewall by adding this to /etc/ufw/before.rules:

```

# From http://ubuntuforums.org/showthread.php?t=833844
# Allow certain ports through:

*nat
:PREROUTING - [0:0]

# My DNAT rules
-A PREROUTING -i eth0 -p tcp --dport 22 -j DNAT --to-destination 192.168.101.1:22
-A PREROUTING -i eth0 -p udp --dport 22 -j DNAT --to-destination 192.168.101.1:22

# don't delete the 'COMMIT' line or these nat table rules won't be processed
COMMIT

# From https://help.ubuntu.com/9.04/serverguide/C/firewall.html
# nat Table rules
*nat
:POSTROUTING ACCEPT [0:0]

# Forward traffic from eth1 through eth0.
-A POSTROUTING -s 192.168.101.0/24 -o eth0 -j MASQUERADE

# don't delete the 'COMMIT' line or these nat table rules won't be processed
COMMIT

```

This is a simple "reverse-NAT" or "port forwarding" setup.  It works for a simple SSH login, but if I try to copy some files with scp, then it dies after copying a few megs worth:

```
dereks@dereks-laptop:~/Lost-Pics$ scp -r -p firewall:/var/cache/rsnapshot/monthly.2/internal/home/samba/groups/shared/Pictures/2007/2007-08/2007-08-06 ./
DSC04942.JPG                                  100% 1749KB   1.7MB/s   00:00    
DSC04944.JPG                                  100% 1735KB   1.7MB/s   00:00    
DSC04893.JPG                                  100% 1791KB   1.8MB/s   00:01    
DSC04927.JPG                                  100% 1510KB   1.5MB/s   00:00    
DSC04966.JPG                                  100% 1703KB   1.7MB/s   00:00    
DSC04926.JPG                                   74% 1312KB   0.0KB/s - stalled -

```

Note that "stalled" at the bottom.

This looks like a problem with connection rate limiting... i.e., one SSH connection is okay, but copying many files (or doing many HTTP requests) causes it to block.  However, I can't find anything with "iptables -L -v", so I don't know what is going on.


EDIT: I upgraded my firewall from 8.04 to 9.04 and now it works as I expect it to.  I think the "MANAGE_BUILTINS" option in ufw (in the 9.04 version) may have something to do with this (in file /etc/default/ufw).  Maybe the old 8.04 version was futzing with my PREROUTING and POSTROUTING...?

---

