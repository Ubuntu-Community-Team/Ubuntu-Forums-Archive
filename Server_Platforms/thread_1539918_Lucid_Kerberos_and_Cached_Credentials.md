---
title: "Lucid: Kerberos and Cached Credentials"
date: 2010-07-27
forum: Server Platforms
---

### Post by apalacheno on 2010-07-27
Hi,
has anybody managed to get kerberos and offline authentication via pam_krb5.so and pam_ccreds.so working in lucid?

In karmic it works like a charm, but the same config on lucid does not work (it works perfectly as long as the network is connected though):

/etc/pam.d/common-account:
```

account		sufficient					pam_unix.so nullok_secure
account		sufficient					pam_krb5.so
account		required					pam_permit.so

```

/etc/pam.d/common-auth:
```

auth		[success=4 default=ignore]			pam_unix.so
auth		[success=1 authinfo_unavail=ignore default=die]	pam_krb5.so use_first_pass
auth		[success=2 default=die]				pam_ccreds.so action=validate use_first_pass
auth		[default=1]					pam_ccreds.so action=store
auth		requisite					pam_deny.so
auth		optional					pam_mount.so

```

/etc/pam.d/common-password:
```

password	requisite					pam_krb5.so
password	[success=2 default=ignore]			pam_unix.so obscure use_authtok try_first_pass sha512
password	[success=1 user_unknown=ignore default=die]	pam_ldap.so use_authtok try_first_pass
password	requisite					pam_deny.so
password	required					pam_permit.so

```

/etc/pam.d/common-session:
```

session		required					pam_mkhomedir.so skel=/etc/skel/ umask=0027
session		[default=1]					pam_permit.so
session		requisite					pam_deny.so
session		required					pam_permit.so
session		optional					pam_krb5.so
session		required					pam_unix.so
session		optional					pam_mount.so
session		optional					pam_ldap.so
session		optional					pam_ck_connector.so nox11

```

Immediately after trying to log in I get the message "Permission denied":

```

loc@vm-ubuntu:~$ su ro
Passwort: 
You have been logged on using cached credentials.
su: Permission denied
loc@vm-ubuntu:~$ 

```

This is the error log I'm getting:

```

Jul 27 11:19:08 vm-ubuntu su[2120]: nss_ldap: could not connect to any LDAP server as (null) - Can't contact LDAP server
Jul 27 11:19:08 vm-ubuntu su[2120]: nss_ldap: failed to bind to LDAP server ldap://ldap.example.org: Can't contact LDAP server
Jul 27 11:19:08 vm-ubuntu su[2120]: nss_ldap: could not search LDAP server - Server is unavailable
Jul 27 11:19:08 vm-ubuntu su[2120]: pam_krb5(su:auth): authentication failure; logname=ro uid=1000 euid=0 tty=/dev/pts/2 ruser=loc rhost=
Jul 27 11:19:10 vm-ubuntu su[2120]: pam_authenticate: Permission denied
Jul 27 11:19:10 vm-ubuntu su[2120]: FAILED su for ro by loc
Jul 27 11:19:10 vm-ubuntu su[2120]: - /dev/pts/2 loc:ro

```

The credentials are cached - a 'getent passwd' and 'getent group' shows the LDAP users and groups even in offline mode.

Any pointers?

Cheers,
Robert

---

### Post by apalacheno on 2010-07-27
These are the steps I did to implement cached credentials on the client.

1. Install required packages:

```

apt-get -y install libpam-krb5 krb5-user ldap-auth-client nss-updatedb libnss-db libpam-ccreds

```

2. Configure Kerberos:

/etc/krb5.conf:
```

[libdefaults] 
	default_realm = EXAMPLE.ORG 

[realms]
	EXAMPLE.ORG = {
		kdc = kerberos.example.org
		admin_server = kerberos.example.org
		master_kdc = kerberos.example.org
		default_domain = example.org
	}

```

3. Specify LDAP server:

/etc/ldap/ldap.conf:
```

BASE		dc=example,dc=org
URI		ldap://ldap.example.org

```

/etc/ldap.conf:
```

base				dc=example,dc=org
uri				ldap://ldap.example.org
ldap_version			3
pam_password			md5

tls_checkpeer			yes
bind_policy			soft
bind_timelimit			5
timelimit			5
nss_base_passwd			ou=users,ou=accounts,dc=example,dc=org?one
nss_base_shadow			ou=users,ou=accounts,dc=example,dc=org?one
nss_base_group			ou=groups,ou=accounts,dc=example,dc=org?one
nss_initgroups_ignoreusers	amavis,aptproxy,avahi,avahi-autoipd,backup,bin,bind,clamav,couchdb,daemon,dhcpd,dkim-filter,dovecot,freerad,ftp,games,gdm,gnats,haldaemon,hplip,irc,kernoops,libuuid,list,lp,mail,man,messagebus,mysql,news,ntp,openldap,openvpn,polkituser,postfix,postgres,proxy,pulse,root,saned,speech-dispatcher,sshd,statd,sync,sys,sys_backup,syslog,uucp,www-data

```

4. Configure NSS:

/etc/nsswitch.conf:
```

passwd:		files ldap [NOTFOUND=return] db
group:		files ldap [NOTFOUND=return] db
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

5. Update the local database once:

```

nss_updatedb ldap

```

Cheers,
Robert

---

### Post by apalacheno on 2010-07-28
I even tried the configuration that pam-auth-update (version 10-5) from the maverick repository spits out:

/etc/pam.d/common-account:
```

account	[success=2 new_authtok_reqd=done default=ignore]	pam_unix.so 
account	[success=1 default=ignore]	pam_ldap.so 
account	requisite			pam_deny.so
account	required			pam_permit.so
account	required			pam_krb5.so minimum_uid=1000

```

/etc/pam.d/common-auth:
```

auth	[success=5 default=ignore]	pam_krb5.so minimum_uid=1000
auth	[success=4 default=ignore]	pam_unix.so nullok_secure try_first_pass
auth	[success=3 default=ignore]	pam_ldap.so use_first_pass
auth	[success=2 default=ignore]	pam_ccreds.so minimum_uid=1000 action=validate use_first_pass
auth	[default=ignore]		pam_ccreds.so minimum_uid=1000 action=update
auth	requisite			pam_deny.so
auth	required			pam_permit.so
auth	optional			pam_ccreds.so minimum_uid=1000 action=store

```

/etc/pam.d/common-password:
```

password	requisite			pam_krb5.so minimum_uid=1000
password	[success=2 default=ignore]	pam_unix.so obscure use_authtok try_first_pass sha512
password	[success=1 user_unknown=ignore default=die]	pam_ldap.so use_authtok try_first_pass
password	requisite			pam_deny.so
password	required			pam_permit.so
password	optional			pam_gnome_keyring.so 

```

/etc/pam.d/common-session:
```

session	[default=1]			pam_permit.so
session	requisite			pam_deny.so
session	required			pam_permit.so
session	optional			pam_krb5.so minimum_uid=1000
session	required			pam_unix.so 
session	optional			pam_ldap.so 
session	optional			pam_ck_connector.so nox11

```

No luck either (again, as long as the client is online, everything works perfectly):

```

loc@vm-ubuntu:~$ su ro
Password: 
You have been logged on using cached credentials.
su: Authentication failure
loc@vm-ubuntu:~$ 

```

```

Jul 27 11:30:34 vm-ubuntu su[2133]: pam_krb5(su:auth): authentication failure; logname=ro uid=1000 euid=0 tty=/dev/pts/2 ruser=loc rhost=
Jul 27 11:30:34 vm-ubuntu su[2133]: nss_ldap: could not connect to any LDAP server as (null) - Can't contact LDAP server
Jul 27 11:30:34 vm-ubuntu su[2133]: nss_ldap: failed to bind to LDAP server ldap://ldap.example.org: Can't contact LDAP server
Jul 27 11:30:34 vm-ubuntu su[2133]: nss_ldap: could not search LDAP server - Server is unavailable
Jul 27 11:30:34 vm-ubuntu su[2133]: pam_ldap: ldap_simple_bind Can't contact LDAP server
Jul 27 11:30:34 vm-ubuntu su[2133]: pam_ldap: reconnecting to LDAP server...
Jul 27 11:30:34 vm-ubuntu su[2133]: pam_ldap: ldap_simple_bind Can't contact LDAP server
Jul 27 11:30:34 vm-ubuntu su[2133]: pam_ccreds: illegal option minimum_uid=1000
Jul 27 11:30:34 vm-ubuntu su[2133]: pam_ccreds: illegal option minimum_uid=1000
Jul 27 11:30:34 vm-ubuntu su[2133]: nss_ldap: could not connect to any LDAP server as (null) - Can't contact LDAP server
Jul 27 11:30:34 vm-ubuntu su[2133]: nss_ldap: failed to bind to LDAP server ldap://ldap.example.org: Can't contact LDAP server
Jul 27 11:30:34 vm-ubuntu su[2133]: nss_ldap: could not search LDAP server - Server is unavailable
Jul 27 11:30:34 vm-ubuntu su[2133]: pam_ldap: ldap_simple_bind Can't contact LDAP server
Jul 27 11:30:34 vm-ubuntu su[2133]: pam_ldap: reconnecting to LDAP server...
Jul 27 11:30:34 vm-ubuntu su[2133]: pam_ldap: ldap_simple_bind Can't contact LDAP server
Jul 27 11:30:34 vm-ubuntu su[2133]: pam_acct_mgmt: Authentication failure
Jul 27 11:30:34 vm-ubuntu su[2133]: FAILED su for ro by loc
Jul 27 11:30:34 vm-ubuntu su[2133]: - /dev/pts/2 loc:ro

```

Cheers,
Robert

---

### Post by apalacheno on 2010-08-03
After days of pulling my hair out, the PAM config from my first post works fine with this /etc/pam.d/common-auth:

```

auth		[success=4 default=ignore]			pam_unix.so
auth		[success=1 authinfo_unavail=ignore default=die]	pam_krb5.so use_first_pass
auth		[success=2 default=die]				pam_ccreds.so action=validate use_first_pass
auth		[default=1]					pam_ccreds.so action=store
auth		requisite					pam_deny.so
auth		required					pam_permit.so
auth		optional					pam_mount.so

```

Note the line "**auth	required	pam_permit.so**" before the *pam_mount* line.

Cheers,
Robert

---

