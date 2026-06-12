---
title: "openssh: how to enable write permissions in chroot directory ?"
date: 2011-01-11
forum: Server Platforms
---

### Post by lowrider2025 on 2011-01-11
Does anyone know how write permissions can be enabled in the chroot directory ? By default openssh will not work when write permissions are enabled for users other than root. I need write permissions for users uploading files to /var/www . I do not want to have to copy files users uploaded under their own home directory under /var/www. I hope someone had the same issue and has found a way to resolve it.

btw: 
1) all users connecting have /bin/false as shell
2) iptables only allows ssh access from users' ip & mac address
/etc/ssh/sshd_config:
PermitRootLogin no
PasswordAuthentication no

---

### Post by tech-hero on 2011-01-11
try typing sudo before the commands... it will ask you the password...

---

### Post by lowrider2025 on 2011-01-11
> **tech-hero said:**
> try typing sudo before the commands... it will ask you the password...

thx for the reply. But the problem is that when I use chmod 764 for /var/www , openssh does not let users log in because the directory permissions are 'wrong'. It will not log you in with write permissions enabled for group or others. It needs to be 700 or 755 or 744 or... . But cannot be 76X or login is denied by openssh server.

---

### Post by lowrider2025 on 2011-01-12
found a solution.Albeit not the solution I preferred,but I guess there is no clean and safe way of doing this.

fyi: this is set in a LAN environment,so no internet access. Or maybe briefly for updating packages.

the way it works now:
/etc/ssh/sshd_config

PermitRootLogin yes

/etc/passwd
change uid of ssh-users to uid of root (0)

firewall restricts ssh access to only ip and mac address of the ssh-users

---

