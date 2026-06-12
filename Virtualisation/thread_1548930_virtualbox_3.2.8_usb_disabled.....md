---
title: "virtualbox 3.2.8 usb disabled...."
date: 2010-08-09
forum: Virtualisation
---

### Post by stalefist on 2010-08-09
Hey everyone. So it's now 4am and I still haven't figured out why the USB support in virtualbox is still disabled. 

I'm running VB 3.2.8 downloaded from the site and I'm using Lucid..

I've added myself to the 'vboxusers' group, logged out, logged back in, restarted, prayed to the computer overlords and offered sacrifices, etc. etc. , and still nothing.

What's even more aggravating is that this is a fresh install of Lucid and I've done the same setup with a friends computer and it worked fine, no tinkering necessary. What gives?!

---

### Post by Ginsu543 on 2010-08-09
Have you installed VirtualBox Guest Additions?

---

### Post by stalefist on 2010-08-09
yes, the latest version


edit: my usb support works fine while running virtualbox as root, but thats not solving the problem, just avoiding it :/

---

### Post by stalefist on 2010-08-09
After doing a complete removal and deleting my .Virtualbox folder from my home folder I reinstalled VB and even went so far as to create a fresh VM and install guest additions rather than import my existing VM. 

result- usb support works, mysteriously..

Not sure what happened but starting from scratch seemed to fix it

---

### Post by Michael12uk on 2010-09-25
easy dude had the same issue. You need to add your account to the root group.all issues solved:KS

hope you overcome the problem:)

---

### Post by preahkumpii on 2010-10-07
> **Michael12uk said:**
> easy dude had the same issue. You need to add your account to the root group.all issues solved:KS

This was my problem. I had to add my user to the "root" user group as well as the "vboxusers" user group. Logged off and back in and USB now works.

Adam

---

### Post by tech7 on 2010-10-08
that's funny, that stuff doesn't work for me.  In fact, my VB won't even install virtualbox additions.  It says that it cannot mount the .iso.

---

### Post by scrooge_74 on 2010-10-09
Add yourself to the admin, vboxusers and I think plugdev.

Your problem is a permits problems.

I had those issues in the past also, in fact if you are not in the vboxusers you cant start a vm

---

