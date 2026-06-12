---
title: "file system acls not correct when mounted via nfs"
date: 2011-12-09
forum: Server Platforms
---

### Post by clubbing80s on 2011-12-09
Hi.

New to nfs :
 
I have a new server 10.10 LTS. I'm using Likewise open for AD authentication and integration, it is joined to the domain and I can login with my AD credentials. 

I have copied the data from the current production server and copied the working nfs exports file. 

I have re-applied the filesystem acls on the new server. 

I'm using the same configuration syntax to mount the new server's nfs export as that on the on the current production clients.

server :
/etc/export
/nfs/apps 192.168.0.0/16(rw,sync,no_root_squash)

client:
/etc/fstab 
nfs-server:/nfs/apps /nfs/apps  nfs     defaults 0 0

The problem I'm having is that what I see in the client side in not what I see on the server side.

server side
   124 drwxrwx---+  3 root root      94208 2009-04-27 16:10 ubuntu_9.04_32bit
      4 drwxrws---+  2 root root        105 2011-03-23 15:55 Windows_isos

client side 
124 drwxrwx---  3 4294967294 4294967294      94208 2009-04-27 16:10 ubuntu_9.04_32bit
      4 drwxrws---  2 4294967294 4294967294        105 2011-03-23 15:55 Windows_isos


the user mappings are missing and the facl's are missing.

I have also noted that new files created do have the correct default facls ..

What have I missed ?

I'm looking for a good likewise howto for nfs and samba .

Thanks

---

### Post by Lachele on 2012-01-05
I think it's a bug.  I get similar behavior no matter what I do.

If I do a standard nfs mount to or from 11.04 or 11.10 with a RHEL 5.6 box, the uid and gid are transmitted properly.  But, if I mount between 11.04 and/or 11.10, this is not the case -- they all map to "4294967294".  I've tried several variants in /etc/exports and on the client side, and that's what it does.  I've looked back at the docs and re-read how-to's, and I don't think the procedure has changed.  But, as always, I might have missed something.

I'm not using nfs4, but there is a similar bug being discussed elsewhere regarding nfs4 (link below).  The behavior isn't exactly the same, but the fact that it shows up in both versions might help pin down the culprit.

nfs4 bug:  [http://www.spinics.net/lists/linux-nfs/msg26046.html](http://www.spinics.net/lists/linux-nfs/msg26046.html)

---

