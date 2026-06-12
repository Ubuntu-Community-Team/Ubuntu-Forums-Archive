---
title: "TCP_NODELAY - Problem with Reverse SSH Tunnel"
date: 2011-09-05
forum: Server Platforms
---

### Post by evolvd on 2011-09-05
Trying to get a reverse SSH tunnel going from Mac OSX 10.6.6 to Ubuntu Server 11.04 .

On the Mac I use the following command:
ssh -R 19999:localhost:22 user@remoteIP

on the server I use:
ssh localhost -p 19999

On the server I get the following message in the terminal:
identification: Connection closed by remote host

On OSX I get the following message:
setsockopt TCP_NODELAY: Invalid argument

I can't tell if this is an issue with OSX or with Ubuntu. Any ideas or thoughts would be great.

---

### Post by BkkBonanza on 2011-09-05
Just to be clear what that command means,

Listen on port 19999 on localhost on the remoteIP machine and forward connections back to your Mac on localhost port 22. 

Before you connect to localhost port 19999 on your server you need to have something listening on your Mac on localhost port 22. Presumably you want sshd to be doing that but you need to make sure that is the case. So on your Mac you can run "sudo netstat -lntp" to check that sshd (or whatever you want) is actually listening on localhost port 22.

Then you can similarly check on your server that ssh is indeed listening on port 19999 using the same command. By default it listens only on localhost and not on "*" (any interface). So you can only connect to it from within the server itself, not from an external location. In order to connect remotely to server:19999 you would need to override the config of ssh on the server with the GatewayPorts option.

---

### Post by evolvd on 2011-09-05
Thanks for the detailed response. This whole time I was thinking there was an issue with SSH its self but I was just over looking the fact I didn't have ssh listening on the mac.

Edit:
How do I change the tag to "Solved"?

---

### Post by BkkBonanza on 2011-09-05
It should be an option on the "Thread Tools" link at top of page.

---

