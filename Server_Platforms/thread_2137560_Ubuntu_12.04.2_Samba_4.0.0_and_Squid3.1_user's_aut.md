---
title: "Ubuntu 12.04.2 Samba 4.0.0 and Squid3.1 user's authentication"
date: 2013-04-21
forum: Server Platforms
---

### Post by Roswebnet on 2013-04-21
[FONT=Times New Roman][COLOR=#000000][SIZE=3][FONT=Calibri]Hi[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I have a virtualised environment built on VBox and GNS (See VInfra.jpg). On picture, you can find the services that are available now. [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I would like to allow an internet access through a Squid3 (U package) to only samba 4.0.1 (U package) authenticated and specific group related users.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I tried already squid_ntlm_auth and squid_ldap_auth. By first one the cli freezes. By second one I got more success with this command line:[/FONT][/SIZE]
```
[COLOR=red][FONT=Calibri]/usr/lib/squid3/squid_ldap_auth -R -b -D [EMAIL="ldap@odm.lan"]ldap@odm.lan[/EMAIL] -w Pa$$w0rd "dc=odm,dc=lan" -f "sAMAccountName=%s" -h odm-gw-srv01.odm.lan[/FONT][/COLOR]
```
[SIZE=3][FONT=Calibri]However when I type the username and password, I get:[/FONT][/SIZE]
```
[COLOR=red][SIZE=3][FONT=Calibri]ERR Success[/FONT][/SIZE][/COLOR]
```
[SIZE=3][FONT=Calibri]Therefore, is an error somewhere in command but not in domain search definition.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Any suggestions?[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Thank you.[/FONT][/SIZE]
[/COLOR][/FONT]

---

### Post by Roswebnet on 2013-05-16
no one? :(

---

### Post by Toxic64 on 2013-05-16
4.0.0.18??? are you sure your domain works correctly?
If you re using samba 4 as a AD DC you need to configure squid to allow  kerberos authentication.

---

### Post by Roswebnet on 2013-05-16
I believe yes. W8pro client can connect to it and access shared folders. I used this tutorial to allow simple bind within nslcd:
[http://www.linuxgfx.co.uk/karoshi/documentation/wiki/index.php?title=Samba4_Testing](http://www.linuxgfx.co.uk/karoshi/documentation/wiki/index.php?title=Samba4_Testing)
 
I can run:```

Kinit Administrator@ODM.LAN
ldapsearch -D ODM\Administrator -w Pa$$w0rd -b "dc=odm,dc=lan" -H ldap://10.1.1.1 -Y GSSAPI
```
 
This works only with:```

apt-get install libsasl2-modules-gssapi-heimdal
```
 
However getent passwd does not work. No samba4 ldap users in list.
In addition, this:
 ```

/usr/lib/squid3/squid_ldap_auth -u cn -b "cn=Users,dc=odm,dc=lan" 10.1.1.1
Administrator Pa$$w0rd
OK
```
 
Works too but only for Administrator. Squid_ldap_group doesn&#8217;t work at all (ERR success)
 
 
The U12.04.2 has now Samba 4.0.1. (My bad)
My smb.conf:
 ```

 
# Global parameters
[global]
                workgroup = ODM
                realm = ODM.LAN
                netbios name = ODM-GW-SRV01
                server role = domain controller
                server services = smb, s3fs, rpc, nbt, wrepl, ldap, cldap, kdc, drepl, winbind, ntp_signd, kcc, dnsupdate
                idmap_ldb:use rfc2307 = yes
                acl:search = false
                interfaces = 10.1.1.1/24 LAN lo 127.0.0.1
                bind interfaces only = yes
                allow dns updates = True
 
                dcerpc endpoint servers = +winreg +srvsvc
                wins support = yes 
                wins proxy = yes 
                template shell = /bin/bash 
                winbind enum users = yes 
                winbind enum groups = yes 
                winbind use default domain = yes 
                winbind expand groups = 4 
                winbind nss info = rfc2307 
                winbind refresh tickets = Yes
                winbind offline logon = yes 
                winbind normalize names = Yes
                idmap config HOME:schema_mode = rfc2307
                idmap config HOME:range = 20000-3100000
                idmap config HOME:backend = ad
                idmap config *:range = 1100-2000
                idmap config *:backend = tdb
 
[netlogon]
                path = /var/lib/samba/sysvol/odm.lan/scripts
                read only = No
 
[sysvol]
                path = /var/lib/samba/sysvol
                read only = No
 
[profiles]
                comment = Users Profile Directories
                path = /data/profiles
                read only = no
                create mask = 0600
                directory mask = 0700
                #profile acls = yes
 
[homes]
                comment = Users Homes Directories
                path = /data/homes
                read only = no
                create mask = 0600
                directory mask = 0700
                #profile acls = yes
 
[printers]
                comment = All Printers
                path = /data/print/spool
                #guest ok = yes
                printable = yes
                read only = no
 
[shares]
                comment = Global share for all users
                path = /data/global
                read only = No
                directory mask = 0777
                create mask = 0777
```
 
Suggestions?
Thank you. 
PS: getent passwd, is working now but only with Administrator in nslcd.conf. It looks not safe to me. I would like to use a specific ldap user.

---

### Post by Roswebnet on 2013-05-29
Basic authentication is working now. There are my steps:
```

apt-get install dpkg-dev
apt-get build-dep samba4
apt-get source samba4
service samba4 stop
 
rm /etc/samba/smb.conf
rm -R /var/lib/samba/private/*
rm -R /var/lib/samba/sysvol/*
 
#pay attention I use default Windows 2003 functional level (Thank you Toxic64)
samba-tool domain provision \--realm=ODM.LAN \--domain=ODM \--adminpass='Pa$$w0rd' \--dns-backend=BIND9_DLZ \--use-xattr=yes \--use-rfc2307 \--host-ip=10.1.1.1
 
sudo vim /etc/samba/smb.conf
#add the smb or smbclient will not work properly
server services = smb, s3fs, rpc, nbt, wrepl, ldap, cldap, kdc, drepl, winbind, ntp_signd, kcc, dnsupdate
 
apt-get install smbclient samba-common-bin
service samba4 restart
 
```
Further steps can token from this tutorial:&#8221;
[http://www.matrix44.net/cms/notes/gnulinux/samba-4-ad-domain-with-ubuntu-12-04](http://www.matrix44.net/cms/notes/gnulinux/samba-4-ad-domain-with-ubuntu-12-04)
Install squid3
And by basic authentication use next code:
```

/usr/lib/squid3/squid_ldap_auth -u cn -b "cn=Users,dc=odm,dc=lan" 10.1.1.1
ldap Pa$$w0rd
OK

```
Ldap user must be created in RSAT. Full squid3 code looks like this:
```

auth_param basic credentialsttl 1 minute
auth_param basic children 10
auth_param basic program /usr/lib/squid3/squid_ldap_auth -u cn -b "cn=Users,dc=odm,dc=lan" -h 10.1.1.1
auth_param basic realm ODM.LAN

```
Do not forget to point the user&#8217;s web browser to the proxy server. Transparent proxy will not work in this scenario : (
The ldap_group_auth is still under researching.
Later I will report if I will found something.
P.S.: I got Idea to write kind of Ubuntu Home/Business Server tutorial, maybe some of you will like it.

---

