---
title: "process authentication"
date: 2009-03-10
forum: Security
---

### Post by mkrahmeh on 2009-03-10
gurus
there are many protocols/methods for authenticating a remote client/user (i.e kerberos, SSL), but is there any kind of protocol/method for authenticating a certain **process** on a remote machine ???? such that i need to ensure that a process establishing a session is the right process, not a process that is created by the user himself ??

can anyone refer me to a website/book that might help ?
thx in advance

---

### Post by uljanow on 2009-03-10
That depends on the programming language. One universal approach would be to check user ids. E.g. C/C++ and POSIX IPC (Unix domain sockets) allow to include credentials.

---

### Post by mkrahmeh on 2009-03-10
> **uljanow said:**
> That depends on the programming language. One universal approach would be to check user ids. E.g. C/C++ and POSIX IPC (Unix domain sockets) allow to include credentials.

i was thinking about certain process ID's..what do you think ?
bear in mind that we r talking about a process on a remote machine..well..am afraid that the process has to be started by the user who is sitting on the machine:o

any ideas ??? or maybe references that might help ? 
been looking around but found nothing :(

---

### Post by bodhi.zazen on 2009-03-10
I can not tell what you are asking.

Tools that can help include sudo and apparmor.

---

