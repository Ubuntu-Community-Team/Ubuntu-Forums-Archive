---
title: "Mounting CIFS share at startup"
date: 2009-01-26
forum: Server Platforms
---

### Post by stonneway on 2009-01-26
Hi chaps,

I'm trying to get a CIFS share to mount at startup. It works fine when mounting it from a terminal window, but I can't seem to find the right entry for fstab to mount the file.

I'm using this in fstab;

//192.168.1.100/sharename     /media/nas      cifs guest,allow_other

The share doesnt require a username or password to access it and from the command line I access it using the guest parameter. 

Any ideas what I'm doing wrong ?

Olly

---

### Post by vanadium on 2009-01-26
Probably you need to add " 0 0" at the end of the line.

To check whether there are errors in /etc/fstab, execute the command

```

sudo mount -a

```

If you do not have any output, your cifs mount will be mounted successfully as well.

If nevertheless it does not mount well during startup, then add the mount command to the file /etc/rc.local (the mount command as you would issue it at the prompt, without the "sudo").

---

### Post by Iowan on 2009-01-27
Probably more information than you need is [here]("http://ubuntuforums.org/showthread.php?t=288534").

---

