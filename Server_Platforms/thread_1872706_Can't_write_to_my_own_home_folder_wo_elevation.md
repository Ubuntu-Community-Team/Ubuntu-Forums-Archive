---
title: "Can't write to my own home folder w/o elevation"
date: 2011-10-31
forum: Server Platforms
---

### Post by FiftyOneFifty on 2011-10-31
This is my first time configuring server Linux (10.04).  So far, I have created only one user login for administration.  I've noticed I can't write to my own home folder without elevating to root status.  This means that almost any process I launch needs to be run with sudo, even creating a text file.

I can see that the user and group for my /home/username folder are both "root", I'm assuming there is a reason.   I'm pretty sure adding my login name to the "root" group would have unintended security consequences, such as being able to edit configuration files without elevation.  Can I change the owner or the group on my home folder without making those files inaccessible to system processes that expect to access them (since under Ubuntu, my user login is a surrogate root account).  I.E., is there a reason editing the content of my own root folder should require elevation?

---

### Post by danbuter on 2011-10-31
Try right-clicking and going into properties. There should be an option for security that you can change.

---

### Post by knight187 on 2011-10-31
your problem is interesting, your home dir should be owned by you. to change it just run the command 

sudo chown username.usergroup /home/username -R
sudo chmod 700 /home/username -R.

doing this will fix the home dir permissions but may cause issues if some custom apps or services have been setup to access files in youe home dir. I would be fixing the home dir permission then fixing the apps and services that may fail due to the updated home dir permission.

Good luck, cheers

---

