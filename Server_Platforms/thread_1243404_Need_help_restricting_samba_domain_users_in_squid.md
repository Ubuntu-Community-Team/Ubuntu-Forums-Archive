---
title: "Need help restricting samba domain users in squid"
date: 2009-08-18
forum: Server Platforms
---

### Post by Avinash.Rao on 2009-08-18
Hi, 

Ubuntu 8.04 Server 64-bit Edition
Samba 3.0.28a
Squid 2.6 stable18

Samba is configured as PDC and i have winxp clients logging to the domain.
I want to restrict these users from accessing the internet the whole day, i just want to give them access to internet only during 6:00-8:00PM everyday. How can i achieve this? 

I read the documentation and have configured squid for NTLM and tested.. but below is the error i am getting when i restart squid. 



 /etc/init.d/squid restart
 * Restarting Squid HTTP proxy squid
        2009/08/18 14:04:15| Invalid Proxy Auth ACL 'acl
AuthorizedUsers proxy_auth REQUIRED' because no authentication schemes
are fully configured.
FATAL: Bungled squid.conf line 39: acl AuthorizedUsers proxy_auth REQUIRED
Squid Cache (Version 2.6.STABLE18): Terminated abnormally.
                                                                        [fail]

squid.conf

root@sunbox:/var/log/squid# more /etc/squid/squid.conf
visible_hostname sunbox
hierarchy_stoplist cgi-bin ?
acl QUERY urlpath_regex cgi-bin \?
no_cache deny QUERY
hosts_file /etc/hosts
http_port 100.100.100.50:3128
refresh_pattern ^ftp: 1440 20% 10080
refresh_pattern ^gopher: 1440 0% 1440
refresh_pattern . 0 20% 4320
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 563
acl Safe_ports port 80                # http
acl Safe_ports port 21                # ftp
acl Safe_ports port 443 563           # https, snews
acl Safe_ports port 70                # gopher
acl Safe_ports port 210               # wais
acl Safe_ports port 1025-65535        # unregistered ports
acl Safe_ports port 280               # http-mgmt
acl Safe_ports port 488               # gss-http
acl Safe_ports port 591               # filemaker
acl Safe_ports port 631               # cups
acl Safe_ports port 777               # multiling http
acl Safe_ports port 901               # SWAT
acl Safe_ports port 993               # IMAP
acl Safe_ports port 587               # SMTP
acl Safe_ports port 22                # SSH
acl purge method PURGE
acl special_urls url_regex "/etc/squid/squid-noblock.acl"
acl extndeny url_regex -i "/etc/squid/blocks.files.acl"
acl malware_block_list url_regex -i "/etc/squid/malware_block_list.txt"
acl badurl url_regex -i teen orkut youtube sex mp3 mp4 exe
acl lan src 192.168.1.0 100.100.100.0/24
acl stud ident_regex babu
acl download method GET
acl CONNECT method CONNECT
acl AuthorizedUsers proxy_auth REQUIRED
cache_mem 100 MB
#redirect_program /usr/bin/squidGuard –c /etc/squid/squidGuard.conf
ident_lookup_access allow all
http_access deny all
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access allow special_urls
http_access deny extndeny download
http_access deny extndeny
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access deny badurl
http_access deny malware_block_list
deny_info [http://malware.hiperlinks.com.br/denied.shtml](http://malware.hiperlinks.com.br/denied.shtml) malware_block_list
http_access allow localhost
http_access allow lan
http_reply_access allow all
http_access allow AuthorizedUsers
http_access deny all
icp_access allow all
coredump_dir /var/spool/squid


auth_param ntlm program /usr/bin/ntlm_auth --helper-protocol=squid-2.5-ntlmssp
auth_param ntlm children 30
auth_param ntlm max_challenge_reuses 0
auth_param ntlm max_challenge_lifetime 2 minutes
# ntlm_auth from Samba 3 supports NTLM NEGOTIATE packet
auth_param ntlm use_ntlm_negotiate on

# warning: basic authentication sends passwords plaintext
# a network sniffer can and will discover passwords
auth_param basic program /usr/bin/ntlm_auth --helper-protocol=squid-2.5-basic
auth_param basic children 5
auth_param basic realm Squid proxy-caching web server
auth_param basic credentialsttl 2 hours


Thanks
Avinash

---

