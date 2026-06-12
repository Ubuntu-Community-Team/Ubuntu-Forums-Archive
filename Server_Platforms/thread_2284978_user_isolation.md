---
title: "user isolation"
date: 2015-07-02
forum: Server Platforms
---

### Post by chrabja on 2015-07-02
Hi

I have small server on Ubuntu Server 14.04 and I have problem with user isolation. I can't use chroot becouse of software that my users should use and I don't have enough space to create chroot for each user. Users can read /etc/passwd and files of other users that should have to be read for everyone (for example html files and so on). I want prevent this. Users should have access only to system programs and own files though the permissions. If it even possible to do this? I have default apparmor settings, but as far as i know this can limit access by programs not by users. Can somebody tell me what can i search/learn/read to do this?

---

### Post by TheFu on 2015-07-02
I don't know of **any** method to limit user access to the password file. That isn't part of the design for Linux or Unix. Basically, it is necessary for a working system. The /etc/shadow file is already protected. There is NOTHING in the password file of any concern.  Even if you chroot, a password file must be provided. Even if you put userids into LDAP, users must be able to query it about other users.  Unix is designed as a cooperative OS - for users to work together on things.  

With all that said .... Unix is very flexible.

If you don't want users to see each other's files in their HOME directories, change the default umask for the system. Smart users can override that, if they choose.  umask 0077 into the /etc/profile and/or /etc/skel/.profile - assuming you don't allow users to chsh.

If you need a really, really, really, locked down system, you can have root be the owner for each user's HOME and take away the userid's write permission to their own HOME directory - there are repercussions in doing that.  Also, check out the different restrictive shells - **rbash** is one.

You can also strongly control the PATH for each userid so only certain programs are available in the PATH.  I've created hard-links into ~/bin/ with each program for users, and removed the common locations from PATH - adding back just $HOME/bin/. If you don't let the users touch their HOME or HOME/bin or any files inside HOME/bin/ ... that can work. A smart user with out a restricted shell will be able to run other programs.

There are other techniques - like swapping out the normal shell for a script that catches all signals and provides a minimal menu of programs that can be run.  For ssh logins, this can work, but for GUI logins it becomes next to impossible due to all the program dependencies necessary.

Some of the old-school UNIX books have step-by-step guides to setup remote shell access to run 1-2 specific programs and nothing else.   [http://shop.oreilly.com/product/9780596003234.do](http://shop.oreilly.com/product/9780596003234.do) is in my bookshelf. That might be where I learned this stuff last time it was needed. The devil is in the details. Miss one thing and a user can do more than you expect.

---

