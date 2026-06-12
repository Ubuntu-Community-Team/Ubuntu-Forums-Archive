---
title: "[VSFTP]  directory  access"
date: 2007-11-06
forum: Server Platforms
---

### Post by romaing on 2007-11-06
Hi guys,

I've set up a ftp server with vsftp, and I'd like to "customize" users directory access.
Let me explain with an exemple:

when users log in, I'd like them to see 2 directories:

[INDENT]- /home/$user (their own home directory)
- /home/share/movies[/INDENT]

and I don't want them to be able to browse any other directory.

Now I know how to lock a user to it's home directory with:
[INDENT]
chroot_local_user=YES[/INDENT]

I know how to set their home directory to another directory with:
[INDENT]
local_root=/home/share[/INDENT]


But i do not know how to sort of combine the two... I could create a directory with links in it but 1) that's kinda dirty, 2) i'd need to do that for each user...



Any idea ?

Thanks in advance.
R.G.

---

