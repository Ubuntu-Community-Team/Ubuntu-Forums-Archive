---
title: "Samba not connecting  with new client"
date: 2016-05-25
forum: Server Platforms
---

### Post by gardenair on 2016-05-25
hi,
      I am using samba on my server. There are 15 users which are already connected with the samba server to share their files. The problem is, in a fresh windows installation ( windows 7 ) i can not access my samba server share folder.In windows 7 the firewall is off,it can ping the server as well. Well on the client windows 7 it takes 3 to 5 minutes after writing the private  IP address on my samba server,I write the user name and its password then it show me "No rights".
I did the same practice with two different computers which which fresh windows install but i face same problem.

On the other hand my running client computer can access with the same user name and password and I can access the samba share folders.

please guide me how can I fix the problem.

thanks,
gardenair

---

### Post by volkswagner on 2016-05-30
You can log into the samba server with \\10.1.83.10 user=system-admin from other clients?
Are the other clients also showing the "pc-name" as the domain?
Does the new client belong to same workgroup/domain?

From the server please post output of:
```
testparm -s
```

---

