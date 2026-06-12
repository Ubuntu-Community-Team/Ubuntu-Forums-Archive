---
title: "Squid server help"
date: 2012-10-05
forum: Server Platforms
---

### Post by pstonge on 2012-10-05
hey everyone, I have installed Squid, have it set up with Active Directory, and now I have been trying to have it set so that the different groups in AD, have different access rights to the internet through Squid. I know its possible, its just i can not find a decent page online that can help me with this.
 
I have installed Samba also, and like i said, the Ubuntu server is on our domain, and can access our active directoy.
 
What we want is for letsay the Marketing group in AD to have more website access then the Agent group does. 
This is the final step of configuring our proxy to be EPIC!!!! Please help..
 
Any help would be great thanks.

---

### Post by pstonge on 2012-10-05
Just to clear things up, what i am trying to do is have it so that Squid has premissions or access to the NTLM, so that user's do not have to enter in their username/passwords with opening up Internet Explorer. 
 
I keep reading about something regarding winbind. But I am lost. 
Following is my Squid.conf file.
########################################################
########################################################
GNU nano 2.2.6 File: /etc/squid3/squid.conf
auth_param ntlm program /usr/bin/ntlm_auth --debug-level=10 --helper-protocol=s$
auth_param ntlm children 50
auth_param ntlm keep_alive on
authenticate_cache_garbage_interval 1 minute
authenticate_ttl 2 minutes
authenticate_ip_ttl 2 minutes
#auth_param ntlm program /usr/bin/ntlm_auth --helper-protocol=squid-2.5-ntlmssp
#auth_param basic program /usr/bin/ntlm_auth --helper-protocol=squid-2.5-basic
#auth_param ntlm children 5
#auth_param ntlm max_challenge_reuses 0
#auth_param ntlm max_challenge_lifetime 2 minutes
 
#auth_param basic program /usr/lib/squid3/squid_ldap_auth -R -b "dc=ncs,dc=net"$
#auth_param basic children 5
#auth_param basic realm Your Organisation Name
#auth_param basic credentialsttl 5 minutes
acl manager proto cache_object
acl localhost src 127.0.0.1/32 ::1
acl to_localhost dst 127.0.0.0/8 0.0.0.0/32 ::1
 
#####################################################################
acl localnet src 192.168.0.0/22
####################################################################
acl SSL_ports port 443
acl Safe_ports port 80 # http
acl Safe_ports port 21 # ftp
acl Safe_ports port 443 # https
acl Safe_ports port 70 # gopher
acl Safe_ports port 210 # wais
acl Safe_ports port 1025-65535 # unregistered ports
acl Safe_ports port 280 # http-mgmt
acl Safe_ports port 488 # gss-http
acl Safe_ports port 591 # filemaker
acl Safe_ports port 777 # multiling http
acl CONNECT method CONNECT
http_access allow manager localhost
http_access deny manager
# Deny requests to certain unsafe ports
http_access deny !Safe_ports
# Deny CONNECT to other than secure SSL ports
http_access deny CONNECT !SSL_ports
http_access deny to_localhost
##################################################################
#external_acl_type InetGroup %LOGIN /usr/lib/squid/squid_ldap_group -R -b "dc=n$
#acl localnet proxy_auth REQUIRED src 192.168.0.0/22
#acl InetAccess external InetGroup InternetAccessGroup
 
###################################################################
 
I really hope this helps a little.

---

