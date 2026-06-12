---
title: "Beryl and Compiz to merge...soon"
date: 2007-03-23
forum: The Cafe
---

### Post by ComplexNumber on 2007-03-23
i think this is good news. i'm not that keen on forks, unless its for a fully justifiable purpose. in the case of beryl, it wasn't.

> Well, I've read all the arguments, and I think I may have been being overly 
cautious.  It is indeed a concern that we might lose our freedom in 
a 'merge', but I have been convinced that it isn't a major concern (and of 
course we reserve the right to re-fork).

We do indeed need to choose a third, new name in a merge, and of course 
(again) rename the beryl-named components, for the obvious reasons.

I hope that we can execute this in a way that the average user sticks with it 
and isn't overwhelmed / doesn't feel left behind.

The only real question in my mind right now is what we should do at/about UDS.  
I am sure there is still reason for us to attend, as I doubt the merge will 
be complete by then, especially with so much code, and so many processes to 
go through.  I also believe that beryl's user-focused model is better for 
Ubuntu, and that having Beryl devs going will give Ubuntu a good working 
relationship with people in the new project who can keep things on track for 
them and their goals (and especially their users)

I know this is kinda a flip-flop from my last position, but its because I 
actually have paid attention to what the various people have commented on the 
obby document, etc.

I hope for good things in the future for all of us.

			--Quinn
 [http://lists.beryl-project.org/pipermail/beryl-dev/2007-March/000356.html](http://lists.beryl-project.org/pipermail/beryl-dev/2007-March/000356.html)






what do you think - do you think this is good news, or do you prefer them to be separate?

---

### Post by PriceChild on 2007-03-23
We'll see :)

Personally I liked my seperate beryl.

---

### Post by darweth on 2007-03-23
Terrible news.

---

### Post by hanzomon4 on 2007-03-23
> **PriceChild said:**
> We'll see :)

Personally I liked my seperate beryl.

Same here, 

It seemed like the compiz folks looked down on compiz-quinn back in the day, *watching with interest*

---

### Post by Hendrixski on 2007-03-23
Forks are not always bad.

Too many forks is always bad, and no forks is always bad.  The trick is just the right amount of forks.

unfortunately, users do not always understand why forks happened, and that is bad.  I like both Beryl and Compiz, though I've only used compiz when trying out Mandriva.  I don't immediately see why they forked, but I appreciate having two options to chose from.  perhaps one will become more professional and the other an eye sore, or perhaps both will be excelent.

---

### Post by FyreBrand on 2007-03-23
> **ComplexNumber said:**
> i think this is good news. i'm not that keen on forks, unless its for a fully justifiable purpose. in the case of beryl, it wasn't.

 [http://lists.beryl-project.org/pipermail/beryl-dev/2007-March/000356.html](http://lists.beryl-project.org/pipermail/beryl-dev/2007-March/000356.html)

what do you think - do you think this is good news, or do you prefer them to be separate?I feel the same way about forks.  I think they happen too often for the wrong reasons and end up weakening resources.  I'm a pretty big believer in consensus and compromise.

> **PriceChild said:**
> We'll see :)

Personally I liked my seperate beryl.The reason I currently like the separate development is that Beryl offers something for non-gnome users.  Compiz, at least how it's implemented in Ubuntu, is heavily tied to gnome.  Well it requires ubuntu-desktop as a dependency doesn't it?

Beryl still has a lot of gnome friendliness, especially in the emerald theme department, but but is separate enough from any individual DE that it doesn't drag extra requirements with it.

Overall I hope the developers can get back on the same page, compromise a bit, and pool resources.

---

### Post by FuturePilot on 2007-03-23
I think that Beryl excelled at what Compiz didn't. Compiz is lighter weight and seems to lack a lot of the cool features of Beryl. I also agree that a fork isn't always a bad thing. It has the potential to develop new stuff. I wonder why though they decided to include Compiz in Feisty instead of Beryl since Compiz is just about dead now.

---

### Post by macogw on 2007-03-23
> **darweth said:**
> Terrible news.

Agreed, because Beryl works and Compiz just crashes.  I'm using Feisty so Compiz is here by default.  When I activate it, everything goes nuts.  I can't even change workspaces, and there are no bars on the windows.  It's like running Beryl without GTK (Heliodor) OR Emerald!   When I start up Beryl, everything works perfectly.  Also, Compiz has pretty much nothing.  All it has is wobbles and cube, and as far as I can figure out, there's nothing there for configuring Compiz at all.  At least I can't find any kind of manager app for Compiz on my computer.

---

### Post by FuturePilot on 2007-03-23
> **macogw said:**
>   All it has is wobbles and cube, and as far as I can figure out, there's nothing there for configuring Compiz at all.  At least I can't find any kind of manager app for Compiz on my computer.

I actually found a Compiz Manager. It took me awhile but I found one.

---

### Post by Foxmike on 2007-03-23
Well I have been using Beryl for a while, then decided to try Compiz... I must say that I like Compiz a lot for its lightweightness (I do not have much resources on my computer).  I have found it a little more stable than Beryl, and, frankly, I don't use a lot all those plugins offered to mewith beryl, so...

Bad new?  Good new?  I don't know since I don't know why they forked yet I don't know why they merge now.

-- FM

---

### Post by maniacmusician on 2007-03-23
I think an ideal situation to appease the majority of beryl **and** compiz users is to keep them seperate, but share development and code between the two of them. As people have found, Compiz is often more lightweight than Beryl. Beryl is definitely more tricked out. Those are the main selling points of the two window managers.

So I say keep Beryl as the super-featured version, and Compiz as the lightweight/conservative version. At the same time, shared development would allow for extremely easy ports of features from one to the other and there would be less conflict. The users would also be happy. It's the ideal solution, in my opinion.

---

### Post by darkhatter on 2007-03-23
not sure why everyone is giving opinion's, its already to late. what I want to see is the merge of compiz into Kwin so I can configure everything from the control center

---

### Post by maniacmusician on 2007-03-23
because as Quinn said, there is always the option of re-forking later or calling off the fork. In that scenario, there's nothing wrong with expressing opinions.

As for merging Compiz into KWin; yeah right. The best-case scenario is better integration between the two and some kind of communications layer (so that KWin becomes more aware of the compositing and doesn't try to render non-composite stuff in a way that just looks like crap), but even that might be a little dreamy; I haven't seen anyone working on anything like that. 

If the basic communications layer is in place, I'm sure someone would build a kcmshell for it.

---

### Post by dbbolton on 2007-03-23
i think beryl and compiz are both more trouble than they're worth. awesome nonetheless.

---

### Post by Xenogis on 2007-03-23
I am against it. Compiz is more stable and faster for my desktop computer which others use. Beryl is slower and flashier for my laptop where I can show stuff off and not worry about anyone bitching about how it is too slow.

---

### Post by maniacmusician on 2007-03-23
> **dbbolton said:**
> i think beryl and compiz are both more trouble than they're worth. awesome nonetheless.
off topic so I don't want to digress too much, but to be honest, they're not that much trouble anymore. It's installing XGL (if you need it *coughATIcough*) that's the hard part. With nVidia drivers, it takes me all of about 15 minutes to have beryl up and running without any problems. And unless I'm using the SVN snapshot repo, it's usually pretty stable as well. 

Okay, back to the scheduled programming.

---

### Post by hanzomon4 on 2007-03-23
> **maniacmusician said:**
> off topic so I don't want to digress too much, but to be honest, they're not that much trouble anymore. It's installing XGL (if you need it *coughATIcough*) that's the hard part. With nVidia drivers, it takes me all of about 15 minutes to have beryl up and running without any problems. And unless I'm using the SVN snapshot repo, it's usually pretty stable as well. 

Okay, back to the scheduled programming.

Amen, I concur

---

### Post by TheMono on 2007-03-24
I'm in favour of the merge, I think development is at a stage now where the compiz approach is going to come in really useful, but ONLY building off the imagination and breakthroughs made by the Beryl people.

Taking what Beryl has, and smoothing it out and cleaning it up is something which favours the compiz approach. 

As far as GNOME integration, I think the comment before slightly misinterpreted it. Compiz does not require ubuntu-desktop as a dependency, it is the other way round. Compiz is installed as a dependency of ubuntu-desktop.

I don't think we will see a regression of KDE integration after a merge.

---

### Post by prizrak on 2007-03-24
I think that for now they will benefit from each other and perhaps be able to speed up development of the technology. In the future, I don't know time will tell.

---

### Post by janfsd on 2007-03-24
I agree with the merge, and as far as I know you will be able to have a choice. They want to merge the compiz-extra and beryl, so if you just liked the way compiz was, dont need to install that extra package. More about it can be found here: 
[http://forum.go-compiz.org/viewtopic.php?t=709](http://forum.go-compiz.org/viewtopic.php?t=709)

---

### Post by brt on 2007-03-24
to me **this is good news**  :)

if a merge means that my emerald themes will work with compiz than this is absolutly **great news** :guitar: 

i used beryl for a while, but then i tried **gandalf's compiz binaries** and i was amazed how good it works ! it's hell more **stable and faster** on my machines (edgy + feisty). 

since then i am using compiz again, with 98% same features / effects as beryl. 

well there are some differences, e.g. no bottom cube images by now, no "middle-mouse-button-close" in scale, i can't disable shadows on panels (but afaik there is already a solution for this one in upstream)

for the user nothing will be lost with the merge, except the name. as i understand this,  it's just that all the features from beryl will come with compiz-extras, or am i wrong?

---

### Post by xopher on 2007-03-24
What Id like to see is a head on comparison of the both. In terms of speed, stability (could be hard to measure though?), and FEATURES. If a merge is what's going to happen - I (we?) don't want to lose features, on the contrary, a merge should bring more features, no?

I truly hope they'll combine the best of the two - into something phenomenal, even better than what it is now.

Im a Beryl-user, I was a compiz-quinn user before, and that's why Beryl seemed like the natural choice for me. I like the way they think - And the speed things progress. The development of beryl has been lightning-fast, and that has, well, left a few holes, bugs etc. Compiz has a reputation of being faster and more stable, I hope this is true, and I hope the expertise from both of the projects will bring us something that will change the way we look at these things. 

Compiz did it. Beryl did it. Now we're about to witness it once again - at least that's what Im hoping for.

---

### Post by graabein on 2007-03-24
I'm optimistic. Hopefully it will be lightweight and not depend on GNOME libs so people can use it on KDE and XFCE and so on. Stability and better integration/GUI for control centres are also important. Good luck to everyone!

---

### Post by daynah on 2007-03-24
Man this is terrible! Terrible!

It wont be a beryl roll anymore! And I just got it!

Terrible!

---

### Post by msak007 on 2007-03-24
Not sure if anybody's read this yet, but it seems that Beryl & Compiz are going to merge again. There's a post on the beryl-dev mailing list about it.

[http://lists.beryl-project.org/pipermail/beryl-dev/2007-March/000356.html](http://lists.beryl-project.org/pipermail/beryl-dev/2007-March/000356.html)

I personally prefer Beryl, but I hope joining forces will make the combined project even better. Competition drives innovation, and I believe in having a choice, but I also believe this was one fork / split that hurt the community more than it helped. If anything, this'll make the choice of Ubuntu's default eye-candy DE even easier :).

Share your thoughts, whether you think this is a good / bad idea, maybe even name ideas for the new project.

---

### Post by bapoumba on 2007-03-24
@ msak007: merged your thread in here.

---

### Post by msak007 on 2007-03-24
> **bapoumba said:**
> @ msak007: merged your thread in here.
Sorry, I searched the forums first to make sure nobody posted this already and looked where I thought this topic was appropriate (the Desktop Effects subforum).

---

### Post by jsmidt on 2007-03-24
This is excellent news.  Now the two will work together.  

I'm sure the compiz "lightweightness" will be installed by default and all the bulk of beryl will be on click away by some new "mega-extra-plugins package."

Thus I'm sure everyone will be happy and the coding will progress faster with both teams merged. 

What I would like to see is a gnome 3.0 based on composite window management.

---

### Post by igknighted on 2007-03-24
I cannot believe this isn't all over the forum: word has it Beryl and Compiz are re-merging.  And on top of that, word also has it they are going to be developing primarily for Ubuntu.  Lots of unhappy people on other distros, but a good thing for Ubuntu I suppose?

Source: [http://www.sabayonlinux.org/forum/viewtopic.php?t=5568](http://www.sabayonlinux.org/forum/viewtopic.php?t=5568)

---

### Post by CarpKing on 2007-03-24
I think this is a good thing.  Forks may be useful sometimes (and perhaps an argument could be made that in this case the fork was beneficial for a time), but the plugin-based modular nature of Compiz and Beryl really lend themselves more to one core and a wide variety of plugins, with the amount of flashiness determined by how many plugins are installed/ turned on, rather than the current situation of porting plugins back and forth between two slightly different cores.

---

### Post by Polygon on 2007-03-24
lol i like the comments in that thread.. ubuntu sucks... ubuntu will become the next windows.... yeah yeah yeah.

anyway just because its developed for ubuntu does not mean it cant work in other distros. No one complained when sabayon was selected to be the main development platform for beryl.... why should they complain that it is now ubuntu?

---

### Post by igknighted on 2007-03-24
> **jsmidt said:**
> This is excellent news.  Now the two will work together.  

I'm sure the compiz "lightweightness" will be installed by default and all the bulk of beryl will be on click away by some new "mega-extra-plugins package."

Thus I'm sure everyone will be happy and the coding will progress faster with both teams merged. 

What I would like to see is a gnome 3.0 based on composite window management.

Sigh, there goes the speculation that Beryl would merge with KDE to give KDE these features natively.  I hope someone decides to start that project, as a return to compiz scares the crap out of me.  From a bugfix and development standpoint, I like the merge.  But I am a KDE user.  I keep any and all gnome stuff I can off my system (not because I hate gnome, but for speed... my kde w/ beryl FLIES).  If Beryl starts to depend on Gnome again, this is a VERY VERY bad thing for me and all other KDE users.

---

### Post by igknighted on 2007-03-24
> **Polygon said:**
> lol i like the comments in that thread.. ubuntu sucks... ubuntu will become the next windows.... yeah yeah yeah.

anyway just because its developed for ubuntu does not mean it cant work in other distros. No one complained when sabayon was selected to be the main development platform for beryl.... why should they complain that it is now ubuntu?

To be fair, Sabayon never really cared about that title.  As a Sabayon user I actually despised it, because people began to view Sabayon as a Beryl preview CD.  I understand where the frustration is coming from.  Ubuntu is a great distro, but gets an inordinate amount of attention.  Go to digg.com and almost anything Ubuntu gets to the front page.  Outside of this community, Ubuntu users are often seen in a similar light to Mac fanboys.  Fair or not, that is the image.  I think I'll start a poll on this in another thread...

To the point, I think Ubuntu has done the least for beryl/compiz of any distro.  It's the only major distro that has no easy setup config tools (even for the free stuff).  Even Feisty has almost nothing in this regard.  Sure compiz is available, but theres no good setup tools.  Sabayon, Fedora, Suse, Mandriva/PCLOS, Gentoo... they all have tools available to help set it up. Ubuntu?  Theres a long wiki page that leads to all the problems we see.  Mint is working on an app to do this, but its not even at a semi-usable alpha yet.  Hopefully as it develops it will come back upstream.

EDIT: I found the main thread finally, feel free to merge this one.

---

### Post by bapoumba on 2007-03-24
@ igknighted: merged your thread.

---

### Post by potrick on 2007-03-24
Am I the only one sad about this because I prefer Compiz, and don't want to see the Beryl bloat added to it? Beryl's great but for those of us with integrated video cards Compiz is much better, unless Beryl has simply jumped forward leaps and bounds since January.

---

### Post by troymcdavis on 2007-03-24
I too am a compiz fan because I prefer the stability/speed over features. However, I don't see the merger being a problem; I guess there could still be a stable/unstable model of development much like there is Debian stable/unstable/experimental, but they are all Debian, right? I think feature selection will also only get better, thus bloat on the performance end will be kept in check by the capability to easily turn features off. As for physical space bloat, I suppose if there's enough demand for it, another version will be made (Beryl/Compiz Lite?), but HDD space is so cheap these days...

---

### Post by brt on 2007-03-27
> **potrick said:**
> Am I the only one sad about this because I prefer Compiz, and don't want to see the Beryl bloat added to it? Beryl's great but for those of us with integrated video cards Compiz is much better, unless Beryl has simply jumped forward leaps and bounds since January.

afaik, if the merge is finished you will still be able to decide if you want all the extra-stuff or just plain "thin" compiz.

and on the other side for those who still prefer beryl, i am sure once the merged compiz+"ex-beryl" has one feature more than beryl had, they will switch to compiz+"ex-beryl" immediatly :) 

so where are the worries?

---

### Post by ButteBlues on 2007-03-27
Think of it like this:

Compiz-Core:
Compiz
Compiz Default Plugins
GTK Window Decorator
KDE Window Decorator

Compiz-Extra:
Non-Default Plugins
Specialized Window Decorator
Apps that rely on Composite Environment (Screenlets) etc
Other Compiz-Related Apps

---

### Post by ComplexNumber on 2007-04-05
more (official) news on this [here]("http://compiz.blogspot.com/2007/04/official-announcement-of-merge.html").

---

### Post by Extreme Coder on 2007-04-11
IMO, I think they should've just modified Beryl for KDE instead of merging, KDE needs its wobbly windows and cubes too ;) But its still good news.

---

### Post by maniacmusician on 2007-04-11
> **potrick said:**
> Am I the only one sad about this because I prefer Compiz, and don't want to see the Beryl bloat added to it? Beryl's great but for those of us with integrated video cards Compiz is much better, unless Beryl has simply jumped forward leaps and bounds since January.
Exactly; and some people prefer Beryl because it gives them a lot more fetaures and their video cards can handle it. They are both targeted at different audiences, which is why the project was forked in the first place. The merge, I think, is a bad idea. 

It would be good for them to set up a centralized HQ where they could share code and ideas, port certain features back and forth, but the projects themselves should be separate, since they serve different user bases and have different purposes.

---

### Post by corstar on 2007-04-11
If people aren't happy with the reunion, just counter-fork it...
That's the beauty of open source.

---

### Post by maniacmusician on 2007-04-11
> **corstar said:**
> If people aren't happy with the reunion, just counter-fork it...
That's the beauty of open source.
yeah, but 99% of the people reading this don't have the resources/time/knowledge to fork a project that big. It worked for Quinn because she already had her own little version of Compiz happening, with a solid team built around it. It was easy to fork and take the team with her. Most people just dont have that luxury.

---

### Post by ButteBlues on 2007-04-12
> **corstar said:**
> If people aren't happy with the reunion, just counter-fork it...
That's the beauty of open source.
The point of the merger was to eliminate duplicated effort.

---

### Post by CarpKing on 2007-04-12
Besides, code-wise Beryl isn't really merging with Compiz.  It's merging with Compiz-Extra.  The communities will be merging, which will hopefully bring another huge benefit which may not be obvious to those who don't frequent either: the end of pointless but vehement bickering between two communities that want basically the same thing, sometime not even to different degrees (the majority of Beryl plugins had already been ported to Compiz before the merger started).

---

### Post by junior aspirin on 2007-04-12
the way i understand this is as so. although i maybe wrong

the two are merging to form a rock stable core, with no effects or anything, this just makes things work. (call this compiz-core)
then everything else will be plugins, as configuable as you like, and as many as you like.
maybe a compiz-basic package for simpleness, and a compiz-extra and compiz-unstable for those who want beryl like features.

i don't see what the big panic is myself. The want a very stable core, that is extensible by plugins.  it should hopefully allow for better integration with the desktop environments, improved stability, and no duplication of work and without the confusion, since beryl is practically compiz anyway, just with all the 'bling' as it were.

wish the devs and the communities all the best :D

---

### Post by igknighted on 2007-04-12
> **junior aspirin said:**
> the way i understand this is as so. although i maybe wrong

the two are merging to form a rock stable core, with no effects or anything, this just makes things work. (call this compiz-core)
then everything else will be plugins, as configuable as you like, and as many as you like.
maybe a compiz-basic package for simpleness, and a compiz-extra and compiz-unstable for those who want beryl like features.

i don't see what the big panic is myself. The want a very stable core, that is extensible by plugins.  it should hopefully allow for better integration with the desktop environments, improved stability, and no duplication of work and without the confusion, since beryl is practically compiz anyway, just with all the 'bling' as it were.

wish the devs and the communities all the best :D

Part of the issue is that compiz has routinely ignored KDE and been built to run well on gnome using gnome libs at times.  Beryl took a more generic approach and is more friendly to KDE (or other non-gnome) users.  If the merge means a return to the gnome approach, *shudders*.

---

### Post by CarpKing on 2007-04-12
> **igknighted said:**
> If the merge means a return to the gnome approach, *shudders*.

They are implementing (or have recently implemented) a flat file backend (it will still be configurable through Gconf, but will not depend on it), and configuration apps along the lines of BSM are in the works for both KDE and Gnome.  Also, BSM will likely be ported to Compiz.

---

### Post by Anthem on 2007-04-12
I'm thrilled about this.

It also means that composite-by-default will be a no-brainer for Gutsy Gibbon.

---

### Post by ButteBlues on 2007-04-12
> **igknighted said:**
> Part of the issue is that compiz has routinely ignored KDE and been built to run well on gnome using gnome libs at times.  Beryl took a more generic approach and is more friendly to KDE (or other non-gnome) users.  If the merge means a return to the gnome approach, *shudders*.

Much of this is FUD.

The only "Gnome" dependency in Compiz 0.3.6 was... gconf.

Beryl (including settings manager) depended on GLib and GTK.

I'll let you compare that for yourself.



As noted, with kde-window-decorator and ini settings backend in place, there is no reason for KDE users to complain about Compiz.

> **junior aspirin said:**
> the way i understand this is as so. although i maybe wrong

the two are merging to form a rock stable core, with no effects or anything, this just makes things work. (call this compiz-core)
then everything else will be plugins, as configuable as you like, and as many as you like.
maybe a compiz-basic package for simpleness, and a compiz-extra and compiz-unstable for those who want beryl like features.

i don't see what the big panic is myself. The want a very stable core, that is extensible by plugins.  it should hopefully allow for better integration with the desktop environments, improved stability, and no duplication of work and without the confusion, since beryl is practically compiz anyway, just with all the 'bling' as it were.

wish the devs and the communities all the best :D

Not quite.

The core will be exactly the same as it is now: with basic plugins and the like.

Compiz-Extra will be essentially like it is now, but with more developers working on the plugins.


Make sense?

---

### Post by Analord on 2007-04-25
Personaly i think that in general merge is a good thing.

I prefer beryl over compiz.

You can adjust beryl to 'be compiz' with any problems.

In the current merge i hope that beryl current 'stuff' will be avalible in the new merged product.

In my opinion compiz lacks options especialy cube regarding (transparency, zoom out on rotate etc.), and many other.

---

