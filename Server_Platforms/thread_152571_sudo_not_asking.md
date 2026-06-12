---
title: "sudo not asking"
date: 2006-03-30
forum: Server Platforms
---

### Post by berger on 2006-03-30
hello!

i got this strange problem today..

sudo does not ask a password when trying to do something which requires
superuser privilege .. for e.g sudo gedit /etc/fstab..

Before this problem I edited the sudoers file, but with a wrong editor 
(it needs to be edited with visudo as root) and messed up the sudoers file
and sudo didn't work at all. After that i made a new /etc/sudoers file with the
command visudo -f sudoers as root, and it only has thease lines:

Defaults     !lecture,tty_tickets,!fqdn

root            ALL=(ALL) ALL

%berger      ALL=(ALL) ALL

and visudo didn't report of any errors so the sudoers file is accepted now.
But sudo doesn't ask any password when doing a sudo command. 
I red someones post on a debian forum and it said that the problem would
be that my user is in the 'sudo' group, but it is in the group 'berger' which is
my account name as well. i also tried adding different groups to the sudoers
and tested sudo with a user in those groups without any luck.



i don't know what has happened. A few days ago things just worked fine.

ps. yesterday the sudoers file looked exatly as it looks now, instead of the 'berger' group
there was the 'admin' group with all privileges, but it didn't work either today after i modified the old file/created the new file.

---

### Post by aysiu on 2006-03-30
This is what your /etc/sudoers file should look like: ```
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

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL
``` These are the groups you should be in: > berger adm dialout cdrom floppy audio dip video plugdev users lpadmin scanner admin

---

### Post by berger on 2006-03-31
Thanks for the info.

Now sudo asks the password for the first time it is used, but before it asked the
password every time. That ain't right is it?

---

### Post by Zimmer on 2006-03-31
The authorisation will last for a set time, then lapse so that you need a password for sudo again, this is normal and can be configured to suit.. default is 15 minutes, but as always there is documentation on it...  type man sudo  in a terminal to see it...

---

### Post by frodon on 2006-03-31
if you want to remove this 'grace period' and have to type your password each time you use sudo, add this line in your /etc/sudoers file : ```
Defaults:ALL timestamp_timeout=0
```

---

### Post by berger on 2006-03-31
Yep. These tips helped me out!

Thank you everyone! 
I'm kinda new to linux :D

---

