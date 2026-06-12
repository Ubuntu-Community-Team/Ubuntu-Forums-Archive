---
title: "Update music score software?"
date: 2008-09-28
forum: Ubuntu Studio
---

### Post by VanillaMozilla on 2008-09-28
Are there any plans to package and update music score software?

1. MuseScore is promising, but it's hard to find and install on Ubuntu.  Worse yet, the packaged version has major problems, and the latest version is not available.  (See [http://musescore.org/en/node/276](http://musescore.org/en/node/276) .)  Are there plans to get this up to date?

2. Denomo looks nice, but it's also out of date on Ubuntu.  A number of common features such as grace notes can only be entered from LilyPond, but the packaged version does not integrate with LilyPond.  I'm not sure the Windows version works either (no icons on my computer, therefore unusable), but does anyone know the status of the package?

(Before you ask, NoteEdit looks good, but it crashed in the first 5 minutes of use, with loss of work.)  Unacceptable.

Is there anything that's simple, fast, and works, for writing and editing written music from the keyboard?

---

### Post by Stochastic on 2008-09-28
Have you installed the hardy-backports version of Denemo?  It's a newer version than the main repository, and from what I hear, it's more stable.

Unfortunately that's about all the updates on the way.  The version numbers in the Ubuntu package listing don't show any major changes on the way for Intrepid at the moment.

I personally find LilyPond to be the best notation editor, as you have ultimate control once you learn how to use the language efficiently.

---

### Post by VanillaMozilla on 2008-09-29
I have 0.7.5.  Where do I find Hardy Backports?  Thanks.

---

### Post by Stochastic on 2008-09-29
The hardy-backports repository can be enabled by going to System -> Administration -> Software Sources  then in the Updates tab check the hardy-backports option.  This will get you Denemo 0.7.7

edit: here's a quick quote from the Denemo website > For Linux check your package-system for Denemo.
Note the packages may be out of date since Denemo is growing quickly, and beware that versions prior to 0.7.7 are very buggy.

---

### Post by VanillaMozilla on 2008-09-29
Thanks.  I checked Hardy backports, uninstalled and reinstalled Denemo, then unchecked backports (I don't want everything updating from there).  I now have 0.7.7.  I'll soon see how it works.

---

### Post by roooz on 2008-10-04
Check out NtEd, really nice, really fast

[http://vsr.informatik.tu-chemnitz.de/staff/jan/nted/nted.xhtml](http://vsr.informatik.tu-chemnitz.de/staff/jan/nted/nted.xhtml)

---

