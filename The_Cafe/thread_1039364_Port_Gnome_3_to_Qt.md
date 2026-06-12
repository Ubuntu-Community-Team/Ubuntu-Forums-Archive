---
title: "Port Gnome 3 to Qt"
date: 2009-01-14
forum: The Cafe
---

### Post by gururise on 2009-01-14
I am an avid Gnome user, and have done much cross-platform development using Gtk+ and the [Gtkmm]("http://www.gtkmm.org")C++ bindings; however, now that Qt 4.5 is going LGPL, is there a reason to not port GnomeLibs over to Qt for Gnome 3.0?

I am not suggesting the demise of Gnome. Gnome 3 was to break API/ABI compatibility with Gnome 2.x, so now would be a good time to discuss the feasibility of porting GnomeLibs to Qt for Gnome 3.  The biggest barrier I see is Qt is based upon C++ and Gtk is C; however, this does not have to be an insurmountable problem. I'm curious to know what others think. :)

---

### Post by Keyper7 on 2009-01-14
This certainly gives food for thought in the current GTK3/Gnome3 discussion. Had a definitive roadmap for Gnome 3 already been stabilished, this idea would probably be rejected. But since they are still on the brainstorming phase, this might be considered...

---

### Post by Half-Left on 2009-01-14
hahahahaha, thats just to funny, you have no idea. :lolflag:

---

### Post by bruce89 on 2009-01-14
If after the 5 years it would take GNOME to port to Qt Nokia pushes out Qt 5.x, that would be interesting.

Anyway, it won't happen ever. Nokia has control of Qt, so they can do anything they want. GTK+ is controlled by GNOME, so they can decide where it goes.

Hopefully the level playing field will make GTK+ improve.

---

### Post by Changturkey on 2009-01-14
Get ready for the #$@$-storm.

---

### Post by Half-Left on 2009-01-14
> **bruce89 said:**
> If after the 5 years it would take GNOME to port to Qt Nokia pushes out Qt 5.x, that would be interesting.

Anyway, it won't happen ever. Nokia has control of Qt, so they can do anything they want. GTK+ is controlled by GNOME, so they can decide where it goes.

Hopefully the level playing field will make GTK+ improve.

GTK is not controlled by GNOME 
LMAO

GNOME says which which toolkit they want to use and use it, they dont "control" since it's GPL and anyone can use it as long as they abide by it's license.

---

### Post by Giant Speck on 2009-01-14
I think I'm confused...

---

### Post by v8YKxgHe on 2009-01-14
> **Half-Left said:**
> GTK is not controlled by GNOME 
LMAO

GNOME says which which toolkit they want to use and use it, they dont "control" since it's GPL and anyone can use it as long as they abide by it's license.

GTK is developed by the GNOME Foundation, so yes they do control it. Sure, anyone can use it, but by no means can anyone say what goes in, and out, of GTK - only they can, since it is their project. Yes, anyone can create a fork of it and do with it what they will, though that is no longer the 'official' GTK that GNOME would use (unless of course the changes were merged back upstream to them).

---

### Post by Half-Left on 2009-01-14
> **AlexC_ said:**
> GTK is developed by the GNOME Foundation, so yes they do control it. Sure, anyone can use it, but by no means can anyone say what goes in, and out, of GTK - only they can, since it is their project. Yes, anyone can create a fork of it and do with it what they will, though that is no longer the 'official' GTK that GNOME would use (unless of course the changes were merged back upstream to them).

It's just a toolkit in the end that anyone can use, I just found moving to Qt funny, hell freeze over they would port to Qt and dump their own toolkit.

---

### Post by SomeGuyDude on 2009-01-14
I dislike QT and everything it stands for. GTK all the way, baby.

---

### Post by v8YKxgHe on 2009-01-14
[QUOTE=Half-Left]It's just a toolkit in the end that anyone can use, I just found moving to Qt funny, hell freeze over they would port to Qt and dump their own toolkit.[/QUOTE]

Indeed it is, my point was more at your claim that GTK was not controled by GNOME (Foundation), which is false.

---

### Post by Half-Left on 2009-01-14
> **AlexC_ said:**
> Indeed it is, my point was more at your claim that GTK was not controled by GNOME (Foundation), which is false.

I always thought it the case that GTK was made up of GNOME devs, I guess it depends on your interpretation of controlled by.

---

### Post by v8YKxgHe on 2009-01-14
> **Half-Left said:**
> I always thought it the case that GTK was made up of GNOME devs, I guess it depends on your interpretation of controlled by.

It is, but you can't just submit a patch which changes GTK in a direction that *you* want, it would be reviewed and either accepted, declined or modified by someone/group of developers (what is a group of developers? A pack, hurd, flock? =3). It is the project leaders that control how their project (GTK) goes, and have the final say. Just because something is open source doesn't mean that anyone and everyone can change how the project goes, that would be a nightmare.

---

### Post by chucky chuckaluck on 2009-01-14
wouldn't porting it to fltk make it faster?

---

### Post by gururise on 2009-01-14
In the long run, porting Gnomelibs to use Qt would free up developers to work on Gnome, the desktop framework.

Qt, thus Nokia, would support improvements/development to Qt, which would trickle back to Gnome for free.. Thus obviating the need for developers to work on Cairo, GnomeVFS, and many other parts of Gnome that see little love. 

Sure, there would be much work involved in a port; however, what better time to break with the past than Gnome 3 Brainstorming phase.  Gtk+, while an admirable effort, is nonetheless technically far inferior to Qt and takes quite a bit of development effort away from Gnome the Desktop.  

By moving Gnome 3 to Qt, Gnome would sidestep many development issues and would also gain many more development resources that are currently used to maintain Gtk.  Not to mention, it would help the freedesktop.org movement considerably and make things easier for App developers wanting to develop for both environments.

---

### Post by gletob on 2009-01-14
> **SomeGuyDude said:**
> I dislike QT and everything it stands for. GTK all the way, baby.

Amen.

---

### Post by tbroderick on 2009-01-14
> **SomeGuyDude said:**
> I dislike QT and everything it stands for. GTK all the way, baby.

What does QT stand for?

---

### Post by GeneralZod on 2009-01-14
> **tbroderick said:**
> What does QT stand for?

QuickTime

:rimshot:

---

### Post by creek23 on 2009-01-14
> **tbroderick said:**
> What does QT stand for?

Quasar Technologies -- I supposed.

---

### Post by phrostbyte on 2009-01-14
Porting an entire desktop to a new graphical toolkit is basically like rewriting it. It would take years! 

It won't happen I don't think.

---

### Post by gururise on 2009-01-14
> **phrostbyte said:**
> Porting an entire desktop to a new graphical toolkit is basically like rewriting it. It would take years! 

It won't happen I don't think.

The Gnome 1 -> Gnome 2 transition was exactly that: an entire Re-Write.  Who would argue that we are not better off today with ditching Gtk1.0 and moving to Gtk2.0...? Sure there were teething problems, but in the long run, it was the right thing to do, as we now have a working file dialog, printing system, etc... In fact, many of the teething problems were due to the relative immaturity of Gtk2.0.  On the contrary, Qt 4.5 is very mature and stable.  

I imagine in the long run, replacing Gtk with Qt would bring similar, if not more benefits.

---

### Post by phrostbyte on 2009-01-14
> **gururise said:**
> The Gnome 1 -> Gnome 2 transition was exactly that: an entire Re-Write.  Who would argue that we are not better off today with ditching Gtk1.0 and moving to Gtk2.0...? Sure there were teething problems, but in the long run, it was the right thing to do, as we now have a working file dialog, printing system, etc... In fact, many of the teething problems were due to the relative immaturity of Gtk2.0.  On the contrary, Qt 4.5 is very mature and stable.  

I imagine in the long run, replacing Gtk with Qt would bring similar, if not more benefits.

Well I think it's a bit different, GNOME was much smaller back then and easier to completely modify. Also Gtk1 -> Gtk2 is still easier then Gtk -> Qt. For one, Qt requires a different programming language then what most of Gnome is written in.

---

### Post by Simian Man on 2009-01-14
Rest assured that this will not ever happen.

---

### Post by gururise on 2009-01-14
> **phrostbyte said:**
> For one, Qt requires a different programming language then what most of Gnome is written in.

There exists, or used to exist, a C wrapper to Qt.  This C wrapper could be brought back to life and used as the basis for the port of Gnomelibs to Qt.

And with the proper Qt2Gtk engine running, the widgets would look exactly the same as they do now.. In fact, if done right, most end-users would not even know that Gnome switched from Gtk+ to Qt.

---

### Post by steeleyuk on 2009-01-14
It would be more difficult to port GNOME to Qt than it would be to start a new desktop environment from scratch.

You'd spend years trying to get back to where you where and still improve on it at the same time. That would also go alongside having to create time for developing new features and apps.

---

### Post by gururise on 2009-01-14
> **steeleyuk said:**
> It would be more difficult to port GNOME to Qt than it would be to start a new desktop environment from scratch.

You'd spend years trying to get back to where you where and still improve on it at the same time. That would also go alongside having to create time for developing new features and apps.

Apparently Mark Shuttleworth, the head financier of the Ubuntu Project, believes there is merit in [porting Gnome to use Qt]("http://tech.slashdot.org/article.pl?sid=08/07/14/1245204&from=rss"). 

Its about time to standardize on one GUI toolkit so that we can compete against Windows and MacOS. Their would also be other advantages, in terms of memory usage, to converging the libs.

---

### Post by SunnyRabbiera on 2009-01-14
> **gururise said:**
> Apparently Mark Shuttleworth, the head financier of the Ubuntu Project, believes there is merit in [porting Gnome to use Qt]("http://tech.slashdot.org/article.pl?sid=08/07/14/1245204&from=rss"). 

Its about time to standardize on one GUI toolkit so that we can compete against Windows and MacOS. Their would also be other advantages, in terms of memory usage, to converging the libs.

But the thing is there would not be choice.
I dont think getting rid of GTK is a good idea, as really we dont want to be like OSX or Windows... the same boring interface, the same boring approach to things...

---

### Post by gururise on 2009-01-14
> **SunnyRabbiera said:**
> But the thing is there would not be choice.
I dont think getting rid of GTK is a good idea, as really we dont want to be like OSX or Windows... the same boring interface, the same boring approach to things...

I am not suggesting to get rid of GNOME.  Rather, replace the Gtk toolkit with Qt.
The Desktop Environments would still be different, and based upon differing libraries, in this case GnomeLibs and KDELibs.  

A user would still have the same choice he has today, and would still be able to choose between Gnome or KDE (or any other DE available). Replacing Gtk with Qt in Gnome would reduce memory usage of having both libs on your system and in memory, and would simplify the development of apps that work well within both desktop environments. GNOME would still exist, as would KDE.  In fact, if done properly, GNOME users would not even notice a change, other than the ability to use KDE themes/widgets and reduced memory usage.

---

### Post by *g!t5^_)*(H on 2009-01-14
Mark is right

Gnome must improve (in many ways) and a good way to do it, is using Qt.

Of course it won't happen, maybe a working group can start creating a new desktop environment with the goals of GNOME, but also improving it where GNOME fails.

Qt has a lot of advantages, now is supported by NOKIA and its license is all right. GNOME (or a kind of) using Qt means the most powerful and usable desktop ever done (even better than Mac OS X if it is done all right).

Hopefully someone (probably someone from NOKIA) will notice it, and will skip KDE (the way it behaves is not nice with new users) and will start doing a kind of GNOME (or a kind of Aqua, or just a better user interface) easy to use (and configure) getting the power of Qt.

That day, if it comes, I probably will use this new software even if it means say goodbye to Ubuntu. Because what we all want, apart of software freedom, is good software.

GNOME engineers must know sometimes, the best way to go on, is just leave the past behind, and expend all the efforts evolving the ideas but rewriting source from the scratch.

In my opinion the good part of KDE is Qt (with some great software and design decisions) and the bad part of GNOME is GTK

Of course this change is radical, and doing it means some loses. But loses are not as big as advantages, because using Qt as "the linux paradigm" means unifying linux and making easier for software companies, to go "the linux way"

---

### Post by Skripka on 2009-01-14
> **gururise said:**
> y of Gtk2.0.  On the contrary, Qt 4.5 is very mature and stable.  

I imagine in the long run, replacing Gtk with Qt would bring similar, if not more benefits.

Hell, QT4.5 isn't even in the Ubuntu repos yet...which is a source of many problems on KDE4.2 and Kubuntu--as problems in 4.4.3 are solved, but cannot be seen as fixed by end users as Ubuntu is lagging (far) behind.

Yes switching from GTK to QT would in the long run, save:

-Time
-Effort
.
.
.

And make sense.  which is exactly why it will never happen.

---

### Post by Changturkey on 2009-01-14
> **Skripka said:**
> 
And make sense.  which is exactly why it will never happen.

So true..

---

### Post by ghindo on 2009-01-14
> **SomeGuyDude said:**
> I dislike QT and everything it stands for. GTK all the way, baby.Why do you dislike QT?  And what exactly does it stand for?  Please elaborate.

---

### Post by bruce89 on 2009-01-14
> **gururise said:**
> Apparently Mark Shuttleworth, the head financier of the Ubuntu Project, believes there is merit in [porting Gnome to use Qt]("http://tech.slashdot.org/article.pl?sid=08/07/14/1245204&from=rss"). 

Most of what Mark says is aspirational nonsense.

> **ghindo said:**
> Why do you dislike QT?  And what exactly does it stand for?  Please elaborate.

There are some arguments against it including the fact it is all-encompassing, which is somewhat against the UNIX philosophy (Qt is not just a UI toolkit, it has a media library, Web rendering library etc.). Another is that Nokia are (at the moment) the only company developing it. Perhaps others can come up with more arguments.

---

### Post by zmjjmz on 2009-01-14
tl;dr, but I believe the main problem with it is that Qt is licensed under the LGPL, not the GPL.

---

### Post by ghindo on 2009-01-14
> **zmjjmz said:**
> tl;dr, but I believe the main problem with it is that Qt is licensed under the LGPL, not the GPL.Qt *is* licensed under the GPL.  It's licensed under like, four different licenses.

---

### Post by Keyper7 on 2009-01-14
> **bruce89 said:**
> There are some arguments against it including the fact it is all-encompassing, which is somewhat against the UNIX philosophy (Qt is not just a UI toolkit, it has a media library, Web rendering library etc.).

In my opinion this is a very weak argument. It's not like you're forced to use the entire library.

> **bruce89 said:**
> Another is that Nokia are (at the moment) the only company developing it.

Quote from [ars technica](http://arstechnica.com/news.ars/post/20090114-nokia-qt-lgpl-switch-huge-win-for-cross-platform-development.html):

> In addition to adopting the LGPL license for Qt, Nokia will also be completely changing Qt's development model to make it more inclusive and transparent. The source code will be moved to a publicly-accessible Git repository so that the latest changes will always be visible. The use of Git, a distributed version control system, will make it easier for third-party developers to participate directly in the process of improving Qt. To further reduce the barrier to participation, Nokia plans to accept code from contributors without requiring copyright assignment. 

---

### Post by bruce89 on 2009-01-14
> **Keyper7 said:**
> In my opinion this is a very weak argument. It's not like you're forced to use the entire library.

I know, that's why I hope other people have better ones.

> **Keyper7 said:**
> Quote from [ars technica](http://arstechnica.com/news.ars/post/20090114-nokia-qt-lgpl-switch-huge-win-for-cross-platform-development.html):

That's why I said "at the moment".

Who honestly thinks that "porting" GNOME to Qt would be worth the years of effort?

---

### Post by CarpKing on 2009-01-14
> **zmjjmz said:**
> tl;dr, but I believe the main problem with it is that Qt is licensed under the LGPL, not the GPL.

You have that backwards.  GTK is under the LGPL (Qt will be too in the near future); Qt's GPL license is an obstacle to developers of closed-source apps, and IIRC there were a variety of other license issues that resulted in GNOME choosing GTK, some of which have now been addressed.  

Having only one main toolkit would make things simpler for people developing things on Linux, but I think the time it would take to rewrite GNOME would be better spent on improving GTK.  If someone wants to write a Gnome-like DE in Qt, they're welcome to it.

---

### Post by days_of_ruin on 2009-01-14
> **tbroderick said:**
> What does QT stand for?

Thats just it, it doesn't stand for anything.Its actually Qt and its 
supposed to be pronounced "cute" as in kittens.

EEEEEEEEEEEEEEEEEEEWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWWW.

---

### Post by days_of_ruin on 2009-01-14
> **bruce89 said:**
> Most of what Mark says is aspirational nonsense.


+1. Like how he wants ubuntu to look as good as OS X but then decides
that the community is no longer making the theme.Who is making the new ubuntu theme?Probably Rod "Rod" Blagoevich.Which is why we haven't seen
anything of it.

---

### Post by igknighted on 2009-01-14
> **Simian Man said:**
> Rest assured that this will not ever happen.

I'm not saying I think that it should happen, but completely closed-minded thoughts like this are what keeps software projects (gnome or otherwise) from moving forward.  As mentioned in the thread, there are obvious benefits and obvious drawbacks.  I think it is worth at least having the discussion and exploring the possibility.

---

### Post by ZuLuuuuuu on 2009-01-15
I don't get what is the so bad about GTK. I used it with some C and Vala coding and it is really elegant and very fun to code with, also pretty stable. What makes you think GTK is a fail and should be replaced with Qt? What makes you think GTK should break ABI/API compatibility? What are the disadvantages of current API, for example?

Surely, GTK is suffering the things almost all the open source software is suffering: "being a community effort". It is mostly a project people contribute in their free time as opposed to Qt. So, it is not moving as fast as Qt from Trolltech which is now also supported by Nokia. But it is not doing that bad.

I think if GNOME is to use Qt the result will be something between GNOME and KDE, not just GNOME with Qt, because Qt is one of the main things what makes KDE, KDE.

---

### Post by wersdaluv on 2009-01-15
I think, it's a good idea. A toolkit, in my opinion, is something different DEs could agree with. That way, there would be one toolkit that would get a lot of attention and development. It means a better toolkit and more universality in the Linux desktop. I just don't know much about technical aspects so I can't tell how feasible it is.

Besides, qt can do this--> [http://code.google.com/p/qgtkstyle/](http://code.google.com/p/qgtkstyle/)

---

### Post by Simian Man on 2009-01-15
> **igknighted said:**
> I'm not saying I think that it should happen, but completely closed-minded thoughts like this are what keeps software projects (gnome or otherwise) from moving forward.  As mentioned in the thread, there are obvious benefits and obvious drawbacks.  I think it is worth at least having the discussion and exploring the possibility.

I'm not saying I think it should or shouldn't happen either - honestly I don't care much - I'm just saying that it won't happen.  The main reason is that GTK is a C library which fills a very important need.  For example, GTK allows for development in [many different languages]("http://www.gtk.org/language-bindings.html") (because C is the Lingua Franca of programming languages) and GTK is targeted by higher level libraries such as wxWidgets and the Gnome and Xfce libs.  There is no way that the Gnome devs would let GTK die.

---

### Post by Seq on 2009-01-15
> **gururise said:**
> In the long run, porting Gnomelibs to use Qt would free up developers to work on Gnome, the desktop framework.

This duplication of effort is such a waste! Does anybody have a contact at Nokia? I'd like to ask them to stop this whole silly QT thing and help maintain GTK+. It would free up the Gnome devs quite a bit.

Also, KDE should switch to GTK+ (KDE5, here we come!). They just did a rewrite, and I hear it doesn't work too well. Everything would still be fresh in their minds for the next rewrite! They're practically in a better position to migrate toolkits!

---

### Post by geoken on 2009-01-15
> **Seq said:**
> This duplication of effort is such a waste! Does anybody have a contact at Nokia? I'd like to ask them to stop this whole silly QT thing and help maintain GTK+. It would free up the Gnome devs quite a bit.

Also, KDE should switch to GTK+ (KDE5, here we come!). They just did a rewrite, and I hear it doesn't work too well. Everything would still be fresh in their minds for the next rewrite! They're practically in a better position to migrate toolkits!

I understand the tongue in cheek argument you're making, but your not taking into account the inherent strengths of the platforms.

People aren't saying the decision to move to Qt should be completely arbitrary. They're saying (not that I necessarily agree) that Qt is a better framework and has better cross platform compatibility. If GTK was widely accepted to be better than Qt, I'm sure people would actually be making comments similar to yours.

---

### Post by Vadi on 2009-01-15
This would be a very silly idea.

GTK is practically designed to be used in Gnome. It helps to handle the Gnome HIG very well. Qt on the other hand is designed for commercial purposes mostly - and that means get the product done cheap, fast, and disregard the quality of the interface.

---

### Post by Keyper7 on 2009-01-15
> **Vadi said:**
> Qt on the other hand is designed for commercial purposes mostly - and that means get the product done cheap, fast, and disregard the quality of the interface.

[citation needed]

---

### Post by cardinals_fan on 2009-01-15
> **Vadi said:**
> This would be a very silly idea.

GTK is practically designed to be used in Gnome. It helps to handle the Gnome HIG very well. Qt on the other hand is designed for commercial purposes mostly - and that means get the product done cheap, fast, and disregard the quality of the interface.
Pretty strong statements there.  Got any sources?

---

### Post by Tom Mann on 2009-01-15
I believe that Gnome should stay with GTK+ - I believe it's Gnome's need that help push GTK+ along. It's the same with KDE and Qt, the desktop's needs drive the development of the toolkit.

I personally think Qt is fantastic and has a better chance of going multi-platform - it's already being seen with VLC's latest version in Windows... Embedded video at last! Gnome will fight back, and GTK+ will eventually become a better toolkit, then it'll be Qt's turn to become better, ad infinitum.
The competition will continue to drive quality software into users hands.

---

### Post by Seq on 2009-01-15
> **geoken said:**
> I understand the tongue in cheek argument you're making, but your not taking into account the inherent strengths of the platforms.

Neither was the post I was quoting (nor many others).

> **geoken said:**
> People aren't saying the decision to move to Qt should be completely arbitrary. They're saying (not that I necessarily agree) that Qt is a better framework and has better cross platform compatibility. If GTK was widely accepted to be better than Qt, I'm sure people would actually be making comments similar to yours.Gnome can't really be "moved" to QT anyway, so the entire discussion is pointless. Essentially, an entirely new desktop environment would exist that would carry the name "Gnome", but have no technical relationship to the previous releases.

I don't know why if so many believe this should be the way forward, they don't just do it themselves instead of whining about what "Gnome" should do. If there is enough demand for GnomeHIG + C++ + QT, then surely one can find others to help.

---

### Post by Vadi on 2009-01-15
Yeah. Look up history of Qt. I think one of it's founders has a nice writeup.

---

### Post by bonzodog on 2009-01-15
Just so people are clear on this:

GTK = Gnome Tool Kit

Qt = Qute

---

### Post by geoken on 2009-01-15
> **Seq said:**
> 

I don't know why if so many believe this should be the way forward, they don't just do it themselves instead of whining about what "Gnome" should do. If there is enough demand for GnomeHIG + C++ + QT, then surely one can find others to help.

And I don't know why so many Linux users are so quick to throw out the "why don't you do it yourself" argument. It's seems like any time a valid suggestion involves work on someone elses part the suggestion is labeled 'whining' and the person is told to right the code and submit the patches themselves.

If you develop a DE and don't want any input form the people using your DE or the developers making apps that target your DE (by virtue of your unique toolkit) then don't go on forums.

When my wife tells me about problems she has with the CMS for her company's website, I don't say "If you want a new CSM, choose it yourself and migrate all your content then learn HTML and CSS to develop your new templates then learn PHP and the CMS's API to re-implement all the custom components I built". I listen to her concerns and then express to her the time/effort required in a migration and then we decide if it's worth it.

---

### Post by geoken on 2009-01-15
> **Seq said:**
> 

Gnome can't really be "moved" to QT anyway, so the entire discussion is pointless. Essentially, an entirely new desktop environment would exist that would carry the name "Gnome", but have no technical relationship to the previous releases.



You mean kind of like what Gnome is proposing with Gnome 3?

---

### Post by phrostbyte on 2009-01-15
> **geoken said:**
> And I don't know why so many Linux users are so quick to throw out the "why don't you do it yourself" argument. It's seems like any time a valid suggestion involves work on someone elses part the suggestion is labeled 'whining' and the person is told to right the code and submit the patches themselves.

If you develop a DE and don't want any input form the people using your DE or the developers making apps that target your DE (by virtue of your unique toolkit) then don't go on forums.

When my wife tells me about problems she has with the CMS for her company's website, I don't say "If you want a new CSM, choose it yourself and migrate all your content then learn HTML and CSS to develop your new templates then learn PHP and the CMS's API to re-implement all the custom components I built". I listen to her concerns and then express to her the time/effort required in a migration and then we decide if it's worth it.

If you care so much about this why don't you go submit a bug report to Gnome. "Suggesting" things on the forums is about as useful as suggesting improvements to brick wall. Even Ubuntu has a special place for proposing suggestions (Ubuntu Brainstorm). 

But really of course the best way for this to happen would be to go ahead and do all these simple Gnome 3.0 like changes yourself, since software doesn't write itself. What will make this actually happen is the willingness to make it happen, and the actions of making it happen. I don't see either of that here.

---

### Post by Vadi on 2009-01-15
> **bonzodog said:**
> 
GTK = Gnome Tool Kit

It's actually "Gimp Tool Kit". Gtk was made for Gimp, then Gnome came around that. But it still points out that the toolkit is tailored to Gnome's needs.

---

### Post by geoken on 2009-01-15
> **phrostbyte said:**
> If you care so much about this why don't you go submit a bug report to Gnome. "Suggesting" things on the forums is about as useful as suggesting improvements to brick wall. Even Ubuntu has a special place for proposing suggestions (Ubuntu Brainstorm). 

But really of course the best way for this to happen would be to go ahead and do all these simple Gnome 3.0 like changes yourself, since software doesn't write itself. What will make this actually happen is the willingness to make it happen, and the actions of making it happen. I don't see either of that here.

I'm not proposing suggestions. We're talking, that's it. It's called the dialectic process. We bring up ideas and bounce them off each other. I don't see what's wrong with that and I definitely don't see why people should be labeled whiners for doing that.

---

### Post by happysmileman on 2009-01-15
To be honest I'd really like if they developed a common theming system for both, that way they could both look the same and use same theme but still use the separate libraries, this would solve most of the complaints.

There's already QGtkStyle (which seems good IMO), and gtk-qt-engine (which looks terrible with every theme except clearlooks), but they're kinda hacky.

---

### Post by Seq on 2009-01-15
> **geoken said:**
> And I don't know why so many Linux users are so quick to throw out the "why don't you do it yourself" argument. It's seems like any time a valid suggestion involves work on someone elses part the suggestion is labeled 'whining' and the person is told to right the code and submit the patches themselves.

If you develop a DE and don't want any input form the people using your DE or the developers making apps that target your DE (by virtue of your unique toolkit) then don't go on forums.

I don't think any gnome devs are posting here in this thread. But Gnome devs are people. People do what they want, and lots of gnome devs like what they work with. More below...

> **geoken said:**
> When my wife tells me about problems she has with the CMS for her company's website, I don't say "If you want a new CSM, choose it yourself and migrate all your content then learn HTML and CSS to develop your new templates then learn PHP and the CMS's API to re-implement all the custom components I built". I listen to her concerns and then express to her the time/effort required in a migration and then we decide if it's worth it.

First of all, you would have a discussion of time/effort. You evaluate based on (I would assume) considerations of suitability, capability, and cost. These things are not occurring in this thread. Otherwise we would be discussing the merits of Pango, Cairo, Webkit, impacts on i10n, etc. What we have here is hand waving and finger pointing.

For my example below, I'm avoiding using a spouse as the example customer. You could perfectly well tell your wife to do it herself, but it would have a negative impact on yourself (i.e. Relationship, which you enjoy), so you don't react that way. She agrees with you as it would have a negative impact on herself (i.e. See less of you as you work on the CMS, doesn't want to deal with angry Geoken, etc).

So let's pretend I was a noted open-source developer with a widely used piece of software (note: I am not either of those). My "program", SuperDuperEmailDeluxe, is used by yourself and many others. It is written in perl+tk, but works exactly as I like. You come along and say "Hey, it would be cool if it could handle attachments". I haven't really needed that, but yes, it would be neat. So SuperDuperEmailDeluxe 2.0 handles attachments. Next, you suggest I change it to Python+wxWidgets as you are more familiar with that platform and it is easier to maintain. I point you to the source code and say "Let me know how it goes". It fills my needs, and there is no requirement for me to go out of my way to fill yours. For me to do something you want, there has to be a return: I want the experience, or I think it would be fun, or You will pay me for it, or I don't want to lose you as my hypothetical spouse, etc.

Now, if you write (or can convince others, such as with the above reasons) to start SuperDuperEmail-wxPythonEdition, and it fills my needs, then I may switch to it. Or better yet, I could see it as fun or good experience, and decide to help out after the ball is rolling. Maybe you were right and it was easier to maintain. You were right, I've switched to your version. The world goes on (Until somebody says Ruby+Motif or something).

Well at least it wasn't a Car analogy.

---

### Post by Seq on 2009-01-15
> **geoken said:**
> You mean kind of like what Gnome is proposing with Gnome 3?I have not seen any official Gnome 3 proposals.

People, who also happen to be Gnome developers, have been suggesting all sorts of "3.0" ideas. Most of the API breakage I have seen has been regarding removing old features ("cruft"). I have seen a suggestion regarding replacing the panel. I have seen discussion regarding changing the main menu applet.

I missed the one where they started with `rm -rf gnome` and started again. I don't read everything, so feel free to pass on the link.

---

### Post by SKLP on 2009-01-15
Now that the Qt licensing situation is acceptable for most people, the reason Gtk/GNOME was created in the first place has now *disappeared*. However, I'm one of those people who happen to believe that GNOME has grown into something which I prefer to use over KDE by a large margin.

IMO, Qt is now KDE's main strength.

What has caused KDE to develop such a cluttered, non-usability focused GUI (in the past) might be in part because many companies did not see it as completely serious, when it depended on a toolkit which has licensing problems. Hence they did not do any of the nice usability work to it that has been put into GNOME since the 1.x days.

What would be optimal right now (IMO) is if 
a) GNOME 3.0 was created by forking all of KDE 4.2, and changing all applications to comply to the GNOME HIG (and changing to other things the gnome guys like, such as adding spatial dolphin, etc)

b) the GNOME and KDE foundations merged to create a new unified DE (based on KDE 4.2, obviously)

But this is just wishful thinking, I'll probably just have to stay with good old GTK GNOME forever ;-)

---

### Post by geoken on 2009-01-15
> **Seq said:**
>  For me to do something you want, there has to be a return: I want the experience, or I think it would be fun, or You will pay me for it, or I don't want to lose you as my hypothetical spouse, etc.

Now, if you write (or can convince others, such as with the above reasons) to start SuperDuperEmail-wxPythonEdition, and it fills my needs, then I may switch to it. Or better yet, I could see it as fun or good experience, and decide to help out after the ball is rolling. Maybe you were right and it was easier to maintain. You were right, I've switched to your version. The world goes on (Until somebody says Ruby+Motif or something).

Well at least it wasn't a Car analogy.

That all makes sense. 

At the same time, there is no reason to be so hostile to people simply discussing tech.

If I was the dev of SuperDuperEmail, shouldn't I at least listen to the reasons why people think I should move the wx? 

I think devs don't realize how alienating that comment is because they don't realize that in making suggestions people are, in their own minds, attempting to 'give something back'. They may not know how to code, or if they do they may not have the time to commit to the project, but they feel they're helping with their suggestions. As a consequent they frequently come off sounding rude.

No one would object to this; "Those are good ideas guys, but we frankly don't have the manpower/time to implement them" or "I understand you feel like that, but you need to understand that there are at least as many people (likely more) who prefer the existing method and we don't have the time code/maintain both". Saying, "There's the code. Do it yourself."

---

### Post by Seq on 2009-01-15
> **geoken said:**
> At the same time, there is no reason to be so hostile to people simply discussing tech.

Sorry I came across as hostile. I apologize. Being hostile was the last thing I wish.

I posted from work, so I suppose I was in hostile mode by default.

> **geoken said:**
> I think devs don't realize how alienating that comment is because they don't realize that in making suggestions people are, in their own minds, attempting to 'give something back'. They may not know how to code, or if they do they may not have the time to commit to the project, but they feel they're helping with their suggestions. As a consequent they frequently come off sounding rude.

If somebody was to do the legwork and present an analysis covering the benefits QT provides in comparison with GTK, it would warrant a really interesting discussion. One does not need to be a programmer to do some research and put forth a worthwhile proposal. I have not seen an objective side-by-side comparison yet. The only argument put forth is essentially "Because it is better".

I can see how you could see those responses as rude, but a lot of Gnome developers have put a lot of effort into GTK and the various libraries based upon it. To have others, in particular those who do not have a programming background, to casually say "Finally we can replace all that crap you worked on" is quite rude as well.

> **geoken said:**
> No one would object to this; "Those are good ideas guys, but we frankly don't have the manpower/time to implement them" or "I understand you feel like that, but you need to understand that there are at least as many people (likely more) who prefer the existing method and we don't have the time code/maintain both". Saying, "There's the code. Do it yourself."Nobody would object to an actual, real, objective analysis either.

---

### Post by DigitalDuality on 2009-01-15
the QT lovers have screwed up KDE as it is.  Keep your darned hands off Gnome and Xfce and their native apps.

---

### Post by toupeiro on 2009-01-15
Personally, I think Gnome should stay and further improve using GTK+.  If you want a Qt based desktop environment, run KDE.  If you want to develop for a Qt based desktop environment, develop for KDE.  Don't completely recode the other major option for desktop environments to Qt just because its licensed under LGPL.  Thats a pretty stupid reason do to anything that massive to put it bluntly. I don't think the benefits are there with Qt to justify such a paradigm shift for gnome to be honest.  At least, nothing that you can't already get in KDE.  Since you can get Qt libraries and launch KDE apps in gnome, and since storage space is pretty darned cheap, why?!

---

### Post by Skripka on 2009-01-15
[quote=toupeiro;6556654 and since storage space is pretty darned cheap, why?![/quote]


The argument is one of "Why re-invent the wheel?"  If I've read correctly.  And it is a valid question.

---

### Post by igknighted on 2009-01-15
> **Skripka said:**
> The argument is one of "Why re-invent the wheel?"  If I've read correctly.  And it is a valid question.

This is not a "reinvent the wheel situation".  Well, OK, it kind of is.  Gnome (and more specifically GTK) is an attempt to recreate the QT wheel.  And it simply (as expected) isn't as good as the original.  GTK is slower and less feature-rich compared to QT (sorry, that's a fact, not an opinion).  As such, many people would like to see the gnome HIG (what makes gnome, gnome) switch to a faster, more robust toolkit.  It would let gnome devs work on more end-user features and make the desktop perform better.  No one wants to see gnome become KDE, or as cluttered as KDE... they want gnome.  But better.  Think of it as upgrading wheels for a hovercraft.

---

### Post by raul_ on 2009-01-15
> **toupeiro said:**
> Personally, I think Gnome should stay and further improve using GTK+.  If you want a Qt based desktop environment, run KDE.  If you want to develop for a Qt based desktop environment, develop for KDE.  Don't completely recode the other major option for desktop environments to Qt just because its licensed under LGPL.  Thats a pretty stupid reason do to anything that massive to put it bluntly. I don't think the benefits are there with Qt to justify such a paradigm shift for gnome to be honest.  At least, nothing that you can't already get in KDE.  Since you can get Qt libraries and launch KDE apps in gnome, and since storage space is pretty darned cheap, why?!

The thing is that this thread is not targeting personal opinions. Personally, I couldn't care less if Gnome uses QT, GTK or even Swing.

The question here is if it's even worth having two major projects that have the same purpose (building widgets) and consume developers resources with no apparent reason.

One of the problems is that most Linux users I meet are all about "I'm on the Gnome side" or "I'm on the KDE side" which leads to stupid points like "QT sucks because it's what KDE uses" or "GTK sucks because Gnome uses it". 

Why should Gnome port to QT? Because it's a well supported toolkit, provides multi-platform crossing (KDE4 runs NATIVELY on Windows, Linux, Mac OS, Maemo and probably in the near future, even Nokia devices) and is developer friendly.

Why shouldn't Gnome port to QT? Because the developers don't want the trouble, don't want to dump a project that took so many effort and/or because they feel they can't implement their ideas or goals using QT.

If Gnome developers decided to port to QT I would be very surprised because that's just not the image I have of them.

---

### Post by Skripka on 2009-01-15
> **igknighted said:**
> This is not a "reinvent the wheel situation".  Well, OK, it kind of is.  Gnome (and more specifically GTK) is an attempt to recreate the QT wheel.  And it simply (as expected) isn't as good as the original.  GTK is slower and less feature-rich compared to QT (sorry, that's a fact, not an opinion).  As such, many people would like to see the gnome HIG (what makes gnome, gnome) switch to a faster, more robust toolkit.  It would let gnome devs work on more end-user features and make the desktop perform better.  No one wants to see gnome become KDE, or as cluttered as KDE... they want gnome.  But better.  Think of it as upgrading wheels for a hovercraft.


I don't think anyone is talking about making GNOME into a branch of KDE-but standardizing the toolkit, and form there you can go wherever you want.

I would think that Gnome could still have all it's GUI trappings but still be Gnome, but be done in Qt?  Yes it would be a major re-write...but from what I've heard Gnome 3 and the next version of GTk are going to be that anyway.

Having options is nice...OTOH, when a commercial developer looks at Linux and sees the messy mass of toolkits-it's not surprising they don't want to have to deal with it.


Of course, all this is hypothetical, as we all know Gnome dropping GTk will never happen.  I think Torvalds called the exercise "Mental Masturbating".

---

### Post by deepclutch on 2009-01-16
Gnome can do with a Forked QT-4.5 purging any dependency factor to do with QT/kde/trolltech/nokia/kdefans . :D

---

### Post by xirtus on 2009-01-17
wow... some of you kids are on spray paint...

All the fanboys sit down, lets just hold on a second.

Look here's the deal, we really can't waste time arguing over this nonsense... as there isn't a GTK3 and the GTK was invented effectively in order to ripoff QT for reasons that don't matter anymore, I can't see where this can possibly be going, (other than to QT)

Now I'm not looking at this from a debate point of view anymore, I'm just willing logic at this point: Gnome WILL be QT and, at least for the meantime, NOT KDE (cause really, anyone who tells you different is an idiot)

Now this kind of hampering blows my mind, why can't we remember the point of GNU?

There's so much room for varied innovation, but we have to use a metric system... Right now you know the BEOS is making a comeback as Haiku -without the linux kernel? I mean its explicitly because of all the work that went into linux that will now help Haiku thru GNU...

I see why people are freaked out about an end to GNOME, I mean any of you old enough to remember HURD? I seriously still think its going to happen. Hear about Viengoos? I hope to Ahura Mazda it will surpass the monolithic Linux Kernel... thats how romantic I am, that I believe the children are going to wake up and fix multiplexing for their multicores and I'll smile..

...I lost my train of thought...

the point is QT is the new gnome3 kit, and aren't we all glad? From now on, we can work to consolidate our tools in a way that will transcend gnome and kde, transcend ubuntu and linux, transcend gnu and unix, bsd & GPL in general.

Today is a GNU beginning for open-source; and I'm happy to see us figure that out together.

---

### Post by bruce89 on 2009-01-17
> **xirtus said:**
> Look here's the deal, we really can't waste time arguing over this nonsense... as there isn't a GTK3 and the GTK was invented effectively in order to ripoff QT for reasons that don't matter anymore, I can't see where this can possibly be going, (other than to QT)

GTK+ 3.0 is in the planning stages at the moment actually. Also, GTK+ isn't a "ripoff" of Qt, it was created because of the licence issue way back in the past (the QPL).

> **xirtus said:**
> Now I'm not looking at this from a debate point of view anymore, I'm just willing logic at this point: Gnome WILL be QT and, at least for the meantime, NOT KDE (cause really, anyone who tells you different is an idiot)

This makes no sense at all, what would KDE switch to?

> **xirtus said:**
> the point is QT is the new gnome3 kit, and aren't we all glad? From now on, we can work to consolidate our tools in a way that will transcend gnome and kde, transcend ubuntu and linux, transcend gnu and unix, bsd & GPL in general.

Where on Earth did you get that information from? No-one of the GNOME have even mentioned switching to Qt (apart from daft Mark, but he's not GNOME).

---

### Post by DeadSuperHero on 2009-01-17
Ah, gotta love the flamebait articles!

Truth be told, if you'd really want to see a version of GNOME using Qt, what's stopping you from forking off GNOME to use the toolkit? Granted, it would have a small developer base at first, and you'd get a FUD storm from both parties. There'd be complications, frustrations, several developers might walk out.

On the other hand, let's look at what this would yield:

-A possible overall improvement to GNOME: GTK, great as it is, can sometimes be really visually ugly. On top of that, I find there to be a lack of integration between apps sometimes, it feels more like a patchwork of frameworks. Not that it's an entirely bad thing, but I'm sure others can understand where I'm going with this.

-A possible improvement to Qt/KDE: Think about it. One of the reasons Qt improved so much in the first place was because KDE was developed with it. Constant demand required Trolltech to improve and share code with the KDE devs, causing everything leading up to KDE 4.x. This has lead to intricate frameworks, wrappers, and what I think to be a really nice desktop overall. However, there remains the problematic state of theming for Qt, and Gnome apps just don't fit into KDE, no matter how many qt-gtk engine patches you use. If, say, Gnome apps such as GIMP or Firefox were fully ported to Qt, they would integrate better with the environment, and some excited devs would already be plugging away to make them fit nicely into the various KDE frameworks.

-Simplified theming in KDE: Gnome has always been easier to theme, and the engines are usually easier to compile nowadays. I have no idea why, but compiling KDE themes across distributions is just flat-out frustrating. However, with some Qt/Gnome devs behind it, they could probably look into a way to compile several high-quality Qt engines and give out a sort of template for users to hack away on. (Sort of like what is done with Murrine, Clearlooks, etc.)

In any case, I'd actually like to see how something like this would play out. Heck, the more choices the better! And if great Gnome apps can integrate into the KDE desktop, and vice versa, why hold back?

---

### Post by bruce89 on 2009-01-17
> **Mr. Psychopath said:**
> -A possible overall improvement to GNOME: GTK, great as it is, can sometimes be really visually ugly. On top of that, I find there to be a lack of integration between apps sometimes, it feels more like a patchwork of frameworks. Not that it's an entirely bad thing, but I'm sure others can understand where I'm going with this.

Theming in GTK+ is a pain in the lower back, but some people can make quite nice ones.

No toolkit can't make people design insane UIs, so you can end up with some very ugly ones. It surely is also possible to make an ugly Qt program.

GTK+ is only a UI library, so in that way there is a "patchwork". For instance, the text rendering is done by Pango, the graphics by GDK and Cairo, the lower level utility code by GLib and the object system by GObject to name a few.

> **Mr. Psychopath said:**
> -A possible improvement to Qt/KDE: Think about it. One of the reasons Qt improved so much in the first place was because KDE was developed with it. Constant demand required Trolltech to improve and share code with the KDE devs, causing everything leading up to KDE 4.x.
[...]
If, say, Gnome apps such as GIMP or Firefox were fully ported to Qt, they would integrate better with the environment, and some excited devs would already be plugging away to make them fit nicely into the various KDE frameworks.

GTK+ is developed by the GNOME people, so GNOME requirements have made GTK+ improve too. Also, GIMP isn't a GNOME program (mind you, how do you define that), and Firefox certainly isn't.

Firefox is gaining a belated Qt port by the way (in the respect that Qt has WebKit now).

---

### Post by deepclutch on 2009-01-18
> GIMP isn't a GNOME program
GIMP tool Kit is not a Gnome Toolkit also. :P

---

### Post by ZuLuuuuuu on 2009-01-18
I can understand most of the opinions but can't understand when people count switching to Qt will make Gnome look better. This is a "taste" thing. Many people use Gnome just because they like its look much better than KDE. And I'm one of them. If every Linux distro look like KDE then I may even give up using Linux, it is that ugly to me.

We are disscussing how Qt switch will improve Gnome. But it is more logical for Qt to switch GTK actually, and no I didn't make mistake by writing Qt instead of KDE. Let me explain it: The GUI part of the Qt is using always the native widget toolkit of the platform it is running on, except Linux where it uses the widget toolkit of its own. The other parts of the Qt is not related with GTK. So Qt may drop its rendering system on Linux and use GTK to render the widgets and the rest of the Qt will remain the same. A change which includes only 1 platform and only 1 part of the toolkit. Easier than modifying a whole desktop environment isn't it? The GTK users would also be happy because the GTK feel won't go anywhere and GTK won't die. This also would make the things easier for Trolltech because they won't have to deal with lower level GUI stuff on Linux anymore...

---

### Post by fissionmailed on 2009-01-18
I have a great idea.  First you take the GTK and Qt developers and you don't feed them for a week.  Then you give them weapons and let them at it.  Who ever wins gets both parties' development money and a trip to the Outback for some nice juicy steaks.  Problem solved? I say so.

---

### Post by techmarks on 2009-01-18
I think it would be great to unite the Linux desktop efforts behind one single GUI toolkit.

That said would Gnome on QT go all bloated and sluggish...slow...like KDE?

---

### Post by jacobw.uk on 2009-01-18
Would it really be such a good idea to put (a large part of) the future of the free desktop in a one big Nokia controlled basket?

---

### Post by Vadi on 2009-01-18
> **jacobw.uk said:**
> Would it really be such a good idea to put (a large part of) the future of the free desktop in a one big Nokia controlled basket?

Well, undoubtedly people will argue against you that "It's LGPL now, open-source, we can do whatever we want, blah blah" and forget that if they move all of the Qt programmers somewhere else / fire them, that will be a large portion of Qt development halted right there.

---

### Post by bruce89 on 2009-01-18
> **deepclutch said:**
> GIMP tool Kit is not a Gnome Toolkit also. :P

Indeed, there is no GNOME toolkit as such (the GNOME libraries are depreciated).

Out of interest, how much stuff is in the KDE libraries?

> **Vadi said:**
> Well, undoubtedly people will argue against you that "It's LGPL now, open-source, we can do whatever we want, blah blah" and forget that if they move all of the Qt programmers somewhere else / fire them, that will be a large portion of Qt development halted right there.

Apparently they promise to open development to outsiders (which you'd think would be the point in FOSS), but I wonder if anyone will bother much.

> **techmarks said:**
> I think it would be great to unite the Linux desktop efforts behind one single GUI toolkit.

Just like there's one desktop environment and one text editor.

---

### Post by jsmidt on 2009-01-18
GTK's devs have proven they cannot compete with the innovation being done with Qt.  Every year Qt makes [significant improvements]("http://en.wikipedia.org/wiki/Qt_toolkit#Current") to the toolkit.  Now, Qt can make apps [look just like GTK]("http://en.wikipedia.org/wiki/QGtkStyle") so the look of the apps shouldn't be a problem anymore.

So yes, if you want Gnome to based off a toolkit which never sees any innovation, stick with GTK.  I prefer innovation without breaking ABI/API, which is what you get with Qt. 

(Seriously, what interesting innovation idea is GTK 3.0 receiving?  Removing legacy code? Here is your [GTK innovation list]("http://en.wikipedia.org/wiki/Gtk#Releases") for the last several years.  Not much at all.)

---

### Post by igknighted on 2009-01-18
> **techmarks said:**
> I think it would be great to unite the Linux desktop efforts behind one single GUI toolkit.

That said would Gnome on QT go all bloated and sluggish...slow...like KDE?

Quite the opposite... assuming the gnome devs build it in qt the same way it was in GTK (KISS), then it should be much faster, as qt is a faster toolkit than gtk.

---

### Post by xirtus on 2009-01-18
The way I write can read different later... -if that makes any sense.. Don't take me for flame, a troll took me to dance. I apologize for my inflammatory way of writing... -Reading over what I said it looks like I meant, "the world must use QT!, I am the lord GOD of hellfire!" which is silly... 

I was only hypothesizing over what the benefits would be to GNOME, and GNU in general (which, Mr psychopath explained much clearer and accurately.) Having Gnome and KDE being in the same kit means the difference between that possibly the two will be small enough to include on the same CD, making it more convenient for people to chose or switch. It will also make life easier for the coders and designers. Some people forget people actually write the code, and do more than just hack it or decorate it. I think it's important to remember that relationship dynamic, and help encourage what stimulates that. Using one kit means all the programmers can put all the features into one machine, that suits the needs of all the projects.. Finally, a kit will be complete before work finally and work done can be shared... 

Some called this a taste issue between GNOME and KDE and that is absolutely the opposite of the situation and it is counter intuitive to look that way... It sounds like there are some GNOME enthusiasts who are worried that KDE storm troopers are going to sneak in and shoot GNOME in the back at night. The idea is to port GNOME to a much better toolkit, so that all the ideas to improve during the rebuild of the GTK toolkit could be better served fixing the already stable and sound QT toolkit...

-and if nokia fires its development, change its name bake to GTK cause they will become synonymous or BORG!


-Sorry for calling the GTK a ripoff, I think it's important to remember why GNOME was started, but not to talk it down... I am entirely in accordance with the Stallman's GNU agenda. GNOME was started to serve the same purposes as non-GPL QT at the time. Well, it certainly did, and GNOME in several ways surpassed KDE, and some of the architects can proudly say they influenced the competitors... -but thats because in the GNU world (theoretically) everyone works together. However diversity isn't division. The last thing we should want is an absurd coldware, and it frustrated me to hear people saying that they wanted a cold war between two viable pieces of software... I mean for all intensive purposes, GNU is an "us or them game", and since we're not against each other, we are one! 

Now can anyone take a breath and remember that we have to restart the project anyway so while were on the subject of KDE,GNOME or XFCE... The reason I said anyone is an idiot who thought unifying the kit would shed either GNOME or KDE is that all the coding is open-source. Because no one can control diversity and there will always be competition (look at awesome xfce!, thats gtk+)

Mainly I just think having a unified kit with the best of both worlds. -All the development because of GTK are great, and aspects of the intuitiveness for GNOME are wonderful, and I'm one to use some of the gtk especially xfce on slower systems. So when I said the old GTK is obsolete now, thats like saying KDE3 is outdated, its subjective. I mean we all know it's old technology but its still damn impressive, and I'll be impressed 20 years from now at what was accomplished in GTK...

Now it's important to realize that QT has made some vast improvements to, not the least of which, joining the GPL club.

So again, these things are in their major rewrite stages, why not take QT and call it GTK, why not take GTK and call it QT.. apples and oranges in a land of milk and honey...

---

### Post by raul_ on 2009-01-18
> **jsmidt said:**
> GTK's devs have proven they cannot compete with the innovation being done with Qt.  Every year Qt makes [significant improvements]("http://en.wikipedia.org/wiki/Qt_toolkit#Current") to the toolkit.  Now, Qt can make apps [look just like GTK]("http://en.wikipedia.org/wiki/QGtkStyle") so the look of the apps shouldn't be a problem anymore

That has been available for quite some time. 

Correct me if I'm wrong, but I remember reading some time ago that the guys working on qt-gtk were behind KDE, and the GTK guys couldn't care less for that compatibility. The guy who wrote it was complaining about the gnome developers' attitude towards inter-DE compatibility.

---

### Post by Vadi on 2009-01-18
> **jsmidt said:**
> Now, Qt can make apps [look just like GTK]("http://en.wikipedia.org/wiki/QGtkStyle") so the look of the apps shouldn't be a problem anymore.

False. The differences are noticable and the bugs show.

---

### Post by smartboyathome on 2009-01-18
> **jsmidt said:**
> GTK's devs have proven they cannot compete with the innovation being done with Qt.  Every year Qt makes [significant improvements]("http://en.wikipedia.org/wiki/Qt_toolkit#Current") to the toolkit.  Now, Qt can make apps [look just like GTK]("http://en.wikipedia.org/wiki/QGtkStyle") so the look of the apps shouldn't be a problem anymore.

Have you haerd of the gtk-qt-engine? It was made to let GTK apps have an emulated look taken from the current Qt theme. It has been out for quite a few years. QGtkStyle is new to the game. So, wouldn't that lead you to believe that GTK is easier to write engines for than QGtkStyle? ;)

Also, I like the fact that I can theme different parts of GTK with different theme engines if I so please. With Qt, you get one theme engine. If you want the look of another theme engine with parts from your current theme engine, you got to hack the theme engines together to create a new one. I haven't done much KDE theming, and none in a long while, though, so what I said could be completely wrong.

---

### Post by xirtus on 2009-01-19
> **raul_ said:**
> ...The guy who wrote it was complaining about the gnome developers' attitude towards inter-DE compatibility.

so either thhere is a conspiracy behind GNOME for decompatibility or the gnome guys think there is a conspiracy at KDE?

either way this is starting to get a little bit paper boats and foil hats, if you know what I mean?

I think we should be glad to have the paid support at Nokia while we still can... I certainly can't imagine what people have against these guys. I mean I understand wanting preference in Gui, I think its a brilliant part of GNU, but it should be based on complexity or preference, not flipping the cars and roads for england and france... (Talk about shooting ourselves in the foot)


I say if you want to make another toolkit, it better be a quake mod because as it stands QT is elite, and because of that KDE4 is at the apex of modernity, I'd like to see gnome catch up to that.

---

### Post by CraigPaleo on 2009-01-19
I'm for Gnome staying with GTK but for the sake of this discussion, wouldn't it be a whole lot easier to fork KDE and make it look, feel and act like Gnome? I mean to the extent that the user wouldn't know the difference. I don't mean just a "Gnome theme" here but something like what Apple did after it acquired Next.

It kept Carbon and Cocoa, removed some redundancies and now has two toolkits. Gtk would then be more akin to Carbon and Qt to Cocoa.  

It just seems like it'd be much more efficient to modify existing code, which already uses Qt, rather than porting a whole DE to an entirely different toolkit, which is also written in a different language. Don't you think?

---

### Post by Changturkey on 2009-01-19
> **CraigPaleo said:**
> I'm for Gnome staying with GTK but for the sake of this discussion, wouldn't it be a whole lot easier to fork KDE and make it look, feel and act like Gnome? I mean to the extent that the user wouldn't know the difference. I don't mean just a "Gnome theme" here but something like what Apple did after it acquired Next.

It kept Carbon and Cocoa, removed some redundancies and now has two toolkits. Gtk would then be more akin to Carbon and Qt to Cocoa.  

It just seems like it'd be much more efficient to modify existing code, which already uses Qt, rather than porting a whole DE to an entirely different toolkit, which is also written in a different language. Don't you think?
Carbon is slowly being depreciated.

---

### Post by gururise on 2009-01-21
Someone posted this as an [Ubuntu Brainstorm Idea]("http://brainstorm.ubuntu.com/idea/17464/"). Go vote now!

I've added another solution, which was brought up earlier in this thread.  The idea of replacing the part of Qt that draws its own widgets with that of native Gtk widget.

---

### Post by Vadi on 2009-01-22
Erm, heh. I think Gnome developers can decide just fine for themselves what to do with their time in the future :)

---

### Post by infinitelink on 2009-01-28
[consolidated below]

---

### Post by infinitelink on 2009-01-28
[consolidated below]

---

### Post by infinitelink on 2009-01-28
[consolidated below]

---

### Post by infinitelink on 2009-01-28
[consolidated below]

---

### Post by infinitelink on 2009-01-28
> **SKLP said:**
> Now that the Qt licensing situation is acceptable for most people, the reason Gtk/GNOME was created in the first place has now *disappeared*. However, I'm one of those people who happen to believe that GNOME has grown into something which I prefer to use over KDE by a large margin.

I want to point-out how much people are ignoring in this forum, making statements already settled, like this consideration: there's no discussion of dropping Gnome in favor of KDE, but rather pointing-out that the next very substantial re/write of Gnome could be based on QT (not KDE, not KDE, not KDE) to unify the linux development efforts.

> **SKLP said:**
> IMO, Qt is now KDE's main strength.

What has caused KDE to develop such a cluttered, non-usability focused GUI (in the past) might be in part because many companies did not see it as completely serious, when it depended on a toolkit which has licensing problems. Hence they did not do any of the nice usability work to it that has been put into GNOME since the 1.x days.

The KDE UI was usable precisely because it was customizable: the constant complaint I hear (and anybody else familiar with the OSS community) about Gnome is its heinously awful customization: even removing all ways to customize when the feature is in the code. : (  People have diverse computing needs, and toddler-level hand-holding, while useful in many contexts, is not suitable for widespreadly used DEs.

> **SKLP said:**
> What would be optimal right now (IMO) is if 
a) GNOME 3.0 was created by forking all of KDE 4.2, and changing all applications to comply to the GNOME HIG (and changing to other things the gnome guys like, such as adding spatial dolphin, etc)

Gnome HIG: "um, we think these common options, especially those used on the most widely adopted OS, with the greatest amount of familiarity, might confuse two year olds. Therefore, we disabled the options: and built an atom-bomb into the code for anyone who tries to re-enable them. Just kidding! Actually it'll just frustrate you to no end why you can't get the re-enabled stuff to work or work correctly; we don't like giving our users too much control." (not subtle sarcasm, I know)

> **SKLP said:**
> b) the GNOME and KDE foundations merged to create a new unified DE (based on KDE 4.2, obviously)

Have you even read any of this? GTK is the development framework used to create Gnome's libs, but in programming terms, it is not its foundation (Gnome's libs); QT is the framework of KDE's libs, but not KDE's foundations (KDE's libs).

-- -- --

> **optimisme said:**
> Mark is right

Gnome must improve (in many ways) and a good way to do it, is using Qt.

Of course it won't happen, maybe a working group can start creating a new desktop environment with the goals of GNOME, but also improving it where GNOME fails.

Qt has a lot of advantages, now is supported by NOKIA and its license is all right. GNOME (or a kind of) using Qt means the most powerful and usable desktop ever done (even better than Mac OS X if it is done all right).

Hopefully someone (probably someone from NOKIA) will notice it, and will skip KDE (the way it behaves is not nice with new users) and will start doing a kind of GNOME (or a kind of Aqua, or just a better user interface) easy to use (and configure) getting the power of Qt.

That day, if it comes, I probably will use this new software even if it means say goodbye to Ubuntu. Because what we all want, apart of software freedom, is good software.

GNOME engineers must know sometimes, the best way to go on, is just leave the past behind, and expend all the efforts evolving the ideas but rewriting source from the scratch.

In my opinion the good part of KDE is Qt (with some great software and design decisions) and the bad part of GNOME is GTK

Of course this change is radical, and doing it means some loses. But loses are not as big as advantages, because using Qt as "the linux paradigm" means unifying linux and making easier for software companies, to go "the linux way"

Except for 4.0 (though 4.2 is supposed to have incredibly clear this problem up), KDE is much more alike to Windows (you know, where the new linux users come from) than Gnome. Gnome's HIG is terribly simplistic and toddlish (not that that doesn't have valid applications). 

Though frankly I believe most computer users would neither notice on care on either, at least initially, though inevitably when they wish to "make their computers their own" (inevitable general consumers of computers), Gnome becomes the show-stopper. KDE's philosophy seems to be "make available", and let the user decide how to tune their desktop. I like this. (Yet I also like Gnome.)

--

> **Tom Mann said:**
> I believe that Gnome should stay with GTK+ - I believe it's Gnome's need that help[ed] push GTK+ along. It's the same with KDE and Qt, the desktop's needs drive the development of the toolkit.

I personally think Qt is fantastic and has a better chance of going multi-platform - it's already being seen with VLC's latest version in Windows... Embedded video at last! Gnome will fight back, and GTK+ will eventually become a better toolkit, then it'll be Qt's turn to become better, ad infinitum.
The competition will continue to drive quality software into users hands.

QT is already multiplatform, FYI. GTK seems to be a giant hack with poor bindings and a ton of needed restructuring: I don't know that dropping it in favor of porting GNOME to QT is actually all that much extra work. It's likely the C could be converted somewhat semi-automatically (I know this really doesn't work too extensively, but some work could be done here to explore the possibility), use the C-related tools from QT to get Gnome's libs working with QT (if they're still around), and so on, so forth. 

> **gururise said:**
> There exists, or used to exist, a C wrapper to Qt.  This C wrapper could be brought back to life and used as the basis for the port of Gnomelibs to Qt.

And with the proper Qt2Gtk engine running, the widgets would look exactly the same as they do now.. In fact, if done right, most end-users would not even know that Gnome switched from Gtk+ to Qt.

Actually I'd love to see this done not in order that GTK be totally abandoned, but to free-up time (since the development tools would be standardized) for its developers to actually to the overhauling GTK needs so that it could truly be competitive, (it's not), and to become very attractive to developers in a wider range of uses. : D

-- -- --

> **phrostbyte said:**
> If you care so much about this why don't you go submit a bug report to Gnome. "Suggesting" things on the forums is about as useful as suggesting improvements to brick wall. Even Ubuntu has a special place for proposing suggestions (Ubuntu Brainstorm). 

But really of course the best way for this to happen would be to go ahead and do all these simple Gnome 3.0 like changes yourself, since software doesn't write itself. What will make this actually happen is the willingness to make it happen, and the actions of making it happen. I don't see either of that here.

I've heard a lot of complaints that Gnome's devs don't like accepting submitted code. That's also their choice, but it's kind-of counter OSS community too. Maybe they've gotten better in the past few years, though, don't know. Anyone know?

-- -- --

> **Vadi said:**
> It's actually "Gimp Tool Kit". Gtk was made for Gimp, then Gnome came around that. But it still points out that the toolkit is tailored to Gnome's needs.

Gnome also suffers from limitations due to GTK, graphical is an areas hackish, and an ideological knee-jerk reaction to KDE's formation and development based upon QT's QPL. Perhaps later GTK's addressed some of this, but I've heard a lot of complaints about graphical limitations confining Gimp to raster for being a hack from GIMP. Not that I'm complaining about that, actually: it makes perfect sense in business terms. : D

-- -- --


> **bruce89 said:**
> [...]

GTK+ 3.0 is in the planning stages at the moment actually. Also, GTK+ isn't a "ripoff" of Qt, it was created because of the licence issue way back in the past (the QPL).


This makes no sense at all, what would KDE switch to?

I think you missed the point; I think he's calling QT the new GTK, the cream that fills the need GTK+Gnome were created for; more suitable and ready for that task, with all the major advantages that GTK can't even begin to dream of attaining in a longshot (on every platform, widely popular and available, and etc.); it's the new "in"...

GTK != Gnome; KDE != QT; or vice versa for either. (!= means "does not equal, by the way). Gnome could be put atop QT with the requisite effort, and remain Gnome, with all of QT's advantages to boot; and now that QT development is being opened-up to the world for participation, without requiring copyright assignment, under the LGPL, QT is not only open source, but they could perhaps also code any advantages GTK has to and submit the work for inclusion in QT!

-- --

> **jacobw.uk said:**
> Would it really be such a good idea to put (a large part of) the future of the free desktop in a one big Nokia controlled basket?

Here: 

> **Keyper7 said:**
> [...]

Quote from [ars technica](http://arstechnica.com/news.ars/post/20090114-nokia-qt-lgpl-switch-huge-win-for-cross-platform-development.html):

-- -- --

From an *Anonymous Coward* over on Slashdot:

> Seriously. This is going to be one of the biggest misquoted articles of the year because some Slashdot nobody editor decided to take Shuttleworth's words out of question's context.

He quite clearly says that it is possible to deliver GNOME's qualities on Qt. He didn't say that he wants to do it. He didn't say he was going to do it. He even pointed out a problem in doing it (GPL vs LGPL).

Of course, it would also be possible to deliver GNOME's qualities on Enlightenment or Tcl/Tk if you could find enough hackers to do it. There's nothing unique about GNOME's qualities that only GNOME could do it. They simply picked a different path, and it happens to be one that works incredibly well for Ubuntu. So well that they can share schedules with GNOME, that they can build a base for ISVs on GNOME, and on and on.

So please, PLEASE read the fine article before jumping to conclusions from the terrible Slashdot header. [Source: [http://tech.slashdot.org/comments.pl?sid=613205&cid=24180679]](http://tech.slashdot.org/comments.pl?sid=613205&cid=24180679])

The mistake of this guy's post is horrible, though: Gnome is much LGPL, not GPL. With QT becoming LGPL, there isn't an incompatibility between Gnome and QT. ([http://derstandard.at/?url=/?id=3413801](http://derstandard.at/?url=/?id=3413801)) I don't know why people aren't paying attention to details, it's really annoying. : (

---

### Post by mips on 2009-01-28
infinitelink,

Wow! =D>

You have a very good wrinting style getting stuff across.

---

### Post by CraigPaleo on 2009-01-28
> **infinitelink said:**
> [consolidated below]

There is an inconspicuous, multi-quote button just to the right of the "quote" button, which can be very useful when quoting more than one post. :)

---

### Post by deepclutch on 2009-01-28
Firstly ,majority of people _[COLOR=Red]**don't**[/COLOR]_ want to customize each and every settings in the desktop environment as some robots(who cannot respect others thought) here and everywhere expects.I call them control freaks.they never stop Gnome bashing.Gnome is very much productive DE compared to Kde - Period and also customizable.
--
then QT toolkit today is much more advanced compared to GTK which I agrees.and this suggestion of porting Gnome or Forking Gnome with QT base is very much welcomed.Those who swears with GTK(I includes) can sure go with it.In FOSS ,options are not needed to be killed which sadly ,our kde fan brothers/sisters forgot to respect(remember tux magazine?typical arrogance against Gnome users).

---

### Post by raul_ on 2009-01-28
> **deepclutch said:**
> Gnome is very much productive DE 

Got any references on that? :popcorn:

---

### Post by deepclutch on 2009-01-28
Ubuntu is the answer.

---

### Post by Skripka on 2009-01-28
> **deepclutch said:**
> Firstly ,majority of people _[COLOR=Red]**don't**[/COLOR]_ want to customize each and every settings in the desktop environment as some robots(who cannot respect others thought) here and everywhere expects.I call them control freaks.they never stop Gnome bashing.Gnome is very much productive DE compared to Kde - Period and also customizable.
--
then QT toolkit today is much more advanced compared to GTK which I agrees.and this suggestion of porting Gnome or Forking Gnome with QT base is very much welcomed.Those who swears with GTK(I includes) can sure go with it.In FOSS ,options are not needed to be killed which sadly ,our kde fan brothers/sisters forgot to respect(remember tux magazine?typical arrogance against Gnome users).

It goes back and forth.  On this forum-most  of the bashing that occurs is Gnome users bashing KDE.

---

### Post by xirtus on 2009-01-28
(slaps face) how did you kids get back to the fanboy catfights again?

lets just summarize things so people don't have to look through these pages recanting our ramblings...

1: the idea of the thread (as the title suggests) is porting Gnome into the new universal Qt4.5 LGPL libraries.

The reasons are varied, mainly focused around Qt's new LGPL which matches the GTK. Another point is that the well funded Qt, now operated by Finnish Nokia; will continue to support and update the software with the community, nurturing the next revolution of the free software movement by providing a common guikit as universal as the kernel was 15 years ago... I think the best reason still is the need for a universal kit. Freedom should be Universal, after all... Ubuntu means Humanity...



okay but there is another side!


2: C++ vs C... I don't know if I'm the one to explain why people think C is faster than C++, I will just admit that it is, but barely -and only because of the sheer volume of code that has to be processed. With smart coding, C++ doesn't have to suck... And there's ways around rewriting every app from C to C++ and it could work. Still who's to say? All I'm saying is no one's jumping at porting xubuntu to Qt...

3: At this point the Gnome programmers have already said I believe several times they don't want to switch to Qt because it would take a very long time and make them frustrated...



NB
So this is my question: what would happen to XFCE if GNOME switched, would that effect their development at all? I don't know how closely they are related, just that they use GTK... I can imagine GNOME developers might get galvanized by the switch, making some hard choices... XFCE is pretty sweet, and I can imagine it will all of the same features of KDE4, just faster with less silly, tacky scripts like snowballs and shattering fireball windows... (slaps face again)

Also this is way of topic, but of fast interfaces, Google and V8, and Javascript... I would like to know more about that...

---

### Post by bruce89 on 2009-01-28
> **infinitelink said:**
> 
QT is already multiplatform, FYI. GTK seems to be a giant hack with poor bindings and a ton of needed restructuring: I don't know that dropping it in favor of porting GNOME to QT is actually all that much extra work. It's likely the C could be converted somewhat semi-automatically (I know this really doesn't work too extensively, but some work could be done here to explore the possibility), use the C-related tools from QT to get Gnome's libs working with QT (if they're still around), and so on, so forth.

GTK+ has bindings for every major language (C, C++, Python, Java, PHP, Ruby, Perl, JavaScript). Also, it is not a "giant hack", and runs on Windows and MacOS X.

> **infinitelink said:**
> 
From an *Anonymous Coward* over on Slashdot:

The mistake of this guy's post is horrible, though: Gnome is much LGPL, not GPL. With QT becoming LGPL, there isn't an incompatibility between Gnome and QT. ([http://derstandard.at/?url=/?id=3413801](http://derstandard.at/?url=/?id=3413801)) I don't know why people aren't paying attention to details, it's really annoying. : (

That was written pre-Qt-LGPLing.

> **xirtus said:**
> 
2: C++ vs C... I don't know if I'm the one to explain why people think C is faster than C++, I will just admit that it is, but barely -and only because of the sheer volume of code that has to be processed. With smart coding, C++ doesn't have to suck... And there's ways around rewriting every app from C to C++ and it could work. Still who's to say? All I'm saying is no one's jumping at porting xubuntu to Qt...

C was chosen because it is more easily used from other languages. The whole point of GNOME was to be able to use any language to write programs, and that has come true (C, C++, Python, C# for instance). C++ code is much more difficult to write bindings for.

> **xirtus said:**
> 
So this is my question: what would happen to XFCE if GNOME switched, would that effect their development at all? I don't know how closely they are related, just that they use GTK... I can imagine GNOME developers might get galvanized by the switch, making some hard choices... XFCE is pretty sweet, and I can imagine it will all of the same features of KDE4, just faster with less silly, tacky scripts like snowballs and shattering fireball windows... (slaps face again)

GNOME are the primary developers of GTK+ (all 2 of them). If GNOME stopped (as if), Xfce would be in a bit of a pickle. Of course, a fork would be in order then.

> **xirtus said:**
> Also this is way of topic, but of fast interfaces, Google and V8, and Javascript... I would like to know more about that...

GNOME 3.0 may bring JavaScript to the desktop.

---

### Post by gururise on 2009-01-30
Over at the [Qt Labs Blog]("http://labs.trolltech.com/blogs/2008/05/13/introducing-qgtkstyle/") there is a beta release of a Qt plugin that allows Qt to render using the Gtk+ widgets!

Perhaps Qt with this plugin should be made an official C++ binding of Gnome, and the Qt libs should ship with Gnome.  That way we can have the best of both worlds.  People who want to program in C can use straight Gtk+, and those who want to use C++ can use the very well documented Qt, or the currently official [Gtkmm]("http://www.gtkmm.org") C++ bindings, which are mostly complete, but are missing bindings for important things like GStreamer, etc.

---

### Post by smartboyathome on 2009-01-30
> **gururise said:**
> Over at the [Qt Labs Blog]("http://labs.trolltech.com/blogs/2008/05/13/introducing-qgtkstyle/") there is a beta release of a Qt plugin that allows Qt to render using the Gtk+ widgets!

Perhaps Qt with this plugin should be made an official C++ binding of Gnome, and the Qt libs should ship with Gnome.  That way we can have the best of both worlds.  People who want to program in C can use straight Gtk+, and those who want to use C++ can use the very well documented Qt, or the currently official [Gtkmm]("http://www.gtkmm.org") C++ bindings, which are mostly complete, but are missing bindings for important things like GStreamer, etc.

Problem is you still need libraries for both to be loaded, which adds bloat.

---

### Post by yse on 2009-01-30
Layer over layer all over again, and much more..

QT is beautiful in general, imho, QT problem is MOC, but thats other story.

GTK and QT should stay how they are and try to improve the code, remove all garbage and bloat from it. Rich GUI applications require good development tools, and there QT/GTK should focus a bit more.

If you talk about KDE/Gnome, their problems are not QT or GTK, their problems are a bit behind .. and i will say X. Honestly.. X is such a piece of garbage...

---

### Post by bruce89 on 2009-01-30
> **gururise said:**
> Perhaps Qt with this plugin should be made an official C++ binding of Gnome, and the Qt libs should ship with Gnome.  That way we can have the best of both worlds.  People who want to program in C can use straight Gtk+, and those who want to use C++ can use the very well documented Qt, or the currently official [Gtkmm]("http://www.gtkmm.org") C++ bindings, which are mostly complete, but are missing bindings for important things like GStreamer, etc.

That's what GStreamer-mm is for. Also, GObject-introspection is an interesting thing (paving the way for automatic bindings for GObject-based libraries).

---

### Post by techmarks on 2009-01-30
I'd say we need to keep both going.

I know QT has the better docs and it has a few more advanced features.

But I just plain like GTK, I like the way it looks.

QT is so Windows like at the moment, there's nothing wrong with that, but I just think GTK has it's own personality, it's own look.


I use QT apps in Gnome without any troubles.

Let's keep both around.

---

### Post by bruce89 on 2009-01-30
> **techmarks said:**
> But I just plain like GTK, I like the way it looks.

QT is so Windows like at the moment, there's nothing wrong with that, but I just think GTK has it's own personality, it's own look.


A UI toolkit doesn't have a look as such, that's completely down to the theme.

Also, I don't understand this lack of documentation thing, there's plenty for GTK+.

I'd like to remind people that it's Qt with a small 't' and GTK+ with a plus ('+').

---

### Post by garba on 2009-01-30
funny thing is in the end we'll end up with two different toolkits (one being qt 4.5 and a revamped gtk) and, to top it off, someone will come up with the idea "hey what about a layer to make gtk and qt apps (ie gnome and kde apps) work nicely together"... yeah that makes sense (development efforts spread across two different toolkits plus some perverted freedesktop-like specs aimed at interoperability and the like) this is what the linux desktop has been like for 10 years after all hasn't it? "the oss community promotes standards!" sure but what about promoting only one at a time ^^?

---

### Post by Virtual DarKness on 2009-01-31
> **gururise said:**
> Apparently Mark Shuttleworth, the head financier of the Ubuntu Project, believes there is merit in [porting Gnome to use Qt]("http://tech.slashdot.org/article.pl?sid=08/07/14/1245204&from=rss"). 

Its about time to standardize on one GUI toolkit so that we can compete against Windows and MacOS. Their would also be other advantages, in terms of memory usage, to converging the libs.


I do fully agree with this.. I think that for linux, having two main GUI toolkit is a big problem cause don't let the community have a "standard"... I mean.. take a look at the screenshots of windows standard apps of the last ten years.. ok they changed, but not that much*. The only apps that looked out of place were java apps with Swing Metal theme. On linux you can have fake QT styles on gnome or fake Gtk style on KDE but they looks crap, like when you set Gtk theme for java apps. Ok maybe not "crap" but there are too many glitches and also.. the file/save dialogs for java apps are not the standard of the operating system and this happens between gnome and kde too.. if you're running a gtk app on gnome you'll get the open/save dialog of gtk apps of course..

so.. if you think in terms of gnome "vs" kde thinking that your main desktop env. (let's say, kde) is which a user would consider the "standard" interface and the other (let's say gnome) is which the user would consider a "foreign" then you can ask yourself which was one of the biggest reasons that java isn't so popular. (don't believe? then think that ppl prefer to code in mono so that the app will have a native gtk look instead of using java [don't think that mono has better performance])

so that's why it is wrong (imho) to say:
> But the thing is there would not be choice.

bye,
Giovanni.

p.s.
* = if you then look at the screenshots of linux desktops in the last ten years you'll see a big mess.. this was ok cause it was the sign of a fast evolution but now it is time for standardize or the user will always have the feeling that he is not using "a product" or "an environment" but a lot of things glued together..

p.p.s.
also.. the fact that a new users that wants to start developing linux apps have to choose if to use QT or GTK for his apps is not a good thing.. one reason (but there are many) is that there is less documentation.. another one is that once he has made his choice he his on a rail that will make him feel like if he has "bet" his time on a toolkit and then have to fight to keep it alive (and this is maybe the main obstacle for the QT + GTK merge) so this makes cooperation more difficult between developers that has choosen different GUI Toolkits. And keep in mind: we are talking about something that should be -the same operating system- but it looks like two operating systems mixed together that uses the same kernel.

---

### Post by xirtus on 2009-02-07
> **bruce89 said:**
> 

GNOME 3.0 may bring JavaScript to the desktop.


could you ellaborate a little more? what is google and gnome via gtk+ v8 and javascript all conspiring to make the worlds most leanest meanest gui?

---

### Post by bruce89 on 2009-02-07
> **garba said:**
> funny thing is in the end we'll end up with two different toolkits (one being qt 4.5 and a revamped gtk) and, to top it off, someone will come up with the idea "hey what about a layer to make gtk and qt apps (ie gnome and kde apps) work nicely together"... yeah that makes sense (development efforts spread across two different toolkits plus some perverted freedesktop-like specs aimed at interoperability and the like) this is what the linux desktop has been like for 10 years after all hasn't it? "the oss community promotes standards!" sure but what about promoting only one at a time ^^?

funny thing is in the end we'll end up with two different distros and, to top it off [..] yeah that makes sense (development efforts spread across two different distros plus some perverted freedesktop-like specs aimed at interoperability and the like) this is what the linux desktop has been like for 10 years after all hasn't it? "the oss community promotes standards!" sure but what about promoting only one at a time ^^?

In other words, if you say there should be only one toolkit, then there should also be one distro, one DE, one text editor...

> **xirtus said:**
> could you ellaborate a little more?

Certainly. [gnome-shell]("http://live.gnome.org/GnomeShell") is a prototype replacement of gnome-panel and Metacity. AFAIK most of the applets and extensions are written in JavaScript. The only snag is the fact (for now), they are using the Mozilla JS library.

---

### Post by conorsulli on 2009-08-04
Yikes! I'm no expert on programming but what would happen to gtk and all the apps wrote on top of it? pidgin, brasero, gimp, Google-chrome(Linux port) this seems a bit mad to me? would it not be more intelligent to implement any missing qt features in gtk! People who just newly released apps for gtk would feel that their software is outdated ..... I like Nokia's efforts with qt but this seems mad... again im just your average user.. correct me if I'm wrong.

---

### Post by Martiini on 2010-03-02
so ...In conclusion. 
1. What are the main reasons gnome has not been ported to qt.
2. What is the amount of effort that would bring us qt-gnome?
(personally, I'm totally in favour of qt-gnome)

---

