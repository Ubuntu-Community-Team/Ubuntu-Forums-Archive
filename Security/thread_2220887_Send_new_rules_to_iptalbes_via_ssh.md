---
title: "Send new rules to iptalbes via ssh"
date: 2014-04-29
forum: Security
---

### Post by johny4 on 2014-04-29
I am a beginner in Linux security and now I solve this problem:
Deployed server emulates a service on port 80 in front of him is a firewall (other ip)
that separates this server and LAN and the external network. the iptables firewall to open a port for input to server. 


I need to create a script that would be me on the basis of access to the port on the server, sent through the firewall via ssh command that adds a blocking rule in iptables.
Alternatively, use a tool that this could do..


** Can someone please help or advice? I would be very grateful**

---

### Post by ian-weisser on 2014-04-29
I'm confused.

Are you trying to control iptables using the web service?
Or are you trying to control iptables using ssh?
Or are you asking for the ssh command to modify the server's iptables?
Or are you asking how to use the web service to block/ublock a port (like the ssh port)?

It seems to me that you are asking how to send an iptables command to the server using ssh.
Since the iptables command requires 'sudo', the easiest way is to login. Since you seem to care a lot about security, best to use ssh keys instead of passwords, and to not permit root logins.
```
client:~$ ssh my_user@server_addr

server:~$ sudo iptables -L
[...lots of output...]

server:~$ exit

client:~$
```

Is that what you are looking for?

---

