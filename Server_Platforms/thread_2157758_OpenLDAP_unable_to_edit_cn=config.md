---
title: "OpenLDAP unable to edit cn=config"
date: 2013-06-26
forum: Server Platforms
---

### Post by sdmike6 on 2013-06-26
How I setup my working LDAP with the script here: [http://www.ghacks.net/2010/08/31/set-up-your-ldap-server-on-ubuntu-10-04/](http://www.ghacks.net/2010/08/31/set-up-your-ldap-server-on-ubuntu-10-04/)


I'm now using Ubuntu 12.04 Server x64


Working on this module here: [http://raerek.blogspot.com/2012/06/sync-ldap-and-samba-passwords-using.html](http://raerek.blogspot.com/2012/06/sync-ldap-and-samba-passwords-using.html)


When I load changes into LDAP I'm denied.


$ sudo ldapmodify -Q -Y EXTERNAL -H ldapi:/// -f smbkrb5pwd_load.ldif
modifying entry "cn=module{0},cn=config"
ldap_modify: Insufficient access (50)


$ sudo ldapmodify -Y EXTERNAL -H ldapi:/// -f smbkrb5pwd_load.ldif
ldap_sasl_interactive_bind_s: Unknown authentication method (-6)
	additional info: SASL(-4): no mechanism available:




$ ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W olcDatabase=hdb olcAccess 
Enter LDAP Password: 
dn: olcDatabase={1}hdb,cn=config
olcAccess: {0}to attrs=userPassword,shadowLastChange by dn="cn=admin,dc=domain,dc=net" write by anonymous auth by self write by * none
olcAccess: {1}to dn.base="" by * read
olcAccess: {2}to * by dn="cn=admin,dc=domain,dc=net" write by * read


Am I able to change the ACL so I can edit cn=config to load this module in? If so how do I do that?

---

### Post by sdmike6 on 2013-06-27
I tried binding as the rootdn and I'm still not able to make changes to c"cn=module{0},cn=config"

$ sudo ldapmodify -x -v -D 'cn=admin,dc=domain,dc=net' -w 'secret' -f smbkrb5pwd_load.ldif 
ldap_initialize( <DEFAULT> )
add olcModuleLoad:
smbkrb5pwd
modifying entry "cn=module{0},cn=config"
ldap_modify: Insufficient access (50)

---

### Post by sdmike6 on 2013-07-01
Bump!

---

