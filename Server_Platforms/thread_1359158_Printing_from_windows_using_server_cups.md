---
title: "Printing from windows using server cups"
date: 2009-12-19
forum: Server Platforms
---

### Post by Spiritof76 on 2009-12-19
I have three computersa on my network.
Ubuntu 9.10 Server
Ubuntu 9.10 Desktop
Vista Desktop.

My ubuntu Desktop prints and store files gloriausly. 
Vista sees that I have a printer on my server  and Installed the drivers onto the windows machine but It informs me that access is denied  and that I am unable to connect.
I also cant access the  file system from the vista machine.

---

### Post by garfonzo on 2009-12-19
I think you need to check your Samba settings. I have a Ubuntu Server and a Vista desktop. I have the server hard drives mapped to my Vista box so I can access them as if they were physically on the Vista machine. The printer is also just as accessible. 

The way I am able to access the Samba shares (and printer) from my Vista box is my user name on the Ubuntu Server is the same as the user name on the Vista box. I set this all up a while ago so I'm a little rusty on how I did it, but I believe you have to do something like add a user for samba. 

[This link may help.]("http://www.comptechdoc.org/os/linux/manual4/sambausers.html")

This should open up the printer and the files for the Vista box. Hope this helps.  

Note: Although I can see the printer attached to my server, I can't print to it from Vista. My XP machines can print fine, but not the Vista box. No idea why.

---

