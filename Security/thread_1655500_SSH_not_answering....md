---
title: "SSH not answering..."
date: 2010-12-29
forum: Security
---

### Post by short-timer on 2010-12-29
I'm setting up an Ubuntu 10.04 system; installed open-ssh. I'll call this box A. I also have an older box B with Debian. From A I can log into B via the usual way (ssh <user>@<IP>). The 1st attempt at this I was presented with the 'unknown host' warnings & elected to accept it.

However, from B when I try logging into A there is no response at all -- no warnings, nothing. I have to ctrl-C back to the prompt. I can successfully ping A from B though. 

I CAN connect to A from a Windows box using PuTTY as an ssh client with all default settings. Once connected I can log in.

Why no response from A when trying to log in from B?

Thanks,
Ron

---

### Post by cariboo on 2010-12-29
Try:

```
ssh -vv user@server
```

It will print out what is happening, and should give you a clue as to what is wrong.

---

### Post by short-timer on 2010-12-30
I get the following. Googling the ssh_connect line hasn't yet given me a usable clue. Is it likely specifically a problem w/ssh, or general networking?

~$ ssh -v -v -v <user>@<IP>
OpenSSH_5.1p1 Debian-5, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 172.20.68.28 [172.20.68.28] port 22.
^C

---

### Post by kyleddm on 2010-12-30
This may not be the case but make sure that you have openssh-client and openssh-server both installed on both machines.  One is to allow access in (server) and the other is to connect to other machines (client)

---

### Post by hawkmage on 2010-12-30
Are you running ufw or iptables?  What do you get if you run either "sudo ufw status" or "sudo iptables --less"?

---

