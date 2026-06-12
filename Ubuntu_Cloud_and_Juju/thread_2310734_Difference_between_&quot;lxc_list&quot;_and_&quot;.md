---
title: "Difference between &quot;lxc list&quot; and &quot;lxc-ls&quot;"
date: 2016-01-21
forum: Ubuntu Cloud and Juju
---

### Post by jon-carmicheal on 2016-01-21
I am very new to cloud and virtualization, so I apologize if this is newbie question.  I followed a tutorial for setting up LXD on my Ubuntu 15.10 laptop.  It had me install nova-compute-lxd - ```
sudo apt-get install nova-compute-lxd
```.  I continued to follow a linked guide that had me do the following:
```
lxc remote add images images.linuxcontainers.org
lxc launch images:centos/7/amd64 centos
```

I could then list the new container with ```
lxc list
```

```
jon@Host-Linux:~$ lxc list
+--------+---------+------------+------+-----------+-----------+
|  NAME  |  STATE  |    IPV4    | IPV6 | EPHEMERAL | SNAPSHOTS |
+--------+---------+------------+------+-----------+-----------+
| centos | RUNNING | 10.0.x.xxx |      | NO        | 0         |
+--------+---------+------------+------+-----------+-----------+


```

Then I was looking for more information and tutorials on LXC/LXD, and I've come across several with commands like "lxc-ls."  So I tried that command on my system, but it does not show the centos container that I have running.  

So my question is, are "lxc launch" and "lxc-create" completely separate programs, as well as "lxc list" and "lxc-ls"?  Are they incompatible with each other?  Or how do they work together?  Which one is preferred, and under which circumstances?

Thanks,
Jon

---

### Post by bmullan2 on 2016-01-22
Jon

In the original LXC ...
the default containers were all Privileged (re required SUDO to start/stop/attach etc).. you could create UN-privileged containers but that required a small pre-setup/config  by the user.
the default location for the LXC containers was /var/lib/lxc/....

With the intro of LXD to LXC
the command syntax changed so did the default LXC container type.   With LXD/LXC the default container is now UN-privileged.
the location for UN-privileged containers you create are in your (or each user's) own HOME directory  in ~/.local/share/lxc
you can still create PRIVILGED containers but you specify that on the LXC LAUNCH command line when you create the container (see documentation - [https://linuxcontainers.org/lxd/getting-started-cli/](https://linuxcontainers.org/lxd/getting-started-cli/))

with traditional LXC (pre LXD) you would use  sudo lxc-ls (to list your default Privileged containers) and just lxc-ls (to list your UN-Privileged containers).

now with LXD/LXC you use -  lxc list

As the old "lxc-ls" and the new "lxc list" were for different implementations (lxc vs lxd/lxc) the commands are both still available but if you only use LXD/LXC then you only need to use "lxc list" from now on.

Same goes for "lxc launch" vs "lxc-create".   So if you see some guide that uses the old commands just be aware that you "could" use them as is or you could translate that command to the new command syntax and use the new and in my opinion VERY improved LXD/LXC capabilities.

Hope that helps.
Brian

---

### Post by bmullan2 on 2016-01-22
Also... unless you are going to use  OpenStack you don't really need to install nova-compute-lxd

---

### Post by jon-carmicheal on 2016-01-26
Thanks bmullan2.  That helps a lot.

---

### Post by karatedog on 2016-02-16
Is it possible to uninstall the old LXC without breaking the new LXD/LXC functionality?
Currently I don't have any unprivileged container, but a simple 'lxc list' drops an error, and as I see it they don't see each other's containers:

straylight :: ~ » lxc-ls     
straylight :: ~ » lxc list
error: Get [http://unix.socket/1.0/containers?recursion=1:](http://unix.socket/1.0/containers?recursion=1:) dial unix /var/lib/lxd/unix.socket: connect: permission denied
straylight :: ~ » sudo lxc-ls
lxc-ubuntu 
straylight :: ~ » sudo lxc list
+---------+---------+------+------+-----------+-----------+
|  NAME   |  STATE  | IPV4 | IPV6 | EPHEMERAL | SNAPSHOTS |
+---------+---------+------+------+-----------+-----------+
| debsq64 | STOPPED |      |      | NO        |         0 |
+---------+---------+------+------+-----------+-----------+
straylight :: ~ »

---

