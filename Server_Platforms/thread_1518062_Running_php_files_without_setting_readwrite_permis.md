---
title: "Running php files without setting read/write permission?"
date: 2010-06-26
forum: Server Platforms
---

### Post by JackTheRyder on 2010-06-26
On an Apache2 server someone else setup, I have a folder with drwx--x--x permission and the php file can still write in the folder.  But on my own setup, I need to set the same folder to drwx--x-wx.

Inside the folder, I have a index.php that runs just by setting rwx--x--x but on my own setup, I need to allow read permission for others/group before it can run: rwxr-xr-x (or else I get a blank page).

I tried changing the folder and files to root but it's the same.

How can I make my php files work the same way?

---

### Post by Ryan Dwyer on 2010-06-26
Keep your files owned by root, but change the group to www-data and give write permission to group.

The server someone else set up might be doing something dangerous like running Apache as root, or it could have all the /var/www files owned by www-data.

---

### Post by JackTheRyder on 2010-06-26
That kinda works, php files run with rwxr-----.  It works if I give group +r but doesn't if I remove it.  Removing execute permission doesn't affect it.  Shouldn't that be the other way around?

---

### Post by Ryan Dwyer on 2010-06-26
No. The read bit allows them to read it. The execute bit allows them to execute it. Why should it be the other way around?

---

### Post by dapperdanny77 on 2010-06-26
the execute flag set for a directory enables you to access files inside a directory - so if you know the filename inside a dir you can access it without having read permissions for that dir. you don't need the execute flag set for your .php files when served by apache. it's only mandatory that apache can read the files.

---

### Post by JackTheRyder on 2010-06-27
I thought the execute let's them execute the php file and read let's them read the file like view the code in a text editor?

The same for directories, I thought the read flag let others enter the folder and read what's inside and the execute flag lets other execute files inside the folder but not let them enter it.

---

