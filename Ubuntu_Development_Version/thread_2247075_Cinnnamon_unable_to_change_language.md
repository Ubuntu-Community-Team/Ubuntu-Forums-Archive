---
title: "Cinnnamon: unable to change language"
date: 2014-10-05
forum: Ubuntu Development Version
---

### Post by PatrickVogeli on 2014-10-05
Hello all,

after some releases using Linux Mint, I'm ready to come back to ubuntu. There are basically 2 reasons for this:
1. Linux mint has decided to stay on the LTS release cycle. I like to have newer SW :)
2. Ubuntu has included the Cinnamon deskto environment to its standard repos: yay!

I've installed 14.10 in a virtual machine, and I've faced a little problem: I can only change the language partially! For example, in the menu, the applications are named in Catalan, but the right click menu, or the control center are in English. Nemo (the file manager) and the control center items are English, Libreoffice is in Catalan.

I've tried setting the language everywhere I could think of, to no avail.

Has anybody also faced this problem? Any solution?

Thanks!

Patrick

---

### Post by Doug S on 2014-10-05
Translations for the 14.10 cycle are not complete yet. The deadline is later this week, but even then there will be a delay until the language packs are updated.
You can monitor the status for your language [here]("http://projects.davidplanella.org/stats/utopic/ca").
Beyond that, and if nobody else adds to this thread, you might find better answers on [the translators e-mail list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-translators").

Edit: Actually, for this case, translations might not be done here, but rather imported from somewhere upstream, as I haven't been able to find it (cinnamon) in the [translators list of stuff]("https://translations.launchpad.net/ubuntu/utopic/+lang/ca").

---

### Post by PatrickVogeli on 2014-10-06
Hi, thanks for answering.

I think the problem is not so much about missing translations (Cinnamon 2.2 has been released for a while, I use it in Linux Mint 17 with near perfect translations), but I suspect that it is ignoring the language settings or ubuntu is not setting the right configuration for it.

Cinnamon specific applications (like the nemo file manager) are in English, while Gnome applications (for ex., gnome-terminal) and others (I mentioned libreoffice) are in catalan. 

I tried it is Spanish and Germany, and the same happened.

Anyone using cinnamon in a language different from English?

---

