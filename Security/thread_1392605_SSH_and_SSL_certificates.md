---
title: "SSH and SSL certificates"
date: 2010-01-28
forum: Security
---

### Post by e24ohm on 2010-01-28
Folks:
I am new to SSH and configuring the daemon and i cannot find an answer to my question.

I have isntalled openssh-server, and going through the configuration of chaning the port.

Q1: After configuration modifications, do i need to chmod the config file?

Q2: I only want one machien to ever access the SSH server. Can i create SSL keys that only the other key will work? I am not sure what it is called. This way, if the password is comprimised, users still can not access the SSH server, without the proper SSL key.


thank you.
E

---

### Post by cdenley on 2010-01-28
1. The default permissions for sshd_config should be fine.

2. You can use public key authentication, then disable password authentication. Only someone who has your key and the password to decrypt it can authenticate.
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by adam814 on 2010-01-28
Q1:  No, don't change the permissions on it.  You might need to restart the SSH server (sudo invoke-rc.d sshd restart).

Q2:  Yes, public key authentication is recommended.  You can limit who can connect adding entries to /etc/hosts.deny and /etc/hosts.allow.

For those files you could add "sshd: ALL" to hosts.deny and "sshd: ip-of-client" to hosts.allow.

How you'll set up public key authentication depends on your remote machine's ssh client.  If it uses OpenSSH you'd run (on the client machine) "ssh-keygen -t dsa -i ~/.ssh/id_dsa" then "ssh-copy-id -i ~/.ssh/id_dsa.pub ip-of-server".  Then once you've done this and are able to login using "ssh -i ip-of-server" uncomment and change the "PasswordAuthentication yes" line to "PasswordAuthentication no" in /etc/ssh/sshd_config.  You might need to restart the SSH server for it to take effect.

---

### Post by e24ohm on 2010-01-28
> **cdenley said:**
> 1. The default permissions for sshd_config should be fine.

2. You can use public key authentication, then disable password authentication. Only someone who has your key and the password to decrypt it can authenticate.
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

The link you provided looks like it gives the complete walk-throgh. Is there anything else I need or you recommend?

thank you.
E

---

### Post by e24ohm on 2010-01-28
> **adam814 said:**
> Q1:  No, don't change the permissions on it.  You might need to restart the SSH server (sudo invoke-rc.d sshd restart).

Q2:  Yes, public key authentication is recommended.  You can limit who can connect adding entries to /etc/hosts.deny and /etc/hosts.allow.

For those files you could add "sshd: ALL" to hosts.deny and "sshd: ip-of-client" to hosts.allow.

How you'll set up public key authentication depends on your remote machine's ssh client.  If it uses OpenSSH you'd run (on the client machine) "ssh-keygen -t dsa -i ~/.ssh/id_dsa" then "ssh-copy-id -i ~/.ssh/id_dsa.pub ip-of-server".  Then once you've done this and are able to login using "ssh -i ip-of-server" uncomment and change the "PasswordAuthentication yes" line to "PasswordAuthentication no" in /etc/ssh/sshd_config.  You might need to restart the SSH server for it to take effect.

thank you for providing the syntex; however, this is a little byond me at this point, but I am reading to catch up so i understand what you are describing. Thank you so much for helping me out.

Cheers!!!

---

