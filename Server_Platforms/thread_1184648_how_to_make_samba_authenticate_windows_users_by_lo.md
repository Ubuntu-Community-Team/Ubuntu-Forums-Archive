---
title: "how to make samba authenticate windows users by local linux account?"
date: 2009-06-11
forum: Server Platforms
---

### Post by chuugokujin on 2009-06-11
ubuntu 9.04 amd64
server name: s001
valid group: sales
valid user: jsmith
target folder: \doc
other folders are shared as public, only this one needs authentication.

[document]
path=\doc
valid users=@sales

I have some windows users that didn't even log in by password, I think it's the best way to authenticate them when they access this folder.
However when I tried one XP computer to access it, it prompts me for user name and password, so I input:
s001\jsmith
[password] 
but it failed.

anything wrong or missed? thanks,

---

### Post by grantemsley on 2009-06-11
samba usually keeps its passwords seperate from the system.  check out the smbpasswd command.

---

### Post by chuugokujin on 2009-06-11
> **grantemsley said:**
> samba usually keeps its passwords seperate from the system.  check out the smbpasswd command.

Problem solved, thank you gantemsley!

---

### Post by grantemsley on 2009-06-12
You're welcome

---

