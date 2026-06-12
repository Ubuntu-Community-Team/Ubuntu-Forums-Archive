---
title: "nfs4/krb5: root_squash and mounting exported shares that aren't chmod 777"
date: 2014-11-12
forum: Server Platforms
---

### Post by daniel201 on 2014-11-12
Hi,

Apologies if this has been asked before, but the searches I've done don't seem elicit the correct answer to my scenario.

I have a kerberized nfs server and if I chmod 777 the export folders on the server, I'm able to mount them on the nfs client. I can then kinit as my non-root user and read/write to the share.Is it possible to tweak this so that the nfs exports don't have to be chmoded to 777?

I think if I have two users, Dave & Ann, they should be able to log-in on a desktop and their profile mounts the shares they should have access to, according to the groups they are members of. Thus using a fixed UID/GID for anonymous users in combination with root_squash doesn't seem ideal. Neither does throwing everything into fstab as automount.Is the answer that the user can run mount command? Then I can put the mount.nfs into their user profile, along with a user specific keytab?

Just to clarify, I'm not using LDAP. I might in future move towards using that, but for now I'd just like to find the best way of doing this.The general answers seem to center around using NFS exported home directories and just giving 'the world' access to NFS shares and I'd like to avoid doing this, if possible.
Thanks
D

---

