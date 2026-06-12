---
title: "Sudoers How to enable just a command or 2 ?"
date: 2008-01-28
forum: Server Platforms
---

### Post by member54321 on 2008-01-28
[INDENT]I have created a user family and used the family group as a place
to share data between family members on our linux box.

A shared folder of DOS files is also there for use. But sometimes
it's permissions go bad. I would like to allow each member of the
family group to run a command to fix these problems. 

I am trying to figure out how to add the group  family to the
sudoers file, but ONLY for specific commands NOT fill access
the only examples I have found are full access.

Below is a copy of my /etc/sudoers file 

*Skip to the comment* ### Below Here is what I am trying to add and does not work ###

my unsucessful ](*,) attempt do anyone know how to fix this.


[/INDENT]

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

### Below Here is what I am trying to add and does not work ###

# Members of Family May Chmod /home/family/Shared/DOS/C: to fix perms

%family  ALL=NOPASSWD:chmod -R 775 /home/family/Shared/DOS/C:
%family  ALL=update_menus
[INDENT]
**END**[/INDENT]

---

### Post by FaBi3ttO on 2008-01-28
try to define an alias for your command, for example :
```

# Cmnd alias specification
Cmnd_Alias          FIXPERM = chmod -R 775 /home/family/Shared/DOS/C:

# User privilege specification
root ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

### Below Here is what I am trying to add and does not work ###

# Members of Family May Chmod /home/family/Shared/DOS/C: to fix perms

%family ALL=NOPASSWD:FIXPERM

```
If it doesn't work try this:
- create an alias for your command, like fixperm (google for bash aliasing)
then try put that alias in the sudoers ruleset.
Hope it helps,

---

