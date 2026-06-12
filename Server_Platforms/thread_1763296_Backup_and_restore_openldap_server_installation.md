---
title: "Backup and restore openldap server installation"
date: 2011-05-20
forum: Server Platforms
---

### Post by andriu1 on 2011-05-20
Hello, here we're again, asking, asking.

    Well, I'm trying to make a backup of an openldap 2.x installed on ubuntu 10.0.4 to restore it on another server, but it seems that there is something that i'm doing wrong or something that i'm not doing, so, here are the steps that i've followed.

   Backup ldap server with slapcat command

```
$sudo /usr/sbin/slapcat -v -l ./backup-ldap.ldif
```

    Copy this file to the new server, and restore

```
$sudo slapadd -c -l backup-ldap.ldif
```

    But, this error appears, "Available database(s) do not allow slapadd"

What's wrong??, I've been looking some minutes and I think that the commands that I've used are the commands that I must use

Regards,
Andres

---

### Post by kenji_08 on 2013-02-25
hi there try to use this script. Ive got this on this link 
[http://supportex.net/2011/02/backup-restore-ldap-database/](http://supportex.net/2011/02/backup-restore-ldap-database/) and itt work for me.
Just make sure to change LDAP suffix from “dc=yourDC,dc=local” to your actual one.

#!/bin/sh
LDAPBK=ldap-$( date +%y%m%d-%H%M ).ldif

BACKUPDIR=/home/backups

/usr/sbin/slapcat -v -b "dc=yourDC,dc=local" -l $BACKUPDIR/$LDAPBK

gzip -9 $BACKUPDIR/$LDAPBK
To **restore** you should perform the following steps.
 1.  stop **slapd** daemon:
debian:~# /etc/init.d/slapd stop
2. delete old database (**make sure you are in right directory to use rm**):
debian:~# cd /var/lib/ldap
rm -rf *
if this error appears  "cd comman not found" it means that you are not permitted to access the folder ldap because it usually owned by user "openldap"
better execute this command first "sudo chown guest:guest /var/lib/ldap -R" then you can proceed to rm -rf * command

 3. Restore database from LDIF file:
debian:~# /usr/sbin/slapadd -l backup.ldif
4. make ldap folder own by user "openldap" again.. by executing this command "sudo chown openldap:openldap /var/lib/ldap -R" 

 5. run **slapd** daemon:

---

### Post by overdrank on 2013-02-25
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

