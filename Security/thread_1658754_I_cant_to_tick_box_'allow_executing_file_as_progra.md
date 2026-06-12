---
title: "I cant to tick box 'allow executing file as program"
date: 2011-01-03
forum: Security
---

### Post by apik kery on 2011-01-03
hello for everybody expert in ubuntu.. 
please help me...
i am new in ubuntu 10.10..
what problem when i cant to tick box 'allow executing file as program' (in permision)..
thanks...

---

### Post by tgm4883 on 2011-01-03
> **apik kery said:**
> hello for everybody expert in ubuntu.. 
please help me...
i am new in ubuntu 10.10..
what problem when i cant to tick box 'allow executing file as program' (in permision)..
thanks...

Does your user own the file?

---

### Post by anystupidname1 on 2011-01-03
> **apik kery said:**
> hello for everybody expert in ubuntu.. 
please help me...
i am new in ubuntu 10.10..
what problem when i cant to tick box 'allow executing file as program' (in permision)..
thanks...

Try this from a terminal:
```
sudo chmod +x /*path*/*file*
```and if you're not the owner and should / want to be:
```
man chown
```

---

### Post by perspectoff on 2011-01-03
Yes, you must be the owner of the file or directory to change permissions.

You can also change all permissions as the root user.

To use one of the file managers Nautilus or Dolphin as root, start it from the command-line (Terminal or Konsole):

 sudo nautilus

or

 sudo dolphin

then you can change the owner, group, and permissions of any file or folder.

Also, sometimes when you change permissions, the changes aren't visible unless you View -> Reload or View -> Refresh the directory.

Occasionally you have to exit Nautilus or Dolphin and restart it to see the changes. This is especially true if you change permissions/ownership from the command line (using the chmod or chown commands).

Note that in the previous reply 

sudo chmod

involves changing permissions with root user-level status as well.

---

### Post by drewster911 on 2011-01-10
Hello, I am having the same problem.  Trying to run "openarena.x86_64", used to have no issues running it, and other executables too.  I did a "chmod +x", then while in openarena folder "./openarena.x86_64", says permission denied.  try "sudo ./openarena.x86_64", says "command not found' wtf?
try to change permisssion on openarena.x86_64 by checking "allow executing", will not stay checked

these permission isssue confuse the crap out of me

---

### Post by aysiu on 2011-01-10
> **perspectoff said:**
> 
To use one of the file managers Nautilus or Dolphin as root, start it from the command-line (Terminal or Konsole):

 sudo nautilus

or

 sudo dolphin

then you can change the owner, group, and permissions of any file or folder. That should actually be ```
gksudo nautilus
``` and ```
kdesudo dolphin
```

---

### Post by llllskywalker on 2011-12-21
why can't there be a button within the file properties that lets us switch to "sudo mode"?? i'm tired of having to resort to the command line to do something so simple. i have the root password, and i want to change a file/folder on MY computer. this is 2011 and it seems lame to have to use the command line for something that trivial.

---

