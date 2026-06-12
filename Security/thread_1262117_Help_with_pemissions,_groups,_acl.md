---
title: "Help with pemissions, groups, acl"
date: 2009-09-09
forum: Security
---

### Post by Ralph L on 2009-09-09
I posted the following in the Absolute Beginner Forum (since I am a beginner), but thought I should post it here also.  Hope this is ok.


I am trying to set up a multi user system. I would like each user to be able to control who can see, use, and replace files and folders. I first attempted to use the classical Linux/Unix permissions of user/owner, group, and others. This works ok with 2 exceptions:
A. To permit a file to one other person it is necessary to set up a group with only that person's user name in it. This is ok except that the group must be set up by the Administrator. This is a big nuisance for such a common action and slows down user progress. Is there any way to allow each user (non admin) to create their own local groups?

B. To allow sharing-users to see a single file/folder in a folder it is necessary to make the entire folder viewable to the sharing user. This is undesirable in that it lets users sharing a file see what else the file owner is doing. One possible solution is for the user to limit the contents of the Home folder to contain just 2 folder (Unshared Documents, and Shared Documents. Then the sharing user can only see these two folders, but this forces all unshared files one level further down in the hierarchy--a big nuisance. Is there any way to limit the sharing users visibility to just the shared folders/files and not to the entire contents of the folder?

I also tried to use the ACL feature, and while this makes it easier to permit a file to a single user, groups must still be created by the administrator, and sharing users have still visibility to files they don't need to know about. In addition, when I copy a file, even if I use cp under Terminal, the ACL permissions are lost. Is there any way to copy a file with ACL permissions and have them retained in the new file?

Thanks for any help

Ralph

---

### Post by Ralph L on 2009-09-13
See the replies to this same item in Absolute Beginner.  It has the same thread title.

Ralph

---

