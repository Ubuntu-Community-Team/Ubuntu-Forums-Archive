---
title: "UBUNTU Samba File Server with Win LDAP Authentication"
date: 2012-09-10
forum: Server Platforms
---

### Post by bingham on 2012-09-10
I am trying to set up a samba file server (on 12.04) that will authenticate through our existing Windows 2008 r2 active directory server.  My smb.conf is below.  What I don't understand is that when I run "sudo smbclient -L <samba_ip> -U <user>" with the correct password I get the listing of shared folders, and when I supply the incorrect password I get "session setup failed: NT_STATUS_LOGON_FAILURE".  So, I feel like the authentication is working.  But, when I try to connect using "smbclient -U<user> \\\\<samba_ip>\\Profiles" I get, "NT_STATUS_ACCESS_DENIED".  And then if I set 'guest ok = yes' I can connect.



[global]
	workgroup = <WINDOWS_WORKGROUP>
	realm = <FQDN>
	server string = %h server (Samba, Ubuntu)
	security = ADS
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = ldapsam:ldap://<AD_IP>:389
	pam password change = Yes
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	add machine script = sudo /usr/sbin/smbldap-useradd -t 0 -w "%u"
	domain master = No
	ldap admin dn = cn=<admin_user>,ou=<admin_dir>,dc=<domain>,dc=BinghamAcademy,dc=net
	ldap passwd sync = yes
	ldap suffix = dc=<domain>,dc=BinghamAcademy,dc=net
	ldap ssl = no
	ldap user suffix = ou=<admin_dir>
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb

[Profiles]
	comment = Ubuntu File Server Share for User Profiles
	path = /srv/samba/win/profiles
	read only = No
	create mask = 0755
	guest ok = No

---

### Post by luvshines on 2012-09-11
Try increasing the 'log level' in smb.conf, restart the smbd service, try CIFS access and see what shows up in the logs.

---

