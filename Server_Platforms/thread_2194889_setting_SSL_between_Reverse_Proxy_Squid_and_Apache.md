---
title: "setting SSL between Reverse Proxy Squid and Apache Web server"
date: 2013-12-21
forum: Server Platforms
---

### Post by isagarran2 on 2013-12-21
SQUID 3.3.11
Apache 
Hello ,
I post this subject in "server Platforms". Usualluy , i request help in order to recover my ubuntu from  graphics os network problems ... but not today :)
As you always answer to me, I'm quite confident that You could help me.
Using HTTP on all the chains, all ressources are reachable and all works fine. If i Set HTTPS from the browser to the reverse Proxy, all works fine. But ...
I'm trying to configure SSL between A Squid Reverse proxy that is in front of an apache web server.
Now if I'm trying to enable SSL between RP to Apache, I got the following errors in cache.log
[HTML]
2013/12/21 12:00:11 kid1| fwdNegotiateSSL: Error negotiating SSL connection on FD 15: error:00000000:lib(0):func(0):reason(0) (5/-1/104)
2013/12/21 12:00:11 kid1| TCP connection to 10.31.23.2/443 failed
[/HTML]
in access log of the Squid
[HTML]
1387623611.162      5 xx.xxx.xx.xx TCP_MISS/503 7382 GET https://MySite/myServletWAR/ - ANY_OLD_PARENT/10.31.23.2 text/html
[/HTML]

I didn't get any logs entries in the Apache Web server.

My Squid conf file is as:
[HTML]
acl SSL_ports port 443
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443         # https
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl CONNECT method CONNECT
cache_effective_user squid
acl localhost src Proxy_IP
acl webserver dst WebServer_IP
http_access allow webserver
http_access deny !Safe_ports
http_access allow localhost manager
http_access deny manager
http_access allow localnet
http_access allow localhost
http_access allow all
https_port 443 accel cert=MyPath/ssl/cert.pem key=MyPath/ssl/key.pem defaultsite=MySite
cache_peer WebServer_IP parent 443 0 no-query originserver login=PASS ssl sslcert= /MyPath/ssl/apache.crt sslkey=MyPath/ssl/apache.key name=apache
acl our_sites dstdomain  MySite
cache deny all
cache_dir ufs MyPath/dir  100 16 256
cache_access_log MyPath/log/squid/access.log
cache_log MyPath/log/squid/cache.log
cache_store_log MyPath/log/squid/store.log
coredump_dir /var/cache/squid  
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern -i (/cgi-bin/|\?) 0     0%      0
refresh_pattern .               0       20%     4320
[/HTML]

On the apache, I have this configuration :
[HTML]
Apache Server file

ServerRoot "/app/apache/2.2.26"
Listen 80
LoadModule authn_file_module modules/mod_authn_file.so
LoadModule authn_dbm_module modules/mod_authn_dbm.so
LoadModule authn_anon_module modules/mod_authn_anon.so
LoadModule authn_dbd_module modules/mod_authn_dbd.so
LoadModule authn_default_module modules/mod_authn_default.so
LoadModule authn_alias_module modules/mod_authn_alias.so
LoadModule authz_host_module modules/mod_authz_host.so
LoadModule authz_groupfile_module modules/mod_authz_groupfile.so
LoadModule authz_user_module modules/mod_authz_user.so
LoadModule authz_dbm_module modules/mod_authz_dbm.so
LoadModule authz_owner_module modules/mod_authz_owner.so
LoadModule authnz_ldap_module modules/mod_authnz_ldap.so
LoadModule authz_default_module modules/mod_authz_default.so
LoadModule auth_basic_module modules/mod_auth_basic.so
LoadModule auth_digest_module modules/mod_auth_digest.so
LoadModule file_cache_module modules/mod_file_cache.so
LoadModule cache_module modules/mod_cache.so
LoadModule disk_cache_module modules/mod_disk_cache.so
LoadModule mem_cache_module modules/mod_mem_cache.so
LoadModule dbd_module modules/mod_dbd.so
LoadModule dumpio_module modules/mod_dumpio.so
LoadModule reqtimeout_module modules/mod_reqtimeout.so
LoadModule ext_filter_module modules/mod_ext_filter.so
LoadModule include_module modules/mod_include.so
LoadModule filter_module modules/mod_filter.so
LoadModule substitute_module modules/mod_substitute.so
LoadModule charset_lite_module modules/mod_charset_lite.so
LoadModule deflate_module modules/mod_deflate.so
LoadModule ldap_module modules/mod_ldap.so
LoadModule log_config_module modules/mod_log_config.so
LoadModule log_forensic_module modules/mod_log_forensic.so
LoadModule logio_module modules/mod_logio.so
LoadModule env_module modules/mod_env.so
LoadModule mime_magic_module modules/mod_mime_magic.so
LoadModule cern_meta_module modules/mod_cern_meta.so
LoadModule expires_module modules/mod_expires.so
LoadModule headers_module modules/mod_headers.so
LoadModule ident_module modules/mod_ident.so
LoadModule usertrack_module modules/mod_usertrack.so
LoadModule unique_id_module modules/mod_unique_id.so
LoadModule setenvif_module modules/mod_setenvif.so
LoadModule version_module modules/mod_version.so
LoadModule proxy_module modules/mod_proxy.so
LoadModule proxy_connect_module modules/mod_proxy_connect.so
LoadModule proxy_ftp_module modules/mod_proxy_ftp.so
LoadModule proxy_http_module modules/mod_proxy_http.so
LoadModule proxy_scgi_module modules/mod_proxy_scgi.so
LoadModule proxy_ajp_module modules/mod_proxy_ajp.so
LoadModule proxy_balancer_module modules/mod_proxy_balancer.so
LoadModule ssl_module modules/mod_ssl.so
LoadModule mime_module modules/mod_mime.so
LoadModule dav_module modules/mod_dav.so
LoadModule status_module modules/mod_status.so
LoadModule autoindex_module modules/mod_autoindex.so
LoadModule asis_module modules/mod_asis.so
LoadModule info_module modules/mod_info.so
LoadModule cgi_module modules/mod_cgi.so
LoadModule dav_fs_module modules/mod_dav_fs.so
LoadModule dav_lock_module modules/mod_dav_lock.so
LoadModule vhost_alias_module modules/mod_vhost_alias.so
LoadModule negotiation_module modules/mod_negotiation.so
LoadModule dir_module modules/mod_dir.so
LoadModule imagemap_module modules/mod_imagemap.so
LoadModule actions_module modules/mod_actions.so
LoadModule speling_module modules/mod_speling.so
LoadModule userdir_module modules/mod_userdir.so
LoadModule alias_module modules/mod_alias.so
LoadModule rewrite_module modules/mod_rewrite.so
User wwwd
Group wwwgrp
ServerAdmin you@example.com
ServerName FullyQualifiedDistinguishedName:80
DocumentRoot "/app/apache/2.2.26/htdocs"
ErrorLog "logs/error_log"
ErrorLog "/datalog/apache/2.2.26/logs/error_log"
LogLevel warn
<IfModule ssl_module>
SSLRandomSeed startup builtin
SSLRandomSeed connect builtin
</IfModule>
include conf/tomcat.conf
include conf/ssl.conf

SSL.conf file
NameVirtualHost *:443
Listen *:443
<virtualhost *:443>
        ServerName MyWebsite
        DocumentRoot /app/apache/2.2.26/htdocs
        SSLEngine on
        SSLCertificateFile /app/apache/2.2.26/ssl/apache.crt
        SSLCertificateKeyFile /app/apache/2.2.26/ssl/apache.key
</virtualhost>
[/HTML]

On the browser web side, I've :
[HTML]
ERROR
The requested URL could not be retrieved
Then (I translated)
the following error occured  trying to access to URL https://MySite/xxxx
It is not possible to establish a secure connexion with Webserver@IP
The system returned:
(104) Connection reset by peer (TLS code: SQUID_ERR_SSL_HANDSHAKE)
Handshake with SSL server failed: [No Error]
This proxy and the remote host are unable to to negociate a secure connexion for your requests. It is possible that your remote host doesn't support secure connexion or that the proxy is not "happy" with the security certificate of your remote host.
[/HTML]
Could help me. I think I'm wrong in the certificate definition. 
Do you have a well known procedure that I could follow in order to establish an SSL configuration between the RP and the apache ? I woul appreciate it.
If you have any advise, let me know because I'm a little bit stucked with that.
best regards,
isagarran

---

### Post by ericdunin on 2014-01-13
Did you fixed your issued ? I'm facing the same and I'm interested if you foind what was wrong. 

Are you using autosigned certificated ? 

Thks Eric.

---

