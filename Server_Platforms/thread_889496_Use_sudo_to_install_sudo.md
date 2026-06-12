---
title: "Use sudo to install sudo?"
date: 2008-08-14
forum: Server Platforms
---

### Post by SoundFriend on 2008-08-14
Not a problem, but this amused me.  Somehow sudo had been removed from my system.

```
sudo apt-get update
The program 'sudo' can be found in the following packages:
 * sudo
 * sudo-ldap
Try: sudo apt-get install <selected package>
-bash: sudo: command not found

```

A bit like 'keyboard not found, press any key to continue'

John

---

### Post by null byte on 2008-08-14
:| I don't know what to tell you, maybe a more experienced member will tell you what's with that.

But you can use the **su** command to get sudo back.

---

### Post by mcduck on 2008-08-14
No, you can't. "su" would require an active root account to work, as it asks for root user's password, not the current user's.


But anyway, the solution is to boot into the recovery mode from Grub menu, which will get you into root shell. then just run "apt-get install sudo".

(I must admit that this is a bit trickier situation to solve than the "keyboard not found"-error you mentioned. Which, actually, is perfectly logical when you know that the machine can't continue the boot process until the keyboard is attached..)

---

### Post by null byte on 2008-08-14
> **mcduck said:**
> No, you can't. "su" would require an active root account to work, as it asks for root user's password, not the current user's.


But anyway, the solution is to boot into the recovery mode from Grub menu, which will get you into root shell. then just run "apt-get install sudo".
My bad, sorry mcduck.

---

### Post by SoundFriend on 2008-08-14
> **mcduck said:**
> No, you can't. "su" would require an active root account to work, as it asks for root user's password, not the current user's.


I had an active root account, so not a problem for me to fix
> 
But anyway, the solution is to boot into the recovery mode from Grub menu, which will get you into root shell. then just run "apt-get install sudo".

Thnaks, useful to know if it happens again..

John

---

