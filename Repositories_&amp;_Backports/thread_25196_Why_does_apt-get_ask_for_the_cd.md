---
title: "Why does apt-get ask for the cd?"
date: 2005-04-09
forum: Repositories &amp; Backports
---

### Post by titus on 2005-04-09
When i did 'sudo apt-get install nmap' i was asked to insert the ubuntu cd.

Why does it need to do this?

Can I turn this off?

Thanks,

Titus.

---

### Post by dusu on 2005-04-09
It's probably because you still have a line in your /etc/apt/sources.list file, where it is said that the cd is a place where to get packages.
If you comment it out, everything should be ok, and only the net will be used.

---

### Post by titus on 2005-04-09
yep, thought i'd checked that, but there it is.

it was hiding on the first line   :?

---

### Post by dusu on 2005-04-09
[QUOTE=titus]yep, thought i'd checked that, but there it is.

it was hiding on the first line   :?[/QUOTE]

No problem ! The first line is always nasty :-D

---

### Post by titus on 2005-04-09
:)

yeah, normally just have a title comment there.

thanks for your help.

---

