---
title: "Looking for gparted 0.19.1"
date: 2014-10-27
forum: Ubuntu, Linux and OS Chat
---

### Post by syntaxerror74 on 2014-10-27
Oh well.

They've managed again to break gparted COMPLETELY. At least the current Utopic gparted build (0.19.0.1build1) is entirely unusable due to a critical bug and will usually crash *before* even showing the GUI.

What, it does not crash for you? Then be happy, for there are many people affected by this issue (telling from [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/1376051"))

For the time being, I had to entirely downgrade to 0.18.x, because none of 0.19.x worked for me so far. And the one that *reportedly* has the issue fixed will require me to build gparted (presumably libparted as well) from source - no thanks.

PPAs are such a great thing! But sometimes their maintainers appear to be asleep - with both eyes open. And as usual, that always happens whenever there's a critical bug in there. When there's a trivial bug in there instead, you may get 5 updates per week via PPA ;) -Rant over-

---

### Post by syntaxerror74 on 2014-11-02
bump ...

---

### Post by Morbius1 on 2014-11-02
There is nothing to bump. You aren't asking for anything.

As for your "rant" well ... you're preaching to the choir for long time Linux users. 

Anyway, You installed Ubuntu 16.04 Alpha 1 ... er .. um ... Ubuntu 14.10 and you found a package that's messed up. If Ubuntu does fix it and assuming it's something Ubuntu can or is responsible to fix it it would be for 15.04 not 14.10 right?

---

### Post by syntaxerror74 on 2014-11-02
> **Morbius1 said:**
> There is nothing to bump. You aren't asking for anything.
Not? Sure I am. I wanted to ask if anybody has come across a 0.19.1 version of gparted even though I was unable to find anything on PPA (but what does that indicate in fact??)

> Anyway, You installed Ubuntu 16.04 Alpha 1 ... er .. um ... Ubuntu 14.10 and you found a package that's messed up. If Ubuntu does fix it and assuming it's something Ubuntu can or is responsible to fix it it would be for 15.04 not 14.10 right?
True, but why would that be a problem? I would even accept a 0.19.1 build made for Vivid. There is no "guarantee" that it will surely fail. Chances are it will even work fine. And this is what I want to test out.

---

### Post by Bucky Ball on 2014-11-02
*Thread moved to** Ubuntu, Linux & OS Chat.** *

Not a support request, but a rant, so unsure why you bumped it. Anyway, 14.10 is wet behind the ears and has been out just over a week. Expect breakage. Update daily and no doubt a fix will come down the line shortly. Is there a bug report in Launchpad? Have you posted on it?

---

### Post by syntaxerror74 on 2014-11-03
There actually is:
[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/1341587](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/1341587)

Please ignore the "USB" bit, since the crash may as well be reproduced easily with just those heavy door-stoppers called hard disks attached. :P

And have a read at these two too:

[https://bugzilla.gnome.org/show_bug.cgi?id=731752](https://bugzilla.gnome.org/show_bug.cgi?id=731752)

*"I am able to reproduce the behaviour using the gparted 0.19.0 code in a single CPU VMWare Player ubuntu 14.04 virtual machine"* (C. Gedak, bug #731752 comment #3) 

So it clearly looks as if I'm *not* making this up. BTW, this could really be the reason, because I am on single-core CPU too. Perhaps this is working actually fine with a multi-core one (and this is why not so many users have complained so far - only speculating, though)[URL="http://permalink.gmane.org/gmane.comp.gnome.svn/845092"]

http://permalink.gmane.org/gmane.comp.gnome.svn/845092[/URL]

---

### Post by buzzingrobot on 2014-11-03
Go to packages.ubuntu.com, search for gparted.  If you find the version you like, download it and install it manually. (Then research how to block a package from bring updated because it will be replaced by the buggy version next time you run updates.)

I'm not sure why the comments about PPA's since you linked to a bug report about the released package.

---

### Post by syntaxerror74 on 2014-11-03
> **buzzingrobot said:**
> 
I'm not sure why the comments about PPA's since you linked to a bug report about the released package.

Because I've searched high & low for a released *binary* package of 0.19.**1** - to no avail!

Even for Vivid there is only 0.19.**0**-1build1 available! I *think* I can still trust my pair of eyes.

---

### Post by buzzingrobot on 2014-11-04
Versions 20..0-1, if you trust the source: [http://www.ubuntuupdates.org/package/getdeb_apps/utopic/apps/getdeb/gparted](http://www.ubuntuupdates.org/package/getdeb_apps/utopic/apps/getdeb/gparted).

Gparted is an upstream package, so it will follow the standard upstream->Debian->Ubuntu route.

---

### Post by syntaxerror74 on 2014-11-04
Thank you!! Finally something that resembles what I was actually looking for!

Besides, I concede that I might have been a little naive in fact :shock:...As I actually thought that PPAs are only found in "PPA central" aka Launchpad, I was filtering on google for *site : ppa.launchpad.net*. But now as I can see there are 3rd-party PPAs whose maintainers do not *intend* to have them appear on Launchpad, things are looking very different.
Will memorize this 3rd party site - might save me plenty of time in the future, since there'll be no longer any need (in general) to compile from source each time. Thanks again.

---

### Post by mc4man on 2014-11-04
> **syntaxerror74 said:**
> 
PPAs are such a great thing! But sometimes their maintainers appear to be asleep - with both eyes open. And as usual, that always happens whenever there's a critical bug in there. When there's a trivial bug in there instead, you may get 5 updates per week via PPA ;) -Rant over-

> **syntaxerror74 said:**
> 

Besides, I concede that I might have been a little naive in fact :shock:...
I would say off-base rather than naive.
No **Personal** Package Archive maintainer owes you or anyone anything other than providing good builds & or fixes for sources that interest them **personally**.

---

### Post by Bucky Ball on 2014-11-05
PPAs go into Launchpad for a reason. Be very careful if you intend to randomly install PPAs from anywhere other than there. PPAs are untrusted and do not need to pass ANY quality control and the creator is under NO obligation to guarantee you of ANYTHING about them, and that includes whether they contain malware. Anyone can create a PPA, call it anything and bang it up on their site. 

Do research and ask around prior to installing untrusted PPAs or you may pay for it later.

---

### Post by syntaxerror74 on 2014-11-05
Granted (in general), but---telling from my recent "expeditions" there---I think ubuntuupdates.org is not *any random* site, but pretty well-known and with a sane reputation to lose if they thought of repeatedly releasing "dangerous" packages.

So one should not generalize too much, but distinguish *which* site it is about.

---

