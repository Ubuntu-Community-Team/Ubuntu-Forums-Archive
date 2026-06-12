---
title: "Passwordless SSH to Leopard from Ubuntu"
date: 2009-02-15
forum: Security
---

### Post by antm88 on 2009-02-15
I followed this guide exactly where my the local computer is running ubuntu 8.10, and I am trying to connect to a MB Pro running Leopard (the remote computer). However I am still being asked for the remote computer's password when I try to log in to ssh. Can anyone explain why this is, and if possible help me solve this problem? Thanks, Ant

The guide:
[http://www.mactips.org/archives/2007/12/20/using-passwordless-ssh-the-easy-guide-leopard-only/](http://www.mactips.org/archives/2007/12/20/using-passwordless-ssh-the-easy-guide-leopard-only/)

---

### Post by punx45 on 2009-02-16
that tutorial supposes that the Mac is the local machine, not the remote, and it is only "passwordless" since the password is stored in keychain.   its not really a true passwordless ssh.   that would use keys.

i think you want to do something more like this:

[http://www.debian-administration.org/articles/152](http://www.debian-administration.org/articles/152)

i believe you will also need to edit /etc/ssh_config on the mac to allow public key authentication.

---

