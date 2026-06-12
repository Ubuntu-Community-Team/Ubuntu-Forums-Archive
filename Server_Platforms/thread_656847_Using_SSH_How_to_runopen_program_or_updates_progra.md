---
title: "Using SSH: How to run/open program or updates program/Ubuntu?"
date: 2008-01-03
forum: Server Platforms
---

### Post by xdefconx on 2008-01-03
Hye all!

I would like to ask how we can do by using SSH client on others PC "to  tell" my Ubuntu server to run some application and updating my Ubuntu version.

So what i need from SSH is:

a- updating my Ubuntu
b- to run Xchat IRC program

thanxs

---

### Post by chewearn on 2008-01-03
> **xdefconx said:**
> Hye all!

I would like to ask how we can do by using SSH client on others PC "to  tell" my Ubuntu server to run some application and updating my Ubuntu version.

So what i need from SSH is:

a- updating my Ubuntu
b- to run Xchat IRC program

thanxs

When you ssh to a server, you get a terminal prompt; any terminal commands you issue will run on the server.  Therefore, e.g. to update, just issue "sudo aptitude update && sudo aptitude upgrade"

---

### Post by xdefconx on 2008-01-03
> **AstalaVista said:**
> When you ssh to a server, you get a terminal prompt; any terminal commands you issue will run on the server.  Therefore, e.g. to update, just issue "sudo aptitude update && sudo aptitude upgrade"

Thanxs AstalaVista, u really help me a lot!!:guitar:

---

