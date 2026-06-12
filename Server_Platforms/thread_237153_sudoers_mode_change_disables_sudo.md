---
title: "sudoers mode change disables sudo"
date: 2006-08-15
forum: Server Platforms
---

### Post by ZaphodNE on 2006-08-15
Sequence of events......

1.  Installed kvpnc
2.  Viewed doc on kvpnc website showing how to start vpnc thru the gui without being sudo.  Requires changes to /etc/sudoers.
3.  Attempt to edit /etc/sudoers as sudo, but mode is set to 0440.
4.  As sudo, chmod 0660 sudoers
5.  Every further attempt to use sudo complains that mode of sudoers is set to 0660 and should be 0440.
6.  sudo is effectively rendered dead.

Does anyone know how to get out of this??????  Please help!

---

### Post by mlind on 2006-08-15
/etc/sudoers file should be only edited with **visudo**..

You need to gain root privileges to revert the changes you made to /etc/sudoers file permissions. Easiest way is to probably boot using recovery option on GRUB menu, or adding 1 as kernel parameter.

You shouldn't usually need to change file permissions outside your $HOME folder. Think twice before doing so at least.

---

### Post by ZaphodNE on 2006-08-15
My humble apoligizes, but could you please provide more specific info on your suggestions.  I have no doubt your directions will work, but I need more detail.  I'm sorry....a bit of a newbie I guess.  If you don't mind, please respond.

Many thanks!

---

### Post by ZaphodNE on 2006-08-15
I don't know how to boot as you suggest, and the 'set to 1' thing is also a mystery.  Please elaborate.  Thank you.

---

### Post by ZaphodNE on 2006-08-15
Discovered recovery boot mode as you suggested and it seems to have been the solution.  That is something that was unknown to me.....thank you very much!!!

Very kind of you to help.  I learned much tonight.

Many thanks!!

---

### Post by mlind on 2006-08-16
> **ZaphodNE said:**
> Discovered recovery boot mode as you suggested and it seems to have been the solution.  That is something that was unknown to me.....thank you very much!!!

Very kind of you to help.  I learned much tonight.

Many thanks!!

Hopefully you got this sorted out. Launching **visudo** once as root should correct any file permissions problems.

---

