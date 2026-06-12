---
title: "local server newbie"
date: 2009-08-17
forum: Server Platforms
---

### Post by jwxie on 2009-08-17
Hi. I will install Ubunto as the backbone for my local home server - mainly for projects and developments, for example, use it to host a drupal test site (which require maybe memory limit up to 120M)...

well... basically here are my newbie questions:

1. Instead of having an no-ip, I just want to skip this easy step and use my local IP. 192.168.1.XXX
I have a cable modem attach to my router. The server gets its connection from the rounter. But every few days or weeks, the IP will change from let say 101 to 102, or from 100 to 103. 
How do I use this local IP so I can browse the php and html files on my desktop (which is also connected to the same router).


2. I am still new to operating server, but the time for the devleopment is a bit out of time. I would like to learn the command but ATM (at the moment), I still want to able to drag, to delete, to copy, to rename my files on my desktop. Yes, I could just install the server on Ubuntu Desktop. But I decide not to because I want to reduce the amount of resources being use. So whatever it is - my server is the command-line default server. 

How do I get the control to do like FTP on my desktop? What client should I install?


3. Last but not the least, I am planning not to use apache for many reasons. So far Nignx is my choice. If I decide to use Nignx as my server operator, is there any specific changes need to take for all the above? Like setting up a FTP access, phpmyadmin access and such...


Bascially I need this server just like any any hosting,  - you have the remote and GUI access from my desktop - instead of doing everything on the server using command.


Please guide me through this. Thank you very much!

---

### Post by drave on 2009-08-18
1. use static ip address's for your machines, or at least for the servers. 
see /etc/network/interfaces. there are a gazillion examples on the net.

2. i like freenx as a remote gui. when your not connected it shuts down all the gui related stuff. you have to install the gui then make sure gdm/kdm/xdm whichever is not running.

3. dont know

---

