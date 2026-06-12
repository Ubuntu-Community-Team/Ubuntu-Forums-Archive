---
title: "SSH Chroot Isn't Working"
date: 2017-01-19
forum: Server Platforms
---

### Post by Kirk Schnable on 2017-01-19
Hey guys,

I am trying to set up an SSH chroot for a user group, based on instructions here: [http://allanfeid.com/content/creating-chroot-jail-ssh-access](http://allanfeid.com/content/creating-chroot-jail-ssh-access)

I have done this before in the past and it doesn't seem to be working for me this time, not sure what I'm doing wrong this time...

/etc/ssh/sshd_config:
```
Match group jailusers
          ChrootDirectory /var/jail/
          X11Forwarding no
          AllowTcpForwarding no

```
/var/jail:
```
root@myserver:/var/jail# ls
bin  dev  etc  lib  lib64  usr
root@myserver:/var/jail# ls /var/jail/bin/
bash  cp  ls  pwd  rm
root@myserver:/var/jail# 

```


ssh output:
```
root@myserver:~# ssh test@localhost
test@localhost's password: 
Welcome to Ubuntu 16.04.1 LTS (GNU/Linux 4.8.0-32-generic x86_64)


Last login: Fri Jan 20 00:43:28 2017 from 127.0.0.1
/bin/bash: Not a directory
Connection to localhost closed.
root@myserver:~# 

```

I seem to be getting **/bin/bash: Not a directory**, but not sure why, it should be there...

Any suggestions?

Thanks!

---

### Post by darkod on 2017-01-22
In those instructions you linked the guy seems to be creating/copying the bash folder into /var/jail/usr/bin while according to what you posted above your bash folder seems to be in /var/jail/bin. Could that be the error?

He used:
```
$ cd /var/jail/usr/bin
$ cp /usr/bin/ls .
$ cp /usr/bin/bash .
```

That would make a copy of ls and bash into /var/jail/usr/bin and in your case they are in folder /var/jail/bin.

---

### Post by Kirk Schnable on 2017-01-22
Yeah I noticed that while I was working on it, no I copied everything to /var/jail/bin, not to /var/jail/usr/bin as they suggested in the article.  So, that's not the issue.

---

### Post by darkod on 2017-01-23
But that is exactly what I was pointing out. Assuming the tutorial is correct, you have copied folders into a different path. Wouldn't that provoke the chroot jail not working?

Have you tried copying the folders into /var/jail/usr/bin as suggested in the tutorial?

---

