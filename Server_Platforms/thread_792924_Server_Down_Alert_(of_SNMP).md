---
title: "Server Down Alert (of SNMP?)"
date: 2008-05-13
forum: Server Platforms
---

### Post by SomethingCronic on 2008-05-13
Hi,

I have a critical SSH server that I need to know quickly if there is a problem and it goes down for whatever reason.

Now I'm not sure if SNMP would help to alert me if there is a problem as I have no experience of it, maybe someone could let me know if that's the case and give some suggestions of what to use?

If on the other hand I'm barking up the wrong tree, would anyone be able to suggest an alternative? At the moment I'm thinking a script to ping the server and if the ping breaks then I receive an email alert or similar?? I don't want fail over so I don't think heartbeat will be the solution here.

But please, any suggestions are welcome :)

Thanks,

---

### Post by pytheas22 on 2008-05-13
I don't know about SNMP, but [OSSEC]("http://ossec.net") would do what you need...you can install it on another machine and have it watch your ssh server.  It can send you an email or SMS if the ssh server disconnects.  It can also do lots of other useful things to help keep the servers secure.

---

### Post by songshu on 2008-05-13
its not what you are looking for but it might be interesting if you are looking for such things any way.

i use monit, its pretty lightweight and it monitors pretty much every application you want, in case it will find an application failing it will attempt to restart it and sends out e-mail notifications if that happens, it runs on the box to monitor itself.

it actually never has been useful to me, but i have it monitor the sshd just to be sure ;)

---

### Post by SomethingCronic on 2008-05-13
Thanks guys, I'll give OSSEC a go - sounds interesting - I may well be back :)

---

