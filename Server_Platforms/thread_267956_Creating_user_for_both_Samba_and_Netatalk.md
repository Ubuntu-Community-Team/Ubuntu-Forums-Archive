---
title: "Creating user for both Samba and Netatalk"
date: 2006-09-29
forum: Server Platforms
---

### Post by fgrieu on 2006-09-29
Hello,

I just set up a fresh 6.06.1 Unbuntu file server with both Samba and Netatalk (as precompiled). I can access my home directory under my user name (the default account used during setup) from all the remote clients needed (native Windows 2k/XP, MacOS 9.2.2 using Appleshare over IP, OS X, hopefully soon Ubuntu). Actually I did this several times, but allways mess up the next phases, where I need to

- create additional users for both Samba and Netatalk, if at all possible in a single operation, sharing a common password in both environments (if possible, password changeable remotely by the users from any client environment).

- have these users remotely access a common shared directory; a home folder for each user in the common shared folder would be nice.

- setup things such that, by default, a new folder remotely created (somewhere in the common shared folder) by one user is accesible by all the others without explicitly setting access rights.

- still make it possible for users to remotely make a folder accessible only to self, or maybe a group.

Since I am in an exploratory phase (replacing an aging Win2k server doing this job mostly satisfactorly), I am 100% free to setup things afresh with whatever optional services / volume partitioning / formatting / options suggested. TIA for any clues.

  François Grieu

---

