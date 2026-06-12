---
title: "Upgrades not identified"
date: 2018-04-15
forum: Security
---

### Post by cam17 on 2018-04-15
When I SSH into my Ubuntu desktop I got the following showing updates pending.

Last login: Wed Apr 11 03:10:01 EDT 2018 from 10.10.10.100 on pts/2
Welcome to Ubuntu 16.04.4 LTS (GNU/Linux 4.13.0-38-generic x86_64)

 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)

9 packages can be updated.
0 updates are security updates.

But when I performed the command "*apt list –upgradable*  " to list the pending updates the result was none as seen below. apt list –upgradable
Listing... Done.

I was expecting a list of information on pending updates. Can anyone tell me why this did not occur?

---

### Post by TheFu on 2018-04-15
I get this:
```
$ apt list --upgradable
E: Opening configuration file /etc/apt/apt.conf.d/02proxy - ifstream::ifstream (13: Permission denied)
```

---

### Post by cam17 on 2018-04-17
I dont understand your response. You provided a response to a previous post by my self. your post thefu is Doing an apt update, followed by **sudo apt list --upgradable**,  perhaps hourly would let you build an hourly bucket - just run the  update periodically to see what changes from period to period. There are  powerful text comparison and processing tools built into every Unix.

Now your saying it doesn't work?

---

### Post by TheFu on 2018-04-18
Sorry if it wasn't clear.
**apt list --upgradable **doesn't work but 
**sudo apt list --upgradable** works as I expected.

---

### Post by cam17 on 2018-04-19
OK. thanks double dash.

---

### Post by thenailedone on 2018-04-21
> **cam17 said:**
> OK. thanks double dash.

Uhm... sudo... #-o

---

