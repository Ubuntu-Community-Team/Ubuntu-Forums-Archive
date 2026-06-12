---
title: "ubuntu server access from external network"
date: 2019-06-07
forum: Server Platforms
---

### Post by christopher-santos18 on 2019-06-07
hi i have creat a ubuntu server and i whant to get access from externel ip to the ssh and to sftp can you help me how can i do that please ?

thanks

---

### Post by TheFu on 2019-06-07
It depends and may not even be possible.
Do you own the WAN router?
Can you modify the WAN router settings?
Is the WAN IP one that can is internet routed or is it one of the internal LAN subnets?
Can the WAN router do port translation?  So  WAN:63022 ---> LAN:22
Does your "ubuntu server" have a static IP?
Does your WAN connection have a static IP?

Answer those 6 questions, please.

The overview of steps for a simple setup:
* install openssh-server and fail2ban on the machine (assuming static LAN IP)
* On the router, forward some non-standard port, say 63022/tcp to the LAN staticIP port 22/tcp
That's it.  

Fail2ban is pre-configured to block brute-force ssh attacks on port 22, but putting ssh on the internet on port 22 will just fill up your logs, so putting it on any crazy high-port will make that stuff almost completely go away.  Your choice, but 100K attempts per day or just 0 or 10, I know which I want.

Depending on the answers to the questions, there are other steps to make it easier to access and more secure.

---

