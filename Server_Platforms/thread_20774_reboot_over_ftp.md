---
title: "reboot over ftp"
date: 2005-03-18
forum: Server Platforms
---

### Post by flade on 2005-03-18
I still got problems with ssh. I'll be back in the office on Monday, but in this time (over weekend) I want to play with my server. 

So is there a way to restart computer over FTP. I have root access.



Tnx,


Flade

---

### Post by alastair on 2005-03-18
Unless you know a security vulnerability .... no.

---

### Post by flade on 2005-03-18
[QUOTE=alastair]Unless you know a security vulnerability .... no.[/QUOTE]

I was afraid of that. 


Tnx,


Flade

---

### Post by az on 2005-03-18
"I still got problems with ssh"

Are you running the server sshd?  Because ubuntu comes with just the client by default.

sudo apt-get install ssh

---

### Post by flade on 2005-03-19
For SSH I'll put it this way:

I have Cisco router, Catalyst swith which I do not program myself - It's done by my ISP. On the local net I have ubuntu server with WWW, SSH, FTP. My ISP opened ports for services that I run.

The problem is when I want to login from outside (ie: from my home). Nothing happens. My Office network has 3 subnets that can not see each other, (IP's are public). 
Server IP is set to accept connections from all subnets (local net) and also outside.

My WEB server works, so I think there is problem in SSH configuration or router. ](*,) 

I have SSH installed (OpenSSH Client and Server).


I'm kinda new to this, but understand a bit of networking.

------------

Flade

---

### Post by Jad on 2005-03-19
installing Webmin is an option here

---

### Post by flade on 2005-03-21
Solved the problem.

Reinstalled Box and works like charm.


-----------------
fladé

---

