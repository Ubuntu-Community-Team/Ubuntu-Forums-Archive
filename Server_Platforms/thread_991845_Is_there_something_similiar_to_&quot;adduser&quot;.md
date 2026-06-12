---
title: "Is there something similiar to &quot;adduser&quot; for LDAP?"
date: 2008-11-24
forum: Server Platforms
---

### Post by amac777 on 2008-11-24
I have open-ldap up and running and clients can authenticate ok. But I'm having a hard time with managing the users and groups within the LDAP database.

The way I've been doing it so far (which works in a really messy way) is to use "adduser" to create new users on the server including adding the new users to the appropriate default groups such as fuse, audio, floppy etc. This populates the /etc/passwd and /etc/group files on the server but does not update LDAP. Then I wrote a little script that uses migrationtools/migrate_passwd.pl and migrationtools/migrate_group.pl to generate ldif files to add the user to the LDAP database, remove all the groups from the LDAP that have changed, and then re-add all the updated groups back to the LDAP.

Problem I'm having:
I need to maintain two sets of user/group data: one set is the official LDAP database, the other set is the passwd/group/shadow files on the server so I can keep using the migrationtools. This is annoying because the whole point of using LDAP in the first place was just to have all the info in one place. Also, if a user changes their password (which updates LDAP), it doesn't update the passwd/shadow file on the server and then they can't login to the server. If I do any group changes manually on the LDAP myself, that also doesn't update the files so the next time I add a new user, the groups sometimes get changed back to previous versions.
  
So is there an easier way? How can I easily manage the users and groups on the LDAP without relying on the migrationtools scripts, which require me to also try and maintain the passwd/group files manually?

Thanks for any advice.

---

