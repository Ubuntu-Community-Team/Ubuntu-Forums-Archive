---
title: "SSH - private and public keys for Putty and RDP"
date: 2010-02-22
forum: Security
---

### Post by e24ohm on 2010-02-22
Am looking at creating private and public keys to use SSH, Putty and remote desktop into my Linux box; however, I want to use key-based method. I will be forwarding the port in putty.

After generating my private key  on my linux box – where do I place the key on my Linux box? I am coming from the windows world, where the key needs to be installed in a special place.

Thank you,
J

---

### Post by cariboo on 2010-02-22
Your authorized keys are located in ~/.ssh in your home directory. You may find [this]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") document helpful.

---

### Post by e24ohm on 2010-02-22
Thanks mate!!! Cheers.

---

