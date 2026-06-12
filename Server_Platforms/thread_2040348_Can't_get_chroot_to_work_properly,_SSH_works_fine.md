---
title: "Can't get chroot to work properly, SSH works fine"
date: 2012-08-10
forum: Server Platforms
---

### Post by adrian18w on 2012-08-10
Hello,

I'm trying to add a user with SFTP and chroot. I fallowed the usual procedure and it seems that the user can ssh and logs in correctly into the server with a rsa key. However, sftp doesn't work at all. The user can connect and gets authorized, but nothing more seems to happen. When i check the auth.log this is what I get:

```
sshd[4770]: Accepted publickey for val11 from xxx.xxx.xxx.xxx port xxxx ssh2
```

Nothing more, nothing less. The story is a bit different when I try to connect with a different user, one with root privelages. This is what I get:
```
sshd[4797]: Accepted publickey for adi from xxx.xxx.xxx.xxx port xxxxx ssh2
sshd[4799]: subsystem request for sftp
```

It seems that the openssh doesn't seem to request the sftp for that new user val11.

My /etc/ssh/sshd_config

```
#Subsystem internal-sftp /usr/lib/openssh/sftp-server
Subsystem  sftp  internal-sftp

allowUsers val11


Match User val11
      ChrootDirectory /home/public_html/
      ForceCommand internal-sftp
      X11Forwarding no
      AllowTcpForwarding no
```

Any helps is greatelly appreciated. Ohhh, I'm running 10.04 with openssh 5.3

Thanks

Adrian

---

### Post by dbrooke on 2012-08-10
permissions?

Did you restart ssh?

You left out a few details.. so it's a bit hard to tell why it's not working I guess.

Donovan

---

### Post by adrian18w on 2012-08-10
- /home/public_html/ owned by root:root

- /home/public_html/val11 owned by adi:val11

- /home/public_html/val11 - 775


Restarted both the ssh and whole server multiple times.

Thanks

---

### Post by adrian18w on 2012-08-17
Anyone?

---

