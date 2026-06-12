---
title: "Shorewall + Squid on Hardy Server Gateway / Firewall"
date: 2008-04-29
forum: Server Platforms
---

### Post by absolute512 on 2008-04-29
I just upgraded from Dapper to Hardy and didn't touch the server in a while, so I'm a bit rusty... 
Hi, I've got the following problem - Shorewall is configured (I as well as LAN clients can surf the internet) and squid is working (if I manually instruct links with the command -http_proxy 127.0.0.1:3128 squid redirects the sites i want it to) but the squid configuraion is not applied to the LAN clients. 
Here is my squid.conf:

http_port 127.0.0.1:3128
http_port 192.168.0.100:3128
icp_port 0
htcp_port 0
hierarchy_stoplist cgi-bin ? php asp
acl QUERY urlpath_regex cgi-bin \?
no_cache deny QUERY
cache_mem 256 MB
maximum_object_size 128 MB
cache_dir ufs /var/cache/squid 1024 16 256
access_log /var/log/squid/access.log squid
acl all src 0.0.0.0/0.0.0.0
acl localhost src 127.0.0.1/32
acl manager proto cache_object
acl ssl_ports port 443
acl ftp_ports port 21
acl www_ports port 80 443
acl CONNECT method CONNECT
acl PURGE method PURGE
http_access allow manager localhost
http_access deny manager
http_access allow PURGE localhost
http_access deny PURGE
http_access deny !www_ports !ftp_ports
http_access deny CONNECT !ssl_ports
acl sdd_proxy_users src 192.168.0.100/32
http_access allow sdd_proxy_users
http_access allow localhost
http_access deny all
reply_body_max_size 102400000 allow all
cache_mgr [email]root@proxy.sdd.com[/email]
visible_hostname proxy.sdd.com
cache_effective_user proxy
cache_effective_group proxy
logfile_rotate 0
buffered_logs on
url_rewrite_program /usr/local/rejik3/redirector /usr/local/rejik3/redirector.conf

These are my shorewall policies


loc		net		ACCEPT
loc	        $FW	        ACCEPT
loc		all		REJECT		info
$FW	        net      	ACCEPT
$FW	        loc	        ACCEPT
$FW		all		REJECT		info
net		$FW		DROP		info
net		loc		DROP		info
net		all		DROP		info
all		all		REJECT		info

and my shorewall rules


ACCEPT	        net	        $FW    tcp	25
ACCEPT	        net	        $FW    tcp	443
ACCEPT	        net     	$FW    udp	6277
DNS/ACCEPT	$FW		net
ACCEPT          loc             $FW    tcp      8080
ACCEPT          $FW             net    tcp      80,443
SSH/ACCEPT	loc		$FW
Ping/ACCEPT	loc		$FW
Ping/REJECT	net		$FW
ACCEPT		$FW		loc		icmp
ACCEPT		$FW		net		icmp

if needed, as I said, i'm a bit rusty and haven't done this for some time, I'll add my /etc/hosts

127.0.0.1       localhost.localdomain   localhost
192.168.0.100   server.sdd.com          server
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

and my /etc/network/interfaces

auto lo
iface inet lo loopback
auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet static
	address		192.168.1.1
	netmask		255.255.255.0
	broadcast	192.168.1.255
	network		192.168.1.0

finally my /etc/dhcp3/dhcpd.conf

subnet 192.168.1.0 netmask 255.255.255.0 {
	option netbios-name-servers 192.168.1.1;
	option domain-name-servers 192.168.1.1;
	option domain-name "your.domain.here";
	option broadcast-address 192.168.1.255;
	option routers 192.168.1.1;
	range 192.168.1.100 192.168.1.130;
	}

and my /etc/default/dhcp3-server
INTERFACES=eth1


Ok, I think that is probably more info than you would actually need, I just posted every config I was asked for in the irc's. I'm sorry for the long post!
I've been trying to figure out the problem for the past week and don't knwo what else to do. If someone could please help me out by telling me what to change to route all LAN traffic through the squid proxy and thereby use the url redirection I would be very grateful. 

Thank you

---

### Post by absolute512 on 2008-05-19
Hi, I have updated my /etc/squid/squid.conf to the following

# squid listens on the loopback and on
# the internal interface (3128 port)
http_port 3128 transparent

# Disable ICP and HTCP queries to/from neighbor caches.
# These features are needed only in a multi-level cache
# environment with multiple siblings and parent caches
icp_port 0
htcp_port 0

# Words defined in this tag when matched in the URLs,
# directs squid not to query caches.
# For example dynamic content - php or asp pages.
hierarchy_stoplist cgi-bin ? php asp
acl QUERY urlpath_regex cgi-bin \?
no_cache deny QUERY

# Specify the amount of RAM, to be used for caching the
# so called: In-Transit objects, Hot Objects,
# Negative-Cached objects.
cache_mem 256 MB

# If a file size is less than - 100 MB,
# squid will place it in cache
maximum_object_size 512 MB

# Define the path to cache directory where all objects which
# are to be cached are stored:
# 1024 - is the amount of disk space (MB)
# to use under /var/cache/squid directory
# 16 - is the number of first-level subdirectories
# which will be created under the
# /var/cache/squid directory
# 256 - is the number of second-level
# subdirectories which will be created under
# each first-level directory
cache_dir ufs /var/cache/squid 1024 16 256

# Log client request activities to the
# /var/log/squid/access.log file using the squid log format
access_log /var/log/squid/access.log squid

# Define access control lists
acl all src 0.0.0.0/0.0.0.0
acl localhost src 127.0.0.1/32
acl manager proto cache_object
acl ssl_ports port 443
acl ftp_ports port 21
acl www_ports port 80 443
acl CONNECT method CONNECT
acl PURGE method PURGE

# Recommended minimum configuration:
# Only allow cachemgr access from localhost
http_access allow manager localhost
http_access deny manager
# Only allow purge requests from localhost
http_access allow PURGE localhost
http_access deny PURGE
# Deny requests to unknown ports
http_access deny !ftp_ports !www_ports
# Deny CONNECT to other than SSL ports
http_access deny CONNECT !ssl_ports

# Rules for our clients
acl sdd_proxy_users src 192.168.0.100/32
# http_redirect allow sdd_proxy_users
http_access allow sdd_proxy_users

# Allow the localhost to have access by default
http_access allow localhost

# And deny all other access to this proxy
# http_redirect allow all
http_access deny all

# Prevent users from downloading very large files
# (limit to ~100MB)
reply_body_max_size 102400000 allow all

# Supply an e-mail where users can send their remarks
# or problems regarding squid
cache_mgr Gustav

# Define the hostname that will be shown in
# error messages etc.
visible_hostname proxy.sdd.com

# Specify the UID/GID that the squid will run on
cache_effective_user proxy
cache_effective_group proxy

# Squid has a built in feature for the rotation of the logs.
# But I prefer logrotate
logfile_rotate 0

# Speed up the writing of some log files
buffered_logs on

# Redirecion
url_rewrite_program /usr/local/rejik3/redirector /usr/local/rejik3/redirector.conf
# redirect_program /usr/local/rejik3/redirector /usr/local/rejik3/redirector.conf

and /etc/shorewall/rules now looks like this

#############################################################################################################
#ACTION        SOURCE        DEST        PROTO    DEST    SOURCE        ORIGINAL    RATE        USER/
#                            PORT    PORT(S)        DEST        LIMIT        GROUP
#                                PORT    PORT(S) DEST            LIMIT    GROUP
#
#    Accept DNS connections from the firewall to the network
#
ACCEPT    net    $FW    tcp    25
ACCEPT    net    $FW    tcp    443
ACCEPT    net    $FW    udp    6277
DNS/ACCEPT    $FW        net
REDIRECT  loc        3128     tcp      www    -  !127.0.0.1    
ACCEPT    $FW        net      tcp      www
#
#Accept SSH connections from the local network for administration
Ping/ACCEPT    loc        $FW
#
#    Allow Ping from the local network
#
SSH/ACCEPT    loc        $FW
#
# Reject Ping from the "bad" net zone.. and prevent your log from being flooded..
#
Ping/REJECT    net        $FW
ACCEPT        $FW        loc        icmp
ACCEPT        $FW        net        icmp
#
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE

But now it blocks all web pages and that is not what I want. But now i think it could be a squid.conf setting I did wrong. 
Every other setting I posted before remains the same. 
Does anzbody have an idea about what i´m doing wrong?

Thank you abs512

---

### Post by sut123 on 2008-05-19
Try to access a webpage from your client and post your /var/log/messages file after the request.

---

### Post by Monicker on 2008-05-19
Are the clients behind 192.168.0.100 as a NAT address?  You are only allowing that one ip in your squid.conf.  Also check /var/log/squid/access_log for detail.

I've never used Shorewall, so I don't know if that is a factor or not.

---

### Post by ginjabunny on 2008-05-19
I had a look through your Shorewall rules and they seem ok, but I know nothing of Squid.

this is from the documention examples for shorewall rules, see [http://www.shorewall.net/Manpages.html](http://www.shorewall.net/Manpages.html)

Redirect all locally-originating www connection requests to port 3128 on the firewall (Squid running on the firewall system) except when the destination address is 192.168.2.2

#ACTION  SOURCE DEST      PROTO DEST    SOURCE  ORIGINAL
#                               PORT    PORT(S) DEST
REDIRECT loc    3128      tcp   www      -      !192.168.2.2

---

### Post by absolute512 on 2008-05-20
Thank you for all your replies, 
ginjabunny: I'm going to change the destination address to 192.168.2.2 when i'm @ the office tomorrow. TY
Monicker: The DHCP-server range is from 192.168.1.100 to 192.168.1.130, eth1 (internal network) is set to 192.168.1.1. I'll cycle through the addresses and check the log. TY
I'll be back tomorrow and tell you how it goes.

abs512

---

### Post by absolute512 on 2008-05-21
I updated the settings as told to a different NAT in acl sdd_proxy_users src, but i found no other way than to write down all the addressess manually (192.168.1.130 192.168.1.129 192.168.1.128 192.16... ), is there a more elegant way to do this, like giving the ip range (192.168.1.100 to 192.168.1.130)? But apart of that everything now seems to work!
 Thank you very much, 

abs512

PS: if someone could just tell me how to make an acl that is no affected by the proxy, that would be great

---

