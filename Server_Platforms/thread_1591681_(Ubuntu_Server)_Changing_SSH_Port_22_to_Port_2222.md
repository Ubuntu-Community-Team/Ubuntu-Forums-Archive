---
title: "(Ubuntu Server) Changing SSH Port 22 to Port 2222"
date: 2010-10-09
forum: Server Platforms
---

### Post by Zanthir on 2010-10-09
I'm trying to change the open port for SSH on my Ubuntu Server. I have two Ubuntu Servers on the same network, and am trying to be able to access both of them from outside the local network. The process is very simple on the [server guide page]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/openssh-server.html"). I just need to change Port 22 (actually commented out by default) to Port 2222 (and of course uncomment it). Then restart the SSH server.

All this is very simple and straight forward. But, after doing this, and not being able to connect, I found out by running ```
netstat -an | grep "LISTEN "
``` that I am actually not listening to port 2222, but still listening to port 22.

Anyone know what I can do to resolve this issue?

Thank you in advance.

---

### Post by scrooge_74 on 2010-10-09
modify /etc/ssh/sshd_config

where it says:


# What ports, IPs and protocols we listen for
Port 22      <---change port to what you need it to be

then save and restart ssh server

and adjust your router to forward request to correct port and internal IP

---

### Post by Zanthir on 2010-10-11
I was accidentally editing the /etc/ssh/ssh_config file instead of the /etc/ssh/sshd_config file. I think I just misread the guide I was following. Thanks.

---

