---
title: "Remote GUI Access to Ubuntu Server 11.04"
date: 2011-11-11
forum: Server Platforms
---

### Post by Monery on 2011-11-11
I been looking into the idea of adding remote GUI access to my Ubuntu 11.04 server. The main reason is there are some Linux apps that I would like to run, and would like to run them not only at home but when I am out and about. I also am not looking to dual boot my desktop and laptop so this is the reason I am thinking I can do this from my allready existing and under used server I currently have running

What I am looking for is...

1) A detailed procedure to add a GUI to Ubuntu 11.04 Server. I prefer GNOME since I am used to it but unity will work as well

2) Server/client software so I can access the system remotely from Windows based PC's. There is also a chance that various Linux OS's may also connect to the system

---

### Post by boetzie on 2011-11-12
for the last part of your question. 
- I installed virtualbox on my windows machine, and installed ubuntu as aa virtual. 
- I remotely connect through ssh to my server (from my virtaulbox ubuntu) (i use putty)
- Putty creates a tunnel over ssh for the interface search on X11 port forwarding on google. 

good luck
[B]
[/B]

---

