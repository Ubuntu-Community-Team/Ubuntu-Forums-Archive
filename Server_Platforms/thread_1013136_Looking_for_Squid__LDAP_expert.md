---
title: "Looking for Squid / LDAP expert"
date: 2008-12-16
forum: Server Platforms
---

### Post by NetworkGuy on 2008-12-16
I'm setting up a squid server that will look at a Windows AD server for authentication.

I currently have everything working using the ldap_auth and the squid_ldap_group programs.  I can setup my test user and sign in or not sign in depending on group membership.  This is where my problem falls.

If I put the user in the correct group and sign in.  All is well.  If I then take the user out of the correct group and try to sign in again... it works?? :-k

It appears that I must restart the squid server for the new settings to take effect.  I have listed the credentialsttl at 5 minutes but that didn't fix my problem.   

What must be added/changed/deleted to allow this to work as designed?

Squid.conf shown below for reference.

```
# NETWORK OPTIONS
# -----------------------------------------------------------------------------
http_port 127.0.0.1:3128
# http_port 172.16.4.4:3128

# OPTIONS WHICH AFFECT THE CACHE SIZE
# -----------------------------------------------------------------------------

cache_mem 512 MB
maximum_object_size 400 MB
minimum_object_size 0 KB
maximum_object_size_in_memory 64 KB

# LOGFILE PATHNAMES AND CACHE DIRECTORIES
# -----------------------------------------------------------------------------

cache_dir ufs /var/spool/squid 2000 16 256
cache_access_log /var/log/squid/access.log
cache_log /var/log/squid/cache.log
cache_store_log /var/log/squid/store.log


# OPTIONS FOR EXTERNAL SUPPORT PROGRAMS
# -----------------------------------------------------------------------------

ftp_user wwwuser@foobar.com
ftp_list_width 50
ftp_passive on

auth_param basic program /usr/lib/squid/ldap_auth -R                      \
   -b "dc=foobar,dc=local"                                               \
   -D "cn=Administrator,cn=Users,dc=foobar,dc=local"                     \
   -w "foobarspassword"                                                          \
   -f sAMAccountName=%s                                                   \
   -h 172.16.4.60
auth_param basic children 5
auth_param basic realm foobar
auth_param basic credentialsttl 5 minutes
 
# OPTIONS FOR TUNING THE CACHE
# -----------------------------------------------------------------------------

  request_header_max_size 8 KB


# TIMEOUTS
# -----------------------------------------------------------------------------


# ACCESS CONTROLS
# -----------------------------------------------------------------------------

external_acl_type InetGroup %LOGIN /usr/lib/squid/squid_ldap_group -R       \
    -b "dc=foobar,dc=local"                                                \
    -D "cn=Administrator,cn=Users,dc=foobar,dc=local"                      \
    -w "foobarspassword"                                                           \
    -f "(&(objectclass=person)(sAMAccountName=%v)(memberof=cn=%a,           \
        ou=foobar Groups,dc=foobar,dc=local))"                            \
    -h 172.16.4.60  

acl localnet proxy_auth REQUIRED src 172.16.0.0/12

acl unrestrictedusers external InetGroup Sales_Internet

acl bypassurl dstdomain "/etc/squid/bypasslist"
acl bypassip dst "/etc/squid/bypasslist.ip"
acl denyall dst "/etc/squid/denyall"
#acl never-cache dstdomain "/etc/squid/nevercache"
acl FTP proto FTP

#Recommended minimum configuration:
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443 563 17780
acl Safe_ports port 80		# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443 563	# https, snews
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl Safe_ports port 592         # Highland Tank Charts
acl CONNECT method CONNECT

http_access allow manager localhost
http_access deny manager
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access deny to_localhost
http_access deny localhost denyall
http_access allow localhost bypassurl
http_access allow localhost bypassip
http_access allow unrestrictedusers
# http_access allow localhost
http_access deny all

http_reply_access allow all

#  reply_header_max_size 2 KB


# ADMINISTRATIVE PARAMETERS
# -----------------------------------------------------------------------------

cache_mgr NPHelpDesk@foobar.com
# cache_effective_user nobody
# cache_effective_group nobody
visible_hostname Proxy-Sales.int.foobar.local


# OPTIONS FOR THE CACHE REGISTRATION SERVICE
# -----------------------------------------------------------------------------


# HTTPD-ACCELERATOR OPTIONS
# -----------------------------------------------------------------------------


# MISCELLANEOUS
# -----------------------------------------------------------------------------

  dns_testnames internic.net 

logfile_rotate 6
memory_pools on
memory_pools_limit 50 MB
forwarded_for off
#  always_direct allow never-cache
always_direct allow FTP

```

---

### Post by koenn on 2008-12-16
it's not unusual for group membership to be cached so that at a next sign in, the number of LDAP look-ups can be reduced because the cached membership is assumed to still be valid.

Found some comments that seem to indicate this might also be the case for squid when using LDAP authentication:

ldap_auth_cache_ttl

	The number of seconds a checked ldap username/password/group combination 
	remains cached (default 3600). If a wrong password is given for a cached 
	user, the user gets removed from the username/password/group cache forcing
	a revalidation.


[http://group-ldap-auth.sourceforge.net/squid/group_ldap_auth/index.html](http://group-ldap-auth.sourceforge.net/squid/group_ldap_auth/index.html)

maybe check if ldap_auth_cache_ttl or something similar is mentioned in the squid documentation, and whether you can check it (it could be a compile-time option with a different name in the config file)

---

