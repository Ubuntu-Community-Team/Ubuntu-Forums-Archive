---
title: "Home directory permissions"
date: 2007-07-09
forum: The Cafe
---

### Post by samschoice on 2007-07-09
What are the default permissions on the home directory ?

I had a proggie change them. Please write the answer in text. i don't understand things like 755..

---

### Post by Polygon on 2007-07-09
everything in your home folder should belong to you...

you should be the owner and can create/delete files

and the home folder should belong to the group that is the same as your username, and thats set as "---" for file access for me.

---

### Post by init1 on 2007-07-09
There needs to a certain permission on the directory itself, and a separate permission for a certain file inside. Not sure the details, but I had some issues with that. As for 755, its a way of  representing the system with numbers. 
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html]("http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html")

---

### Post by saulgoode on 2007-07-09
I would recommend 'rwxr-xr-x' for both files and directories -- this provides everyone the right to search your subdirectories and view your files but they can't change them. If you do not wish others to view your files then you should use 'rwxr-x---'.

---

### Post by samschoice on 2007-07-09
thanks guys. hopefully I'll be able to help you one day.

---

