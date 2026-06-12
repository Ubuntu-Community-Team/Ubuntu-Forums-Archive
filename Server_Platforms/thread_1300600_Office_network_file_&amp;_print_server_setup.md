---
title: "Office network file &amp; print server setup"
date: 2009-10-25
forum: Server Platforms
---

### Post by majdi on 2009-10-25
Hi

We have a project where we have a mixed network environment of Windows XP, Windows Vista and Ubuntu desktops. We want to setup a Centos server to be used as a file and print server.

From my readings, I can see that I will have to setup a Samba server for the windows users to connect and share files on the Centos server, but I'm not sure about how to setup these features for the Ubuntu users.

Do Ubuntu users need to use Samba to share folders on the Centos server? What is the usual method for Ubuntu users to share folders on a Linux based server.

The idea is to have the shared folder to appear as a local disk on the Ubuntu users desktops and auto mount them on restart?

Your feedback is appreciated. If you know of any links that can guide us in this setup up, please post them here.

---

### Post by volkswagner on 2009-10-25
You can use Samba for both linux and windows clients.  

If you don't mind setting up separate shares, NFS will have a performance edge on the linux clients.  Samba can be a little bugger at times with different versions, and finding up to date documentation for you OS/version.

Here is an excellent [how to for setting up nfs shares]("http://ubuntuforums.org/showthread.php?t=249889"), you will need to check with Centos for proper NFS server configs.

---

### Post by majdi on 2009-10-26
Thanks volkswagner,

So NFS share is a better option when configuring shared folders on a linux server for linux clients? 

Would I have any problems running both NFS and Samba on the same server? Or is there a way to configure windows clients to share using NFS.

---

