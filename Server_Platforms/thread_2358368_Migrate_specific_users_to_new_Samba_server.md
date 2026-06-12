---
title: "Migrate specific users to new Samba server"
date: 2017-04-12
forum: Server Platforms
---

### Post by matthewmcwest on 2017-04-12
I have an older Ubuntu 12.04 server running samba version 3.6.3 and I would like to move some of the users to a new server (many of the original users are no longer with us).  I have setup a new Ubuntu 16.04 server running samba version 4.3.11-Ubuntu.  I have already made an account for all users on the new server and copied their password hashes to the new server so that they can keep the same password.
I would like to do the same with their samba passwords, but not all users will be migrated to the new system.  Also, I notice that the structure of the /var/lib/samba folder is different on the new server, so I don't think I can just copy the contents over as it has been suggested other postings.  How do I migrate a single user over to the new server so that they can keep their password?

As a side note, I set the new server up with a different host netbios name so that there would be no confusion.  When I am ready, the idea is to shutdown the old server and rename the host netbios name of the new one so that all clients will automatically connect to the new server without anyone needing to change anything on their machines.

---

### Post by SeijiSensei on 2017-04-12
If you know the users' unencrypted Samba passwords, you could just use "sudo smbpasswd -a username" and recreate the Samba password list.  If not, try copying /var/lib/samba/private/passdb.tdb from the old server and see if that's enough.

---

### Post by matthewmcwest on 2017-04-17
Would there be differences in the format of the passdb.tdb between the old and new server?  I guess I could just rename the current passdb.tdb and give it a try.

---

