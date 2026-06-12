---
title: "ubuntu studio feature request: Edirol UA-25EX patch"
date: 2008-10-17
forum: Ubuntu Studio
---

### Post by [censored] on 2008-10-17
I would like to use my Edirol ua-25ex usb soundcard to its fullest abilities, but unfortunately it requires a kernel patch. One such patch, blablack has generously written for us.

[http://ubuntuforums.org/showpost.php?p=5815179&postcount=6](http://ubuntuforums.org/showpost.php?p=5815179&postcount=6)

Can we have this patch in the standard repo kernels, so as to us Edirol UA-25EXers the trouble of having to re compile the kernel?

---

### Post by Stochastic on 2008-10-18
file a launchpad bug report & the developers will act accordingly (get things ready for the 9.04 release) [http://launchpad.net](http://launchpad.net)

---

### Post by JDPP on 2009-07-01
Is there any news about that ?
does the last Jaunty support UA-25EX?
 (I mean without recompiling the kernel...)

---

### Post by Stochastic on 2009-07-02
I haven't seen any bug reports on Launchpad about it, so chances are that none of the developers are working on it yet.  I'll mention it in the #ubuntustudio-devel IRC chat room, but unless a formal launchpad bug appears, I doubt anyone will be willing to modify the kernel builds.

---

### Post by TheMuso on 2009-07-02
I would encourage you to contact the ALSA developers, and submit your patch to them. I would also make sure your patch applies cleanly to the latest sound git tree, found at git://git.kernel.org/pub/scm/linux/kernel/git/tiwai/sound-2.6.git.

The best way to contact the ALSA developers, is to subscribe to the alsa-dev mailing list, and post to the list with your proposed patch. What would be even better, is if you could post a git formatted patch. What I mean by that, is you create a git commit with your patch, authorship details, and a signed-off message to indicate that its your work. The patch then gets created with git-format-patch.

Feel free to private message me, or email me at [email]themuso@ubuntu.com[/email] if you have any questions, or want more help getting the patch ready to send upstream. Once the patch is upstream, we have a better chance of getting it into Ubuntu.

---

