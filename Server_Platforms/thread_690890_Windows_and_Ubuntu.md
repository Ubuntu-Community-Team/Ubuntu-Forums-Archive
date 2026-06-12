---
title: "Windows and Ubuntu"
date: 2008-02-07
forum: Server Platforms
---

### Post by Vrekk on 2008-02-07
Hey, i run a dual boot between xp pro and ubuntu.  Well i have given an  old computer i have life and want to install ubuntu server edition on it.  Well all of the other computers in the house run windows alone, and i want to know if they will be able to use the server.  If it can be done, how?

---

### Post by linksolo74 on 2008-02-07
yes, windows computers can connect to a linux server. They have too, since about 85% of all servers use linux. How you do it though, i'm not sure.

---

### Post by Vrekk on 2008-02-07
Ok so if i set it up, they will be able to accessr files on the server without much effort to set up?

---

### Post by linksolo74 on 2008-02-07
[read this]("http://citnews.unl.edu/linux/LinuxPresentation.html#Cross%20platform") It appears you can. I'd say the best thing to do would just be set it up and try. I'm almost positive that it will work.

---

### Post by Vrekk on 2008-02-07
ok thanks, i will tell u if it works well i get it all installed, (i need to do a little hard ware installing first)

---

### Post by lnx4me on 2008-02-08
You will need to install samba and configure it. the samba by example 3 is posted to the web. I bought the book. just google samba by example. it will guide you through the complete setup. 
when/if you have setup your server just install samba
apt-get install samba
then you will need to edit the smb.conf file i believe you will find it in
/etc/default/samba or /etc/samba  I forget which directory.

hope this helps.

---

