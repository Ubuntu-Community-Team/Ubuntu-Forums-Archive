---
title: "How root can unlock desktop"
date: 2008-08-14
forum: Security
---

### Post by alSee on 2008-08-14
I use Ubuntu Hardy 8.04 with Gnome desktop.

When I lock the computer (with Ctrl+Alt+L) it is possible to unlock only with current user password. Or someone may start another session.
What have I to do for Administrator (with root privileges) to be able to unlock CURRENT (locked) user session?

---

### Post by meindian523 on 2008-08-14
Login as admin and do what you want.Root(what you call Administrator) doesn't need to unlock anyone's desktop.

---

### Post by alSee on 2008-08-14
It doesn't need for root to login another session. He has its own computer.
Root must be able to interact with apps running on user's desktop.

It was possible in RHEL, why in Ubuntu is NOT?

---

### Post by meindian523 on 2008-08-14
Is this a networked environment?

---

### Post by alSee on 2008-08-14
Yes. And root can login remotely via ssh.
But if user runs GUI which controls remote system that needs to be released correctly (not just to kill GUI but to send some commands by GUI). Or if user through ssh-terminal locks some device on remote host. Then user may lock desktop. In this case root must have an ability to unlock desktop and to finish GUI controlling remote system or to release remote device vis ssh.

---

### Post by cariboo on 2008-08-14
Have a look here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

For an explanation why Ubuntu is different from other distros concerning root.

Jim

---

### Post by alSee on 2008-08-14
I've read it and found out nothing new. There is a phrase about unlocking root password in special cases of office/network environment. I have such case. I've unlocked root password. But problem with locking workstation.
I amn't talking about "return root to Ubuntu distro", I just want to do special things to get availability unlocking desktop by root. Maybe another screensaver or something similar...

---

### Post by meindian523 on 2008-08-15
I have no competence with a networked environment.You will have to look to others for help.The maximum I know is that you can kill all user processes after logging in as root.Other than that,interaction with a GUI a user opened?I give up.

---

### Post by alSee on 2008-08-15
**meindian523**, thanks for response anyway.

Has anyone ideas?

---

### Post by dentaku65 on 2008-08-15
As far as I know the root user cannot lock (and maybe unlock) a machine in GUI mode, at least under Gnome environment; in KDE root can lock the machine in GUI mode. For Gnome you can use an external tool like xlockmore (former xlock) instead the xscreensaver used in Gnome... or install Kubuntu :).

---

