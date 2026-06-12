---
title: "Server Synchronization - Does a solution exist"
date: 2010-05-31
forum: Server Platforms
---

### Post by rnielsen on 2010-05-31
I am looking for a server synchronization solution that will meet the below requirements:
[LIST]
[*]Synchronize files between 3 or more servers on remote networks connected via the internet
[*]When file is opened (via samba) on each network, the corresponding file on the other servers is locked (i.e. message to users that this file is currently in use and may be opened as read only)
[*]Once the file is closed, it is automatically synchronized between the other servers.
[/LIST]

This setup needs to be secure as sensitive data may be transferred.  The 3 servers will primarily be file servers for 3 separate locations where people travel between these locations.  At each network, the user would connect to the network locally and open a shared file on the local server work on it, close it.  While it is open, no one else could modify it either locally or on any of the other remote servers until it is closed.

There is also a possibility that an additional remote server would be in the mix, purely as a backup server and it would most likely be a MS server.

The options that I have looked into are unison and rsync but they both seem to have some limitations.

Does anyone know if there is a solution to this?

Thanks

---

### Post by richardjh on 2010-06-01
I have not yet set this up myself, but I understand GlusterFS will meet your requirements.
The[ FAQ is here]("http://www.gluster.com/community/documentation/index.php/GlusterFS_Technical_FAQ") which answers your questions on synchronisation, file locking security etc.

There is a [howto here]("http://www.howtoforge.com/high-availability-storage-cluster-with-glusterfs-on-ubuntu") for Ubuntu.

---

