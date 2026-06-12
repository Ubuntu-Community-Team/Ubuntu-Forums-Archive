---
title: "Sftp mount list"
date: 2010-04-08
forum: Server Platforms
---

### Post by dragos2 on 2010-04-08
In Nautilus I have a sftp:// mount as favorite, how can I see where it is mounted ?

---

### Post by richardjh on 2010-04-15
I am fairly sure Nautilus doesn't mount the remote filesystem, it just provides an abstraction layer to sftp which allows you to use nautilus to drag and drop files etc, but underneath it is running the sftp commands.

You can mount an sftp resource (as it is ftp over ssh) by installing fuse and sshfs.

Then mount the sftp resource like this

```
sshfs <remote_server>:/path/to/folder /mnt/sftp/<remote_server>
```

---

### Post by richardjh on 2010-04-15
I may be wrong. What is under 

```
~/.gvfs/
```

---

### Post by dragos2 on 2010-04-20
> **richardjh said:**
> I may be wrong. What is under 

```
~/.gvfs/
```

Empty unfortunately.

---

### Post by dragos2 on 2010-04-20
Anyone knows where nautilus mounts sftp ?

---

### Post by richardjh on 2010-04-20
Assuming then that it does get mounted you would be able to find it using ```
mount
```.

In fact I have just done this on my machine to test what results you would get and this is what I get:

```
richardjh@ubuntu:~$ mount
... all my existing mount points ...
gvfs-fuse-daemon on /home/richardjh/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=richardjh)
```So then I checked to see what is under ~/.gvfs and I see:
```

richardjh@ubuntu:~$ ls -l /home/richardjh/.gvfs/
total 4
drwx------ 1 richardjh richardjh 4096 2009-10-22 07:36 SFTP for richardjh on remotehost
```This should help you find out where your sFTP server is mounted.

---

