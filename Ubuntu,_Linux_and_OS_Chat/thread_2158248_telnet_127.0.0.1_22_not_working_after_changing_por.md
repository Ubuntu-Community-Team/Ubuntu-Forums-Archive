---
title: "telnet 127.0.0.1 22 not working after changing port from 56786 to port 22 on linux"
date: 2013-06-28
forum: Ubuntu, Linux and OS Chat
---

### Post by omkar jadhav on 2013-06-28
we have change the port from network end of linuxserver from 56786 to port 22.now i am not able to telnet from port 22.i am getting below error :
telnet 127.0.0.1 22
Trying 127.0.0.1...
telnet: connect to address 127.0.0.1: Connection refused
telnet: Unable to connect to remote host: Connection refused

---

### Post by DeathByDenim on 2013-06-28
Ports below 1024 are privileged and only servers running as root can use those. Does the server run as a normal user maybe?
You can check using
```
ps aux
```
That will list all the processes, including the user information. If your server isn't running as root, then that is the problem.

---

### Post by Lars Noodén on 2013-06-28
> **omkar jadhav said:**
> we have change the port from network end of linuxserver from 56786 to port 22.now i am not able to telnet from port 22.i am getting below error :
telnet 127.0.0.1 22
Trying 127.0.0.1...
telnet: connect to address 127.0.0.1: Connection refused
telnet: Unable to connect to remote host: Connection refused

Can you go into more detail about what you changed and how it was before you changed it?

Port 22 is for ssh and if you telnet to it, if sshd is running, then you should see some output like this:

```

$ telnet 127.0.0.1 22
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
SSH-2.0-OpenSSH_6.2p2 Debian-4

```

---

