---
title: "Help!! Samba with W2k domain Problem"
date: 2009-10-09
forum: Server Platforms
---

### Post by Carlos Pena on 2009-10-09
I have a Windows 2k server and a Ubuntu Server. I need to configure Samba to authenticate the users from the Windows server on a domain. 

I have read a lot of examples at samba.org and others sites, but my configuration doesn't work at all. I set the samba directive "security = domain", joined the server to the domain. When i try to access the volume on Samba(Linux) server it doesn't accept the users/password that are valid on windows Server. Only public share works. 

I have several weeks tryint to do this with no goods results. The samba conf directive "security = users" requires that all groups and users on Windows Server must be registered again in the Linux server. 

I hope someone could help me.


Carlos R. Pena
Santo Domingo, Dominican Republic


======================================
My last smb.conf is:

[global]

   workgroup = MyDomain
   server string = %h 
   log file = /var/log/samba/log.%m
   max log size = 1000

   syslog = 0

   security = domain
   password server = *   /*(i tryed with the domain name too)*/
   encrypt passwords = yes 

   passdb backend = tdbsam

   netbios name = LinuxServer
   unix password sync = Yes 


   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

   pam password change = yes

   map to guest = bad user

   socket options = TCP_NODELAY

   winbind enum groups = yes
   winbind enum users = yes


[Public Share]
public = yes
read only = no
create mode = 0777
path = /Volume/Public
create mask = 777
directory mask = 777
  
[VIP Share]
valid users = @sales, administrator 
path = /Volume/VIP
read only = no
public = no 
create mode = 0777
create mask = 777
directory mask = 777

=============== END =========

---

### Post by lykwydchykyn on 2009-10-09
I'm no expert on this, but I think "domain" is for NT4 domains, so unless your Win2k server is running a "compatibility mode" domain (I think that's what it's called) it won't work.  You need "security=ads" which is for Active Directory domains.

That may not fix your problem, but if you're running your domain in native mode I would think it would be required.

---

### Post by koenn on 2009-10-09
have a look at this:
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm)

it should cover the basics of what you're trying to do

---

### Post by Carlos Pena on 2009-10-09
I will try configuring samba with ADS and let you know what happen.

Thank you guys.

---

### Post by Carlos Pena on 2009-12-14
After trying a lot I am still having problems to join my ubuntu server to the y2k domain.

My krb5.conf is:
=========================================================
[logging]
default = FILE:/var/log/krb5libs.log
kdc = FILE:/var/log/krb5kdc.log
admin_server = FILE:/var/log/kadmind.log

[libdefaults]
default_realm = EMPRESA.LOCAL
dns_lookup_realm = false
dns_lookup_kdc = false
ticket_lifetime = 24h
forwardable = yes

[realms]
EMPRESA.LOCAL = {
   kdc = empresa.local
   admin_server = empresa.local
   default_domain = empresa.local
}

[domain_realm]
.kerberos.server = empresa.local
.empresa.local = EMPRESA.LOCAL

[kdc]
profile = /var/kerberos/krb5kdc/kdc.conf

[appdefaults]
pam = {
   debug = false
   ticket_lifetime = 36000
   renew_lifetime = 36000
   forwardable = true
   krb4_convert = false
}
==========================================================

My smb.conf is:
=====================================

[global]
   workgroup = EMPRESA   
   realm = EMPRESA.LOCAL
   preferred master = no
   server string = Servidor de Archivos de Anso (Archivos-Anso)

   security = ADS
   encrypt passwords = yes 
   log level = 3
   log file = /var/log/samba/%m
   max log size = 50

   winbind enum users = yes
   winbind enum groups = yes
   winbind use default domain = Yes
   winbind nested groups = Yes
   winbind separator = +
   password server = 26.4.0.1
   
   idmap uid = 10000-20000
   idmap gid = 10000-20000
   
   
   
   template homedir = /dev/null
   ;template shell = /bin/true
   ;template primary group = "Domain Users"
   template shell = /bin/bash


   
#======================= Share Definitions =======================

[Volumen Publico]
public = yes
read only = no
create mode = 0777
comment = Disco 1 - Para Uso General o de Transito
path = /Volumen/Volumen_Publico
create mask = 777
directory mask = 777

[Volumen Contabilidad]
valid users = -@EMPRESA+contabilidad, -@EMPRESA+ingenieros, EMPRESA+facturacion-01, EMPRESA+administrator administrator
comment = Disco 1 - Archivos Depto. Contabilidad 
path = /Volumen/Volumen_Contabilidad
read only = no
public = no 
create mode = 0777
create mask = 777
directory mask = 777

=====================================

I tried everything. I have read all examples for ADS at samba.org and linux forums on the internet. but it doesn't work. 

Please help!!!

When I run 

sudo net ads join -UAdministrator

the command returns:

utils/net_ads.c:ads_startup_int(286)
  ads_connect: No logon servers
Failed to join domain: No logon servers

or 

Failed to join domain: Operations error

Carlos Pena
Santo Domingo, Dominican Republic

---

### Post by benjaminsuman on 2009-12-14
You should try the LikewiseOpen client for AD integration.  I have had a lot of luck using this to quickly configure AD authenticated samba shares.

[https://help.ubuntu.com/9.10/serverguide/C/likewise-open.html](https://help.ubuntu.com/9.10/serverguide/C/likewise-open.html)

Example smb.conf:
```

[global]
  server string = %h (File Server)
  workgroup = WORKGROUP
  realm = DOMAIN.LOCAL
  security = ads
  disable spoolss = yes
  idmap domains = ALL
  idmap config ALL:readonly = yes
  idmap config ALL:default = yes
  idmap config ALL:backend = lwicompat_v4
  password server = [AD Server IP Address]
  wins server = [WINS Server IP Address]
  dns proxy = yes
  encrypt passwords = true
  invalid users = root

#LOGGING#
  log file = /var/log/samba/log.%m
  max log size = 100
  syslog = 0
  panic action = /usr/share/samba/panic-action %d

#==================== Share Definitions ==================
[share]
  path = /share
  comment = Shared Files
  browseable = yes
  writable = yes
  valid users = @DomainName\RW_UserGroup
  read list = @DomainName\RO_UserGroup
  force directory mode = 0770
  force group = DomainName\RW_GroupName #needs rw permissions on dir
  create mask = 0770
  directory mask = 0770

```You will need to link the Likewise authentication libraries lwicompat_v2.so, lwicompat_v3.so, and lwicompat_v4.so to /usr/lib/samba/idmap to make the Likewise client authentication available to Samba.  I am not sure if this is done or not by the installer in the repositories as I have only installed v5 using the binary installer from Likewise.

---

