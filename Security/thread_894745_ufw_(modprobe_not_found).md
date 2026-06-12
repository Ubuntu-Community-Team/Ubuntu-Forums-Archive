---
title: "ufw (modprobe not found)"
date: 2008-08-19
forum: Security
---

### Post by ngmachado on 2008-08-19
Hi, 

I installed ufw in my Ubuntu VPS using the apt-get command. I configured it and it seems to be working fine (blocking connections).

The problem is, whenever I boot my server, the boot screen shows:

```

 * Checking minimum space in /tmp...                                     [ OK ] 
 * Starting firewall: ufw...                                                    /etc/rcS.d/S39ufw: 192: modprobe: not found
/etc/rcS.d/S39ufw: 192: modprobe: not found
/etc/rcS.d/S39ufw: 192: modprobe: not found
/etc/rcS.d/S39ufw: 192: modprobe: not found
                                                                         [ OK ]
 * Configuring network interfaces... 

```

I've searched "all" the Web for this problem at no avail. 

What's wrong? How should I fix the problem? 

Thank you.

---

### Post by cdenley on 2008-08-19
What is this output?
```

ls -l /sbin/modprobe
whereis modprobe
dpkg -L module-init-tools

```

---

### Post by ngmachado on 2008-08-19
Hi cdenley, thank you for help me out on this.

```

ls -l /sbin/modprobe
ls: cannot access /sbin/modprobe: No such file or directory

sudo find / -name "*modprobe*"
/etc/udev/rules.d/90-modprobe.rules
/etc/modprobe.d

whereis modprobe
modprobe: /etc/modprobe.d

dpkg -L module-init-tools
/etc
/etc/modprobe.d
/etc/modprobe.d/arch
/etc/modprobe.d/arch/i386
/etc/modprobe.d/aliases
/etc/modprobe.d/blacklist
/etc/modprobe.d/blacklist-framebuffer
/etc/modprobe.d/blacklist-watchdog
/etc/modprobe.d/isapnp
/etc/modprobe.d/options
/etc/depmod.d
/etc/depmod.d/ubuntu.conf
/etc/init.d
/etc/init.d/module-init-tools

```

I thought that modprobe wasn't installed... but it seems it is. I'm confused.

Thank you.

---

### Post by cdenley on 2008-08-19
That package is missing a lot of files!
```

cdenley@ubuntu:~$ dpkg -L module-init-tools
/.
/bin
/bin/lsmod
/sbin
/sbin/insmod
/sbin/modprobe
/sbin/rmmod
/sbin/depmod
/sbin/modinfo
/sbin/update-modules
/etc
/etc/modprobe.d
/etc/modprobe.d/arch
/etc/modprobe.d/arch/x86_64
/etc/modprobe.d/aliases
/etc/modprobe.d/blacklist
/etc/modprobe.d/blacklist-framebuffer
/etc/modprobe.d/blacklist-watchdog
/etc/modprobe.d/isapnp
/etc/modprobe.d/options
/etc/depmod.d
/etc/depmod.d/ubuntu.conf
/etc/init.d
/etc/init.d/module-init-tools
/lib
/lib/modules
/usr
/usr/share
/usr/share/doc
/usr/share/doc/module-init-tools
/usr/share/doc/module-init-tools/changelog.gz
/usr/share/doc/module-init-tools/copyright
/usr/share/doc/module-init-tools/changelog.Debian.gz
/usr/share/man
/usr/share/man/man5
/usr/share/man/man5/modprobe.conf.5.gz
/usr/share/man/man5/modules.dep.5.gz
/usr/share/man/man5/modules.5.gz
/usr/share/man/man5/depmod.conf.5.gz
/usr/share/man/fr
/usr/share/man/fr/man5
/usr/share/man/fr/man5/modules.5.gz
/usr/share/man/man8
/usr/share/man/man8/depmod.8.gz
/usr/share/man/man8/insmod.8.gz
/usr/share/man/man8/modinfo.8.gz
/usr/share/man/man8/modprobe.8.gz
/usr/share/man/man8/rmmod.8.gz
/usr/share/man/man8/update-modules.8.gz
/usr/share/man/man8/lsmod.8.gz
/sbin/lsmod

```

Try reinstalling it
```

sudo apt-get --reinstall install module-init-tools

```

---

### Post by ngmachado on 2008-08-19
Hi cdenley,

After reinstalling module-init-tools, I reboot my VPS and got:

```
 * Starting firewall: ufw...                                                    FATAL: Could not load /lib/modules/2.6.23.17-linode43/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.23.17-linode43/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.23.17-linode43/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.23.17-linode43/modules.dep: No such file or directory
                                                                         [ OK ]
```

Because the error messages have the name of the VPS company (linode), I searched its forum and found that "Module support is not compiled into Linode's UML kernels, as it would cause a security hole being able to insert code into the "process" on the host."

There're some users reporting the same problem and the company says we can ignore the error as everything is running fine. If we want to get rid of the boot error message, we must comment some  lines of code somewhere.

I'll dig a bit more about this in Linode's Forum because now it is not an ubuntu issue. 

Thank you.

---

### Post by cdenley on 2008-08-20
Are you sure you haven't deleted stuff by accident? Are you sure ubuntu was installed correctly? I don't understand why you would be missing so many files. I guess maybe the missing files is related to the missing module support.

---

### Post by honeybear on 2013-01-13
> **cdenley said:**
> That package is missing a lot of files!
```

cdenley@ubuntu:~$ dpkg -L module-init-tools
/.
/bin
/bin/lsmod
/sbin
/sbin/insmod
/sbin/modprobe
/sbin/rmmod
/sbin/depmod
/sbin/modinfo
/sbin/update-modules
/etc
/etc/modprobe.d
/etc/modprobe.d/arch
/etc/modprobe.d/arch/x86_64
/etc/modprobe.d/aliases
/etc/modprobe.d/blacklist
/etc/modprobe.d/blacklist-framebuffer
/etc/modprobe.d/blacklist-watchdog
/etc/modprobe.d/isapnp
/etc/modprobe.d/options
/etc/depmod.d
/etc/depmod.d/ubuntu.conf
/etc/init.d
/etc/init.d/module-init-tools
/lib
/lib/modules
/usr
/usr/share
/usr/share/doc
/usr/share/doc/module-init-tools
/usr/share/doc/module-init-tools/changelog.gz
/usr/share/doc/module-init-tools/copyright
/usr/share/doc/module-init-tools/changelog.Debian.gz
/usr/share/man
/usr/share/man/man5
/usr/share/man/man5/modprobe.conf.5.gz
/usr/share/man/man5/modules.dep.5.gz
/usr/share/man/man5/modules.5.gz
/usr/share/man/man5/depmod.conf.5.gz
/usr/share/man/fr
/usr/share/man/fr/man5
/usr/share/man/fr/man5/modules.5.gz
/usr/share/man/man8
/usr/share/man/man8/depmod.8.gz
/usr/share/man/man8/insmod.8.gz
/usr/share/man/man8/modinfo.8.gz
/usr/share/man/man8/modprobe.8.gz
/usr/share/man/man8/rmmod.8.gz
/usr/share/man/man8/update-modules.8.gz
/usr/share/man/man8/lsmod.8.gz
/sbin/lsmod

```

Try reinstalling it
```

sudo apt-get --reinstall install module-init-tools

```



and how to know to which packages (all of them) that it will depend module-init-tools? libcc6, ...

---

### Post by overdrank on 2013-01-13
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

