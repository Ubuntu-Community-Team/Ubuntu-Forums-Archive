---
title: "Samba file permission problem"
date: 2014-07-29
forum: Server Platforms
---

### Post by rsteinmetz70112 on 2014-07-29
I have a server running samba providing samba share to windowes clients.

I have discovered some existing files with the wrong permissions in Windows but the correct permission in Ubuntu. I can't change the permissions in WIndows. 

As a Domain Administrator I get "access denied" errors whenever I try to change the permissions.

Anybody got any ideas how I can correct the permissions.

---

### Post by TheFu on 2014-07-30
Hopefully someone who knows samba more than I will reply, 
but my understanding is that permissions from a client perspective are 100% controlled by the samba server settings and have NOTHING to do with Linux permissions.  Basically, the permissions for any samba share are fixed by the settings for that share.

If you provide exact permissions (linux/samba) that you have and that you want, we may be able to provide the desired settings.

---

### Post by rsteinmetz70112 on 2014-08-04
Normally Samba permissions for files can be change by a System Administrator using Windows Tools. I have some files that can't be changed.

---

### Post by TheFu on 2014-08-04
> **rsteinmetz70112 said:**
> Normally Samba permissions for files can be change by a System Administrator using Windows Tools. I have some files that can't be changed.

This has NOT been my experience with samba shares - so I looked at the **smb.conf** man page to learn.

**acl map full control** or **acl group control** settings?

Have you tried them?

---

### Post by rsteinmetz70112 on 2014-08-17
I have not. Currently away from that site so I will try it whne I return.

---

