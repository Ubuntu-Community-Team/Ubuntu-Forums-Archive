---
title: "SSH Tunneling (SOCKS) Overhead?"
date: 2011-02-22
forum: Security
---

### Post by kevin11951 on 2011-02-22
Does anyone know of any benchmarks for the overhead incurred by encrypting your web traffic over an SSH proxy?

The following assumptions are made:

[LIST]
[*]The client is on a 10mb (symmetrical) connection
[*]The server is also on a 10mb (symm.) connection
[/LIST]

---

### Post by bodhi.zazen on 2011-02-22
> **kevin11951 said:**
> Does anyone know of any benchmarks for the overhead incurred by encrypting your web traffic over an SSH proxy?

The following assumptions are made:

[LIST]
[*]The client is on a 10mb (symmetrical) connection
[*]The server is also on a 10mb (symm.) connection
[/LIST]

IMO the overhead is fairly minimal, and most of the overhead will depend on your network / server and not the ssh protocol.

You will need to do the benchmarks for yourself, take a look at tools such as ab ;)

---

