---
title: "rsh ... linked ... ssh"
date: 2006-09-26
forum: Server Platforms
---

### Post by gblemings on 2006-09-26
Hi, i have a ubuntu server on my network, running some applications.  I need the ability to rsh over to a Risc6000 running 
AIX 4.3.3. 

the rsh doesnt work, and when i look around the ubuntu, i notice that the rsh command is linked to the ssh command, so that when every i try rsh....it fails showing ssh. 

i dont want to do ssh, because my risc6000 doesnt have it setup.  looking into trying get the risc6000 Aix 4.3.3, to run ssh, is a job in itself...

bottom line is, i need rsh...i cannot find it anywhere on the ubuntu machine (any reference i find, is linked to ssh).

So questions 

1) how do i unlink it so rsh will run?
2) if i cannot, where do i go to 'install' setup 'rsh' so that it works? 

i understand the underlying issues with rsh vs ssh, the interaction of these two machines on our network, are NOT accessable to the internet...

thanks for any feedback...i am new to ubuntu (linux), but am familiar with Unix (aix), so i see lots of similarities...

garyb

---

### Post by colo on 2006-09-26
```
sudo apt-get install rsh-client
```

---

### Post by gblemings on 2006-09-27
wow, that was easy, many thanks for you reply, i was messing around trying to figure that out for while...

once again, thanks for the reply, 

garyb

---

### Post by mcrae on 2006-10-09
Doing 
sudo apt-get install rsh-client
was really easy but I still do not manage to rsh :
rsh: connect(remote.host [xxx.xxx.xxx.xxx]): Connection refused

...everything seems the same as before

---

### Post by rastilin on 2006-10-11
Well it might be that your target isn't set up to accept inbound connections.

1. Does the thing run a server that is listening on a known port?
2. Does it block or drop packets?

---

### Post by PolSed on 2006-10-11
It could be to do with your hosts.equiv and .rhosts files on the client and server. I'm not going to re-invent the wheel and explain there setup, but if you google .rhosts you will find loads info and examples on how these two files are configured.

---

