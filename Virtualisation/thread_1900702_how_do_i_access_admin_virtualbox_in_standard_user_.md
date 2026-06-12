---
title: "how do i access admin virtualbox in standard user account?"
date: 2011-12-26
forum: Virtualisation
---

### Post by jj97403 on 2011-12-26
I installed virtualbox in my admin account and loaded xp and everything is fine. i can't figure out how to run virutalbox xp in my standard user account. 

Nothing shows up there when I open virualbox. It is almost as if I would have to reinstall xp all over again in the standard user account.

Isn't there someway to share the loaded xp installed on virtualbox, between standard user accounts on the host os, which is ubuntu.

i don't need to share files or folders, i just want to be able to run xp in virtualbox in a standard user account, without having to reload it, because I already have it installed in the admin account on ubuntu.

so

---

### Post by QIII on 2011-12-27
Virtualbox uses an .xml file for configuration.  That file is kept in the /home directory by user. 

With other OSes, you can just add and configure a new virtual machine in a different account and point to the existing .vdi. I can't say for sure if you can do that with XP, but it's worth a try.

When setting up the new machine, be careful to set up the virtual hardware exactly as you did in the other user account -- otherwise your XP may give you grief because the hardware configuration will have changed and try to tell you you need to re-register.

That's the beauty of virtualization.  I have a couple of virtual machines that I access from several machines.  The .vdi is on a network disk.  I can talk to that disk from any machine.  This also means that read/writes on the virtual machine and the host machine happen independently of each other without conflict.  Neither is slowed down by the other.

Edit:  Just happened to think...  I believe that by default the .vdi is also set up in the /home folder, which means the one you have in one account will not be accessible to the other.  You'll have to move the .vdi to a commonly accessible location that all users can get at.  You'll have to re-configure on the first user account, too.  It's been so long since I have been doing this by setting the .vdi file up in a common location that I can't honestly say if you can just C&P it elsewhere.

---

### Post by jj97403 on 2011-12-30
Thanks! 

All way beyond me, a noob forever. :confused: But I will say virtualization is a lot of fun and quite interesting. I had no idea it was so simple.:D

I just decided to delete and install and run from the account I wanted to use it in. No point in me attempting surgery. Thanks again.

---

