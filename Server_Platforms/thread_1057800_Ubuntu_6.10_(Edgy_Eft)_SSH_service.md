---
title: "Ubuntu 6.10 (Edgy Eft) SSH service"
date: 2009-02-02
forum: Server Platforms
---

### Post by maildemon on 2009-02-02
Hi, I have Ubuntu 6.10 (Edgy EFT) webserver and worked flawlessly, until i noticed that someone is trying regulary to access SSH service, in an attempt to guess passwords, etc.. Then the hosts.deny and hosts.allow alowed only 2 IPs. I understand that it is not a best way to protect. Then some times Nmap shows i have there about 1000 connections on port 22.  And one day ssh service stopped. I cannot start it, and dont know why. etc/init.d/ssh start or restart shows nothing, no mesages about what happened. What i can do, to start sshd? Tnx

---

### Post by spinanicky on 2009-02-02
Most likely you got hacked. Access your server normally, ie plug in a keyboard and screen, boot it up, un-install and reinstall. Monitor your active network connections to the server with iftop and if the perutrator is still gaining access you will be able to see their ip in iftop. From which you can then block their connection with the firewall.

---

### Post by maildemon on 2009-02-03
OK, thx.
I tried to
apt-get remove ssh
apt-get install ssh openssh-server

and there is notification:

unable to make backup link of `./usr/bin/sshd' before installing new version ...

I cannot rename or remove this file? Why it is so?

---

