---
title: "configuring login to samba shares"
date: 2008-09-06
forum: Server Platforms
---

### Post by z3uSS on 2008-09-06
Hy, i need to make an samba share with prefered users login into it. So far i managed to start samba up and share files to the network users but still can't manage to build them users for login and rights. So far i'm controling the acces to samba share from firestarter with ip white list :) but still my network users have full acces to the share and i need to have some acces rules, make some folders there accesible for only a few users, not to mention that not all users must have writable rights.Can someone help me ? i'm new to this and dunno what to do next. I'm readin now 2 extremly big books about it and can seem to figure it out.

i forgot to mention my config : ubuntu server edition 8.04 with kubuntu desktop installed on it. the hardware is more than the required for what i wanna do here ( 1Gb DDram, p4 proc and MB with 800 + FSB )

PS escuse my bad english :)

---

### Post by windependence on 2008-09-06
I can't really tell you one simple way to do this because as usual in Linux, there are so many ways you can accomplish the same thing. Generally, you would use user groups to control access to directories and files. Here is a small tutorial that may help you;

[http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)

-Tim

---

### Post by z3uSS on 2008-09-06
thx.. nice tutorial.. i had some problems cause my samba didn't create smbusers.conf file but after i figuret that out it went all smoothly. Now all i have to do is create users and shares for them. Still i have a small problem.. can u tell me how i can make quotas for user in the Share folder ? and how i can set an general quota for all shares? 

ps I know u are against ppl who uses servers with GUI interface but this is just a test for me.. after i figure it all i reinstall and rebuild it without GUI.

---

### Post by bab1 on 2008-09-06
I'll give you a reason to not use the GUI to setup Samba.  It does not work!  It's broken.  The reasons are many, but in a nutshell, the GIO-gvfs (the GUI) is in a transitional state.  There are changes being made that will be part of Intrepid (9.04).  What this means is: you should setup Samba manually if you want consistent results.  I personally believe that it is good practice to confirm the infrastructure (IP addressing and DNS) is correct before configuring Samba (the server) and smbfs (client).

I suggest reading [[COLOR="Blue"]**Samba3 by Example**[/COLOR]]("http://us1.samba.org/samba/docs/man/Samba-Guide/").  This is a great intro to Samba configuration.

Edit:  I would use ACL's if you have complicated permissions (access) needs

---

### Post by z3uSS on 2008-09-06
> **bab1 said:**
> I'll give you a reason to not use the GUI to setup Samba.  It does not work!  It's broken.  The reasons are many, but in a nutshell, the GIO-gvfs (the GUI) is in a transitional state.  There are changes being made that will be part of Intrepid (9.04).  What this means is: you should setup Samba manually if you want consistent results.  I personally believe that it is good practice to confirm the infrastructure (IP addressing and DNS) is correct before configuring Samba (the server) and smbfs (client).

I suggest reading [[COLOR="Blue"]**Samba3 by Example**[/COLOR]]("http://us1.samba.org/samba/docs/man/Samba-Guide/").  This is a great intro to Samba configuration.

Edit:  I would use ACL's if you have complicated permissions (access) needs
Actualy it went pretty well with GUI ( first i installed ubuntu dektop 8.04 and it was harder to make samba work there ) :). The main problem was my lack of knowledge. But i'm starting to learn pretty well so soon i'll be able to lose GUI. Until then is imposible to do that. Working only with MC and manualy is way too much for me. GUI really makes it easy for a begginer. Atm i have samba up with user configured ( i know u'll laugh but for me is an achievement :) ). My last problem is establishing quotas for users. But i'll study that link u gave me and i hope i learn something from there. thx for the help

---

### Post by bab1 on 2008-09-06
I'm glad your learning.  Even the mistakes are a learning oportunity.  Quotas are **not** a Samba thing.  You can set user [[COLOR="Magenta"]**disk quotas**[/COLOR]]("http://www.debianadmin.com/implement-and-manage-disk-quotas-in-linux.html") in Linux (Ubuntu).

---

### Post by bab1 on 2008-09-06
Double post (sorry)

---

