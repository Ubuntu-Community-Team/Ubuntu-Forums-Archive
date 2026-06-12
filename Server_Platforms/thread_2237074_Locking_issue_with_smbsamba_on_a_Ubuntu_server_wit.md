---
title: "Locking issue with smb/samba on a Ubuntu server with mac clients"
date: 2014-07-30
forum: Server Platforms
---

### Post by rbnsweden on 2014-07-30
Found lots of input on this... so I know I am not the only one. But cannot find a solution.


Basically this is what happens. You have a folder with the name 1, in that folder you have the folders 11 and 12 and some files. When user 1 renames a file in folder 1 user 2 cannot move the folder 12 into 11 since it is locked. The only way to solve this is for user 2 to disconnect to the server and then reconnect to it.
 
This happens on both 10.8 and 10.9 as far as I can see.
 
This seems like regular file sharing and should not be a problem. Is there any way to fix this. I have tried disabling oplocks, but it does not seem to be the locking this is about.
 
//rbn

---

### Post by rbnsweden on 2014-07-30
Oh and by the way. I just noticed that I can manage this lock with only one user as well.

lets look at the same example as above... but in folder 11 there is a file. If no user els is logged in and user one changes a name of a file in folder 11, if he then tries to move folder 11 into folder 12 or the other way around... mac os x will tell him he has not permisson and will ask for admin rights (which of course do not work, even if you would have it)

I know some say this has to do with file preview, but I have tried this... I can recreate this even with "show preview column" turned off.

oh and by the way, this is how a share is setup:
[smb_share] 	
comment = smb main share
path = /srv/smb_share
read only = no
writable = yes
valid users = +groupname
force security mode = 664
force directory security mode = 775
force group = groupname

---

### Post by rbnsweden on 2014-07-31
Over 100 views and no one has any input. Please please... write whatever you come to think of... I am willing to try anything you might think helps!!

---

### Post by volkswagner on 2014-07-31
What version of Ubuntu and SAMBA are you using?

---

### Post by rbnsweden on 2014-08-01
Oh, sorry. 

I have been able to reproduce this on
Ubuntu 12.04
Ubuntu 12.04.4

Samba 3.6.3

/rbn

---

