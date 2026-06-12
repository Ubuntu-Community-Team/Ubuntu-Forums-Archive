---
title: "Samba question"
date: 2016-11-27
forum: Server Platforms
---

### Post by thomasc93 on 2016-11-27
Hi everyone,

So I have an issue with samba and I'm a bit perplexed.

I set up a samba server and things are generally good. However the weird quirk exists where shares added via the smb.conf file are not accessible, but if I set up a Local Network Share from the context menu when a file is right clicked using the Ubuntu GUI I'm using with Ubuntu Server, it works perfectly and the share is accessible.

Any ideas of why this might be?

---

### Post by darkod on 2016-11-28
Usually linux permissions on folders/files. Beside the samba share definition you also have to think about what type of access you want to give people to the shares and configure specific permissions on the linux path where the shared folder is. And I mean the whole path, starting from the /.

For example if the want to share /shares/datashare you have to set correct permissions on both /shares and /shares/datashare.

What do you want, a share open to all, or locked down to specific user(s)?

---

### Post by Morbius1 on 2016-11-29
The "Local Network Share" option in nautilus invokes nautilus-share and does two things:

** It creates a Samba Usershare ( the definition of which is in /var/lib/samba/usershares ).

** And depending on what options you select it asks you if you want it to modify permissions. When you say yes it sets the permissions on the folder being shared to 777.

All of this is done automatically by nautilus-share.

Creating an accessible share in smb.conf is also a two step process but those steps have to be done independently as darkod outlined. Samba determines what the user may do. Linux permissions determines what the user can do.

---

