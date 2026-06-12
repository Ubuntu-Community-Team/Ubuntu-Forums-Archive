---
title: "Need some guidance on stripped-down installs"
date: 2005-05-11
forum: The Cafe
---

### Post by digiboi on 2005-05-11
I'd like to use Ubuntu to build a box that runs a select set of applications, such as Firefox, Thunderbird, vim, gFTP, XChat, etc. And I'd like to do it in the most efficient way possible. Not necessarily because my machine doesn't have the latest and greatest hardware, but more because of the reduced risks that come associated with fewer pieces of unused software installed.

I've browsed through Linux From Scratch, and before I dive in head first, was just curious if something similar would be possible in Ubuntu.

In a perfect world I'd be able to pick kernel X, have the hardware drivers be auto-detected, and then use apt-get to install binaries.

Is there hope in achieving something close to this in Ubuntu, or should I commit myself to LFS?

Much thanks in advance. :)

 - digiboi

---

### Post by JonahRowley on 2005-05-11
You can do what you need by doing a "server" install, and building your way up.  Tools like apt-build can help if you're a control freak.

I don't think Ubuntu is best-suited to this though.  Ubuntu's strength is in the polished desktop interface, something you'll be skipping.  Remove that, and what you're left with is a lot like a Debian base install.  Take a look at Debian, Gentoo and Slackware first, they might be better choices (all for their own reasons).  As for LFS, I don't see a need for it anymore unless you want something really stripped down or to customize the base system heavily.  Gentoo has mostly taken over as far as maximum-configurability goes.

---

### Post by TravisNewman on 2005-05-11
Agreed with Jonah-- except LFS is a GREAT way to learn things. For your setup though, I'd choose one of the three Jonah mentioned-- probably Gentoo. Keep an LFS box around to learn on, but it's complexity makes it hard to do maintenance/updates.

---

### Post by digiboi on 2005-05-11
Much thanks for the quick replies and advice. :)

---

