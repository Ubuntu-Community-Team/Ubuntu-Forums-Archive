---
title: "Will Qt 4.6 cause KDE 4.4 to go backwards?"
date: 2009-10-11
forum: The Cafe
---

### Post by isaacj87 on 2009-10-11
I apologize for the title, but there is something that I've been wondering about. Now, I'm not a developer and I don't have a full understanding of development cycles and whatnot, but I wonder: If KDE 4.4 will be switching over to Qt 4.6...

A) Will it cause KDE 4.4 to be a buggy release? There are a lot of new things being introduced in Qt 4.6 (my personal favorite being Qt Kinetic).

B) Will developers of the many apps of KDE (Kmail, Kopete, etc.) will they have to update to reflect the changes in Qt 4.6? How exactly does it work?

KDE 4.3 is a great release and I like that it's pretty solid. I would hate to see KDE go backwards...Obviously, I need to be educated on these types of things. Could someone help me out?

---

### Post by hoppipolla on 2009-10-11
This is interesting, and I'm not enough of a developer to say for certain.

So what are the changes in the new Qt?

Yeah I hope it doesn't have any negative effects either, but I would be surprised if it did as they are focusing on making the 4.x branch more stable at the moment.

I guess Qt is always going to be evolving and changing though, so the K team must have a way of dealing with that :)

---

### Post by isaacj87 on 2009-10-11
> **hoppipolla said:**
> 

So what are the changes in the new Qt?



[http://doc.qt.nokia.com/4.6-snapshot/qt4-6-intro.html]("http://doc.qt.nokia.com/4.6-snapshot/qt4-6-intro.html")

---

### Post by hoppipolla on 2009-10-11
> **isaacj87 said:**
> [http://doc.qt.nokia.com/4.6-snapshot/qt4-6-intro.html]("http://doc.qt.nokia.com/4.6-snapshot/qt4-6-intro.html")

Qt4 is crazy man it's developing so fast! I would be struggling if I was the KDE guys!

So much of that is jargon to me though O.O

I think we need some more technically-minded people or developers to join the thread tbh :)

---

### Post by Screwdriver0815 on 2009-10-11
[http://techbase.kde.org/index.php?title=Schedules/KDE4/4.4_Feature_Plan](http://techbase.kde.org/index.php?title=Schedules/KDE4/4.4_Feature_Plan)

in the german ubuntuusers forum we have a big KDE 4 thread and there also some developers are posting. Its great, BTW, to have such close contact user <--> developer  :D

there KDE 4.4 was not such a big issue but what I have understood, the KDE guys really look forward to 4.4 and qt 4.6 because they can improve KDE more on this base. They can finish the transition of applications from KDE 3 to KDE 4 (this is not finished yet) and also bring some improvements into Kwin and so on.

They also want to implement Tiling (must be something with windowmanagement) and transit Konqueror to Webkit.

so my impression is that the KDE guys are aware of this and they also have learned from the KDE 4.0 desaster, although all the dev's state that it was the mistake of the particular disros as KDE has clearly stated that KDE 4.0 is not intended for production.

---

### Post by GeneralZod on 2009-10-11
> **isaacj87 said:**
> 
A) Will it cause KDE 4.4 to be a buggy release? There are a lot of new things being introduced in Qt 4.6 (my personal favorite being Qt Kinetic).



Potentially some additional bugs will be introduced by the new features in Qt 4.6.  I wouldn't expect anything too severe, though: Qt Software do quite a lot of testing with KDE before release and will use *some* bugs introduced into KDE by the new Qt version to   [block Qt releases](http://labs.trolltech.com/blogs/2008/12/04/how-kde-4-is-blocking-qt-45/) until they (Qt Software) fix them.

> 
B) Will developers of the many apps of KDE (Kmail, Kopete, etc.) will they have to update to reflect the changes in Qt 4.6? How exactly does it work?


If they want to take full advantage of the new *features* they will of course have to update their apps.  If not, then (again, assuming Qt 4.6 doesn't have any regressions over 4.5) they don't have to do anything (and will generally automatically benefit from any speed/ stability improvements in the new version of Qt).

Edit: To expand on this latter point: Qt (like GTK) has a policy of source and binary compatibility within its major versions.  What this means is that, an app that was compiled against, say, Qt 4.0.0 should compile *without* changes to the source code, against Qt 4.6.whatever (source compatibility) and that the app should also run, *without* needing to be recompiled, against Qt 4.6.whatever (binary compatibility).

---

### Post by hoppipolla on 2009-10-11
Well there we go! Thanks guys! :)

---

### Post by jhahoneyk on 2009-10-14
It won't make KDE4 go backwards. Developers at KDE are working hard to port KDE3 apps to KDE4 (for example KDevelop has almost been ported to Qt4 and is under beta).
Work on integrating Qt Kinetic (mentioning as its my favorite too :) ) in KDE is going on (it was a GSoC2009 project). And lots more ...
So, Qt4.6 will just make the next release of KDE better for sure.

Shantanu Tushar,
Plasma contributor, KDE

---

### Post by hoppipolla on 2009-10-14
^_^ *loves KDE!*

---

### Post by SunnyRabbiera on 2009-10-14
My fear is that by the time KDE4 finally reaches the amount of features KDE 3.5 had it will be replaced by KDE 5

---

