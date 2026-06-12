---
title: "NFS uid and gid mismatch on client"
date: 2009-02-13
forum: Server Platforms
---

### Post by easterndodo on 2009-02-13
Hello everyone,
I am setting up a small network of 10 Pc's (pc-01, pc-02 etc.) and a server. The server is supposed to provide LDAP authentication, NFS server, SFTP and SSH access and the like. The users' home directories are meant to be kept on the server and auto-mounted by the clients via NFS.

On server, I did bind /home to /export/home and then exported /export/home to the relevant clients (specifying IP's and options on /etc/exports). 
The clients mount the share correctly. The user whose UID is 1000, called "ilbutta", is the main user for now. I am still in the testing phase, in the end server and clients are meant to get user names and uids from the LDAP server. This local user is present, with the same UID and attributes, on both client and server and he of course owns his home directory. 
When I automount and access the home directory from the client though, if doing a ls -l I get a very weird listing where every file/directory appears to be owned by 4294967294 which is actually 2^32 -2. I figured out therefore that the client believes that all files owned by uid=1000 are actually owned by uid=-2 (since it is an unsigned long it overflows and get listed as 2^32 -2 ).
I did a Google search and figured out it is a fairly common problem due to idmapd issues. I can't figure out how to make it work though.

Does anybody have any help/suggestion?

I am using ubuntu 8.10 with latest updates.

Cheers
Tommaso.

---

