---
title: "WINE stopped offering support for my programming language???"
date: 2011-05-06
forum: Wine
---

### Post by ki4jgt on 2011-05-06
The justBASIC programming language ([http://www.justbasic.com](http://www.justbasic.com)) has worked on every version of WINE I've ever run it on in the past. Now, WINE no longer has the ability to satisfy it. I was wondering if you guys could tell me a little about what's going on, or if there was a WINE change list since 10.10. Thanks in advanced.

---

### Post by NightwishFan on 2011-05-06
You might be better off asking the wine people themselves.

---

### Post by ki4jgt on 2011-05-06
> **NightwishFan said:**
> You might be better off asking the wine people themselves.

I don't exactly know how to get in touch with them directly. They have mailing lists and forums. Several other options (I'm assuming is run almost completely by volunteers) That's how I ended  up here. Their site actually lists you guys. So what mailing list/forum/irc would be the best way to address this issue?

---

### Post by NightwishFan on 2011-05-06
You might get an answer here, but if not, try the mailing lists. :)
[http://www.winehq.org/site/forums](http://www.winehq.org/site/forums)

---

### Post by dacha on 2011-05-16
This is an Ubuntu 11.04 bug. Ubuntu's new libfontconfig is crashing some Wine applications. There was a thread about this in the forums a week or so back. If you can install libfontconfig from Ubuntu 10.10 or older, it will work.

---

### Post by dacha on 2011-05-16
I've reported the bug here: [https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/783622](https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/783622)

---

### Post by ki4jgt on 2011-05-16
Thanks. . .

---

### Post by ki4jgt on 2011-05-16
> **dacha said:**
> This is an Ubuntu 11.04 bug. Ubuntu's new libfontconfig is crashing some Wine applications. There was a thread about this in the forums a week or so back. If you can install libfontconfig from Ubuntu 10.10 or older, it will work.

How would I go about doing this? What version numbers?

---

### Post by dacha on 2011-05-17
See [http://ubuntuforums.org/showpost.php?p=10804481&postcount=8](http://ubuntuforums.org/showpost.php?p=10804481&postcount=8) for instructions.

---

