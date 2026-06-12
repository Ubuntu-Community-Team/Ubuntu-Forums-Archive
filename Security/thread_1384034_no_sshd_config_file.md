---
title: "no sshd_config file"
date: 2010-01-17
forum: Security
---

### Post by Fika on 2010-01-17
I am trying to modify ssh for more secure setting according to this article which says

**SSH Settings**

 While the SSH daemon is secure enough for most people, some may wish to further enhance their security by changing certain sshd settings. Some settings which could be changed to enhance security are given here. All changes, unless otherwise stated, are made in the /etc/ssh/sshd_config file.  Lines with a pound sign (#) are commented and not read.  To edit this file from a terminal: 
sudoedit /etc/ssh/sshd_config

When I go to edit the file, the path on my ubuntu 9.10 install is /etc/ssh/ssh_config instead of sshd_config.
Is this ssh installed and running by default on ubuntu 9.10? Need I worry about it?

---

### Post by FuturePilot on 2010-01-18
No, the SSH server package is not installed by default on the desktop install.

---

### Post by Sarmacid on 2010-01-18
The ssh client is intalled by default in Ubuntu, which is the config file you're looking at. The other file, *sshd_config*, will appear after you install the ssh server.

---

### Post by Lars Noodén on 2010-01-18
> **Fika said:**
> 
When I go to edit the file, the path on my ubuntu 9.10 install is /etc/ssh/ssh_config instead of sshd_config.
Is this ssh installed and running by default on ubuntu 9.10? Need I worry about it?

Only if you already installed openssh-server and find that sshd_config is not there. ;)

/etc/ssh/ssh_config is to set global defaults for the ssh client.  All Ubuntu desktop setups have this because the OpenSSH client is included in the basic distro.

/etc/ssh/ssh**d**_config is the server configuration file for OpenSSH server.  The server, and thus the server configuration file, is not present unless you add the package [openssh-server](apt://openssh-server).

---

