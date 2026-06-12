---
title: "can't save smb.conf as smb.conf.master"
date: 2009-02-15
forum: Server Platforms
---

### Post by Lumpy3 on 2009-02-15
Looks like I need to configure my share in the smb.conf file.  Since i'm new to this I think it's wise to save a smb.conf.master version before I go mucking about.

I get a message that I don't have the permission.   What gives?  I'm the only user.

---

### Post by x33a on 2009-02-15
try 
```
sudo cp smb.conf smb.conf.master
```[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Lumpy3 on 2009-02-16
Ok, easy enough from the terminal, but how do I save a text file in gedit after I've made some changes to it?

---

### Post by dmizer on 2009-02-16
> **Lumpy3 said:**
> Ok, easy enough from the terminal, but how do I save a text file in gedit after I've made some changes to it?

You'll need to open the file with gksudo like so:
```
gksudo gedit /etc/samba/smb.conf
```

---

### Post by Lumpy3 on 2009-02-16
works a charm.  thanks.

---

### Post by x33a on 2009-02-16
and if you don't like terminal to copy/move root files, then use 
```
gksudo nautilus
```this way, you can do all file/folder tasks as root.

but, remember to close the root nautilus after the work is done.

---

### Post by dmizer on 2009-02-16
> **x33a said:**
> and if you don't like terminal to copy/move root files, then use 
```
gksudo nautilus
```this way, you can do all file/folder tasks as root.

but, remember to close the root nautilus after the work is done.

That is a really bad idea. It only takes one wrong click to render your system inoperative.

---

### Post by x33a on 2009-02-16
> **dmizer said:**
> That is a really bad idea. It only takes one wrong click to render your system inoperative.

depends on the level of expertise.

---

### Post by dmizer on 2009-02-16
In an attempt to refrain from beating a dead horse (we all know that even the best of the best make mistakes), consider this bug report: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/224360](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/224360) ... and then imagine that you encounter that bug while dragging a file with Nautilus opened as root. Doesn't matter how good you are if the system borks. And, that particular system bork with Nautilus open as root could be devistating.

---

### Post by x33a on 2009-02-16
i apologise if i may have sent the wrong message. actually i don't use root nautilus, heck i don't even use a graphical file manager these days. i said that so that newbies don't feel frustrated to do simple tasks. but i guess, prevention is the best cure :D

---

