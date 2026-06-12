---
title: "Mounting samba shares on system boot/user login"
date: 2011-06-28
forum: Server Platforms
---

### Post by jzollo on 2011-06-28
Greetings all!

I wrote a little script that will automatically mount two Samba shares to my home directory and I was wondering if a) You guys/gals had any input as to how I could improve on this script and b) Tell me how I would go about having this script automatically execute when I log on via SSH.

```

#!/bin/sh

mount -t smbfs -o username=Myuser,password=Thepassword //192.168.1.102/Data1 /home/user/Data1
mount -t smbfs -o username=Myuser,password=Thepassword //192.168.1.102/Data2 /home/user/Data2

```

Thanks in advance!

---

### Post by jzollo on 2011-06-28
Well, I seem to have made some headway, but hit a snag.

> 
mount: only root can do that
mount: only root can do that


The script executes but it requires root/sudo.

---

### Post by Cheesehead on 2011-06-28
xinetd makes it easy. Are you using it?

For example, you can create a separate socket service purely for the mount.
Or you can create an in-the-middle script that does automated tasks before handing the port over to sshd.

---

### Post by kgatan on 2011-07-02
By default only root can mount but you can allow users to do it by adding the option "user".

Im not sure if it works like this with samba shares but with devices you can pre define the mount in fstab with noauto and add the user option.

```
/dev/cdrom  /cd  iso9660  ro,user,noauto,unhide
```

Then you should be able to mount in above example using when logged in as the user.

```
mount /cd
or
mount /dev/cdrom
```

---

### Post by kgatan on 2011-07-02
The file "~/.bash_login" is executed on ssh login if i understand correctly.
You should be able to add the mount command in there.

---

