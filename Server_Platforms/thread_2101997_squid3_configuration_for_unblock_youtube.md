---
title: "squid3 configuration for unblock youtube"
date: 2013-01-06
forum: Server Platforms
---

### Post by jibon_24 on 2013-01-06
Hello everyone,
I have installed squid3  proxy cache server on my VPS using ubuntu 12.04. Recently my ISP has blocked youtube access for my mobile broadband internet connection that's why I am trying use squid proxy to access youtube. But I can access all other site but not youtube :(. Here is my squid configuration file:
```

acl QUERY urlpath_regex -i cgi-bin ? .php$ .asp$ .shtml$ .cfm$ .cfml$ .phtml$ .php3$ localhost
acl all src
acl localnet src 10.0.0.0/8
acl localnet src 192.168.1.0/24 # Your network here
acl localhost src 127.0.0.1/32
acl safeports port 21 70 80 210 280 443 488 563 591 631 777 901 81 3128 1025-65535
acl sslports port 443 563 81 2087 10000
acl manager proto cache_object
acl purge method PURGE
acl connect method CONNECT
acl ym dstdomain .messenger.yahoo.com .psq.yahoo.com
acl ym dstdomain .us.il.yimg.com .msg.yahoo.com .pager.yahoo.com
acl ym dstdomain .rareedge.com .ytunnelpro.com .chat.yahoo.com
acl ym dstdomain .voice.yahoo.com
acl ymregex url_regex yupdater.yim ymsgr myspaceim
#
http_access deny ym
http_access deny ymregex
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !safeports
http_access deny CONNECT !sslports
http_access allow localhost
http_access allow localnet
http_access allow all
#
# NETWORK OPTIONS
# —————
#
http_port 3128
#
# OPTIONS WHICH AFFECT THE CACHE SIZE
# ==============================
#
cache_mem 8 MB
maximum_object_size_in_memory 32 KB
memory_replacement_policy heap GDSF
cache_replacement_policy heap LFUDA
cache_dir aufs /home/cache 10000 14 256
maximum_object_size 128000 KB
cache_swap_low 95
cache_swap_high 99
#
# LOGFILE PATHNAMES AND CACHE DIRECTORIES
# ==================================
#
access_log /var/log/squid3/access.log
cache_log /cache/cache.log
#cache_log /dev/null
cache_store_log none
logfile_rotate 5
log_icp_queries off
#
# OPTIONS FOR TUNING THE CACHE
# ========================
#
cache deny QUERY
refresh_pattern ^ftp: 1440 20% 10080 reload-into-ims
refresh_pattern ^gopher: 1440 0% 1440
refresh_pattern -i .(gif|png|jp?g|ico|bmp|tiff?)$ 10080 95% 43200 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-private
refresh_pattern -i .(rpm|cab|deb|exe|msi|msu|zip|tar|xz|bz|bz2|lzma|gz|tgz|rar|bin|7z|doc?|xls?|ppt?|pdf|nth|psd|sis)$ 10080 90% 43200 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-private
refresh_pattern -i .(avi|iso|wav|mid|mp?|mpeg|mov|3gp|wm?|swf|flv|x-flv|axd)$ 43200 95% 432000 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-private
refresh_pattern -i .(html|htm|css|js)$ 1440 75% 40320
refresh_pattern -i .index.(html|htm)$ 0 75% 10080
refresh_pattern -i (/cgi-bin/|?) 0 0% 0
refresh_pattern . 1440 90% 10080
dns_v4_first on
#
quick_abort_min 0 KB
quick_abort_max 0 KB
quick_abort_pct 100
store_avg_object_size 13 KB
#
# HTTP OPTIONS
# ===========
vary_ignore_expire on
#
# ANONIMITY OPTIONS
# ===============
#
request_header_access From deny all
request_header_access Server deny all
request_header_access Link deny all
request_header_access Via deny all
request_header_access X-Forwarded-For deny all
#
# TIMEOUTS
# =======
#
forward_timeout 240 second
connect_timeout 30 second
peer_connect_timeout 5 second
read_timeout 600 second
request_timeout 60 second
shutdown_lifetime 10 second
#
# ADMINISTRATIVE PARAMETERS
# =====================
#
cache_mgr ninja
cache_effective_user proxy
cache_effective_group proxy
httpd_suppress_version_string on
visible_hostname ninja
#
ftp_list_width 32
ftp_passive on
ftp_sanitycheck on
#
# DNS OPTIONS
# ==========
#
dns_timeout 10 seconds
dns_nameservers 208.67.222.222 208.67.220.220 
#
# MISCELLANEOUS
# ===========
#
memory_pools off
client_db off
reload_into_ims on
coredump_dir /cache
pipeline_prefetch on
offline_mode off
#
#Marking ZPH
#==========
zph_mode tos
zph_local 0x04
zph_parent 0
zph_option 136
### END CONFIGURATION ###
```Anyone can help me please so that I can access youtube with squid. Thanks in advance :p

---

### Post by jibon_24 on 2013-01-06
No one to help me please :( :(

---

### Post by SeijiSensei on 2013-01-07
Look through /var/log/squid3/access.log and find connections to YouTube.  What do they report?  You might browse the error log for the same period.  Logs are always the first step when diagnosing problems like these.

---

### Post by jibon_24 on 2013-01-07
Hi, [SeijiSensei]("http://ubuntuforums.org/member.php?u=698195") thanks a lot for your reply. Here is the squid log for youtube. Please help me.
> 1357416555.319    147 202.134.13.130 TCP_MISS/301 279 GET [http://youtube.com/](http://youtube.com/) - DIRECT/173.194.37.130 text/plain

---

### Post by sandyd on 2013-01-07
> **jibon_24 said:**
> Hello everyone,
I have installed squid3  proxy cache server on my VPS using ubuntu 12.04. Recently my ISP has blocked youtube access for my mobile broadband internet connection that's why I am trying use squid proxy to access youtube. But I can access all other site but not youtube :(. Here is my squid configuration file:
```

acl QUERY urlpath_regex -i cgi-bin ? .php$ .asp$ .shtml$ .cfm$ .cfml$ .phtml$ .php3$ localhost
acl all src
acl localnet src 10.0.0.0/8
acl localnet src 192.168.1.0/24 # Your network here
acl localhost src 127.0.0.1/32
acl safeports port 21 70 80 210 280 443 488 563 591 631 777 901 81 3128 1025-65535
acl sslports port 443 563 81 2087 10000
acl manager proto cache_object
acl purge method PURGE
acl connect method CONNECT
acl ym dstdomain .messenger.yahoo.com .psq.yahoo.com
acl ym dstdomain .us.il.yimg.com .msg.yahoo.com .pager.yahoo.com
acl ym dstdomain .rareedge.com .ytunnelpro.com .chat.yahoo.com
acl ym dstdomain .voice.yahoo.com
acl ymregex url_regex yupdater.yim ymsgr myspaceim
#
http_access deny ym
http_access deny ymregex
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !safeports
http_access deny CONNECT !sslports
http_access allow localhost
http_access allow localnet
http_access allow all
#
# NETWORK OPTIONS
# —————
#
http_port 3128
#
# OPTIONS WHICH AFFECT THE CACHE SIZE
# ==============================
#
cache_mem 8 MB
maximum_object_size_in_memory 32 KB
memory_replacement_policy heap GDSF
cache_replacement_policy heap LFUDA
cache_dir aufs /home/cache 10000 14 256
maximum_object_size 128000 KB
cache_swap_low 95
cache_swap_high 99
#
# LOGFILE PATHNAMES AND CACHE DIRECTORIES
# ==================================
#
access_log /var/log/squid3/access.log
cache_log /cache/cache.log
#cache_log /dev/null
cache_store_log none
logfile_rotate 5
log_icp_queries off
#
# OPTIONS FOR TUNING THE CACHE
# ========================
#
cache deny QUERY
refresh_pattern ^ftp: 1440 20% 10080 reload-into-ims
refresh_pattern ^gopher: 1440 0% 1440
refresh_pattern -i .(gif|png|jp?g|ico|bmp|tiff?)$ 10080 95% 43200 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-private
refresh_pattern -i .(rpm|cab|deb|exe|msi|msu|zip|tar|xz|bz|bz2|lzma|gz|tgz|rar|bin|7z|doc?|xls?|ppt?|pdf|nth|psd|sis)$ 10080 90% 43200 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-private
refresh_pattern -i .(avi|iso|wav|mid|mp?|mpeg|mov|3gp|wm?|swf|flv|x-flv|axd)$ 43200 95% 432000 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-private
refresh_pattern -i .(html|htm|css|js)$ 1440 75% 40320
refresh_pattern -i .index.(html|htm)$ 0 75% 10080
refresh_pattern -i (/cgi-bin/|?) 0 0% 0
refresh_pattern . 1440 90% 10080
dns_v4_first on
#
quick_abort_min 0 KB
quick_abort_max 0 KB
quick_abort_pct 100
store_avg_object_size 13 KB
#
# HTTP OPTIONS
# ===========
vary_ignore_expire on
#
# ANONIMITY OPTIONS
# ===============
#
request_header_access From deny all
request_header_access Server deny all
request_header_access Link deny all
request_header_access Via deny all
request_header_access X-Forwarded-For deny all
#
# TIMEOUTS
# =======
#
forward_timeout 240 second
connect_timeout 30 second
peer_connect_timeout 5 second
read_timeout 600 second
request_timeout 60 second
shutdown_lifetime 10 second
#
# ADMINISTRATIVE PARAMETERS
# =====================
#
cache_mgr ninja
cache_effective_user proxy
cache_effective_group proxy
httpd_suppress_version_string on
visible_hostname ninja
#
ftp_list_width 32
ftp_passive on
ftp_sanitycheck on
#
# DNS OPTIONS
# ==========
#
dns_timeout 10 seconds
dns_nameservers 208.67.222.222 208.67.220.220 
#
# MISCELLANEOUS
# ===========
#
memory_pools off
client_db off
reload_into_ims on
coredump_dir /cache
pipeline_prefetch on
offline_mode off
#
#Marking ZPH
#==========
zph_mode tos
zph_local 0x04
zph_parent 0
zph_option 136
### END CONFIGURATION ###
```Anyone can help me please so that I can access youtube with squid. Thanks in advance :p
Is your ISP blocking YouTube via DNS as well?
If yes, you also need to setup DNS overrides.

---

### Post by jibon_24 on 2013-01-07
Thanks a lot for your answer.
> Is your ISP blocking YouTube via DNS as well?

I think so. I think they disabled all the IP addresses. I tried with https but failed. 
> If yes, you also need to setup DNS overrides
How can I do that ? I am have configured squid with opendns nameserver. Thanks in advance

---

### Post by sandyd on 2013-01-07
Your device still uses your ISP's DNS nameservers, so the DNS data is not going through Squid, but your ISP's DNS nameservers. As a result, youtube is still blocked

---

### Post by SeijiSensei on 2013-01-07
I'm confused.  I thought your regular connection was filtered so you were using a virtual machine out on the Internet to run your proxy.  If you're running a proxy on a machine that is also filtered by your ISP, I don't see why you would think that should help.

Try this.  On the machine where squid is installed, run 

```
host youtube.com
```

and see what you get.  Then try

```
host youtube.com 8.8.8.8
```

and see if you get a different result.  That uses Google's DNS servers to resolve youtube.com.  You should get a bunch of addresses with 74.125.228 as the prefix.  The address that squid used for YouTube, 173.194.37.130, returns the Google home page when opened with a browser.

If the command that uses Google's DNS server works correctly, then edit /etc/resolv.conf on the proxy server to make 8.8.8.8 your primary nameserver.

---

### Post by jibon_24 on 2013-01-08
Thanks a lot for your answer. > **SeijiSensei said:**
> 
Try this.  On the machine where squid is installed, run 

```
host youtube.com
```
Result 
```
youtube.com has address 173.194.37.133
youtube.com has address 173.194.37.142
youtube.com has address 173.194.37.136
youtube.com has address 173.194.37.130
youtube.com has address 173.194.37.132
youtube.com has address 173.194.37.128
youtube.com has address 173.194.37.134
youtube.com has address 173.194.37.129
youtube.com has address 173.194.37.131
youtube.com has address 173.194.37.137
youtube.com has address 173.194.37.135
youtube.com has IPv6 address 2607:f8b0:400c:c01::5d
youtube.com mail is handled by 50 alt4.aspmx.l.google.com.
youtube.com mail is handled by 10 aspmx.l.google.com.
youtube.com mail is handled by 40 alt3.aspmx.l.google.com.
youtube.com mail is handled by 30 alt2.aspmx.l.google.com.
youtube.com mail is handled by 20 alt1.aspmx.l.google.com.

```

> **SeijiSensei said:**
> 
Then try

```
host youtube.com 8.8.8.8
```
Result:
```
Using domain server:
Name: 8.8.8.8
Address: 8.8.8.8#53
Aliases: 

youtube.com has address 173.194.37.133
youtube.com has address 173.194.37.142
youtube.com has address 173.194.37.136
youtube.com has address 173.194.37.130
youtube.com has address 173.194.37.132
youtube.com has address 173.194.37.128
youtube.com has address 173.194.37.134
youtube.com has address 173.194.37.129
youtube.com has address 173.194.37.131
youtube.com has address 173.194.37.137
youtube.com has address 173.194.37.135
youtube.com has IPv6 address 2607:f8b0:400c:c01::5d
youtube.com mail is handled by 50 alt4.aspmx.l.google.com.
youtube.com mail is handled by 10 aspmx.l.google.com.
youtube.com mail is handled by 40 alt3.aspmx.l.google.com.
youtube.com mail is handled by 30 alt2.aspmx.l.google.com.
youtube.com mail is handled by 20 alt1.aspmx.l.google.com.

```
I use 173.194.37.130 from my browser & I can see google home page & added 8.8.8.8 in  /etc/resolv.conf on the proxy server of my VPS but when I try to access youtube again same problem. ```
The connection to the server was reset while the page was loading.
```

---

### Post by SeijiSensei on 2013-01-08
It appears that your provider is grabbing all DNS requests and pushing them through their server.  Otherwise you should have seen:

```

youtube.com has address 74.125.224.195
youtube.com has address 74.125.224.201
youtube.com has address 74.125.224.192
youtube.com has address 74.125.224.196
youtube.com has address 74.125.224.197
youtube.com has address 74.125.224.193
youtube.com has address 74.125.224.199
youtube.com has address 74.125.224.194
youtube.com has address 74.125.224.198
youtube.com has address 74.125.224.206
youtube.com has address 74.125.224.200

```

when you queried the 8.8.8.8 server.

---

### Post by sandyd on 2013-01-08
What are you using to access the internet with?
You can add custom entries in /etc/hosts to override your provider's DNS

---

### Post by jibon_24 on 2013-01-09
Thank you  [SeijiSensei]("http://ubuntuforums.org/member.php?u=698195"). What should I do then ? Is there any way ?

Thank you [[COLOR=#DD4814]**sandyd**[/COLOR]]("http://ubuntuforums.org/member.php?u=717412") too.  I am using mobile broadband
 > You can add custom entries in /etc/hosts to override your provider's DNS
What should I write there ?

---

### Post by sandyd on 2013-01-09
> **jibon_24 said:**
> Thank you  [SeijiSensei]("http://ubuntuforums.org/member.php?u=698195"). What should I do then ? Is there any way ?

Thank you [[COLOR=#DD4814]**sandyd**[/COLOR]]("http://ubuntuforums.org/member.php?u=717412") too.  I am using mobile broadband
 
What should I write there ?

My apologies - I meant what device you are using to connect (i.e. laptop, phone, .etc .etc)

---

### Post by jibon_24 on 2013-01-09
> My apologies - I meant what device you are using to connect (i.e. laptop, phone, .etc .etc)
It's OK [[COLOR=#DD4814]**sandyd**[/COLOR]]("http://ubuntuforums.org/member.php?u=717412") :). Thanks for your reply. I am using laptop with modem connection. Not only modem but also broadband connection has same problem. Actually Government blocked youtube :(

---

### Post by 2fast4youbr on 2013-04-30
hi [**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195")[COLOR=#000000] ,

I was wondering, do you know if there is a logfile with more info then acces.log / squid.log ? 

in my access.log I only have TCP_MISS, i wanto to know why Squid is not caching anything...

cheers

[/COLOR]

---

### Post by matt_symes on 2013-05-01
> Actually Government blocked youtube :sad:

This is slipping into dangerous territory for the Ubuntu forums. Thread closed.

@[**[COLOR=#000000]2fast4youbr[/COLOR]**]("http://ubuntuforums.org/member.php?u=1816345"). Please start a new thread for your question.

---

