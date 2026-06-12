---
title: "What happened to KSplice?"
date: 2009-12-08
forum: The Cafe
---

### Post by toupeiro on 2009-12-08
Just curious, is there anyone in the know as to why ksplice was removed from karmic by default?  I have a relatively new build that I noticed I had to reboot because ksplice was not splicing.  After more research, I found out that it wasn't there at all.  It was easy enough to install it, but I thought this was a standard thing as of about a version or two ago?

---

### Post by the yawner on 2009-12-08
Huh? I've never tried KSplice. And the most recent Ubuntu versions I've use are Intrepid and Karmic (skipped Jaunty) and neither offered KSplice on a default install.

---

### Post by toupeiro on 2009-12-08
I know for a matter of fact it was included because I've seen message logs with ksplice entries in them.  I've even read stuff on launchpad when it was done because I was testing the upstream project a while before ubuntu adopted it.. its not something you'd see in a GUI.  it's  a compoment which allows live splicing of patches and modules into an active kernel without rebooting, thus eliminating most of the last few remaining reasons to ever reboot a linux machine.  I know its not there by default now because .. I get asked to reboot on system updates, so I looked for it and it was gone.  For a while, that stopped .. because it was there.

---

### Post by FuturePilot on 2009-12-08
AFAIK it was never installed by default in any release.

---

### Post by toupeiro on 2009-12-08
[http://ubuntuforums.org/showthread.php?t=765352&highlight=ksplice](http://ubuntuforums.org/showthread.php?t=765352&highlight=ksplice)

Read the last message in this thread.

which sources

[http://linux.slashdot.org/story/09/06/27/2238255/Ksplice-Offers-Rebootless-Updates-For-Ubuntu-Systems](http://linux.slashdot.org/story/09/06/27/2238255/Ksplice-Offers-Rebootless-Updates-For-Ubuntu-Systems)

[http://ubuntuforums.org/showpost.php?p=7552739&postcount=24](http://ubuntuforums.org/showpost.php?p=7552739&postcount=24)

[http://lifehacker.com/5303813/ksplice-offers-no+reboot-ubuntu-security-fixes](http://lifehacker.com/5303813/ksplice-offers-no+reboot-ubuntu-security-fixes)

---

### Post by FuturePilot on 2009-12-08
> **toupeiro said:**
> [http://ubuntuforums.org/showthread.php?t=765352&highlight=ksplice](http://ubuntuforums.org/showthread.php?t=765352&highlight=ksplice)

Read the last message in this thread.

which sources

[http://linux.slashdot.org/story/09/06/27/2238255/Ksplice-Offers-Rebootless-Updates-For-Ubuntu-Systems](http://linux.slashdot.org/story/09/06/27/2238255/Ksplice-Offers-Rebootless-Updates-For-Ubuntu-Systems)

It's not built in to Ubuntu, you have to install it yourself [http://www.ksplice.com/uptrack/]("http://www.ksplice.com/uptrack/")

---

### Post by toupeiro on 2009-12-08
> **FuturePilot said:**
> It's not built in to Ubuntu, you have to install it yourself [http://www.ksplice.com/uptrack/]("http://www.ksplice.com/uptrack/")

Then why the heck don't I remember installing it manually, ever?   Damn senility before 30...


Well, its still definitely in the repos, I just pulled it back down.

---

### Post by Exodist on 2009-12-08
KSplice should be default. You think everyone would want to be able to keep running after a kernel update. At the very least it should be on the server install CD.

---

