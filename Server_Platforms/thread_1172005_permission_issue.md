---
title: "permission issue"
date: 2009-05-28
forum: Server Platforms
---

### Post by ace2007 on 2009-05-28
hi,
maybe someone could help me out, i am using Ubuntu server 8.10 with KDE GUI.
I heard alot about never login with root and i want to do the things right so I want to conform to that... 
 
My problem is that to run my backup program without having issue with permission, i need to make it run with the root account. could someone tell me what I have to do ?
 
the backup program im using is Keep
 
also, i need to be login with a user and share my session to be able to access remotly the server, is there any program to allow to connect properly?
 
thanks!
 
dany

---

### Post by JanvL on 2009-05-28
Hi

Start it with "run command" in the menu and give command

sudo keep

Then you should start it with rootrights without being root.

Regards
Jan

---

### Post by ghen on 2009-05-28
does sudo work from the run command effectively? In my meager knowledge I've been told that gksudo is for running graphical programs from the run command and sudo is reserved for the terminal.

---

