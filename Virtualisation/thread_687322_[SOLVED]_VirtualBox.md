---
title: "[SOLVED] VirtualBox"
date: 2008-02-04
forum: Virtualisation
---

### Post by rchokler on 2008-02-04
I'm trying to install virtual xp on  virtual machine but i have small problem
can you help me please ?

---

### Post by Dekunuts on 2008-02-04
you have to go into user / group administration in the system menu and add yourself to the vbox group if i remember correctly.

---

### Post by ichbinesderelch on 2008-02-04
as the messages states you just have to add your user to vboxusers grp, you could easily do this with gpasswd -a USERNAME vboxusers, after that you have to login again to apply changes! (EDIT)

---

### Post by p_quarles on 2008-02-04
Moved to Virtualization forum.

The exact name of the group you need to add your user to is "vboxuser."

---

### Post by rchokler on 2008-02-04
I'm very new with Ubuntu ,my apologizing for some silly questions
i tried to do you suggestion but

alon@alon-laptop:~$ gpasswd -a alon vboxusers
gpasswd: Permission denied.

---

### Post by p_quarles on 2008-02-04
Try this instead:
```
sudo adduser alon vboxusers
```
Log out, then back in for the change to take effect.

---

### Post by rchokler on 2008-02-04
Great work, thak you very much
can you explain me what was i doing :)
and what is the different between those two sentence you wrote ?

---

### Post by ichbinesderelch on 2008-02-04
the only difference was that you executed the command with superuser rights (kinda as root), you don't have permission to edit users to group as normal user

---

### Post by p_quarles on 2008-02-04
> **rchokler said:**
> Great work, thak you very much
can you explain me what was i doing :)
and what is the different between those two sentence you wrote ?
Sure. The command I gave you goes like this:
sudo = run command as root
adduser = just what it sounds like ;)
alon = name of user to modify
vboxusers = name of group to add user alon to

---

