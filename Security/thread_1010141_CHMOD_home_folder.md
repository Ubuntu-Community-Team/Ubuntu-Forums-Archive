---
title: "CHMOD home folder?"
date: 2008-12-13
forum: Security
---

### Post by Neostar2119 on 2008-12-13
I suspect I somehow jacked up my permissions during a Neverwinter Nights fiasco a few weeks ago, but...

What should the Home folder and folders and files within it be set to as far as CHMOD?

---

### Post by lensman3 on 2008-12-13
The chmod (as root) on my system for all files and directories is:

chmod 744 -R ~<home_Directory>            (notice the leading tilde)

This sets everthing (and lower directories) to read-write-execute for owner, read-nowrite-noexecute for group, and r-nowrite-noexecute or -rwxr--r--.  This is a minimum.  I would even suggest 700.  That way only your login can read or write or execute a file.

The -R recursively goes down through all sub directories and sets them too.

You will need to be superuser because you can't change the ownership of a file unless it belong to you.  Root can change anything it wants at anytime (99.9999% true).

A word about the ~<home_directory>.  Your home directory is alway the last field in the /etc/passwd for your login name.  To automatically find your home directory enter a "cd" on a line by itself.  If you are in another directory you will return to home (the tilde).  My examples are for a user called joe and his home directory is called joe. There is a sutle difference between ~joe and ~/joe.  The first is the home directory of "joe" and the second is a subdirectory called "joe" of  joe's home directory (in this case a subdirectory called joe of user joe).

Be careful as the -R can cause it to go up the directory tree to the parent too.  Then if you have multiple accounts on your system you will have to go and fix them back up.

You can always test out what the command is going to do first by do a "ls -R ~user".  The list command will expand just  like chown, chmod, and chgrp will do.

The only thing left is to make certain that owner and group for the files are correct.  To get the group you belong to type in "groups" and your group(s) will be echoed.  The first in the list, if a list is printed, is your primary group.  You can verify this by "cat /etc/passwd".  When you login this file determines your home directory and default group. The third and fourth fields (between colons) are the user and the group as a number.

To change your owners

chown OWNER:GROUP -R ~user
or
chown 502:502 -R ~user
or
chown joe:joe -R ~joe

where OWNER is the number of the owner in the passwd file and GROUP is the group numberthat you belong to.  Add -v to the command and everyfile changed will be echoed to the screen.  A cntl-c will kill the command, but by then it is too usually to late.

Be sure you get it right before you log out or you may not be able to log back in.  If you break it log back in as "root" and fix it.  Been-there-done-that! If you do an "ls -la" after all the changes and you see numbers where a user or group name should be displayed, then the group or user were not found in the /etc/passwd or /etc/group files.

I would suggest that you log out and then back in after all the changes to get the initial login spawn correct.  The initial login spawn is slightly different than later process spawns and different DOT files are read. 

Have fun doing this and remember you can also undo it too, it is just a little harder because you have to login then as root.

---

### Post by bodhi.zazen on 2008-12-13
Once you are done, take a look at apparmor. You can use apparmor to limit access to your home directory in this way.

Also, if you have been compromised, perhaps you should re-install ;)

---

