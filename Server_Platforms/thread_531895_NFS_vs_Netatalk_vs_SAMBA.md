---
title: "NFS vs Netatalk vs SAMBA"
date: 2007-08-22
forum: Server Platforms
---

### Post by PedroCarvalho on 2007-08-22
I recently installed an Ubuntu 7.04 Server in my home Network, to use as a WebServer and Backup System.

All my computers are Macs and I decided to use Netatalk on the Server to be able to make backups from the Macs to the Server. The problem is that sometimes I am able to mount the server others don't. It seems that Netatalk is an old way to do it and that  maybe Samba or NFS work better. But using samba to make connections between UNIX boxes does not seems right. NFS seems the right tool for the job, but for what I found it has no easy setup, and a lot of people complains about the difficulty of it. SAMBA on the other hand is easy to setup!

So what do you recommend? What is the big difference between  NFS, Netatalk and SAMBA? There is something really better in one of this options or is just a question of using nfs://, afp:// or smb:// to make the connection?

Cheers

---

### Post by ssam on 2007-08-22
for backup you could just use ssh and rsync.

with mac clients you may have to worry about file resource forks. if you have any classic (as in pre mac os x) applications they may still be using them. i don't think any mac os x apps use them but i may be wrong.

---

