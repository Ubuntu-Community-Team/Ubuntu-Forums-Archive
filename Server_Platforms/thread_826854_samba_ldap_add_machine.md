---
title: "samba ldap add machine"
date: 2008-06-12
forum: Server Platforms
---

### Post by cdenley on 2008-06-12
I've finally gotten samba working with an LDAP server. However, I can't seem to get joining the domain to work unless a machine account is created in /etc/passwd. Here is what I tried...

-Removed the "add machine script" option from smb.conf. XP client gives error "The user name could not be found". The machine account wasn't created.

-Set "add machine script" to run "/bin/true". Same results.

-Set "add machine script" to run a typical "adduser" command. As expected, a machine account is created in /etc/passwd, but the machine account is only now successfully added to the LDAP server.

Does the machine account have to exist in /etc/passwd before it can be added to the LDAP server? Is there anyway I can avoid cluttering the server's /etc/passwd file with machine accounts? I would rather not have to delete local user's from a cron job.

---

### Post by cdenley on 2008-06-12
If I delete the local unix machine account, I can still use that client. If I remove the LDAP machine account, I can no longer use the client. It is clear to me that a local unix machine account shouldn't be necessary but apparently is.

For the time being, this will be my workaround.

from smb.conf
```

add machine script = /usr/sbin/useradd -s /bin/false -d /dev/null -o -u 9999 -g 65534 %u

```

cron script
```

#!/bin/sh
MUSER=`getent passwd 9999|cut -d : -f 1`
while [ "$MUSER" != "" ]
do
        echo deleting $MUSER ...
        deluser "$MUSER"
        MUSER=`getent passwd 9999|cut -d : -f 1`
done

```

---

### Post by cdenley on 2008-06-13
> 
Machine accounts have to exist either in /etc/passwd or as posixAccount objects in LDAP, samba requires a numerical uid for machines. It might be possible that your nscd does not recognize ldap changes fast enough during the join process.

Volker

Does anyone know why a uid is required? Will my "workaround" cause any problems. It seems to work fine without a uid for my machine account so far. Is there a safe way for me to add posixAccount objects to the LDAP server from a command that I can use for the "add machine account" option?

---

### Post by promodus on 2008-06-16
> **cdenley said:**
> Does anyone know why a uid is required? Will my "workaround" cause any problems. It seems to work fine without a uid for my machine account so far. Is there a safe way for me to add posixAccount objects to the LDAP server from a command that I can use for the "add machine account" option?

Computer objects are required to have a UID as computer objects can be applied to a user group.

Also, if you use GPO's (which I don't know how in SAMBA) you can apply a GPO to a container and assign a user, group, or a computer.

Computer GPO's, such *** deploying software you'll see "Installing Managed software" before you even get a login prompt.

So if you had your installation programs on a DFS share and you only want computers who have a license to have access to these files... then you need a UID to assign to NTFS permissions.

There are other reasons, I'm sure.

---

### Post by iskatyel on 2008-06-17
I am not sure how you have configured samba and ldap, but in my experience you would want to use a command such as:
```
add machine script = /usr/sbin/smbldap-useradd -w "%u"
```
in order to add the machine to ldap without creating a local entry.  Perhaps you have some reason for avoiding the smbldap tools?

---

