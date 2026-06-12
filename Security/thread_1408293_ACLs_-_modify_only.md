---
title: "ACLs - modify only ?"
date: 2010-02-16
forum: Security
---

### Post by MrEgg on 2010-02-16
Hi all,

I'm trying to fine tune user permissions with my data files. In addition to UGO, I have enabled acl in fstab, but I may be missing something as I cannot yet achieve what I want.

_What I'm trying to do_ :
In a folder /Data, I would like to allow all group members to create, read and modify files. At the same time, I would like to allow *only* user1 and user2 to delete files.

_So far_ : I've tried setting the sticky bit to /Data - this does indeed restrict delete perms to the file owner (say user1). I've tried using acl to add user2 with rwx perms both on /Data and a test file within - but no success.

Can somebody help me out?

Thanks,
Egg

---

### Post by MrEgg on 2010-02-16
Update :

I am now able to allow only 2 users to delete files from a folder :[LIST]
[*]sticky bit set for the folder
[*]user1 : owner of the folder
[*]user2 : owner of the files within in the folder
[/LIST]

It says in [linux.org]("http://www.linux.org/docs/ldp/howto/Security-HOWTO/file-security.html") that :
> If the sticky bit is set on a directory, then a user may only delete files that the he owns or for which he has explicit write permission granted, even when he has write access to the directory.

What if I now want to give user3 the same delete privileges as those of user1 and user2 ?

How do you explicitly grant write permissions to a user, other than making her the directory owner or the file owner ?

Thanks,
Egg

---

### Post by bodhi.zazen on 2010-02-16
Try these links :

[http://ubuntuforums.org/showthread.php?t=145741](http://ubuntuforums.org/showthread.php?t=145741)

        This link is a nice discussion, see pot #9 for ACL.

    GUI tool : eiciel

        [http://linuxpoison.blogspot.com/2008/09/acl-editor-eiciel.html](http://linuxpoison.blogspot.com/2008/09/acl-editor-eiciel.html)

---

### Post by MrEgg on 2010-02-16
Thanks for your reply and for pointing out Eiciel, which I had tried. It's nice to have a graphical tool, but I haven't seen any added value over setfacl and getfacl (aside from the gui of course).

My main concern unfortunately remains: How can I prevent users from deleting files from a specified folder, while at the same time allowing them to create new files and modify existing ones? And how can then I elect specific users with the delete permission?

To my understanding - please correct me if I'm wrong - ACL (and UGO for that matter) does not make any difference between write and delete : if a user has the w permission at directory level, he will be able to delete any file within that directory, regardless of ownership - *unless* the sticky bit is set.

So, what I've done so far, to complete post #2, is to write a script which is run periodically (preferably at night, when users are no longer logged in), in which users lose file ownership to user2, and lose subdirectory ownership to user1. That way, user2 and user1 are the only users able to delete files within the /Data structure. At the same time, the files' perms remain 660 and the subdirectories 770.

My little scheme works for now, and today I'm happy. But what if later on I need to add a user3 with the same delete permission - what do I do then?

I have tried granting user3 write perms with ```
setfacl -m u:user3:rw testfile.txt
```but it didn't seem to work.

I know, I know, I'm asking for much... but with Linux everything always seems possible - it has totally spoiled me into always wanting more ;)

---

### Post by bodhi.zazen on 2010-02-16
As far as I know, if you can write the file you can delete it. I am not aware of any method to separate these privileges beyond what you are doing.

---

