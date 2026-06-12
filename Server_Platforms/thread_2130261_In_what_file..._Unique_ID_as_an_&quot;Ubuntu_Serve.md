---
title: "In what file... Unique ID as an &quot;Ubuntu Server Edition&quot;?"
date: 2013-03-28
forum: Server Platforms
---

### Post by MAFoElffen on 2013-03-28
I'm converting some HP Server Management utils from RPM to Debian. Why? for one reason, one of my HP servers runs the fans at full speed all the time if the Health Monitor is not installed to monitor temps...  Right now I'm rewriting the install scripts to what is relevant in Debian branches.

Currently... 12.04 and up- What ID in what file uniquely ID's an install as an Ubuntu Server Edition versus a Desktop Edition? We can't go off the kernel ID anymore since that was merged...

---

### Post by tgalati4 on 2013-03-28
;)```
cat /etc/issue
uname -a
lsb_release -a
```

Perhaps a better way would be to look for a package that is installed with the server that is not installed on the desktop.  (Edited:  Like landscape. ;) )

---

### Post by MAFoElffen on 2013-03-28
All three of those hints - same info as what I mentioned and also looking in /proc/... I don't see anything offhand unique between server and desktop in those.

Your second idea has a possibility. The only app i can think of that I install on all servers, only on servers, even as a vanilla temporary test server that I'm going to test and get rid of... is "openssh-server". But that is something that I install, not something that is just there.

On the other hand, on existing "Server Editions" when you log into an Ubuntu server (vs. a Desktop VT) there's some status files that get called and it displays those stats (and advertises Landscape stat's graphing)... Anyone know what/where those files are? Maybe called by motd?

---

### Post by MAFoElffen on 2013-03-28
Got it. Thanks for prodding me. It was:
/etc/update-motd.d/50-landscape-sysinfo

It's only on Server Edition.

---

### Post by CharlesA on 2013-03-29
> **MAFoElffen said:**
> Got it. Thanks for prodding me. It was:
/etc/update-motd.d/50-landscape-sysinfo

It's only on Server Edition.

Yep. Well, unless you install the landscape-common package on the desktop edition. ;)

Hope that gives you a point to start at.

EDIT: You could also go off the kernel, at least if you want to read it from dpkg. :)

```
dpkg -l | grep "kernel image" | cut -d " " -f 3
linux-image-3.2.0-37-generic
linux-image-3.2.0-38-generic
linux-image-3.2.0-39-generic
linux-image-server

```

---

### Post by MAFoElffen on 2013-03-29
CharlesA-
But it no longer works that way after they merged the kernels:
```

mafoelffen@maferr-ubuntu-1:~$ ssh -X mafoelffen@192.168.2.8
mafoelffen@192.168.2.8's password: 
Welcome to [COLOR=#ff0000]Ubuntu 12.04.2 LTS[/COLOR] (GNU/Linux 3.5.0-23-generic i686)

 * Documentation:  https://help.ubuntu.com/

  System information as of Fri Mar 29 15:09:15 PDT 2013

  System load:  0.0               Processes:           97
  Usage of /:   23.0% of 9.17GB   Users logged in:     1
  Memory usage: 3%                IP address for eth0: 192.168.2.8
  Swap usage:   0%

  Graph this data and manage this system at https://landscape.canonical.com/

Last login: Fri Mar 29 15:03:16 2013
mafoelffen@maferr-hpdl380g3:~$ dpkg -l | grep "kernel image" | cut -d " " -f 3
linux-generic-lts-quantal
linux-image-3.5.0-23-generic
linux-image-generic-lts-quantal
mafoelffen@maferr-hpdl380g3:~$ 

```

---

### Post by CharlesA on 2013-03-29
Ah ok. I am still running the old 3.2 kernel, not the 3.5 kernel, even though I am running 12.04.2.

Thanks.

---

