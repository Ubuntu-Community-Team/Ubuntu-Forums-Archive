---
title: "Allow ssh access on different port"
date: 2008-10-20
forum: Server Platforms
---

### Post by Iain71 on 2008-10-20
I have an Ubuntu server version 8.04 which acts as an IMAP mail server, runs ssh and shares files using Samba over a network.  I am now trying to access these files remotely over the internet from both Mac and Windows laptops.  I understand from reading all the useful help provided that the best way to do his is by creating an ssh tunnel which I can do.  However, I understand that leaving port 22 open on my router to direct to my server will leave me open to attack and that the best way to avoid this is to change the port to another number.  I should really appreciate a clear description of how to do this as thus far I seem not to have succeeded.

---

### Post by mamcgrath on 2008-10-20
I believe you just have to edit the file '/etc/ssh/sshd_config' on your server. Near the top of the file you should have something like this

> # Package generated configuration file
# See the sshd(8 ) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

Change 22 to whatever you want.

---

### Post by heebus on 2008-10-20
> **mamcgrath said:**
> I believe you just have to edit the file '/etc/ssh/sshd_config' on your server. Near the top of the file you should have something like this



Change 22 to whatever you want.

He's right.  The only thing you need to remember, after you change the daemon you need to restart the service.

```
sudo /etc/init.d/ssh restart
```

---

### Post by Joeb454 on 2008-10-20
I actually had to restart my server before that would work for some really weird reason :p

---

### Post by TreeFinger on 2008-10-20
Do you have a firewall in front of this server?

---

