---
title: "System says up-to-date when it isn't"
date: 2005-05-26
forum: Repositories &amp; Backports
---

### Post by kentl on 2005-05-26
There is something strange about my system. It says that everything is up-to-date but I know for a fact that FireFox most recent version is 1.0.4 when I in fact have 1.0.2. I investigate further in the context of FireFox.

The "Ubuntu Update Manager" gladly says "Your system is up-to-date!" and I can not find a more recent version if I check the package information through "The Synaptic Package Manager".

Is it as simple as the FireFox package haven't yet been released as an Ubuntu packages?

---

### Post by nocturn on 2005-05-26
Ubuntu does not update to newer versions.  It stays at FF 1.0.2 for as long as you user Hoary.
Security fixes (only) from newer version are backported to 1.0.2.  Currently, 1.0.2-Ubuntu contains the fixes from 1.0.3 but not yet from 1.0.4.

---

### Post by kentl on 2005-05-26
Thank you for your reply!

But Ubuntu will update to a more recent version of FireFox later on, right?  :???: With this i mean that when the next version is the current stable one I will automaticly get the new FireFox when upgrading right? (as it will automaticly step from Hoary to the next current stable one)

---

### Post by mendicant on 2005-05-26
Well, the next version (Breezy) will have a later version of firefox, yes.  You will not automatically update to Breezy when it is released, however.  You must do that manually.

---

### Post by A-star on 2005-05-27
The best thing to do is use the backports repositorie if you want the latest version of everything.

see this forum for more info:
[http://www.ubuntuforums.org/forumdisplay.php?f=47](http://www.ubuntuforums.org/forumdisplay.php?f=47)

---

### Post by jdong on 2005-05-27
[QUOTE=A-star]The best thing to do is use the backports repositorie if you want the latest version of everything.

see this forum for more info:
[http://www.ubuntuforums.org/forumdisplay.php?f=47]("http://www.ubuntuforums.org/forumdisplay.php?f=47")[/QUOTE]

Yep, you bet :)

I created the Ubuntu Backports project specifically to address the problem of desktop apps getting dated over the 6-month period.

Among the 430+ updates I've packaged is your Firefox 1.0.4, and also GAIM 1.3.0.

Add the following repos to your /etc/apt/sources.list:

```

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

---

### Post by nern on 2005-05-29
[QUOTE=mendicant]Well, the next version (Breezy) will have a later version of firefox, yes.  You will not automatically update to Breezy when it is released, however.  You must do that manually.[/QUOTE]

Any Idea if the upgrade to breezy will be possible through a simple change of sources.list and a dist-upgrade?

---

### Post by mendicant on 2005-05-29
[QUOTE=nern]Any Idea if the upgrade to breezy will be possible through a simple change of sources.list and a dist-upgrade?[/QUOTE]

That's right.  It may not necessarily work (cleanly) until breezy gets released, but it should work at that point.

---

