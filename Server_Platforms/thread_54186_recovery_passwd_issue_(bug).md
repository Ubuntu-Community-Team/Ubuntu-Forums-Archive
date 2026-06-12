---
title: "recovery passwd issue (bug?)"
date: 2005-08-03
forum: Server Platforms
---

### Post by BipolarLogic on 2005-08-03
I just installed Ubuntu for a friend and he was concerned about the lack of a root user, so as an experiment we booted into recovery mode to see what we could do.

I issued the command 'passwd user' and changed his password.  I then started X and logged in as him with my new password.  I basically just wanted to see if I could gain administrative access.

The weird part:  this seemed to enable the root account on his machine.  Also, when he tried to run a program which required sudo, the app would hang or else say his password was incorrect or do something else weird.  I tried to fix this with 'sudo passwd -l root' but apps would still not request a sudo password or else would hang.  I ended up re-installing Ubuntu to fix the problem.

Is there anything inherently evil about changing passwords from recovery mode?  Has anyone had similar problems, or am I just imagining things?

---

### Post by amohanty on 2005-08-03
Can you do an su with the new passwd?

>> su

enter the password you just set and launch synaptic.

AM

---

### Post by BipolarLogic on 2005-08-03
yeah, which is what led me to believe I somehow created the root account on accident.

It was my belief that 'su' wouldn't work unless the root acount was enabled with 'sudo passwd root'.

It's as if I inadvertently changed the root's password when I changed his user account's password, and thereby created the root account.  But when I tried to disable the root account with 'sudo passwd -l root' it didn't fix the weird behavior of the apps that require sudo.

I assume it is possible to change one's own password without causing these problems, so why would changing someone else's password thru the recovery mode cause problems?

---

### Post by amohanty on 2005-08-03
When in recovery mode you are pretty much root. Have you looked at the sudoers list and checked if it has changed?

AM

---

### Post by BipolarLogic on 2005-08-03
No, and unfortunately I have already re-installed so I can't check.

I was able to sudo with his user account though.  For example, I tried 'sudo passwd -l root' to remove the root account after logging in normally.  I suppose it is possible that the sudoers list was modified somehow.  I'll admit I'm afraid to try to repeat the incident on my laptop.

Does anyone have a fresh install they'd be willing to test this on?  I'm curious to see if this is a recurrent problem or just a fluke.

---

