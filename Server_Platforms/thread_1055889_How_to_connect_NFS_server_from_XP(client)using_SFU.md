---
title: "How to connect NFS server from XP(client)using SFU"
date: 2009-01-31
forum: Server Platforms
---

### Post by tigga on 2009-01-31
I have a big problem,
i installed SFU3.5 on a XP and defined as nfs client 
the nfs server is Ubuntu8.04.

I have a connection and i can see the nfs server and his IP address also i can enter to it by double clicking and i can see the shared file wich i defined on /etc/exports (/srv/work) .

But when i try to enter to this directory an error message say that i don't have the right permission.

can anyone help me??:(:(

By the way i have established NFS share between this server(Ubuntu8.04) and a debian-etch and it worked fine.

---

### Post by HermanAB on 2009-01-31
Go to the NFS server and open up the permissions to 666, eg:
$ sudo chmod -R 666 /wherever/it/is

That should get you going, but you should get the users and groups under control.

Cheers,

Herman

---

