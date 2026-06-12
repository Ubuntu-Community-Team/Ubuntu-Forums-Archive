---
title: "Shared directory permissions question"
date: 2009-11-17
forum: Security
---

### Post by captnemo on 2009-11-17
This question has surely been asked before but I'm not getting it.  I've studied the tutorials and for some reason I cannot make directory permissions work properly.  

Example:

I want to create a directory that users Phil and Bob can both access read/write.  I've tried all kinds of variations but here's a simple procedure that seems like it ought to work but it doesn't:

1) As root, I create /home/testdir.  
2) Add a group called testgroup and make phil and bob both members of the group.
3) Set the group setting for /home/testdir to testgroup with read/write permission.
4) Log in as Phil.  I ought to be able to navigate and view /home/testdir but I can't.  It says I don't have permission.

There must be something really dumb that I'm missing here.  Any suggestions?

---

### Post by Agent ME on 2009-11-17
Does the folder have group read and executable permissions? This command should set the permissions correctly if they aren't already.
```
sudo chmod g+rwx /home/testdir
```

If that doesn't work, can you show the output of these commands? (These don't change anything on your system; they just report the permissions of the folder and whether your current user is in testgroup.)
```
echo "Groups: `groups | grep 'testgroup'`"
ls -l /home | grep ' testdir$'
```

---

### Post by captnemo on 2009-11-17
Thank you!  Lesson learned: Use the command line and not Nautilus to set this stuff up.
NOTE: The actual folder name and group name is alexisftp, not testdir and testgroup, and I had set the owner to myself, phil.

ls -l /home | grep ' alexisftp$'

Produced the following:
drwxr-s---  2 phil     alexisftp 4096 2009-11-17 14:30 alexisftp

Which is obviously wrong.  So I rechecked Nautilus and sure enough, it showed alexisftp for the group and showed "Create and Delete" for the permissions, which does not agree with the above.

So I used chmod to change the group permissions on /home/alexisftp and now get the following result:

drwxrwx---  2 phil     alexisftp 4096 2009-11-17 14:30 alexisftp

Nautilus still says exactly the same thing, however the permissions now work correctly.  Users phil and alexis can both copy files into the /home/alexisftp directory, delete them, and create and delete folders, which is what I was after.

Thank you very much.  :D

---

