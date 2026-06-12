---
title: "Update frequency"
date: 2018-04-03
forum: Security
---

### Post by cam17 on 2018-04-03
I have 16.04.3LTS and I receive updates roughly every other day. Can anyone confirm this update period and tell me how I can determine when a update was released?

---

### Post by QIII on 2018-04-03
Hello!

There is no "Patch Tuesday" with Ubuntu.

Updates through the Canonical repos occur as they come and are tested/packaged.  There isn't necessarily a set schedule.  The other repos (Partners, Universe, Multiverse, etc) are updated whenever the developers release updates and someone (a MOTU in the case of the Universe repo) packages it and gets it into the appropriate repo.  If you use PPAs (Personal Package Archives), your guess is as good as anyone else's when the maintainer will have updates.

I just do daily updates to make sure I have everything.

---

### Post by cam17 on 2018-04-08
How can I tell when an update was released?

---

### Post by PaulW2U on 2018-04-08
> **cam17 said:**
> How can I tell when an update was released?
Launchpad will have the information but it can be quite lengthy navigating to the required page. You have to know what you are looking for. And you'll have to search for each package individually.

For example, [https://launchpad.net/ubuntu/bionic/amd64/gnome-shell](https://launchpad.net/ubuntu/bionic/amd64/gnome-shell) shows you that the latest gnome-shell update for Ubuntu 18.04 was released yesterday, 8th April at 11:34 BST, (UK time).

I tend to use **apt changelog <packagename>** in a terminal which shows the date that the package was first uploaded to the package builders. As packages tend to spend some time in the -proposed repository before being released the date given may be several days or even weeks earlier than the actual release date. Much quicker but it depends on what you want the information for.

Hope that helps, have fun. :)

---

### Post by TheFu on 2018-04-10
> **cam17 said:**
> I have 16.04.3LTS and I receive updates roughly every other day. Can anyone confirm this update period and tell me how I can determine when a update was released?

[https://www.debian.org/doc/debian-policy/](https://www.debian.org/doc/debian-policy/) might have the information you seek.

Perhaps if we understood why you want to know the timestamp for any specific update, we could help get to the final result more efficiently? 

I can see some excellent reasons for this information to be known - mainly to audit the correct versions are installed across an enterprise.  But the version information is already stored in each package metadata, not a timestamp.

Some other use?

Doing an apt update, followed by **sudo apt list --upgradable**, perhaps hourly would let you build an hourly bucket - just run the update periodically to see what changes from period to period. There are powerful text comparison and processing tools built into every Unix.

---

### Post by cam17 on 2018-04-13
The command apt changelog <packagename> will give me the date and  creator. I use it after asking ubuntu for pending updates using apt list  --upgradable.

Thanks

---

