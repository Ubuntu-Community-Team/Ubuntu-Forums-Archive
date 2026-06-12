---
title: "problem with authentication via SSH on MaaS Nodes"
date: 2014-06-14
forum: Virtualisation
---

### Post by riccardo-magrini on 2014-06-14
hi everyone, i need to resolve a problem with MaaS server, after have added the nodes, changed the their status to ready, added ssh key, started the ubuntu's installer, boot the nodes from their HD.....
when i try to make the login via ssh on the nodes they ask me the password.
 i've also try to modify the parteed file added a pwd in md5 but nothing. 
is there someone can help me, please?

---

### Post by kira_belka2 on 2014-06-16
hi!
Check /home/$user/.ssh folder on each node and right permissions for it.

---

### Post by riccardo-magrini on 2014-06-17
hi Kira_belka2,
my problem is the impossibility to access to node either via ssh or from their VM shell. I don't know why they ask me the pwd. their should make that automatically via ssh key generated on the region controller.

---

### Post by riccardo-magrini on 2014-06-20
I've resolved it, how can I close this post as resolved? thanks

---

