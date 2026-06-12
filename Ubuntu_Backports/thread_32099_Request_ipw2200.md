---
title: "Request: ipw2200"
date: 2005-05-06
forum: Ubuntu Backports
---

### Post by snop on 2005-05-06
Hi,

I don't know if it's really possible to package a new ipw2200 (I don't know how tied is this to kernel).

Many people is having issues with this, mainly connection drops (see [http://ubuntuforums.org/showthread.php?t=21056](http://ubuntuforums.org/showthread.php?t=21056) where I proposed an ugly hack).

The ipw2200 driver for Hoary is a bit outdated and connection drop issues where well known by ipw2200 developers. It seems that newer versions of this driver correct those problems (found at [http://ipw2200.sourceforge.net/)](http://ipw2200.sourceforge.net/)).

So I wonder if this could be "backported" easily (or if it has been backported already).

Edit: I've just read that driver/kernel backports are not encouraged (which I can understand) but this driver is really buggy and thus this can bring many laptop users to abandon Ubuntu because of frustration so perhaps is good to give it a try. Any other opnion's welcome.

Thanks in advance.

SnOp

PD: I've been too lazy to compile the driver myself but I think this time I'm gonna make an effort and try to package either the driver myself or a kernel with the new driver. Anyway any clue/hint/suggestion will be appreciated.

---

### Post by jdong on 2005-05-06
Is it a part of linux-restricted-modules? I couldn't find a separate package

I'd recommend first notifying Ubuntu developers of this, via the Ubuntu Bugzilla link in the top-right corner. They are supposed to be rolling out update packages "some time after Hoary is released". :) :)


I'll look into it.

---

### Post by Psquared on 2005-05-06
Yeah, this is a problem and it is getting worse -- at least for me. My wifi got dropped 3 times yesterday. I kept getting up and looking at my router until I read the ipw2200 threads here. The fixes on here are temporary workarounds -- unless someone has the gumption to compile themselves. (no offense to you snop - you worked hard on those scripts) There is a good thread about this by luca_linux, but I swear it looks tricky.

Anyway, the current version of the driver is 1.03 and Hoary is using ver .19. Go figure.

Jdong - pls see what you can do.  :smile:

---

### Post by jdong on 2005-05-06
I'll ask again:

What package is this driver in?

---

### Post by jdong on 2005-05-06
Ugh, answered my own question -- it's in the monster "linux-image" package. I'll try to patch a new driver, either from the official site or from Linus's Git tree, and issue a kernel update in the "bleeding" tree.


It'll be better if you guys all filed a bug report with Ubuntu, though.

---

### Post by snop on 2005-05-06
Thanks for that fast answers.

[QUOTE=jdong]It'll be better if you guys all filed a bug report with Ubuntu, though.[/QUOTE]

In fact the bug was filled more than once but the update was delayed because of Hoary freeze:

[https://bugzilla.ubuntu.com/buglist.cgi?bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&bug_status=NEEDINFO&bug_status=UPSTREAM&bug_status=PENDINGUPLOAD&field0-0-0=product&type0-0-0=substring&value0-0-0=ipw2200&field0-0-1=component&type0-0-1=substring&value0-0-1=ipw2200&field0-0-2=short_desc&type0-0-2=substring&value0-0-2=ipw2200&field0-0-3=status_whiteboard&type0-0-3=substring&value0-0-3=ipw2200](https://bugzilla.ubuntu.com/buglist.cgi?bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&bug_status=NEEDINFO&bug_status=UPSTREAM&bug_status=PENDINGUPLOAD&field0-0-0=product&type0-0-0=substring&value0-0-0=ipw2200&field0-0-1=component&type0-0-1=substring&value0-0-1=ipw2200&field0-0-2=short_desc&type0-0-2=substring&value0-0-2=ipw2200&field0-0-3=status_whiteboard&type0-0-3=substring&value0-0-3=ipw2200)

I'll try to compile the driver and see if it actually solves this issue.

Bye

PD: It's odd that this kind of things (i.e. drivers) must follow the same "freeze" as some other packages specialy when this driver is really buggy.

---

### Post by Psquared on 2005-05-06
[QUOTE=snop]Thanks for that fast answers.



In fact the bug was filled more than once but the update was delayed because of Hoary freeze:

[https://bugzilla.ubuntu.com/buglist.cgi?bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&bug_status=NEEDINFO&bug_status=UPSTREAM&bug_status=PENDINGUPLOAD&field0-0-0=product&type0-0-0=substring&value0-0-0=ipw2200&field0-0-1=component&type0-0-1=substring&value0-0-1=ipw2200&field0-0-2=short_desc&type0-0-2=substring&value0-0-2=ipw2200&field0-0-3=status_whiteboard&type0-0-3=substring&value0-0-3=ipw2200](https://bugzilla.ubuntu.com/buglist.cgi?bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&bug_status=NEEDINFO&bug_status=UPSTREAM&bug_status=PENDINGUPLOAD&field0-0-0=product&type0-0-0=substring&value0-0-0=ipw2200&field0-0-1=component&type0-0-1=substring&value0-0-1=ipw2200&field0-0-2=short_desc&type0-0-2=substring&value0-0-2=ipw2200&field0-0-3=status_whiteboard&type0-0-3=substring&value0-0-3=ipw2200)

I'll try to compile the driver and see if it actually solves this issue.

Bye

PD: It's odd that this kind of things (i.e. drivers) must follow the same "freeze" as some other packages specialy when this driver is really buggy.[/QUOTE]

Snop, if you are successful compiling the driver (I assume as a module and not the kernel) please post your results. The instructions by Luca_linux are not very novice friendly.

Thanks.  O:)

---

### Post by snop on 2005-05-06
After some research it seems that the newest driver (1.0.3) from ipw2200.sourceforge.net dosen't have the needed patches to be merged into a kernel. This means that it will be probably packaged apart on Breezy.

This is both good and bad: It means that it would probably be easily updated in the future but also that it's probably a little harder to package than earlier versions.

Apart from this I've been triying 1.0.3 and connection dropouts seem to be a think of the past. I created a tgz with all the needed files to be installed with 2.6.10-686-5 kenrels (instructions here [http://ubuntuforums.org/showpost.php?p=161217&postcount=35)](http://ubuntuforums.org/showpost.php?p=161217&postcount=35)).

This is yet an ugly hack (but not as ugly as the first python script I wrote).

If this helps someone great. Otherwise... I works for me, at least. ;)

Bye

---

