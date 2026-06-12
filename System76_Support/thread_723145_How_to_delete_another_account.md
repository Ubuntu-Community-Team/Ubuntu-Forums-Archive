---
title: "How to delete another account"
date: 2008-03-13
forum: System76 Support
---

### Post by Acunga on 2008-03-13
*** I cant delete my second account and I hope I didn't mess up again
I have created a test account with limited rights.Anyway, when I go to user settings and i right click on the said account >delete I get this message:
"This will disable this user's access to the system without deleting the user's home directory." 
delete...nothing, it is there.
I hae deleted the /home/acungas dir with the terminal command sudo -r/home/acungas but it is still in the user settings list.
Is there a reason this account is still working or something.I mean 10 minutes ago I understood when you log out the programs in previous account sill work(and you can hear them working:))
:confused:

---

### Post by Acunga on 2008-03-13
*** I cant delete my second account and I hope I didn't mess up again
I have created a test account with limited rights.Anyway, when I go to user settings and i right click on the said account >delete I get this message:
"This will disable this user's access to the system without deleting the user's home directory." 
delete...nothing, it is there.
I hae deleted the /home/acungas dir with the terminal command sudo -r/home/acungas but it is still in the user settings list.
Is there a reason this account is still working or something.I mean 10 minutes ago I understood when you log out the programs in previous account sill work(and you can hear them working:))
:confused:

---

### Post by NorthernLights on 2008-03-13
I don't know if it's GUI's fault, but the text command to remove a user is "userdel" (to be run as root).

Check the man page : [http://linux.die.net/man/8/userdel](http://linux.die.net/man/8/userdel) (or "man userdel").

---

### Post by thomasaaron on 2008-03-13
sudo deluser <username>
sudo rm -r /home/<username>

That should get rid of the user and the unwanted directory.

---

### Post by thomasaaron on 2008-03-13
Duplicate posting...
[http://ubuntuforums.org/showthread.php?t=723152](http://ubuntuforums.org/showthread.php?t=723152)

---

