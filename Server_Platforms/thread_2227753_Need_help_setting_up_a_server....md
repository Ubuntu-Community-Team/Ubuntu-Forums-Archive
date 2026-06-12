---
title: "Need help setting up a server..."
date: 2014-06-03
forum: Server Platforms
---

### Post by joshua31 on 2014-06-03
Okay, so I have not had very much experience concerning trying to set up servers. I am a windows nut and have been setting up make-shift servers through the sharing process on my local network for about a year now, just from tinkering with it. Ubuntu server i am finding to be a whole new animal. I followed a server making process for ubuntu 12.04 i think it is at this link:  [https://www.youtube.com/watch?v=ndAYZ0DJ-U4](https://www.youtube.com/watch?v=ndAYZ0DJ-U4). I had downloaded ubuntu server and ubuntu desktop onto the hp i have been trying to set p to be a server. I find this to be a waste of time because i desired for my computer to not have to take 2-3 minutes just to load something on the desktop. So i re-installed and set up a server according to how that video showed. The problem i primarily had with desktop is that though i could see what was on my server from the network, my windows computers could not access it. Now as i have made a server according to the gentleman in the link i posted has shown, the server is no longer on the network and i am left sorely confused as to what to do in order to take the next step. Could i receive some assistance? Eventually, I would like to have either a samba server set up or an openSSH set up. 

Btw, i am using ubuntu 14.04 server software, an hp small form factor compaq with 2 GB RAM, 2 ghz cpu speed, and an 80 gb HDD with two partitions; one for swap, and the other for the main disk storage.

I believe the biggest problem i am encountering is trying to get my windows 8.1 laptop to see the separate computer acting as a server. As of now, i have tried to set up the server with a static ip and an auto DHCP server ip. Neither got me anywhere concerning it and i am having a hard time trying to get this to work.

---

### Post by joshua31 on 2014-06-03
Okay, so i figured out a way to set up a server with it through the workgroup. Once i set the workgroup of all the computers in the network while getting on an DCHP server for the sake of ip address, it works great. This was done through vi /etc/network/interfaces.

---

### Post by dmhymers on 2014-06-04
What are you trying to do with this server? That'll help us figure out what advice to give you. Do you desperately need a desktop environment, or would you be comfortable learning how to use the command line (latter highly recommended)

---

