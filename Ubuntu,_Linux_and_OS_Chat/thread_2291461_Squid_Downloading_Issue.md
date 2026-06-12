---
title: "Squid Downloading Issue"
date: 2015-08-20
forum: Ubuntu, Linux and OS Chat
---

### Post by kashif_khan on 2015-08-20
I 'm running LUSCA Squid and getting that whenever my client request for download any extension more then 50 MB or above, by using their browser (google chrome, safari, opera, mozilla).  There download stuck in between half the download, however when they tried to download the same file with the help of IDM or DAP, there download completed successfully...
 
Anyone suggest the Issue..
below is the linux script.
```

# HTTP Port for SQUID Service
http_port 8080 transparent
server_http11 on
 
# Cache Pee, for parent proxy if you ahve any, or ignore it.
#cache_peer x.x.x.x parent 8080 0
 
# Various Logs/files location
pid_filename /var/run/squid.pid
coredump_dir /var/spool/squid/
error_directory /usr/share/squid/errors/English
icon_directory /usr/share/squid/icons
mime_table /etc/squid/mime.conf
access_log daemon:/var/log/squid/access.log squid
cache_log /var/log/squid/cache.log
#debug_options ALL,1 22,3 11,2 #84,9
referer_log /var/log/squid/referer.log
cache_store_log none
store_dir_select_algorithm  round-robin
logfile_daemon /usr/lib/squid/logfile-daemon
logfile_rotate 1
 
# Cache Policy
cache_mem 5 GB
maximum_object_size_in_memory 2 MB
memory_replacement_policy heap GDSF
cache_replacement_policy heap LFUDA
 
minimum_object_size 0 KB
maximum_object_size 4 MB
cache_swap_low 93
cache_swap_high 95
 
# Cache Folder Path, using 5GB for test
cache_dir aufs /cache-1 38000 16 256
cache_dir aufs /cache-2 376000 16 256 
# ACL Section
acl all src all
acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8
acl localnet src 10.0.0.0/8            # RFC1918 possible internal network
#acl localnet src 172.16.0.0/12        # RFC1918 possible internal network
#acl localnet src 192.168.0.0/16        # RFC1918 possible internal network
#acl localnet src 125.165.92.1        # RFC1918 possible internal network
acl SSL_ports port 443
acl Safe_ports port 80                # http
acl Safe_ports port 21                # ftp
acl Safe_ports port 443                # https
acl Safe_ports port 70                # gopher
acl Safe_ports port 210                # wais
acl Safe_ports port 1025-65535        # unregistered ports
acl Safe_ports port 280                # http-mgmt
acl Safe_ports port 488                # gss-http
acl Safe_ports port 591                # filemaker
acl Safe_ports port 777                # multiling http
acl CONNECT method CONNECT
acl purge method PURGE
acl snmppublic snmp_community public
 
acl range dstdomain .windowsupdate.com
range_offset_limit 0 KB  
#===========================================================================
#    Loading Patch
acl DENYCACHE urlpath_regex \.(ini|ui|lst|inf|pak|ver|patch|md5|cfg|lst|list|rsc|log|conf|dbd|db)$
acl DENYCACHE urlpath_regex (notice.html|afs.dat|dat.asp|patchinfo.xml|version.list|iepngfix.htc|updates.txt|patchlist.txt)
acl DENYCACHE urlpath_regex (pointblank.css|login_form.css|form.css|noupdate.ui|ahn.ui|3n.mh)$
acl DENYCACHE urlpath_regex (Loader|gamenotice|sources|captcha|notice|reset)
no_cache deny DENYCACHE
 
range_offset_limit 1 MB !DENYCACHE
uri_whitespace strip
 
#===========================================================================
#    Rules to block few Advertising sites
acl ads url_regex -i .youtube\.com\/ad_frame?
acl ads url_regex -i .(s|s[0-90-9])\.youtube\.com
acl ads url_regex -i .googlesyndication\.com
acl ads url_regex -i .doubleclick\.net
acl ads url_regex -i ^http:\/\/googleads\.*
acl ads url_regex -i ^http:\/\/(ad|ads|ads[0-90-9]|ads\d|kad|a[b|d]|ad\d|adserver|adsbox)\.[a-z0-9]*\.[a-z][a-z]*
acl ads url_regex -i ^http:\/\/openx\.[a-z0-9]*\.[a-z][a-z]*
acl ads url_regex -i ^http:\/\/[a-z0-9]*\.openx\.net\/
acl ads url_regex -i ^http:\/\/[a-z0-9]*\.u-ad\.info\/
acl ads url_regex -i ^http:\/\/adserver\.bs\/
acl ads url_regex -i !^http:\/\/adf\.ly
http_access deny ads
http_reply_access deny ads
#deny_info [http://yoursite/yourad,htm](http://yoursite/yourad,htm) ads
#==== End Rules: Advertising ====
 
strip_query_terms off
 
acl yutub url_regex -i .*youtube\.com\/.*$
acl yutub url_regex -i .*youtu\.be\/.*$
logformat squid1 %{Referer}>h %ru
access_log /var/log/squid/yt.log squid1 yutub
 
# ==== Custom Option REWRITE ====
acl store_rewrite_list urlpath_regex \/(get_video\?|videodownload\?|videoplayback.*id)
 
acl store_rewrite_list urlpath_regex \.(mp2|mp3|mid|midi|mp[234]|wav|ram|ra|rm|au|3gp|m4r|m4a)\?
acl store_rewrite_list urlpath_regex \.(mpg|mpeg|mp4|m4v|mov|avi|asf|wmv|wma|dat|flv|swf)\?
acl store_rewrite_list urlpath_regex \.(jpeg|jpg|jpe|jp2|gif|tiff?|pcx|png|bmp|pic|ico)\?
acl store_rewrite_list urlpath_regex \.(chm|dll|doc|docx|xls|xlsx|ppt|pptx|pps|ppsx|mdb|mdbx)\?
acl store_rewrite_list urlpath_regex \.(txt|conf|cfm|psd|wmf|emf|vsd|pdf|rtf|odt)\?
acl store_rewrite_list urlpath_regex \.(class|jar|exe|gz|bz|bz2|tar|tgz|zip|gzip|arj|ace|bin|cab|msi|rar)\?
acl store_rewrite_list urlpath_regex \.(htm|html|mhtml|css|js)\?
 
acl store_rewrite_list_web url_regex ^http:\/\/([A-Za-z-]+[0-9]+)*\.[A-Za-z]*\.[A-Za-z]*
acl store_rewrite_list_web_CDN url_regex ^http:\/\/[a-z]+[0-9]\.google\.com doubleclick\.net
 
acl store_rewrite_list_path urlpath_regex \.(mp2|mp3|mid|midi|mp[234]|wav|ram|ra|rm|au|3gp|m4r|m4a)$
acl store_rewrite_list_path urlpath_regex \.(mpg|mpeg|mp4|m4v|mov|avi|asf|wmv|wma|dat|flv|swf)$
acl store_rewrite_list_path urlpath_regex \.(jpeg|jpg|jpe|jp2|gif|tiff?|pcx|png|bmp|pic|ico)$
acl store_rewrite_list_path urlpath_regex \.(chm|dll|doc|docx|xls|xlsx|ppt|pptx|pps|ppsx|mdb|mdbx)$
acl store_rewrite_list_path urlpath_regex \.(txt|conf|cfm|psd|wmf|emf|vsd|pdf|rtf|odt)$
acl store_rewrite_list_path urlpath_regex \.(class|jar|exe|gz|bz|bz2|tar|tgz|zip|gzip|arj|ace|bin|cab|msi|rar)$
acl store_rewrite_list_path urlpath_regex \.(htm|html|mhtml|css|js)$
 
acl getmethod method GET
 
storeurl_access deny !getmethod
#this is not related to youtube video its only for CDN pictures
storeurl_access allow store_rewrite_list_web_CDN
storeurl_access allow store_rewrite_list_web store_rewrite_list_path
storeurl_access allow store_rewrite_list
storeurl_access deny all
storeurl_rewrite_program /etc/squid/storeurl.pl
storeurl_rewrite_children 10
storeurl_rewrite_concurrency 40
# ==== End Custom Option REWRITE ====
 
#===========================================================================
#    Custom Option REFRESH PATTERN
#===========================================================================
refresh_pattern (get_video\?|videoplayback\?|videodownload\?|\.flv\?|\.fid\?) 43200 99% 43200 override-expire ignore-reload ignore-must-revalidate ignore-private
refresh_pattern -i (get_video\?|videoplayback\?|videodownload\?) 5259487 999% 5259487 override-expire ignore-reload reload-into-ims ignore-no-cache ignore-private
# -- refresh pattern for specific sites -- #
refresh_pattern ^[http://*.jobstreet.com.*/.*](http://*.jobstreet.com.*/.*) 720 100% 10080 override-expire override-lastmod ignore-no-cache
refresh_pattern ^[http://*.indowebster.com.*/.*](http://*.indowebster.com.*/.*) 720 100% 10080 override-expire override-lastmod reload-into-ims ignore-reload ignore-no-cache ignore-auth
refresh_pattern ^[http://*.21cineplex.*/.*](http://*.21cineplex.*/.*) 720 100% 10080 override-expire override-lastmod reload-into-ims ignore-reload ignore-no-cache ignore-auth
refresh_pattern ^[http://*.atmajaya.*/.*](http://*.atmajaya.*/.*) 720 100% 10080 override-expire ignore-no-cache ignore-auth
refresh_pattern ^[http://*.kompas.*/.*](http://*.kompas.*/.*) 720 100% 10080 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-auth
refresh_pattern ^[http://*.theinquirer.*/.*](http://*.theinquirer.*/.*) 720 100% 10080 override-expire ignore-no-cache ignore-auth
refresh_pattern ^[http://*.blogspot.com/.*](http://*.blogspot.com/.*) 720 100% 10080 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-auth
refresh_pattern ^[http://*.wordpress.com/.*](http://*.wordpress.com/.*) 720 100% 10080 override-expire override-lastmod reload-into-ims ignore-no-cache
refresh_pattern ^[http://*.photobucket.com/.*](http://*.photobucket.com/.*) 720 100% 10080 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-auth
refresh_pattern ^[http://*.tinypic.com/.*](http://*.tinypic.com/.*) 720 100% 10080 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-auth
refresh_pattern ^[http://*.imageshack.us/.*](http://*.imageshack.us/.*) 720 100% 10080 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-auth
refresh_pattern ^[http://*.kaskus.*/.*](http://*.kaskus.*/.*) 720 100% 28800 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-auth
refresh_pattern ^[http://www.kaskus.com/.*](http://www.kaskus.com/.*) 720 100% 28800 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-auth
refresh_pattern ^[http://*.detik.*/.*](http://*.detik.*/.*) 720 50% 2880 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-auth
refresh_pattern ^[http://*.detiknews.*/*.*](http://*.detiknews.*/*.*) 720 50% 2880 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-auth
refresh_pattern ^[http://video.liputan6.com/.*](http://video.liputan6.com/.*) 720 100% 10080 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-auth
refresh_pattern ^[http://static.liputan6.com/.*](http://static.liputan6.com/.*) 720 100% 10080 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-auth
refresh_pattern ^[http://*.friendster.com/.*](http://*.friendster.com/.*) 720 100% 10080 override-expire override-lastmod ignore-no-cache ignore-auth
refresh_pattern ^[http://*.facebook.com/.*](http://*.facebook.com/.*) 720 100% 10080 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-auth
refresh_pattern ^[http://apps.facebook.com/.*](http://apps.facebook.com/.*) 720 100% 10080 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-auth
refresh_pattern ^[http://*.fbcdn.net/.*](http://*.fbcdn.net/.*) 720 100% 10080 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-auth
refresh_pattern ^[http://profile.ak.fbcdn.net/.*](http://profile.ak.fbcdn.net/.*) 720 100% 10080 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-auth
refresh_pattern ^[http://static.playspoon.com/.*](http://static.playspoon.com/.*) 720 100% 10080 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-auth
refresh_pattern ^[http://cooking.game.playspoon.com/.*](http://cooking.game.playspoon.com/.*) 720 100% 10080 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-auth
refresh_pattern -i http://[^a-z\.]*onemanga\.com/? 720 80% 10080 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-auth
refresh_pattern ^[http://media?.onemanga.com/.*](http://media?.onemanga.com/.*) 720 80% 10080 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-auth
refresh_pattern ^[http://*.yahoo.com/.*](http://*.yahoo.com/.*) 720 80% 10080 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-auth
refresh_pattern ^[http://*.google.com/.*](http://*.google.com/.*) 720 80% 10080 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-auth
refresh_pattern ^[http://*.forummikrotik.com/.*](http://*.forummikrotik.com/.*) 720 80% 10080 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-auth
refresh_pattern ^[http://*.linux.or.id/.*](http://*.linux.or.id/.*) 720 100% 10080 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-auth
# -- refresh pattern for extension -- #
refresh_pattern -i \.(mp2|mp3|mid|midi|mp[234]|wav|ram|ra|rm|au|3gp|m4r|m4a)(\?.*|$) 5259487 999% 5259487 override-expire ignore-reload reload-into-ims ignore-no-cache ignore-private
refresh_pattern -i \.(mpg|mpeg|mp4|m4v|mov|avi|asf|wmv|wma|dat|flv|swf)(\?.*|$) 5259487 999% 5259487 override-expire ignore-reload reload-into-ims ignore-no-cache ignore-private
refresh_pattern -i \.(jpeg|jpg|jpe|jp2|gif|tiff?|pcx|png|bmp|pic|ico)(\?.*|$) 5259487 999% 5259487 override-expire ignore-reload reload-into-ims ignore-no-cache ignore-private
refresh_pattern -i \.(chm|dll|doc|docx|xls|xlsx|ppt|pptx|pps|ppsx|mdb|mdbx)(\?.*|$) 5259487 999% 5259487 override-expire ignore-reload reload-into-ims ignore-no-cache ignore-private
refresh_pattern -i \.(txt|conf|cfm|psd|wmf|emf|vsd|pdf|rtf|odt)(\?.*|$) 5259487 999% 5259487 override-expire ignore-reload reload-into-ims ignore-no-cache ignore-private
refresh_pattern -i \.(class|jar|exe|gz|bz|bz2|tar|tgz|zip|gzip|arj|ace|bin|cab|msi|rar)(\?.*|$) 5259487 999% 5259487 override-expire ignore-reload reload-into-ims ignore-no-cache ignore-private
refresh_pattern -i \.(htm|html|mhtml|css|js)(\?.*|$) 1440 90% 86400 override-expire ignore-reload reload-into-ims
#===========================================================================
refresh_pattern -i (/cgi-bin/|\?) 0 0% 0
refresh_pattern ^gopher: 1440 0% 1440
refresh_pattern ^ftp: 10080 95% 10080 override-lastmod reload-into-ims
refresh_pattern . 0 20% 10080 override-lastmod reload-into-ims
 
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
 
http_access allow localnet
http_access allow all
http_access deny all
 
icp_access allow localnet
icp_access deny all
icp_port 0
 
buffered_logs on
 
acl shoutcast rep_header X-HTTP09-First-Line ^ICY.[0-9]
upgrade_http0.9 deny shoutcast
 
acl apache rep_header Server ^Apache
broken_vary_encoding allow apache
 
forwarded_for off
header_access From deny all
header_access Server deny all
header_access Link deny all
header_access Via deny all
header_access X-Forwarded-For deny all
httpd_suppress_version_string on
 
shutdown_lifetime 10 seconds
 
snmp_port 3401
snmp_access allow snmppublic all
dns_timeout 1 minutes
 
dns_nameservers 202.141.224.34 202.125.132.154 8.8.8.8 
 
fqdncache_size 5000    #16384
ipcache_size 5000    #16384
ipcache_low 98
ipcache_high 99
log_fqdn off
log_icp_queries off
memory_pools off
 
maximum_single_addr_tries 2
retry_on_error on
 
icp_hit_stale on
 
strip_query_terms off
 
query_icmp on
reload_into_ims on
emulate_httpd_log off
negative_ttl 0 seconds
pipeline_prefetch on
vary_ignore_expire on
half_closed_clients off
high_page_fault_warning 2
nonhierarchical_direct on
prefer_direct off
cache_mgr webmaster
cache_effective_user proxy
cache_effective_group proxy
visible_hostname proxy.skynet
unique_hostname kashif_skynet
cachemgr_passwd none all
client_db on
max_filedescriptors 8192
 
# ZPH config Marking Cache Hit, so cached contents can be delivered at full lan speed via MT
zph_mode tos
zph_local 0x30
zph_parent 0
zph_option 136

```

---

