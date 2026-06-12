---
title: "can't connect to sshd over internet"
date: 2005-09-13
forum: Server Platforms
---

### Post by jerome bettis on 2005-09-13
hi 
 
i'm trying to set up sshd over here so i can work on this machine when i'm at work and stuff. 
 
ssh [email="user@127.0.0.1"]user@127.0.0.1[/email] works fine 
 
xxxx@ ~ $ ssh -vvv user@`ip` 
OpenSSH_3.9p1, OpenSSL 0.9.7e 25 Oct 2004 
debug2: ssh_connect: needpriv 0 
debug1: Connecting to 67.186.xxx.xxx [67.186.xxx.xxx] port 22. 
debug1: connect to address 67.186.xxx.xxx port 22: Connection timed out 
ssh: connect to host 67.186.xxx.xxx port 22: Connection timed out 

^ here `ip` is just a simple python script i wrote to get my external ip address.  if anybody wants it i can post it.  what i'm doing is trying to connect to my laptop (from the laptop) via my external ip address.    i've tried connecting from a really remote machine and the same thing happens.
 
i have a firewall on my router, port 22 is forwarded and connections to port 22 are allowed. does anybody know what's going on and how i fix it?? 
 
thanks

---

### Post by jerome bettis on 2005-09-13
ok nevermind i figured it out (right after i made this post haha)

i just restored the factory settings on my router, added a forward thingy for ssh and it works fine now.  this is pretty sweet.

---

