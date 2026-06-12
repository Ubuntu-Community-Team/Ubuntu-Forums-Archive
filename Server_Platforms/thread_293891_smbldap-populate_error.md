---
title: "smbldap-populate error"
date: 2006-11-05
forum: Server Platforms
---

### Post by nagindian on 2006-11-05
i am getting the following error when i give
smbldap-populate
Populating LDAP directory for domain test (S-1-5-21-2779949074-1403611050-451456 209)
(using builtin directory structure)

entry dc=ubuntutest, dc=com already exist.
adding new entry: ou=Users,dc=ubuntutest, dc=com
failed to add entry: modifications require authentication at /usr/sbin/smbldap-p opulate line 495, <GEN1> line 3.
adding new entry: ou=Groups,dc=ubuntutest, dc=com
failed to add entry: modifications require authentication at /usr/sbin/smbldap-p opulate line 495, <GEN1> line 4.
adding new entry: ou=Machines,dc=ubuntutest, dc=com
failed to add entry: modifications require authentication at /usr/sbin/smbldap-p opulate line 495, <GEN1> line 5.
adding new entry: ou=Idmap,dc=ubuntutest, dc=com
failed to add entry: modifications require authentication at /usr/sbin/smbldap-p opulate line 495, <GEN1> line 6.
adding new entry: uid=root,ou=Users,dc=ubuntutest, dc=com
failed to add entry: modifications require authentication at /usr/sbin/smbldap-p opulate line 495, <GEN1> line 7.
adding new entry: uid=nobody,ou=Users,dc=ubuntutest, dc=com
failed to add entry: modifications require authentication at /usr/sbin/smbldap-p opulate line 495, <GEN1> line 8.
adding new entry: cn=Domain Admins,ou=Groups,dc=ubuntutest, dc=com
failed to add entry: modifications require authentication at /usr/sbin/smbldap-p opulate line 495, <GEN1> line 9.
adding new entry: cn=Domain Users,ou=Groups,dc=ubuntutest, dc=com
failed to add entry: modifications require authentication at /usr/sbin/smbldap-p opulate line 495, <GEN1> line 10.
adding new entry: cn=Domain Guests,ou=Groups,dc=ubuntutest, dc=com
failed to add entry: modifications require authentication at /usr/sbin/smbldap-p opulate line 495, <GEN1> line 11.
adding new entry: cn=Domain Computers,ou=Groups,dc=ubuntutest, dc=com
failed to add entry: modifications require authentication at /usr/sbin/smbldap-p opulate line 495, <GEN1> line 12.
adding new entry: cn=Administrators,ou=Groups,dc=ubuntutest, dc=com
failed to add entry: modifications require authentication at /usr/sbin/smbldap-p opulate line 495, <GEN1> line 16.
adding new entry: cn=Account Operators,ou=Groups,dc=ubuntutest, dc=com
failed to add entry: modifications require authentication at /usr/sbin/smbldap-p opulate line 495, <GEN1> line 18.
adding new entry: cn=Print Operators,ou=Groups,dc=ubuntutest, dc=com
failed to add entry: modifications require authentication at /usr/sbin/smbldap-p opulate line 495, <GEN1> line 19.
adding new entry: cn=Backup Operators,ou=Groups,dc=ubuntutest, dc=com
failed to add entry: modifications require authentication at /usr/sbin/smbldap-p opulate line 495, <GEN1> line 20.
adding new entry: cn=Replicators,ou=Groups,dc=ubuntutest, dc=com
failed to add entry: modifications require authentication at /usr/sbin/smbldap-p opulate line 495, <GEN1> line 21.
adding new entry: sambaDomainName=test,dc=ubuntutest, dc=com
failed to add entry: invalid DN at /usr/sbin/smbldap-populate line 495, <GEN1> l ine 21.

Please provide a password for the domain root:
/usr/sbin/smbldap-passwd: user root doesn't exist

---

