---
title: "Getting involved with development"
date: 2012-03-17
forum: The Cafe
---

### Post by rwonder on 2012-03-17
Hey,

How do I get started if I want to get involved with development on the Ubuntu OS?  What are some things I need to know?

Thanks :)

---

### Post by Cheesehead on 2012-03-17
Depends on what you want to develop.

If you want to work on applications instead of the OS, then you need to understand how dependencies work in Debian/Ubuntu, how packaging works, and how Launchpad works for your version management and bug tracking.

If you want to work on the OS itself, then you need to understand the team and decisionmaking structure, the release cycle, and the difference between Canonical vs. Ubuntu-project.

If you're not sure what you want to work on, then I suggest joining the Bug Squad. After a few dozen bugs, you'll have a much clearer understading of the system and your preferred places in it.

---

### Post by rwonder on 2012-03-17
Thanks for the info Cheesehead.
Yeah I think I'll start by joining the Bug Squad :)

---

### Post by philinux on 2012-03-17
> **rwonder said:**
> Hey,

How do I get started if I want to get involved with development on the Ubuntu OS?  What are some things I need to know?

Thanks :)

Try our ubuntu+1 forum [http://ubuntuforums.org/forumdisplay.php?f=412](http://ubuntuforums.org/forumdisplay.php?f=412)

---

### Post by kostkon on 2012-03-17
You could start from [here]("http://developer.ubuntu.com/").

---

### Post by cariboo on 2012-03-17
philinux, gave you a link to the U+1 devel sub-forum, I'd suggest you create an empty partition on your system, and install one of the daily builds available here:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

The reason I say create an extra partition, is that even though we are getting close to the end of development for this release, there could still be a show-stopper bug that may make your system unusable for some amount of time. If you have a stable release installed, you can use it to chroot into your broken install, and affect repairs.

---

