---
title: "Ubuntu 10.10 How to enable ssh root with public key ?"
date: 2010-10-22
forum: Security
---

### Post by khicygni on 2010-10-22
Hello,
I'm scripting virtual machines and I need to ssh root ubuntu 10.10 machines.

Ubuntu 10.04 permits ssh root with rsa public key with just change PermitRootLogin as yes in /etc/sshd/sshd_config 

Ubuntu 10.10 seems to have change security policies, PermitRootLogin is already set to yes by default, but does not permits ssh root login with rsa public key

How to enable ssh root with rsa public key on an ubuntu 10.10 machine ?

        Thanks in advance,

---

### Post by iponeverything on 2010-10-22
If you start the server sshd in debug mode you might see why it's not working. 

Off the top of my head, I say that that is promiscuous permissions on the key file.

---

### Post by nxmehta on 2010-11-12
Make sure the /root directory and the /root/.ssh directory are not world readable/writeable, and are owned by root.

---

