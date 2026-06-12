---
title: "I want to choose the synched folder location"
date: 2009-07-07
forum: Ubuntu One (CLOSED)
---

### Post by Wise Ferret on 2009-07-07
I do not like the fact that ubuntu one sticks a root-owned folder inside my home folder. This is not a polite behavior. 

1. Is there any way to configure ubuntu one to use a custom synched folder location? 

2. Why can't it set this folder with my user's permission? Everything in my home folder should belong strictly to me.

---

### Post by chipaca on 2009-07-07
There isn't currently a way to configure the location.
However, note the folder is not owned by root, unless for some reason the syncdaemon has been started as root (it shouldn't; it runs as the normal user).

---

### Post by Wise Ferret on 2009-07-07
> **chipaca said:**
> There isn't currently a way to configure the location.
However, note the folder is not owned by root, unless for some reason the syncdaemon has been started as root (it shouldn't; it runs as the normal user).
This is probably a bug then. After installing my gnome client, the folder was set with root permissions. I'll try deleting it and restarting...

EDIT: OK, this is a bug. After rebooting, deleting the folder and logging in, the folder was re-created as locked. Looking at its permissions it seems that I am the owner, but I have only access permissions and cannot delete or move it. The simple workaround for me is to change the permissions manually (no root/sudo is needed as I am the owner).

---

### Post by chipaca on 2009-07-07
Is there any chance you started the client (either the applet or the syncdaemon itself) manually after doing the install, and that you either did it as root or using sudo?

---

### Post by chipaca on 2009-07-07
As to question #1, you might find [question 76321]("https://answers.edge.launchpad.net/ubuntuone-client/+question/76321") relevant

---

### Post by Wise Ferret on 2009-07-07
I have not started the client manually.

By the way, the permission bug hits again. My gdm crashed, and after logging back in, the permissions were messed up again and the folder is locked.

---

### Post by Wise Ferret on 2009-07-07
> **chipaca said:**
> As to question #1, you might find [question 76321]("https://answers.edge.launchpad.net/ubuntuone-client/+question/76321") relevant
Thank you, it is a sort of a workaround. But I do not wish my home folder to contain any non-hidden folders or symlinks I did not put there myself. Treating my home folder as the public property of all apps is a windows behavior.

---

### Post by RealG187 on 2009-07-09
I think you are not supposed to write anything right under the "Ubuntu One" folder, bur rather the "My Files" folder within it.

Thanks to Symbolic links one can have any folder be any other folder so it doesn't matter. I am doing that for my Knotes:

[http://ubuntuforums.org/showthread.php?t=1208239](http://ubuntuforums.org/showthread.php?t=1208239)

---

### Post by jpeddicord on 2009-07-11
> **RealG187 said:**
> I think you are not supposed to write anything right under the "Ubuntu One" folder, bur rather the "My Files" folder within it.

Thanks to Symbolic links one can have any folder be any other folder so it doesn't matter. I am doing that for my Knotes:

[http://ubuntuforums.org/showthread.php?t=1208239](http://ubuntuforums.org/showthread.php?t=1208239)

Nailed it. The Ubuntu One folder is *not* owned by root, it is just marked as read-only.

---

### Post by RealG187 on 2009-07-13
What happens if you put files in there? Will Ubuntu One upload them?

---

### Post by jpeddicord on 2009-07-13
> **RealG187 said:**
> What happens if you put files in there? Will Ubuntu One upload them?

Nope, nothing happens. They either need to be in My Files or one of the Shared With Me folders. Having the folder set as read-only just reduces confusion so that files are not placed in there and expected to sync.

---

### Post by RealG187 on 2009-07-13
> **jacobmp92 said:**
> Nope, nothing happens. They either need to be in My Files or one of the Shared With Me folders. Having the folder set as read-only just reduces confusion so that files are not placed in there and expected to sync.That's what I thought, they have to be under one of those folders, so it only writes to those folders only...

---

