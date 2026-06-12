---
title: "[SOLVED] SSH permissions"
date: 2007-07-24
forum: Server Platforms
---

### Post by DanielSwe on 2007-07-24
I let my friends send me files via ssh (scp) and I always end up having to use my root account to access the files that they send me if I want to remove their files.
Is there a solution so that I always get permissions to do whatever I please with the files that they send via scp?

---

### Post by meatpan on 2007-07-24
The current situation sounds normal.  A user is copying files to their own user space, and you, as another user, want to remove them.  As a regular user you are not allowed to remove other users files (by default).

There are a few things you can do to circumvent the default behavior:

o Use sudo, which is your current workaround
o Create a common 'group' to which you and the external users belong.  You can configure the permissions of  files created by members of this group to be executable by everyone in the group, which will allow you to delete the files.  Here is a handy tutorial about creating and adding new groups: [http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html)
o Change the umask of the external users (I mean external in the context of your example.  They are all essentially 'internal' when they are operating via scp) so files are 'other' group removable by default.  As root, recursively chmod their home directory to match the new, less restrictive, permission settings.

---

### Post by DanielSwe on 2007-07-25
Thanks! 
I set the umask to 007 in /etc/profile and the home dirs using chmod -R g+s. Works like a charm! :)

---

### Post by warpforge on 2007-10-18
This solution isn't working for me. I'm using MacFUSE-based clients.

---

