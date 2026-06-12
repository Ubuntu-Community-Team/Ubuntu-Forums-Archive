---
title: "ssh with keyboard auth"
date: 2012-05-03
forum: Server Platforms
---

### Post by francwalter on 2012-05-03
Hello

I have two Ubuntu servers, one with keyboard authentification disabled (only keyfile auth), ubuntu 8.04 LTS, I name him "myserver" and another new one with keyboard auth enabled, Ubuntu 10.04 LTS "mysecondserver".

In myserver I have in the sshd_config:

> PasswordAuthentication no
ChallengeResponseAuthentication no

Now I want to connect from myserver to mysecondserver but I get errors:

> root@myserver:~# ssh root@1.2.3.4 -v
OpenSSH_4.7p1 Debian-8ubuntu3, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 1.2.3.4 [1.2.3.4] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/identity type -1
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host
root@myserver:~#
Do I need to enable Keyboard authentification on myserver if I only want to connect to the other server?
Isn't the setting of only file-auth (no keyboard auth) only for an incoming ssh-connection?

mysecondserver's ssh-Version:
> root@mysecondserver:/# ssh -V
OpenSSH_5.3p1 Debian-3ubuntu7, OpenSSL 0.9.8k 25 Mar 2009
frank

---

### Post by francwalter on 2012-05-05
Never mind for reading it, if anyone read it anyway.

I installed the new server again (Ubuntu 12.04) and now there are no problems anymore to login with ssh.
Still I have problems to rsync over ssh.

When I do this:

> # rsync -avz -e ssh me@1.2.3.4:/tmp/test /tmp/test/

I get this error:

> ssh_exchange_identification: Connection closed by remote host
rsync: connection unexpectedly closed (0 bytes received so far) [receiver]
rsync error: unexplained error (code 255) at io.c(632) [receiver=3.0.4]

---

### Post by francwalter on 2013-01-29
Endly I did this:

**rsync -avzP --stats -e 'ssh -p 2222' / me@1.2.3.4:/backup/oldserver**

which backups the whole old server (/) to the new server (ssh there on port 2222, IP there 1.2.3.4) to the directory /backup/oldserver

It took a while but worked :)

frank

---

### Post by SeijiSensei on 2013-01-29
Rsync defaults to SSH so you don't need the "-e" option.

francwalter, rsync works best if you use shared keys.  The target server's /root/.ssh/authorized_keys file should includes root's public key on the source server.

---

### Post by Lars Noodén on 2013-01-29
The -e option is only needed with rsync if special parameters, like a port change, are to be passed to ssh.

---

### Post by SeijiSensei on 2013-01-29
> **Lars Noodén said:**
> The -e option is only needed with rsync if special parameters, like a port change, are to be passed to ssh.

Ah, that makes sense, Lars.  Usually I've seen the option documented in cases where you might prefer to use rsh instead of ssh.

---

