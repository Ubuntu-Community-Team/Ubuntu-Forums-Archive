---
title: "Removing The Backports"
date: 2005-04-27
forum: Ubuntu Backports
---

### Post by punkrockguy318 on 2005-04-27
Hey, I'm wondering about how I can remove Hoary Backports, and go back to Vanilla Hoary.  Thanks!

---

### Post by Leif on 2005-04-27
Remove the repositories from your sources.list, and remove and reinstall whatever updates you got from backports. So far, I've only noticed firefox for my usage.

---

### Post by bored2k on 2005-04-27
sudo gedit /etc/apt/sources.list

Put a # at the beggining of every line that says backport.

---

### Post by jdong on 2005-04-27
You'll also have to roll back the backported packages... Easiest way is to invoke "apt-get install PKGNAME/hoary" on all Backports updates you've installed.

---

### Post by punkrockguy318 on 2005-04-27
[QUOTE=jdong]You'll also have to roll back the backported packages... Easiest way is to invoke "apt-get install PKGNAME/hoary" on all Backports updates you've installed.[/QUOTE]
 How can I get a list of the installed backport packages?  Maybe I should try to work up a script for this.

---

### Post by dafrabbit on 2005-04-27
[QUOTE=punkrockguy318]How can I get a list of the installed backport packages?  Maybe I should try to work up a script for this.[/QUOTE]
 This thread has what you want:

[http://ubuntuforums.org/showthread.php?t=12174](http://ubuntuforums.org/showthread.php?t=12174)

I used it to roll back my warty backports so I could dist-upgrade to hoary. The basic idea should be the same, give it a try.

---

### Post by Gustav on 2005-04-28
Or you can search for "ubp" in version in synaptic

---

### Post by slnkez on 2010-03-20
Old thread, but it's the first result on Google search.  The instructions here are for karmic.

To remove backports without going through individual packages, use a process called apt pinning.

Create a text file /etc/apt/preferences.d/downgrade (or whatever name you choose).  In the file, put:

```
Package: *
Pin: release a=karmic-security
Pin-Priority: 1003

Package: *
Pin: release a=karmic-updates
Pin-Priority: 1002

Package: *
Pin: release a=karmic
Pin-Priority: 1001

```

Packages from repositories with higher pin-priority have higher priority regardless of version number.  Pin-priority of 1000+ allows downgrading.  The repositories are in /etc/apt/sources.list

Do this in a console after saving the file:
sudo apt-get update

Do this to make sure your apt-pinning policy is there (use arrow keys to scroll, 'q' to quit):
apt-cache policy|less

Do this to downgrade:
apt-get upgrade

Afterwards, you can remove the backport repositories and the downgrade text file if you like.

---

