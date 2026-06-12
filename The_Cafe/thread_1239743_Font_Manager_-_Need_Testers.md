---
title: "Font Manager - Need Testers"
date: 2009-08-13
forum: The Cafe
---

### Post by Dies on 2009-08-13
If you're interested in helping test this app, please get the package from the downloads section at:

[http://code.google.com/p/font-manager/](http://code.google.com/p/font-manager/)

Testing:

* Install deb, make sure it installs without issue
* Make sure app appears in menus and runs when selected

Once familiar with the app, please start it from a terminal with

font-manager

and use it while paying attention that no warnings or errors appear in the terminal. 

If you encounter any problems, file an issue and include the terminal output if possible along with steps to reproduce.
If the issue involves a particular font please try to include the font or a link to it.


*At this point only file issues regarding bugs. Please do not file any feature requests or issues regarding enhancements.*


For anyone interested in contributing:

I am not an experienced programmer, so at this point I'm sure the code is pretty rough, any patches which cleanup, simplify or improve are more than welcome as long as they are well documented.

---

### Post by MikeTheC on 2009-08-13
Hmm...

I think I'd like to participate with this. Does your app support OpenType and PostScript Type 1 as well as TrueType?

---

### Post by Dies on 2009-08-13
> **MikeTheC said:**
> Hmm...

I think I'd like to participate with this. Does your app support OpenType and PostScript Type 1 as well as TrueType?

It doesn't really care about the type of font, it just uses whatever fc-list reports to populate the views. 

So yeah, any font that's usable on your system *should* show up.

---

