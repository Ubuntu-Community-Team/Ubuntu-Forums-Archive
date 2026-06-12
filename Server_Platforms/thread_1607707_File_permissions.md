---
title: "File permissions"
date: 2010-10-28
forum: Server Platforms
---

### Post by djanie78 on 2010-10-28
Curently, when a user creates a file or a folder on my server, that file or folder is read and write to that user but only read and execute to the group. Apart from manually "chmod"ing the file or directory can i set it such that whatever file or directory created by a particular user is set with permission 777?
Help please

thanks

---

### Post by AndyCee on 2010-10-28
Assuming you've considered any security concerns that could arise - 

For each user, add into their .bashrc file the following line:

umask 0000

For more info about umask & the like, there's a nice explanation [here]("http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html").

EDIT: I'm pretty sure this will only affect files & folders created AFTER this line is added.

---

### Post by djanie78 on 2010-10-28
Thanks  looking into that now. Will report back

---

### Post by Morbius1 on 2010-10-28
It would be better to see how your share definition is set up but you could use "force user" to to accomplish this.

If you add the following line to the share definition in smb.conf:
```
force user = some_user_name
```Then every time a user is authenticated to gain access to the share his identity will be converted to "some_user_name". All new files will still save with mode = 0755 but all ownership will be "some_user_name".

"some_user_name" can be the local server user name or even "nobody" depending on how you are set up.

---

### Post by djanie78 on 2010-10-28
> **Morbius1 said:**
> It would be better to see how your share definition is set up but you could use "force user" to to accomplish this.

If you add the following line to the share definition in smb.conf:
```
force user = some_user_name
```Then every time a user is authenticated to gain access to the share his identity will be converted to "some_user_name". All new files will still save with mode = 0755 but all ownership will be "some_user_name".

"some_user_name" can be the local server user name or even "nobody" depending on how you are set up.

My users are coming in via winscp ie ssh which restricts them to their home directory. However there is one user who need access to all other user directories

---

### Post by the_original_billq on 2010-10-28
I'm going to assume your experience with *nix is somewhat novice.

While AndyCee mentions security and points you to a doc explaining file system permissions, I'm going to mention a couple of things in this thread.

If every user authenticating on your server is a member of some group, you can set your permissions so that everyone in the group has access, but "the world" doesn't.  Setting a umask of 002 or 006 prevents every user on the system from being able to read or read/write everyone elses' files, while allowing the "group" to share their data.

If a user wants to be more restrictive, they can setup a "setgid" directory, use a umask of 066, and achieve the same result.  Make each of your users the member of one group, let's call it "developers".  Then each user makes a work directory in their HOME and sets the permissions on that directory such that anything dropped into that directory gets chgrp'd to the "developers" group.

```

mkdir $HOME/work_dir
chmod 770 $HOME/work_dir
chmod g+s $HOME/work_dir

```

Now, even though the default umask is 066, everything in $HOME/work_dir will be accessible to everyone in the group.

The huge benefit of this is that your users can collaborate and your system still remains secure.

-Bill

---

### Post by djanie78 on 2010-10-29
I dont think i explained what i want properly. 

I got four user, three of which are normal users and one an admin.

All users have their own secure directories and are able to do as they like within them. 

The fourth user, who is the admin is able to see whatever is placed in the other three user directories. The admin user is even able to write to their directories as well. 
Upto this point we are fine. 

Our issue now is if one of the three users should create a a new directory within thier home directories of course, The admin user is still able to read whatever was created, great, but not able to write to that directory.
I hope am making sense. 
thanks fellas

---

### Post by SeijiSensei on 2010-10-29
Are you handling this by having admin user belong to each user's group?  (User "jane" has primary group "jane" with members "jane" and "admin".)  Then changing the default umask from 022 to 002 in $HOME/.profile will give the admin user full privileges to any files or directories created by the user.

---

### Post by djanie78 on 2010-11-03
The suggestions here did not work for me but certainly pointed me in the right direction.

I achieved my aim first by installing the libpam-umask package then adding 

```
session optional pam_umask.so umask=002
```

to /etc/pam.d/common-session

This way whoever authenticates will create files or folders with group read and write access.

Thats if anyone wants to know

---

