---
title: "Redundant servers"
date: 2010-05-05
forum: Server Platforms
---

### Post by rwslippey on 2010-05-05
Ok new idea here.. (I enjoy just "playing" with things to see if and how they work)

ok here is the senerio...

I wanted to host a few websites on a local dedicated server... I've seen VMWare (too expensive).. and heard of ubuntu doing virtuilaztion. The question I have is... if I creat a web server...is their a way to have a second one running along side it to pickup if the first fails, complete with all databases, files, ect...  The idea here as you ahve guesed is to have a second server pickup if the first fails. I'm not above reading documentation and learning my way through it if someone can point me in the right direction.

Thanks

Rob

---

### Post by waloshin on 2010-05-05
I would believe a) it would be a mirrored server, or b) a load balanced server.

---

### Post by HermanAB on 2010-05-05
Here you go:
[http://linux-ha.org/wiki/Main_Page](http://linux-ha.org/wiki/Main_Page)

---

### Post by rwslippey on 2010-05-05
Thank you for your replies... I looked at Linux HA looks like it might work. 

My total intent here is 1 physical server with atleast 2 virtual servers for the purpose of web hosting. 

If I want to update a package on one of the servers I don't want the website some come down... and vis versa for the other server. 



I know this kind of deffies the purpose the redundant system ...exspecially if your hardware server fails.. but this is mostly a learning experience more than production.

Thanks again...

---

### Post by spynappels on 2010-05-05
Just a quick question, what makes you say VMWare is too expensive? VMWare ESXi is free for a full featured bare-metal hypervisor. Might be worth having a look at.

---

