---
title: "shutdown server simultaniously with workstation"
date: 2006-04-24
forum: Server Platforms
---

### Post by lucien on 2006-04-24
Hi there,

i have a small "server" with apache2, mysql, php, python, ... for my webdesign issues. I only need it to be up while my workstation runs also, so it would be nice if the sever was shut down simultaniously with the workstation.

What i'm looking for is some kind of init script that is run when the workstation shuts down. It check whether the server is running. If not it quits. If yes, it does some kind of RPC and waits until the server is shut down, then it quits.

I have absolutely no clue how to start or what keywords I should google for.

Thaks in advance,
lucien

---

### Post by tomski on 2006-04-24
does the server have open sshd running?

if so you could ssh into it as root then at the command line type:
shutdown -h now

or

telinit 0

if you are running windows on the 'workstation' then you will need PuTTy
but if you run linux as 'workstation' then just type:
ssh xxx.xxx.xxx.xxx

---

### Post by lucien on 2006-04-24
Both run Ubuntu, for sure ;) 

I'll try this solution, thank you.

---

