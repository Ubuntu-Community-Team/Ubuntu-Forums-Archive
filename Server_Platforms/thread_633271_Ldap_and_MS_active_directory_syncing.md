---
title: "Ldap and MS active directory syncing"
date: 2007-12-06
forum: Server Platforms
---

### Post by apix on 2007-12-06
Hey there  ! 


The task i want to do is something like this:
I have a MS active directory server and id like to setup another one ( possibly wiht openldap) into my ubuntu mashine. The main idea is that those two servers needs to be running at the same time and if i change something (add/remove/etc) into the first server, the other one will get updated and vice versa. Any ideas/forum posts/sites/links on how can i do that ? 


Thanks in advance :)

Edit: Im not sure this is the right thread to post, if so tell me and ill remove it.

---

### Post by koenn on 2007-12-06
Good luck with that one. 
Microsoft AD is  more or less LDAP compliant, but, as they always do, they've extended and modified the standard so that only other microsoft products are 100% compatible with it. Likewise for the Kerberos component that handles authentication in AD. Compatibility between AD and OpenLDAP therefore could be troublesome.

2nd, I have no idea how AD replication works even between Microsoft AD Domain controllers, so I can't tell you how ( or if) it would work between MS AD and OpenLDAP. 

My suggestion would be to first find out about replication (both on MS Technet and Knowledge Base websites and OpenLDAP documentation) and figure out if they can replicate with each other. 
If you manage to take that hurdle, you can go on and fin,d out how bad an effect  the differences between AD and OpenLDAP have on your plans.

---

