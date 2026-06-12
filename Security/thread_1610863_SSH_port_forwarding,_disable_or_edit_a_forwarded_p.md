---
title: "SSH port forwarding, disable or edit a forwarded port"
date: 2010-11-01
forum: Security
---

### Post by yoma1977 on 2010-11-01
Hi all.
I managed to set up port forwarding through ssh like this
 
sudo ssh -L 750:192.168.123.103:873 username[EMAIL="username@192.168.123.103"]@192.168.123.103[/EMAIL]
 
It does exactly what it's supposed to do, but how do i edit / remove this rule?
Is there some config file where i can alter the forwarding? How does it get stored?
Im using Ubuntu 10.10 Server Edition (allthough i recon it would be pretty much the same across all versions)
 
Sorry for my noobishness...

---

### Post by HermanAB on 2010-11-01
$ sudo killall ssh

---

### Post by yoma1977 on 2010-11-01
Does that mean that the port forwarding set in this way is not permanent?
(a machine reboot would also remove it?)

---

### Post by HermanAB on 2010-11-01
Correct.  SSH is a general purpose secure communications program.  It only works while it is explicitly running.  SSH is not part of the network stack or OS Kernel.

---

### Post by yoma1977 on 2010-11-01
Well the weird thing is i rebooted my system for testing this but the port forwarding still exists.
 (do forgive me for being an absolute noob, i just want to learn better how this actually works)
I would have thought that rebooting would give the same effect as 
$ sudo killall ssh

---

### Post by Boondoklife on 2010-11-01
rebooting would, the ssh tunnel is only active while the ssh session is running.

---

