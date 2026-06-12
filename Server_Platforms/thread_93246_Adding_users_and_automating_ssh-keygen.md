---
title: "Adding users and automating ssh-keygen"
date: 2005-11-21
forum: Server Platforms
---

### Post by kharyett on 2005-11-21
Is there another script for adding users that will auto create the ssh-keygen based on the users password when we add a user?

I am not a scripting guy and most of my server configuration has been using ssh with the forum open and 2-3 google search windows:)


I want to add a bunch of users and have them setup for ssh use without them having to generate the keys. I can do simple scripts, but I looked at adduser and got lost in about 3.45 seconds.

Any ideas?

Thanks
-Kevin

---

### Post by Glut on 2005-11-21
The adduser command is a perl script, you could modify that. Alternatively you could write a small bash script, which accepts a single argument:
#! /bin/bash
adduser $1
su $1 -- ssh-keygen -t dsa

Of course, this is just off the top of my head, is untested and some scripting guru will probably know better.

---

### Post by kharyett on 2005-11-21
Duh!:o

Why didn't I think of that....

Sometimes I forget the KISS rule.

---

