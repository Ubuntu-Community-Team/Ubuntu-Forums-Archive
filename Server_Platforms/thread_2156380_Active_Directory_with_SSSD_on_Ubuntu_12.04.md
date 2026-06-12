---
title: "Active Directory with SSSD on Ubuntu 12.04"
date: 2013-06-21
forum: Server Platforms
---

### Post by World_emp on 2013-06-21
I followed this guide: [http://www.lancs.ac.uk/iss/tsg/unix-ad/]("http://www.lancs.ac.uk/iss/tsg/unix-ad/") to configure a Ubuntu 12.04.02 Client to authenticate on Active Directory (on a Windows 2008R2 Server), i did everything step by step but I'm not able to see any remote users.

This are my config files:

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat sss
group:          compat sss
shadow:         compat sss

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis sss
```

```
[sssd]
debug_level = 3
config_file_version = 2
reconnection_retries = 3
sbus_timeout = 30
services = nss, pam

domains = TESTSUPSI.CH

[nss]
debug_level = 3
filter_groups = root
filter_users = root,ldap,named,avahi,haldaemon,dbus,radvd,tomcat,radiusd,news,mailman,nscd
reconnection_retries = 3
entry_cache_nowait_percentage = 50

[pam]
debug_level = 3
reconnection_retries = 3
offline_failed_login_attempts = 5
offline_failed_login_delay = 5

[domain/TESTSUPSI.CH]
enumerate = true
min_id = 200
debug_level = 3
ldap_tls_reqcert = never
ldap_id_use_start_tls = False
cache_credentials = true

dns_discovery_domain = TESTSUPSI.CH

auth_provider = krb5
krb5_realm = TESTSUPSI.CH

id_provider = ldap
ldap_search_base = dc=TESTSUPSI,dc=CH
ldap_schema = rfc2307bis
ldap_sasl_mech=gssapi
ldap_sasl_authid=UBUNTU1$@TESTSUPSI.CH
ldap_user_object_class = user
ldap_user_name = sAMAccountName
ldap_user_gecos = displayName
ldap_user_home_directory = unixHomeDirectory
ldap_user_uuid = objectGUID
ldap_user_modify_timestamp = whenChanged
ldap_user_principal = userPrincipalName
ldap_force_upper_case_realm = True
ldap_group_object_class = group
ldap_group_name = sAMAccountName
ldap_group_uuid = objectGUID
ldap_group_modify_timestamp = whenChanged
ldap_group_nesting_level = 2
ldap_user_search_base = ou=Users,dc=TESTSUPSI,dc=CH
ldap_group_search_base = ou=Groups,dc=TESTSUPSI,dc=CH

access_provider = ldap
ldap_access_filter = memberOf=CN=tig_systems_unix_admins,OU=TIG,OU=ISS,OU=Groups,OU=University,DC=TESTSUPSI,DC=CH
ldap_account_expire_policy = ad
ldap_access_order = filter,expire
```

krb5.conf
```
[libdefaults]
	default_realm = TESTSUPSI.CH
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

[login]
	krb4_convert = true
	krb4_get_tickets = false
```

Can anyone help me out please?

---

