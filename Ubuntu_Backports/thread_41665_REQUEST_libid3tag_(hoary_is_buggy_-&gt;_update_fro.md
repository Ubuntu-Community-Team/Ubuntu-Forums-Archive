---
title: "REQUEST: libid3tag (hoary is buggy -&gt; update from breezy)"
date: 2005-06-14
forum: Ubuntu Backports
---

### Post by infinito on 2005-06-14
Hi!

I was having problems with Gtkpod not reading correctly id3 tags. After some mails with autor we found that the cause was Hoary's libid3tag0, which has a bug that prevent apps form reading v2 tags.

I've backported this myself and now gtkpod works fine.
Please update this lib to latest from breezy (0.15.1b-7) to avoid this annoying bug.

Thanks for great work!

---

### Post by Seth on 2005-06-14
[QUOTE=infinito]Hi!

I was having problems with Gtkpod not reading correctly id3 tags. After some mails with autor we found that the cause was Hoary's libid3tag0, which has a bug that prevent apps form reading v2 tags.

I've backported this myself and now gtkpod works fine.
Please update this lib to latest from breezy (0.15.1b-7) to avoid this annoying bug.

Thanks for great work![/QUOTE]
 Here you are, fresh from Breezy.
[http://sethkinast.com/ubuntu/hoary/backports/libid3tag0_0.15.1b-7~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/libid3tag0_0.15.1b-7~5.04ubp1_i386.deb)
[http://sethkinast.com/ubuntu/hoary/backports/libid3tag0-dev_0.15.1b-7~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/libid3tag0-dev_0.15.1b-7~5.04ubp1_i386.deb)

---

### Post by Mez on 2005-06-14
The devs dont like libs being backported :(

---

### Post by infinito on 2005-06-14
[QUOTE=Mez]The devs dont like libs being backported :([/QUOTE]
 I know devs don't like libs backported, but the version that comes with Hoary is useless (no support for v2 id3 tags?? WTF!!!)
I think this is a good example on when libs should be backported.

---

### Post by Seth on 2005-06-14
I agree. Buggy libs should be backported; otherwise there's no point in having the lib in the distro to begin with.

Backporting something like a major version increment on a lib would of course be a no-no, but this is a very minor bump, just to fix a bug.

---

### Post by infinito on 2005-06-14
[QUOTE=Seth]I agree. Buggy libs should be backported; otherwise there's no point in having the lib in the distro to begin with.

Backporting something like a major version increment on a lib would of course be a no-no, but this is a very minor bump, just to fix a bug.[/QUOTE]
 Yes, and that's why I think making Backports official was the best thing Ubuntu people made in the last times...

---

### Post by graabein on 2005-06-15
[QUOTE=infinito]Yes, and that's why I think making Backports official was the best thing Ubuntu people made in the last times...[/QUOTE]
 And receiving undefiled... It's all blueprint. Fugazi is a great band.

I also noticed the lack of id3tag v2 support. Glad it's fixed now! Thanks!

---

