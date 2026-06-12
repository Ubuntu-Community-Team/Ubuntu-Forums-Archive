---
title: "Gnome Do - what deskbar could have been?"
date: 2007-12-11
forum: The Cafe
---

### Post by Blutack on 2007-12-11
Sick of people spamming the forums with applications?  Sorry.

[http://do.davebsd.com/](http://do.davebsd.com/)

Found this today, awesome little app.  I mean, yes...it is mono...and normally I'd shy like a horse but this seems rock stable, fast and so god damn useful!  Everything deskbar could have become before startup race conditions, slow interfaces and the occasional lockup.
And no, it isn't mine, I don't know the guy who makes it and I won't be held responsible if it kills your cat.  Go blame Schrödinger.

---

### Post by Mateo on 2007-12-11
Hmm, too bad those repos don't have signatures, otherwise i'd give it a shot.

---

### Post by Blutack on 2007-12-11
They are probably trustworthy as they are from the launchpad ppa service (upload your package and get it built).  There is nothing to stop someone signing a package full of malware, putting it in a repo and then giving you the gpg key to download.

---

### Post by undine on 2007-12-11
lol I'll stick with ALT+F2, thanks.

---

### Post by p_quarles on 2007-12-11
Gnome Do is definitely not malicious software -- in fact, one of the developers has a long-running thread about in this very Cafe:
[http://ubuntuforums.org/showthread.php?t=381039](http://ubuntuforums.org/showthread.php?t=381039)

---

### Post by aimran on 2007-12-11
> **p_quarles said:**
> Gnome Do is definitely not malicious software -- in fact, one of the developers has a long-running thread about in this very Cafe:
[http://ubuntuforums.org/showthread.php?t=381039](http://ubuntuforums.org/showthread.php?t=381039)

What he means is the linked version is unsigned, and hence prolly has  malicious code in it.

---

### Post by hanzomon4 on 2007-12-11
> **aimran said:**
> What he means is the linked version is unsigned, and hence prolly has  malicious code in it.

Nope, it's probably doesn't. 

I've installed it and it's fine. It's pretty neat, kinda like quicksilver for MacOS X. The only problem I have with it is that it does not make use of beagle or tracker so it sucks at searching, if you compare to beagle/tracker, although you get results much faster. Basically it has a basic indexer but that indexer does not index meta-data, only file names. 

But it does so much more then search, I suggest following the thread linked to by p_quarles to get the lowdown on this bad boy.

---

### Post by FuturePilot on 2007-12-11
I believe the Launchpad PPAs are meant to be unsigned. Seems totally legit to me.
I'll have to try this out, looks cool. :)

---

### Post by Mateo on 2007-12-11
Heh, my adversion to installing gnome-do through repos without a key was not security concerns, it was not wanting to have to confirm that I want to install unsigned software everytime I upgrade.  It's annoying to me.  If I didn't want to install the software I wouldn't have typed "apt-get install" and I wouldn't have added the repo to my list.

---

### Post by p_quarles on 2007-12-11
> **Mateo said:**
> Heh, my adversion to installing gnome-do through repos without a key was not security concerns, it was not wanting to have to confirm that I want to install unsigned software everytime I upgrade.  It's annoying to me.  If I didn't want to install the software I wouldn't have typed "apt-get install" and I wouldn't have added the repo to my list.
That's simple to work around:
```
nano .bashrc
```Add the line:
```
alias apt-get='apt-get --allow-unauthenticated'
```Log out, log back in, and apt won't bug you about unsigned repos any more (disclaimer: I don't really recommend doing this, but if you're certain you're unsigned repos are all safe, it shouldn't lead to any major problems).

---

### Post by bash on 2007-12-11
I think questions and discussions regarding Gnome Do would be better located in the already existing thread about Gnome Do instead of creating here a second one.

[http://ubuntuforums.org/showthread.php?t=381039](http://ubuntuforums.org/showthread.php?t=381039)

---

