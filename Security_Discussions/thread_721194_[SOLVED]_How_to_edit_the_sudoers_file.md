---
title: "[SOLVED] How to edit the sudoers file?"
date: 2008-03-11
forum: Security Discussions
---

### Post by Arthur Archnix on 2008-03-11
I just can't get this to work. I want all users who are part of the powerdev group to be able to load or unload the psmouse module. I tried writing these two scripts and giving users permissions to use them without being prompted by sudo, but it hasn't worked. Even on my account I get prompted for a password, I'd bet on others it doesn't even load.

Here's my sudoers:
```
arthur@archnix: sudo cat /etc/sudoers
# /etc/sudoers
# Defaults
Defaults        !lecture,tty_tickets,!fqdn
# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL
# Host alias specification
# User alias specification
# Cmnd alias specification
# User privilege specification
root    ALL=(ALL) ALL
powerdev        ALL=NOPASSWD: /usr/bin/scripts/tpad_load.sh
powerdev        ALL=NOPASSWD: /usr/bin/scripts/tpad_unload.sh
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```And here's my scripts:
```
arthur@archnix:/usr/bin/scripts$ cat /usr/bin/scripts/*.sh
#!/bin/sh
#tpad_load.sh
sudo modprobe psmouse

#!/bin/sh
#tpad_unload.sh
sudo modprobe -r psmouse

```I'm open to suggestions. Going through the man page it seems like I should be able to just bypass the scripts altogether, maybe make a group and give everyone in that group permission to load and unload the module psmouse. But I've been beating my head against this for a few days now, and been getting help from the IRC channels, but I just can't make it work.

EDIT: Admins, I thought this was the appropriate forum for this question but if I'm wrong please feel free to move it to the appropriate one. Thanks...

---

### Post by Arthur Archnix on 2008-03-11
This doesn't work either.

```
Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL
%powerdev       ALL=NOPASSWD: /sbin/modprobe -r psmouse
%powerdev       ALL=NOPASSWD: /sbin/modprobe psmouse

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

---

### Post by Arthur Archnix on 2008-03-11
Here's what works:
```
# /etc/sudoers
Defaults        !lecture,tty_tickets,!fqdn
root    ALL=(ALL) ALL
%admin ALL=(ALL) ALL
%powerdev        ALL=NOPASSWD: /sbin/rmmod psmouse
%powerdev        ALL=NOPASSWD: /sbin/modprobe psmouse
```The order is what was messing me up. Sudo reads the file sequentially, so it says everyone in the powerdev group can use these two commands without a password, but then it reads the next line which says anyone who is admin can run any command with a password. Thus, someone who is in the admin group and the powerdev will need a password to run those two commands, unless they are below the %admin ALL=(ALL)ALL line.

After that, setting up the keyboard shortcut is trivial, just be sure to use gksudo instead of sudo.

Thanks to the great guys/gals over on #ubuntu and #ubuntu-offtopic.

If you're wondering why I chose to do it this way, I've found that the xorg-xserver-input-synaptic driver that ships with Gutsy causes a huge number of interrupts/wakeups (about 130/second), which hurts battery life. Thus, I didn't want to use the much simpler synclient workarounds for disabling the touchpad because I've uninstalled it.

---

