---
title: "Confusing permissions"
date: 2012-01-27
forum: Server Platforms
---

### Post by Ghosthaven on 2012-01-27
This may take a moment to explain...

I own and run a MUD (think World of Warcraft except text only
using oldschool telnet protocol). I've ran this MUD for many
years now and for the past year or so have ran it off a home
ubuntu server.

I want to move the MUD to a dedicated VM that runs nothing but
a clean copy of Ubuntu server. This will allow me to give out
limited shell access to other members of my admin staff so the
workload on me is lightened somewhat.

My problem is I'm unable to clearly understand permissions to the
extent that I need to make this work.

My mud has this directory structure.

MUD->
  area (read/write required for all users)
  logs (read required for all users)
  player (locked)
  src (no read/write for all files, execution allowed for one
       shell script that runs one program in this directory)

My problem is I can't figure out how to arrange it so I can
access everything, the MUD can access all its own files with
both read and write, and so I can limit the access to my staff.

If I give execution access to this one shell script (called
startup in the src directory) then when one of my staff members
runs it, it'll run under their user, which won't have write
access to the area and player directory that the MUD needs.

I THINK the solution is to create a user account just for the
MUD, allowing the MUD to access everything, but limiting it
to other users. But I don't know of any kind of Do-As command
that'll let someone else execute the required shell
script/program as needed. At least not one that doesn't require
knowledge of the password.

I fully understand how chmod and chown work... I just can't
figure out how to use them to get the result I want.

If I haven't explained things clearly, please excuse me... my
brain is fried from worrying about this for hours. I'll be glad
to clear up any gray areas.

---

### Post by oldfred on 2012-01-27
There are a few here that really understand groups & permissions. (not me). But to get you started on understanding:

Group File, Directory and Device permissions: chmod
[http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html)
Info on permissions for groups
[http://www.zzee.com/solutions/unix-permissions.shtml#setuid](http://www.zzee.com/solutions/unix-permissions.shtml#setuid)

[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

All users read/write shared folder - morbius1
[http://ubuntuforums.org/showthread.php?t=1727396](http://ubuntuforums.org/showthread.php?t=1727396)
See lucky's post on network based shares & setting permissions commands
[http://ubuntuforums.org/showthread.php?t=1498422](http://ubuntuforums.org/showthread.php?t=1498422)

---

### Post by TheFu on 2012-01-29
You probably want each individual to be part of one or more Linux groups. Then you use the groups to control read-only, read-write, and write-only access to the different file areas. Users can be in multiple groups.

You can also force new files to be created with a specific groupid under a directory using the g+s permissions option on the directory holding the files.  Of course the userid trying to create the file will need to have write permissions to the directory already.

You can prevent new files from being added to a directory, while still allowing existing files to be modified too.

As for RunAs or DoAs, sudo can do this. It is a fairly common use. Check the man pages for how. It is pretty easy, but I'd try to avoid it when normal user and group permissions can accomplish what you desire.

Allowing all users (even non-admin users) read-write to a file system is a scary thing, since it means they can open a file for edit and truncate it to 0 bytes of data, effectively deleting the file.

After you read a little about users and groups, if you post your plans here, someone should be able to confirm reasonable well whether your plan will have the needed outcome and point out any security issues beyond allowing other people onto your internal LAN (which scares me personally).

---

