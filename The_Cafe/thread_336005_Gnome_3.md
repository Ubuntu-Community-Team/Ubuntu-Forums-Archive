---
title: "Gnome 3"
date: 2007-01-11
forum: The Cafe
---

### Post by Quillz on 2007-01-11
Is there any concrete info on what will be in GNOME 3, or when it's planned for some eventual release? With KDE 4 coming out (hopefully) this year, I was wondering what GNOME would be adding to remain competitive.

---

### Post by Engnome on 2007-01-11
There is no real reason for GNOME 3 yet, small upgrades to GNOME 2 upgrading it and making it better is good enough. 

[http://live.gnome.org/ThreePointZero](http://live.gnome.org/ThreePointZero)

---

### Post by rai4shu2 on 2007-01-11
If GTK ever implements GTK+ 3.0, that might be a good time to change the version number for Gnome. Doesn't look like it'll be any time soon.

[http://www.gtk.org/plan/](http://www.gtk.org/plan/)

---

### Post by Quillz on 2007-01-11
> **There are no plans for a GNOME 3.0 release at this time. The GNOME community believes that regular, reliable, iterative improvements are more important to our users than ground-shaking major releases, and that we can more comfortably deliver major features -- when they're ready -- in our regular, six-monthly releases.** 
We made a substantial API/ABI break for GTK+ and GNOME 2.0, which was a massively beneficial change for our platform, and has allowed us to maintain a stable branch for a significant period of time. We're still deriving enormous benefit from the break *and* the stability. As such, we do not plan to do the same again soon. 
[LIST]
[*]A major rewrite or API break **won't** provide any benefit to our users, contributors, or independent developers creating software based on the GNOME platform. 
[*]A major rewrite or API break is **not at all** necessary to achieve our goals for or enhance active development on the GNOME experience in the forseeable future. 
[*]A major rewrite or API break **won't** have a positive impact on the broadening ecosystem around the GNOME platform, such as activity around mobile and embedded device development with GTK+ and GNOME.
[/LIST]
Well, I guess that explains it all.

---

### Post by Pobega on 2007-01-11
I read in this month's *Linux Format* that they're **just** starting with 2.16, so plans for Gnome 3 probably won't be arising for a while.

---

### Post by G Morgan on 2007-01-11
It'll happen when they realise how good KDE4 is going to be and how much catch up work they will have to do*. The ability to run on OSX and Win XP is a killer feature for KDE4 and could sway control of the OSS desktop back in their favour. They are also annihilating most of the most annoying problems in KDE. No longer will everything begin with K, Arts is finally going to die and never come back, a serious UI shake up is planned to simplify things.

Fortunately for GNOME they could port large chunks of the KDE4 system into their own without much difficulty. For example I don't think Phonon depends on anything in QT and could be ported as the standard audio API for GNOME without untangling a mass of KDE built around it.

Really I'd like to see both put a lot of effort into Portland though.

*this depends on the GStreamer team stabilising their API so a Phonon plugin for it can be built.

---

### Post by Patrick-Ruff on 2007-01-11
I don't think gnome is going to break their promis just because something "might" get more publicity then them, at this point I can guarentee you it probably wont happen.

---

### Post by fuscia on 2007-01-11
kde4 > gnome3

---

### Post by viciouslime on 2007-01-11
> **fuscia said:**
> kde4 > gnome3

<gasp> :-#

---

### Post by manmower on 2007-01-11
> **Patrick-Ruff said:**
> I don't think gnome is going to break their promis just because something "might" get more publicity then them, at this point I can guarentee you it probably wont happen.

I agree, some users seem to care a lot more about this alleged "competition" between Gnome and KDE than the developers do. Gnome is doing fine and there's nothing wrong with more gradually upgrading. They seem to have some nice stuff of their own planned such as the built-in compositing capability in Metacity. I don't see why they would feel the need to rush out a release just because KDE is getting a major overhaul.

---

### Post by Mateo on 2007-01-11
someone explain to me what gtk is.  thansk.

---

### Post by GeneralZod on 2007-01-11
> **Mateo said:**
> someone explain to me what gtk is.  thansk.

Simply: The graphics toolkit used by GNOME.  Used for drawing and interacting with widgets such as buttons, lists, menus etc.   The graphics toolkit used by KDE is Qt.

[http://en.wikipedia.org/wiki/Gtk](http://en.wikipedia.org/wiki/Gtk)
[http://en.wikipedia.org/wiki/Qt_%28toolkit%29](http://en.wikipedia.org/wiki/Qt_%28toolkit%29)

> **G Morgan said:**
> It'll happen when they realise how good KDE4 is going to be and how much catch up work they will have to do*. The ability to run on OSX and Win XP is a killer feature for KDE4 and could sway control of the OSS desktop back in their favour. They are also annihilating most of the most annoying problems in KDE. No longer will everything begin with K, Arts is finally going to die and never come back, a serious UI shake up is planned to simplify things.

Fortunately for GNOME they could port large chunks of the KDE4 system into their own without much difficulty. For example I don't think Phonon depends on anything in QT and could be ported as the standard audio API for GNOME without untangling a mass of KDE built around it.

Really I'd like to see both put a lot of effort into Portland though.

*this depends on the GStreamer team stabilising their API so a Phonon plugin for it can be built.

It's way too early to tell what KDE4 will be like and implying that it will be much better than GNOME is very premature, especially given that some of the "pillars" of KDE are very, very underdeveloped (the much-hyped Plasma, for instance, and assuming that Aaron is using KDE's svn, is currently less than 2000 lines of code, about a third of which are header files).  Also, the KDE guys don't have much control over what third-party guys name their apps, although none of mine will ever begin with "K" ;).  Pretty much the whole reason for being of Phonon is that gstreamer *doesn't* have a stable API, so the gstreamer back-end will likely always be in flux: this is not too much of a headache, though.

---

### Post by ComplexNumber on 2007-01-11
> **Quillz said:**
> Is there any concrete info on what will be in GNOME 3, or when it's planned for some eventual release? With KDE 4 coming out (hopefully) this year, I was wondering what GNOME would be adding to remain competitive.
it doesn't need to 'remain' competitive. gnome is currently replacing gnome-vfs and it could do with replacing bonobo. but other than that, can you see any area of gnome that needs to be improved with a massive overhaul? kde, on the otherhand, in its present state is in dire need of an overhaul, and can't realistically continue in its present direction.

---

### Post by G Morgan on 2007-01-11
> **GeneralZod said:**
> Simply: The graphics toolkit used by GNOME.  Used for drawing and interacting with widgets such as buttons, lists, menus etc.   The graphics toolkit used by KDE is Qt.

[http://en.wikipedia.org/wiki/Gtk](http://en.wikipedia.org/wiki/Gtk)
[http://en.wikipedia.org/wiki/Qt_%28toolkit%29](http://en.wikipedia.org/wiki/Qt_%28toolkit%29)



It's way too early to tell what KDE4 will be like and implying that it will be much better than GNOME is very premature, especially given that some of the "pillars" of KDE are very, very underdeveloped (the much-hyped Plasma, for instance, and assuming that Aaron is using KDE's svn, is currently less than 2000 lines of code, about a third of which are header files).  Also, the KDE guys don't have much control over what third-party guys name their apps, although none of mine will ever begin with "K" ;).  Pretty much the whole reason for being of Phonon is that gstreamer *doesn't* have a stable API, so the gstreamer back-end will likely always be in flux: this is not too much of a headache, though.

It'll all work, it's just a matter of if they will meet their release date or whether it will become 'done when its done'.

Do the gstreamer team never plan to have a stable API then. What'll probably happen is distros will take a snapshot and declare that as stable even if the gstreamer team say otherwise.

---

### Post by Sef on 2007-01-11
> I read in this month's Linux Format that they're just starting with 2.16, so plans for Gnome 3 probably won't be arising for a while.

2.16 is the current stable version.   2.17 is the current unstable version with 2.18 stable due in March.

---

### Post by jbus on 2007-01-11
What I would like to see in gnome is the ability to apply the current GTK theme and colors to KDE applications. KDE can apply the current KDE theme to GTK apps, so I think this should be possible for gnome as well and it would go a long way  for improving the look and feel of the gnome desktop.

Also, gnome desperately needs a new taskbar that looks better and takes up less space than the window list currently does.

Other than that, I think gnome is a great desktop.

---

### Post by plb on 2007-01-11
I just hope KDE 4 won't end up with that horrid kickoff menu from opensuse 10.2

---

### Post by EdThaSlayer on 2007-01-11
GNOME is already used by lets see...80% of Ubuntu users(and 8 million times .8 is...). GNOME 2 just needs to evolve a bit more. GNOME by itself is already a really good and stable project and lots of people are happy with the way things are at the moment. Who knows, in 2008 maybe GNOME 3.0 might pop up to deliver the eye candy that people are thirsty for.

---

### Post by ComplexNumber on 2007-01-11
> in 2008 maybe GNOME 3.0 might pop up to deliver the eye candy that people are thirsty for.what type of "eye candy" is this that people are apparently thirsty for? i mean, what do you want? holographic 3D images of spaceships shooting past your left eye when you're trying to type  a letter to your mum.
gnome 2 is just fine in the eye candy department.

---

### Post by insane_alien on 2007-01-11
y'know what, gnome works good for me just now. i can't afford to take the risk of screwing something up by changing things at the moment so i'm staying put. in march i'll be going on a config changing binge though unless something else pops up.

---

### Post by Erunno on 2007-01-11
> **ComplexNumber said:**
> kde, on the otherhand, in its present state is in dire need of an overhaul, and can't realistically continue in its present direction.

Answering to ComplexNumber's posts is likely to become an addiction of mine.  ;)

Anyway, which direction do you mean ?

The

1. building superior technology 

or

2. having awful default GUI's for their applications which need a lot of tweaking after installation ?

I strongly disagree with point 1 as I'd really hate to see KDE throw away half of their current features just to "catch up" with GNOME. I fully agree on the second one though, the default interfaces need some hot and passionate love from the HIG people. Let's hope that we'll see some of their improvements in the KDE 4.0 release as I'm slowly starting to doubt that anything worth noting besides the switch to QT4 will be in the initial release plus some incremental updates to the current apps.

I can't tell right now what would warrant GNOME 3.0 at the moment. I'd rather see them include some of the missing functionality for casual users (a decent trash can, pretty please) and deepened cooperation with third party software developers which GNOME depends on, most notably OpenOffice and Firefox which still don't fit nicely into the DE itself.

---

### Post by ComplexNumber on 2007-01-11
> **Erunno said:**
> Answering to ComplexNumber's posts is likely to become an addiction of mine.  ;)

Anyway, which direction do you mean ?

The

1. building superior technology 

or

2. having awful default GUI's for their applications which need a lot of tweaking after installation ?

I strongly disagree with point 1 as I'd really hate to see KDE throw away half of their current features just to "catch up" with GNOME. I fully agree on the second one though, the default interfaces need some hot and passionate love from the HIG people. Let's hope that we'll see some of their improvements in the KDE 4.0 release as I'm slowly starting to doubt that anything worth noting besides the switch to QT4 will be in the initial release plus some incremental updates to the current apps.

well, you only have to ask yourself the following question: "apart from kparts and kioslaves, name me one framework that both DE's share or are due to share that is in a more advanced stage on kde?". and there you have you answer. i suppose one could include superkaramba in there because its much better than gdesklets, but thats not a fault of the actual framework, but more a fault of the developers of the actual gdesklets.

---

### Post by RChickenMan on 2007-01-11
I have a lot of respect for their attitude regarding the idea of a GNOME 3.0.  As opposed to trying to make it seem like they are "staying competitive" with KDE, they just come right out and say that a total overhaul just really isn't necessary, nor would it be advantageous.

---

### Post by henriquemaia on 2007-01-11
No need to hurry on that.

---

### Post by Erunno on 2007-01-11
> **ComplexNumber said:**
> well, you only have to ask yourself the following question: "apart from kparts and kioslaves, name me one framework that both DE's share or are due to share that is in a more advanced stage on kde?". and there you have you answer. i suppose one could include superkaramba in there because its much better than gdesklets, but thats not a fault of the actual framework, but more a fault of the developers of the actual gdesklets.

Both of said frameworks are a core part of KDE. It's tight integration is founded upon it and provide most of the KDE's additional functionality which GNOME lacks. This is a huge "apart from" to be sure ! :D

Or what about kiosk mode ? I know it was mainly developed for system administrators but it comes in handy when trying to tame the beast that is KDE.

Anyways, it's difficult to talk about the frameworks right now as the KDE3 line is becoming obsolete and we don't know how well the new ones will work in the wild.
 
> I have a lot of respect for their attitude regarding the idea of a GNOME 3.0. As opposed to trying to make it seem like they are "staying competitive" with KDE, they just come right out and say that a total overhaul just really isn't necessary, nor would it be advantageous.

Well, one could argue that this is not solely done by choice. When browsing various forums and tech sites I get the impression that GNOME lacks developers especially in core components like GTK+. Well, let's put it this way: The KDE developers seem to have a grander technical vision about the future of desktop environments than their counterparts and the manpower to accomplish them in time :)

---

### Post by ComplexNumber on 2007-01-11
> When browsing various forums and tech sites I get the impression that GNOME lacks developers especially in core components like GTK+.you're just repeating what Thom Holwerda said over on OSNews. it was later found to be completely unsubstantiated.

---

### Post by lyceum on 2007-01-11
> **ComplexNumber said:**
> what type of "eye candy" is this that people are apparently thirsty for? i mean, what do you want? holographic 3D images of spaceships shooting past your left eye when you're trying to type  a letter to your mum.
gnome 2 is just fine in the eye candy department.

hex yes!!!

But really, Gnome is fine. When compix and beryl get better and Gnome puts them in as a normal part, then maybe 3.0. Until then, I will dream of the day when we just plug our brains in to the box.

:D

---

### Post by kripkenstein on 2007-01-11
I don't really see much of a point in comparing GNOME (or anything) to KDE4. KDE4 will contain so much rewriting and so many infrastructure changes that it is hard to tell when in fact it will be released. Also, all these changes make it hard to tell how good it will be - new code means possibly new bugs, or other new problems (will it be resource-hungry? who knows, it isn't written yet).

If KDE4 turns out great, then who knows, I may run it myself. But I am somewhat skeptical. Meanwhile I think the GNOME idea makes a lot of sense - incremental improvements, slowly adding new apps as they mature, etc.

---

### Post by ffi on 2007-01-11
> **Erunno said:**
>  I fully agree on the second one though, the default interfaces need some hot and passionate love from the HIG people. Let's hope that we'll see some of their improvements in the KDE 4.0 release as I'm slowly starting to doubt that anything worth noting besides the switch to QT4 will be in the initial release plus some incremental updates to the current apps.


Please don't let those people touch KDE, they'll take out or hide all the features they think I will never need but actually do need. I can think for myself what I need and don't need. I find Gnome to be incredibly confusing and counter intuitive whereas KDE is just very easy and intuitive.

---

### Post by Quillz on 2007-01-12
> **plb said:**
> I just hope KDE 4 won't end up with that horrid kickoff menu from opensuse 10.2
I actually like openSUSE's kicker, with the integrated Beagle. It's pretty useful.

---

