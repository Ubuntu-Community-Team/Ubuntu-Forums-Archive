---
title: "Severly restricting a user account"
date: 2008-06-19
forum: Security
---

### Post by theacoustician on 2008-06-19
I'm having a little bit of an issue setting up a user account to operate the way I'd like.  I'd like to set up an account for users to log in remotely (over SSH) and *only* have permissions to run about a half dozen commands from CLI.  I don't want to let them have the ability to leave their home directory, I don't want them to be able to change their permissions, and I really don't want them to have sudo access.  I'd like to do all this and not mess up other user accounts on the machine.

I created a new account using adduser and since its not listed under /etc/sudoers it doesn't have sudo access, as I desired.  However, getting the other restrictions in place seems to elude me.  Any help is welcome here.

---

### Post by pytheas22 on 2008-06-19
Users can only run programs for which they have execute permissions.  So you could chmod all the stuff that you don't want them to have access to in /usr/bin, /bin and anywhere else and they won't be able to run it.  If you need those programs to be available to other users, you can make them members of a group that does have execute permissions for the stuff in those directories.

The same goes for preventing your ssh users from viewing directories outside of their homes--anything that's not readable by everyone will be unviewable for them, so remove read permissions on all directories except their home folders.

---

### Post by gaten on 2008-06-19
You might want to look into chrooting ssh users.

[http://www.howtoforge.com/chrooted_ssh_howto_debian](http://www.howtoforge.com/chrooted_ssh_howto_debian)

---

