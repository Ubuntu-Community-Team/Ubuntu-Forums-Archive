---
title: "windowsserver 2003 and samba"
date: 2010-02-24
forum: Server Platforms
---

### Post by shootme on 2010-02-24
Hello,
 
I am using ubuntu with samba.
I have a windows 2003 server and i want to log in from the w2003 to the samba server.
 
But when i do this (i have samba set up and made the shares) i get a pop up asking for my username and password.
 
when i fill in administrator (i am logged in at the w2003 with administrator) the username changes to samba/administrator, but i cannot log in.
 
Please help me, i am having this problem for over 2 weeks and i cant find a solution.
 
Thank you very much in advance!

---

### Post by mcarrara on 2010-02-24
Have you checked out the Samba web site?  They have extensive documentation.  For this issue I would guess that the user administrator is not a user on the Samba server.  How are your Windows clients authentcating for the Win2003 server?  Is it AD?  I do not know how well Samab can participate in an AD style system.  I am still using NT style logins and winbind to sync the passwords between Windows and Samba

Mark

---

### Post by joberly on 2010-02-24
mcarrara is correct in stating that you are trying to login to the Samba server using 'administrator' as a username, which is obviously not an existing user on the Linux machine.

If you are just setting up simple shares w/ the Samba box, make sure your share permissions are set properly and either use guest access, or set your perms with valid Samba users.

Integration with AD is more in-depth and if you are just wanting to share data between the two boxes or network, it's best to keep it simple!

---

