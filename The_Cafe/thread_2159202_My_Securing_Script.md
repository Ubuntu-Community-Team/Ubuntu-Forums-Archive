---
title: "My Securing Script"
date: 2013-07-02
forum: The Cafe
---

### Post by ki4jgt on 2013-07-02
After hunting around in Ubuntu and on ubuntu websites, this is what I've come up with:

The program makes these changes system-wide (for EVERY user).

- Removes unity-lens-shopping
- Places 750 on ALL $HOME directories
- Disables the recently accessed files list
- Prevents Empathy from auto-connecting to services
- Turns off Empathy location services
- Removes image thumbnails
- Turns on auto-update

to run, simply make the file an executable and:
sudo ./secure.py
Logout and log back in for the full effect.

What do you guys think?

---

### Post by TheFu on 2013-07-02
It is a start, but I'd change many more things. By default, every user is added to their own, unique group, so managing the umask usually doesn't help much for real security.  If groups are used, like for normal UNIX systems, it is common to use the g+rws setting on group specific directories to keep them open and with the correct gid by default.  This implies that all the people on the system understand groups and group permissions, which is NOT usually the case.

I'd install a number of packages that help with security too, like **fail2ban** for ssh login controls.  I'd always turn on the firewall too and setup key-based ssh connectivity.  Securing a system is a very system specific task. Each is a little different.  My friend Bob Toxen wrote the book on **Real World Linux Security** [http://www.realworldlinuxsecurity.com/](http://www.realworldlinuxsecurity.com/) . Highly recommended.  The O'Reilly books on **Practical UNIX & Internet Security** are useful too.

Basically, for every service provided on a system, there are extra security measures to install and configure. Defaults are seldom what is desired for a secure system.

**Versioned Backups** are more important for security than anything else that I know.  A mirror as a backup is NOT enough.  If you can't restore a system to the same exact state as last week or last month, then the backups are a failure, IMHO.  Admins seldom discover a break-in on the first day, so being able to go back a few weeks at least is critical.

I also capture the system hardware and all installed packages (OS, ruby-gems, perl-cpan) daily, which are included in my backups.  Unexplained changes are a signal.

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) is full of some other basic security ideas.

A script that addresses all these things would be nice.  These have been attempted, but every major release changes something in a way that breaks the scripts.  In many environments, using something like puppet or ansible or chef is the solution that best works to maintain consistent levels and settings across all systems.  **Ansible** is simple enough to setup and use that it really makes sense for smaller shops with 3-300 systems to maintain.

Sadly, most security needs to happen between our ears. Just 1 accident for every 10,000 choices is all it takes to compromise a system. It can happen to anyone. Our relatives, boss, you, me, security experts ... anyone. Being constantly and consistently diligent is hard, probably impossible in the real world.

I did a quick google for this sort of stuff. [https://code.google.com/p/lusas/](https://code.google.com/p/lusas/) is a security and audit script claiming 2000 checks. Might be worth a look?

Having a script means you are consistent. THAT is fantastic, but there are almost always exceptions necessary for some systems. Blindly changing file permissions or system settings can be terrible.

---

