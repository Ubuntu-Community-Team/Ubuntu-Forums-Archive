---
title: "Samba File server ADS Domain Member easy setup"
date: 2012-08-31
forum: Server Platforms
---

### Post by vace on 2012-08-31
Samba file sharing Domain member active directory
on Ubuntu 12.04 server

This is my first thread on this forum .
I lost  2-3 days to configure samba with a lot of pain and
headaches and finally got done. I had configured samba many times ago , but this way was different as i started with simplest configuration and added only needed commands only to make samba 
working but i hadn't time to make extensive testing , so you can
post your feedback on this thread. 

notice you don't need to write commented # descriptions
At first define names for configuration options:

YOURDOMAIN.LOCAL  - name of your domain on local network
kdcserver  - same as your domain server if only one, also  can be server's ip address 
'username'  -  user in which home directory share folder will stay
sambaserver - name of your linux server name in /etc/hostname


1. installation of services:
[B]sudo apt-get update
sudo apt-get upgrade
sudo apt-get install samba smbfs smbclient
sudo apt-get install krb5-user libpam-krb5 libpam-ccreds auth-client-config
sudo apt-get install winbind[/B]
	
2. edit /etc/krb5.conf    with domain name (YOURDOMAIN.LOCAL)
[B][libdefaults]
	default_realm = YOURDOMAIN.LOCAL
	dns_lookup_realm = true
	dns_lookup_kdc = true[/B]
	
[B][realms]
	YOURDOMAIN.LOCAL = {
		kdc = kdcserver [/B]       # kdcserver is full dns name of realm server same as domain server , or ip address can be also A.B.C.D
		[B]default_domain = yourdomain.local
	}[/B]
	
[B]	
[domain_realm]
	.yourdomain.local = YOURDOMAIN.LOCAL
	yourdomain.local = YOURDOMAIN.LOCAL[/B]
	
	
3. edit /etc/samba/smb.conf   with domain name (YOURDOMAIN.LOCAL)
[B]realm = YOURDOMAIN.LOCAL
workgroup = YOURDOMAIN
security = ads
preferred master = no
server string = Samba file server
encrypt passwords = yes
winbind separator = +
password server = kdcserver #  your server name , full dns name or ip address A.B.C.D
idmap uid = 10000-99999
idmap gid = 10000-99999
log level = 3
log file = /var/log/samba/log.%m
max log size = 50
#client ntlmv2 auth = yes[/B]

# one share for testing
[B][testshare]
	comment = Test share
	path = /home/'username'/share      # username name of user's home directory
	read only = no[/B]
	
	
4. edit /etc/nsswitch.conf   # very important winbind to work !!!

change  lines to:

[B]passwd:	compat  winbind
group:	compat  winbind
shadow:	compat[/B]

5. edit /etc/hosts  

#  sambaserver is name of the linux server found in /etc/hostname 
**127.0.0.1    sambaserver  sambaserver.yourdomain.local  **    

# IP address and name of domain server and full dns domain
**A.B.C.D    kdcserver  kdcserver.yourdomain.local ** 


6. restart services and join domain
[B]sudo service winbind restart
sudo service smbd restart
sudo kinit [email]Administrator@YOURDOMAIN.LOCAL[/email] [/B]   # domain must be with uppercases
 - when asks put domain administrator password
**sudo net ads join -U [email]Administrator@YOURDOMAIN.LOCAL[/email]**
- when asks put domain administrator password
 
 7. test 
 [B]mkdir /home/'username'/share
 sudo chmod 777 /home/'username'/share[/B]
reboot computer 
- after login test wbinfo
 [B]sudo wbinfo -g
 sudo wbinfo -u[/B]
 
- if ok then test from local windows machine
 if login windows popup problem with winbind , put full domain
name/username    in login window and password
for troubleshooting  read logs  
**cd /var/log/samba**
**tail -n 50 log.machine-name**       or  other log files

---

