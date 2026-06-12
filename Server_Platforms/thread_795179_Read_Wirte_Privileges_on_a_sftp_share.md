---
title: "Read Wirte Privileges on a sftp share"
date: 2008-05-15
forum: Server Platforms
---

### Post by very_japi on 2008-05-15
So im setting up as server for my office. THis server will act as a SAMBA, HTTP, SSH, MySQL,ASP .NET, php, NFS, etc. server. 

Right now im in the process of choosing a distribution  for it. I would like to use Ubuntu since its the distribution imm most familiar with, but theres only one thing (one pretty important thing) thats pointing me towards Fedora 8:

I need to be able to remotely and securely modify files on the web server, hece my need to mount via ssh (sftp) the /var/www folder AND be able to modify it. (Samba just doesnt cut it for me, because i dont want to leave /var/www writeable by everyone)

You cant just login as root on ubuntu, so my question is, how can i SECURELY have read/write acces to /var/www using Places > Connect to server > SSH ? 

any ideas?

---

