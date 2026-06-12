---
title: "Squid3 Proxy Ubuntu 12.04.1"
date: 2012-09-18
forum: Security
---

### Post by netwo on 2012-09-18
here it goes i wanted to filter a group of user by their groups and right to see some pages and to filter some pages taht i wanted to block them.Actually, i think i've messed up the config file of Squid, could someone look over it ... Thank you everyone ! 


## Nom du proxy
visible_hostname PROXY

## Port du proxy (par dÃ©faut)
http_port 3128

## Configuration recommandÃ© par Squid (le double D n'est pas une faute de frape!)
cache_effective_group winbindd_priv
###

## Configuration pour SBS
#auth_param ntlm program /usr/bin/ntlm_auth --helper-protocol=squid-2.5-ntlmssp
auth_param ntlm program /usr/lib/squid3/ntlm_smb_lm_auth 
auth_param ntlm children 20 startup=0 idle=1
auth_param ntlm keep_alive on

#auth_param basic program /usr/bin/ntlm_auth --helper-protocol=squid-2.5-basic
auth_param basic program /usr/lib/squid3/ntlm_smb_lm_auth
auth_param basic children 20
auth_param basic realm Squid AD
auth_param basic credentialsttl 2 hours
###

## Configuration recommandÃ© par Squid
acl all src all
acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8
###

## DÃ©finit le type d'ACL groupe_SBS se rapportant sur les groupes SBS
#	TTL 5 minutes (regulier)
external_acl_type groupe_SBS ttl=300 %LOGIN /usr/lib/squid3/wbinfo_group.pl

#	TTL 1 seconde (pour tests)
#external_acl_type groupe_SBS ttl=1 %LOGIN /usr/lib/squid3/wbinfo_group.pl


## Configuration recommandÃ© par Squid
acl localnet src 192.168.0.0/16 # RFC1918 possible internal network
acl SSL_ports port 443          # https
acl SSL_ports port 563          # snews
acl SSL_ports port 873          # rsync
acl Safe_ports port 80          # http
acl Safe_ports port 88		# alternate HTTP
acl Safe_ports port 21          # ftp
acl Safe_ports port 443         # https
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl Safe_ports port 631         # cups
acl Safe_ports port 873         # rsync
acl Safe_ports port 901         # SWAT
acl purge method PURGE
acl CONNECT method CONNECT
###

## DÃ©finition des groupes
# acl Nom du groupe Squid	Type de liste		Nom du groupe SBS (minuscule)
# acl SBS_NomDuGroupe		external groupe_SBS	nomdugroupe

acl SBS_InternetAcces4	external groupe_SBS InternetAcces4
acl SBS_InternetAcces3  external groupe_SBS InternetAcces3
acl SBS_InternetAcces2  external groupe_SBS InternetAcces2
acl SBS_InternetAcces1  external groupe_SBS InternetAcces1
acl SBS_InternetAcces0  external groupe_SBS InternetAcces0
### 

## DÃ©finition des sites autorisÃ©s (par groupe)
# Ces listes retournent Ã* des fichiers externes
# afin d'allÃ©ger le fichier de configuration principal
#
# Note: Les expressions rÃ©guliÃ¨res sont sensible Ã* la case.  
# 	  L'option -i dÃ©sactive la sensibilitÃ© de la case 
#
# acl	Nom de la liste Squid	Type de liste	"/chemin/du/fichier.txt"
# acl	Allow_Groupe		url_regex -i	"/etc/squid3/Allow/Sites/Groupe.txt"
#

acl AllowIA4	url_regex -i "/etc/squid3/ACLs/AllowIA4.txt"
acl AllowIA3    url_regex -i "/etc/squid3/ACLs/AllowIA3.txt"
acl AllowIA2    url_regex -i "/etc/squid3/ACLs/AllowIA2.txt"
acl AllowIA1    url_regex -i "/etc/squid3/ACLs/AllowIA1.txt"
acl AllowIA0    url_regex -i "/etc/squid3/ACLs/AllowIA0.txt"

acl DenyIA4    url_regex -i "/etc/squid3/ACLs/DenyIA4.txt"
acl DenyIA3    url_regex -i "/etc/squid3/ACLs/DenyIA3.txt"
acl DenyIA2    url_regex -i "/etc/squid3/ACLs/DenyIA2.txt"
acl DenyIA1    url_regex -i "/etc/squid3/ACLs/DenyIA1.txt"
###


## ACL RESEAU_LOCAL pour permettre les adresses interne
acl RESEAU_LOCAL	url_regex -i 192\.168\.0
acl RESEAU_LOCAL	url_regex -i intranet\.ashcent\.com
acl RESEAU_LOCAL	url_regex -i .\.ashton\.local

## ACL SSL_CERT pour permettre la validation des certificat SSL
acl SSL_CERT 	url_regex -i ^[http://www.download.windowsupdate.com/msdownload/update/v3/static/trustedr/](http://www.download.windowsupdate.com/msdownload/update/v3/static/trustedr/)
acl SSL_CERT 	url_regex -i ^[http://www.download.windowsupdate.com/msdownload/update/v3/static/trustedr/](http://www.download.windowsupdate.com/msdownload/update/v3/static/trustedr/)
acl SSL_CERT	url_regex -i ^[http://crl.godaddy.com/](http://crl.godaddy.com/)
acl SSL_CERT	url_regex -i .*\.verisign\.com

## ACL BlockMSN 1 a 3
# Il necessite trois type different d'ACL pour bloquer MSN Messenger
acl BlockMSN1	url_regex	-i gateway.edge.messenger.live.com
acl BlockMSN2	req_mime_type	-i ^application/x-msn-messenger$
acl BlockMSN3	url_regex 	-i gateway.dll 

## ACL Updates Sites
# Donne acces a certains sites de mises a jour a tout le monde
acl UPDATE_SITES url_regex	-i "/etc/squid3/ACLs/Update_Sites.txt"

## Configuration recommandÃ© par Squid
http_access allow manager localhost
http_access deny manager
http_access deny BlockMSN1
http_access deny BlockMSN2
http_access deny BlockMSN3
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
###


## DÃ©finition des accÃ¨s

# Comme les accÃ¨s sont dÃ©finis ligne par ligne, 
# nous dÃ©butons avec le groupe le plus strict

# Excepter le groupe Restreint, tous les autres sont autorise 
# au reseau interne et a valider des certificats SSL
http_access allow RESEAU_LOCAL all
http_access allow SSL_CERT all
http_access allow UPDATE_SITES all


# Nous bloquons MSN
http_access deny BlockMSN1
http_access deny BlockMSN2
http_access deny BlockMSN3
###


http_access deny	SBS_InternetAcces0	!AllowIA0

http_access deny	DenyIA4
http_access allow	SBS_InternetAcces4	AllowIA4

http_access deny	DenyIA3
http_access allow	SBS_InternetAcces3	AllowIA3

http_access deny	DenyIA2
http_access allow	SBS_InternetAcces2	AllowIA2

http_access deny	DenyIA1
http_access allow	SBS_InternetAcces1	AllowIA1

#  lignes d'accÃ¨s, nous refusons l'accÃ¨s
http_access allow all

# Puisque le protocole ICP n'est pas utilisÃ©, 
# nous refusons toute communication ICP
icp_port 0

## Configuration recommandÃ© par Squid
hierarchy_stoplist cgi-bin ?
access_log /var/log/squid3/access.log squid

refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern -i (/cgi-bin/|\?) 0     0%      0
refresh_pattern (Release|Package(.gz)*)$        0       20%     2880
refresh_pattern .               0       20%     4320

acl apache rep_header Server ^Apache
broken_vary_encoding allow apache

extension_methods REPORT MERGE MKACTIVITY CHECKOUT
hosts_file /etc/hosts
###

# Ajout du domaine puisque Squid n'utilise 
# pas l'entrÃ©e search du fichier /etc/resolv.conf
append_domain .ashton.local

# N'inclus pas l'adresse IP ou le nom de machine 
# dans les requÃªtes HTTP
forwarded_for off
coredump_dir /var/spool/squid3

---

### Post by netwo on 2012-09-18
I think that the NTLM authentification is messed up .. i can't find waht is the error...

---

### Post by netwo on 2012-09-18
Anyone ?

---

### Post by netwo on 2012-09-21
no one ?

---

### Post by wacky_sung on 2012-09-21
To be honest, i am too lazy to read through the mess. The quick and easy way is do a complete removal and reinstalled it back.

---

