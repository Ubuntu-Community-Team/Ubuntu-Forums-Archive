---
title: "Why is Ubuntu GNOME so weird?"
date: 2007-02-03
forum: The Cafe
---

### Post by BarfBag on 2007-02-03
I just finished setting up and configuring an Arch system.  It's really fast and bug free - but I only set it up to learn more.  I tested both KDE and GNOME.  The default GNOME desktop is horrendous looking, but it's much more bug free then the altered Ubuntu version.  Window sizes are consistent, all window buttons on bottom panel are same size and cleaner looking, that annoying "Starting Administrative Application" button doesn't appear on the bottom panel (happens when using an app that requires root and slows down everything else until it disappears), etc.  The Ubuntu version is much cleaner looking, but after using this, I'm going to have a hard time adjusting back.  What do they change anything under the hood that could be causing this?  Are there any plans to fix it?

---

### Post by xabbott on 2007-02-04
Maybe it's because I've used Gnome before Ubuntu but...it's hard for me to notice a difference. I see certain dialogs, new defaults, and extra buttons sometimes but nothing drastic.

---

### Post by manmower on 2007-02-04
> **BarfBag said:**
> The default GNOME desktop is horrendous looking [...] the Ubuntu version is much cleaner looking, but after using this, I'm going to have a hard time adjusting back.

You don't have to adjust back... Just stick with Arch. :p
But seriously if you miss Ubuntu's appearance: the Ubuntulooks GTK+ 2 engine is somewhere in the Arch repos (it's in extra to be precise) and the Metacity theme, icons and other artwork can be downloaded as tarballs from the ubuntu repos (e.g. using a browser). You can literally make it look identical.

---

### Post by BoyOfDestiny on 2007-02-04
> **BarfBag said:**
> that annoying "Starting Administrative Application" button doesn't appear on the bottom panel (happens when using an app that requires root and slows down everything else until it disappears), etc.

Yes, that annoyed the heck out of me. Here are mostly simple instructions to fix it. I'm on feisty so it might be a tad different.

System -> Control Center -> Assistive Technologies -> check the box - Password dialog as floating window...

I guess on edgy it was something like System -> Administration -> Accessibility -> same step as above...

Sometimes I ssh (using the -X option) to "cheat" so I can use some of the Ubuntu Gnome gui tools... Let me tell you, doing a gksudo via ssh with that enabled... Ugh... Hopefully it will just go away, or not be the default option anymore (it's happened before: cd/dvd eject buttons work now, nautilus uses browser mode and can handle changing file permissions recursively, etc... Gotta love open source :) )

---

