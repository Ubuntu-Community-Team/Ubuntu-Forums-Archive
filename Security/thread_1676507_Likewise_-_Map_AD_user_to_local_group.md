---
title: "Likewise - Map AD user to local group"
date: 2011-01-27
forum: Security
---

### Post by eshimony on 2011-01-27
Hello All,

I am using Likewise to join a Linux box to the AD domain.
My Linux box holds a filesystem i am sharing both for UNIX and windows machines.

I would like to keep my data with unix permissions using local/NIS groups, but i can't find any options to map a windows user to a unix one.

I tried adding the domain user to the local group in /etc/group and i indeed see the group when i run "groups" or "id username" and even "id DOMAIN\\username" i do get the group and i even able to write to a folder owned by this group (With permissions 755).

the problem is when i access from Windows machine - when i try writing on the same folder, i get "You need permissions to perform this action".

Please help !! i really stuck with this #-o .

thanks,
Eyal.

---

