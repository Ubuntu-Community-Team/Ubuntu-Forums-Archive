---
title: "Reinstalling and keeping ssh keys"
date: 2013-11-22
forum: Security
---

### Post by captainKrash on 2013-11-22
I am curretly running 12.04 LTS with gnome 3, but I would like to upgrade to 13.10 with default desktop. I have a few server keys for remote logins. Is it possible to save these and add them back in when I reinstall? I would rather not need to hassle about changing stuff on the remote servers if possible.

Many thanks for any advice.

---

### Post by Lars Noodén on 2013-11-22
For your own ssh server, those keys would be in /etc/ssh  Just make a backup of the key files and then put them back after you reinstall the server. 

If you are talking about keys that you use to connect to other servers, they are wherever you saved them.  Usually most people keep them in ~/.ssh/  Again, it is just a matter of copying the files and restoring them after the new system is installed.  Better, if it is possible, keep a separate /home partition and choose not to erase it during the re-installation.

---

### Post by captainKrash on 2013-11-22
Thank you Lars. It's for remote servers. I'll save them and copy in. Think the partition bit might be beyond me. I store most files on an external drive so not a great deal of housekeeping to do before upgrade/reinstall.

---

### Post by Lars Noodén on 2013-11-22
Just be sure that when you copy them back to the new machine that the file permissions are set correctly.  For the private keys it should be 0600.  For the public keys it does not matter so much, since they are public anyway.  Depending on your system you may have to set the permission on the private keys manually after you restore them.  But that's not a big deal, just a detail.

---

