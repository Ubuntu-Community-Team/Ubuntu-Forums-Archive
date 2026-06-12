---
title: "Should KDE and Qt Libraries Merge?"
date: 2010-10-31
forum: The Cafe
---

### Post by CraigPaleo on 2010-10-31
Is it too much, too fast? I'm not quite sure what I think about it yet. How about you?

[http://www.phoronix.com/scan.php?page=news_item&px=ODczOQ](http://www.phoronix.com/scan.php?page=news_item&px=ODczOQ)

---

### Post by Islington on 2010-10-31
sigh phoronix really? link to the source:[http://lists.kde.org/?l=kde-core-devel&m=128842761708404](http://lists.kde.org/?l=kde-core-devel&m=128842761708404)

and to tbh I dont know enough about either to have an opinion.

---

### Post by JDShu on 2010-10-31
Whats wrong with the Phoronix link? The source itself is just one post and theres alot of follow up that a regular person is not going to understand.

On the face of it, it sounds like a good idea since it seems to me that simplification is always good. However, I don't know how technically feasible it is, or how Nokia's involvement with Qt affects things.

---

### Post by CraigPaleo on 2010-10-31
> **Islington said:**
> sigh phoronix really? link to the source:[http://lists.kde.org/?l=kde-core-devel&m=128842761708404](http://lists.kde.org/?l=kde-core-devel&m=128842761708404)

and to tbh I dont know enough about either to have an opinion.

That ***IS ***cited within the article I posted.

---

### Post by CraigPaleo on 2010-10-31
> **JDShu said:**
> Whats wrong with the Phoronix link? The source itself is just one post and theres alot of follow up that a regular person is not going to understand.

On the face of it, it sounds like a good idea since it seems to me that simplification is always good. However, I don't know how technically feasible it is, or how Nokia's involvement with Qt affects things.

It does sound great but after 10 years of KDE 4 development to get where it is now, I'm afraid they'll never catch up with themselves with such radical changes one after another.

---

### Post by forrestcupp on 2010-10-31
It shouldn't if that includes cross-platform.  There are a lot of people in other OSs that use Qt who will never use KDE.  Qt != KDE.

---

### Post by CraigPaleo on 2010-10-31
> **forrestcupp said:**
> It shouldn't if that includes cross-platform.  There are a lot of people in other OSs that use Qt who will never use KDE.  Qt != KDE.

It would have to be cross-platform. And it's true *now* that Qt != KDE but If they do merge, devs would still be using Qt regardless of where the code originated. Devs wouldn't be forced to use KDE at all but KDE would depend on Qt libs instead of Qt libs + KDE libs, where there are redundancies.

---

### Post by Khakilang on 2010-10-31
I think they should get marry and live happily ever after.

---

### Post by nrs on 2010-11-01
> **forrestcupp said:**
> It shouldn't if that includes cross-platform.  There are a lot of people in other OSs that use Qt who will never use KDE.  Qt != KDE.
Right, and they wouldn't have to even if merged. It's just a set of (very good) libraries. Doesn't mean you'd have to switch to the desktop environment group X decided to build around it anymore than using KHTML/WebKit meant Apple had to switch to KDE/Konqueror.

---

### Post by Spice Weasel on 2010-11-01
No! I like being able to use Virtualbox and Arora without installing anything beginning with k. :)

---

### Post by del_diablo on 2010-11-01
KDElibs are far too bloat for being merged with QT.
So, really: Why is it a good idea?

---

### Post by 3Miro on 2010-11-01
I am support of everything that will lead KDE to not being such a memory hog. On the other hand, if it leads to KDE apps being an even bigger hogs on GTK platform, I think it is a bad idea.

---

### Post by forrestcupp on 2010-11-01
I think KDE just needs to get rid of all redundancies and completely depend on Qt, without them being merged.  I use Qt in Windows for GUI stuff, and I'd hate for it to be bogged down with a bunch of extra KDE crap.

I think, hopefully, that I'm misunderstanding, though.

---

### Post by mips on 2010-11-01
> **forrestcupp said:**
> I think KDE just needs to get rid of all redundancies and completely depend on Qt, without them being merged.

I think that's a good idea ;)

---

### Post by CraigPaleo on 2010-11-01
> **forrestcupp said:**
> I think KDE just needs to get rid of all redundancies and completely depend on Qt, without them being merged.  I use Qt in Windows for GUI stuff, and I'd hate for it to be bogged down with a bunch of extra KDE crap.

I think, hopefully, that I'm misunderstanding, though.

I think you're understanding somewhat. The way I understand it , apps like VB and VLC will still be able to use just the Qt GUI toolkit. But Qt is more than that. It's also an application framework. As it is now, you can use Qt or KDE frameworks (or just use a Qt front end) with the Qt toolkit. The application framework libraries are what they want to consolidate.

---

### Post by forrestcupp on 2010-11-01
> **CraigPaleo said:**
> I think you're understanding somewhat. The way I understand it , apps like VB and VLC will still be able to use just the Qt GUI toolkit. But Qt is more than that. It's also an application framework. As it is now, you can use Qt or KDE frameworks (or just use a Qt front end) with the Qt toolkit. The application framework libraries are what they want to consolidate.

But Qt is already a framework, and not just a GUI toolkit. I can use plain ol' Qt for networking, multimedia, animation, OpenGL and about everything I'd want it for.  Why would I need or want KDE libs added in?  What do KDE libs have that Qt doesn't already have?

I don't like it, and I hope it doesn't happen.  If they do, they'd better have the option to only use Qt.

---

### Post by Simian Man on 2010-11-01
Man posts impractical idea on a mailing list, Phoronix and UbuntuForums blow it out of proportion.  Sounds about right :).

---

### Post by CraigPaleo on 2010-11-01
> **forrestcupp said:**
> But Qt is already a framework, and not just a GUI toolkit. I can use plain ol' Qt for networking, multimedia, animation, OpenGL and about everything I'd want it for.  Why would I need or want KDE libs added in?  What do KDE libs have that Qt doesn't already have?

I don't like it, and I hope it doesn't happen.  If they do, they'd better have the option to only use Qt.

Kioslaves is one but there are more examples in the mailing list. It probably won't happen. I don't want it either but for different reasons. 

Anyway, If there's only Qt in the end, Qt would be the only option you'd have. 

> **Simian Man said:**
> Man posts impractical idea on a mailing list, Phoronix and UbuntuForums blow it out of proportion.  Sounds about right :).

True. :)  People just tend to infer a lot more than what's actually being said. The very first sentence on the Phoronix link says: "...there's a ***polarized discussion*** taking place right now among core KDE developers." The next thing you know, all hypotheticals are gone and people start acting as if it's going to happen. 

Maybe we should discuss [Project Ridley]("http://live.gnome.org/ProjectRidley") instead. That actually is happening. :)

---

