---
title: "Repository request for APTus"
date: 2014-10-20
forum: Repositories &amp; Backports
---

### Post by ipselute on 2014-10-20
I recently tried the new Sparky Linux and a i saw a cool program bundled in the liveusb. It is called APTus (and another one called APTus Extra). Anyway, APTus is actually nothing more than a (very nice) GUI interface for a bunch of useful linux commands like update, upgrade, fix broken sources, etc. Could you add this piece of software to the Ubuntu repository? Or at least make some ppa for it. It is really very useful software for linux newbies who are afraid of the terminal windows. Really saves me tons of command typing everyday (on 10 PCs that's a LOT!!).

---

### Post by QIII on 2014-10-20
Hello!

This is a user forum.  Although the occasional Canonical employee may wander through here purely by accident, this is not a very good place to catch their attention.

None of us here is responsible for the contents of the repos.

However, it is possible that someone will be able to help you to find what you are looking for.

It looks like you might be able to just use synaptic, which is an apt front end already available in the repos.

Cheers!

Edit: have you tried [http://sparkylinux.org/sparky-aptus-on-debian-and-ubuntu/](http://sparkylinux.org/sparky-aptus-on-debian-and-ubuntu/) ?

I'd recommend synaptic first since it is in the Ubuntu repo already.

---

### Post by Bucky Ball on 2014-10-20
I don't have it in Synaptics, but I'm using Xubuntu. Is that the issue?

---

### Post by slickymaster on 2014-10-20
There are a number of paths that a package can take to enter Ubuntu. I advise you to start by having a read at at the [Ubuntu Technical Board page]("https://wiki.ubuntu.com/TechnicalBoard") as they are the responsible for the technical direction that Ubuntu takes. They make decisions on package selection, packaging policy, installation systems and processes, kernel, X server, library versions and dependencies.
Another place would be the [Ubuntu Foundations Team page]("https://wiki.ubuntu.com/FoundationsTeam"), who are the responsible for delivering the core Ubuntu system, which is common to the whole Ubuntu family of products and services.

You can also try to get some of the developers and/or Canonical liaisons on IRC in #ubuntu-devel on irc.freenode.net

Hope this will somehow help you. Good luck.

---

### Post by QIII on 2014-10-20
Sorry folks, perhaps I was unclear...

APTus seems to be a GUI front end for apt, just as synaptic is a GUI front end for apt.

Perhaps synaptic will fulfill the same role without having to add a third party repo.

---

### Post by coffeecat on 2014-10-20
@QIII, just to add... Do you want to edit your edit in your earlier post? Somehow the useful link you provided lost its url tags and is not clickable. I'll repost it here anyway for the OP:

[http://sparkylinux.org/sparky-aptus-on-debian-and-ubuntu/](http://sparkylinux.org/sparky-aptus-on-debian-and-ubuntu/)

It's appears to be a viable way of getting APTus installed in Ubuntu although I haven't tried it myself. Like you, I'm quite happy with Synaptic.

---

### Post by QIII on 2014-10-20
Darn cell phone!

---

### Post by Bucky Ball on 2014-10-20
> **QIII said:**
> Sorry folks, perhaps I was unclear...

APTus seems to be a GUI front end for apt, just as synaptic is a GUI front end for apt.

Perhaps synaptic will fulfill the same role without having to add a third party repo.

Ah, now I get you. ;)

---

### Post by slickymaster on 2014-10-21
> **QIII said:**
> Sorry folks, perhaps I was unclear...

APTus seems to be a GUI front end for apt, just as synaptic is a GUI front end for apt.

Perhaps synaptic will fulfill the same role without having to add a third party repo.

Ok, understood now, even though I think that the thread title can be somewhat misleading.

---

### Post by ian-weisser on 2014-10-21
> **ipselute said:**
> Could you add this piece of software to the Ubuntu repository?

Anyone can learn to package software. Many developers *don't* package, but rely upon volunteers to package for them. It leaves them more time to develop.

Anyone, including you or me, can contribute packaged software to the Ubuntu Repositories, or to the Debian Archives. 

If you think it's really great software, this can be your contribution to the Ubuntu community.

See [http://packaging.ubuntu.com](http://packaging.ubuntu.com) to learn how to start the process.

---

### Post by ipselute on 2014-10-29
Many thanks to you! That hyperlink is exactly what i was looking for! Cheers and good luck!

---

