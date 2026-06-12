---
title: "Making apache2 folder writable?"
date: 2005-09-30
forum: Server Platforms
---

### Post by hansoffate on 2005-09-30
Since the apache 2 folder  /var/www/   is all sudo protected, i cannot install php-nuke or mambo.  Well, its rather hard.  Is there any easy way to make this are none superusered so i can do everything without typing sudo and junk?

---

### Post by adwait on 2005-09-30
You could simple change its permissions using chmod........

---

### Post by hansoffate on 2005-10-01
Could you please explain to me ... how?

---

### Post by herrpoon on 2005-10-01
this is a nice guide, includes a guide to chmod stuff too :D 

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

### Post by LordHunter317 on 2005-10-01
The far better solution is to just have /var/www owned by your own user, which can be changed using chown.  Just remember that the apache user (www-data) needs read access to all files/directories in order to function.

---

### Post by hansoffate on 2005-10-02
I don't quite understand what am i supposed to do.  Could somone help me in nooby terms?  Thank you

---

### Post by Glut on 2005-10-04
From memory the www-data user has a www-data group to go with it. load up a terminal, type in the following. You will need to provide your password to do the chmod. I strongly suggest reading the above link to understand what you're doing with chmod, or simply read the chmod manual page by typing into the terminal: man chmod

*username* is your username. I think *www-data* is right, but someone might like to correct me . An alternative is to use your username as your group, try this if you have any issues. It will have the same broad effect.

cd /var
sudo chmod -R  0644 *username*:*www-data* ./www

---

### Post by az on 2005-10-04
Can't you just add your user to the www-data group using the users administration tool?

---

### Post by LordHunter317 on 2005-10-04
No, that's genearlly undesirable.  Apache should have a user and group all to themselves.  Far better is to give the user/group that will edit files in the webroot ownership over them, and then make sure Apache has access, either via world permissions or ACLs.  This is the model that makes the most sense, as it most closely follows the real world.

---

