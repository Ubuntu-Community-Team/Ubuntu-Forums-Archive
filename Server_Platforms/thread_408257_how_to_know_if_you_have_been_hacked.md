---
title: "how to know if you have been hacked"
date: 2007-04-13
forum: Server Platforms
---

### Post by PetePete on 2007-04-13
I dont think I have been hacked, or even slightly suspect it.

but are there any things i can do to check if any intruders have entered my system? i could look at my logs, but then any person gaining access would edit/rm them straight away.

this is what i tend to do, is it good enough?
1) full port scan using nmap on local address, see what ports are open. Should just be the ones i've setup

2) check /etc/passwd for any unknown new users

---

### Post by mac.ryan on 2007-04-13
The most undetectable of the threats are probably rootkits. If you want to, you can install one rootkit detector from the repos: *rkhunter* or *chkrootkit*. The problem with this kind of stuff is that it is a continuous chasing between the creativity of the perpetrators and that of the defenders...

You might wish to have a look at this [simple article]("http://www.psychocats.net/ubuntu/security") as well (on ubuntu and security in general).

---

### Post by eentonig on 2007-04-13
Check your network traffic regularly. create a baseline of traffic that you're used/allowed to see and exclude this from the list. 

it's a pain in the beginning, but once you have established a baseline of legite traffic (including ports and destinations), new flows will jump out.

---

