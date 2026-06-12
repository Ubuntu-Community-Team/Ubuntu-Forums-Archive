---
title: "I found a bug."
date: 2010-04-11
forum: The Cafe
---

### Post by themarker0 on 2010-04-11
I feel so proud. Just wondering? Is it a common thing finding bugs? Like in everyday use, not trying to. (One no one has found to your knowledge)

---

### Post by tica vun on 2010-04-11
I haven't come across that many bugs, even in the beta.

Don't forget to file a proper report (or, if the bug was already reported, indicate that you're able to reproduce it) on launchpad.

---

### Post by RiceMonster on 2010-04-11
So report it.

---

### Post by Joeb454 on 2010-04-11
Try reporting it - if nobody has found it, it won't be listed on Launchpad :)

And it's not that common, unless of course, you're using the development version, then you're a little more likely to run into them ;)

---

### Post by NightwishFan on 2010-04-11
Every software has bugs, and fixing bugs creates more bugs. However reporting bugs makes Ubuntu better for everyone. Thank you for helping out! :D

If you like finding and reporting bugs, check out some of these links.
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
[https://wiki.ubuntu.com/Bugs/HowToTriage](https://wiki.ubuntu.com/Bugs/HowToTriage)

---

### Post by themarker0 on 2010-04-11
Its not common because its WUBI, and not many people don't have the windows bootloader when they use it. And i've just started one.

---

### Post by jflaker on 2010-04-11
> **Joeb454 said:**
> Try reporting it - if nobody has found it, it won't be listed on Launchpad :)

And it's not that common, unless of course, you're using the development version, then you're a little more likely to run into them ;)

Report it anyway.  If something similar is found, you will be given some options on launchpad.net....If none of the items match what you are seeing, create a new report....

The triage team will determine if there is already a report....if a duplicate, they will merge your report with a master report....

---

### Post by Joeb454 on 2010-04-11
Whenever I've reported things, I've been taken straight to a pre-existing bug on Launchpad, that's why I worded it that way :)

---

### Post by Phrea on 2010-04-11
[img]http://www.cirrusimage.com/Bugs/stink_bug_menecles_1.jpg[/img]

...or am I now too off topic? ;)

---

### Post by NightwishFan on 2010-04-11
[http://www.jamesshuggins.com/h/tek1/first_computer_bug.htm](http://www.jamesshuggins.com/h/tek1/first_computer_bug.htm) :lolflag:

---

### Post by -grubby on 2010-04-11
> **Phrea said:**
> [img]http://www.cirrusimage.com/Bugs/stink_bug_menecles_1.jpg[/img]

...or am I now too off topic? ;)

that looks serious

---

### Post by pielover88888 on 2010-04-11
> **Phrea said:**
> [img]http://www.cirrusimage.com/Bugs/stink_bug_menecles_1.jpg[/img]

...or am I now too off topic? ;)
Where did you get that picture? I love bugs(and pie!)and wanted to know.... let me guess..... Google, right?

---

### Post by new_tolinux on 2010-04-11
> **pielover88888 said:**
> Where did you get that picture? I love bugs(and pie!)and wanted to know.... let me guess..... Google, right?
What about here: [http://www.cirrusimage.com/Bugs/stink_bug_menecles_1.jpg](http://www.cirrusimage.com/Bugs/stink_bug_menecles_1.jpg)

---

### Post by wojox on 2010-04-11
So what's the Bug?

---

### Post by themarker0 on 2010-04-11
> **wojox said:**
> So what's the Bug?

WUBI didn't replace my bootloader, it installed grub ontop of FreeBSD bootloader.

---

### Post by oldos2er on 2010-04-11
> **themarker0 said:**
> I feel so proud. Just wondering? Is it a common thing finding bugs?

Well, a spider just ran under my chair....

---

### Post by Frak on 2010-04-12
> **themarker0 said:**
> WUBI didn't replace my bootloader, it installed grub ontop of FreeBSD bootloader.
You do know that Wubi just installs a bootloader inside of the Windows bootloader, right? That's not a bug; that's the intended design.

---

### Post by Khakilang on 2010-04-12
None so far only dead coakcraches in my old computer.

---

### Post by uRock on 2010-04-12
I thought Wubi was a bug? J/K! I found a new one the other day and of course the bug report didn't have enough info in it, so I am having to "debug" it.

---

### Post by themarker0 on 2010-04-12
> **Frak said:**
> You do know that Wubi just installs a bootloader inside of the Windows bootloader, right? That's not a bug; that's the intended design.

Its itended to only install GRUB?

---

### Post by uRock on 2010-04-12
> **themarker0 said:**
> Its itended to only install GRUB?

In the bootloader, yes. Did it install the rest of Wubi?

---

### Post by Frak on 2010-04-12
> **themarker0 said:**
> Its itended to only install GRUB?
It just installs a menu entry into the Windows bootloader. When FreeBSD starts, choose Windows, when that menu pops up, choose Ubuntu.

---

### Post by themarker0 on 2010-04-12
> **uRock said:**
> In the bootloader, yes. Did it install the rest of Wubi?

Nope. I just explained it badly.

---

