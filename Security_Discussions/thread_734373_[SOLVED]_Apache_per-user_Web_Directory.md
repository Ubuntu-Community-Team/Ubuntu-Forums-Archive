---
title: "[SOLVED] Apache per-user Web Directory"
date: 2008-03-24
forum: Security Discussions
---

### Post by samona on 2008-03-24
Hello everyone,

I'm trying to set up a per user web directory and I'm reading the tutorial on apache but I still can't figure it out.

I want to set up something like students.school.edu/~username where this will point to a public_html folder in a student's home directory.

I created a subdomain called students and made the DocumentRoot point to /home/*/  ,  and included this in the apache2.conf file 

<IfModule mod_userdir>
UserDir enabled
UserDir public_html
</IfModule>

Any help would be greatly appreciated.

---

### Post by newtonfn on 2008-03-24
You must enable userdir module. To do this you should type in a terminal

```

$ sudo a2enmod userdir

```

This well create two new symbolics link in /etc/apache2/mods-enabled: userdir.conf and userdir.load

I am not sure it students.school.edu/~username will work out-of-the-box but school.edu/~username will.

Maybe you should copy (or move) the content of /etc/apache2/mods-enabled/userdir.conf to the virtualhost you had created and then delete that symlink.

**Just a comment**. What you have done is allright (except to change DocumentRoot. that is innecesary). But you were missing to load the module with a line similar to:
LoadModule userdir_module /usr/lib/apache2/modules/mod_userdir.so and giving permission to the user's public_html directories.


Good luck
Sorry about my english.

---

### Post by samona on 2008-03-24
Thanks, but now what happened is it says forbidden?

where do i sent the permissions to allow school.edu/~student, to work?

---

### Post by newtonfn on 2008-03-24
You have created a VirtualHost?
I guess you did. Inside the VirtualHost, or outside any virtualhost you must add:

```

        <Directory /home/*/public_html>
                AllowOverride FileInfo AuthConfig Limit
                Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
        </Directory>

```

All your users (at least those with public webpage) must have a directory called public_html in theris home where theirs html resides.

And that directory, and all the files inside, must have at least read permissions to the Apache user (www-data). The easy way is to give read access to everyone. (that's the way I did it)

---

### Post by samona on 2008-03-24
Actually, I had each user's home directory set to private so that the other users wouldn't be able to access each other's home directories.  Is there a way to keep the users from access other user home directories, and still provide a web directory public_html for each user?

---

### Post by newtonfn on 2008-03-24
It's getting harder jejee.

First, I recommend to give a few users read access to everyone, so we can test the configuration is working and then try to harden the security.

Then, what I am thinking is that you should change user's directories group ownership to www-data

That's way www-data (the apache) will have access to the files, the user too because you must not change the owner user, only the group. But users could not see each others files.

to change the group of a directory entry:
```

chgrp www-data /home/username

```

---

### Post by samona on 2008-03-24
i appreciate all the help.

When I remove the permission restrictions from a user I am able to access their public_html directory from the browser, but with a user who's home directory is still restricted it still doesn't work even with the chgrp command.  

I don't know what i'm doing wrong.

---

### Post by newtonfn on 2008-03-24
At least, we now now that it is working, it is just a permissions thing.
Let's find out what is wrong (if you still tolerate my english)

I guess that the problem is apache not having permissions. By default, apache does not run as Root. It runs under a normal user account (just like a student), that's why he can't access the files.

A dirty solution, could be run apache as Root. It is possible but a security hole (a very big one) I do not recommend that but if you can live with that security issue... it is a easy solution.

I suggest to make sure the files and directories permissions are right.

When you make a "ls -l /home" the users have the right group (www-data) and their have group read permission? (in the permission columns should be something like (drwxr-x--- and in the owner column should be username:www-data)

The exact same permission (or less secure) should have the public_html directory too.
You can do a "ls -ld /home/username/public_html" too see the that directory permissions.

**What is important:** The group must be www-data and have at least read and execute permission for the group (The files inside public_html should have only read permission) OR the group could be anything but must have read permission to others.

Why the execute permission on the directories? Because on directories, execute permissions means permission to make a cd and list the content. If a directory do not have execute permission you can not access the files inside them even if the files have the right permissions.

If nothing woks, please send me the output of the ls commands so i can see them. (I am sure the problem is permission because if you give full permissions it is working.. i can't think about any other problem)

---

### Post by samona on 2008-03-24
yesssssssssssssssss, that worked.  Thanks so much!!!

One question, now that the user is in group www-data, what exactly is the drawback.  Say I wanted them to be in group student, is it ok for them to be in both groups?

---

### Post by newtonfn on 2008-03-24
There is no problem for a user to be in two groups. For example, in Ubuntu the user with sudo privileges is in more than two groups. One is the primary group usually with the same name as the user, but it is also in the adm group, the cdrom group and many others. If a user is in a group, then it have permission to access every file in the system that this group have access. (a user can be in many groups.. but a file can only have one group)

But in your case the users are not in www-data (if you didn't alter the group files or used commands like groupadd, usermod or thing like that)

With chgrp we changed the directory groups only. The drawback is (if it is a drawback) that anyone in www-data group can access the files. But www-data is used by programs, almost none should be in that group. (actually I only know apache to use www-data)

To see the goups a user is member, you can use the command **groups**. Try to write in a terminal **groups** without any paramter, and if you are logged as the administrator account you should see something like: fernando adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin

That's means that my user, Fernando is in groups fernando, adm, dialou, cdrom, floppy, etc etc etc. If I want to know other user group, I can type something like "groups francisco" and will show me the groups that francisco is member.

Btw, I am glad that it worked :)

---

### Post by samona on 2008-03-24
Thank you very much for everything and for taking the time to explain everything to me. I really appreciate it.  Thank you!!!

---

### Post by newtonfn on 2008-03-24
I was thinking. There is a drawback.

Because we make all directories accessible by group www-data, apache have access to all of them.
If you installed a scripting engine like php, or give cgi access or something like that, I could make a script that access everyplace apache have access, because the scripts run under apache privileges.

In your case, a student can make a php script that access all the home directory of another student.
The only solution that I can think of is using something like suphp (in the case of php) but i cannot assist you because I never did that before.

---

