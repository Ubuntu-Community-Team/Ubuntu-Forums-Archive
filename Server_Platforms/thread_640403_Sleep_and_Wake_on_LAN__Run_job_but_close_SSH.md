---
title: "Sleep and Wake on LAN / Run job but close SSH"
date: 2007-12-14
forum: Server Platforms
---

### Post by Mick12 on 2007-12-14
I am running ubuntu 7.10 Server and access it via SSH. I would like to know if it is possible to put the server to sleep and wake it again when i use ssh.

Also, is there a way to run a job on the server but close the ssh connection and log back in some time later.

Any help would be appreciated.

---

### Post by HermanAB on 2007-12-14
What use is a server that goes to sleep?

Backgrounding with "-n":
$ ssh -n [email]user@example.com[/email] program &

However, the gotcha is that, that will only work if you have public keys without a passphrase cofigured, since you wont be able to type your password.

Cheers,

H.

---

### Post by Mick12 on 2007-12-14
Many uses a server can have, such as rendering. So is there a way to achieve the wake on lan idea?

---

### Post by HermanAB on 2007-12-14
Can you use the laptop kernel and do speed stepping?  That would be a good alternative to shutting the whole machine down.  

BTW, wake-on-LAN is a BIOS feature.  All you need to do is enable it, if it exists, bt then you need to ensure that the machine will boot rapidly, else it will be interminable.

Cheers,

H.

---

### Post by Mick12 on 2007-12-14
So there is no command that puts ubuntu server (no gui) into a standby mode? I am not that familiar with linux so i am not sure if i might be asking the obvious?

---

### Post by HermanAB on 2007-12-14
Yes you can go into standby, which will save the current state to the swap partition.  Ubuntu  uses Suspend version 2, I think. Some Googling will turn up something.

---

