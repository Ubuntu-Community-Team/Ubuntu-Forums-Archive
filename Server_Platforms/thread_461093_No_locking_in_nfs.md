---
title: "No locking in nfs"
date: 2007-06-01
forum: Server Platforms
---

### Post by arnaldo on 2007-06-01
I just installed a Feisty nfs server.  Clients can mount, read and write, but cannot lock files.
On the server,  rpc.statd is running, and it has the right permissions to access 
/var/lib/nfs/sm*.

A typical entry in /etc/exports:

/export client(rw,no_root_squash,sync,no_subtree_check,no_auth_nlm) 

(I have added no_auth_nlm as an attempt to solve the problem)

On the client's /etc/fstab:

server:/export/home /home nfs defaults,soft,rw,tcp          0 0

The problem seems to be flock failure.

Any ideas?

---

### Post by puelocesar on 2007-06-05
I'm having the same problem with Feisty clients here. Our homes are located in a nfs partition on a Suse Server, and now that I updated my Ubuntu to feisty some things like kde are not working anymore, as they fail to "lock lock files".

My /etc/fstab entry:
10.90.67.4:/home         /home   nfs   rw,hard,rsize=8192,wsize=8192,timeo=14,intr  0 0

If you solve your problem please report back. Thanks.

---

### Post by puelocesar on 2007-06-05
Ha!

I installed the following packages on my clients: nfs-common and liblockfile1, now everything works fine.

The strange thing was that everything was working except from the lock files.. Even without nfs-common, that are NFS support files common to client and server...

---

