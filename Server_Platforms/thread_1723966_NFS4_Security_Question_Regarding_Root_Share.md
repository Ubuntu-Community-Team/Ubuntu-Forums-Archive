---
title: "NFS4 Security Question Regarding Root Share"
date: 2011-04-07
forum: Server Platforms
---

### Post by TaBaScO77 on 2011-04-07
I'm setting up an NFS server to share to two different projects, and both should not be able to see each others data or shares.  Project 1's server names are ab-project1 & ab-project2.  The other projects servers start with the name zy-project....  It is a requirement that I use NFS4 for this.

I've setup the /etc/export as follows:

/share *(ro,fsid=0,sync)
/share/ab    ab-project*(rw,nohide,sync)
/share/zy   zy-project*(rw,nohide,sync)


My problem is I'm not sure exactly what to put for the /share.  I know its necessary for NFS4.  If I leave it as * then either project could theoretically mount up that directory, and see down into the others shares.  What would be the best practice to ensure that no one can mount to /share, but still leave it available for setting up NFS4?

The only way the projects are mounting it is by using these commands:
mount -t nfs4 nfs-proj-serv32:/ab /ab
mount -t nfs4 nfs-proj-serv32:/zy /zy

I've searched all over the forums, and Google, but don't seem to be finding the answer.  This is probably a simple question, but this is the first time I've had to use NFS4.

---

