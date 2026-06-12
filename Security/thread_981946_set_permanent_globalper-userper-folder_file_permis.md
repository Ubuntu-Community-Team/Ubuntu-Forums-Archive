---
title: "set permanent global/per-user/per-folder file permissions"
date: 2008-11-14
forum: Security
---

### Post by pavallokazzo on 2008-11-14
Hello folks!
I'm using Ubuntu Server for a little file server (SMB) in the office.
We have a folder per-user(homes), a public folder (guest access) and a folder where every authorized user can write and read but guest access is denied.
No problem in the pub or the private (homes) folder.

The problem starts in the members shared foder...
What I would like to have is a folder where every body can write and read in EVERY subfolder, while keeping track of who is the owner of a file.
So I have made an account members:members, and created every user with gid members.
(I know this can breaks security in user's home folder, but the server is small and firewalled and by now I'm trying to focus to get things working.)
In the smb.conf there isn't a share that points to this folder, cause this folder is accessed by user through a symlink in their home folder  ---> /home/members. 
The only shares listed in smb.conf are [homes] and [pub].

Now a user can get in /home/members loggin in their /home/$USER folder and opening the members symlink, then create a file or a directory, but the file created will have permission rw-r--r-- while I want to set permission to ug+rwx automatically.
Same thing for home folder, they will write file with default permission (rw-r--r--) but I want this file only available to user (u+rwx).

How can I modify this? Where can I modify the default setting for file/dir permission?
Also, the sticky bit, I never really used it. Should I set all files in /home with sticky bit?

Thanks

---

### Post by pavallokazzo on 2008-11-14
Found out create mode and directory mode options for the smb.conf, this can resolve it but things aren't working.
If I set in service section:
	create mask = 0770
	directory mask = 0770

or
	force create mode = 0770
	force directory mode = 0770

it will still create file/folder with 022 (rw-r--r--)

Any help?

---

