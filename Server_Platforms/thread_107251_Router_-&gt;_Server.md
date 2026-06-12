---
title: "Router -&gt; Server"
date: 2005-12-22
forum: Server Platforms
---

### Post by rensu on 2005-12-22
I want to give acces telnet/ssh to server from Router Web Conf. But it dont want to give. I gave 23 port access but still it says Connection refused if im trying to connect into server. Can someone tell me whats wrong? And with port 22: tried to start /usr/sbin/sshd but it says that there is no such file. But i can connection from server with ssh. Do i need to install anything else for ssh?

---

### Post by dodger on 2005-12-22
probable telnet daemon is not started. that is a good thing. you should really use ssh.

sudo apt-get install openssh-server

should do the trick.

take care.

---

### Post by rensu on 2005-12-22
Thanks:)

---

