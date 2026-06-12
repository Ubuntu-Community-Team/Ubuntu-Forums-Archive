---
title: "Access Ubuntu server from ubuntu client"
date: 2010-04-25
forum: Server Platforms
---

### Post by mw4jet on 2010-04-25
Hi, some basics of what I have and what I want to learn about.

I have an Ubuntu server 8.04.3, have been accessing from Webmin and Putty with Vista and XP, I am not very good with the terminal (but am learning), have followed how-to's to install it and set the server up, so far I am glad I wiped WHS and set up Ubuntu Server. 

I also have Ubuntu 9.10 multi-booting as a client. I am wondering if I can go to **_places, connect to server,_** and view my folders and files on my desktop?

I have openSSH and Samba installed on server, I know openSSH is on client as well.

I have tried to go to **_places, server_** but cannot get a connection, I would think that being on an Ubuntu client I would be able to see the server files without using the terminal or Webmin. 

Any help would be appreciated as always.

---

### Post by Iowan on 2010-04-26
I have a similar setup (client and server are both Hardy 8.04 machines) and I can access Samba files from this client. On the server, check **ps -ef |grep mbd** to verify Samba is running. I presume the client can ping the server...

---

### Post by BobVila on 2010-04-27
If you've got openssh running on the server, you can open up Nautilus and type ssh:\\[SERVERIP] and access the filesystem through your desktop GUI that way.

---

