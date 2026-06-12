---
title: "LDAP groups/users takes precedence over Local group"
date: 2010-09-09
forum: Server Platforms
---

### Post by Phillip Thomas on 2010-09-09
I recently setup an Ubuntu server as an LDAP client. All authentication is working, but I have one issue: it seems LDAP groups are taking precedence over Local groups. This also seems to occur with users, but there is little overlap in users since we only maintain one human Local user and all Directory users have uids far above the typical Local uids.

To get LDAP up and running, I basically did the following two things: 
- Installed nslcd and configured it via the associated prompts, including the requisite packages.
- Installed auth-client-config and used the "open_ldap" profile found here:  [LDAPClientAuthentication]("https://help.ubuntu.com/community/LDAPClientAuthentication")

Example:
Local user labadmin has uid 1000
Directory user diradmin has uid 1000
Local admin group has gid 109
Directory admin group has gid 80

```
labadmin@labvm1:~$ getent passwd labadmin
labadmin:x:1000:1000:Lab Administrator,,,:/home/labadmin:/bin/bash

labadmin@labvm1:~$ getent passwd diradmin
diradmin:x:1000:20:Directory Administrator:/home/diradmin:/bin/bash

labadmin@labvm1:~$ getent passwd 1000
diradmin:x:1000:20:Directory Administrator:/home/diradmin:/bin/bash
```
```
labadmin@labvm1:~$ getent group admin
admin:*:80:diradmin

labadmin@labvm1:~$ getent group 109
admin:x:109:labadmin

labadmin@labvm1:~$ getent group 80
admin:*:80:diradmin
```

The problem, you see, is that looking up the user based on uid returns the Directory user diradmin instead of the Local user labadmin. Similarly, and more problematic, is that looking up the 'admin' group returns the Directory group, instead of the local group.

I would prefer to have the Local groups take precedence and just ensure that Directory users are members where needed via /etc/security/group.conf.

Any help is appreciated.

---

### Post by LightningCrash on 2010-09-20
sounds like it's in /etc/nsswitch.conf

you'll have to establish the priority there AFAIK

Yeah, it's there in the HOWTO:
[https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)

> 
After the installation of the necessary packages you will need to configure the Name Service and PAM.

Name Service

In /etc/nsswitch.conf replace compat with files ldap for both the passwd and group entries so you get something like this:

passwd:         files ldap
group:          files ldap

There is a full example provided in the documentation of libnss-ldap: /usr/share/doc/libnss-ldap/examples/nsswitch.ldap

Because the nscd daemon caches the lookup results, you need to restart it:

$ /etc/init.d/nscd restart

---

### Post by Phillip Thomas on 2010-09-20
It is my understanding that my example wouldn't have even worked had I not edited /etc/nsswitch.conf as such.

I have those datasources correctly configured in all methods I've tried, yet none correctly allow a local user/group to always take precedence over one found in ldap.

I have followed the official server documentation, the community documentation, including following the wiki step-by-step, just following the "7.10 and later" section, and following the OS X documentation that is linked from the wiki page.

All have subtle differences, none of which change my issue above. Either the user or the group, or both, from LDAP will be "considered" instead of the local one.


The only fix I've found is to simply filter them out by using nslcd and using custom search filters in /etc/nslcd.conf.

---

### Post by LightningCrash on 2010-09-20
Maybe you could post more of your config, because I have never had this problem.

---

### Post by Phillip Thomas on 2010-09-20
I'll be a little more details.

If I follow, for example, the "LDAP Authentication" section of the official server documentation found here: [OpenLDAP Server]("https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html"), the getent queries seem okay.

However, though the directory user with uid number 1000 can log in to the console (good), the shell prompt will not show the correct uid "diradmin," but instead shows the uid of the local user with uid number 1000: labadmin. (bad)

Another issue I run into is that LDAP users can not use sudo due to a setuid error (I believe there are some bug reports about this). To resolve/fix/workaround this issue, I install a cacheing daemon: nscd. Once that is installed, I get the aforementioned getent behavior, though my directory users can now use sudo.

Here are what I believe to be the relevant files after following the documentation I just mentioned. If I miss anything, just ask and I'll post it up. Also, I've removed commented sections since some files are very long with them (ldap.conf).

/etc/nsswitch.conf
```
# /etc/nsswitch.conf
passwd: files ldap
group: files ldap
shadow: files ldap
hosts:          files dns
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup: nis
```

/etc/ldap.conf
```
base dc=ldap,dc=xxxx,dc=xxxx,dc=edu
uri ldaps://ldap.xxxx.xxxx.edu
ldap_version 3
pam_password md5
nss_initgroups_ignoreusers backup,bin,daemon,games,gnats,irc,libuuid,list,lp,mail,man,news,proxy,root,sshd,sync,sys,syslog,uucp,www-data
```

/etc/ldap/ldap.conf
```
TLS_REQCERT	never
```

/etc/nscd.conf
```
	debug-level		0
	paranoia		no
	enable-cache		passwd		yes
	positive-time-to-live	passwd		600
	negative-time-to-live	passwd		20
	suggested-size		passwd		211
	check-files		passwd		yes
	persistent		passwd		yes
	shared			passwd		yes
	max-db-size		passwd		33554432
	auto-propagate		passwd		yes
	enable-cache		group		yes
	positive-time-to-live	group		3600
	negative-time-to-live	group		60
	suggested-size		group		211
	check-files		group		yes
	persistent		group		yes
	shared			group		yes
	max-db-size		group		33554432
	auto-propagate		group		yes
	enable-cache		hosts		no
	positive-time-to-live	hosts		3600
	negative-time-to-live	hosts		20
	suggested-size		hosts		211
	check-files		hosts		yes
	persistent		hosts		yes
	shared			hosts		yes
	max-db-size		hosts		33554432
	enable-cache		services	yes
	positive-time-to-live	services	28800
	negative-time-to-live	services	20
	suggested-size		services	211
	check-files		services	yes
	persistent		services	yes
	shared			services	yes
	max-db-size		services	33554432
```

/etc/pam.d/common-account
```
account	[success=2 new_authtok_reqd=done default=ignore]	pam_unix.so 
account	[success=1 default=ignore]	pam_ldap.so 
account	requisite			pam_deny.so
account	required			pam_permit.so
```

/etc/pam.d/common-auth
```
auth	[success=2 default=ignore]	pam_unix.so nullok_secure
auth	[success=1 default=ignore]	pam_ldap.so use_first_pass
auth	requisite			pam_deny.so
auth	required			pam_permit.so
```

/etc/pam.d/common-password
```
password	[success=2 default=ignore]	pam_unix.so obscure sha512
password	[success=1 user_unknown=ignore default=die]	pam_ldap.so use_authtok try_first_pass
password	requisite			pam_deny.so
password	required			pam_permit.so
```

/etc/pam.d/common-session
```
session	[default=1]			pam_permit.so
session	requisite			pam_deny.so
session	required			pam_permit.so
session	required	pam_unix.so 
session	optional			pam_ldap.so
```

---

### Post by LightningCrash on 2010-09-23
I've been busy with CVE-2010-3081 (sigh) but I will try to look at my LDAP setups once I get done.

---

### Post by Phillip Thomas on 2010-09-23
No problem; I appreciate any help.

---

