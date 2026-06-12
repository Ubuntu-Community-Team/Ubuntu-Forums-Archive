---
title: "Samba Folder Rights Help"
date: 2018-02-07
forum: Server Platforms
---

### Post by rduhb on 2018-02-07
I want users to only have read capability of my folders.  Setting "chmod 755" achieves that, but it also prevents me from editing or adding files to the folder.  How do I keep full access, but limit others?

---

### Post by darkod on 2018-02-08
First of all, don't use 'chmod 755' unless these are new folders being set up for the first time. Because the 5 means read+execute and if you run that on existing folders and files with -R, it will make all files executable. Which you don't want...

Second, what is the group ownership of the folder(s)? Are other users also members of that group?

Third, are you the owner of the folder? I assume not otherwise the 7 would allow you write in any case...

To give the user (owner) write access to a folder and subfolders/files, use 'chmod u+w'.
To give the group owner the same use 'chmod g+w'.
To prevent write by any other users use 'chmod o-w'.

But of course, think about which user and group ownership you want on the folders, and plan your permissions...

---

### Post by rduhb on 2018-02-08
> **darkod said:**
> First of all, don't use 'chmod 755' unless these are new folders being set up for the first time. Because the 5 means read+execute and if you run that on existing folders and files with -R, it will make all files executable. Which you don't want...

Second, what is the group ownership of the folder(s)? Are other users also members of that group?

Third, are you the owner of the folder? I assume not otherwise the 7 would allow you write in any case...

To give the user (owner) write access to a folder and subfolders/files, use 'chmod u+w'.
To give the group owner the same use 'chmod g+w'.
To prevent write by any other users use 'chmod o-w'.

But of course, think about which user and group ownership you want on the folders, and plan your permissions...


What I discovered shortly after my post was that I was not the owner of the folder.  I fixed that with with 'chown'.  Now I can read/write, while my test user only has read access.  These were new folders I setup so I'm curious why the ownership defaulted to 'root' instead of the user name of the person that created the directory.  I'm new to Linux so THANKS FOR YOUR HELP.

---

### Post by volkswagner on 2018-02-08
If you will be adding files and folders to this
directory, you'll want to set the default behavior for newly created files.

I've found [this document]("http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm") invaluable for setting file permissions for SAMBA.

---

