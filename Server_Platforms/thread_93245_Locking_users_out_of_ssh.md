---
title: "Locking users out of ssh"
date: 2005-11-21
forum: Server Platforms
---

### Post by mega on 2005-11-21
I need to lock out a user from ssh

they only scp me files

I added "logout" to the end of thier profile, works great


only problem they can simply erase the profile and create a new one without the logout line


I did chgrp/chuser to root/root and chmod 444 the file

but they still can overwrite


what am I missing?  Or is there a better way to do this?

---

### Post by mega on 2005-11-21
Found an easy way, the scponly shell, locked them down nice


now any way to lock them into thier home folder when they scp into my server?

---

### Post by Glut on 2005-11-21
Correct file/directory permissions will achieve this. Alternatively, a chrooting version of sshd will also achieve this. Do a search for 'chroot ssh'.

---

### Post by mega on 2005-11-22
[QUOTE=Glut]Correct file/directory permissions will achieve this. Alternatively, a chrooting version of sshd will also achieve this. Do a search for 'chroot ssh'.[/QUOTE]


I installed a chroot shell, but heck if I can figure out how to use it

anyone set this up?

---

### Post by LordHunter317 on 2005-11-22
rssh will achieve both of your goals.

---

