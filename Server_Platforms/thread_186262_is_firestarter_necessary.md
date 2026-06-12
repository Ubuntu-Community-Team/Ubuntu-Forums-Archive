---
title: "is firestarter necessary?"
date: 2006-06-01
forum: Server Platforms
---

### Post by miguelgomes79 on 2006-06-01
Hi
There are lots of discussion about installing a firewall like firestarter.
I talked with a friend of mine and i told him i use ubuntu and use lots of filesharing programs like amule, azureus and bittornado, and of course i navigate with firefox.
I asked him if i need a firewall like firestarter.
He said NO.
My question is: In wich cases do we need to install a firewall?

---

### Post by 23meg on 2006-06-01
To begin with, Firestarter isn't strictly a firewall but a frontend to the sophisticated iptables application, which is used to adjust the kernel's IP routing. It can be used to block incoming connections according to certain criteria, so it can be employed to function like a firewall app as well.

To answer your question:

- If you're running a server
- If you're not running a server but just have some apps / daemons that open and listen on a particular port 
- If you want simple control over incoming / outgoing connections

---

### Post by az on 2006-06-01
[QUOTE=miguelgomes79]
My question is: In wich cases do we need to install a firewall?[/QUOTE]


On a desktop, if you are running applications that are sending packets and receiving packets that you don't want snet or recieved.  If you only install stuff from the ubuntu repos, this doesn't happen behind your back and so a firewall is not needed like in windows.  The chance that spyware or other malware is present in the repos is greatly diminished because this is free-libre open source software and not just anyone can upload to the repositories.

On a server, you need a firewall for a number of things, not the least of which is to deny access to ip addresses that abuse your bandwidth.

---

### Post by Klaidas on 2006-06-02
Weel, my suggestion is to have it. I simply like to see incomming/outgoing traffic and blocked connections ;)

---

