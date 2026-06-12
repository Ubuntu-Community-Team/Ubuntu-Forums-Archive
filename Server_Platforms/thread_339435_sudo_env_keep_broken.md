---
title: "sudo env_keep broken?"
date: 2007-01-15
forum: Server Platforms
---

### Post by alexgutteridge on 2007-01-15
Hi,

I've been trying to use the sudoers file to keep my PATH variable intact when I use sudo - to no avail. Perhaps the syntax of my sudoers file is incorrect. Can anyone help? I've pasted my sudoers file and the output of printenv PATH for me (alexg) and when run under sudo. You can see my PATH is not kept by sudo.

alexg@alexgdesktop:~/Desktop$ sudo cat /etc/sudoers
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn
Defaults        env_keep+="PATH"

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

#Backuppc
backuppc ALL = NOPASSWD: /bin/tar
alexg@alexgdesktop:~/Desktop$ printenv PATH
/usr/local/texlive/2005/bin/i386-linux:/opt/ruby/bin:/opt/ruby/lib/ruby/gems/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/opt/SBW-2.5.0/bin:/home/alexg/bin
alexg@alexgdesktop:~/Desktop$ sudo printenv PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

---

