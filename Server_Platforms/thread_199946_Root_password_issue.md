---
title: "Root password issue"
date: 2006-06-19
forum: Server Platforms
---

### Post by mssever on 2006-06-19
I've just switched to Ubuntu from RedHat 7 and Ubuntu seems to have two root passwords. The root password I created using passwd is as I expected. However, when GNOME apps (such as synaptic) require the root password, they require my normal user password :confused:. Same goes for sudo. How come it doesn't use my root password?

In other words, su uses the root password and sudo uses my normal password.

Maybe this is an issue with sudo? I didn't have sudo on my RH installation, so I'm not very familiar with it.

---

### Post by LordHunter317 on 2006-06-19
Ubuntu never asks you for a root password during installation.   You're supposed to use sudo for everything, and the applications have been written or patch to function in that manner.

---

### Post by mssever on 2006-06-19
Isn't that a huge security hole? Why would you circumvent the root password? Couldn't anybody, then, become root?

---

### Post by fuelman on 2006-06-19
Check this out : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by DirtDart on 2006-06-29
[QUOTE=mssever]Isn't that a huge security hole? Why would you circumvent the root password? Couldn't anybody, then, become root?[/QUOTE]

By default, only the first user that is created has sudo access.  The assumption is that this user is also the installer, so you should have the power to do admin-type stuff on the system.

---

### Post by RavenOfOdin on 2006-06-29
Actually, a root account is created with the expert install, but I think you should be able to manually add yourself to sudoers and then via the user account you added do "sudo passwd -l root" to lock the account.

---

