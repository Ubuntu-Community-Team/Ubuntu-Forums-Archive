---
title: "Mounting using Autofs needs to reboot Nfs-server after rebooting the server"
date: 2016-07-13
forum: Ubuntu/Debian BASED
---

### Post by malazbw on 2016-07-13
I have 2 RPis3 and nfs server 4, i used this tutorial for Autofs[http://www.instructables.com/id/Reduce-overhead-due-to-network-drive-on-Raspberry-/?ALLSTEPS](http://www.instructables.com/id/Reduce-overhead-due-to-network-drive-on-Raspberry-/?ALLSTEPS)And it works but after restarting the server (pi) i try to access the mounting folder but i stuck for a long time and i don't get any files
And in the Rp server I've installed this package

```
sudo apt-get install nfs-common nfs-kernel-server
```

after modifying exports file

```
sudo service nfs-kernel-server start
```

I 've installed this package in Rp client

```
$sudo apt-get install autofs
```

and i added the following line at the end

```
/home/pi /etc/mnt.autofs
```

i wrote in the autofs file,

```
nfsfiles  -fstype=nfs4  192.168.0.10:/remote/share 
```

Start automounter

```
$sudo service autofs stop
$sudo service autofs start
```

At the end i open the folder to mount the files

```
$cd /home/pi/nfsfiles
$ls
```

after this steps it's working, but when i reboot the server, it doesn't work and i need to reboot the nfs-server

---

### Post by howefield on 2016-07-13
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

