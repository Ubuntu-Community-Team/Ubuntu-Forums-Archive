---
title: "Ldap+nfs mkhomedir doubt"
date: 2011-09-30
forum: Server Platforms
---

### Post by jeanconte on 2011-09-30
Hello,
 
Im new to ubuntu forums, but got a doubt, my english is not that good, anyway, here i go:
 
Im have a LDAP server that authenticates Linux Clients and Samba authenticating windows clients . Im using pam_mkhomedir.so to make new directories if ppl doesnt have a dir yet, but, im not sure about how this pam stuff works. i configured the common-session file on CLIENT to use pam_mkhomedir.so to create a new home on a NFS mounted drive from the server, but, the stuff only works if i mount the NFS /home with the no_root_squash option, i guess that way the client will consider root privileges on client same way as on the server. my question is:
 
-if someone steal my root password, will they have access to all home folders, so all my home data could be excluded, isnt that method a bit "unsecure"?
 
i have seen ppl steal passwords from linux using programs, and some untrusted ppl has my password, so im trying to find a way of making homes without giving root access to the clients.
 
if someone has better ideas tell me please.
 
thanks in advance.

---

