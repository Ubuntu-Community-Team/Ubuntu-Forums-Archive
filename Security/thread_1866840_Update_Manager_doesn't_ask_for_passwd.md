---
title: "Update Manager doesn't ask for passwd"
date: 2011-10-22
forum: Security
---

### Post by hakermania on 2011-10-22
Yes, and that's have happened twice actually, it installs the stuff without asking for passwd.

And no, I haven't given it any recently, to be more specific, my pc is on doing a specific task and I haven't touched it 2 days now and now I decided to see for updates and it didn't ask me for passwd. What's going on ;) ?

11.10

---

### Post by lovbuntu on 2011-10-22
> **hakermania said:**
> Yes, and that's have happened twice actually, it installs the stuff without asking for passwd.

And no, I haven't given it any recently, to be more specific, my pc is on doing a specific task and I haven't touched it 2 days now and now I decided to see for updates and it didn't ask me for passwd. What's going on ;) ?

11.10

I guess they did it like that so users can easily get updates

---

### Post by hakermania on 2011-10-22
No, I don't get it, this should be a security vuln, it installs stuff without my passwd, 1st time now in 2 years.

---

### Post by Soul-Sing on 2011-10-22
it seems to be the new update-policy in 11.10. There are several "bug reports" on launchpad.

---

### Post by dfarrell07 on 2011-10-24
Interesting that apt-get update/upgrade still requires sudo, if this is a new 'policy.' Passwords ftw, I say.

---

### Post by roton on 2011-10-25
I noticed this too. Much prefer there to be a password.

---

### Post by Larkspur on 2011-10-25
Where's the security risk?  You installed the stuff that's being updated.  Only the administrator can update, so there's no problem with standard users.

---

### Post by The Cog on 2011-10-25
> **Larkspur said:**
> Where's the security risk?  You installed the stuff that's being updated.  Only the administrator can update, so there's no problem with standard users.
I confirm that non-admin users don't get offered the chance to upgrade - I just got the chance to check that with the latest round of updates. It still "feels" wrong to me, but I can't think if a good logical reason why.

---

### Post by hakermania on 2011-10-26
> **Larkspur said:**
> Where's the security risk?  You installed the stuff that's being updated.  Only the administrator can update, so there's no problem with standard users.

Well, as I though it:
If A is allowed to use B for opening the door then C may also use B for killing you :P

For example, somebody may as well trick the system that a package is on the updates and install a malicious package as well (dunno if possible, just saying).
If there's a way of installing *some* way of packages without passwd then there should be a way to install *all* the packages without passwd with some kind of trick.
Well, that's the security risk in which I referred to, a possible security risk.:P

---

### Post by bruno9779 on 2011-10-31
:shock::shock::shock:

I am not liking the direction Ubuntu is going...

I don't want to start a flame war, but this just feels too Windows for my taste.

---

### Post by crazyguy510 on 2011-11-02
> **hakermania said:**
> Well, as I though it:
If A is allowed to use B for opening the door then C may also use B for killing you :P

For example, somebody may as well trick the system that a package is on the updates and install a malicious package as well (dunno if possible, just saying).
If there's a way of installing *some* way of packages without passwd then there should be a way to install *all* the packages without passwd with some kind of trick.
Well, that's the security risk in which I referred to, a possible security risk.:P

I may be way off, but I'm not sure this is possible. The update manager only draws from the sources that you allow in synaptic package manager. To install completely new packages, or modify and add sources to synaptic package manager, you would still need a root password. So I would assume that the only way this would pose a problem is if there was a breach on the sources server. I don't quite know how a typical source pushes out an update to their software on a Linux distro, but I've never heard of this as a widespread problem.

I will say that true security is very rarely convenient, and this certainly ups the level of convenience.

---

