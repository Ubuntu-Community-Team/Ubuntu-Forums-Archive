---
title: "Netowrk-based storage server"
date: 2014-05-14
forum: Server Platforms
---

### Post by Jacob_Tennant on 2014-05-14
I am trying to build a storage server to facilitate the network-based HOME storage directory for my Active Directory users.

I was wondering if I create a NFS server can I connect it to my AD server then tell AD thru a group policy to create the users HOME storage directory on the NFS server without every user needing to be connected to the NFS server?

Also, would a NFS server be the best way to go with this or would iSCSI be better? I have tried to get samba to work with my Windows Server 2012R2 AD before but have not had much luck with it.

---

### Post by sandyd on 2014-05-14
Moved to Server Platforms

---

### Post by SeijiSensei on 2014-05-15
> **Jacob_Tennant said:**
> I was wondering if I create a NFS server can I connect it to my AD server then tell AD thru a group policy to create the users HOME storage directory on the NFS server without every user needing to be connected to the NFS server?

That depends on the security model Windows uses.  On *nix systems, re-exportation of mounted shares is usually forbidden for security reasons.  A client should not be able to grant other users access to a share that they don't have rights to at the server level.  Windows could take a more permissive view, but that's well outside my knowledge of Windows.

---

### Post by Jacob_Tennant on 2014-05-15
SO them a SAMBA file server would be more appropriate?

---

### Post by nerdtron on 2014-05-16
Samba is the easiest way here since you don't have to install anything on the client machines and all configuration will be done on the server machine. If you are having problems on samba, you can post your problems here and we'll see what the community can do to help you.

---

