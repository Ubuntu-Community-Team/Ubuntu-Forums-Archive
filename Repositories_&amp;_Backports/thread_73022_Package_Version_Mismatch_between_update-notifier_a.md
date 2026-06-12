---
title: "Package Version Mismatch between update-notifier and http://packages.ubuntu.com"
date: 2005-10-07
forum: Repositories &amp; Backports
---

### Post by Jonathan Wiebe on 2005-10-07
Greetings!

A few days ago update-notifier appeared showing six updates available for hoary.  However the versions shown do not match the listings found at:
[http://packages.ubuntu.com](http://packages.ubuntu.com)

The packages and versions is question are:

Package / ubuntu.com version / update-notifier version
gtk2-engines-pixbuf / 2.6.4ubuntu4 / 2.6.4-0ubuntu3
libgtk2.0-0 / 2.6.4-0ubuntu4 / 2.6.4-0ubuntu3
libgtk2.0-bin / 2.6.4-0ubuntu4 / 2.6.4-0ubuntu3
libgtk2.0-common / 2.6.4-0ubuntu4 / 2.6.4-0ubuntu3
openoffice.org-debian-files / 1.1.3-3+1ubuntu1.1 / 1.1.3-3+1ubuntu1
update-notifier / 0.38.11ubuntu1 / 0.38.11

Maybe I'm being overly cautious but it makes me nervous to see this kind of discrepency.  Can anyone explain what is going on here?  Or is everything fine and I'm just missing something obvious?

Regards,

Jonathan Wiebe

---

### Post by adwait on 2005-10-07
I think if you run
```
sudo apt-get update
```

Then the versions shown by the notifier and the versions on the site will match. Its just that newer updates have been added, by apt hasn't updated your cache. The update notifier (AFAIK) refers to this cache and not directly to the net.

---

### Post by Jonathan Wiebe on 2005-10-07
Perhaps my first post wasn't quite clear.

The package versions shown by the update-notifier are NEWER than those shown on the web.  I could understand it if they were older and my apt cache had not been updated but the current situation has me confused.

Just to make sure a did a "sudo apt-get update" but the initial problem persists.

Thanks anyway,

Jonathan Wiebe

---

### Post by Jonathan Wiebe on 2005-10-07
My apologies,

I just realized that I **reversed** the version columns on my initial post.

The correct information is as follows:

Package / ubuntu.com version / update-notifier version
gtk2-engines-pixbuf / 2.6.4ubuntu3 / 2.6.4-0ubuntu4
libgtk2.0-0 / 2.6.4-0ubuntu3 / 2.6.4-0ubuntu4
libgtk2.0-bin / 2.6.4-0ubuntu3 / 2.6.4-0ubuntu4
libgtk2.0-common / 2.6.4-0ubuntu3 / 2.6.4-0ubuntu4
openoffice.org-debian-files / 1.1.3-3+1ubuntu1 / 1.1.3-3+1ubuntu1.1
update-notifier / 0.38.11 / 0.38.11ubuntu1

As you can see the update-notifier version is **newer** than the version shown on the web site.  So I am confused.

Sorry for the mixup and thanks in advance for any help.

Jonathan Wiebe

---

### Post by adwait on 2005-10-08
Have you added any repositories apart from the default ubuntu ones?

---

### Post by Jonathan Wiebe on 2005-10-08
The repositories that I have enabled are ubuntu "main", "restricted", "universe", and "multiverse".

I have not enabled any other repositories.

Here is the contents of my /etc/apt/sources.list file:

```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb-src http://ca.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hoary-updates main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src http://ca.archive.ubuntu.com/ubuntu hoary universe

deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu/ hoary-security universe main restricted multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
# deb-src http://security.ubuntu.com/ubuntu hoary-security universe

```

If there is any other information which would be helpful please let me know.

Regards,

Jonathan Wiebe

---

