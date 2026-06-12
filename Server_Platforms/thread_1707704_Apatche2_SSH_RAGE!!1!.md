---
title: "Apatche2 SSH RAGE!!1!"
date: 2011-03-15
forum: Server Platforms
---

### Post by hehe3301 on 2011-03-15
So i was running an ssh server fine, could access from phone comp and others then my friend tried to 'help' me by starting an apatche2 server off my computer. Now although my ubuntu says ssh is fine and i can ping the computer i cannot ssh into my server.

HELP!

---

### Post by wongo888 on 2011-03-16
From a remote computer, check if port 22 is open using nmap (use your own IP):

```
$ nmap -A -p 22 192.168.0.6

```

---

