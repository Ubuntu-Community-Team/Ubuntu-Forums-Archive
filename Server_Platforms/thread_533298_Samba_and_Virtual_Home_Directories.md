---
title: "Samba and Virtual Home Directories"
date: 2007-08-23
forum: Server Platforms
---

### Post by codemaster on 2007-08-23
I recently have setup Samba, pulling accounts from LDAP. This, from what I can tell, works.

Now, what I am attempting to do with this Samba-LDAP setup is to allow my LDAP users (which they log into any of our linux servers) to have the same home directory. To do this, I will have a folder (/vhome/) where a directory will be created the first time the user logs in (such as /vhome/tuser/).

Now, the problem arises, is that I am unsure how to configure Samba (the smb.conf) to share the virtual home directories properly; also, Samba needs to create the user's virtual home directory if it does not already exist when they log onto any of our servers.

Thanks for any help! :)

---

