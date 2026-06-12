---
title: "How to delete user profile when logoff in XP"
date: 2007-08-21
forum: Server Platforms
---

### Post by knutbert on 2007-08-21
Hi,
I'm running Ubuntu server 6.06 and Samba as a PDC with several Windows XP computers. How could I set up XP pro so that after domain user logs out the profile automaticly deleted from workstation machines? 
I'm using these computers as a Internet cafe and want every "new" users to log in with all my default settings e.g. Start page, Desktop icons etc.

Any good solutions out there? 

Thanks in advance.
Knut, Norway.

---

### Post by rickyjones on 2007-08-21
Edit the group policy object on the local machine.

Computer Configuration > Administrative Templates > System > User Profiles

"Delete cached copies of roaming profiles" - Configure this to yes.

This should accomplish the task.

-Richard

---

### Post by craigp84 on 2007-08-21
Use mandatory profiles? (Rename profile.dat to profile.man IIRC).

-c

---

