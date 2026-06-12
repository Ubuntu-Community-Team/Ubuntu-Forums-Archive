---
title: "problem configuring Samba &amp; LDAP"
date: 2011-12-29
forum: Server Platforms
---

### Post by fluca1978 on 2011-12-29
Hi all,
I'm trying to configure a server as openldap server and samba domain controller. I've followed the howto [here]("http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10-p2"), that worked for me for other two servers with pretty almost setup. However, now when I try to populate the ldap domain I got errors:

```

# smbldap-populate -u 30000 -g 30000
entry dc=myHost,dc=com already exist. 
entry ou=Users,dc=myHost,dc=com already exist. 
entry ou=Groups,dc=myHost,dc=com already exist. 
entry ou=Computers,dc=myHost,dc=com already exist. 
entry ou=Idmap,dc=myHost,dc=com already exist. 
adding new entry: uid=root,ou=Users,dc=myHost,dc=com
adding new entry: uid=nobody,ou=Users,dc=myHost,dc=com
adding new entry: cn=Domain Admins,ou=Groups,dc=myHost,dc=com
adding new entry: cn=Domain Users,ou=Groups,dc=myHost,dc=com
adding new entry: cn=Domain Guests,ou=Groups,dc=myHost,dc=com
adding new entry: cn=Domain Computers,ou=Groups,dc=myHost,dc=com
adding new entry: cn=Administrators,ou=Groups,dc=myHost,dc=com
adding new entry: cn=Account Operators,ou=Groups,dc=myHost,dc=com
adding new entry: cn=Print Operators,ou=Groups,dc=myHost,dc=com
adding new entry: cn=Backup Operators,ou=Groups,dc=myHost,dc=com
adding new entry: cn=Replicators,ou=Groups,dc=myHost,dc=com
adding new entry: sambaDomainName=LDAP,dc=myHost,dc=com

failed to add entry: objectClass: value #4 invalid per syntax at /usr/sbin/smbldap-populate line 498, <GEN1> line 58.
failed to add entry: objectClass: value #4 invalid per syntax at /usr/sbin/smbldap-populate line 498, <GEN1> line 89.
failed to add entry: objectClass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 498, <GEN1> line 101.
failed to add entry: objectClass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 498, <GEN1> line 112.
failed to add entry: objectClass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 498, <GEN1> line 123.
failed to add entry: objectClass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 498, <GEN1> line 134.
failed to add entry: objectClass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 498, <GEN1> line 179.
failed to add entry: objectClass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 498, <GEN1> line 201.
failed to add entry: objectClass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 498, <GEN1> line 212.
failed to add entry: objectClass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 498, <GEN1> line 223.
failed to add entry: objectClass: value #2 invalid per syntax at /usr/sbin/smbldap-populate line 498, <GEN1> line 234.
failed to add entry: invalid DN at /usr/sbin/smbldap-populate line 498, <GEN1> line 242.
Populating LDAP directory for domain LDAP (S-1-5-21-2198990887-1994421642-1008310464)
(using builtin directory structure)


Please provide a password for the domain root: 
/usr/sbin/smbldap-passwd: user root doesn't exist

```

Moreover, when I got my local sid I got another error:

```
# net getlocalsid
[2011/12/29 14:12:18.337870,  0] lib/smbldap_util.c:310(smbldap_search_domain_info)
  smbldap_search_domain_info: Adding domain info for LDAP failed with NT_STATUS_UNSUCCESSFUL
SID for domain MYHOST is: S-1-5-21-2198990887-1994421642-1008310464
```

where LDAP is my workgroup name and MYHOST is the netbios name.
I've double checked the passwords and done several times the configuration steps from the beginning. Any idea?

```
# uname -a
Linux myHost 3.0.0-12-server #20-Ubuntu SMP Fri Oct 7 16:36:30 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by fluca1978 on 2011-12-29
Ok, now I've locked myself out of the system after a reboot! Neither my normal account or root is accepting the login via ssh.

Update: it seems the system requires a lot to log me in, but I'm able to log in via SSH. It could be a host name resolution or nsswitch problem.

---

### Post by fluca1978 on 2011-12-29
I've tried to remove the whole ldap database and populate it again, but this time the system is still getting wrong starting with root:

```
adding new entry: dc=myHost,dc=com
adding new entry: ou=Users,dc=myHost,dc=com
adding new entry: ou=Groups,dc=myHost,dc=com
adding new entry: ou=Computers,dc=myHost,dc=com
adding new entry: ou=Idmap,dc=myHost,dc=com
adding new entry: uid=root,ou=Users,dc=myHost,dc=com
failed to add entry: objectClass: value #4 invalid per syntax at /usr/sbin/smbldap-populate line 498, <GEN1> line 58.

```

---

### Post by fluca1978 on 2011-12-30
I'm still fighting against the problem, and I found that the LDAP seems to refuse populating with each entry:

```
adding new entry: uid=nobody,ou=Users,dc=myHost,dc=com
failed to add entry: objectClass: value #4 invalid per syntax at /usr/sbin/smbldap-populate line 498, <GEN1> line 89.

```

the same error is replicated for each entry that is going to be added. Any idea on what the problem could be?

---

### Post by fluca1978 on 2011-12-30
Hi all,
sorry for [cross posting]("http://ubuntuforums.org/showthread.php?t=1901773") but I believe this thread is better placed in this forum. I'm trying to configure an ubuntu 11.10 server to act as a ldap sever and samba server, so I followed the howto described [here]("http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10-p2") (that worked for me for other servers).
The problem is that the ldap refuses to add any entry:

```

# smbldap-populate -u 30000 -g 30000 
Populating LDAP directory for domain LDAP (S-1-5-21-2198990887-1994421642-1008310464)
(using builtin directory structure)

entry dc=myHost,dc=com already exist. 
entry ou=Users,dc=myHost,dc=com already exist. 
entry ou=Groups,dc=myHost,dc=com already exist. 
entry ou=Computers,dc=myHost,dc=com already exist. 
entry ou=Idmap,dc=myHost,dc=com already exist. 
adding new entry: uid=root,ou=Users,dc=myHost,dc=com
failed to add entry: objectClass: value #4 invalid per syntax at /usr/sbin/smbldap-populate line 498, <GEN1> line 58.
adding new entry: uid=nobody,ou=Users,dc=myHost,dc=com
failed to add entry: objectClass: value #4 invalid per syntax at /usr/sbin/smbldap-populate line 498, <GEN1> line 89.
...
Please provide a password for the domain root: 
/usr/sbin/smbldap-passwd: user root doesn't exist


```

Moreover I've got the following error:

```
# net getlocalsid
[2011/12/29 14:12:18.337870,  0] lib/smbldap_util.c:310(smbldap_search_domain_info)
  smbldap_search_domain_info: Adding domain info for LDAP failed with NT_STATUS_UNSUCCESSFUL
SID for domain MYHOST is: S-1-5-21-2198990887-1994421642-1008310464
```

where LDAP is the workgroup of the samba server.
I've checked the ldap password and account credentials, I'm able to do a ldapsearch so the software is running, but seems there is some permission problem somewhere. Any idea?

---

### Post by oldos2er on 2011-12-30
Threads merged. Please don't start more than one thread per issue.

---

