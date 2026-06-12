---
title: "JAUNTY: Can't use smbldap-populate"
date: 2009-09-08
forum: Server Platforms
---

### Post by Wackie187 on 2009-09-08
I've just set up my LDAP server using the guide on the wiki (although no TLS due to a bug),
so the next step was configurating my Samba with LDAP support, using the [guide](https://help.ubuntu.com/9.04/serverguide/C/samba-ldap.html) on the
wiki as well.

However if i get to the part where I should populate the database with users, i get permission
problems and I don't know where to look.

```

robert@hydra:~$ sudo smbldap-populate 
Populating LDAP directory for domain AMK27 (S-1-5-21-1715502-3981193130-538665503)
(using builtin directory structure)

entry dc=amk27,dc=voesten,dc=nl already exist. 
entry ou=People,dc=amk27,dc=voesten,dc=nl already exist. 
entry ou=Groups,dc=amk27,dc=voesten,dc=nl already exist. 
adding new entry: ou=Computers,dc=amk27,dc=voesten,dc=nl
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 22.
adding new entry: ou=Idmap,dc=amk27,dc=voesten,dc=nl
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 27.
entry uid=root,ou=People,dc=amk27,dc=voesten,dc=nl already exist. 
adding new entry: uid=nobody,ou=People,dc=amk27,dc=voesten,dc=nl
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 89.
adding new entry: cn=Domain Admins,ou=Groups,dc=amk27,dc=voesten,dc=nl
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 101.
adding new entry: cn=Domain Users,ou=Groups,dc=amk27,dc=voesten,dc=nl
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 112.
adding new entry: cn=Domain Guests,ou=Groups,dc=amk27,dc=voesten,dc=nl
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 123.
adding new entry: cn=Domain Computers,ou=Groups,dc=amk27,dc=voesten,dc=nl
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 134.
adding new entry: cn=Administrators,ou=Groups,dc=amk27,dc=voesten,dc=nl
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 179.
adding new entry: cn=Account Operators,ou=Groups,dc=amk27,dc=voesten,dc=nl
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 201.
adding new entry: cn=Print Operators,ou=Groups,dc=amk27,dc=voesten,dc=nl
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 212.
adding new entry: cn=Backup Operators,ou=Groups,dc=amk27,dc=voesten,dc=nl
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 223.
adding new entry: cn=Replicators,ou=Groups,dc=amk27,dc=voesten,dc=nl
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 234.
adding new entry: sambaDomainName=AMK27,dc=amk27,dc=voesten,dc=nl
failed to add entry: modifications require authentication at /usr/sbin/smbldap-populate line 499, <GEN1> line 242.

Please provide a password for the domain root: 
Changing UNIX password for root
New password: 
Retype new password: 
Failed to modify UNIX password: modifications require authentication at /usr/sbin/smbldap-passwd line 285, <STDIN> line 2.

```

any idea what am I doing wrong?

---

### Post by windependence on 2009-09-08
Is sudo prompting you for a password? This is an authentication issue. You must run the command as root and from what you posted it doesn't look like it is prompting you for a password.

-Tim

---

### Post by Wackie187 on 2009-09-08
well, it isn't asking me for a password, since i've been working for the past hours with sudo, so it remembers the entered password. So technically i did enter it as root. Just to be sure, i logged in as root and I still get the same errors.

He asks me to enter a new UNIX password, which I enter and it then validates and comes back with the same errors

---

### Post by windependence on 2009-09-08
Strange. It's pretty clear it's not authenticating you by the "modifications require authentication" in your error. Let me dig a bit more

-Tim

---

### Post by windependence on 2009-09-08
Make sure you have correct authorization data in /etc/smbldap-tools/smbldap_bind.conf

```
slaveDN="cn=admin,dc=example,dc=local"
slavePw="12345"
masterDN="cn=admin,dc=example,dc=local"
masterPw="12345"
```

You also have to give the same password to the LDAP tree:

```
smbpasswd -w 12345

```


-Tim

---

### Post by Wackie187 on 2009-09-08
the smbpasswd gave an error saying that dn=admin didn't exist, which was correct, so I modified the smb.conf to add the ldap settings and rebooted the daemon. I hadn't add them earlier because it shows later up in the tutorial.
So those are synchronised, but I still get the same error.

Btw, now i get this error/notification if I change to root:

```

robert@hydra:/etc/samba$ su -
Password: 
Failed to initialize account for user root: NT_STATUS_ACCESS_DENIED

```

It then continues to root anyway though

---

### Post by mushroomblue on 2009-09-10
> **Wackie187 said:**
> the smbpasswd gave an error saying that dn=admin didn't exist, which was correct, so I modified the smb.conf to add the ldap settings and rebooted the daemon. I hadn't add them earlier because it shows later up in the tutorial.
So those are synchronised, but I still get the same error.

Btw, now i get this error/notification if I change to root:

```

robert@hydra:/etc/samba$ su -
Password: 
Failed to initialize account for user root: NT_STATUS_ACCESS_DENIED

```

It then continues to root anyway though

I'm having this same issue with every system user on my server.

---

