---
title: "probloem using ssh"
date: 2007-12-12
forum: Server Platforms
---

### Post by naveenmudunuru on 2007-12-12
Dear All, 
when i'm connecting to my server, i get this message


Add correct host key in /root/.ssh/known_hosts to get rid of this message.
Offending key in /root/.ssh/known_hosts:2
Host key verification failed.

i had no issues before re-installing my server. please help on how to make my system enable new RSA key....

---

### Post by bmathis on 2007-12-12
try deleting the key on your computer and then reconnect to store the servers key again.

```
rm /root/.ssh/known_hosts
```

---

### Post by naveenmudunuru on 2007-12-12
thanks this worked actually but it is there a way where i can force my ssh to accept the new RSA key

---

### Post by gaten on 2007-12-13
Yes, you can disable StrictHostKeyChecking in your ssh_config file.

---

