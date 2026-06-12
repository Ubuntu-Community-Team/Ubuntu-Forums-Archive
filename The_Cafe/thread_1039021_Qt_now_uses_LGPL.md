---
title: "Qt now uses LGPL"
date: 2009-01-14
forum: The Cafe
---

### Post by Erunno on 2009-01-14
The announcement is spreading fast but I haven't see a topic here yet so here we go: Qt is now available under the LGPL license. [1][2]

[1] [http://www.qtsoftware.com/about/news/lgpl-license-option-added-to-qt]("http://www.qtsoftware.com/about/news/lgpl-license-option-added-to-qt")
[2] [http://dot.kde.org/1231920504/]("http://dot.kde.org/1231920504/")

---

### Post by loell on 2009-01-14
that has been my last issue against Qt. :)

---

### Post by roschern on 2009-01-14
I am looking forward to be seeing a lot more Qt in Ubuntu...

---

### Post by mangar on 2009-01-14
Great news!!
Qt is the best toolkit I've ever used!
.
.
.

Goodbye, Gtk..

---

### Post by Rhapsody on 2009-01-14
I'm really liking this news. I've seen a couple of developers explicitly say they prefer Qt over GTK+, but end up using GTK+ in their applications because they're under non-free licenses. This may now see Qt and GTK+ judged purely on their merits rather than licensing issues.

---

### Post by mips on 2009-01-14
Could all the Nokia naysers that made such a big fuss when they purchased Ot from Trolltech step forward please ;)

Great news indeed! Everybody wins.

---

### Post by mips on 2009-01-14
> **roschern said:**
> I am looking forward to be seeing a lot more Qt in Ubuntu...

I doubt it, people are stuck in their ways and some people simply do not like Qt.

---

### Post by gnomeuser on 2009-01-14
While I am happy that QT now has a much nicer licensing scheme, I am however not planning to use it for anything. KDE is still hopelessly unusable and overloaded compared to GNOME, it just feels much less elegant. Where I do hope this leads though is to more cooperation on standards and perhaps unification in more areas between the two major toolkits.

Even at that, I believe more and more toolkit usage will move away from QT and GTK+ towards something like Silverlight. We are already seeing a desire to integrate traditional web tech like javascript into the desktop (the new GNOME shell e.g. is largely done using js), and there is a lot of sense in adopting the same set of technologies on and offline for many kinds of applications - Silverlight here is a very nice contender.

---

### Post by mangar on 2009-01-14
Gtk has been conceived as a reaction to Qt being, at the time, under propriety license, and later due to it being GPL (and thus preventing commercial adoption). Now that Qt is LGPL, There's now reason for Gtk continued existance.
The best of breed software libraries from Gtk can be merged with Qt (such as Pango, Tracker, gstreamer), and the rest can be deprecated. 

It does not mean that Gnome should cease to exists, as gnome principals calls for clean, minimalist desktops. On the otherhand, the FOSS GUI development can standartisize on Qt.

---

### Post by Trail on 2009-01-14
Great stuff. I quite liked QT4 when I developed a small personal project with it. I'll be sure to suggest it on my work environment should I have to develop a GUI application in the future.

Enjoyable development is enjoyable.

---

### Post by Mazza558 on 2009-01-14
> **gnomeuser said:**
> While I am happy that QT now has a much nicer licensing scheme, I am however not planning to use it for anything. KDE is still hopelessly unusable and overloaded compared to GNOME, it just feels much less elegant. 

I disagree. If anything, KDE 4.2 feels **more** elegant in my opinion than GNOME these days. In fact, if it wasn't for Gtk themes not being supported in 4.2, I'd be using it full-time.

---

### Post by ushimitsudoki on 2009-01-14
I'd **really** like to see an alternative DE based on QT, like XFCE uses GTK+.

It's a shame the only QT-based DE is KDE, because KDE4.x is such an epic fail at every level it reflects badly upon QT, which is a very nice toolkit based on my experience (limited to Python).

---

### Post by roschern on 2009-01-14
> **gnomeuser said:**
> While I am happy that QT now has a much nicer licensing scheme, I am however not planning to use it for anything. KDE is still hopelessly unusable and overloaded compared to GNOME, it just feels much less elegant. Where I do hope this leads though is to more cooperation on standards and perhaps unification in more areas between the two major toolkits.

The fact that you don't like KDE doesn't mean you can't develop great Gnome apps with Qt... I think this will strengthen both Gnome and KDE.

---

### Post by k@e on 2009-01-14
Not trying to move too far away from this topic but does anyone know if Qt 4.5 will find its way into jaunty? According to what I have read, it is scheduled to be released in March.

---

### Post by gnomeuser on 2009-01-14
> **roschern said:**
> The fact that you don't like KDE doesn't mean you can't develop great Gnome apps with Qt... I think this will strengthen both Gnome and KDE.

I never said that this was fundamentally impossible, however the major consumer of QT is KDE and to build GNOME apps that live up to the term "GNOME apps" you will have to use the platform which extends far beyond GTK+. E.g. how to interact with GConf, gnome-session manager, how to fit the look and feel of the app into the existing GNOME environment. QT cannot do this currently and we need to work on this, luckily this is exactly the space FreeDesktop.org occupies for us.

All this goes towards showing that it is not feable to do such development currently, thus I hope now that the licensing will allow for more cooperation that we will actually see FreeDesktop.org play a bigger role in helping us find common ground, define standards and letting us cut down on duplication. This way we could get to a point where a GNOME or KDE app might become closer to a FreeDesktop.org app that would fit into any compliant environment not just KDE or GNOME. 

There would be great wins to be had in doing this, less code and more consumers would lead to much more stable platform with a greater range of best of breed functionality.

One might envision handing over GTK/Glib/Pango and QT over to a common toolkit alliance with the plan of creating GTK4 and QT5 as sharing the same core. Unifying the two will take many years but would be rewarding especially if we can work towards embracing more market segments, both toolkits needs to look beyond the desktop. If we fail to do this, both toolkits will lose their relevance quickly, which on the whole would be very sad indeed. There is a need to use the same tools and languages for deployments ranging from the very small embedded or special usage devices (phones, MIDs, settop boxes and netbooks) through the desktop and onto the RIA web application space. We currently don't offer that with either framework, in fact the only thing Free Software offers that will do this is Moonlight.

---

### Post by mips on 2009-01-14
> **k@e said:**
> According to what I have read, it is scheduled to be released in March.

If that's the case then probably 'no' as it is only a month before 9.04 release.

---

### Post by mangar on 2009-01-14
There's no need to merge Gtk and Qt. Qt is better, all around.
If there are some points of strength to Gtk - Gio, Gstreamer, Tracker, Pango - those components can be ported to Qt. 

The rest (widget engine, hardware abstraction, networking, etc), can be safely retired.

Btw:
Was Gtk migrating to Webkit anyway? Why put the boundary there?

---

### Post by Mr. Picklesworth on 2009-01-14
Why *is* Qt considered so vastly superior? I really would like to know, since it seems I'm doomed to using it eventually.

On my end, I generally love GTK's API, and I love that it builds on fluid layouts by default so that everything with GTK is resizable and flexible unless the developers are explicitly trying to do it wrong. I found the whole ComboBox + CellRenderer + ListModel thing a bit insane, but the end result is pretty. It means that more advanced things like showing progress bars, icons or other widgets inside combo boxes are completely trivial.
Pango and Cairo are each really, really important things. Not only are they used widely in the raw, but they are also used in piles of canvas libraries. Oh, and they produce pretty results.

Whenever I play with Qt I see some awesome animation, and definitely the smooth resizing stuff is a tweak we are still waiting for. It definitely does everything GTK does. However, nothing happens that really makes me think "this is unique. This is worth GNOME forgoing a year of progress." Is that an adequate assumption, or am I missing something?

On either end, we still sorely need a more context-aware theme engine, for example that can change its behaviour based on where a widget is placed relative to others.

Here's an issue that transcends toolkit: KDE and GNOME have very different concepts for how applications should interact with the user. Using the same toolkit may make people start to agree more readily on these things, but I only want to see it done GNOME's way... and I bet KDE people only want to see it done KDE's way :P
In a sense, having the distinct toolkits almost plays to our advantage, except for that lower level stuff. Maybe everyone should just give up and start building on the Enlightenment Foundation Libraries. Edje would solve this problem *for us*!

---

### Post by Keyper7 on 2009-01-14
> **Mr. Picklesworth said:**
> Whenever I play with Qt I see some awesome animation, and definitely the smooth resizing stuff is a tweak we are still waiting for. It definitely does everything GTK does. However, nothing happens that really makes me think "this is unique. This is worth GNOME forgoing a year of progress." Is that an adequate assumption, or am I missing something?

I've never used Qt, but according to what I hear its advantages are under the hood: cleaner API, better documentation and, lately, an impressive effort to be completely portable to Windows and Mac.

---

### Post by ZuLuuuuuu on 2009-01-14
Does this mean, we can use Qt even for making closed source, commercial software without paying for the license?

---

### Post by Keyper7 on 2009-01-14
> **ZuLuuuuuu said:**
> Does this mean, we can use Qt even for making closed source, commercial software without paying for the license?

You can now link it to proprietary software without paying the license, yes.

---

### Post by cardinals_fan on 2009-01-14
I'm going mostly Qt anyway.  This is just the icing on the cake :)

---

### Post by ZuLuuuuuu on 2009-01-14
> **Keyper7 said:**
> You can now link it to proprietary software without paying the license, yes.

Then, Qt will clearly widen its usage percentage over GTK. GTK is still the only C framework for GUI and it is preferred by a lot of people because of its elegance etc. but Qt has already more features and a lot of people like native looking applications, also the biggest reason not to use Qt is now eliminated. So, GTK will not die but the development might slow down and we might see less and less GTK applications over time.

But this means the death of wxWidgets, I guess.

---

### Post by jrusso2 on 2009-01-14
> **mips said:**
> I doubt it, people are stuck in their ways and some people simply do not like Qt.

QT has been under the GPL for the Linux version anyway for years.  And it has not changed people who don't like its feelings.

---

### Post by Mr. Picklesworth on 2009-01-14
GPL was still a restrictive license, though. You'll notice that a lot of commercial software -- which we do still need to support -- uses GTK if it wants to have a native Linux version and is not under GPL. (Then there are the nitwits who use TK just to torment everyone).
GTK, on the other hand, is under the LGPL (which Qt is now going to use, too). This means that it can be linked to safely; one need only be concerned about licenses if he is actually modifying the library directly.

This pretty much eliminates the only reason I didn't like KDE from a development perspective. And it's Nokia, too, whose open source contributions I respect.

Still, only time will tell how this turns out. With regards to the free desktop thing, I think we are seeing the growth of a lot of technologies that work consistently across either one. After all, the front end is somewhat easy to add when all the back end stuff is in place. That practise is getting more common and a bit easier nowadays, so the issue of integration is somewhat smaller than it was before.

---

### Post by bruce89 on 2009-01-14
> **mangar said:**
> If there are some points of strength to Gtk - Gio, Gstreamer, Tracker, Pango - those components can be ported to Qt. 

No they can't. It would require a complete rewrite, and a migration to another language. In other words, it will never happen.

Funny thing is that yesterday my first patch for GTK+ was committed.

---

### Post by BGFG on 2009-01-14
> **mangar said:**
> Gtk has been conceived as a reaction to Qt being, at the time, under propriety license, and later due to it being GPL (and thus preventing commercial adoption). Now that Qt is LGPL, There's now reason for Gtk continued existance.
The best of breed software libraries from Gtk can be merged with Qt (such as Pango, Tracker, gstreamer), and the rest can be deprecated. 

It does not mean that Gnome should cease to exists, as gnome principals calls for clean, minimalist desktops. On the otherhand, the FOSS GUI development can standartisize on Qt.

I'm new to all of this, but was gnome created solely because Qt was proprietary? 
Also, I know many complain about Qt's look but I recently installed SMplayer and after a little tweaking in Qt4 settings, i have to say that the GUI is smooth, friendly and pleasant to use.
The real question is if a desktop environment is done in Qt, how does it stack up in terms of resource use and so on.
Is Qt where the Ubuntu desktop is heading ?

---

### Post by bruce89 on 2009-01-14
> **BGFG said:**
> I'm new to all of this, but was gnome created solely because Qt was proprietary?

GNOME was created because KDE depended on Qt which at the time was licensed under the QPL, which they said was "a non-copyleft free software license which is incompatible with the GNU GPL. It also causes major practical inconvenience, because modified sources can only be distributed as patches."

> **BGFG said:**
> Is Ot where the Ubuntu desktop is heading ?

No, nor Qt for that matter.

---

### Post by mangar on 2009-01-14
@bruce89
All the libraries I've mentioned (and I should have added Cairo), 
are not dependent on any specific Gnome technology, rather, those are basic, interchangeble components.

I agree that merging them into the mainline Qt code will require some extensive refactoring, but I'm not terribly sure that as a first step a complete rewrite will be neccesary.

---

### Post by bruce89 on 2009-01-14
> **mangar said:**
> @bruce89
All the libraries I've mentioned (and I should have added Cairo), 
are not dependent on any specific Gnome technology, rather, those are basic, interchangeble components.

Tracker certainly depends on GNOME things. Also, all these things have Qt equivalents.

---

