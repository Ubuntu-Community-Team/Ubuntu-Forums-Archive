---
title: "First installed user appropriate for general use?"
date: 2011-09-20
forum: Security
---

### Post by altesk on 2011-09-20
When Ubuntu (in my case, 11.04) is first installed onto a computer, the setup creates one user. That user has a custom set of powers and privileges greater than an ordinary user.

From a security standpoint, is it OK for the person who installed the system to always log in as that user? Or should that person create a second user with minimal priveleges, and log in as this second user to do ordinary day-to-day work like using the web browser and emailing and so on?

Are there considerations besides security that affect this decision?

I welcome your informed opinions. Thank you.

---

### Post by mikewhatever on 2011-09-20
The default policy is considered a good compromise between restriction and ease of use. If 'that person' feels the need to work as a more restricted user, the tools are in place to achieve that. So, ultimately, it's up to 'that person'.

---

### Post by OpSecShellshock on 2011-09-21
The first user has to specifically elevate privileges in order to have those enhanced abilities, which most people won't need or want to do when engaging in regular desktop user activities like web browsing. It should be fine on a single-user system to just use that account.

---

### Post by sanderd17 on 2011-09-21
In classical linux installations, there was a "root" user. That user could do everything without warning.

Ubuntu disabled the root user account and created sudo (super-user-do). Someone who has sudo rights can become root for a short time (to do needed maintenance). But you have to give your password to become root.

This way, it is safe (when you get asked for you password and don't expect it, don't give your password) and it is convenient (you don't need to log out in order to become root).

---

### Post by bodhi.zazen on 2011-09-21
> **altesk said:**
> When Ubuntu (in my case, 11.04) is first installed onto a computer, the setup creates one user. That user has a custom set of powers and privileges greater than an ordinary user.

From a security standpoint, is it OK for the person who installed the system to always log in as that user? Or should that person create a second user with minimal priveleges, and log in as this second user to do ordinary day-to-day work like using the web browser and emailing and so on?

Are there considerations besides security that affect this decision?

I welcome your informed opinions. Thank you.

It has been up to now. Nothing wrong with creating a second non-privileged account for daily operations either. Up to you.

---

### Post by dfarrell07 on 2011-09-21
The most I would do, along these lines, is to remove the root account. That would give the users in the sudoers file sudo access, but not allow anyone to become root with 'sudo -i' or whatever. I saw some recommendations to do this with servers, when trying to really lock them down.

---

### Post by Lars Noodén on 2011-09-22
[privilege separation](http://en.wikipedia.org/wiki/Privilege_separation) is a good thing and adding a second user helps there.

---

### Post by bodhi.zazen on 2011-09-22
> **dfarrell07 said:**
> The most I would do, along these lines, is to remove the root account. That would give the users in the sudoers file sudo access, but not allow anyone to become root with 'sudo -i' or whatever. I saw some recommendations to do this with servers, when trying to really lock them down.

I do no think you can remove the root account. You can lock down the root account, in particular with selinux, but ultimately you need a root account to be able to sudo -i to.

I suggest you re-read your reference material.

---

### Post by Dangertux on 2011-09-22
I'm with bodhi.zazen on this one you can't just REMOVE your root account bad things will start to happen or rather good things will fail to happen. You can restrict it greatly, however the default configuration Ubuntu ships in , in terms of user privileges is fine.

You could in theory debate that because your user is a sudoer that's one less password to crack to get root privileges. Then again you could conversely say a remote attacker would have to guess at a username as opposed to root which all unix-like systems will have. Besides you should have a strong password anyway so...6 in one half dozen in the other?

---

