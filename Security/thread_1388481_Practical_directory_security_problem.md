---
title: "Practical directory security problem"
date: 2010-01-23
forum: Security
---

### Post by warci on 2010-01-23
Hello everyone.

I've got the following problem: I have a directory structure shared with samba which should be writable from a certain directory. You've got a tree like this:

dir1>dir2>dir3

where dir3 is a subdir of dir2 and so on. I have one group logging in through samba and i need the permission so:

-the group can't write or modify dir1 or dir2
-the group can modify dir3 and can write inside dir2 (but can't modify dir2 itsself!)

Is there an elegant solution to this problem? I've been checking out ACL's, but i'm no expert. How do i go about this?

thanks!

---

### Post by Ryan Dwyer on 2010-01-24
I don't understand what you mean with dir2. Give some examples of what the user should and shouldn't be able to do, such as making new folders and editing files inside dir2.

I think this is what you want: Add those users to a group (eg. sambausers). Set dir1, dir2 and dir3 so the group owner is sambausers. Leave the user owner as root.

dir1 - chmod 755 - (root = all, sambausers = read only, others = read only)
dir2 - chmod 755 - (root = all, sambausers = read only, others = read only)
dir3 - chmod 775 - (root = all, sambausers = all, others = read only)

---

