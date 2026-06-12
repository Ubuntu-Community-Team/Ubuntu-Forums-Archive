---
title: "Samba + Domain Authentication"
date: 2009-12-17
forum: Server Platforms
---

### Post by robgolding63 on 2009-12-17
Hi,

I have an issue that I can't find a lot of documentation about on the internet, and I wondered if anyone in the forums had experience with it.

Basically, I started using Samba and Winbind on my server a while ago, to authenticate users to a Server 2003 Active Directory domain. Then, more and more linux clients started to pop up in my environment - so I enabled NFS on the server also. The problem now is, that the linux clients authenticate to the domain using Likewise Open, which hashed the UIDs from the domain - so they are the same across all clients. Plain Winbind, however (as on the server) doesn't do this, so the UIDs are different when compared on the server and clients. Therefore, NFS will not allow my users access to their files.

The problem I have is that I can't get likewise to work with Samba, in order to authenticate clients. The guide for Likewise Open 5 only mentions Samba 3.0.X, whereas Ubuntu how has 3.3.X in the repositories. Does anyone know how to make this work?

Thanks a lot,

Rob

---

### Post by oneloveamaru on 2009-12-17
Is your Samba using local authentication or domain authentication? NFS and local Samba users will share common UID's but Domain users will not.

"Likewise" on the other hand uses winbind+samba, so it's using ADS and Kerberos, that's why regular old Samba and NFS permissions are incompatible, since the UIDs are way off.

You can either configure "Likewise" to hand out the Samba shares, by editing /etc/samba/lwiauthd.conf or .... create local groups, add the domain users to them and grant them access to the shares. Make sure to edit smb.conf correctly so the correct UMASK is used when domain users create files, or else they'll create a file and then not have full permissions on it.

NFS just won't work nicely with Samba because of permissions. I would kill NFS off and make everyone use Samba.

Good luck.

---

### Post by Vegan on 2009-12-18
SAMBA is much easier to deploy in a mixed shop with lots of different departments.

NFS is too rigid.

SAMBA can live beside Windows Server as well as mainframes. That makes it the service of choice in my shop.

---

### Post by robgolding63 on 2009-12-18
I've got it half working now, by symlinking lwopen.so and secrets.tdb - I didn't really know what I was doing but I've managed to get Samba authenticating clients using Likewise.

However, something is still very wrong - winbind seems to be taking over every so often, and my UIDs change from the hashed LW ones (like 726641024) to plain Winbind ones (like 100023).

This is difficult!

Thanks for the help so far, I think I may end up just ditching NFS - but it would be nice to have Samba use Likewise like the rest of my network...

Cheers,

Rob

---

