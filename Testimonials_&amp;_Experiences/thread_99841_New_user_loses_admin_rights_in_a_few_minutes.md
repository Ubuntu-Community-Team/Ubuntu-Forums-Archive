---
title: "New user loses admin rights in a few minutes"
date: 2005-12-06
forum: Testimonials &amp; Experiences
---

### Post by Sisyphe on 2005-12-06
Hi everyone.

I've been using Linux for 4 years now (Mandrake then Debian).
My main machine is Debian Sarge but I've just installed Ubuntu Breezy on a free partition and on my wife's laptop.

I must say I'm impressed at how easy the installation was.
Hardware was recognised, everythings seems to be working fine.
Ubuntu is certainly one of the most user-friendly distro I've ever tried.

I would like to report a problem though.

I wanted to delete the first user created during install and replace it wit another (although you may find it strange, it was all about chosing the uid of the admin user).

I had read the doc so I knew that on Ubuntu, the root account is deactivated and that the first user  receives full administrative power through sudo so I was carefull.

After install, I logged in gnome as user1 (the one created during install) and used users-admin (I think) from the gnome menu to create user2 and gave him admin privileges.

I disconnected and relogged as user2.
Tried sudo : it worked.
I used users-admin once more to delete user1. 
The single fact that I succeeded proves that user2 had root privileges.
I logged off.

The next time I logged in as user2, I had lost root privileges : user2 was not allowed to use sudo anymore. Nobody was !

I had to reboot in recovery mode.
I suppose I could just have put user2 in the admin group from the recovery mode command line but I didn't think about that so I used another method (reactivating the root password then deactivating it again later).

I agree that what I did is somehow unusual and that, in a way, I was looking for trouble but I still think there is a bug somewhere (in users-admin?) because user2 should never have been removed from the admin group.

Just to be sure, I reproduced the same problem on my wife's laptop.

Well I don't know what to think : is it a bug, is it known, should it be reported and to whom ?

Great distro anyway.

---

