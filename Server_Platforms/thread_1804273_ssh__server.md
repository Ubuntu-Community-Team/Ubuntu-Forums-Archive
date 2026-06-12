---
title: "ssh  server"
date: 2011-07-14
forum: Server Platforms
---

### Post by kirthi on 2011-07-14
I came across ssh server. I want to how to connect with my friend's system through ssh. Want should I do and How does it help me?

---

### Post by karlson on 2011-07-14
> **kirthi said:**
> I came across ssh server. I want to how to connect with my friend's system through ssh. Want should I do and How does it help me?

To connect from a Linux machine you would run:
```

ssh <userid>@<hostname>

```

What should you do and how does it help you I don't think anyone on this forum could answer.

---

### Post by kirthi on 2011-07-14
With ssh why can't I connect to another system??
If I give the host of other system will I be able to connect with them?

---

### Post by karlson on 2011-07-14
> **kirthi said:**
> With ssh why can't I connect to another system??

An error or a message would help.

> 
If I give the host of other system will I be able to connect with them?

Are you allowed access to the remote system?

---

### Post by msandoy on 2011-07-14
> **kirthi said:**
> With ssh why can't I connect to another system??
If I give the host of other system will I be able to connect with them?

SSH is a very good tool for administering remote systems and for setting up tunnels for routing traffic on a local LAN via internet. In order to use it, you need a running SSH server to connect to, and a user account with the proper user rights.

If you have a ubuntu computer running ssh server, it is also possible to connect to it from a windows computer with a program like putty.exe.

---

