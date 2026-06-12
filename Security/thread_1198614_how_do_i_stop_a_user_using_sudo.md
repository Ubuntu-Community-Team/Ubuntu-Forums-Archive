---
title: "how do i stop a user using sudo"
date: 2009-06-27
forum: Security
---

### Post by jarrah-95 on 2009-06-27
im trying to set up ubuntu for someone that cant use windows and whould like to remmove them form using sudo as they might do something to destroy the computer (they have know idea what they are doing) can i do this without disabeling updates and add/remove userbility
thank you

---

### Post by philcamlin on 2009-06-27
dont tell them the root password

---

### Post by surfed on 2009-06-27
dont make them part of the admin group

---

### Post by HermanAB on 2009-06-27
Edit /etc/sudoers

---

### Post by sisco311 on 2009-06-27
> **philcamlin said:**
> dont tell them the root password

by default, the root account password is locked.

> **jarrah-95 said:**
> im trying to set up ubuntu for someone that cant use windows and whould like to remmove them form using sudo as they might do something to destroy the computer (they have know idea what they are doing) 

> **surfed said:**
> dont make them part of the admin group

+1

> **jarrah-95 said:**
> can i do this without disabeling updates and add/remove userbility
thank you

for this you have to edit the sudoers file and append it with something like:
```
*username *ALL=(ALL) /usr/sbin/synaptic
```

For more info read this:
[thread=1132821]HowTO: Sudoers Configuration[/thread]

EDIT: always edit the file with the *sudo visudo* command.

---

### Post by jarrah-95 on 2009-06-27
i dont think theyre in the admin but i can still use sudo when i try also if i removed them from the sudoers file whouldent that stop them from using the updates and add/remove

---

### Post by philcamlin on 2009-06-27
they cant use updates if they dont know the admin password. :popcorn:

---

### Post by sisco311 on 2009-06-27
> **jarrah-95 said:**
> i dont think theyre in the admin but i can still use sudo when i try also if i removed them from the sudoers file whouldent that stop them from using the updates and add/remove

By default, only members of the admin group may gain root privileges. This is the relevant part in the sudoers file:
```
%admin ALL=(ALL) ALL
```

If you want to allow user *bob* to use update-manager, add/remove programs(gnome-app-install) and synaptic package manager follow this steps:
[list=i]
[*]remove *bob* from the admin group:
```
sudo deluser bob admin
```


[*]edit the sudoers file:
```
VISUAL=gedit sudo -E visudo
```

[*]add this line to the end of the file:
```
bob ALL=(ALL) /usr/sbin/synaptic
```
save the file and exit.

[/list]


your sudoers file should look like this:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

bob ALL=(ALL) /usr/sbin/synaptic

```

---

### Post by cariboo on 2009-06-27
> **philcamlin said:**
> dont tell them the root password

Ubuntu disables the root account. There is no root password.

---

### Post by cariboo on 2009-06-27
Create a limited account for the user. Go to System-->Administration-->Users & Groups, to setup a user and set what permissions he/she needs. To make it easier on them you may want to set up autologin too.

---

### Post by bodhi.zazen on 2009-06-28
Thank you [sisco311]("http://ubuntuforums.org/member.php?u=244665") for your explanations on this thread.

As a reference :

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo")

---

