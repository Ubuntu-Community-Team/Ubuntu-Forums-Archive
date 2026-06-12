---
title: "[SOLVED] cant login as root"
date: 2008-02-24
forum: Server Platforms
---

### Post by ttallos on 2008-02-24
when I try to run this command
sudo apt-get update
I get this error
default(my user ID)not in the sudoers file?
when I try to set it up by typing after exiting the default user
 sudo passwd root
I get login incorrect
I used no password when I setup for the root account...
I cant login as root?

---

### Post by faulkes on 2008-02-24
> **ttallos said:**
> when I try to run this command
sudo apt-get update
I get this error
default(my user ID)not in the sudoers file?
when I try to set it up by typing after exiting the default user
 sudo passwd root
I get login incorrect
I used no password when I setup for the root account...
I cant login as root?

Reboot into recovery mode.

This will provide you a root console, you may then add yourself to the
admin group (which will allow you to sudo).

If no admin group exists (for some reason), create the group in the /etc/group
file, ensuring that you add yourself to it.

Faulkes

---

### Post by ttallos on 2008-02-24
thanks I got into recovery mode....how do I type in the command line to add the user default to the admin group?

---

### Post by Iowan on 2008-02-24
FYI from the **/etc/sudoers** file:> # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
More useful information under **man usermod**.

---

### Post by aysiu on 2008-02-24
[This](http://www.psychocats.net/ubuntu/sudo) may help, too.

---

### Post by ttallos on 2008-02-24
addgroup --system admin
adduser USERNAME admin
echo '%admin ALL=(ALL) ALL' >>/etc/sudoers
this fixed it thanks all.....

---

