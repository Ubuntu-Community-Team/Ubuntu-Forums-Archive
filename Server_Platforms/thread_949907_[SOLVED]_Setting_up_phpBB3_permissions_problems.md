---
title: "[SOLVED] Setting up phpBB3 permissions problems?"
date: 2008-10-16
forum: Server Platforms
---

### Post by Gannon8 on 2008-10-16
I grabbed phpBB3 from the site, and I am trying to install it. I get the following errors:
>  Files and Directories

Required - In order to function correctly phpBB needs to be able to access or write to certain files or directories. If you see “Not Found” you need to create the relevant file or directory. If you see “Unwritable” you need to change the permissions on the file or directory to allow phpBB to write to it.

cache/:
    Found, Unwritable

files/:
    Found, Unwritable

store/:
    Found, Unwritable

Optional files and directories

Optional - These files, directories or permission settings are not required. The installation system will attempt to use various techniques to create them if they do not exist or cannot be written to. However, the presence of these will speed installation.

config.php:
    Found, Unwritable

images/avatars/upload/:
    Found, Unwritable

 Could someone help me on how to find and change the permissions for these directories?

---

### Post by Gannon8 on 2008-10-16
Nevermind, the files are in the phpBB3 directory, and not the /var/ directory.

---

