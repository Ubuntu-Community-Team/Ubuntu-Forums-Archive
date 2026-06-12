---
title: "Samba and subfolder security"
date: 2011-03-21
forum: Server Platforms
---

### Post by yield_ on 2011-03-21
Hi There,

Here is my problem and what I try to do when it does occur.

I have a Samba server with, let say, 1 share....
The filesystem that this share is sharing files from is ext4.

From there, all my valid users are able to read or write whthin that share everywhere and I'm happy about it....

However, in some of the subfolders, I do not want some specific user to access....
I did change the filesystem ownership and access and it does now allow user's who should for theses subfolders....

So, my question is : Does samba really care about filesystem securitu on subfolders or only on the parent shared one ?

And, is there anything I can add in my smb.conf to fix that and also be able to use ACL ? (Yes, my file system is mounted using ACL....)

---

### Post by jmacgowan on 2011-03-21
Yes, samba does care about individual file permissions.  For instance, my network at work is set up in such a way that employeeA has read/write access to /home/public/ but read only access to /home/public/myReadOnlyFile.ext

---

### Post by yield_ on 2011-03-21
Do you have any special instructions in smb.conf to hae samba
check file permissions or does it do it by default ?

---

### Post by Morbius1 on 2011-03-21
Depends on what you mean by "cares". Samba itself is not aware of the underlying Linux file permissions.

Samba through different authentication parameters determines what a given remote user **[COLOR=Blue]may[/COLOR]** do. Linux file permissions determines what that user **[COLOR=Blue]can[/COLOR]** do.

Let's say you set up a share that allows guests to write but set the folder to have ownerhip:group = root:root and permissions of 755. Samba will not prevent the remote guest from getting access but Linux will prevent the remote user from writing.

---

