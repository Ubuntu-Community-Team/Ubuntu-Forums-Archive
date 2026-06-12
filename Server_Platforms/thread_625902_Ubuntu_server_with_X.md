---
title: "Ubuntu server with X"
date: 2007-11-28
forum: Server Platforms
---

### Post by ottothecow on 2007-11-28
I have a series of print kiosks currently running freeBSD that I would like to migrate over to ubuntu (because the packages system is driving me insane).  

Their use is pretty simple: they present a login screen (with a custom app that will compile just fine on ubuntu) that allows a user to print documents to a shared printer and deduct the cost from an account.  They are pretty close to being dumb terminals, all of the printing and account management is handled on the server.

The freeBSD installs are simple, it is an expert install with nothing installed (except enabling sshd for remote admin) and then we pkg_add xorg, qt4, subversion, x11vnc, and bash.  Script pulls print monitor source from subversion, compiles it and sets up a user account for the software which will then autorun in fullscreen on boot.

Is the ubuntu-server install right for this?  I was planning on apt-get xorg and the other needed packages and then setting up a repository for the print app so I can just apt get that too.

Also since I am only familiar with desktop ubuntu, how do I set up a more standard root/normal user organization (the normal user should not be a sudoer and the root account should be available for local and su login).

-
Thanks

---

### Post by p_quarles on 2007-11-28
Ubuntu server edition would be just fine for that, but doesn't offer the same kind of "expert install" that you used for the FreeBSD setup. In other words, you might get more than you really need. You can, however, use the "minimal" CD to build the system straight from the repositories. [[link]("https://help.ubuntu.com/community/Installation/MinimalCD")]

The other possibility is Debian. Works almost exactly like Ubuntu, but you have a slightly broader range of installation options. You would be able to get a more minimal installation by using either their "business card" CD (~8 MB, equivalent to the Ubuntu minimal), or the "net install" CD (~150 MB, and comes with the base system). Also, Debian enables the root account during the setup process, so you wouldn't need to fiddle with that. 

As for how to do that in Ubuntu, it's pretty straightforward:
```
sudo passwd root
```
Type the password, verify, and root is up and running. To disable the sudo account:
```
su visudo
```
and comment out the line that begins with "%admin"

That said, I'll also offer my opinion: sudo is a good system, and has some advantages (especially in terms of dumb-mistake prevention) that an enabled root password does not offer. Keeping the admin account separate, though, is also wise. This can be accomplished by simply adding a non-sudo user for normal use:
```
sudo adduser *username*
sudo passwd *username*
```
Then, just make sure that this user is a member of groups that it needs access to, and that it's *not *a member of the group "admin."

---

### Post by ottothecow on 2007-11-28
Thanks, that pretty much answered the questions I have right now.

One thing on the minimal CD, if I use a LTS release (dapper or the upcoming one) but use the minimal installation, how do I make sure I am only using server packages that have a 5-year support term (compared to the 3-year for desktops).  I'd like to set this up in such a way that it can be kept clear of vulnerabilities via simple upgrades for some time so that when I am gone, my replacement won't end up with the nightmare I am having with freebsd (we are using a bunch of hacked together scripts on an installation base that was built by someone I have never met).

---

### Post by p_quarles on 2007-11-28
> **ottothecow said:**
> One thing on the minimal CD, if I use a LTS release (dapper or the upcoming one) but use the minimal installation, how do I make sure I am only using server packages that have a 5-year support term (compared to the 3-year for desktops).  I'd like to set this up in such a way that it can be kept clear of vulnerabilities via simple upgrades for some time so that when I am gone, my replacement won't end up with the nightmare I am having with freebsd (we are using a bunch of hacked together scripts on an installation base that was built by someone I have never met).
That's actually a really good question. Ordinarily I would say that so long as you don't install any desktop applications, everything will be supported for the LTS period. 

I would *assume* that Xorg is included in the security updates for the long haul, but I don't know for certain. Maybe someone else here would have a more definite answer.

---

### Post by ottothecow on 2007-11-28
Thats what I figured, thanks.

Also, not to sound creepy but I noticed it said you were from chicago so I clicked through to your profile and noticed you were at UChicago.  Thought you might like to know that the system in question here is the print system we use in all of the dorms here (as well as the new grad residence hall).

---

### Post by p_quarles on 2007-11-28
No kidding. I figured this was for a college setting, but had no idea it was that close to home. It was actually NSIT that first introduced me to open source (via the Mozilla suite, back in 2002), so I'm glad to know that I'm able to give a few tips back in return. :)

Cheers

---

### Post by HermanAB on 2007-11-28
For  a server with X, I recommend the appropriately named Xubuntu.  It is nice and fast.  Xubuntu also runs nicely on VMware.  So you can make a server with Xubuntu, install VMware and then run many virtual servers which may also be Xubuntu.

Cheers,

Herman

---

