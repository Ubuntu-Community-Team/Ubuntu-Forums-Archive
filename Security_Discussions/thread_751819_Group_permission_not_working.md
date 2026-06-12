---
title: "Group permission not working?"
date: 2008-04-10
forum: Security Discussions
---

### Post by booyabazooka on 2008-04-10
There must be something I don't understand about how group permissions work.

I have a directory with umask 775, owned by group svnusers:

```
chris@kingsley:~$ ls -al /var | grep svn
drwxrwxr-x  7 root svnusers 4096 2008-04-10 20:13 svn
```

I am a member of the svnusers group:

```
chris@kingsley:~$ cat /etc/group | grep svn
svnusers:x:1001:chris
```

Yet I can't write to the directory:

```
chris@kingsley:~$ mkdir /var/svn/test
mkdir: cannot create directory `/var/svn/test': Permission denied
```

What am I missing?

---

### Post by netlogic on 2008-04-10
You should study UNIX permission.
[http://www.perlfect.com/articles/chmod.shtml](http://www.perlfect.com/articles/chmod.shtml)

---

### Post by Dr Small on 2008-04-10
> **netlogic said:**
> You should study UNIX permission.
[http://www.perlfect.com/articles/chmod.shtml](http://www.perlfect.com/articles/chmod.shtml)
That doen't explain a thing...
Let's see here.

/var/svn is set to 775 with root as the owner and svnusers as the group.
You have verified that you are in the svnusers' group.

Yet you can not write to the directory? That doesn't make sense.
Something isn't adding up.

---

### Post by netlogic on 2008-04-10
I am not trying to be rude. It makes perfect sense to me.

His umask isn't set properly on the /var/svn or he needs to check his environmental variable for umask. He can always use ACL if he needs more complex permission. Something like this can be discussed with steps. Something a  person has to read.

---

### Post by netlogic on 2008-04-10
There is another thread from few hours ago should explain this...
[http://ubuntuforums.org/showthread.php?t=738099](http://ubuntuforums.org/showthread.php?t=738099)

---

### Post by booyabazooka on 2008-04-11
Netlogic, I read the chmod summary you linked, and it doesn't seem to explain anything I don't already know.  I'm not particularly comfortable with using file permissions, but I'd say I'm past the point where an RTFM comment can be helpful.

/var/svn is owned by the svnusers group, chris is a member of this group, and the group permission for /var/svn is rwx (as I said in my initial post), so this would lead me to believe that the user chris can modify the directory.

"His umask isn't set properly" - are you saying that my train of thought in how group permissions are supposed to work is incorrect, or that I haven't actually set the permissions I thought I did?

"he needs to check his environmental variable for umask" - I have not modified this, and after reading the thread you linked to, I still can't figure out what exactly it means.  Is this part of what you'd say "a person has to" know?

"Something like this can be discussed with steps" - steps?  what?

I don't think I'm doing anything particularly complicated.  Just trying to grant write access on a folder, to every member of the svnusers group.  As far as I understand, this is exactly what the group permission is supposed to do.  What part of this is wrong?

---

### Post by netlogic on 2008-04-11
Hi.
Maybe, you should do research about how inodes are linked the filesystem. Information about the file is the inode. There are million different things can go wrong here. Also, how the filesystem works with the permission are important to know. It will take you less than 30mins to browse the web for the detail clarifications. Something like UNIX permissions has been explained better for many decades. The current topic is heavily documented .

good luck

---

### Post by hyper_ch on 2008-04-11
just out of curiosity: after you added yourself to the svn group, did you logout?

---

### Post by cdenley on 2008-04-11
> **hyper_ch said:**
> just out of curiosity: after you added yourself to the svn group, did you logout?

That's what I was thinking. The /etc/groups file is only read when you log in. To see if you are currently in a group, you use the "groups" command.

---

### Post by booyabazooka on 2008-04-11
Thanks, that was it.  I didn't log out.

---

### Post by hyper_ch on 2008-04-11
;)

---

### Post by drhiii on 2008-07-10
To add fuel to this... 

Is it possible to add a user to a 'root' or 'admin' group and have them at login assume the abilty to make changes to filesystems?

Scenario is... have a slew of /home/users with individual photo gallery applications.  In order to upgrade modules, permissions need to be changed temporarily to allow for the import of the upgrades, and then permissions can be reset.  Am trying to use a GUI application (an sftp proggie that allows for the changing of perms as well as file xfr support), so I can teach someone how to do this without having them log into a shell and do it manually.  Easy for me... but easier to train how to do this with a GUI app.  

I've added the user to several groups starting with root, but I cannot get it to work without going to a shell and sudo-ing to root.  

Anyone have thoughts on how to get past this, so a user can acquire root permissions at login, to be able to change perms via a GUI program?

tx

---

### Post by cdenley on 2008-07-10
The only way to log in as root is to login as root, which is not recommended. If you're just trying to avoid the terminal, you can press alt+f2, or create a launcher (right click desktop).

---

