---
title: "openLDAP error connection from local network"
date: 2014-03-27
forum: Server Platforms
---

### Post by alexandr4 on 2014-03-27
Ubuntu 12.10
@(#) $OpenLDAP: slapd  (Sep 19 2013 22:49:31) $
        buildd@batsu:/build/buildd/openldap-2.4.28/debian/build/servers/slapd


The problem can not connect server ldap, on a local network. 
Service slapd on the server it good works, it works phpLDAPAdmin.
Checking nmap showed that the port 389 is closed. 
Normally passes mail and everything else. 
Give the reason for where to dig?



netstat -an | grep '389'
> 
tcp        0      0 0.0.0.0:389             0.0.0.0:*               LISTEN
tcp6       0      0 :::389                  :::*                    LISTEN



iptables
> 
*filter
:INPUT DROP [18804:1680221]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [2282789:318205837]
:fail2ban-dovecot - [0:0]
:fail2ban-postfix - [0:0]
:fail2ban-roundcube - [0:0]
:fail2ban-ssh - [0:0]
-A INPUT -p tcp -m multiport --dports 80,443,25,587,110,995,143,993,4190 -j fail2ban-postfix
-A INPUT -p tcp -m multiport --dports 80,443,25,587,110,995,143,993,4190 -j fail2ban-dovecot
-A INPUT -p tcp -m multiport --dports 80,443,25,587,110,995,143,993,4190 -j fail2ban-roundcube
-A INPUT -p tcp -m tcp --dport 22 -j fail2ban-ssh
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i lo -j ACCEPT
-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 443 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 25 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 587 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 465 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 110 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 995 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 143 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 993 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
-A INPUT -p icmp -m icmp --icmp-type 8 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 389 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 636 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 9830 -j ACCEPT
-A fail2ban-dovecot -j RETURN
-A fail2ban-postfix -j RETURN
-A fail2ban-roundcube -j RETURN
-A fail2ban-ssh -j RETURN
COMMIT



nmap from local network
> 
PORT    STATE SERVICE
25/tcp  open  smtp
53/tcp  open  domain
80/tcp  open  http
443/tcp open  https
465/tcp open  smtps
993/tcp open  imaps
995/tcp open  pop3s


/etc/default/slapd
> SLAPD_CONF=SLAPD_USER="openldap"
SLAPD_GROUP="openldap"
SLAPD_PIDFILE=
SLAPD_SERVICES="ldap:/// ldaps:/// ldapi:///"
SLAPD_SENTINEL_FILE=/etc/ldap/noslapd
SLAPD_OPTIONS=""


---

