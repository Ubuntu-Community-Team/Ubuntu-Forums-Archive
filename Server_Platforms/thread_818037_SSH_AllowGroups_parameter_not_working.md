---
title: "SSH AllowGroups parameter not working"
date: 2008-06-04
forum: Server Platforms
---

### Post by mike.broughton on 2008-06-04
Hi, 
I have created a group on my ubuntu server and added two users to the group. I have then edited the /etc/ssh/ssh_config file and added the AllowGroups groupName parameter. I have saved the file and then restarted the ssh server. However I can still ssh to the server as a user not in the specified group. Does anyone know what the problem is?
Do I need to add the parameter anywhere in particular to the file or is it fine to append it at the end?
Thanks very much

---

### Post by cdenley on 2008-06-04
/etc/ssh/ssh_config is the client configuration. You want the server configuration, /etc/ssh/sshd_config.

---

### Post by mike.broughton on 2008-06-05
oops :-) 

That solved it. 

thanks very much

---

