---
title: "Accessing SAMBA AD on Ubuntu Server 14.04 via SSSD"
date: 2014-07-01
forum: Server Platforms
---

### Post by Roswebnet on 2014-07-01
[FONT=Calibri][SIZE=3][COLOR=#000000]Hieveryone,[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]I would liketo access my samba domain controller via SSSD using LDAP and/or Kerberos. Didanyone already tried it? How it is working?[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]Sambaconfiguration.[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]My provision:[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]```
samba-tool domain provision \--realm=DOT.LAN \--domain=DOT \--adminpass='Pa77w0rd' \--dns-backend=BIND9_DLZ \--server-role=dc \--use-xattr=yes \--use-rfc2307  \--function-level=2008_R2 \--use-ntvfs

``` [/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]Bind,apparmor,krb5 have a correct configuration, there is no errors in logs.  
Windows 8.1 client can connect to DC without any problems by an admin account[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]/etc/samba/smb.conf[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]```

# Global parameters
[global]
 workgroup = DOT
 realm = DOT.LAN
 netbios name = SRV01
 server role = active directory domain controller
 server services = rpc, nbt, wrepl, ldap, cldap, kdc, drepl, winbind, ntp_signd, kcc, dnsupdate, smb
 dcerpc endpoint servers = epmapper, wkssvc, rpcecho, samr, netlogon, lsarpc, spoolss, drsuapi, dssetup, unixinfo, browser, eventlog6, backupkey, dnsserver, winreg, srvsvc
 idmap_ldb:use rfc2307 = yes
[netlogon]
 path = /var/lib/samba/sysvol/dot.lan/scripts
 read only = No
[sysvol]
 path = /var/lib/samba/sysvol
 read only = No

``` 
[/COLOR][/SIZE][/FONT] 
 
[FONT=Calibri][SIZE=3][COLOR=#000000]SSSD configuration.[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]/etc/sssd/sssd.conf[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]```

[sssd]
config_file_version = 2
domains = dot.lan
services = nss, pam
debug_level = 6
[nss]
filter_groups = root
filer_users = root
fallback_homedir = /home/%u
default_shell = /bin/bash
reconnection_retries = 3
[pam]
reconnection_retries = 3
[domain/dot.lan]
# Using id_provider=ad sets the best defaults on its own
#id_provider = ad
# In sssd, the default access provider is always 'permit'. The AD access
# provider by default checks for account expiration
#access_provider = ad
# Uncomment to use POSIX attributes on the server
# ldap_id_mapping=false
# Uncomment if the client machine hostname doesn't match the computer object on the DC.
# ad_hostname = dc1.samdom.example.com
# Uncomment if DNS SRV resolution is not working
# ad_server = dc1.samdom.example.com
# Uncomment if the domain section is named differently than your Samba domain
# ad_domain = samdom.example.com
# Enumeration is discouraged for performance reasons.
#enumerate = true

#debug_level=6
dyndns_update=true
#dyndns_refresh_interval=16
ad_hostname = srv01.dot.lan
ad_server = srv01.dot.lan
ad_domain = dot.lan
id_provider = ldap
access_provider = simple
enumerate = FALSE
cache_credentials = true
#entry_cache_timeout = 60
auth_provider = krb5
chpass_provider = krb5
krb5_realm = DOT.LAN
krb5_server = srv01.dot.lan
krb5_kpasswd = srv01.dot.lan
ldap_id_mapping=false
ldap_uri = [ldap://srv01.dot.lan](ldap://srv01.dot.lan)
ldap_schema = rfc2307bis
ldap_referrals = false
ldap_default_bind_dn = CN=sssd-connect,cn=Users,dc=dot,dc=lan
ldap_default_authtok_type = password
ldap_default_authtok = Pa77w0rd
ldap_user_search_base = dc=dot,dc=lan
ldap_user_object_class = user
ldap_user_name = cn
ldap_user_uid_number = uidNumber
ldap_user_gid_number = gidNumber
ldap_user_gecos = displayName
ldap_user_fullname = displayName
ldap_user_home_directory = unixHomeDirectory
ldap_user_principal = userPrincipalName
ldap_user_shell = loginShell
ldap_group_search_base = dc=dot,dc=lan
ldap_group_object_class = group
ldap_group_name = cn
ldap_group_member = member
access_provider = ldap
ldap_access_order = expire
ldap_account_expire_policy = ad
ldap_sasl_mech = gssapi
ldap_sasl_authid = [EMAIL="SRV01@DOT.LAN"]SRV01@DOT.LAN[/EMAIL]
krb5_keytab = /etc/krb5.sssd.keytab 
ldap_krb5_init_creds = true

``` 
[/COLOR][/SIZE][/FONT]The commands:
```
getent passwd
getent group
```

returning only Unix users.
[FONT=Calibri][SIZE=3][COLOR=#000000]Sources:[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000][https://wiki.samba.org/index.php/Local_user_management_and_authentication/sssd](https://wiki.samba.org/index.php/Local_user_management_and_authentication/sssd)
[https://fedorahosted.org/sssd/wiki/Configuring_sssd_with_ad_server](https://fedorahosted.org/sssd/wiki/Configuring_sssd_with_ad_server)
[http://wiki.eri.ucsb.edu/stadm/AD_Samba4#SSSD](http://wiki.eri.ucsb.edu/stadm/AD_Samba4#SSSD)
[http://www.linuxgfx.co.uk/karoshi/documentation/wiki/index.php?title=Samba4_Testing#SSSD_with_LDAP](http://www.linuxgfx.co.uk/karoshi/documentation/wiki/index.php?title=Samba4_Testing#SSSD_with_LDAP)
[http://www.linuxgfx.co.uk/karoshi/documentation/wiki/index.php?title=Samba4_Testing#SSSD_Authentication_with_Kerberos](http://www.linuxgfx.co.uk/karoshi/documentation/wiki/index.php?title=Samba4_Testing#SSSD_Authentication_with_Kerberos)
[http://linuxcostablanca.blogspot.nl/2013/04/sssd-in-samba-40.html](http://linuxcostablanca.blogspot.nl/2013/04/sssd-in-samba-40.html)
[http://stackoverflow.com/questions/18825848/sssd-authentication-with-samba-4](http://stackoverflow.com/questions/18825848/sssd-authentication-with-samba-4)
[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]Thank you.[/COLOR][/SIZE][/FONT]

---

### Post by Roswebnet on 2014-07-03
Yes! I got something working based on Kerberos:

```
apt-get install sssd
vim /etc/sssd/sssd.conf
chown root:root /etc/sssd/sssd.conf
chmod 600 /etc/sssd/sssd.conf
 
samba-tool domain exportkeytab /etc/krb5.keytab --principal=srv01$
chown root:root /etc/krb5.keytab
chmod 600 /etc/krb5.keytab
```


And my sssd.conf looking like this:
```
[sssd]
services = nss, pam
config_file_version = 2
domains = dot.lan
reconnection_retries = 3
[nss]
filter_groups = root
filer_users = root
fallback_homedir = /srv/samba/home/%u
default_shell = /bin/bash
reconnection_retries = 3
[pam]
reconnection_retries = 3
[domain/dot.lan]
# Uncomment if you need offline logins
cache_credentials = true
id_provider = ad
auth_provider = ad
access_provider = ad
# Uncomment if service discovery is not working
ad_server = srv01.dot.lan
# Uncomment if the domain section is named differently than your Samba domain
ad_domain = dot.lan
# Uncomment if you want to use POSIX UIDs and GIDs set on the AD side
# ldap_id_mapping = False
# Comment out if the users have the shell and home dir set on the AD side
#fallback_homedir = /srv/samba/home/%u
#default_shell = /bin/bash
# Uncomment and adjust if the default principal SHORTNAME$@REALM is not available
# ldap_sasl_authid = [EMAIL="host/client.ad.example.com@AD.EXAMPLE.COM"]host/client.ad.example.com@AD.EXAMPLE.COM[/EMAIL]
# Comment out if you prefer to user shortnames.
#use_fully_qualified_names = true
# Enumeration is discouraged for performance reasons.
enumerate = true

```

Now I need to understand how to join a Linux server with samba, but in DC I can login just with [EMAIL="administrator@dot.lan"]administrator@dot.lan[/EMAIL] with root rights

To get admin group just do with /etc/sudoers following steeps:

```
chmod 740 /etc/sudoers

vim /etc/sudoers
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%Domain\x20Admins ALL=(ALL) ALL

chmod 440 /etc/sudoers
reboot
```

With use_fully_qualified_names = true  in sssd.conf I could not get sudo rights on Domain Admins group. However, I can log with fully qualified name on ssh. **Strange**.

 To create during the login procedure user directory defined in sssd.conf, just put after session optional pam_sss.so in /etc/pam.d/common-session:

```
session optional pam_mkhomedir.so skel = /etc/skel/ mask=0077
```


Sources:
[https://wiki.samba.org/index.php/Local_user_management_and_authentication/sssd#Method_1:_Connecting_to_AD_via_Kerberos_.28recommended.29](https://wiki.samba.org/index.php/Local_user_management_and_authentication/sssd#Method_1:_Connecting_to_AD_via_Kerberos_.28recommended.29)
[https://fedorahosted.org/sssd/wiki/Configuring_sssd_with_ad_server#etcsssdsssd.conf](https://fedorahosted.org/sssd/wiki/Configuring_sssd_with_ad_server#etcsssdsssd.conf)
[http://www.linuxgfx.co.uk/karoshi/documentation/wiki/index.php?title=Samba4_Testing#SSSD_with_LDAP](http://www.linuxgfx.co.uk/karoshi/documentation/wiki/index.php?title=Samba4_Testing#SSSD_with_LDAP)
[http://www.linuxgfx.co.uk/karoshi/documentation/wiki/index.php?title=Samba4_Testing#SSSD_Authentication_with_Kerberos](http://www.linuxgfx.co.uk/karoshi/documentation/wiki/index.php?title=Samba4_Testing#SSSD_Authentication_with_Kerberos)
[http://ubuntuforums.org/showthread.php?t=2182061](http://ubuntuforums.org/showthread.php?t=2182061)
[http://www.itadmintools.com/2012/02/ubuntu-1110-logging-into-active.html](http://www.itadmintools.com/2012/02/ubuntu-1110-logging-into-active.html)

---

