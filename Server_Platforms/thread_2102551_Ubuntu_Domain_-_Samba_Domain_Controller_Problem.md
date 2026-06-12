---
title: "Ubuntu Domain - Samba Domain Controller Problem"
date: 2013-01-07
forum: Server Platforms
---

### Post by CaseyC on 2013-01-07
I am currently following the following guide: 

[https://help.ubuntu.com/10.04/serverguide/samba-dc.html]("https://help.ubuntu.com/10.04/serverguide/samba-dc.html")

But when I get to this part: 

> net rpc rights grant "EXAMPLE\Domain Admins" SeMachineAccountPrivilege SePrintOperatorPrivilege \
SeAddUsersPrivilege SeDiskOperatorPrivilege SeRemoteShutdownPrivilege

I get the error in the attachment. The user "casey" is in the adm group. I tried using users and groups to process this step but still stuck. I tried using the IP of the machine and the HostName. 

Any since of direction or advice would be greatly appreciated.

---

### Post by CaseyC on 2013-01-07
Update: 


The ignoring unknown script error is gone, however I still have the Could not connect to server 127.0.0.1 (new line) Connection Failed: NT_STATUS_ACCESS_DENIED


Help :)

---

