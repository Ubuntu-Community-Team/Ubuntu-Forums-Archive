---
title: "Samba Winbind problem"
date: 2007-11-14
forum: Server Platforms
---

### Post by Gone fishing on 2007-11-14
I’m having a real problem getting winbind to work with our domain server SAMBA version:3.0.26a. Winbind used to work fine with the old server running an old version of samba

The Globals of my smb.conf looks like:


# Samba config file created using SWAT
# from 0.0.0.0 (0.0.0.0)
# Date: 2005/07/04 14:40:01

# Global parameters
[global]
	logon drive = H:
	domain master = Yes
	map to guest = Bad User
	username map = /etc/samba/smbusers
	encrypt passwords = yes
	printer admin = @ntadmin, root, administrator
	logon home = \\%L\%u\.win_profile\%m
	wins support = Yes
	printcap cache time = 750
	cups options = raw
	ldap machine suffix = ou=Computers
	logon script = logon.bat
	ldap suffix = dc=example,dc=com
	workgroup = MACHABENG
	logon path = \\%L\profiles\%u\%m
	os level = 65
	printcap name = cups
	security = DOMAIN
	preferred master = Yes
	add machine script = /usr/sbin/useradd  -c Machine -d /var/lib/nobody -s /bin/false %m$
	ldap idmap suffix = ou=Idmap
	domain logons = Yes

If I run the following command things seem to work 

wbinfo -t
checking the trust secret via RPC calls succeeded

wbinfo -u

produces a list of users

getent passwd

guidance:x:10005:10000:guidance:/home/MACHABENG/guidance:/bin/bash
science:x:10006:10000:science:/home/MACHABENG/science:/bin/bash
humanities:x:10007:10000:humanities:/home/MACHABENG/humanities:/bin/bash

however,

sudo wbinfo -a user%password

plaintext password authentication failed
error code was NT_STATUS_NO_LOGON_SERVERS (0xc000005e)
error messsage was: No logon servers
Could not authenticate user asta%verity with plaintext password
challenge/response password authentication failed
error code was NT_STATUS_NO_LOGON_SERVERS (0xc000005e)
error messsage was: No logon servers
Could not authenticate user asta with challenge/response
jhumphreys@ubuntu5-desktop:~$


Well I’m stuck may be a bug in SAMBA version:3.0.26a. Is there a better way of getting a username and password from a Linux server than winbind?

---

