---
title: "Ubuntu won't install in french"
date: 2005-06-17
forum: The Cafe
---

### Post by Azmodan on 2005-06-17
My father decided to give Ubuntu a try.  He wanted to learn how to install it and I told him it was very easy.  In the begining, everything seemed ok.  The installer did a good job of guessing things and language was the first question asked which was a good thing since my father only speaks french.

Things got complicated when we got asked for the timezone.  The installer refused to accept the "Eastern" time zone (even if it was among the Canadian choices proposed).  I decided to select atlantic for now and change it later.  Next step, the installer asked for a **root** password.  I was really wondering what was happening.

I decided to just start the install over in english and had no trouble.  I then installed language-support-fr and language-pack-fr.  My father comented that it was exactly easy for a newbie to guess that you have to install in english (and even understand english).  And figuring out about installing language-support-fr and language-pack-fr is even harder, especially in a system not in your language.

I think that Breezy will have a totally different installer so is it worth it to report it somewhere ?  And if so, where ?

---

### Post by tread on 2005-06-17
Check [https://wiki.ubuntu.com//BreezyBadger](https://wiki.ubuntu.com//BreezyBadger) 
Other than that, try asking on the breezy part of the forum .. maybe someone there could help.

Edited to add: hardcore developer types prolly don't visit community chat :)

---

### Post by Astrophobos on 2005-06-17
I have the exact same problem everytime I try it with the setting you told and that on all of my system since hoary release.

French install and eastern timezone

---

### Post by kiddo on 2005-09-13
I'm just praying we get a fix for that soon. See also:
[https://bugs.freedesktop.org/show_bug.cgi?id=4042](https://bugs.freedesktop.org/show_bug.cgi?id=4042)

This reappeared in breezy! Before I could hack it by adding ca_enhanced to xorg.conf, now I can't! x_x why are the keyboard layouts so messed up in canada anyway? I mean we roughly use only US english and Canadian French AFAIK

---

