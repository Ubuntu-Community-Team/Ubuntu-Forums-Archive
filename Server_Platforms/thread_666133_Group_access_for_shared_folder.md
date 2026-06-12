---
title: "Group access for shared folder"
date: 2008-01-13
forum: Server Platforms
---

### Post by hmhmhm on 2008-01-13
Hi,
I have a network with one Ubuntu server and a couple of Ubuntu desktops setup.
The server shares files via Samba. I have created a user group called "group1" with a couple of members. I intended to setup a folder where all members of the group have full read/write/execute access. This works very well, however, when a group member called "member1" copies a new file into the folder, the file has owner "member1" and group "member1", so the other group members don't have write access to the file. I can do manually chown -R to assign all files in the shared folder to group1, however, that's not a very good solution.
Is there no way to make the group for all files in a particular folder static?
Thanks for any suggestion,
hmhmhm

---

### Post by koenn on 2008-01-13
try
```
chmod g+rws /path/to/hsareddirectory
```
new files in that directory will then get group = group1 (i.e. the group of the parent dir) in stead of the primary group of the user that created the file

it doesn't change existing files, so you'd have to chown those manually, eg chown -R

---

### Post by hmhmhm on 2008-01-14
brilliant, that did the trick!!!
thanks heaps!
hmhmhm

---

### Post by pneaveill on 2008-02-20
Not sure if this is still being monitored or not, but here goes....

I am needing to build a file server via samba for the people at work to be accessed similarly as the previous poster.  Each group needs access to the data in the other groups, yet needs to be kept separate for billing/project status, etc.

  Do I need a symlink or something to tell samba/apache where to find the files?  I tried the previous chmod, but not sure if I did it correctly.  Drive 2 on the server is creatively called 'archive' and will have close to a dozen projects in it.

Thanks in advance

---

