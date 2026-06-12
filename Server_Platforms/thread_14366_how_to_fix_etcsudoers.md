---
title: "how to fix /etc/sudoers?"
date: 2005-02-06
forum: Server Platforms
---

### Post by mike_c on 2005-02-06
I messed up my /etc/sudoers file (yes, I edited it with vi, rather than /usr/sbin/visudo-- I don't know whether that's what caused the problem, or whether it was just the syntax of my edit).  I was attempting to make another usr (who is me in another account) elegible for superuser status.  Now I receive a parse error whenever I try to run sudo, including when trying to "sudo /usr/sbin/visudo -f /etc/sudoers."  ARRGGHH!  

How can I fix this, and add my other user to /etc/sudoers?

---

### Post by az on 2005-02-06
Good question.

Try booting with the following added to your kernel line in grub (press escape if your grub menu is hidden to reveal it and use "e" to edit the entry.)  edit the kernel line and add to it:

init=/bin/bash

example:
kernel     /boot/vmlinuz-2.6.8.1-4-386 root=/dev/hdb2 ro quiet splash init=/bin/bash

Then, when at the prompt (you will be root)

nano /etc/sudoers

(CTRL-O to save, CTRL-X to exit)

Lemme know if it works...

---

### Post by Mikael on 2005-02-07
[QUOTE=azz]Lemme know if it works...[/QUOTE]
It works just fine! I had to do it just now... I just had one user in the system and decided to change its name and password. That worked out fine, but the only user in the system lost its sudo privilege... Not good.

kernel /boot/vmlinuz-2.6.8.1-4-386 root=/dev/hdb2 ro quiet splash **rw init=/bin/bash**

Added the above text in bold at startup and came directly to a promt with root privilege. Edited the sudoers file and rebooted. Done.

Thanks a load! :grin:

---

### Post by coolclassic on 2005-06-21
I have the same problem after editing sudoers. I am able to edit file and I deleated the entries I made but I still get the parse problem. Would someone show me what is wrong, here is my file.

ï»¿# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin	ALL=(ALL) ALL

---

### Post by az on 2005-06-21
[QUOTE=coolclassic]I have the same problem after editing sudoers. I am able to edit file and I deleated the entries I made but I still get the parse problem. Would someone show me what is wrong, here is my file.

ï»¿# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges


%admin	ALL=(ALL) ALL[/QUOTE]


Boot into recovery mode.  It is simpler.

Your sudoers file should look like this:  (you have some garbage.  Change username to your user name)

#! /etc/sudoers

root	ALL=(ALL) ALL

username	   ALL=(ALL) ALL

---

### Post by LordHunter317 on 2005-06-21
No, he shouldn't change his sudoers file to what you recommend.

It's setup the way it is for a reason.

All he needs to do is clear the UTF-8 garbage at the start of the file; I'm 99% certain that's what's causing it.

And to give a user sudo access equivalent to the first user's on Ubuntu Hoary, just add the user to the admin group.  To do this on the command line, do:```
sudo adduser <user> admin
```

---

### Post by coolclassic on 2005-06-22
Thanks LordHunter you were 100% correct. I used Oepen office to edit file and this must of caused the garbage. In case some asks Kate was not loading and I hate Vi. The next time I will create a duplicate file this would of save alot of hasle.

---

### Post by gksmithlcw on 2007-03-10
So... I have a broken sudoers file and I used the 'init=/bin/bash' GRUB method and booted into a shell as root.

However, when I 'nano /etc/sudoers' and edit the file and hit ^o to save, I receive an error stating that the file system is Read Only.

Any suggestions???

G.K.

**edit**

I got myself patched up by using the recovery mode.

Thanks,

---

### Post by jvc26 on 2007-07-04
Very late I know but I have only just dropped into this thread looking for something else, but basically rather than ```
nano /etc/sudoers
```you need```
sudo nano /etc/sudoers
``` as without sudo privileges you can only access the file as read-only, hence the error message you received.
Il

---

### Post by jack@tortuga on 2007-07-05
Note that he booted into single-user mode as root. Sudo shouldn't have any effect in this case. The error message wasn't that the file was read-only, but the file**[COLOR="Red"]system[/COLOR]** was read-only.

---

