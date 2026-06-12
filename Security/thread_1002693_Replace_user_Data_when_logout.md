---
title: "Replace user Data when logout"
date: 2008-12-05
forum: Security
---

### Post by godor on 2008-12-05
Hi,
On a public surf station i wanted to allow a guest user using a session and after an (automatical) logout all his userdata to replace and have a fresh clean session for the next user.
I did this by modifying /etc/gdm/PostSession/Default.
I simply added something like:
rm -rf /home/guest
cp -af /home/backup /home/guest

By the way I am using Ubuntu 8.10.
I thought all left over guest user data will deleted and everything (including icon position etc) will be restored.
If I do this manually everything worked like I expected.
But in the Logout Script, it seams that some files are not deletable. (maybe still in use) and I run into strange things, and often the computer is using a new default home directory for guest.

So how can i realize this working?
Is there maybe a better location for my script?
Or a better way of doing this? Guests home in an temporal dataspace?
Thanks for the help
Guido

---

### Post by tubbygweilo on 2008-12-05
Can you use the guest session option available  8.10?
> Guest session

The User Switcher panel applet (package fast-user-switch-applet) now provides an extra entry for starting a Guest session (by Martin Pitt). This creates a temporary password-less user account with restricted privileges: the account cannot access any users' home directories, nor permanently store data. This is sufficiently safe to lend your laptop to someone else for a quick email check. 

---

### Post by godor on 2008-12-07
I would love to use the Guest session, but I think it is not acessible from GDM Login? On the Machines the Users have to login themselves.
Or is there a way to use it?

Greetings Guido

---

