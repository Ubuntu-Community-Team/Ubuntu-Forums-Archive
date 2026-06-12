---
title: "sftp keeps asking for a password"
date: 2009-05-16
forum: Server Platforms
---

### Post by R.Bucky on 2009-05-16
I recently re-installed Ubuntu Server (I host my own site). I erased my /home/user/.ssh/known_hosts from the remote machine that I use to access the Server. Everytime I use Dolphin to access files on the server, it asks for a password whenever I look at a file and make changes to it. 

I hate that sftp password dialog box. It is driving me insane. Help!!! Make the dialog box go away!

---

### Post by hictio on 2009-05-16
Mmhhh... The key, if you were accessing the server via public key over ssh, it is actually stored on the file '/home/user/.ssh/authorized_keys'.

BTW, on the client, after generated, the key is stored on the file '/home/user/.ssh/id_rsa.pub', if you are using rsa to generate it.

---

### Post by R.Bucky on 2009-05-16
ahhhh - thank you!

---

