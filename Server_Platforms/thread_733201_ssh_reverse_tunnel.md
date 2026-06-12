---
title: "ssh reverse tunnel"
date: 2008-03-23
forum: Server Platforms
---

### Post by wgcampbell on 2008-03-23
Trying to setup a machine at work for ssh remote access.  I don't have control of the router, so I'm trying to use "reverse ssh tunneling".

I'm setting up my home machine as the server.  Everything works in a test environment (at home with another box) , but **not **when I try to setup the connection from work.

For example:
ssh -v -N -R 5555:localhost:22 192.168.1.113
...this works on my local home network.

ssh -v -N -R 5555:localhost:22 myMachineAtHom
...does not work.  The error is: "Remote: Server has disabled port forwarding"

I don't understand this error since it is using "port forwarding" and works just fine in the home test environment.

Any help would be appreciated.

(And yes, I have forwarded port 5555 on my home router to 192.168.1.113)

---

### Post by wgcampbell on 2008-03-23
Sorry, I jumped the gun.  I was confused on what port to forward on my home machine (in the router).  I needed to forward port 22

---

