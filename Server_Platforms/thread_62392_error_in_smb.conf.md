---
title: "error in smb.conf"
date: 2005-09-04
forum: Server Platforms
---

### Post by haze03 on 2005-09-04
Ok in my continuing adventure to get windows to see ubuntu since it is serving all of my music, I attempted to add network suers in samba.  When following the ubuntu guide I got an error "params.c:Section() - Badly formed line in configuration file: ]
params.c:pm_process() - Failed.  Error returned from params.c:parse().
Error loading services."  What does that mean?  Where did I screw up when setting up samba\?

---

### Post by TheDanMan on 2005-09-04
We could better help if you posted your /usr/share/samba/smb.conf file contents.

---

### Post by Velox Letum on 2005-09-04
[QUOTE=TheDanMan]We could better help if you posted your /usr/share/samba/smb.conf file contents.[/QUOTE]
 Agreed. It sounds to me like you may have accidentally mistyped something.

---

### Post by cvmostert on 2005-11-01
I also had the same problem, but i seemd to fix it by editing the smb.conf file...
go to the part where it looks like this...

[]
path= /home/user
comment = ubuntu pc
available = yes
browseable = yes
public = yes
writable =yes

and make sure you have something written in the [], it can not just be empty.
example: [user]

that solved the problem for me to see my ubuntu pc on my win laptop over LAN.

hope it works.

remember, i am no professional, so try at will.

---

### Post by DaveRoberts on 2005-11-12
Top man! :) 

Found the empty []. Added [user]. Worked for me first time! 
Error message from testparm disappeared. Another problem
bites the dust!

Many Thanks

---

