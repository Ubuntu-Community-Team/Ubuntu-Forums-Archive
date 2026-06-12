---
title: "Access-Your-Private-Data.desktop"
date: 2011-07-05
forum: Security
---

### Post by pcarlos853 on 2011-07-05
Hello,  I have two ubuntu 10.10 servers running. Both have home dir encryption. The servers both restarted (Power failure (?)) now when I log in the alias are gone until run /usr/bin/ecryptfs-mount-private I type in the password and everything is good. But when I close my ssh connection they are locked again. I need them to be unlocked because I back up to my home dir via rsync and ssh. How would I keep them unlocked until the next power cycle?   Thanks, Carlos

---

### Post by pcarlos853 on 2011-07-05
I have found out that when I log in and log out via the physical computer I get the desired result (having home decrypted), but I don't have physical access to the second server so how would I keep my home dir decrypted via ssh. (even after I disconnect, until a power cycle)  Thanks, Carlos

---

### Post by CharlesA on 2011-07-05
Have you tried running screen then decrypting the home directory?

Detach the screen session before disconnecting ssh.

---

### Post by pcarlos853 on 2011-07-05
CharlesA,   I stepped out of my office for lunch and when I came back the home dir stayed decrypted. I now have the servers they way I want them but I just don't know why now the second server is staying decrypted. I am happy that everything is working now, but it bugs me that I don't know if this is normal behaviour or a bug, Trojan, config error, etc. I will keep in mind the screen command as I am sure it will be useful later on.  Thanks, Carlos

---

### Post by CharlesA on 2011-07-07
Glad it started working as expected for you. So strange.

---

