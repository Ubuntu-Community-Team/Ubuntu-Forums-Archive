---
title: "User Groups fail - - WIN!"
date: 2010-10-24
forum: Security
---

### Post by Linus_Sandro on 2010-10-24
Hello everyone, today I did the most n00bish thing I've ever done on ubuntu: I quited my user from the 'sudo' group, i wasn't able to get any admin privileges that sudo gives and as my user is the only one in the system (root is locked), i wasn't able to set back my user into sudo group.
I solved it by modifying 'group' and 'group-' files in the /etc/ folder being root in the live CD. i spent about 1 hour; but WIN!!!
Should i report this as a bug? (if there's only one user and root is locked, as default in ubuntu,  there's no waring for changing privileges of the user)
Cya.

---

### Post by SavageWolf on 2010-10-24
No, but if a program were to do it automatically them yes. A warning would be a good idea though...

---

### Post by CharlesA on 2010-10-24
It's not a bug. If you remove yourself from the admin group, you lock yourself out of using sudo.

To fix it, you need to drop to a root prompt in recovery mode (hold shift to access the GRUB menu) and add yourself back to the admin group.

---

### Post by sisco311 on 2010-10-25
> **CharlesA said:**
> It's not a bug. If you remove yourself from the admin group, you lock yourself out of using sudo.


Yes and no. 

In general, you have to start a new login session in order the new group membership to take effect, but policykit reads the groups directly from /etc/groups. So if you remove your user from the admin group, you can still use sudo until you log out, but you can't use policykit.

---

### Post by CharlesA on 2010-10-25
> **sisco311 said:**
> Yes and no. 

In general, you have to start a new login session in order the new group membership to take effect, but policykit reads the groups directly from /etc/groups. So if you remove your user from the admin group, you can still use sudo until you log out, but you can't use policykit.

Interesting.

That's (sort of) the same way it works in Windows as well - you need to log out and back in again to have the new permissions take effect.

Thanks for the info. :)

---

