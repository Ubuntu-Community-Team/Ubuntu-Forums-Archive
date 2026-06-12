---
title: "Samba home share password vs real user password"
date: 2007-11-07
forum: Server Platforms
---

### Post by enryfox on 2007-11-07
Hi all,

i need to set-up a small workstation with multiusers access (8+ users); i have created an account for each user and i would like each user to be able to access his own home folder from his windows laptop. I have uncommented the [home] sections in smb.conf and now i'm adding users with smbpasswd but i have some doubts regarding passwords: is the samba password not related to user password ? 
When i create a user i set-up an initial password and invite the user to change it at first login; do the user also have to change his samba password or do they sync automatically ? 

thanks
bye

---

### Post by MJN on 2007-11-07
A user's Samba password is indeed a seperately-stored credential to the user's system password.
 
The system passwords are stored as a hash and hence any Samba-password synchronisation would have to be done at the time the initial/new system is set (as, by design, the hash cannot be reversed).
 
This is not an area I am familiar with however until someone comes along with a simple one-click solution it may be worth your while searching for info about the pam_smbpass PAM module which sets both passwords at once.
 
Of course, you would perhaps ideally want Samba to simply use the system password outright but this is beyond my experience.
 
Mathew

---

