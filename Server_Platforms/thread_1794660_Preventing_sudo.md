---
title: "Preventing sudo"
date: 2011-07-01
forum: Server Platforms
---

### Post by Loki57701 on 2011-07-01
Hi all, 

I have a box with about 30-40 users on it, and I need to prevent a certain group of users from using sudo at all. Is this even possible.

---

### Post by haqking on 2011-07-01
> **Loki57701 said:**
> Hi all, 

I have a box with about 30-40 users on it, and I need to prevent a certain group of users from using sudo at all. Is this even possible.


make sure those users are not in the Sudo group or admin group ?

if they are then why do you want to prevent them from using Sudo ?

---

### Post by collisionystm on 2011-07-01
> **Loki57701 said:**
> Hi all, 

I have a box with about 30-40 users on it, and I need to prevent a certain group of users from using sudo at all. Is this even possible.


Yup.

Review your /etc/sudoers file

```
sudo nano /etc/sudoers
```

My 11.04 looks like this
> 
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults    env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo    ALL=(ALL:ALL) ALL


Those are the requirements to sudo

just make sure your users do not belong to the root, admin or sudo group.

OR, you can change your sudoers file so it looks for a different group to use it.

Just make sure you don't lock yourself out!

---

### Post by Rubi1200 on 2011-07-01
The correct way to edit sudoers is following the instructions here:
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by ahears on 2011-07-01
NEVER USE 'nano' DIRECTLY ON THE '/etc/sudoers' FILE! Use the command '**_sudo visudo_**'  IT WILL OPEN THE '/etc/sudoers' FILE AUTOMATICALLY, AND Do NOT cut and paste text entries from the GUI, as it will corrupt the file.

It should look like: 

> 
[COLOR=Black]#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults    env_reset

# Host alias specification [/COLOR][COLOR=Black]

# User alias specification [/COLOR][COLOR=Black]

# Cmnd alias specification [/COLOR][COLOR=Black]

# User privilege specification [/COLOR][COLOR=Black]
root    ALL=(ALL:ALL) ALL

[COLOR=Red]# Members of the admin group may gain root privileges [/COLOR][/COLOR][COLOR=Black][COLOR=Red]
%admin ALL=(ALL) ALL[/COLOR]

[COLOR=Magenta]# Allow members of group sudo to execute any command [/COLOR][/COLOR][COLOR=Black][COLOR=Magenta]
%sudo    ALL=(ALL:ALL) ALL[/COLOR]

[/COLOR][COLOR=Black]

After this, make sure that the Users are not in the Admin group and not in the Sudo group.
This is self explanatory but here are some links below to editing 'Rootsudo' and fixing it if you break it while editing. [COLOR=Blue]Sorry if this is repetitive but do not use 'nano' directly on the file. :([/COLOR]
[/COLOR]

---

