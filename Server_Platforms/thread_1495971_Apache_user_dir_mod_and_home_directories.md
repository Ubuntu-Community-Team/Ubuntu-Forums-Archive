---
title: "Apache user_dir mod and home directories"
date: 2010-05-28
forum: Server Platforms
---

### Post by kaw3939 on 2010-05-28
I am using ubuntu server.  I want to automaticly set the group ownership of user home directories to a group that the user is not part of.  This is so that Apache can be part of this group and can access user public HTML directory, but other users are not able to access in any way the files in the users home directory.

What I have seen that works manually is adding the user and then changing the group for the home directory.  But I want to automatically set this when the user account is created.  WHat I see happening is that when /etc/skel is copied, it automatically sets the group and ownership of everything to the users default group and ownership.

I've seen some suggestions on setting permissions, but these don't seem to work because it seems that users are able to cd into a directory and not list it, but if they know the file name they can access the file.

Any advice on setting this up would be great.
I'm doing this to setup a server for students in my web development class and I don't want them to be able to peak at each others projects.

By the way I set the setgid bi on the home directory but this is ignored when the directories are coppied.  Essentially I just want this to be obeyed when user directories are created in /home

---

### Post by kaw3939 on 2010-06-01
THis is a shameless bump and a less than optimal resolution.

The options were essentially to create a jail or what I ended up doing is to set the permissions on the directories to enable group execute, other execute, and other read on the public_html

---

