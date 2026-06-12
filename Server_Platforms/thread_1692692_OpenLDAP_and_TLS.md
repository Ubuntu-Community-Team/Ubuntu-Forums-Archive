---
title: "OpenLDAP and TLS"
date: 2011-02-21
forum: Server Platforms
---

### Post by headvampyre@hotmail.co.uk on 2011-02-21
Hi, ive installed OpenLDAP on ubuntu lucid, configured the schemas, frontends, etc. but im having an issue starting slapd when TLS is enabled. I followed [https://help.ubuntu.com/10.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.10/serverguide/C/openldap-server.html)
but no success. 
Permissions are configured correctly for all Certificates, CA's and Keys.
Heres some of the output when i run slapd -d 100000:

[B]=> access_allowed: search access to "olcDatabase={0}config,cn=config" "objectClass" requested
<= root access granted
=> access_allowed: search access granted by manage(=mwrscxd)
<= test_filter 6
Backend ACL: access to *
	by dn.base="gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth" manage
	by * +0 break

/etc/ldap/slapd.d: line 1: warning: cannot assess the validity of the ACL scope within backend naming context
=> test_filter
    PRESENT
=> access_allowed: search access to "olcDatabase={1}hdb,cn=config" "objectClass" requested
<= root access granted
=> access_allowed: search access granted by manage(=mwrscxd)
<= test_filter 6
Backend ACL: access to attrs=userPassword
	by dn.base="cn=root,dc=example,dc=com" write
	by anonymous auth
	by self write
	by * none

/etc/ldap/slapd.d: line 1: warning: cannot assess the validity of the ACL scope within backend naming context
Backend ACL: access to attrs=shadowLastChange
	by self write
	by * read

/etc/ldap/slapd.d: line 1: warning: cannot assess the validity of the ACL scope within backend naming context
Backend ACL: access to dn.base=""
	by * read

/etc/ldap/slapd.d: line 1: warning: ACL appears to be out of scope within backend naming context
Backend ACL: access to *
	by dn.base="cn=root,dc=example,dc=com" write
	by * read

/etc/ldap/slapd.d: line 1: warning: cannot assess the validity of the ACL scope within backend naming context
main: TLS init def ctx failed: -1
slapd stopped.
connections_destroy: nothing to destroy.
[/B]

Could anyone help me to a solution to this, i cant find any documentation related to this error. Thanks in advance.

---

