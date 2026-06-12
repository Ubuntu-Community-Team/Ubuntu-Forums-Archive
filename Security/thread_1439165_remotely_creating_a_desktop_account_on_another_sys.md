---
title: "remotely creating a desktop account on another system"
date: 2010-03-25
forum: Security
---

### Post by boondocks on 2010-03-25
I am at my own desktop and I have root access on my own desktop.

I also have root access on a Desktop Ubuntu system (192.168.5.10) on the LAN.
I need to create another desktop user account on that 192.168.5.10 system.

So I logged into that system with:
 [COLOR="Blue"]ssh -Y  myself@192.168.5.10[/COLOR]
Then I did:
 [COLOR="Blue"]sudo users-admin[/COLOR]  

This brings up the **Users Settings** but the **Add User** and **Unlock** buttons are disabled.
How do I enable these buttons?

---

### Post by mikewhatever on 2010-03-25
You could add users with <sudo adduser>. See <man adduser> for more options.

---

### Post by boondocks on 2010-03-26
> **mikewhatever said:**
> You could add users with <sudo adduser>. See <man adduser> for more options.

Yes, that is true.
(I have done that in the past.)

But I want the new desktop user to inherit all the attributes of the default desktop user.
That way all these non-technical desktop users have a consistent look-and-feel.
They can learn from each other.

---

### Post by mikewhatever on 2010-03-26
Are you saying that creating users with 'adduser' somehow gives them non-default profile? I just tried running <sudo users-admin> from within Ubuntu, and the expected window opened, but there was no unlock button. Odd.

---

### Post by boondocks on 2010-03-26
> **mikewhatever said:**
> Are you saying that creating users with 'adduser' somehow gives them non-default profile? 
No.  I am saying that creating a user from the command line using 'sudo adduser' creates a user account but the attributes are not the same as when you create a user account using 'sudo users-admin'.
In other words, 'sudo adduser' creates (just) a user account whereas 'sudo users-admin' creates a user account such that when that user logs into the desktop he gets the typical desktop. Which includes the Desktop folder, Downloads folder, etc.


> **mikewhatever said:**
> I just tried running <sudo users-admin> from within Ubuntu, and the expected window opened, but there was no unlock button. Odd.
I have sudo access on this system.
The unlock button is visible, if I am (local) sitting in front of the system.
But when I (remotely) log into that system with:
[COLOR="Blue"]ssh -Y myself@192.168.5.10[/COLOR]
Then I do:
[COLOR="Blue"]sudo users-admin[/COLOR] 
This brings up the Users Settings but the Add User and Unlock buttons are disabled.

---

### Post by adam814 on 2010-03-28
Is 'myself@192.168.5.10' a user in the admin/sudo group on 192.168.5.10?  Also, have you tried using gksu instead of sudo?

---

