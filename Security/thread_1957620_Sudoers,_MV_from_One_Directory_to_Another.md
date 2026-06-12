---
title: "Sudoers, MV from One Directory to Another"
date: 2012-04-12
forum: Security
---

### Post by hateborne on 2012-04-12
Evening Ladies and Gents,

I am trying to set the sudoers file to allow user "bob" to move files from his home directory to my directory.
```
bob:  /home/bob
me: /home/hateborne
```I understand the sudoers line would be something along the lines of: (NON-WORKING)
```
bob ALL=(root) NOPASSWD: /bin/mv /home/bob/* /home/hateborne/*
```Could anyone provide the correct syntax for that? I have dumped a good 45min into trying to find a solution online, but simply have not found anything useful. 

-Hate

---

### Post by cariboo on 2012-04-12
Wouldn't:

```
gksu nautilus
```

accomplish the same thing without chancing screwing up your sudoers file?

---

### Post by hateborne on 2012-04-13
Crap, sorry. Forgot to mention that I am using Ubuntu 11.10 Server x86.

That might work on the desktop version, but unlikely server.

-Hate

---

### Post by bab1 on 2012-04-14
> **hateborne said:**
> Evening Ladies and Gents,

I am trying to set the sudoers file to allow user "bob" to move files from his home directory to my directory.
```
bob:  /home/bob
me: /home/hateborne
```I understand the sudoers line would be something along the lines of: (NON-WORKING)
```
bob ALL=(root) NOPASSWD: /bin/mv /home/bob/* /home/hateborne/*
```Could anyone provide the correct syntax for that? I have dumped a good 45min into trying to find a solution online, but simply have not found anything useful. 

-Hate

A couple of things.  First: I don't believe you can specify the the directories to be used (only the command).  Second; You are providing the user "bob" the ability to run /bin/mv (anywhere in the system) with root user privilege (Yikes!) and with no password needed (Double Yikes!).  So essentially anyone that typed in something like: *sudo mv /etc/* /tmp * could kill the system.

Here is a good [**_[COLOR="Purple"]guide[/COLOR]_**]("http://www.gentoo.org/doc/en/sudo-guide.xml") to sudo.  But I don't think sudo is what you want to use.

A users home directory should be for that users use only.  I would use a common place for the files and folders you want multiple users to access.  Then create a group for these users.  Then anything bob wanted you to have he could place in that directory and you could get it.  Some thing like this```

common dir = /srv/admins
common group = users
users = bob hateborne
```

When you create the directory you can change the group so you have this```
$ls /srv/
drwxrwsr-x 3 root admins 4.0K 2011-04-11 20:58
$ls /srv/admins
-rw-rw-r-x 3 bob       admins 4.0K 2011-04-11 20:58 test_file
-rw-rw-r-x 3 hateborne admins 4.0K 2011-04-11 20:58 test_file2
```

As you can see the directory /srv/admins has a file that both users can rw.  I use the sgid bit to preserve the group when adding files (see the red s for the sgid bit above for clarity)  See [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid") more info on suid and sgid and the sticky bit.  

On your machine you will see that /srv/cvs is set up exactly like what I have described (the group is *src*).

Once again it is dangerous to allow users to have root power, even if it is for just one command.  There are other ways to reach your goal.

---

### Post by Jonathan L on 2012-04-14
Hi Hateborne

> to allow user "bob" to move files from his home directory to my directoryAs bab1 says, it's really a permissions issue, rather than a sudo issue.  I agree with them entirely about making shared directories.  My belief is that the groups mechanism is essential for shared work on a given computer, and I wholeheartedly agree with bab1's use of group-sticky (or better yet, bsdgroups in the mount options).  But that is only going to work on newly-created files; any files which are renamed with mv will retain their original group.  (When I've run this on large servers with many users and many shared-group directories that might be a problem; for you it won't be.)

To directly do what you've said, assuming you have the usual singleton groups (ie, a group per user), you can have a directory like this:

```
cd ~
mkdir frombob
chgrp bob frombob
chmod 775 frombob
```He can then do
```
mv myfile ~hateborne/frombob

```You could of course make your home directory writeable by others in the same way, but it's not a good idea, and many programs will complain about its implied loss of security.

NB: bob can write in the directory because it's group writeable for a group he's a member of.  The file will be owned by user bob, but you'll be able to delete if because you own the directory.

If you actually have a lot of this, follow bab1's advice.  A good place for the shared directories is to make a user for each shared group, and just use ~groupname.

Hope that helps.

Kind regards,
Jonathan.

---

