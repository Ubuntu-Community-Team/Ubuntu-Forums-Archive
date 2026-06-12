---
title: "NFS share"
date: 2011-03-06
forum: Server Platforms
---

### Post by macstl on 2011-03-06
I got a NFS server share working on my desktop computer. using command line scripts. 
What is the best way to make these load up when I boot the machines

---

### Post by rubylaser on 2011-03-07
I'll assume you mean how to I get this to mount automatically from an NFS share on a different machine.  You'll just need to add an entry to /etc/fstab

```
sudo gedit /etc/fstab
```

Then paste an entry in like this...
```
server:/shared_directory /mnt/nfs nfs <options> 0 0
```

---

### Post by bsntech on 2011-03-07
Also ensure that you install:

sudo apt-get install nfs-common

On the client computer that you are using to connect to the NFS share - otherwise you'll get all kinds of errors about how it may be an incorrect FS type.

Brian S.
BsnTech Networks
[http://www.bsntech.com]("http://www.bsntech.com/picture-gallery.html")

---

### Post by macstl on 2011-03-07
Thank you Ill do that.  What can i use to find out what version of NFS Im running?

---

### Post by bsntech on 2011-03-07
I'm not sure if the version is important really - especially if your NFS server and NFS client are using the same OS.

Brian S.

---

### Post by supremedalek on 2011-03-07
Chances are it is NFS4 or at the earliest 3. If you are not using any NFS4-specific features, you should not worry.

---

### Post by macstl on 2011-03-07
Reading docs here , it sounds like you have to tell the system your using ver 4 if that is so.

---

