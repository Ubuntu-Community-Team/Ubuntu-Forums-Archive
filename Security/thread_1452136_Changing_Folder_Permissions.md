---
title: "Changing Folder Permissions"
date: 2010-04-11
forum: Security
---

### Post by uRock on 2010-04-11
I am having an issue with folder permissions. When I right-click on my Music folder and click properties, then permissions. It shows --- in the File Access permissions for owner. I recently copied all of the files from it onto another machine and most of the subfolders would not copy do to lack of permission. When I try to change the --- to read and write, then click "Apply Permissions to Enclosed File" the access returns to ---. I have also tried doing this to the individual file folders that have refused to copied and the access field does the same thing of returning to --- instead of changing the permissions. I have also tried the same things while running gksu nautilus and that didn't work. What do i need to do in order to make these files sharable to my other system?

Thanx,
Ronnie

---

### Post by new_tolinux on 2010-04-11
Go to the folder in terminal and execute
```
chmod -R 770 *
```That way you set read/write/execute for the user, read/write/execute for the group and none for "the rest of the world".

Edit:
If that doesn't work try using it with sudo.

---

### Post by uRock on 2010-04-11
> **new_tolinux said:**
> Go to the folder in terminal and execute
```
chmod -R 770 *
```That way you set read/write/execute for the user, read/write/execute for the group and none for "the rest of the world".

Edit:
If that doesn't work try using it with sudo.

I think I need a different chmod #, the command ran perfectly, but I can't access the folders from the network at all now. 

Thanx,
Ronnie

---

### Post by new_tolinux on 2010-04-11
Maybe you can do
```
chmod -R o+r *
```
in the same folder. It will grant read-access to "everyone".

Maybe you'll even have to change ownership:
```
chown -R youruser:yourgroup *
```
But I'll think the first command will do. And again: if it doesn't work, try sudo.

---

### Post by uRock on 2010-04-13
Still isn't working.:confused:

---

