---
title: "smb.conf question"
date: 2007-07-22
forum: Server Platforms
---

### Post by knorr.orange on 2007-07-22
I would like to share a directory using Samba, but am not sure exactly what lines to add to my smb.conf file.  The result I am trying to get is to have a directory available to everyone but read only.  However, for a couple of users it should be read/write.  Can someone help me out with what I should put in my configuration?

I am using a fresh install of Ubuntu Server 7.04 (with samba installed of course.)

Thanks.

---

### Post by p_quarles on 2007-07-22
It's a little more complicated than setting up smb.conf (though you need to do that, as well). You also set permissions for the shared directories using chown and chmod.

This link will help:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by knorr.orange on 2007-07-23
Sorry, I forgot to mention that the users who will access with read/write have already had their samba passwords set and the physical directory to share has also had appropriate permissions set.

I have created the share and it works fine, but currently does not ask for a password and allows anyone to write to the directory.  My guess is I am missing a line from the configuration of the share or have something wrong.  At the moment I the computer is not here so I am unable to post the configuration I have now.  I was hoping someone could post the share config for it though assuming that the dir, users, and other config is already done.

---

### Post by mckryptyk on 2007-07-23
This will help 
[http://ubuntuforums.org/showthread.php?t=438577](http://ubuntuforums.org/showthread.php?t=438577)

Disclaimer: I wrote it based off something I saw on the forums before. 
It should work for you.

---

### Post by codmate on 2007-07-23
> **knorr.orange said:**
> Sorry, I forgot to mention that the users who will access with read/write have already had their samba passwords set and the physical directory to share has also had appropriate permissions set.

I have created the share and it works fine, but currently does not ask for a password and allows anyone to write to the directory.  My guess is I am missing a line from the configuration of the share or have something wrong.  At the moment I the computer is not here so I am unable to post the configuration I have now.  I was hoping someone could post the share config for it though assuming that the dir, users, and other config is already done.

You need to turn off global guest access, turn on 'user' security and turn on 'writable' for the share in smb.conf.
Have a look at my file here:
[http://ubuntuforums.org/showthread.php?t=424063&page=4](http://ubuntuforums.org/showthread.php?t=424063&page=4)

You may also need to use the smbpasswd command to add users to samba.

---

### Post by knorr.orange on 2007-07-24
Thanks for the responses.  It will be about a week or so until I will have access to that machine again, but I will try the suggestions and post my results here afterwards.

---

