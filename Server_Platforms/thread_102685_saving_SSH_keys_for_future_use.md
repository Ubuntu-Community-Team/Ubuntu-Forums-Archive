---
title: "saving SSH keys for future use"
date: 2005-12-12
forum: Server Platforms
---

### Post by harisund on 2005-12-12
Hello

My question is simple. How do I save the current RSA/DSA keys so that the next time I reinstall Ubuntu, I can get the SSH Server to reuse the keys instead of having to generate a new set everytime? 

Thanks in advance !

---

### Post by Hube on 2005-12-12
I believe the known_hosts is in $HOME/.ssh

For the server they are in /etc/ssh.

---

### Post by harisund on 2005-12-12
Ha! Exactly what I needed.. thanks a real lot.. 

Thanks again !

Hari

---

