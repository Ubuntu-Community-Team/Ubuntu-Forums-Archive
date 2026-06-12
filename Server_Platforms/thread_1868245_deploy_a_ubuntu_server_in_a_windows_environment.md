---
title: "deploy a ubuntu server in a windows environment"
date: 2011-10-24
forum: Server Platforms
---

### Post by kokyun on 2011-10-24
I have around 10 windows xp machines, want to have a ubuntu server in that network to save some cost on server. 
is there any similar application for ubuntu server example active directory provided by windows server platform, so that i can manage those users to login into their machine?

i would want to have the server to act as a file server, then only allow a few shared folders to save among some colleagues only. 

can someone guide me?

---

### Post by newbie-user on 2011-10-24
Installing samba would help with that.  Samba can act as a domain controller for a Windows environment, with usernames and passwords.

[https://help.ubuntu.com/10.04/serverguide/C/samba-dc.html](https://help.ubuntu.com/10.04/serverguide/C/samba-dc.html)

---

