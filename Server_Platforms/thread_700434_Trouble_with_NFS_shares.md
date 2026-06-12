---
title: "Trouble with NFS shares"
date: 2008-02-18
forum: Server Platforms
---

### Post by eldaria on 2008-02-18
Hello, 

I have a bit of an issue.

I have created a Xen setup with 4 DomU.
When I created the individual DomU I told it to replicate all user accounts from Dom0.
SO I thought it was straighforward to set up one of the domu to be a file server and the folder rights would replicate to the clients(Other domU).

But I can't create or modify anything on the clients.
I get permission errors, even when using sudo su.

for example, I have 2 DomU.
lnxfile is the file server
lnxsql is the sql server

on lnxfile I have configured the exports and I'm able to mount them on lnxsql.

*From lnxfile /etc/exports*
```

/exports/lnxsql/var     192.168.1.104(rw,async)

```

*From lnxsql mount command*
```

lnxfile:/exports/lnxsql/var on /tmp/nfsvar type nfs (rw,addr=192.168.1.105)

```

*But when I try to create a folder on the mount lnxsql:*
```

root@lnxsql:/tmp/nfsvar# mkdir test
mkdir: cannot create directory `test': Permission denied

```

Note that I'm using root by typing 'sudo su'

Using 'sudo mkdir test' makes no difference.


Anyone have an idea to what is wrong?
Regards.
Brian/

---

### Post by faulkes on 2008-02-18
This is likely an effect of NFS doing a root_squash.

try 
```

192.168.1.104(rw,no_root_squash,async)

```

Faulkes

---

### Post by eldaria on 2008-02-18
ok, that worked.

Thanks a lot.

How does this work in regards to security?
Will the directories inherit the user accounts from the client even if they do not exist on the nfs server?

---

### Post by faulkes on 2008-02-18
> **eldaria said:**
> ok, that worked.

Thanks a lot.

How does this work in regards to security?
Will the directories inherit the user accounts from the client even if they do not exist on the nfs server?

It is best if the users on each machine have a matching UID

i.e. nfs client1 user A has UID 501
     nfs server user A has UID 501

If the uid's do not match, then the numerical UID will be substituted instead of the username, at which point the user would not be able to access the file, however if a different user has that UID, they would be able to access the file.

To mitigate this situation, most people choose to have a single signon solution so that such things always match.

Faulkes

---

### Post by eldaria on 2008-02-19
I was actually looking to set up something like a single sign on, but was not sure how to do it.

This way all users could have same log in ofr FTP, Mail, SQL etc.

Was thinking about using pam-mysql or something, but have never used it.
Also I was not sure how to limit what users can log on to, like some users would only have mail, and no FTP and certainly not shell/ssh access.

Any suggestion on literature to look at, preferably a nice guide?
Ok I know it is a bit of the original thread, I could start a new if needed. :)

---

### Post by faulkes on 2008-02-19
> **eldaria said:**
> I was actually looking to set up something like a single sign on, but was not sure how to do it.

This way all users could have same log in ofr FTP, Mail, SQL etc.

Was thinking about using pam-mysql or something, but have never used it.
Also I was not sure how to limit what users can log on to, like some users would only have mail, and no FTP and certainly not shell/ssh access.

Any suggestion on literature to look at, preferably a nice guide?
Ok I know it is a bit of the original thread, I could start a new if needed. :)

You could use LDAP:

[https://help.ubuntu.com/7.10/server/C/openldap-server.html](https://help.ubuntu.com/7.10/server/C/openldap-server.html)
[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

or NIS

[https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo)
[http://tldp.org/HOWTO/NIS-HOWTO/index.html](http://tldp.org/HOWTO/NIS-HOWTO/index.html)

Faulkes

---

