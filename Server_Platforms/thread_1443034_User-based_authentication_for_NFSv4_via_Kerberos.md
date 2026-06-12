---
title: "User-based authentication for NFSv4 via Kerberos"
date: 2010-03-30
forum: Server Platforms
---

### Post by tomiondrums on 2010-03-30
hi,
i've currently set up my nfs clients to authenticate via kerberos to the nfs server. therefore i use a keytab-file which contains the secret for the client machine pricipal (i.e. nfs/clientname.domain.name)
is there a chance to implement some kind of user-based authorization, that is i'd like to use pricipals like "nfs/username" or something like that.
the main idea behind that is that the production system will have to run in a workstation pool where workstations are not dedicated to a particular user (centralized login)
i need to have something like this:
 a users log's on (-> ticked obtained) and if successful his particular home-directory shall be mounted via nfs 

is something like that possible and if yes how to implement it?

this guy seems to have what i need but he doesn't state how it was achieved:
[http://linux-nfs.org/pipermail/nfsv4/2006-November/005609.html](http://linux-nfs.org/pipermail/nfsv4/2006-November/005609.html)

thanks in advance!

---

