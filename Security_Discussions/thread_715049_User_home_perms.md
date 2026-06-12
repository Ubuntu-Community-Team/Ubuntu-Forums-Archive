---
title: "User /home perms"
date: 2008-03-04
forum: Security Discussions
---

### Post by knichel on 2008-03-04
I wish to protect the users home dirs on a server.  I have sudo access.  I do not want other users able to browse into each others home folders. So...

Can I ...
sudo chmod -R 700 /home/username
sudo chgrp -R www-data /home/username/public_html
sudo chmod 750 /home/username/public_html 

and put that into a shell script that runs periodically using a list of current users to protec the users home dirs? without breaking things?


--
TIA,
JuJuBee

---

### Post by luisromangz on 2008-03-04
Users cannot enter other people's folders by default

---

### Post by knichel on 2008-03-04
When a user is created on this server, it is assigned to the group called users and all home dirs have rwxr--r-- for some reason.  I am looking for a way to correct this.

---

### Post by ung/xunil on 2008-03-05
Yes, you are right knichel.

By default all users do belong to the group "users" and also to another called $USERNAME (his username). So all users can view each others files because all belong to the group "users".

If you don't want new users to belong to "users" group, not being able to see the home directory of the other users, reconfigure the "adduser" package, so that this doesn't happen anymore:
```
sudo dpkg-reconfigure -plow adduser
```
And answer "No".

You also need to chmod /home directories so that others can't see your home directory:
```
sudo chmod o-r /home/$USERNAME
```
Now all users you create from now on will not be able to see inside your home directory. To remove this privilege from existing users, remove yourself from the "users" group, or remove them.

If later you want to create some users and you want them to be able to read each others files, reconfigure the "adduser" package again.

Each new file created by a user has some default permissions (set by the umask), and those default permissions are: other users and group users can read the new file. If you want to change this, you need to change the umask of the user(s). Edit the following files in your home directory (you can have just one of them, or both), the are executed each time you login or open a console/terminal:
```
~/.profile
~/.bash_profile
```
And add a line with:
```
umask 077
```
Logout and login again.

This new umask will make all new files created with the equivalent of "chmod 700" -only the user (owner) have permissions to read/write/execute, no one else. Take a look here to read more about umask: [http://wiki.debian.org/DebianDesktopHowTo]("http://wiki.debian.org/DebianDesktopHowTo").

If you want all new users to have this new umask (or a different one), edit the same files in the /etc/skel/ directory. Each new users default files (backgrounds pictures, directories, menus and other files) are copied from here, so changes in these files will be copied to the new users.

I read somewhere that changing the file /etc/profile will change the umask for all users, but never confirmed it.

[SIZE="4"]IMPORTANT:[/SIZE] To make changes take effect you (or the users who have a changed umask) **must logout from all sessions** (reboot to be sure).

About that public_html directory that has different permissions, and also as an alternative to umask/chmod permissions, you could use ACL. I don't use it but here is a link about it: [http://www.debianhelp.co.uk/acl.htm]("http://www.debianhelp.co.uk/acl.htm")

---

### Post by knichel on 2008-03-06
Thanks soooo much for the Plethera of information.  Great stuff.  Let me clarify...

Suppose I want to set the umask to 037.  That means that the perms on newly created files  will be rwxr----- ?  So if I change adduser to the owner and group are the same (group for each user).  That way for the public_html folder, all the user needs to do is chgrp www-data -R /home/$USERNAME/public_html ?

In order for the web server (www-data) to be able to read ~/public_html, what do the perms on /home/$USERNAME need to be?

Thanks again.

---

### Post by ung/xunil on 2008-03-06
Your welcome knichel. Well, I think you are correct about it all. 

About the umask. The default one is the first:
```
$ umask
0022
$ touch file-with-umask-0022
$ ls -l file-with-umask-0022
-rw-r--r-- 1 user user 0 2008-03-06 17:47 file-with-umask-0022
$ umask 0077
$ umask
0077
$ touch file-with-umask-0077
$ ls -l file-with-umask-0077
-rw------- 1 user user 0 2008-03-06 17:50 file-with-umask-0077
$ umask 0037
$ umask
0037
$ touch file-with-umask-0037
$ ls -l file-with-umask-0037
-rw-r----- 1 user user 0 2008-03-06 17:53 file-with-umask-0037
```
I think the rest would work as you are saying (at least I hope so). Did you tested it?

EDIT: About the permissions in /home/$USERNAME, I think it can be rwx------ and the /home/$USERNAME/public_html has rwxr-----. That way www-data can read /home/$USERNAME/public_html, but cannot read /home/$USERNAME and all the other things in /home/$USERNAME, just inside /home/$USERNAME/public_html/.

---

