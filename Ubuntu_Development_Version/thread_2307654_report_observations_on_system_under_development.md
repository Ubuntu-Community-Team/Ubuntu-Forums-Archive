---
title: "report observations on system under development"
date: 2015-12-27
forum: Ubuntu Development Version
---

### Post by oui on 2015-12-27
I am using 16.04 and it works very well.

I did update today and after that, divers diacritic signs are away (not all! éáäßç«» etc. stay usable, but ^a, ^o, ~n apostrophe etc are away) out my keyboard layout us intl.

In a separate message, I did also write on my bad observations concerning «jwm»...

What is to report, how to report, where is to do that?

How to contact especially a developer (f. ex. the developer of xombrero)?

---

### Post by dino99 on 2015-12-27
your example: watch the package changelog (from synaptic for example)

xombrero (2:1.6.4-3) unstable; urgency=medium

  * QA upload.
  * Upload to unstable.

 -- Joao Eriberto Mota Filho <eriberto@debian.org>  Sun, 21 Jun 2015 10:49:07 -0300

report bug:
ubuntu-bug <packagename>
(will open a bug on launchpad)
(if 'packagename' is unknown, then report against 'lubuntu' as a generic name, dev will reaffect it if necessary)

---

### Post by vasa1 on 2015-12-27
> **oui said:**
> ... What is to report, how to report, where is to do that?

How to contact especially a developer (f. ex. the developer of xombrero)?

For Lubuntu-specific issues see [https://wiki.ubuntu.com/Lubuntu/GettingInvolved](https://wiki.ubuntu.com/Lubuntu/GettingInvolved)

Re. xombrero,
[https://github.com/conformal/xombrero/issues](https://github.com/conformal/xombrero/issues)
[https://opensource.conformal.com/fluxbb/viewforum.php?id=8](https://opensource.conformal.com/fluxbb/viewforum.php?id=8)

---

### Post by oui on 2015-12-27
Hi

Thank you very much for above replies.

But xombrero is not really my big problem (only copy the adequate directories from SliTaz ):P (fable: «on a toujours besoin d un plus petit que soi» :p ! ; those directories are /usr/share/xombrero and /home/../.xombrero . eventually copy after that our old /home/../.xombrero/favorites on the new one after that! you can try to use with precautions part of your old /home/../.xombrero.cfg if you did use one: inspect it, create a new one where ALL lines are at first commented and uncomment one line, restart xombrero, test now, after the other, test again, until you are happy) and xombrero goes (the hobby coder username «aleksej», as it names himself in the SliTaz forum, has implemented xombrero perfectly in SliTaz ;) ) and SliTaz goes in Ubuntu64 as in SliTaz... Probably because the SliTaz guys have a great experience in webkit as they did develop an own webkit browser, TazWeb, and develope all services in the TazWeb browser / webkit-frontend as SliTaz panel ):P , things that great distributions can not can until this date... xombrero is for them only one little frontend more webkit like midori. as will only point out this thing...

My big problem is the disfunction in the keyboard layout management where divers signs very important in my natal tongue, French, disappear (probably an attack of English speaking folk ):P ?) since the last reactuallization : It is not possible to use this release any more for us...

Kind regards

---

### Post by vasa1 on 2015-12-27
If you are interested in contributing to the development of 16.04, the best way would be to follow the process described in "Getting Involved". IIRC, Lubuntu's lead developer is French.

---

