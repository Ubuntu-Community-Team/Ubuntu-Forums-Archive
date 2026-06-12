---
title: "please help with blocking https site with squid on webmin"
date: 2010-12-08
forum: Server Platforms
---

### Post by sipetron on 2010-12-08
Dear all 
i blocked facebook and youtube but if any one change the http with https its open with him 
how can i mange https like http

---

### Post by chrislynch8 on 2010-12-08
No sure about the webmin way but look at squidGuard and use that with squid.

---

### Post by SlugSlug on 2010-12-08
how are you blocking?

only put 
.facebook.com


not [www.facebook.com](www.facebook.com) etc

---

### Post by sipetron on 2010-12-08
That's what I did even I put facebook alone and nothing happend

---

### Post by SlugSlug on 2010-12-08
try add to the squid.conf

acl SSL_ports port 443 563
##to your acl section 

and a bit lower down 
http_access deny CONNECT !SSL_ports

---

### Post by sipetron on 2010-12-08
its didnt work [IMG]file:///tmp/moz-screenshot-1.png[/IMG][IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by SlugSlug on 2010-12-08
perhaps post the whole of 
```
cat /etc/squid/squid.conf
```

and someone here can help..

---

### Post by sipetron on 2010-12-08
```
# max_filedescriptors 0

#  TAG: accept_filter
#    FreeBSD:
#
#    The name of an accept(2) filter to install on Squid's
#    listen socket(s).  This feature is perhaps specific to
#    FreeBSD and requires support in the kernel.
#
#    The 'httpready' filter delays delivering new connections
#    to Squid until a full HTTP request has been received.
#    See the accf_http(9) man page for details.
#
#    The 'dataready' filter delays delivering new connections
#    to Squid until there is some data to process.
#    See the accf_dataready(9) man page for details.
#
#    Linux:
#    
#    The 'data' filter delays delivering of new connections
#    to Squid until there is some data to process by TCP_ACCEPT_DEFER.
#    You may optionally specify a number of seconds to wait by
#    'data=N' where N is the number of seconds. Defaults to 30
#    if not specified.  See the tcp(7) man page for details.
#EXAMPLE:
## FreeBSD
#accept_filter httpready
## Linux
#accept_filter data
#
#Default:
# none

#  TAG: tcp_recv_bufsize    (bytes)
#    Size of receive buffer to set for TCP sockets.  Probably just
#    as easy to change your kernel's default.  Set to zero to use
#    the default buffer size.
#
#Default:
# tcp_recv_bufsize 0 bytes

#  TAG: incoming_rate
#    This directive controls how aggressive Squid should accept new
#    connections compared to processing existing connections. 
#    The lower number the more frequent Squid will look for new
#    incoming requests.
#
#Default:
# incoming_rate 30


# DNS OPTIONS
# -----------------------------------------------------------------------------

#  TAG: check_hostnames
#    For security and stability reasons Squid by default checks
#    hostnames for Internet standard RFC compliance. If you do not want
#    Squid to perform these checks then turn this directive off.
#
#Default:
# check_hostnames on

#  TAG: allow_underscore
#    Underscore characters is not strictly allowed in Internet hostnames
#    but nevertheless used by many sites. Set this to off if you want
#    Squid to be strict about the standard.
#    This check is performed only when check_hostnames is set to on.
#
#Default:
# allow_underscore on

#  TAG: cache_dns_program
# Note: This option is only available if Squid is rebuilt with the
#       --disable-internal-dns option
#
#    Specify the location of the executable for dnslookup process.
#
#Default:
# cache_dns_program /usr/lib/squid/dnsserver

#  TAG: dns_children
# Note: This option is only available if Squid is rebuilt with the
#       --disable-internal-dns option
#
#    The number of processes spawn to service DNS name lookups.
#    For heavily loaded caches on large servers, you should
#    probably increase this value to at least 10.  The maximum
#    is 32.  The default is 5.
#
#    You must have at least one dnsserver process.
#
#Default:
# dns_children 5

#  TAG: dns_retransmit_interval
#    Initial retransmit interval for DNS queries. The interval is
#    doubled each time all configured DNS servers have been tried.
#
#
#Default:
# dns_retransmit_interval 5 seconds

#  TAG: dns_timeout
#    DNS Query timeout. If no response is received to a DNS query
#    within this time all DNS servers for the queried domain
#    are assumed to be unavailable.
#
#Default:
# dns_timeout 2 minutes

#  TAG: dns_defnames    on|off
#    Normally the RES_DEFNAMES resolver option is disabled
#    (see res_init(3)).  This prevents caches in a hierarchy
#    from interpreting single-component hostnames locally.  To allow
#    Squid to handle single-component names, enable this option.
#
#Default:
# dns_defnames off

#  TAG: dns_nameservers
#    Use this if you want to specify a list of DNS name servers
#    (IP addresses) to use instead of those given in your
#    /etc/resolv.conf file.
#    On Windows platforms, if no value is specified here or in
#    the /etc/resolv.conf file, the list of DNS name servers are
#    taken from the Windows registry, both static and dynamic DHCP
#    configurations are supported.
#
#    Example: dns_nameservers 10.0.0.1 192.172.0.4
#
#Default:
# none

#  TAG: hosts_file
#    Location of the host-local IP name-address associations
#    database. Most Operating Systems have such a file on different
#    default locations:
#    - Un*X & Linux:    /etc/hosts
#    - Windows NT/2000: %SystemRoot%\system32\drivers\etc\hosts
#               (%SystemRoot% value install default is c:\winnt)
#    - Windows XP/2003: %SystemRoot%\system32\drivers\etc\hosts
#               (%SystemRoot% value install default is c:\windows)
#    - Windows 9x/Me:   %windir%\hosts
#               (%windir% value is usually c:\windows)
#    - Cygwin:          /etc/hosts
#
#    The file contains newline-separated definitions, in the
#    form ip_address_in_dotted_form name [name ...] names are
#    whitespace-separated. Lines beginning with an hash (#)
#    character are comments.
#
#    The file is checked at startup and upon configuration.
#    If set to 'none', it won't be checked.
#    If append_domain is used, that domain will be added to
#    domain-local (i.e. not containing any dot character) host
#    definitions.
#
#Default:
# hosts_file /etc/hosts
#
hosts_file /etc/hosts

#  TAG: dns_testnames
#    The DNS tests exit as soon as the first site is successfully looked up
#
#    This test can be disabled with the -D command line option.
#
#Default:
# dns_testnames netscape.com internic.net nlanr.net microsoft.com

#  TAG: append_domain
#    Appends local domain name to hostnames without any dots in
#    them.  append_domain must begin with a period.
#
#    Be warned there are now Internet names with no dots in
#    them using only top-domain names, so setting this may
#    cause some Internet sites to become unavailable.
#
#Example:
# append_domain .yourdomain.com
#
#Default:
# none

#  TAG: ignore_unknown_nameservers
#    By default Squid checks that DNS responses are received
#    from the same IP addresses they are sent to.  If they
#    don't match, Squid ignores the response and writes a warning
#    message to cache.log.  You can allow responses from unknown
#    nameservers by setting this option to 'off'.
#
#Default:
# ignore_unknown_nameservers on

#  TAG: ipcache_size    (number of entries)
#  TAG: ipcache_low    (percent)
#  TAG: ipcache_high    (percent)
#    The size, low-, and high-water marks for the IP cache.
#
#Default:
# ipcache_size 1024
# ipcache_low 90
# ipcache_high 95

#  TAG: fqdncache_size    (number of entries)
#    Maximum number of FQDN cache entries.
#
#Default:
# fqdncache_size 1024


# MISCELLANEOUS
# -----------------------------------------------------------------------------

#  TAG: memory_pools    on|off
#    If set, Squid will keep pools of allocated (but unused) memory
#    available for future use.  If memory is a premium on your
#    system and you believe your malloc library outperforms Squid
#    routines, disable this.
#
#Default:
# memory_pools on

#  TAG: memory_pools_limit    (bytes)
#    Used only with memory_pools on:
#    memory_pools_limit 50 MB
#
#    If set to a non-zero value, Squid will keep at most the specified
#    limit of allocated (but unused) memory in memory pools. All free()
#    requests that exceed this limit will be handled by your malloc
#    library. Squid does not pre-allocate any memory, just safe-keeps
#    objects that otherwise would be free()d. Thus, it is safe to set
#    memory_pools_limit to a reasonably high value even if your
#    configuration will use less memory.
#
#    If set to zero, Squid will keep all memory it can. That is, there
#    will be no limit on the total amount of memory used for safe-keeping.
#
#    To disable memory allocation optimization, do not set
#    memory_pools_limit to 0. Set memory_pools to "off" instead.
#
#    An overhead for maintaining memory pools is not taken into account
#    when the limit is checked. This overhead is close to four bytes per
#    object kept. However, pools may actually _save_ memory because of
#    reduced memory thrashing in your malloc library.
#
#Default:
# memory_pools_limit 5 MB

#  TAG: forwarded_for    on|off
#    If set, Squid will include your system's IP address or name
#    in the HTTP requests it forwards.  By default it looks like
#    this:
#
#        X-Forwarded-For: 192.1.2.3
#
#    If you disable this, it will appear as
#
#        X-Forwarded-For: unknown
#
#Default:
# forwarded_for on

#  TAG: cachemgr_passwd
#    Specify passwords for cachemgr operations.
#
#    Usage: cachemgr_passwd password action action ...
#
#    Some valid actions are (see cache manager menu for a full list):
#        5min
#        60min
#        asndb
#        authenticator
#        cbdata
#        client_list
#        comm_incoming
#        config *
#        counters
#        delay
#        digest_stats
#        dns
#        events
#        filedescriptors
#        fqdncache
#        histograms
#        http_headers
#        info
#        io
#        ipcache
#        mem
#        menu
#        netdb
#        non_peers
#        objects
#        offline_toggle *
#        pconn
#        peer_select
#        reconfigure *
#        redirector
#        refresh
#        server_list
#        shutdown *
#        store_digest
#        storedir
#        utilization
#        via_headers
#        vm_objects
#
#    * Indicates actions which will not be performed without a
#      valid password, others can be performed if not listed here.
#
#    To disable an action, set the password to "disable".
#    To allow performing an action without a password, set the
#    password to "none".
#
#    Use the keyword "all" to set the same password for all actions.
#
#Example:
# cachemgr_passwd secret shutdown
# cachemgr_passwd lesssssssecret info stats/objects
# cachemgr_passwd disable all
#
#Default:
# none

#  TAG: client_db    on|off
#    If you want to disable collecting per-client statistics,
#    turn off client_db here.
#
#Default:
# client_db on

#  TAG: reload_into_ims    on|off
#    When you enable this option, client no-cache or ``reload''
#    requests will be changed to If-Modified-Since requests.
#    Doing this VIOLATES the HTTP standard.  Enabling this
#    feature could make you liable for problems which it
#    causes.
#
#    see also refresh_pattern for a more selective approach.
#
#Default:
# reload_into_ims off

#  TAG: maximum_single_addr_tries
#    This sets the maximum number of connection attempts for a
#    host that only has one address (for multiple-address hosts,
#    each address is tried once).
#
#    The default value is one attempt, the (not recommended)
#    maximum is 255 tries.  A warning message will be generated
#    if it is set to a value greater than ten.
#
#    Note: This is in addition to the request re-forwarding which
#    takes place if Squid fails to get a satisfying response.
#
#Default:
# maximum_single_addr_tries 1

#  TAG: retry_on_error
#    If set to on Squid will automatically retry requests when
#    receiving an error response. This is mainly useful if you
#    are in a complex cache hierarchy to work around access
#    control errors.
#
#Default:
# retry_on_error off

#  TAG: as_whois_server
#    WHOIS server to query for AS numbers.  NOTE: AS numbers are
#    queried only when Squid starts up, not for every request.
#
#Default:
# as_whois_server whois.ra.net
# as_whois_server whois.ra.net

#  TAG: offline_mode
#    Enable this option and Squid will never try to validate cached
#    objects.
#
#Default:
# offline_mode off

#  TAG: uri_whitespace
#    What to do with requests that have whitespace characters in the
#    URI.  Options:
#
#    strip:  The whitespace characters are stripped out of the URL.
#        This is the behavior recommended by RFC2396.
#    deny:   The request is denied.  The user receives an "Invalid
#        Request" message.
#    allow:  The request is allowed and the URI is not changed.  The
#        whitespace characters remain in the URI.  Note the
#        whitespace is passed to redirector processes if they
#        are in use.
#    encode:    The request is allowed and the whitespace characters are
#        encoded according to RFC1738.  This could be considered
#        a violation of the HTTP/1.1
#        RFC because proxies are not allowed to rewrite URI's.
#    chop:    The request is allowed and the URI is chopped at the
#        first whitespace.  This might also be considered a
#        violation.
#
#Default:
# uri_whitespace strip

#  TAG: coredump_dir
#    By default Squid leaves core files in the directory from where
#    it was started. If you set 'coredump_dir' to a directory
#    that exists, Squid will chdir() to that directory at startup
#    and coredump files will be left there.
#
#Default:
# coredump_dir none
#
# Leave coredumps in the first cache dir
coredump_dir /var/spool/squid

#  TAG: chroot
#    Use this to have Squid do a chroot() while initializing.  This
#    also causes Squid to fully drop root privileges after
#    initializing.  This means, for example, if you use a HTTP
#    port less than 1024 and try to reconfigure, you will may get an
#    error saying that Squid can not open the port.
#
#Default:
# none

#  TAG: balance_on_multiple_ip
#    Some load balancing servers based on round robin DNS have been
#    found not to preserve user session state across requests
#    to different IP addresses.
#
#    By default Squid rotates IP's per request. By disabling
#    this directive only connection failure triggers rotation.
#
#Default:
# balance_on_multiple_ip on

#  TAG: pipeline_prefetch
#    To boost the performance of pipelined requests to closer
#    match that of a non-proxied environment Squid can try to fetch
#    up to two requests in parallel from a pipeline.
#
#    Defaults to off for bandwidth management and access logging
#    reasons.
#
#Default:
# pipeline_prefetch off

#  TAG: high_response_time_warning    (msec)
#    If the one-minute median response time exceeds this value,
#    Squid prints a WARNING with debug level 0 to get the
#    administrators attention.  The value is in milliseconds.
#
#Default:
# high_response_time_warning 0

#  TAG: high_page_fault_warning
#    If the one-minute average page fault rate exceeds this
#    value, Squid prints a WARNING with debug level 0 to get
#    the administrators attention.  The value is in page faults
#    per second.
#
#Default:
# high_page_fault_warning 0

#  TAG: high_memory_warning
#    If the memory usage (as determined by mallinfo) exceeds
#    this amount, Squid prints a WARNING with debug level 0 to get
#    the administrators attention.
#
#Default:
# high_memory_warning 0 KB

#  TAG: sleep_after_fork    (microseconds)
#    When this is set to a non-zero value, the main Squid process
#    sleeps the specified number of microseconds after a fork()
#    system call. This sleep may help the situation where your
#    system reports fork() failures due to lack of (virtual)
#    memory. Note, however, if you have a lot of child
#    processes, these sleep delays will add up and your
#    Squid will not service requests for some amount of time
#    until all the child processes have been started.
#    On Windows value less then 1000 (1 milliseconds) are
#    rounded to 1000.
#
#Default:
# sleep_after_fork 0

#  TAG: zero_buffers    on|off
#    Squid by default will zero all buffers before using or reusing them.
#     Setting this to 'off' will result in fixed-sized temporary buffers
#    not being zero'ed. This may give a performance boost on certain
#    platforms but it may result in undefined behaviour at the present
#    time.
#
#Default:
# zero_buffers on

#  TAG: windows_ipaddrchangemonitor    on|off
#    On Windows Squid by default will monitor IP address changes and will 
#    reconfigure itself after any detected event. This is very useful for
#    proxies connected to internet with dial-up interfaces.
#    In some cases (a Proxy server acting as VPN gateway is one) it could be
#    desiderable to disable this behaviour setting this to 'off'.
#    Note: after changing this, Squid service must be restarted.
#
#Default:
# windows_ipaddrchangemonitor on
```

---

### Post by SlugSlug on 2010-12-08
that doesn't seem complete

are you able to attach the config file?

---

### Post by SeijiSensei on 2010-12-08
Squid cannot proxy HTTPS requests because it would look like a "man-in-the-middle" attack.  See [this posting](http://www.pubbs.net/200904/squid/50660-squid-users-squid-on-transparent-proxy-for-443-request.html) for details.

What you can do is write iptables rules that would block connections to port 443 on remote hosts.  For something like Facebook, with multiple IP addresses serving its pages, you'll need multiple entries or a subnet address.  Using the command "host facebook.com" I get 

facebook.com has address 69.63.181.12
facebook.com has address 69.63.189.11
facebook.com has address 69.63.189.16

so I could write iptables rules like this:

```

iptables -A OUTPUT -d 69.63.181.12 -j REJECT
iptables -A OUTPUT -d 69.63.189.11 -j REJECT
iptables -A OUTPUT -d 69.63.189.16 -j REJECT

```

and install them on the proxy router.  These block all connections to these addresses which, in case of Facebook, is probably what you want.  If you need to be a bit more discriminate and block only HTTPS connections, then use these rules instead:

```

iptables -A OUTPUT -d 69.63.181.12 -p tcp --dport 443 -j REJECT
iptables -A OUTPUT -d 69.63.189.11 -p tcp --dport 443 -j REJECT
iptables -A OUTPUT -d 69.63.189.16 -p tcp --dport 443 -j REJECT

```

---

### Post by SlugSlug on 2010-12-08
> **SeijiSensei said:**
> Squid cannot proxy HTTPS requests because it would look like a "man-in-the-middle" attack.  See [this posting]("http://www.pubbs.net/200904/squid/50660-squid-users-squid-on-transparent-proxy-for-443-request.html") for details.


the squid at our place manages it,

if I add a site to the blocked-sites acl I can no longer access it via https (tested facebook when came to this thread)

the firefox error it returns is connection refused by proxy (admittedly not the conection denined message (?!))

---

### Post by SeijiSensei on 2010-12-08
Hmm.  Looks like I was wrong after having glanced briefly at [http://www.squid-cache.org/Doc/config/https_port/](http://www.squid-cache.org/Doc/config/https_port/).  Now I'm intrigued enough to look into why this doesn't appear to be an MITM attack to the secure webserver.  As a guess, I suspect Squid provides a secure website to which the proxy connects, then Squid grabs the URL and sends it with its certificate.  I thought SSL protected against measures like this.  If not, then how do I know my ISP isn't intercepting all my supposedly secure traffic the same way?  Inquiring minds want to know.

**Update**: Looks like "[Squid-in-the-middle SSL Bump]("http://wiki.squid-cache.org/Features/SslBump")" is the answer.  The documentation includes this warning: "By default, most user agents will warn end-users about a possible man-in-the-middle attack."  Looks like [this feature](http://wiki.squid-cache.org/Features/DynamicSslCert) might be a way around that problem.  You have to create a Certificate Authority and install a certificate in all the browsers so they will trust the Squid host.  The second link gives details.

---

### Post by sipetron on 2010-12-08
i attached the squid configure file 
and about the iptable its didnt work too..... please help me with it and its the same with youtube :(

---

### Post by SeijiSensei on 2010-12-08
> **sipetron said:**
> i attached the squid configure file 
and about the iptable its didnt work too..... please help me with it and its the same with youtube :(

From what I've read now, configuring Squid to work with SSL is not for the faint of heart.  If you can understand the links I posted, then you can probably figure it out yourself.  If not, let's try other approaches like iptables.

You do understand that the rules are applied in order so it matters a lot where you place them.  Packets might match another rule before they reach the rules to block Facebook.  Let's start by seeing the results of "sudo iptables -L -nv" and "sudo iptables -t nat -L -nv".  Put them in code tags for easier reading, please.

---

### Post by sipetron on 2010-12-09
hassan@Linux:~$ sudo iptables -L -nv
Chain INPUT (policy DROP 4294 packets, 597K bytes)
 pkts bytes target     prot opt in     out     source               destination         
   51  3352 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
   48  5290 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
34694 4371K ACCEPT     all  --  eth0   *       0.0.0.0/0            0.0.0.0/0           
30909   27M ACCEPT     all  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           tcp multiport ports 10000 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
94167   16M ACCEPT     all  --  eth0   ppp0    0.0.0.0/0            0.0.0.0/0           
79443   16M ACCEPT     all  --  ppp0   eth0    0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 

Chain OUTPUT (policy ACCEPT 71889 packets, 34M bytes)
 pkts bytes target     prot opt in     out     source               destination         
hassan@Linux:~$ sudo iptables -t nat -L -nv
Chain PREROUTING (policy ACCEPT 16292 packets, 1685K bytes)
 pkts bytes target     prot opt in     out     source               destination         
 1816 94756 REDIRECT   tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 redir ports 3128 

Chain POSTROUTING (policy ACCEPT 108 packets, 25912 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 6934  568K MASQUERADE  all  --  *      ppp0    0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 1932 packets, 136K bytes)
 pkts bytes target     prot opt in     out     source               destination

---

### Post by SlugSlug on 2010-12-09
Not sure will have to check iptables later.. but I know we dnt have to accept any for of certificate for https it just connects as it should,

I'll try find out and post back

---

### Post by SeijiSensei on 2010-12-09
Try replacing OUTPUT with INPUT in the rules I gave you and place them right after the rule for the "lo" interface and above the ACCEPT rule for eth0.

---

### Post by sipetron on 2010-12-09
its the same my friend ,and i put it in the nat its the same

---

### Post by sipetron on 2010-12-09
[SlugSlug]("http://ubuntuforums.org/member.php?u=716956") if u can ping me on my mail 
[email]hassan.h.jaber@gmail.com[/email]

---

### Post by AlexanderDGreat on 2012-02-08
@SeijiSensei - The iptables configuration you suggested did not work for me, perhaps, Facebook is using many servers?

Can you help me block Facebook HTTPS, or just make them be able to LOG via Squid's Log files, from my understanding even HTTPS aren't log by SQUID.

Thanks for your help.

---

### Post by SeijiSensei on 2012-02-08
They have new servers: 

```
$ host -t a facebook.com
facebook.com has address 66.220.149.11
facebook.com has address 69.171.224.11
facebook.com has address 69.171.229.11
```

> Can you help me block Facebook HTTPS, or just make them be able to LOG via Squid's Log files, from my understanding even HTTPS aren't log by SQUID.

Did you read the articles I cited [above]("http://ubuntuforums.org/showpost.php?p=10215543&postcount=12")?  As I said, this isn't a task for the faint of heart.

---

### Post by AdmiralMorketh on 2012-02-13
im not exactly sure if this is the place to ask this but reading through the forums you guys have squid at least working i am a bit confused as to get my system running i have at this point a computer acting as my dhcp/gateway for any client on eth1 my internet connection is on eth0 i can access the internet from behind the computer the network map is:
CLIENTS ---> [ ETH1 -- squid -- ETH0 ] --> internet

Eth0: 192.168.1.X
Eth1: 192.168.2.X

so far iptables is just forwarding pakets back and forth using this script i found on a difrent forum:
```

echo -e "\n\nLoading simple rc.firewall-iptables version $FWVER..\n"
DEPMOD=/sbin/depmod
MODPROBE=/sbin/modprobe

EXTIF="eth0"
INTIF="eth1"
#INTIF2="eth0"
echo "   External Interface:  $EXTIF"
echo "   Internal Interface:  $INTIF"

#======================================================================
#== No editing beyond this line is required for initial MASQ testing ==
echo -en "   loading modules: "
echo "  - Verifying that all kernel modules are ok"
$DEPMOD -a
echo "----------------------------------------------------------------------"
echo -en "ip_tables, "
$MODPROBE ip_tables
echo -en "nf_conntrack, "
$MODPROBE nf_conntrack
echo -en "nf_conntrack_ftp, "
$MODPROBE nf_conntrack_ftp
echo -en "nf_conntrack_irc, "
$MODPROBE nf_conntrack_irc
echo -en "iptable_nat, "
$MODPROBE iptable_nat
echo -en "nf_nat_ftp, "
$MODPROBE nf_nat_ftp
echo "----------------------------------------------------------------------"
echo -e "   Done loading modules.\n"
echo "   Enabling forwarding.."
echo "1" > /proc/sys/net/ipv4/ip_forward
echo "   Enabling DynamicAddr.."
echo "1" > /proc/sys/net/ipv4/ip_dynaddr
echo "   Clearing any existing rules and setting default policy.."

iptables-restore <<-EOF
*nat
-A POSTROUTING -o "$EXTIF" -j MASQUERADE
COMMIT
*filter
:INPUT ACCEPT [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]
-A FORWARD -i "$EXTIF" -o "$INTIF" -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
-A FORWARD -i "$INTIF" -o "$EXTIF" -j ACCEPT
-A FORWARD -j LOG
COMMIT
EOF

echo -e "\nrc.firewall-iptables v$FWVER done.\n"

```ive been working with ubuntu for close to 3 years and so far never had the chance nor the reason to play with iptables as a result i am at a loss to even figure this one out. as soon as i tell squid to use Port Redirection it screws up the iptables and blocks everything from connecting as a result i'm not sure if iptables is to blame or if i have something screwy in my squid config so far i have added the lines:
```

acl localnet src 192.168.2.0-0.0.0.0/24
acl BadSites dstdomain "/etc/squid/restricted-sites.squid"

http_access allow localnet
http_access allow localhost
http_access deny BadSites
http_access deny all

```the file /etc/squid/restricted-sites.squid:
```
www.google.com
```as a test site it was the only thing i could think of at the time of building the server just to see if i could get it to block something
and then farther down in the tcp_outgoing_address section i have this:
```
tcp_outgoing_address 192.168.1.6
```and finaly in the NETWORK section i have:
```

http_port 192.168.2.1:3128 transparent

```I'm at the point of pulling my hair out in frustration at this problem. any ideas sugestions or help of any kind would be more then welcome ^_^ thanks in advance

---

