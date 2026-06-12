---
title: "HELP: Problem opening a port"
date: 2008-02-11
forum: Server Platforms
---

### Post by cjtjamandra on 2008-02-11
I want to open the port 1983 using this command:

sudo iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 1983 -j ACCEPT

but it seems not to be working because the port is still closed. i have issued the command:


netstat -an | grep "LISTEN "


and still, the port 1983 is not there... please help me.. i have tried so many iptables command in opening a port but nothing have worked... thx in advance...

---

### Post by amo-ej1 on 2008-02-11
you don't need iptables to do that, you need an application listening on the port, what incoming data are you expecting there ?

---

### Post by cjtjamandra on 2008-02-11
At last someone replies... my ubuntu box is sharing an internet connection and  iam using an xp as a client, and iam playing a game that uses port 1983, i cant connect to the game because i think my ubuntu box is blocking it...


i have tested to telnet through port 1983 from xp to ubuntu and it is refusing, so i thought that port 1983 is blocked... could you please help me... thx

---

