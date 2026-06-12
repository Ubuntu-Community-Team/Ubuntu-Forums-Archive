---
title: "backticks in fstab?"
date: 2011-02-14
forum: Server Platforms
---

### Post by jmallen2982 on 2011-02-14
I want to have fstab mount an nfs partition based on the output of a python script whose job it is to find the appropriate server, like this:

`/root/serverIp.py`:/home   /ebs   nfs4   _netdev,auto 0  0

Now for some reason this actually works on one of my x86_64 10.04 LTS amazon ec2 instances. On my 10.04 i386 instance it does not.

Now when I run mount -a on the 64bit instance, it also doesn't work.This is the kind of error I get.

mount.nfs4: DNS resolution failed for `/root/serverIp.py`: Name or service not known

It's clearly not evaluating the expression, and simply treating it as a string.


But somehow on bootup it magically mounts the drive. I have no idea how this is happening. I really can't explain why it works. I would imagine that it isn't running things as a shell script, so it makes little sense. Is it possible that it's reconnecting all drives that were previously connected? The IP it's connecting to on the working server isn't changing.


The information about what exactly happens on bootup is woefully incomplete, and the whole process is very opaque. What process calls the fstab, and in what fashion? Why is it working for one server and not for the other? What log file should I check? 

Any help appreciated.

---

### Post by elico on 2011-02-14
instead of using fstab you should use a script on system startup.

---

### Post by hawkmage on 2011-02-14
Another idea would be to use autofs and an automount script to auto mount the required locations when accessed.

---

