---
title: "Linux Root with Non Linux Diskless Host???"
date: 2010-06-22
forum: Server Platforms
---

### Post by jk.cheng on 2010-06-22
I just finish set up ubuntu 10.04 server to play as root to serve diskless clients... Using some old time method... not using UEC, not sure UEC can work as diskless or not? hehe...

The problem here, 10 PCs which success boot up on PXE with different Linux Distro; got Fedora,OpenSuSE,Ubuntu Desktop... But, can i set up other OS as host such as window xp and etc???

If yes, any how to that i can look into... Because i had been looking on google for the hole day, result still negative...

---

### Post by koenn on 2010-06-22
You probably understand by now that for diskless clients, you need to download the entire operating system over the network + provide a filesystem for it, also over the network, + have a bootloader of some sort that can boot that whole contraption - without relying on harddisk addresses and such

So you need operating systems that are modified to to be capable of all that. For non open source OSes, that means you'll only be able to do this if the manufacturer of the OS made it possible.  

eg [http://msdn.microsoft.com/en-us/library/ms838569(WinEmbedded.5).aspx](http://msdn.microsoft.com/en-us/library/ms838569(WinEmbedded.5).aspx)

---

### Post by dapperdanny77 on 2010-06-22
I did it years ago on linux with a nfs root filesystem -[http://www.faqs.org/docs/Linux-mini/NFS-Root.html](http://www.faqs.org/docs/Linux-mini/NFS-Root.html)
I have no idea how to do it on windows ...

---

### Post by jk.cheng on 2010-06-23
Thanks for the information... I am looking on those documentations now...

Wondering... can UEC tech used as diskless system??? coz now i only run UEC for VPS only...

---

### Post by jk.cheng on 2010-06-23
> **koenn said:**
> You probably understand by now that for diskless clients, you need to download the entire operating system over the network + provide a filesystem for it, also over the network, + have a bootloader of some sort that can boot that whole contraption - without relying on harddisk addresses and such

So you need operating systems that are modified to to be capable of all that. For non open source OSes, that means you'll only be able to do this if the manufacturer of the OS made it possible.  

eg [http://msdn.microsoft.com/en-us/library/ms838569(WinEmbedded.5).aspx](http://msdn.microsoft.com/en-us/library/ms838569(WinEmbedded.5).aspx)

This document mean alot for some one really noob in microsoft stuff like me...

However, how can i get the information of integrate it into my ubuntu root server? and most important is how the license is count? (Hate this license stuff, but the customer just can't get out of it totally)...

---

### Post by arrrghhh on 2010-06-23
No licensing for Ubuntu clients.  Not sure how Windows diskless clients work tho... Not really a good forum for this type of discussion honestly.

---

### Post by koenn on 2010-06-23
On the linux side, your server would just need to do the dhcp + tftp part and serve the image to the clients - same as always

How to deal with the microsoft side and the licensing, I wouldn't know. Someone at Microsoft probably knows.

---

