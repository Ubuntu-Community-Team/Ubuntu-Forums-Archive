---
title: "[SOLVED] Is this safe?"
date: 2008-08-18
forum: The Cafe
---

### Post by nerd0795 on 2008-08-18
I know this doesn't belong here. But I installed Xubuntu within virtualbox on a friend's computer.  They don't like it.  So I'm wondering if it's safe to fire up xubuntu within virtual box and type the code that deletes all the files within root directory?
It's under virtualbox and was installed by virtualbox.  Will it delete any of Windows XP (the host OS) files?

EDIT: I installed Guest Additions drivers.

EDIT:  It's a code under malicious commands.  and if your wondering why I just don't delete the virtual hard drive it's because it's no fun that way.

---

### Post by eragon100 on 2008-08-18
That is perfectly safe :wink:

---

### Post by RiceMonster on 2008-08-18
Yeah go ahead and do it. Nothing will be damaged. The virtual machine can only access it's own virtual hd.

---

### Post by nerd0795 on 2008-08-18
Thanks I was just making sure.  I thought it wouldn't but since it wasn't my computer I didn't want to damage it.

---

### Post by FuturePilot on 2008-08-18
You might want to unmount any shared folders first.

---

### Post by nerd0795 on 2008-08-18
Huh? It doesn't work I can't execute any of those commands under root. It just says cannot remove /

---

### Post by nerd0795 on 2008-08-18
nvm I fixed it I forgot to run as root. :lolflag:

---

### Post by nerd0795 on 2008-08-18
I did it, but it did not tell me that it worked.  So when I tried to launch terminal it didn't work.  Just a black screen so I rebooted and said Missing configurations files or something like that... and it was dead :(  May you rest in peace xubuntu...

---

### Post by drubin on 2008-08-18
Why not just delete the "virtual" hard drive.  (it is a file) and then re-install it?

---

