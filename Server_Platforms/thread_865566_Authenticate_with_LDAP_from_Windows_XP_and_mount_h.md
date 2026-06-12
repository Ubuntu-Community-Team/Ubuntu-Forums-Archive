---
title: "Authenticate with LDAP from Windows XP and mount home dir"
date: 2008-07-20
forum: Server Platforms
---

### Post by jw29 on 2008-07-20
Hello,

I'm upgrading the workstations in one of our labs from Windows 2000 to Windows XP.

We had previously used pgina to do it with the ldap auth plugin.  I tried setting it up with the same settings as before, but it didn't work...it appears pgina may not be fully compatible with Win XP SP3.

What we need to do is authenticate the username and password with our server, and then mount their home directory from our NFS server to the H: drive.

Any suggestions?

Thanks,
jw

---

### Post by promodus on 2008-07-20
A couple quick suggestions:

You could have SAMBA bind to LDAP, and have your XP Clients authenticate to SAMBA. Rather than accessing NFS shares you could access SAMBA shares.

For the deployments you could do a Linux version of RIS:
[http://www.promodus.net/linuxris](http://www.promodus.net/linuxris)

and yes it is possible to do the entire lab all at once, join a domain and push out software without touching any of the computers... :) But that's for a much much more involved thread.

---

