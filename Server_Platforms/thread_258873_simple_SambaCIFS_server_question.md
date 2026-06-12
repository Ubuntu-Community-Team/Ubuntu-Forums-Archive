---
title: "simple Samba/CIFS server question"
date: 2006-09-16
forum: Server Platforms
---

### Post by spiderworm on 2006-09-16
Hi all,

I have an Ubuntu samba server and a couple of clients connecting to it.  One of the clients is an Ubuntu desktop.  With this machine, I am trying to set up some automounts (from fstab):

//SPIDEY/backup /mnt/spidey/backup cifs credentials=/home/spiderworm/.smbpasswd 0 0

Here's the problem: on the server and the client, the uid for user spiderworm is different.  The files that belong to user spiderworm on the server, when mounted on the client, belong to another user on the client, named heidi.  The reason, as far as I can tell, is that heidi is the user on the client machine whose uid matches the spiderworm account uid on the server.

Of course, even though spiderworm on the server and the client have different uids, I would like to be able to mount the files on the client so that spiderworm has the same access to those files as he would if he were working directly on the server.  Any way to do this?

spiderworm

---

### Post by spiderworm on 2006-09-23
I'm bumping this because I still need an answer on this, please.  Anyone?

spiderworm

---

### Post by imagine on 2006-09-24
You can set the user ID and group ID:

//SPIDEY/backup /mnt/spidey/backup cifs credentials=/home/spiderworm/.smbpasswd**,uid=UID,gid=GID** 0 0

---

### Post by spiderworm on 2006-10-12
Setting the uid and the gid isn't working.  When browsing around, I found this lengthy-yet-informative email:

[http://lists.samba.org/archive/smb-clients/2005-May/000572.html](http://lists.samba.org/archive/smb-clients/2005-May/000572.html)

Basically I am told that I should disable CIFS Unix Extensions in order to get uid and gid to work.  Unfortunately, I can't find any information on how to do that on Ubuntu.  Does anyone know?

Thanks,
spiderworm

---

### Post by spiderworm on 2006-10-12
NM, I found it.  Problem was I was searching for CIFS unix extensions, but in smb.conf, it's just:

unix extensions = no

If anyone is having troubles like mine, just add that line to the [global] section of your /etc/samba/smb.conf file, then restart your samba server with /etc/init.d/samba restart

spiderworm

---

