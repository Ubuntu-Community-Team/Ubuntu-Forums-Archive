---
title: "neatx-server and SSH Issue"
date: 2010-05-18
forum: Server Platforms
---

### Post by elias832 on 2010-05-18
Im running 32-bit ubuntu 10.04 server, and trying to install neatx-server this is what i get when i run sudo apt-get install neatx-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
neatx-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up neatx-server (0.3.1+svn59-0~ppa1~lucid1) ...
chown: cannot dereference `/var/lib/nxserver/home//.ssh/authorized_keys2.disabled': No such file or directory
chown: cannot dereference `/var/lib/nxserver/home//.ssh/client.id_dsa.key': No such file or directory
chmod: cannot operate on dangling symlink `/var/lib/nxserver/home//.ssh/authorized_keys2.disabled'
chmod: cannot operate on dangling symlink `/var/lib/nxserver/home//.ssh/client.id_dsa.key'
dpkg: error processing neatx-server (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 neatx-server
E: Sub-process /usr/bin/dpkg returned an error code (1)


even though those files exist, when i run ls  

[email]root@server:/var/lib/nxserver/home/.ssh[/email]# ls
authorized_keys  authorized_keys2.disabled  client.id_dsa.key  known_hosts

SSH is working fine. Any help is appreciated.

Thank you in advance.

---

### Post by elias832 on 2010-05-24
removed SSH and ran sudo apt-get install open-ssh
worked like a charm after.

---

### Post by lucacerone on 2010-06-08
Hi,
I've just installed OpenSSH and NeatX and it seems to work.
I could access my Computer from remote and I was quite happy of it.
I just received a warning about the RSA key that is not certified,
what is about???
Thanks for the help,
Cheers, -Luca

---

