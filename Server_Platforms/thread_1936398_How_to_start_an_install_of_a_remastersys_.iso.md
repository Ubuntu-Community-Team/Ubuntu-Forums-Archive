---
title: "How to start an install of a remastersys .iso"
date: 2012-03-06
forum: Server Platforms
---

### Post by Ghost_Mazal on 2012-03-06
Lo all,

I have a big problem. I made a remastersys distributable iso from a 11.10 server build. I burned it and now I want to install the .iso on a different pc. But the live cd start up in cli (as it's server). How do I start the installer ? There is no "install ubuntu" like with dekstop edition.

I tried choosing "start installer" on the live disk's grub menu , but that doesn't work. It also boot's up to a cli interface and just stands there waiting for commands.

Does anybody please know the cli command to start the installer form the cli on the live cd ?

Thanx

---

### Post by fkasmani on 2012-09-27
Ghost_Mazal, I seem to be having a similar problem. Have you had any luck? You may want to join in to follow this thread:
[http://ubuntuforums.org/showthread.php?t=2063572](http://ubuntuforums.org/showthread.php?t=2063572)

---

### Post by Ghost_Mazal on 2012-09-28
> **fkasmani said:**
> Ghost_Mazal, I seem to be having a similar problem. Have you had any luck? You may want to join in to follow this thread:
[http://ubuntuforums.org/showthread.php?t=2063572](http://ubuntuforums.org/showthread.php?t=2063572)

Nope I haven't had any luck. Since then I don't use server and use a graphical version of Ubuntu and just add the server components I need.

Another thing I did was to clone the server with the rsync method.
A lot more work than a remastersys install as you have to manually install grub
and edit fstab and grub.cfg files after clone. Drawback of this is that you then also have
ALL the data and users on the server as well and that is not an option when you want to
make a fresh install for a completely different server.

---

### Post by fkasmani on 2012-09-28
> **Ghost_Mazal said:**
> I don't use server and use a graphical version of Ubuntu and just add the server components I need.
Remastersys didn't manage to do the "install" even when you made a GUI based distro?

---

### Post by Ghost_Mazal on 2012-09-29
> **fkasmani said:**
> Remastersys didn't manage to do the "install" even when you made a GUI based distro?

No what I mean is , because I couldn't get a way for remastersys to work with server version I don't use server version for servers anymore. It's a wrong solution I applied and was forced into. Remastersys works 100% with gui version of Ubuntu.

---

