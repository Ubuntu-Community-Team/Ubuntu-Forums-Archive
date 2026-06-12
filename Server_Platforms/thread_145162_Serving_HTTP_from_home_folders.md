---
title: "Serving HTTP from home folders"
date: 2006-03-15
forum: Server Platforms
---

### Post by spectre_25gt on 2006-03-15
Ok, I'm trying to set things up so that if I go to $website.$username.server.com it will serve files from /home/$username/dev/www/$website/. Unfortunately, I can't figure out how to set up the permissions so that Apache can read the files.

Any ideas?

---

### Post by Glut on 2006-03-15
chown the files to the group www (or www-data or whatever apache is using) and chmod all the files group readable.

*edit: sorted my chown'ing and chmod'ing - it's so confusing :-)*

---

### Post by spectre_25gt on 2006-03-16
I've tried setting permissions that way but apache still can't get to it because the permissions higher up in the hierarchy don't allow it. I really don't want to change that, either.

Also, what can I do to ensure that files created or moved into that folder keep www-data as the group and the correct permissions are inherited? Should I make my users that deal with those files part of the www-data group?

---

### Post by spectre_25gt on 2006-03-18
Just one bump and I'll let it die. This is just kinda holding me up a bit.

Edit:

Ok, I've got it working. I ended up just being a little bit more lenient with the permissions on my home folder and tightening up the subdirectories instead.

---

### Post by ice.man on 2006-03-19
***@lanstats:~$ sudo adduser *** www-data
Password:
The user `***' is already a member of `www-data'.
***@***stats:~$ sudo chown -R www-data:www-data /var/www
***@***stats:~$ sudo chmod -R 664 /var/www
***@***stats:~$


And it still says i don't have permissioms!! 


anyone got any idears?

---

### Post by LordHunter317 on 2006-03-19
[QUOTE=Glut]chown the files to the group www (or www-data or whatever apache is using) and chmod all the files group readable.

*edit: sorted my chown'ing and chmod'ing - it's so confusing :-)*[/QUOTE]No.  Files should be owned by whoever will be editing them.  Apache should get access through world permissions.

---

### Post by claes on 2006-03-20
Check that others have execute permissions on all the folders down to the folder apache will use to publish from. And that folder others need both read and execute permissions.

Claes

---

