---
title: "Gnome-shell and mutter 3.5.4"
date: 2012-07-18
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-07-18
The newest development versions of gnome-shell and mutter (3.5.4) are now available from the official repos of QQ. Thanks to Jeremy Bicha. :)
These work quite smoothly and well.

---

### Post by cecilpierce on 2012-07-18
> **Harry33 said:**
> The newest development versions of gnome-shell and mutter (3.5.4) are now available from the official repos of QQ. Thanks to Jeremy Bicha. :)
These work quite smoothly and well.

How about extensions ?
Any news on them ?

---

### Post by Harry33 on 2012-07-18
> **cecilpierce said:**
> How about extensions ?
Any news on them ?
I am not using any of the extensions myself.
Perhaps Jeremy knows about this.

---

### Post by Harry33 on 2012-07-18
Well, here it is:

[https://launchpad.net/ubuntu/quantal/+source/gnome-shell-extensions/3.5.2-0ubuntu1](https://launchpad.net/ubuntu/quantal/+source/gnome-shell-extensions/3.5.2-0ubuntu1)

---

### Post by cecilpierce on 2012-07-18
3.5.2 Extensions are in the repos but dont work ?
The metadata.json files say ver 3.5.4...?

---

### Post by Harry33 on 2012-07-19
OK
However, it was meant to work, see this:
> gnome-shell-extensions (3.5.2-0ubuntu1) quantal; urgency=low
* Resynchronize with Debian. Remaining change:
- New upstream version. (LP: #1017979)
- debian/patches/01_update-version-numbers.patch:
- Bump GNOME Shell compatibility version to 3.5.4

---

### Post by jbicha on 2012-07-19
Cecil, may I suggest rebooting your computer. dconf had a major update and I noticed some things didn't work right until I rebooted. If that still doesn't work, please give us some more details about what exactly isn't working.

Also, gnome-tweak-tool badly needs an update; it's on my list of things to get done later this week.

---

### Post by cecilpierce on 2012-07-19
@jbicha

None of the installed extensions work and neither does 'Advance Settiugs'.
I moved some to /.local/share/gnome-shell/extensions to see if that would help, nope  :confused:

---

### Post by cecilpierce on 2012-07-20
3.5.2 Extensions are working now and so is advance settings, thanks :)

---

