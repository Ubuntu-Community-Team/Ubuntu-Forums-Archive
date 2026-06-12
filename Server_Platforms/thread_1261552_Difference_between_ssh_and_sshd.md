---
title: "Difference between ssh and sshd?"
date: 2009-09-08
forum: Server Platforms
---

### Post by Cardale on 2009-09-08
I am looking at services and was wondering if there was a difference?

---

### Post by gombadi on 2009-09-08
ssh is the command you use to connect to remote machines - the client.

sshd is the daemon that is running and allows others to connect to the machine - the server.

---

### Post by Cardale on 2009-09-08
so a server has no use for the client.

---

### Post by Whiffle on 2009-09-08
Sometimes its useful to ssh into the server, and then ssh from there into another computer.

---

### Post by ainsworth_t on 2009-09-09
> so a server has no use for the client.

Only if you don't plan on SSHing into another box from that server.

---

### Post by trundlenut on 2009-09-09
I didn't think I would need to be able to SSH from a server until I needed to copy a load of files from one server to another then it was very handy indeed.

---

### Post by Cardale on 2009-09-09
> **trundlenut said:**
> I didn't think I would need to be able to SSH from a server until I needed to copy a load of files from one server to another then it was very handy indeed.

hmm...Interesting...

---

