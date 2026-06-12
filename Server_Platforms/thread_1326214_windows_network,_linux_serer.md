---
title: "windows network, linux serer"
date: 2009-11-14
forum: Server Platforms
---

### Post by Fenix1 on 2009-11-14
I have linux server in school which has a network. I assigned an ip for the server that will work in the network, now do I have to install samba and all this stuff so i can get DNS, vsftpd, CUPS services working from the linux server to computers in the network in my school.

If so how accurate is this on solving my problem [http://www.linuxquestions.org/questions/slackware-14/join-linux-to-windows-domain-371794/](http://www.linuxquestions.org/questions/slackware-14/join-linux-to-windows-domain-371794/)

like, if you want to add windows machine to domain, you go "my computer", "properties", "computer name" and add the domain to its rightful place. So is adding linux machine to windows domain, like samba install, then add domain name to smb.conf and etc. like in the link above. or am I missing the bigger picture

I know Im a bit unclear, but you wont mind, thank you understanding :)

---

### Post by Vegan on 2009-11-14
look into LDAP if you want to run a swarm of servers. This will allow a single log-on.

---

### Post by koenn on 2009-11-15
your missing the big picture. Worse, you'd probably wouldn't recognize the big picture if it was standing in front of you.

To join an existing AD domain, look here:
[https://help.ubuntu.com/8.10/serverguide/C/likewise-open.html](https://help.ubuntu.com/8.10/serverguide/C/likewise-open.html)

For the rest : samba isn't DNS, DNS has nothing to do with ftp, and ftp is not CUPS, and so on.
If you're going to run a server, step 1 is you should have a clear idea of what you want / need this server to do. And then step 2 is to set it up accordingly. 
Your post sounds as if you missed step 1.

---

