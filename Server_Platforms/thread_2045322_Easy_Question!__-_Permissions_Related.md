---
title: "Easy Question!  - Permissions Related"
date: 2012-08-21
forum: Server Platforms
---

### Post by nuclearj on 2012-08-21
Hello, I just installed 12.04 64bit Server and also installed NFSv4 and can mount the share/export.  However, I cannot write anything to it.

The folder properties say that I am not the owner so I cannot change the permissions.  Which I tried with one of those chmods... this just hit me, should I have started with a chown?

I'm a not a complete noob.  More like a hack and slash, shotgun, spaghetti on the wall kinda linux user... I hope that communicates.  Thanks!

---

### Post by LHammonds on 2012-08-21
Anytime I create files/folders, I make sure the permissions are correct.

1st - I set ownership if necessary using chown
2nd - I set permissions using chmod
3rd - I make sure the stuff is in the correct logical locations

Also, when mounting file systems or sharing folders, make sure the mount point is mounted like you think it should.  If you are expecting write/delete access, do not mount it as read-only because no matter what permissions/rights you have, you cannot modify a read-only access point unless you re-mount it as not read-only.

LHammonds

---

### Post by nuclearj on 2012-08-21
Ok I will try that out tonight.  Another question,  Do I set the folder ownership permissions from within the server via ssh?  Or do I set the permissions on the server from the client side?

---

### Post by sandyd on 2012-08-21
> **nuclearj said:**
> Hello, I just installed 12.04 64bit Server and also installed NFSv4 and can mount the share/export.  However, I cannot write anything to it.

The folder properties say that I am not the owner so I cannot change the permissions.  Which I tried with one of those chmods... this just hit me, should I have started with a chown?

I'm a not a complete noob.  More like a hack and slash, shotgun, spaghetti on the wall kinda linux user... I hope that communicates.  Thanks!
What are you NFSing to?

If you are not using the same domain and/or synced uids/gids on NFS4 (this is only on NFS4!) for both the client and the server, it doesn't work.

NFS4 works on uids/gids, not names ;)

---

### Post by LHammonds on 2012-08-21
> **nuclearj said:**
>  Do I set the folder ownership permissions from within the server via ssh?  Or do I set the permissions on the server from the client side?
I only manage my servers via SSH so I cannot give any advice beyond that.

LHammonds

---

### Post by nuclearj on 2012-08-21
> **sandyd said:**
> What are you NFSing to?

If you are not using the same domain and/or synced uids/gids on NFS4 (this is only on NFS4!) for both the client and the server, it doesn't work.

NFS4 works on uids/gids, not names ;)

The client and server are both on the same network.  That would mean they are on the same domain.  Is that correct?

---

### Post by nuclearj on 2012-08-21
> **LHammonds said:**
> I only manage my servers via SSH so I cannot give any advice beyond that.

LHammonds

I see what you are saying.  I will change the folders permissions on the server through ssh.  I'll report back later!

---

### Post by sandyd on 2012-08-22
> **nuclearj said:**
> The client and server are both on the same network.  That would mean they are on the same domain.  Is that correct?
Did you configure both the client and the server with idmapd? (/etc/idmapd.conf)

Check that, then make sure the user's uid/gids match on each system.

For example, if you have a user that you are accessing NFS with, called

"a" with a gid of "2001", and a uid of "2001", you will also need a user named "a" with a gid of "2001", and a uid of "2001" on the server.
Then, chown the files on the server to the user and its group.

---

### Post by nuclearj on 2012-09-10
Hey just wanted to say thanks for the help.  I did get the folder to communicate.

---

