---
title: "Problem installing VMWare Server 2 on ubuntu version 8.10"
date: 2009-03-29
forum: Server Platforms
---

### Post by ubantuwannabe on 2009-03-29
initially i goggole how to install vmware on ubuntu which leads me to the following web pages.

[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

unforunately I realize that this was not suitable as my server is now ubuntu 8.10

when I run the installer

sudo vmware-install.pl

sudo: vmware-install.pl: command not found

so I

sudo find / -name vmware-config.pl -print
/home/chunhung/download/vmware/vmware-server-distrib/bin/vmware-config.pl

next I

cd bin
sudo ./vmware-config.pl

Unable to find the database file (/etc/vmware/locations)

Execution aborted.

Could anybody helps me to resolve this issue.

later I realize my version of ubuntu is Ubuntu 8.10

and come across

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

so how should I resolve this issue?

thanks

---

### Post by namaku0 on 2009-03-29
Which VMware Server 2 package did you use for installing?
If it's RPM, try the **tar.gz** package.

Use this guide instead:
[http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-8.10](http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-8.10)

---

### Post by hyper_ch on 2009-03-29
you could also ask in the howtoforge forum :) people are also nice there.

---

### Post by doogy2004 on 2009-03-29
[QUOTE=ubantuwannabe;6976335]initially i goggole how to install vmware on ubuntu which leads me to the following web pages.

[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

unforunately I realize that this was not suitable as my server is now ubuntu 8.10

when I run the installer

sudo vmware-install.pl
[QUOTE]

Change sudo vmware-install.pl to:
```
sudo ./vmware-install.pl
```

to execute a program/script that is not in the locations scanned for programs you need to uses a relative path "./" or an absolute path "/home/user/vmware-server/vmware-install.pl"

---

