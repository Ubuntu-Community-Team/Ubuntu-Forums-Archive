---
title: "making a secure directory exclusive to a specified account"
date: 2008-02-17
forum: Security Discussions
---

### Post by MustNotSleep on 2008-02-17
this is a fairly begginer-type security question..

basically, i created a new user (private) and i want to be able to run commands such as `sudo -u private mkdir blah` anywhere on the system (most importantly, under my normal user account's home directory).. right now, though, the above command returns: "mkdir: cannot create directory `private3': Permission denied".

i've added 'private' to the sudoers file using visudo, with the following line: 'private ALL=(ALL) ALL'.

i have restarted multiple times with no change. the command `groups private` returns "private : admin adm cdrom audio plugdev fuse".

the basic idea is that i want to create a directory using the private account, give it exclusive ownership (chmod 600), so that i can have a secure directory for any private data i might need to keep. this is to make sure not even root or sudo through my user account can access those files. also, it would be nice to be able to use the current X session for doing stuff like `sudo -u private mplayer test.mp4`, without sudo giving an error. i tried the sux command with no luck.

how can i accomplish this? additionally, is there a different method for this case? i was thinking the most smart and convenient way would be to use Unix permissions, but maybe i'm mistaken.

any help is appreciated. thanks!

---

### Post by ruy_lopez on 2008-02-18
Try adding 'private' to your normal group. The parent folder will need group write privileges.

Adding 'private' to sudoers only means that 'private' can call sudo. It doesn't make 'private' into root. If 'private' doesn't have permissions to write in the directory, in which you are creating a private subfolder, 'sudo -u private mkdir blah' will fail.

Also, login to 'private' and create a 'umask 077' entry in it's '.bash_profile' or '.bashrc', so any folder or file 'private' creates will have the right permissions.

umask 077 will create files as 'chmod 600' and folders as 'chmod 700' (you need 700 to 'cd' into folders).

---

