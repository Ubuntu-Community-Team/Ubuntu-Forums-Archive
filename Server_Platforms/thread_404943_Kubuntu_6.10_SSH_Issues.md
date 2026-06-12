---
title: "Kubuntu 6.10 SSH Issues"
date: 2007-04-09
forum: Server Platforms
---

### Post by userthebuntu on 2007-04-09
Hi everyone,

I am trying to set up my kubuntu box for remote ssh access.
I have a dyndns account all set up, openssh-server packet installed and sshd_config for the server altered (now listening on port 27015).
My router forwards 27015 to my LAN IP, the ssh server should be running and still whenever trying to log onto the server I get a message:
"Name or service not known"

When typing netstat -tulpen I don't see anything listening on 27015, however I have done the /etc/init.d/ssh reload and judging from the "OK" I get the server should be running.

Another weird thing is that when setting the port to 22 I can log on via ssh user@localhost but when changing the port to 27015 or anything other than 22 I get the same message (name or service not known) when putting ssh [email]user@localhost:27015...just[/email] putting ssh user@localhost gives me a connection refused.

Anyone have an idea?

Many thanks in advance

---

### Post by rsermilik on 2007-04-09
man ssh is your friend.
Try ssh -p 27015 user@localhost instead.

---

### Post by userthebuntu on 2007-04-09
Thanks and sorry I didn't check before.
I also just ran into that -p thing and tried it but now i'm getting:

ssh: connect to host HOSTNAME port 27015: Connection refused

Looks like either my router or ubuntu isn't letting the connection go through. Or could it be anything else?

EDIT:

Also, do you know why port 27015 isn't listed listening when typing netstat -tulpen ?

---

### Post by rsermilik on 2007-04-09
Does ps ax show that sshd is running when listening on port 27015?

If doing ssh -p 27015 user@localhost the your router is not involved. This is locally on your machine. If doing ssh -p 27015 user@a.b.c.d does not work and a.b.c.d is the external ip address of your router its your router. But most home routers don't allow that. Instead use ssh -p 27015 user@e.f.g.h where e.f.g.h is the LAN ip address of your server.

---

### Post by userthebuntu on 2007-04-09
I'm new to linux so I don't know if this is the dumbest command ever, but:

ssh localhost -p 27015 | ps ax

gives me a list of processes and sshd itself is missing from it.

Same goes for replacing localhost with my computer's LAN address.


Does that mean sshd isn't running? However as stated above I can log on locally when running sshd on port 22. Also I started and restarted sshd a couple of times (together with the sudo).

EDIT: I just rebooted my computer and ssh localhost -p 27015 is working now. However ssh adress.ath.cx -p 27015 doesn't. ath.cx is one of those dyndns service URL's carrying my current IP address.
The shell replies: Connection refused so I'm guessing now we're at my router not allowing access right?

UPDATE: It's working...my gf can log on from an external computer. Thanks rsermilik!

---

### Post by rsermilik on 2007-04-09
Your welcome.
Remember the 'man' command. It gives you the manual pages of the  specified command, like 'man man'. Try it....

When you change the port number in sshd_config or when you change anything in any daemon you have running - remember to restart the service for the changes to take effect. 

If from your local lan you give the command 'ssh -p 27015 adress.ath.cx' it means that you want to log in with the same username as you have logged in with on the computer your are doing this from. Otherwise you must give a username.

Also remember many routers don't allow you to come from internal lan out to the outside and then going in again.

---

