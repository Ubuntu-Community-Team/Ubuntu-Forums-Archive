---
title: "How to have transparent Squid proxy and HTTPS ?"
date: 2009-01-07
forum: Server Platforms
---

### Post by kurtkraut on 2009-01-07
Hi,

I have a working Squid transparent proxy in my local network, allowing user to access internet. But HTTPS websites like Gmail or mail.yahoo.com are inacessible. Firefox gives me the **[COLOR="Red"]ssl_error_rx_record_too_long[/COLOR]** error.

Here is my squid.conf:
```

http_port 3127 transparent
cache_mem 8 MB
cache_dir ufs /var/spool/squid 100 16 256
cache_log /var/log/squid/cache.log
cache_store_log /var/log/squid/store.log
pid_filename /var/run/squid.pid
visible_hostname adngateway
cache_effective_user proxy
cache_effective_group proxy
acl REDE_INTERNA src 192.168.1.0/255.255.255.0
acl WIRELESS src 192.168.2.0/255.255.255.0
acl all src 0.0.0.0/0.0.0.0
http_access allow REDE_INTERNA
http_access allow WIRELESS
http_access deny all
```

Here is my iptables rule:

```
iptables -t nat -A PREROUTING -i eth1 -p tcp -j REDIRECT --to-port 3127
```

From what I've seen on other posts, the best approach would be allowing to **443 TCP port access the internet directly**, without passing thru the proxy. But I'm not an iptables expert, don't know how to achieve that. Ny suggestions ? Other approaches ? Thanks in advance.

---

### Post by alan34 on 2009-01-07
In your squid.conf file add in your acl section
#
#  This line enables https connections - after much sweat and tears
#  Only in FAQs on squid website
#
acl SSL method CONNECT
#
#
#

The sweat and tears were mine it took me ages to find it!!

---

### Post by kurtkraut on 2009-01-07
> **alan34 said:**
> In your squid.conf file add in your acl 
acl SSL method CONNECT


Hi,

Thanks for your tip but it didn't work. Firefox still complains 'ssl_error_rx_record_too_long'. Here is my current squid.conf:
```

http_port 3127 transparent
cache_mem 8 MB
cache_dir ufs /var/spool/squid 100 16 256
cache_log /var/log/squid/cache.log
cache_store_log /var/log/squid/store.log
pid_filename /var/run/squid.pid
visible_hostname adngateway
cache_effective_user proxy
cache_effective_group proxy
acl SSL method CONNECT
acl REDE_INTERNA src 192.168.1.0/255.255.255.0
acl WIRELESS src 192.168.2.0/255.255.255.0
acl all src 0.0.0.0/0.0.0.0
http_access allow REDE_INTERNA
http_access allow WIRELESS
http_access deny all
```

---

### Post by alan34 on 2009-01-09
Sorry that did not work for you 

Here is most of the complete file

#Recommended minimum configuration:
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 563
acl Safe_ports port 80 88 	# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443 563	# https, snews
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl CONNECT method CONNECT
#
#  This line enables https connections - after much sweat and tears
#  Only in FAQs on squid website
#
acl SSL method CONNECT
#
#
#

#  TAG: http_access
#	Allowing or Denying access based on defined access lists
#
#	Access to the HTTP port:
#	http_access allow|deny [!]aclname ...
#
#	NOTE on default values:
#
#	If there are no "access" lines present, the default is to deny
#	the request.
#
#	If none of the "access" lines cause a match, the default is the
#	opposite of the last line in the list.  If the last line was
#	deny, the default is allow.  Conversely, if the last line
#	is allow, the default will be deny.  For these reasons, it is a
#	good idea to have an "deny all" or "allow all" entry at the end
#	of your access lists to avoid potential confusion.
#
#Default:
# http_access deny all
#
#Recommended minimum configuration:
#
# Only allow cachemgr access from localhost
http_access allow manager localhost
http_access deny manager
# Deny requests to unknown ports
http_access deny !Safe_ports
# Deny CONNECT to other than SSL ports
http_access deny CONNECT !SSL_ports
#
# We strongly recommend the following be uncommented to protect innocent
# web applications running on the proxy server who think the only
# one who can access services on "localhost" is a local user
#
#
http_access deny to_localhost
#
#
# Example rule allowing access from your local networks. Adapt
# to list your (internal) IP networks from where browsing should
# be allowed
#acl our_networks src 192.168.1.0/24 192.168.2.0/24
#http_access allow our_networks
#
#
# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS
#
#       	(old server)
#
acl allowed_hosts1 src  10.0.0.1/255.255.255.255
http_access allow allowed_hosts1
icp_access allow allowed_hosts1
#

# plus any computers you want or deny access to the proxy

#
#
#
# And finally deny all other access to this proxy
http_access deny all

#  TAG: http_reply_access
#        Allow replies to client requests. This is complementary to http_access.
#
#        http_reply_access allow|deny [!] aclname ...
#
#        NOTE: if there are no access lines present, the default is to allow
#	all replies
#
#        If none of the access lines cause a match the opposite of the
#        last line will apply. Thus it is good practice to end the rules
#        with an "allow all" or "deny all" entry.
#
#Default:
# http_reply_access allow all
#
#Recommended minimum configuration:
#
# Insert your own rules here.
#
#
# and finally allow by default
http_reply_access allow all

#  TAG: icp_access
#	Allowing or Denying access to the ICP port based on defined
#	access lists
#
#	icp_access  allow|deny [!]aclname ...
#
#	See http_access for details
#
#Default:
# icp_access deny all
#
#Allow ICP queries from everyone
icp_access allow all
#icp_access allow allowed_hosts


This is what I use on my server at work. Note I listen on port 88 I think it should be port 80 by default but I used port 88.

If you want to pm me with your email I will send you the complete file.

---

### Post by Kairon on 2011-01-02
> **kurtkraut said:**
> Hi,
 
Thanks for your tip but it didn't work. Firefox still complains 'ssl_error_rx_record_too_long'. 
 
After running into the exact same problem as you, and fighting with it for hours, I understood why you couldn't get it working: because it is impossible in transparent/intercept configuration.
 
alan34's posts are missing the http_port command but after much research, it became obvious that alan34 is using a regular proxy (where it is configured in the web browser) while you are trying a transparent proxy configuration which just doesn't work with SSL.
 
I decided to register just so I can post this here - being one of the top search engine results on the subject.

---

### Post by SeijiSensei on 2011-01-04
It looks like you can use the [SSLBump]("http://wiki.squid-cache.org/Features/SslBump") add-on for Squid to make it proxy HTTPS requests.  Obviously these will look like a "man-in-the-middle" attack to the users' browsers, but I think you can eliminate this problem if you can set up a Certificate Authority and install the appropriate certificates in the browsers.

I haven't done this myself, so YMMV.

---

