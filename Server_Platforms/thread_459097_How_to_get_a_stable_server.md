---
title: "How to get a stable server"
date: 2007-05-30
forum: Server Platforms
---

### Post by dannytherocker on 2007-05-30
Hi, I would build a server to be used as printer server, data storage, p2p server and so on....
now, what about upgrades to keep it stable ? how should /etc/apt/sources.list be ??
thanks

---

### Post by compiledkernel on 2007-05-30
Just keep it in the Universe, and youll be ok.

---

### Post by craigp84 on 2007-05-30
Hi dannytherocker,

> what about upgrades to keep it stable

Normally your box will be stable, you'll normally only upgrade if it's not. The exception is security patches for a public facing box where security patching has to be a top priority.

```
sudo apt-get install unattended-upgrades
```

And the job is done :-)

Hope this helps,

-c

---

### Post by dannytherocker on 2007-05-30
> **craigp84 said:**
> Hi dannytherocker,



Normally your box will be stable, you'll normally only upgrade if it's not. The exception is security patches for a public facing box where security patching has to be a top priority.

```
sudo apt-get install unattended-upgrades
```

And the job is done :-)

Hope this helps,

-c

Maybe you're right.......thanks for you suggestion...

---

