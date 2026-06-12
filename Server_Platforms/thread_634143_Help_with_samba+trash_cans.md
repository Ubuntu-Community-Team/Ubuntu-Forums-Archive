---
title: "Help with samba+trash cans"
date: 2007-12-07
forum: Server Platforms
---

### Post by jdm2 on 2007-12-07
Hi, as some of you know I'm setting up two severs for my school.  I'm almost done with one.  I did a fresh install of ubuntu drapper desktop.  Then I create the users and groups.  I then set the permissions and then I installed the packages for samba and swat (I tell you which package I used for swat when I get a chance to check).  I then set up the samba users and shares.  Everything is working, but besides me and the teacher account none of the other accounts have .Trash.  Not even the root account.  I went into terminal and did sudo nauitlus.  I then hit ctrl h and it didn't show up.  When I deleted a file in a folder it didn't go into the root trash or the user trash.  Everything else, but this is working.  I need some help to figure out why this is.  Thanks for the help. 
jdm

Note:  The user account are jdm, teacher, g01 - g20
Note:  Group name is teacher and teacher is the only user for it. 
Note:  Also on the g01 -g20 I changed the shell to /bin/false so they couldn't login to the sever. 

Thanks for the help.

---

### Post by jdm2 on 2007-12-11
Thanks for the help.  I got it to work.  .Trash is created when you first login to the accoutns.  That goes for root too.
jdm

---

