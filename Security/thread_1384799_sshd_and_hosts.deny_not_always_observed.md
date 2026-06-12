---
title: "sshd and hosts.deny not always observed"
date: 2010-01-18
forum: Security
---

### Post by lafayette on 2010-01-18
Hi all,

I'm having troubles trying to understand this problem:

my homeserver until yesterday had a public IP, staying on network, with sshd running and all was fine;
this evening I changed the IP, giving it a local lan address, and what happened if I tried to connect to it by ssh?

I got an error about "Connection closed by remote host". Google helped me finding that was regarded to hosts.deny file, that was actually containing a line

ALL:ALL

that I commented, and all was fine.


My question is: why the hosts.deny (that has never changed) was observed only with the local IP?

I tried to switch back to the public IP and leaving ALL:ALL, and it did connect without any problem! Any hint on what to investigate to know more?

---

### Post by lafayette on 2010-01-18
maybe it's needed:

ubuntu 9.04, sshd 5.1p1-5ubuntu1

---

