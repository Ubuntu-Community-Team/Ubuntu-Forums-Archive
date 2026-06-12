---
title: "Qt firefox"
date: 2008-12-12
forum: The Cafe
---

### Post by wildman4god on 2008-12-12
I heard that nokia was helping mozzila port firefox to qt so it integrates better with kde the problem is I can't find any new info on the project, the newest I can find is about mid september, 2008 has anybody else here heard of this project and know the current status of it? last i checked the qt firefox port was in pre alpha but that was sept. I would hope that after almost 3 months with mozilla and nokia working on it we would at least have and alpha release.

---

### Post by happysmileman on 2008-12-12
I've built it from source recently, very buggy and I had to add a few lins of code myself to even get it to build, but it works far better than that alpha (showing that at least SOME work has been done on it).

It still looks hideously ugly and has many rendering bugs, don't expect it any time soon. The fact that it won't even build without adding a few lines (adding some QT value to an enum and changing a function declaration with seems to be outdated was what I did, as well as couple of other small things, nothing that requires actual knowledge of the FF codebase) suggest that it isn't being tested or developed much.

---

### Post by wildman4god on 2008-12-12
> **happysmileman said:**
> I've built it from source recently, very buggy and I had to add a few lins of code myself to even get it to build, but it works far better than that alpha (showing that at least SOME work has been done on it).

It still looks hideously ugly and has many rendering bugs, don't expect it any time soon. The fact that it won't even build without adding a few lines (adding some QT value to an enum and changing a function declaration with seems to be outdated was what I did, as well as couple of other small things, nothing that requires actual knowledge of the FF codebase) suggest that it isn't being tested or developed much.

Do you think it'll be ready by kubuntu 9.04 release in april, because thats when I am switching from gnome to kde and I would like to run firefox without using the gtk+ engine in kubuntu (I hear that it requires more rescources to run and slows down proformance as well as not integrating well)

---

### Post by Giant Speck on 2008-12-12
There's a QT Firefox in the KDE 4.2 Beta 1 repos.  I don't know if that is what you are talking about.

---

### Post by bash on 2008-12-12
Are they actually porting the Firefox fort-end to Qt or are the just theming XUL to look like your current Qt/KDE Theme as they did for GTK+/GNOME look-alike?

---

### Post by happysmileman on 2008-12-12
> **bash said:**
> Are they actually porting the Firefox fort-end to Qt or are the just theming XUL to look like your current Qt/KDE Theme as they did for GTK+/GNOME look-alike?

As far as I know they don't just "theme" XUL, from what I've seen in the code they use XUl just as they are now but use QPainter to display things, right now it looks nothing like your current Qt/KDE theme (last time I checked anyway), but I've seen somewhere that any QWidget can be basically displayed in a QPainter, so in theory it's possible to do this in a way that would both respect your theme and require no large changes to any other aspect of Firefox.

Of course I really have no idea what I'm talking about, someone correct me if that's wrong.

> There's a QT Firefox in the KDE 4.2 Beta 1 repos. I don't know if that is what you are talking about.

That's a very old build and freezes constantly (the trunk version as of last time I checked only freezesalmost constantly), AFAIK only way to get any recent build is to build yourself, if anyone can link to updated debs or anything it'd be great though :P

---

