---
title: "Apache2 virtual servers"
date: 2005-10-31
forum: Server Platforms
---

### Post by godlike on 2005-10-31
Ok i tried irc and google and i cant seem to find help on this topic so im not sure its possible.
Basically i just want to know if theres a line u can add to one of the sites-available scripts for the virtual hosts so that instead of www-dat the owner of the files would be a user?
Basically when the site adds new content threw php or what not it always creates it with the www-dat and then i cant edit the files with my user account always have to switch to www-dat......

---

### Post by Glut on 2005-11-01
A simpler solution would be to have the user of the file as your own user and the group of the file set to www-data
Then, if www-data has read access, everything is hunky-dory.

---

### Post by godlike on 2005-11-02
Well ya i was thinking that also but the problem is the site is using e107 and whenever it adds any new files its sets www-data:www-data

---

### Post by Glut on 2005-11-02
Make your user part of the www-data group and the files editable by group, it's slightly messy, but you wont have any issues.

---

### Post by godlike on 2005-11-02
thanks, ya thats what i have been doing just annoying cuz the site always adds new content 770 or whatever user only can write lol so i gotta manually 775 em to do any editing lol
O well i guess thats how it goes

---

