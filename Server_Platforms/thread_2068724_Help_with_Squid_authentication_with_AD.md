---
title: "Help with Squid authentication with AD"
date: 2012-10-09
forum: Server Platforms
---

### Post by pstonge on 2012-10-09
Hey guys, i have been going through the setup for setting up Squid3 to track our users web surfing. And I am at the point where I am joining my 12.04 server to our domain through Active Directory running Windows 2003. 
 
The error message is this;
 
##############################################
Joined 'Proxy' to realm 'test.com'
No DNS domain configured for proxy. Unable to perform DNS Update.
DNS update failed!
##############################################
 
I can look in my "computers" OU, and see that the server has joined. But what is the No DNS domain configured for proxy mean.
 
Here is my squid.conf file;
 
acl manager proto cache_object
acl localhost src 127.0.0.1/32 ::1
acl to_localhost dst 127.0.0.0/8 0.0.0.0/32 ::1
acl localnet src 192.168.0.0/22
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
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
dns_nameserver 192.168.12.20 #DNS Server
http_access allow localnet
http_access allow localhost
http_access deny all
# Add any of your own refresh_pattern entries above these.
refresh_pattern ^ftp: 1440 20% 10080
refresh_pattern ^gopher: 1440 0% 1440
refresh_pattern -i (/cgi-bin/|\?) 0 0% 0
refresh_pattern (Release|Packages(.gz)*)$ 0 20% 2880
refresh_pattern . 0 20% 4320
 
#############################################
 
Here is my smb.conf file;
 
ncrypt passwords = Yes
winbind separator = /
winbind cache time = 10
template homedir = /home/%D/%U
template shell = /bin/bash
idmap uid = 10000-20000
idmap gid = 10000-20000
winbind uid = 10000-20000
winbind gid = 10000-20000
winbind enum users = yes
winbind enum groups = yes
winbind use default domain = yes
server string = rad_test
netbios name = PROXY
security = ads
workgroup = NCS
log file = /var/log/samba/log.%m
max log size = 50
password server = ncsdcon
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
wins proxy = no
 
realm = NCS.NET
 
winbind uid = 10000-20000
winbind gid = 10000-20000
winbind use default domain = yes
winbind enum users = yes
winbind enum groups = yes
 
#################################################
 
And here is my krb5.conf file
 
[logging]
default = FILE:/var/log/krb5libs.log
kdc = FILE:/var/log/krb5kdc.log
admin_server = FILE:/var/log/kadmind.log
[libdefaults]
clockskew = 300
default_realm = NCS.NET
dns_lookup_kdc = false
dns_lookup_realm = false
ticket_lifetime = 24h
default_keytab_name = /etc/squid3/PROXY.keytab
# The following krb5.conf variables are only for MIT Kerberos.
krb4_config = /etc/krb.conf
krb4_realms = /etc/krb.realms
kdc_timesync = 1
ccache_type = 4
forwardable = true
proxiable = true
 
# The following libdefaults parameters are only for Heimdal Kerberos.
v4_instance_resolve = false
v4_name_convert = {
host = {
rcmd = host
ftp = ftp
}
plain = {
something = something-else
}
}
fcc-mit-ticketflags = true
[realms]
NCS.NET = {
kdc = ncsdcon.ncs.net
admin_server = ncsdcon.ncs.net
default_domain = NCS.NET
kpasswd_server = ncsdcon.ncs.net
[domain_realm]
.ncs.net = NCS.NET
ncs.net = NCS.NET
[kdc]
profile = /var/kerberos/krb5kdc/kdc.conf
[login]
krb4_convert = true
krb4_get_tickets = false
 
##############################################
 
I hope this helps, my goal is to have my users in AD, use the proxy for their web surfing, so we can track it. We want them to authenticate through NTLM, but I dont think I am at the NTLM stage yet. 
 
Thanks guys.
 
Paul

---

### Post by pstonge on 2012-10-09
Sorry left out some info.
 
When I issue a wbinfo -u i see the list of users, and when i do wbinfo -g i see the list of groups, but when i wbinfo -t  i get 
 
##################################
 
checking the trust secret for domain NCS via RPC calls failed
failed to call wbcCheckTrustCredentials: WBC_ERR_WINBIND_NOT_AVAILABLE
Could not check secret

###################################

---

### Post by fredted40x on 2012-11-19
Hi,

Have you found the answer?

Have the xact sae problem here.

---

