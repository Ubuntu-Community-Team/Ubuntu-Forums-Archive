---
title: "Samba: spurious files, changing permissions in folder"
date: 2018-02-11
forum: Server Platforms
---

### Post by XBMC old School on 2018-02-11
Hey all, I have a headless server set up & running (16.04). I have smb running, with several different shares & users privileges.  But i can't get one folder to work. Every time i create it it comes full of driver folders, and I can't get the permissions to work. I have;  1. deleted, and recreated the directory  2. renamed (mv), and created new directory  3. changed the case of the directory (first letter)  4. used a different directory label all together.   None of this works soooo, there is a gap in my knowledge and google has not returned anything of value.  Can anyone help, or provide insight or direction?

---

### Post by XBMC old School on 2018-02-11
This is Virtually not Virtualization

---

### Post by wildmanne39 on 2018-02-11
*Thread moved to **Server Platforms, a more appropriate forum**.*

Apologies!

---

### Post by XBMC old School on 2018-02-13
bump

---

### Post by LHammonds on 2018-02-13
> **XBMC old School said:**
> Hey all, I have a headless server set up & running (16.04).
Congratulations and welcome to the club!  I'm an old XBOX fan too.  I also made an XBMC machine and used it to play back my 1st-born's pictures/movies to our visitors while we were still in the hospital. ;)

> **XBMC old School said:**
> I have smb running, with several different shares & users privileges.
Are we talking local users, Samba DC users, Microsoft AD users?

> **XBMC old School said:**
> But i can't get one folder to work. Every time i create it it comes full of driver folders, and I can't get the permissions to work.
Are you saying that "driver" files magically appear when you create a folder?  What is the path you are talking about?  Is it somewhere under /srv?

> **XBMC old School said:**
> I have;  1. deleted, and recreated the directory  2. renamed (mv), and created new directory  3. changed the case of the directory (first letter)  4. used a different directory label all together.
Your primary tools are: "chown" to set user and group ownership, "chmod" to set file/folder permissions for the user, the group and everyone else not the user or group.

Here is a nice overview of [Linux permissions]("https://www.digitalocean.com/community/tutorials/an-introduction-to-linux-permissions").

LHammonds

---

### Post by XBMC old School on 2018-02-13
> Congratulations and welcome to the club!  I'm an old XBOX fan too.  I  also made an XBMC machine and used it to play back my 1st-born's  pictures/movies to our visitors while we were still in the hospital.
Been rockin it since xbox1
> local users, Samba DC users, Microsoft AD users?
Network users, that have users accounts on the server as well. linux and windoes
> Are you saying that "driver" files magically appear when you create a  folder?  What is the path you are talking about?  Is it somewhere under  /srv?
Yes magical. The shared folders are on Btrfs raids, mounted "on the system" so .... /apples/banana/stuffthatworks & apples/bananas/stuffthatdoesn'twork
> Your primary tools are: "chown" to set user and group ownership, "chmod"  to set file/folder permissions for the user, the group and everyone  else not the user or group.
Everytime i have moved, made, and/or remade a directory, i have chmod to 777.
> Here is a nice overview of Linux permissions.
Thanks for the link, I pretty sure that i read it before, with no avail

Thanks @lhammonds

Maybe it is chown???  Thoughts?

---

