---
title: "[SOLVED] changing user account name"
date: 2008-11-26
forum: Server Platforms
---

### Post by tr333 on 2008-11-26
Is it possible to change the username of the main user account?  If not, how do I create a new account with the same sudo privs. as the main account (so i can delete the other account)?

---

### Post by unutbu on 2008-11-26
As you use an account, the username insidiously becomes entwined in the paths and contents of many config files. Changing your account name is possible, but it becomes a horrendous mess. I think it is much better to create a new user and then copy data over.
Config files have to be redone or copied with care.

To create a new user:
```
sudo useradd -D NEWUSER
for group in `groups`; do echo $group; sudo gpasswd -a NEWUSER $group; done
```
The first command creates NEWUSER with default settings. The second command makes NEWUSER a member of all the groups you currently are a member of.

---

### Post by tr333 on 2008-11-27
I just tried creating a new user with "sudo useradd -D username" and its printing out the useradd help info to stderr.  The help information says that this is the correct syntax :?

> Usage: useradd [options] LOGIN

Options:
...

---

### Post by unutbu on 2008-11-27
Sorry, my mistake. Try
```

sudo useradd --create-home NEWUSER
```

---

### Post by tr333 on 2008-11-27
That seemed to work for adding the user and the groups, but it created the default shell as /bin/sh.  How do i set this to /bin/bash?

---

### Post by benhur99ph on 2008-11-27
Go to System>Administration>Users and Groups...
Then edit it from there...
You may need to unlock it ... just type the password and you're all set...

---

### Post by tr333 on 2008-11-27
> **benhur99ph said:**
> Go to System>Administration>Users and Groups...
Then edit it from there...
You may need to unlock it ... just type the password and you're all set...

I'm running Ubuntu Server.  I don't have the GUI preferences.

---

### Post by tr333 on 2008-11-27
Found the solution in 'chsh'.  Thanks for the help on this.

---

