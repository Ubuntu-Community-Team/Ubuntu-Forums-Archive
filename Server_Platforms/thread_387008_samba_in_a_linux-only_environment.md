---
title: "samba in a linux-only environment"
date: 2007-03-17
forum: Server Platforms
---

### Post by garba on 2007-03-17
if you were to set up a linux only computing environment would you use samba to serve home dirs? i've been experimenting with kerberos+nfs4 for my diskless computer lab but i'd rather rely on a central repository such as ldap for user accounting and authorization, i know this is not the unix way through and true but nfs4 is a pain... the only thing i'll using nfs (v3) for is feeding the root fs to the clients... i'd love to hear your opinion about this solution, regards, andre

---

### Post by elst on 2007-03-18
I haven't used Linux for Kerberos myself, but AIUI Kerberos and NFS shouldn't stop you using LDAP - your LDAP directory can act as the store for Kerberos credentials.

Using Samba for sharing root directories to Linux diskless clients really sounds like overkill. IIRC, Edubuntu currently just uses NFS v. 3 for this, although I believe that it's being extended to be something like the arrangement you describe.

---

### Post by Soleil-Raid on 2007-03-20
I would probably replicate what I've got here, which is LDAP for uid/gecos/username Directory information, Kerberos for authentication, and NFS for home directories.

NFSv4 is a pain to set up, so if you need to make stuff go fast, I would install NFS3 first, then migrate over to NFS4 once you've got it working reliably.

The 'unix way' for doing Directory Information is to use NIS. Don't. NIS is trash.

Unfortunatly, documentation for setting up OpenLDAP is sorely lacking. Google around, there's quite a bit of good stuff out there.

---

