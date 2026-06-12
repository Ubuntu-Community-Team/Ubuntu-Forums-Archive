---
title: "Shockingly poor quality control"
date: 2012-06-12
forum: Testimonials &amp; Experiences
---

### Post by snowpine on 2012-06-12
No, this isn't a Unity rant... I actually like the new interface! Ubuntu 7.10 was my first distro, I was a loyal user through 9.04 until a bug with Intel video cards drove me away. Unity is what brought me back to Ubuntu 12.04 after a 3-year hiatus. I figured "If so many people hate it, Canonical must being doing something right," and they were right. However...

Why on earth would you ship a "long term support" release with a year- old, confirmed, high-priority bug in the default terminal application? Do you think that will not anger and alienate intermediate/advanced users who rely on the terminal every day?

[https://bugs.launchpad.net/unity-2d/+bug/788607](https://bugs.launchpad.net/unity-2d/+bug/788607)

It is futile to Alt-TAB between terminal and other apps because the terminal stays on top. Copy commands from the forum to the terminal? Impossible because the terminal is always on top. Copy & paste from my text editor to the terminal? Impossible because the terminal is always on top. Hide what I'm working on while I'm away from my desk? Impossible because the terminal is even on top of the screensaver! What a disgusting security flaw, that anyone who wiggles my mouse can see the contents of my root terminal. I don't think I am overreacting to say, if I was a military, banking, or corporate IT manager responsible for deploying Ubuntu 12.04 instead of enterprise linux, I would potentially lose my job over this glaring security flaw.

You've had over 1 year to fix this bug and you chose to spend it doing lord knows what! I'm done, this is my ragequit notice, better luck with 14.04. I will be switching to a more stable distribution and hoping Unity gets ported over at some point soon.

I make fun of UT&E rants all the time ;) so now the community gets a fair chance to dismiss and ridicule my testimonial as I have done myself so many times... don't hold back, I can handle it. :)

---

### Post by Cheesehead on 2012-06-12
That bug isn't triaged, it's not assigned to the correct package, and there are (unfollowed) hints that it's a known compiz or OpenGL bug. I wouldn't touch it either.

Users suffering from this bug still haven't provided enough information to locate the package or offending code, or to refer it to the correct upstream project. It seems unreasonable to expect volunteer triagers on bug-squad to be everywhere and all-knowing, or to expect developers to be psychic.

If the bug affects you and you *really* want it fixed, learn how to triage it. Look for related problems, bugs, and forum questions. Figure out which package is causing the failure, and then go to that project homepage and learn what information they need to debug or diagnose it. Figure out how to reproduce the bug under controlled conditions, and create a debug trace. When the developer releases the fix, install and confirm that it's really fixed. Help manage and coordinate the Launchpad bug, the upstream bug, the mailing list discussion, and queries from other venues.

That's how I learned triage; I *really* wanted an appletalk bug fixed. It got fixed.

---

### Post by snowpine on 2012-06-12
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/865031](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/865031)
[https://bugs.launchpad.net/ubuntu/+source/vte/+bug/809911](https://bugs.launchpad.net/ubuntu/+source/vte/+bug/809911)
[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/929028](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/929028)
[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/869802](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/869802)
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/943167](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/943167)
[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/848540](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/848540)

[https://bugzilla.gnome.org/show_bug.cgi?id=662751](https://bugzilla.gnome.org/show_bug.cgi?id=662751)
[https://lists.launchpad.net/compiz/msg22672.html](https://lists.launchpad.net/compiz/msg22672.html)

---

### Post by Cheesehead on 2012-06-12
Excellent! The more you know about it, the easier to get it fixed!

---

### Post by QIII on 2012-06-12
Personally, in the situations you mentioned, I'd use an enterprise distro to begin with.

Ubuntu wouldn't probably be something I'd consider.

That said...

It's definitely a bug that has been around for a while.  There is a point, however, at which developers must make the decision to weigh what will hold back deployment and what will not.  Otherwise, nobody would deploy anything.  Is that comforting to those who encounter problems?  Certainly not!  Is it a fact of life in the industry?  Yes.

If someone told me Canonical had Ubuntu perfect before shipping it, I'd chuckle.

---

