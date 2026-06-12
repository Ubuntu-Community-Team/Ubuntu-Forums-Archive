---
title: "Browseable shares - selected users"
date: 2007-06-21
forum: Server Platforms
---

### Post by willough on 2007-06-21
I want to make a directory share and files within browseable to only certain users on our network.  To all others I would like the directory to be invisible.  Authorized users can have full read, write privileges.  All clients are Windows. We run latest Samba and Feisty.  Presently, in smb.conf for the share, if browseable = yes shows the existence of the directory to all, browseable = no makes it invisible to all, though it can be mapped.  Any suggestions for making it invisible to just some users?  I don't know if directory mode would play into this or not. Thanks.

---

### Post by renzokuken on 2007-06-21
could you post your smb.conf.

on our server at work we just edit the smb file for each folder we are sharing and add a line saying

public = no ( to make it invisible)

valid users = rob brian pete dave    (for full read write access)

there is also

admin users = rob pete sean ben    ..........         but i'm not sure what the difference is between this and valid

---

