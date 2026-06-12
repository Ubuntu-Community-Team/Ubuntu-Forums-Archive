---
title: "NFS not mounting properly using autofs"
date: 2011-05-28
forum: Server Platforms
---

### Post by DJWK on 2011-05-28
Hi! I've got a little problem here...

I've configured a server with Ubuntu Server (Natty) and i'm trying to mount a NFS filesystem on another Ubuntu machine (Natty).

/etc/exports on the server looks like this:

```

/home/juha      192.168.1.0/255.255.255.0(rw,sync)
/var/www        192.168.1.0/255.255.255.0(rw,sync)

```

And...
```

$showmount -e 192.168.1.39
/var/www   192.168.1.0/255.255.255.0
/home/juha 192.168.1.0/255.255.255.0

```

So far so good, right?

Now autofs and auto.master is configured like this:

```

+auto.master
/home/juha/nfs/wnxs1    /etc/auto.wnxs1 --timeout=15

```

and auto.wnxs1:
```

home    -rw,soft,intr,rsize=8192,wsize=8192 192.168.1.39:/home/juha
www     -rw,soft,intr,rsize=8192,wsize=8192 192.168.1.39:/var/www

```

folder /home/juha/nfs/wnxs1 already exists on the client and autofs should now dynamically create folders *www* and *home* under it. But it doesn't.

Both, client and server have the /etc/idmapd.conf:
```

Nobody-User = nobody
Nobody-Group = nogroup

```

The user and group exist on both machines.

I've understood that autofs could be used this way to mount filesystems. I don't want to use fstab mounting because in case the server is down when i boot my client, I would have to mount the folders manually.

Anyone who can help me with this? Thank you! (in advance)

---

### Post by papibe on 2011-05-28
I would advice you to first test if your exports can be mounted normally.

First stop the autofs service:
```
$ sudo service autofs stop
```
Then try to mount them manually:
```
$ mkdir mnt1
$ mkdir mnt2
$ sudo mount -t nfs 192.168.1.39:/home/juha mnt1
$ sudo mount -t nfs 192.168.1.39:/var/www mnt2
```
If that works we can discard the nfs service and client as sources of the problem, then focusing on autofs.

Regards.

---

### Post by DJWK on 2011-05-31
Thank you papibe, that was exactly what I did :) It turned out that the NFS and auto mounts were working just fine.

I don't know why, but 'ls' command in the *wnxs1/* folder came back empty, not showing the mounts. But '*ls wnxs1/www/*' and *wnxs1/juha* showed folders contents properly.

It would be nice to know why you can't list folders using ls in the mount root. Maybe the resources are mounted first when you ask specifically for the mounted folders? But it's resolved now, I created symbolic links to each folder and they work as they should.

Thank you for your help!

---

### Post by hawkmage on 2011-05-31
If you want to ghost the auto mounted directories on your local file system with the autofs try adding the "--ghost" option to the line in the auto.master file like this:
```
/home/juha/nfs/wnxs1    /etc/auto.wnxs1 --timeout=15 --ghost
```
This should cause the auto mounter to create the juha and www directories.

---

### Post by manopj1 on 2013-04-11
you go to /etc/default/autofs.
change browsable "yes" by default it is no and try

---

### Post by Anubis on 2013-05-01
[https://bugs.launchpad.net/ubuntu/+source/autofs/+bug/1050021](https://bugs.launchpad.net/ubuntu/+source/autofs/+bug/1050021)

---

