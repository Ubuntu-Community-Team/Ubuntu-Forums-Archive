---
title: "need some help on 6.06 LAMP"
date: 2007-07-22
forum: Server Platforms
---

### Post by ratbastard on 2007-07-22
Hello all, 

My objective is to run lamp on one machine and my desktop on another -- 
The desktop is PClinixOS and The LAMP is on 6.06 with no Gui - 



When I make web pages on the desktop I need to get them over to the servers Apache2 directory -- 

I am guessing FTP / Samba would be the best way -- 
but at this point PC Linux OS (the samba utility in the admin center) keeps telling my I do not have A qualified Domain name . 

I am using a DYN dns set up. 

any takers on my dilemma or maybe an easier way to accomplish my task.

---

### Post by jtc on 2007-07-22
Why not take a look at NFS or SFTP instead?

NFS if it is on the same local network, behind a router/firewall.
SFTP is the server is on a remote network.

---

### Post by ratbastard on 2007-07-22
Okay I am getting closer I am using smb4k and I see that samba in on 6.06 -- 

JUst need to Config Samba -- 


Any help would be most nice!!!!

---

