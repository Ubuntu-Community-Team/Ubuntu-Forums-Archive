---
title: "OpenLDAP and Active Directory Integration"
date: 2011-09-19
forum: Server Platforms
---

### Post by kaushal@nttmcl.com on 2011-09-19
Hi All,

I need some guidance with AD and OpenLDAP user database integration/synchronization. 
Here is what i am trying to do,

We have Full Linux database(Ubuntu 10.4) with users on OpenLDAP and using only opensource applications(POSTFIX, Fileserver, Print server, apache, VPN etc.). Currently all windows(Mostly 7 and Vista) clients machines are not on Domain. We want to introduce Active directory because of its excellent features when it comes to handling users, plus with it can also handle update patches and we can have a variety of restrictions on users using group policies.
I have been digging on the web since last couple of days but have had no luck in finding something that can synchronize user information from AD to openldap so we can have one user password for all the applications. We would like to have a centralized user database with one password for all applications. 
I hope i was able to explain it correct on what i am looking for.
Please let me know if you have implemented something similar to synchronize user password information between AD and OpenLDAP. I will appreciate any input. 

Thank you!!

---

### Post by wineman on 2011-09-19
Hi there!

The situation that you described can - i think - can be summed up as this:
> We have Full Linux database(Ubuntu 10.4) with users on OpenLDAP and using only opensource applications(POSTFIX, Fileserver, Print server, apache, VPN etc.).We want to introduce Active directory because of its excellent features when it comes to handling users, plus with it can also handle update patches and we can have a variety of restrictions on users using group policies.

Now i assume that you have heard of SAMBA4 ([http://wiki.samba.org/index.php/samba4]("http://wiki.samba.org/index.php/SAMBA4")), which is the latest version of the SAMBA project. I would highly recommend using it as your AD Server backend, and this is (basically) how you do it.

There are one of two ways that you can do this, and i will list them both and explain both of them in theory and then in practice. 
The first method is by setting up 2 servers (either both physical or virtual) with the following configurations:

**SERVER 1: (IP: 10.0.0.1/24)**
**Role**: SAMBA4 AD server without slapd or openldap, but with bind9, krb5-user, dhcp3-server, ntpdate, and ntpd. These are the packages you'll need for the system to run in a basic fasion as a primary DC.
**DHCP**: all servers point to itself (ie - router, domain-name-server, netbios-name-server, netbios-dd-server, time-server, etc. point to this server), and 10.0.0.10-10.0.0.100/24 subnet range.
**DNS**: Domain name "wineman.local", with MX, SRV (ports 389 and 88), A and basically everything DNS-related to do with the SRVs for _ldap and _kerberos pointing back to the DC (or to 10.0.0.1).
**KRB5-USER**: (kerberos) Realm is internal.wineman.org, with the administrative and password server being 10.0.0.1 (or srv.wineman.local, where srv is 10.0.0.1)
**NTP**: Set to synchronize with any time server every 240 hours or Saturday (its up to you)
**SAMBA4**: Configured as follows (which will create all the configurations needed for the above programs except for DHCP):
```
# The assumption is that you're running ubuntu 10.10
# This config create a SAMBA4 config with SMB Realm internal.wineman.org, 
# DNS Domain wineman.local, Administrator's password is 'p@ssword123' and 
# the server type is a 2008 'Domain Controller', for the host ip 10.0.0.1
$ cd /usr/share/samba/setup
$ ./provision --realm=internal.wineman.org --domain=wineman.local --adminpass=p@ssword123 --server-role='domain controller' --host-ip=10.0.0.1
```

Now, copy the newly created configs from /var/lib/samba/private to the various locations:
```
$ sudo cp /var/lib/psamba/private/krb5.conf /etc/krb5.conf
$ sudo echo "include  \"/var/lib/samba/private/named.conf\"" >> /etc/bind/named.conf.local
```

Initialise the Admnistrator's account according to kerberos. You'll need to type in the admin's password here.

```
# NOTE: Any issues, change /etc/krb5.conf's DNS names (in this case, srv.wineman.local) to IP Addresses.
```

```
# Initialize the Administrator@INTERNAL.WINEMAN.ORG realm
$ sudo kinit [email]Administrator@INTERNAL.WINEMAN.ORG[/email]
```

```
# Create symlinks for SAMBA4
$ sudo ln -s /usr/local/sbin/samba{,_dnsupdate}
$ sudo ln -s /usr/local/sbin/samba{,_spnupdate}
```

```
# Add these to /etc/apparmor/usr.sbin.named at the bottom:
/var/lib/samba/private/* rw,
/var/lib/samba/private/dns/* rw, 
```

```
# now restart the server.
$ sudo reboot
```

Basically from there you should be able to join the domain from a windows 7 client, and (once RSAT,  [http://support.microsoft.com/kb/941314]("http://support.microsoft.com/kb/941314"), is installed) you can setup a TRUST DOMAIN. I'm not good with the Windows side of things, but basically it is telling SAMBA4 that the domain (or the AD Server or server or whatever) is trustable, ie - we are going to let it copy FROM, TO and BETWEEN us and itself. This is done through th Acive Directory Sites and Domains Management Console (ADSMC or ADSC or ADSM or some silly acronym) and you specify 'Trust Domains' and 'Trust Servers' in the Forest (in this cast, the Forest is internal.wineman.org).
What we want to do is basically allow you OpenLdap server (a separate server which is the SLAVE server, whic we're gonna be setting up now) to sync with it.

[B]LDAP SERVER: (IP:10.0.0.5)
Role:[/B] LDAP Authentication Server, with NSS/VPN/POSTFIX/Fileserver/Print server/apache/etc)
I'm not going to tell you how to configure your servers individually, ie i'm not going to show you how to configure VPN and Postfix and FS, etc but i will tell you how to sync off the SAMBA4 AD.

execute these in bash to get the server to pick up samba subsystems and schemas:
```
sudo cp /usr/share/doc/samba-doc/examples/LDAP/samba.schema.gz /etc/ldap/schema/samba.schema && sudo gzip -d /etc/ldap/schema/samba.schema && sudo service slapd restart
```

in /etc/ldap/slapd.conf:
```
# Set your config like this:
# slapd.conf delta synrepl Openldap2.3
# LDAP Consumer
 
# Change the following things:
# /var/lib/ldap - path of your LDAP directory
# dc=wineman,dc=local - the DN that samba4 creates on your Samba4 server 
# (10.0.0.1). It is usually the DN form of your DNS Domain name, ie i
# replaces the dots with ",dc=". 
# So wineman.local becomes DC=wineman,DC=local
# rootdn and rootpw - this should be your administrative DN and pw you 
# put in when you installed slapd on this server.
# syncuser - that should be a NON-ADMINISTRATIVE trusted account on your
# samba4 DC.
# 10.0.0.1 (in ldap://10.0.0.1:389) - this should be your samba4 DC's ip 
# that you put in initially.
include     /etc/ldap/schema/core.schema
include     /etc/ldap/schema/cosine.schema
include     /etc/ldap/schema/inetorgperson.schema
include     /etc/ldap/schema/nis.schema
include     /etc/ldap/schema/samba.schema

modulepath /var/lib/ldap
moduleload back_bdb.la

pidfile     /var/run/slapd/slapd.pid
argsfile    /var/run/slapd/slapd.args
 
database    bdb
suffix      "dc=wineman,dc=local"
directory   /var/lib/ldap
# Change this with your root user's DN and pw
rootdn      "cn=admin,dc=wineman,dc=local"
rootpw      Manager

# syncrepl directives - you'll need to add a user called 'syncuser' 
# on your SAMBA4 DC
syncrepl  rid=0
       provider=ldap://10.0.0.1:389
       bindmethod=simple
       binddn="cn=syncuser,ou=People,ou=Users,dc=wineman,dc=local"
       credentials=SyncUser
       searchbase="ou=People,ou=Users,dc=wineman,dc=local"
       logbase="cn=accesslog"
       logfilter="(&(objectClass=auditWriteObject)(reqResult=0))"
       schemachecking=on
       type=refreshAndPersist
       retry="60 +"
       syncdata=accesslog
 
access to attrs=userPassword
        by dn="cn=syncuser,ou=People,ou=Users,dc=wineman,dc=local" read
        by dn="cn=syncuser,ou=People,ou=Users,dc=wineman,dc=local" write
        by * auth

access to attrs=sambaLMPassword,sambaNTPassword
        by dn="cn=syncuser,ou=People,ou=Users,dc=wineman,dc=local" read
        by dn="cn=syncuser,ou=People,ou=Users,dc=wineman,dc=local" write

access to *
        by dn="cn=syncuser,ou=People,ou=Users,dc=wineman,dc=local" read
        by dn="cn=syncuser,ou=People,ou=Users,dc=wineman,dc=local" write
        by * read

updateref   ldap://10.0.0.1
index objectClass           eq
index cn                    pres,sub,eq
index sn                    pres,sub,eq
index uid                   pres,sub,eq
index displayName           pres,sub,eq
index uidNumber             eq
index gidNumber             eq
index memberUID             eq
index sambaSID              eq
index sambaPrimaryGroupSID  eq
index sambaDomainName       eq
index default               sub
```
# End of File

Now, for /etc/ldap.conf:
```
#/etc/ldap.conf
# LDAP Slave
# the first IP Should be the IP of the
# server that you're syncing TO; the
# second IP should be the server you're
# syncing from.
# In this exmaple, it is:
# FROM 10.0.0.1 --> 10.0.0.5
host    10.0.0.5 10.0.0.1
base    dc=wineman,dc=local
# Change accordingly with your LDAP Server settings
binddn  cn=admin,dc=wineman,dc=local
bindpw  Manager

bind_policy soft 
pam_password exop

# User base pam-style pws for Auth
nss_base_passwd ou=People,ou=Users,dc=wineman,dc=local?one
# User base shadow pw for Auth
nss_base_shadow ou=People,ou=Users,dc=wineman,dc=local?one
# PC pam passwords for Auth
nss_base_passwd ou=Computers,ou=Users,dc=wineman,dc=local?one
# PC shadow password for Auth
nss_base_shadow ou=Computers,ou=Users,dc=wineman,dc=local?one
# User groups for Auth
nss_base_group  ou=Groups,dc=wineman,dc=local?one
# Disable ssl connections in LDAP
ssl     no
```

Ok so now your SAMBA4 LDB Will be synced to the slapd client, and then you can grab the data off the LDAP database. The hierarchy of the DB is as follows:
```

|-Samba Base
|---Manager                  
|------syncuser                
|------sambaadmin           
|------mailadmin               
|---------Users                              
|---------------------People                          
|--------------------------------root Administrator)                      
|--------------------------------(various users)
|--------------------------------simo
|---------------------Computers                     
|--------------------------------workstation1$
|--------------------------------(domain computers)
|---------Groups                
|---------------------Domain Admin               
|--------------------------------root (Adminsitrator)       
|---------------------Domain Users                
|--------------------------------root (Again, same user)
|--------------------------------(Domain users)
|--------------------------------simo
|---------------------Domain Guests            
|---------------------------------nobody
|---------------------Domain Computers       
|--------------------------------workstation1$
|--------------------------------(domain clients)
|-----------Domains             
|-------------sambaDomainName (NAME of the realm)
```

You should be able to setup your apps to auth off this LDAP DB. THe standard user LDAP schema is as follows:
```
# Similar, but not exactly:
dn: CN=Administrator,CN=Users,DC=wineman,DC=local
objectClass: user
description: Built-in account for administering the computer/domain
userAccountControl: 512
objectSid: (domain's SID)-500
adminCount: 1
accountExpires: 9223372036854775807
sAMAccountName: Administrator
clearTextPassword:: (admin password as a Base64 Encrypted key)
isCriticalSystemObject: TRUE
```

it has all the usual markers of a** Samba/POSIX user** (objectclass person, sAMAccount, posixAccount, etc) and can have custom LDAP entries added via **LDAPAdmin** (downloaded [here]("http://ldapadmin.sourceforge.net/"), and its FREE AND OPENSOURCE).

In dhcpd.conf, add the following to your subnet config:
(Provided the subnet is 10.0.0.0 netmask 255.255.255.0)
```

option netbios-dd-server 10.0.0.1;
option netbios-name-server 10.0.0.1;
option netbios-node-type = 8;
# sangoma.saix.net is my country (SA)'s time server for our ISP,
# so i use it to sync my networks to.
option time-servers 10.0.0.5,sangoma.saix.net;
# Specifying the samba4 AD as a DNS server will allow your to connect to 
# it without having to specify your DNS/KRB servers in Windows XP/7.
# This is helpful because it will first ask YOUR DC where the domain is,
# Then query your network's official DNS server, then ask your DSL Router,
# then ask the internet (by which time, it will have found our domain).
option domain-name-servers 10.0.0.5,<ip of your router>,<ip of your intern DNS server>;

```

Now, restart everything on the SERVER 1 (10.0.0.1):
```
sudo service isc-dhcp-server restart
sudo service bind9 restart
sudo service samba4 restart
sudo service ntpd restart

```

and on SERVER 2 (10.0.0.5):

```
sudo service slapd restart
# Not needed, but refreshes any shares 
# or services you may have on the system
sudo service smbd restart
# restart all your other stuff that you run (postfix, vpn...)
sudo service postfix restart
sudo service openvpn restart
sudo service dovecot restart
sudo service iptables restart
sudo service squid restart
# ...
# ....
# etc
```

With regards to user passwords, this is a ONE WAY SYNC, so any changes on the LDAP server (10.0.0.5, SERVER 2) will be erased. This thing to do is to get the clients to update the SAMBA4 passwords, and then wait like 60 minutes for the passwords to update and sync between the 2 servers. This should take about 2 minutes to copy across.
Almost all the user auths should be read from "ou=People,ou=Users,dc=wineman,dc=local" or the same DN but without the ou=People.

Again, all the admin of users/domains/sites can be done from Windows 7 via Remote Server Administration Tools (RSAT, link above), or Windows XP from the group policy management console (gpmc, google it, it's like the 2nd result there) and Server 2003 Administration Kit for Windows XP and Windows 2000 Clients (its also google-able, but is sometimes called SERVER 2003 KIT).

If there is anything else you would like to know with regards to the LDAP or setting up of the systems, i'm more than happy to help. If this fails to meet your expectations, there is a system called Zentyal ([http://www.zentyal.org]("http://www.zentyal.org")) that is a free Ubuntu based system for (basically) DC-systems, and it is modular, so you can install only the active directory replication module and have that as your central auth system. The cool part is that it is all webpage based, and so you can fiddle around with it as much as you like and it WILL NEVER break.

I hope this helps. Again, any questions or requests, im happy to help :)

HTH
wineman

---

### Post by kaushal@nttmcl.com on 2011-09-25
Hi Wineman...

sorry i couldnt reply, i was out at my clients site. But thanks a lot for this guided reply. I am now working on implementing this. Will let you know if i face any issues. thanks again :)

---

### Post by kash13 on 2011-10-06
Hi..
I was trying to implement this but i dont understand where AD is involved. Out of all the implementation AD role is not defined. I want to add users to AD and then have them propagated to openLDAP and or add them to openLDAP and have it synchronized with AD. Can you please help please?

---

### Post by headvampyre@hotmail.co.uk on 2011-10-06
Samba4 will host Active Directory in this environment, but if I remember, they were starting to remove the code for external LDAP servers as it is a low priority as it has an internal LDAP server aswell. You could risk it, but I would try this on a test domain first.

---

### Post by kash13 on 2011-10-06
thanks for the reply. Have you implemented something similar?? AD to OpenLDAP user database. I am really looking to create a centralized user database between Ubuntu and AD with single password for all the applications. Not sure if this is possible??

---

