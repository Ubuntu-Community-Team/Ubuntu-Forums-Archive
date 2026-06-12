---
title: "Mir: Stop this train before it derails Ubuntu."
date: 2013-06-28
forum: Ubuntu, Linux and OS Chat
---

### Post by quequotion on 2013-06-28
This will probably end up locked and buried in Recurring Discussions, but I feel the need to express my sincere concern for the future of Ubuntu if Canonical does not cease development of Mir and return to supporting and improving Wayland.

I honestly don't mean to antagonize the developers of Mir. I understand that they have jobs to do and that they may even have justifications for Mir. I simply disagree with the way Canonical turned on Wayland and invested resources into such a huge project that will not be supported by anything else and is going to take a very long time to result in anything useful. There has already been a huge investment in Wayland and it is just starting to pay off. I feel that Canonical has, at a very critical moment, stabbed Wayland in the back, emptied its pockets, and left it for dead.

I filed a bug report on the issue: [Bug #1195623 "Waste of resources and development: likely to ostracize Ubuntu from the linux community"]("https://bugs.launchpad.net/mir/+bug/1195623").

It's my hope that people will join in the discussion here and add their valid complaints against canonical's decision to the bug report.

---

### Post by mörgæs on 2013-06-28
Moved, as this is not a support request.

If the debate is kept in a civilised manner there's no need for closing the thread.

---

### Post by quequotion on 2013-06-28
Understood. Indeed, I'm not looking for flaming or bashing here but valid reasons to reverse this course of development.

I notice in your signature a list of Ubuntu derivatives. [None of them will be compatible with Mir]("https://lists.ubuntu.com/archives/ubuntu-devel/2013-June/037250.html").

---

### Post by howefield on 2013-06-28
> **quequotion said:**
> Understood. Indeed, I'm not looking for flaming or bashing here but valid reasons to reverse this course of development.

Of course you don't, why else post such emotional guff as "I feel that Canonical has, at a very critical moment, stabbed Wayland in the back, emptied its pockets, and left it for dead."

> None of them will be compatible with Mir[/URL].

[Mir Plans In 13.10 - (Flavours running in Mir)]("http://fridge.ubuntu.com/2013/06/27/mir-plans-in-13-10/?utm_source=rss&utm_medium=rss&utm_campaign=mir-plans-in-13-10")

Whether they want it or not is another question.

---

### Post by quequotion on 2013-06-28
It may sound like emotional guff, but it's intended to make clear what's happened.

Canonical promised to develop Wayland, then took the lessons learned and abandoned it. Canonical was certainly not the only party supporting or developing Wayland, but they were one of the most important. [s]Without dedication from Canonical, development of Wayland will be handled by mostly volunteers who may come from myriad other projects[/s]. Wayland took a long time to get to where it is now, but in time will be a viable alternative to xorg. Unfortunately, the next stage of development could take much longer now that Canonical has withdrawn their support. We'll have to see which wins the race to replace xorg now that other projects, like Gnome and KDE, are dedicated to Wayland while Canonical is proceeding with Mir on their own.

> Canonical is investing in building Unity 8 support for Mir, but **other  projects are invited to build Mir backends** too. We are currently  revising and improving our documentation to make this development work  easier, and questions on this topic are welcomedStop and think about this statement: "invited to build Mir backends"
Canonical has no interest in helping the developers of other desktop environments to add compatibility.* In return, I doubt those developers are going to become interested developing for Mir, especially after all the time and work they've already invested in developing for Wayland. The teams supporting these desktop environments are not as big as Canonical and they don't have the resources to begin on a whole new framework, especially one that's hardly off to a start itself and isn't supported by any other platforms.

*"add compatiblity" may be a gross understatement. I'm not an expert on the issue, but I gather that the changes necessary to work with Mir are fundamental and in no way as simple as adding a backend.

---

### Post by MadmanRB on 2013-06-28
I would not worry about Mir, after all Kubuntu, Xubuntu and the others are mainly community developed.
This means Mir can mainly stay in the main ubuntu but have no effect on the others.
Plus there is hope that Mir would get accepted by the other DE's, its slowly happening so I would not give up on Mir.

---

### Post by quequotion on 2013-06-28
In concession, perhaps the some of the same things were said about Wayland early in it's development. Why not improve xorg? Why develop for something that isn't supported by many major distributions? etc.

Wayland eventually did garner wider support, and the design is too different from xorg to justify modifying xorg into Wayland. One of the biggest pushes to get Wayland that far was Canonical's promise to use it in future versions of Ubuntu.

---

### Post by quequotion on 2013-06-28
> **MadmanRB said:**
> I would not worry about Mir, after all Kubuntu, Xubuntu and the others are mainly community developed.
This means Mir can mainly stay in the main ubuntu but have no effect on the others. Thus, [Kubuntu]("http://blogs.kde.org/2013/06/26/kubuntu-wont-be-switching-mir-or-xmir") will not be going with Mir. Hopefully it will be as simple as having your favorite derivative's repository enabled and simply not installing Mir.
> Plus there is hope that Mir would get accepted by the other DE's, its slowly happening so I would not give up on Mir.Anything is possible. If Mir does come together as a viable display server, and the possibility of compatibly with non-Unity environments exists, then maybe.
At the moment, there is only minimal talk of this and a few shaky tests with XMir. Worse yet is the impression that Canonical isn't really concerned with this ever happening.

---

### Post by quequotion on 2013-06-28
There are some interesting comment's in SmSpillaz's blog on the topic:

[http://smspillaz.wordpress.com/2013/03/05/mir-display-server/](http://smspillaz.wordpress.com/2013/03/05/mir-display-server/)

Particularly: > "Wayland is clearly a project lead by Intel and Red Hat."

Wayland will proceed without Canonical's help, but I do think it's taken a big hit in losing support from the backer of Ubuntu. Ubuntu is intended to be the linux for the masses, and it's one of the most widespread distributions for home users (especially when including its many derivatives).

---

### Post by 3rdalbum on 2013-06-28
If Wayland has merit, it will survive. Unfortunately I have some doubts about Wayland's viability.

Wayland's approach seems to be "do as little as possible and push everything out to the clients". Because of this, there is exactly one desktop environment that can run on Wayland after five years of development.

Mir is just over a year old, and runs Unity 8. As with Wayland, there is an X compatibility layer. Unlike Wayland, Mir will actually be shipping by default in a distro later this year.

Ubuntu was already the black sheep of Linux. Adopting Wayland will not help, and Mir did not hinder Ubuntu's reputation any more than already. It is tall-poppy syndrome.

Mir won't hurt interoperability either, X11 is the common language of all three display servers. Target X11 and your app will run on any Linux distro.

---

### Post by dino99 on 2013-06-28
Stop this train ?

you miss your ticket :confused: , the train is far now and going faster & faster :P
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5NzM](http://www.phoronix.com/scan.php?page=news_item&px=MTM5NzM)

---

### Post by kurt18947 on 2013-06-28
Not being very knowledgeable in these matters, I wonder if Wayland looks viable on tablets and phones?  Projects intended solely for traditional PCs (desktops/laptops) might not have much standing at Canoncial right now.  Just guessing here.

---

### Post by buzzingrobot on 2013-06-28
As a user, I can't think of a reason why I should be upset about Mir.  X has needed replacing for years. Wayland is one effort to do that. Mir is another. Improvements in one ought to spur improvements in the other.

When full-fledged Mir is released (targeted for 14.04), I'll compare 14.04 with Unity to comparable systems running Wayland, if Wayland is ready then.  I'll make my own mind.

Developers may have their own reasons to eliminate diversity and reduce competition in Linux, but users really don't.

---

### Post by beautifulcoder on 2013-06-28
Sounds interesting, does this mean Unity will support touch?

---

### Post by quequotion on 2013-06-28
> **3rdalbum said:**
> If Wayland has merit, it will survive. Unfortunately I have some doubts about Wayland's viability.I have more doubts about Ubuntu/Mir's viability. Being singled out and excluded is generally not healthy for a project that depends on the work of such a large community. > Wayland's approach seems to be "do as little as possible and push everything out to the clients". Because of this, there is exactly one desktop environment that can run on Wayland after five years of development. Sounds like an attempt to reduce display server latency. What you say is not true: KWin and Mutter already have partial support (KDE, GNOME, MATE, Elementary, Cinnamon, etc) and the development teams behind both are fully committed to Wayland. > Mir is just over a year old, and runs Unity 8.Mir and Unity are designed by the same people, of course they *will* work together, *whenever they start to actually work*. The problem is how unlikey it is that *anything else* will ever work with Mir. Not everybody *wants* to use Unity, even though they want to use Ubuntu (or one of its derivatives). The result will be that people who don't want to use Unity won't be able to use Ubuntu; derivatives will be pushed to re-base on Debian (or something else) and Ubuntu will become a walled-garden.> As with Wayland, there is an X compatibility layer.It almost goes without saying, but a compatibility layer is a sub-optimal stop-gap solution. Eventually, applications will need to be ported. Fortunately, several toolkits already have full Wayland implementations while apparently only QT presently supports Mir.> Unlike Wayland, Mir will actually be shipping by default in a distro later this year.Remember when Unity shipped out in 11.04 and it was a train wreck? Yes, *it's happening again*. Perhaps Mir will be stable and usable by the next LTS release *after* 13.10 (14.04, coming out around April 2014, by which time Canonical *hopes* to have secured commitments from NVidia and ATI to support Mir in their binary drivers)--like Unity was finally stable and usable in 12.04 (two release cycles later).> Ubuntu was already the black sheep of Linux. Adopting Wayland will not help, and Mir did not hinder Ubuntu's reputation any more than already. It is tall-poppy syndrome.I disagree. Read the blogosphere. Mir is ruining what's left of Canonical's reputation. Developers who could have helped implement an Ubuntu/Wayland have lost interest because of their frustration and disgust with Canonical. Several have said outright that they will not code for Mir for a variety of reasons, not the least of which is the** licensing agreement they'd have to sign with Canonical**.> Mir won't hurt interoperability either, X11 is the common language of all three display servers. Target X11 and your app will run on any Linux distro.Incorrect: the whole reason both Wayland and Mir were created is to get  away from the limitations of X11. Wayland *is* it's own protocol, while [Mir doesn't seem to have a clear definition for how applications are supposed to interact with it yet]("http://blog.cooperteam.net/2013/03/artistic-differences.html").

The applications *may* run, but the choice of desktop environments to run them in will be limited to what Canonical provides. That spells doom to me. Everyone has their own way of doing things and different people have different needs. In the end, they'll probably jump to other distributions to find it. The Ubuntu community will be fractured and it will shrink; support for Ubuntu and derivatives will fade away; Canonical will lose everything it set out to gain, and so on....

---

### Post by quequotion on 2013-06-28
> **kurt18947 said:**
> Not being very knowledgeable in these matters, I wonder if Wayland looks viable on tablets and phones?  Projects intended solely for traditional PCs (desktops/laptops) might not have much standing at Canoncial right now.  Just guessing here.There's already [an implementation]("https://wiki.tizen.org/w/index.php?title=IVI/IVI_Setup&oldid=1037") of Wayland in Tizen (a tablet and phone OS developed under the direction of the Linux Foundation with Samsung, Intel and the Tizen Community contributing). There are a lot of important manufactures behind Tizen.

---

### Post by quequotion on 2013-06-28
> **dino99 said:**
> Stop this train ?

you miss your ticket :confused: , the train is far now and going faster & faster :P
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5NzM](http://www.phoronix.com/scan.php?page=news_item&px=MTM5NzM)Months away, and 13.10 won't be an LTS release. That gives us plenty of time to avert this disaster.

---

### Post by buzzingrobot on 2013-06-28
> **quequotion said:**
> 
The applications *may* run, but the choice of desktop environments to run them in will be limited to what Canonical provides. That spells doom to me. Everyone has their own way of doing things and different people have different needs. In the end, they'll probably jump to other distributions to find it. The Ubuntu community will be fractured and it will shrink; support for Ubuntu and derivatives will fade away; Canonical will lose everything it set out to gain, and so on....

Of course, the DE on Canonical's product will be limited to what Canonical provides.  That's how it's always worked.  They provide Unity on Ubuntu.  Other DE's are available for other initiatives. It doesn't look like that's going to change. 

If someone wants to use an app on Unity that can't run on Mir then, yes, that user has a problem. It is, though, a problem with many, many parallels in the current environment.  Not all apps, and certainly not all versions of apps, run on all systems.

The Ubuntu universe is already split and diversified in uncounted ways. It will stay that way, like the rest of Linux. Some people will build derivatives on Mir, some on Wayland, some on X.  

Canonical, the business, wants to develop Ubuntu as a single platform that can run on all devices. That becomes much more difficult, and problematic, if Canonical lacks control of the core components that need to run on all those devices.  That, presumably, is the reason they're doing Mir, not Wayland.  Some Wayland developers don't agree with that, but it really isn't their call. 

I don't know how all this will impact the Ubuntu "community".  Frankly, I don't know what that really is.

---

### Post by quequotion on 2013-06-28
The only thing that could turn the situation around for me is if NVidia and ATI decide to support Mir in their binary drivers and don't provide support for Wayland.

I'm not convinced that they're interested in developing for either, but obviously the linux community is getting ready to put X11 to rest after so many years so they'll either have to support one, both, or neither and give up on future linux distributions.

Wayland is being developed by many of the same people who developed X11--people who have worked with these binary drivers and who were involved in getting them implemented in X11. There's a better chance that the existing driver code could be adapted to Wayland if developers who've worked on  X11 get involved or at least advise the development. The Mir team doesn't have that kind of experience.

---

### Post by EgoGratis on 2013-06-28
> The only thing that could turn the situation around for me is if NVidia  and ATI decide to support Mir in their binary drivers and don't provide  support for Wayland.

Probably the support will be made through EGL and Wayland can use that and both can use the same FOSS drivers. There is not much of duplication work needed when it comes to drivers.

> I'm not convinced that they're interested in developing for either, but  obviously the linux community is getting ready to put X11 to rest after  so many years so they'll either have to support one, both, or neither  and give up on future linux distributions.

Basically AFAIK supporting one will support both.

> Wayland is being developed by many of the same people who developed  X11--people who have worked with these binary drivers and who were  involved in getting them implemented in X11. There's a better chance  that the existing driver code could be adapted to Wayland if developers  who've worked on  X11 get involved or at least advise the development.  The Mir team doesn't have that kind of experience.                

Basically you can look it like this if Canonical would stick to pure Wayland (protocol) they still might not use Weston (reference compositor) and situation would be similar to what we have now. I think it makes sense to support both now and to be positive about it and hope both will be ready for consumers ASAP.

---

### Post by quequotion on 2013-06-28
> **buzzingrobot said:**
> Of course, the DE on Canonical's product will be limited to what Canonical provides.  That's how it's always worked.  They provide Unity on Ubuntu.  Other DE's are available for other initiatives. It doesn't look like that's going to change. There will be one important difference: Until Ubuntu/Mir, users and developers can take Ubuntu's software suite and configuration and adapt it to their needs. If enough people have preferences in common, they could even repackage the OS with their own choices and re-distribute it under a new name. Developing for Mir requires agreeing to a license form Canonical that makes your code "Mir derivative", even if you are merely adapting something that existed before Mir, and therefore tied to Canonical *legally *(this is one of the reasons KDE and therefore Kubuntu will not implement Mir). In addition, other DEs using X11 or Wayland will become so different from Ubuntu that there won't be much point in maintaining themselves as Ubuntu derivatives. It may even be more practical to re-base back to Debian for distributions that want similarity with Ubuntu but don't intend to use Unity.

I'm concerned about what that means for the future of Ubuntu, as it means lots of users leaving the distribution. Without a userbase, it won't matter what Canonical does with their display server.

> If someone wants to use an app on Unity that can't run on Mir then, yes, that user has a problem. It is, though, a problem with many, many parallels in the current environment.  Not all apps, and certainly not all versions of apps, run on all systems.

The Ubuntu universe is already split and diversified in uncounted ways. It will stay that way, like the rest of Linux. Some people will build derivatives on Mir, some on Wayland, some on X.   I'd like to agree with you, that "diversification" does not necessarily mean "fracturing" and that developing one alternative does not negatively affect another. In most cases that's true, and it's one of the virtues of the greater linux community: whatever it is you want, it's probably out there. 

Unfortunately, it's not quite the situation we have here. Canonical didn't simply develop an alternative to X11 or Wayland. Canonical promised to develop Wayland, contributed relatively little work over a long period of time, then dropped it in favor of their own solution while citing several bogus technical reasons for doing so (later redacted). This happened not long before the "Community" link vanished from the main site (back now, as part of the new navigation bar; explained, but not apologized for, in a blog post that reeked of "oops, we got caught"). Canonical has not been playing well with others lately. Mir isn't diversification, it's domination.

> Canonical, the business, wants to develop Ubuntu as a single platform that can run on all devices. That becomes much more difficult, and problematic, if Canonical lacks control of the core components that need to run on all those devices.  That, presumably, is the reason they're doing Mir, not Wayland.  Some Wayland developers don't agree with that, but it really isn't their call.  I don't see why they have to own the components to make use of them. I also don't see things like Ubuntu TV actually happening, but that's another topic.  If Canonical had increased their contribution to Wayland, they could have had more influence on it and it might have been ready for distribution release earlier. Rather than contribute so something that could help everyone, they've decided to focus on what's best for them and them alone.

> I don't know how all this will impact the Ubuntu "community".  Frankly, I don't know what that really is. Not easy to define indeed. We have a lot of communities coming together to make what I think of as the Ubuntu community. To me this includes all the people who develop software that gets included in Ubuntu (which likely includes people who have never even used Ubuntu) as well as the users of Ubuntu and all of its derivatives (some of which are quite different from the source). That's a lot of people, a *lot* of a lot of people.

In the future, if Canonical sticks with Mir, many of those people will be cut off from the Ubuntu community, which will consist of only those people who develop for QMir (only the qt toolkit has yet been ported to Mir) and those who use the standard Ubuntu distribution.

---

### Post by MadmanRB on 2013-06-28
For me my biggest concern for Mir is who it will effect those who use proprietary cards for gaming, especially steam.
So when Mir is forced on us in 14.04 will it break gaming compatibility and such.
If Canonical is willing to ditch x in 14.04 trhey must hav e some plan in store.
Either thast or people will be using Xubuntu for gaming.

---

### Post by quequotion on 2013-06-28
> **EgoGratis said:**
> Probably the support will be made through EGL and Wayland can use that and both can use the same FOSS drivers. There is not much of duplication work needed when it comes to drivers. Basically AFAIK supporting one will support both. That's good to hear, let's hope you are right!> Basically you can look it like this if Canonical would stick to pure Wayland (protocol) they still might not use Weston (reference compositor) and situation would be similar to what we have now.Weston isn't intended to be used as the main compositor. I wouldn't have any problem with Ubuntu/Wayland+*Theoretical Unity Compositor* (compiz?). This would make it much easier for developers to port Ubuntu derivatives to new versions of Ubuntu, as they'd only need to develop a compositor, and easier for users to try out derivatives that wouldn't be so radically different from Ubuntu. In addition, users and developers alike could enjoy all the advantages of Wayland over X11 (assuming development would reach release stage by that time).> I think it makes sense to support both now and to be positive about it and hope both will be ready for consumers ASAP.I'd like to be positive about it, but I'm not a "consumer". I'm a user. I don't like having software branded, boxed and sold to me, even for free. I also don't like restrictive licensing agreements, like the one required to develop with Mir. It doesn't make sense to me to support a project that's going to restrict its users, especially when there's an alternative that will have as many benefits and doesn't limit its own usefulness.

Although I understand Canonical's need to monetize, I don't want to see Ubuntu, which once stood for responding to the community's needs, become a commercial product focused on only profit. I see Mir as part of a process of closing the walls in around Ubuntu so that it can be boxed up and put on shelves. That's not the OS I'm interested in. I hope I'm not alone.

Of course I could simply go elsewhere, but I *like* Ubuntu; I like its debian package management; I like its licensed binary drivers that make things work (even if they aren't absolutely "free"); I like its flexibility (I run a custom DE made of compiz and pantheon); I've been using it at home exclusively since *Jaunty* (did you know [this bug]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/931929") has not been fixed in all that time?).  I won't be able to use Mir either, since I'm not interested in using Unity and I don't see other DE developers becoming motivated to develop for Mir in light of Canonical's attitude and behaviour. If it were just me it wouldn't make any difference, but I think the  direction Canonical is going with Mir, Unity, and Ubuntu in general is a  self-destructive one that will lead to more users and developers leaving the  distribution.

---

### Post by quequotion on 2013-06-28
> **MadmanRB said:**
> For me my biggest concern for Mir is who it will effect those who use proprietary cards for gaming, especially steam.
So when Mir is forced on us in 14.04 will it break gaming compatibility and such.
If Canonical is willing to ditch x in 14.04 trhey must hav e some plan in store.
Either thast or people will be using Xubuntu for gaming.They hope to secure commitments from NVidia and ATI to support Mir by 14.04, but April 2014 is less than a year away and neither NVidia nor ATI has are going to rewrite their drivers to support an incomplete display server that is only used by one distribution. If the procedure is more trivial than a rewrite, or if Mir somehow becomes desirable to other distributions, there's a possibility that development could get underway in 2014... One also has to consider the history of Canonical's major design change decisions, which have almost consistently been minefields. 

Lubuntu would be better for gaming :) I sometimes use a custom openbox DE for gaming myself.

---

### Post by castrojo on 2013-06-28
> **quequotion said:**
> Although I understand Canonical's need to monetize, I don't want to see Ubuntu, which once stood for responding to the community's needs, become a commercial product focused on only profit. I see Mir as part of a process of closing the walls in around Ubuntu so that it can be boxed up and put on shelves. That's not the OS I'm interested in. I hope I'm not alone.

It's impossible to close off Ubuntu, Mir is GPL3 and everything in main is required to be OSS, it's part of the Ubuntu promise. 


> I won't be able to use Mir either, since I'm not interested in using Unity and I don't see other DE developers becoming motivated to develop for Mir in light of Canonical's attitude and behaviour. If it were just me it wouldn't make any difference, but I think the  direction Canonical is going with Mir, Unity, and Ubuntu in general is a  self-destructive one that will lead to more users and developers leaving the  distribution.

I think you're over-reacting, you'll be able to use whatever window manager you want via XMir; as far as the end user is concerned they probably won't even notice Mir is there.

---

### Post by EgoGratis on 2013-06-28
> Weston isn't intended to be used as the main compositor. I wouldn't have any problem with Ubuntu/Wayland+*Theoretical Unity Compositor*.

Yes but you see Canonical would have to make/code this just like it is doing with Mir.

> I also don't like restrictive licensing agreements, like the one required to develop with Mir.

CLAs are not restrictive for the end user to be honest. You are probably talking about that? CLA does give more power to Canonical to change the licence in the future to something else or to distribute the code with more licences BUT:

-Everything that was already done cant be "undone" in a way it would effect the licence of current Mir (GPL).
-Currently the main source of developers are AFAIK Canonical employees and they code everything under GPL terms...
-Qt toolkit for example uses CLA too...

In the end if it's used only on Ubuntu for Unity it doesn't change much it's just more work for Canonical and that is about it. If it makes Ubuntu more popular it will probably help to boost Wayland too and if it stays GPL software i don't see a reason why others couldn't adopt it in some way. Being Wayland or Mir based  is not that important in my opinion ATM because both relies on the same drivers  and share much more than one would think.

---

### Post by deadflowr on 2013-06-28
> **MadmanRB said:**
> For me my biggest concern for Mir is who it will effect those who use proprietary cards for gaming, especially steam.
So when Mir is forced on us in 14.04 will it break gaming compatibility and such.
If Canonical is willing to ditch x in 14.04 trhey must hav e some plan in store.
Either thast or people will be using Xubuntu for gaming.

Until the proprietary driver makers make their choices on what to build drivers for, anyone using their drivers will run X, and mir will be nothing but dead files on their system.

---

### Post by cariboo on 2013-06-28
@quequotion, I don't know if you've been following the conversation [here]("https://lists.ubuntu.com/archives/ubuntu-devel/2013-June/037401.html"), because most of what you have been posting, is just plain FUD. Check out the video link at the bottom of the email.

---

### Post by EgoGratis on 2013-06-28
> **deadflowr said:**
> Until the proprietary driver makers make their choices on what to build drivers for, anyone using their drivers will run X, and mir will be nothing but dead files on their system.

I am quite sure they will support both over EGL and that this will be done soon.

---

### Post by EgoGratis on 2013-06-28
> **cariboo907 said:**
> @quequotion, I don't know if you've been following the conversation [here]("https://lists.ubuntu.com/archives/ubuntu-devel/2013-June/037401.html"), because most of what you have been posting, is just plain FUD. Check out the video link at the bottom of the email.

I wouldn't call it FUD it's just majority of users don't have needed information yet...

---

### Post by quequotion on 2013-06-28
> **cariboo907 said:**
> @quequotion, I don't know if you've been following the conversation [here]("https://lists.ubuntu.com/archives/ubuntu-devel/2013-June/037401.html"), because most of what you have been posting, is just plain FUD. Check out the video link at the bottom of the email. I don't trust in plans and roadmaps. I've been using GNU/Linux long enough to understand that how things are planned is rather often not how they work out. Whatever Canonical may say or promise they are going to do, I only put stock in what I actually see getting done.

As I said before, Xmir (and Xwayland for that matter) are stop-gap solutions. They aren't going to solve the long-term problem that applications need to be ported to something better than X11. Although it may do a nice job of hiding the incomplete display server that's going to ship with 13.10, this is only delaying a more serious issue that Mir will have to face sooner or later: other DEs are not interested in porting to Mir, but they are already working on Wayland ports.

The more I read that discussion the more I see **Oliver Ries** making lots of excuses and assumptions with very little substance to them. He seems to have the impression that it's perfectly reasonable to run an entire DE on top of a compatibility layer with no definite plan on how to properly integrate that DE and no guarantee of any kind that Mir will ever be supported by proprietary binary drivers, and that it isn't a problem if other distributions never pick up Mir (because he believes they one day will?)

---

### Post by MadmanRB on 2013-06-28
> **deadflowr said:**
> Until the proprietary driver makers make their choices on what to build drivers for, anyone using their drivers will run X, and mir will be nothing but dead files on their system.
Yes but 14.04 is supposed to kill of X fallback, as Unity will be tied into Mir.
This means a lot of borked things for ubuntu and making 14.04 the worst LTS in history, even worse then 12.04.

---

### Post by quequotion on 2013-06-28
> **EgoGratis said:**
> I wouldn't call it FUD it's just majority of users don't have needed information yet...I've done a lot of googling since Canonical announced Mir. There are lots of unanswered questions out there. The fate of the derivatives being one of the most serious. To be honest, I've only ever used KDE once; it's not my thing; but it was [Kubuntu's decision to exclude both Mir and XMir from future releases while proceeding with Wayland/KWin and their rational for doing so]("http://blogs.kde.org/2013/06/26/kubuntu-wont-be-switching-mir-or-xmir") that got my attention and inspired this thread.

---

### Post by EgoGratis on 2013-06-28
I do believe Debian will offer KDE/XFCE/LXDE/... on Xorg or something Wayland based... If XMir is not an option probably K/X/Lubuntu... will be able to use the work from Debian...

If Mir in the future proofs as viable solution i don't see why upstreams couldn't change their mind but for that part Canonical will need to prove it can pool it off. Currently Mir is tightly related/intended for/to use with Unity but this might change in the future.

---

### Post by deadflowr on 2013-06-28
> **MadmanRB said:**
> Yes but 14.04 is supposed to kill of X fallback, as Unity will be tied into Mir.
This means a lot of borked things for ubuntu and making 14.04 the worst LTS in history, even worse then 12.04.

Personally, I reserve judgement on the TT series until development begins.
The great thing about the extended support cycle for LTS now, is that if TT is garbage, then simply skip it and see what comes out of 16.04.

> **EgoGratis said:**
> I do believe Debian will offer KDE/XFCE/LXDE/... on Xorg or something Wayland based... If XMir is not an option probably K/X/Lubuntu... will be able to use the work from Debian...

If Mir in the future proofs as viable solution i don't see why upstreams couldn't change their mind but for that part Canonical will need to prove it can pool it off. Currently Mir is tightly related/intended for/to use with Unity but this might change in the future.

[http://www.phoronix.com/scan.php?page=news_item&px=MTM5NDQ](http://www.phoronix.com/scan.php?page=news_item&px=MTM5NDQ)

---

### Post by MadmanRB on 2013-06-28
> **deadflowr said:**
> Personally, I reserve judgement on the TT series until development begins.
The great thing about the extended support cycle for LTS now, is that if TT is garbage, then simply skip it and see what comes out of 16.04.



[http://www.phoronix.com/scan.php?page=news_item&px=MTM5NDQ](http://www.phoronix.com/scan.php?page=news_item&px=MTM5NDQ)

Yes but you imply that if 14.04 dosnt work go to 12.04, that would be fine if 12.04 was actually a good release...
and its not to be honest.

---

### Post by deadflowr on 2013-06-28
> **MadmanRB said:**
> Yes but you imply that if 14.04 dosnt work go to 12.04, that would be fine if 12.04 was actually a good release...
and its not to be honest.

We'll simply agree to full-on disagree about Precise.
I find it to to be a solid release.
Everything I need to use works, without much tweaking.
So calling it a bad release because of your own experience doesn't make it so.

I've run mint, fedora, opensuse, etc releases, which others have called mana from heaven, and myself considered them utter garbage.
But that doesn't mean any of those are bad, just my experience with them wasn't so great.

---

### Post by EgoGratis on 2013-06-28
> **deadflowr said:**
> [http://www.phoronix.com/scan.php?page=news_item&px=MTM5NDQ](http://www.phoronix.com/scan.php?page=news_item&px=MTM5NDQ)

I don't believe they will settle with XMir for the whole DEs in the long run. They will be maintaining something Wayland based by themselves or to adopt Mir by default. It's too early to say which option will prevail (if any).

---

### Post by buzzingrobot on 2013-06-28
> **quequotion said:**
> There will be one important difference...
 Developing for Mir requires agreeing to a license form Canonical that makes your code "Mir derivative"... DEs using X11 or Wayland will become so different from Ubuntu that there won't be much point in maintaining themselves as Ubuntu derivatives. It may even be more practical to re-base back to Debian for distributions that want similarity with Ubuntu but don't intend to use Unity. 

Quite true. Although I think rebasing on Debian wouldn't be all that simple. They would need the resources to massage Testing or Unstable to maintain the currency that Ubuntu users expect.

> I'm concerned about what that means for the future of Ubuntu, as it means lots of users leaving the distribution. Without a userbase, it won't matter what Canonical does with their display server.

I suspect people will leave or stay with Ubuntu and Unity depending on what's on offer, not depending on the display driver. 

It's my impression that, since Ubuntu is still costing Canonical money, not producing a profit, the move to put Unity on other devices comes in the hope that it can generate some profit.  I certainly don't expect Ubuntu-for-desktops to ever make any money, and I doubt Canonical does, either. 

So, if things go well,  Canonical will be able to fund continued Ubuntu development out of the returns from the device market.  If not, I would expect Ubuntu to be killed off at some point, at least as a project receiving financial support from Canonical or Shuttleworth.

>  Mir isn't diversification, it's domination. 

How can it be "domination" when X remains *the* major player and everyone else seems to be on the Wayland bandwagon?  The assertion that Canonical is going its own way doesn't synch with the assertion that it's going for "domination".

> ...I don't see why they have to own the components to make use of them... If Canonical had increased their contribution to Wayland, they could have had more influence on it and it might have been ready for distribution release earlier. Rather than contribute so something that could help everyone, they've decided to focus on what's best for them and them alone.


I think there's long been hard feelings and bad blood between Shuttleworth, et al, and parts of the FOSS developer community.  The reasons may or may not be justifiable, but that's not material. He doesn't trust them; they don't trust him. Shuttleworth certainly hasn't bought into the cultural and ideological constraints that many in FOSS seem to accept.

One reason for not relying on contributions from people who do not work for you is if you have contract commitments to deliver products according to a schedule. Presumably, Canonical will need to do that to play in the device market. They can't depend on needed contributions coming from outsiders who do not -- can not -- work to a schedule.

> Not easy to define indeed. We have a lot of communities coming together to make what I think of as the Ubuntu community. To me this includes all the people who develop software that gets included in Ubuntu (which likely includes people who have never even used Ubuntu) as well as the users of Ubuntu and all of its derivatives...

I see FOSS as essentially a community by and for developers.  Users reap benefits, but I have a very difficult time considering so many disparate users as any kind of a coherent community.  We see constant chatter about what the community wants or deserves, etc., etc. Perhaps I'm too cynical, but I have no idea how we are supposed to determine what that "community" wants.  There's no accurate way to encompass who is in the "community", much less if it's come to a consensus about something. (I've been an active Linux user since the 1990's and no one has ever presented me with an organized, formal way of expressing my wishes about it.)  What happens is that someone reads the tea leaves and announces that consensus.

---

### Post by deadflowr on 2013-06-28
> **EgoGratis said:**
> I don't believe they will settle with XMir for the whole DEs in the long run. They will be maintaining something Wayland based by themselves or to adopt Mir by default. It's too early to say which option will prevail (if any).

Whether the various flavors choose to run xmir or not, doesn't matter to me.
I simply wanted to point to the fact that they've tested other DE's to see the viabilty of xmir.

---

### Post by EgoGratis on 2013-06-28
> Whether the various flavors choose to run xmir or not, doesn't matter to me.

Yes i think the OP is more concerned in this. Or at least i was under such impression. And this is why we are here talking about this (who will chose what in the future).

---

### Post by deadflowr on 2013-06-28
> **EgoGratis said:**
> Yes i think the OP is more concerned in this. Or at least i was under such impression. And this is why we are here talking about this (who will chose what in the future).

What we know is that mir is the direction Ubuntu is taking.
What the others do should be asked of the others.

---

### Post by monkeybrain2012 on 2013-06-28
> **MadmanRB said:**
> For me my biggest concern for Mir is who it will effect those who use proprietary cards for gaming, especially steam.
So when Mir is forced on us in 14.04 will it break gaming compatibility and such.
If Canonical is willing to ditch x in 14.04 trhey must hav e some plan in store.
Either thast or people will be using Xubuntu for gaming.

Actually it doesn't look too good performance wise even for the free drivers

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_xmir_benchmark&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_xmir_benchmark&num=1)

But then it is still early, hope that will get fixed by the time of 13.10's freeze.

---

### Post by quequotion on 2013-06-28
> **EgoGratis said:**
> If Mir in the future proofs as viable solution i don't see why upstreams couldn't change their mind but for that part Canonical will need to prove it can pool it off. Currently Mir is tightly related/intended for/to use with Unity but this might change in the future. It's not that they couldn't change their minds, but I doubt they will ever have the motivation to do so. Mir comes off as a bit of an insult to people who have been working on Wayland ports of their Ubuntu derivatives. It's only for use in Ubuntu and only for use with Unity. Canonical is not interested in adapting Mir to other DEs either. Neither side is giving the other any chance, but Canonical's point of view strikes me as particularly arrogant.

Allow me to summarize and paraphrase the debate, as you may read in some of the articles linked from this thread:

**Canonical**: "Yeah, we were going to go with Wayland, but we had a [s]better[/s], [s]or somewhat better[/s], or actually neither better nor worse just different, idea--although we don't really have the details down just yet--so we're going ahead and doing it our way. If you'd like to forget about how much time you've invested in Wayland and join us you may, but we can't and won't do anything to help you, maybe not ever."
[B]
Derivative devs[/B]: "Eh? What? Why? So, what are we supposed to do now? Upstream devs, what do we do about Mir?"
[B]
Upstream DE devs[/B]: "What's MIr? Oh, Canonical's pushing a new display server in Ubuntu... with a licensing agreement... interesting... We develop for twenty different distributions that are going with Wayland, so we're going to stick with that."
[B]
Derivative devs[/B]: "Well, Wayland it is then. um.... but what do we do about Mir in the future?"
[B]
Upstream DE devs[/B]: "..."[B]

Canonical[/B]: "Anything will run on XMir!"
[B]
Derivative devs[/B]: "But we're never going to port to Mir, so why bother with XMir?"
[B]
Canonical[/B]: "It'll be fine, don't worry so much."
[B]
Derivative devs[/B]: "..."


> **buzzingrobot said:**
> Quite true. Although I think rebasing on Debian wouldn't be all that simple. They would need the resources to massage Testing or Unstable to maintain the currency that Ubuntu users expect.You've kind of misinterpreted me here. I am not suggesting that they should re-base on Debian, I was pointing out the unfortunate reality that they *may be forced to re-base on Debian*.> I suspect people will leave or stay with Ubuntu and Unity depending on what's on offer, not depending on the display driver.What Ubuntu will be offering in the future (13.10) is an incomplete, broken display server with no support for proprietary binary drivers.> How can it be "domination" when X remains *the* major player and everyone else seems to be on the Wayland bandwagon?  The assertion that Canonical is going its own way doesn't synch with the assertion that it's going for "domination".Domination of their own userbase. Forcing users to choose standard Ubuntu or *go away*.> One reason for not relying on contributions from people who do not work for you is if you have contract commitments to deliver products according to a schedule. Presumably, Canonical will need to do that to play in the device market. They can't depend on needed contributions coming from outsiders who do not -- can not -- work to a schedule. This is the most valid argument I have seen toward the "in-house development uber alles" policy Canonical relies on more and more. This makes sense. I wish this mess didn't have to spill over on to my home desktop.*> I see FOSS as essentially a community by and for developers.  Users reap benefits, but I have a very difficult time considering so many disparate users as any kind of a coherent community.  We see constant chatter about what the community wants or deserves, etc., etc. Perhaps I'm too cynical, but I have no idea how we are supposed to determine what that "community" wants.  There's no accurate way to encompass who is in the "community", much less if it's come to a consensus about something. (I've been an active Linux user since the 1990's and no one has ever presented me with an organized, formal way of expressing my wishes about it.)  What happens is that someone reads the tea leaves and announces that consensus.I am actually very happy to be discussing this particular topic. It needs it's own thread; or maybe it's own subform: "FOSS Community" because you're right in most ways, but I think we also need to recognize that as linux has become more user-friendly and more viable as a home-pc OS there are a great many non-developers who are permanent members of the community now. I think it's just as important to recognize their needs as the needs of the people who make the software if FOSS is to really give the big corporate players a run for their money, but judging those needs is hard. FOSS is obviously not a democracy, but it isn't complete anarchy either. The best way I can describe the governance across the entire FOSS spectrum is "meritocracy" wherein people and projects of significant value are awarded significant influence. Like all other political systems, it is vulnerable to manipulation and corruption, thus needs to be monitored and managed carefully.> **EgoGratis said:**
> Yes i think the OP is more concerned in this. Or at least i was under such impression. And this is why we are here talking about this (who will chose what in the future).My name is quequotion. OP is someone on 4chan. qq would do. My concern is not "who will choose what", but "what choices will be available?" and "will users and developers be able to make a choice at all?".

*Of course, there's always the option to never upgrade.

---

### Post by buzzingrobot on 2013-06-28
> **quequotion said:**
>  Mir comes off as a bit of an insult to people who have been working on Wayland ports of their Ubuntu derivatives. 

It would be nice if ego didn't interfere with professionalism. A debate about the technical merits of Mir versus Wayland is legitimate. Trashing one because, well, Not Invented Here, isn't.

> What Ubuntu will be offering in the future is an incomplete, broken display server with no support for proprietary binary drivers. 

Too early too tell.

> Forcing users to choose standard Ubuntu or *go away*. 

Of course they can, It's their product. Just because a zillion-and-one Ubuntu derivatives exists today does not mean Canonical has a reason to go out of its way to ensure they can continue under Mir if Canonical sees that as not being in its best interests. All those derivatives are *competition* for Unity.

> This is the most valid argument I have seen toward the "in-house development uber alles" policy Canonical relies on more and more. This makes sense.
 
Fundamental tensions exist between the culture and ideology of FOSS as it has developed, and efforts to make money from Linux. No one has ever sustained a business selling Linux.  Red Hat is quite successful selling support contracts for RHEL, but it got out of the shinkwrapped Linux retail market years ago.  The relationship of Red Hat to Fedora is not the same as that of Canonical to Ubuntu.  But, I think if Red Hat decided to go into the device business as Canonical has, Fedora would face similar conflicts.

> I think it's just as important to recognize their needs as the needs of the people who make the software if FOSS is to really give the big corporate players a run for their money...

Now, that's something I no longer have an interest in.  I never really did, I guess.  The first OS I was exposed to was Unix. I began using Linux (Slackware, way back when) because it was, essentially, Unix.  When I used DOS or Windows, I typically used Unix emulators that gave me a shell and the GNU tool set.

If my choices were between a FOSS-ified Windows and a closed proprietary Microsoft Unix for $300, I'd buy the latter.

> ...governance across the entire FOSS spectrum is "meritocracy" wherein people and projects of significant value are awarded significant influence.

I have problems with that.  For one, it assumes universally shared values about what is or is not of "significant value". It gets back to the "who decides?" issue.  Who decides what's of value? Who says they can make those decisions for everyone else?

I much prefer an environment where developers are free to make whatever it is they want to make, then release it and see what happens, taking their lumps as necessary, over all this angst about community and culture and who's good and who's bad.  If Canonical thinks Mir is better than Wayland, then the proof is in the pudding.  I'll judge for myself when the pudding is done. Ditto for the Wayland supporters.

---

### Post by quequotion on 2013-06-28
> **buzzingrobot said:**
> It would be nice if ego didn't interfere with professionalism. A debate about the technical merits of Mir versus Wayland is legitimate. Trashing one because, well, Not Invented Here, isn't.And, as duely noted elsewhere in this thread and in this forum, [that is exactly what happened]("http://vignatti.com/2013/03/05/ui-customization-on-wayland/") (see "A footnote about Canonical's Mir").

> I have problems with that.  For one, it assumes universally shared values about what is or is not of "significant value". It gets back to the "who decides?" issue.  Who decides what's of value? Who says they can make those decisions for everyone else?Valid concerns. The values may not be universally shared or even recognized, and the precise quantization of "significant" is somewhat impossible. Nonetheless, these decisions get made. Linus Torvalds is the benevolent dictator of the kernel because he started it I suppose, X11 has been in use for over a decade because it hasn't been trumped yet, people follow the fredesktop.org specifications because they exist, etc. etc.> I much prefer an environment where developers are free to make whatever it is they want to make, then release it and see what happens, taking their lumps as necessary, over all this angst about community and culture and who's good and who's bad.  If Canonical thinks Mir is better than Wayland, then the proof is in the pudding.  I'll judge for myself when the pudding is done. Ditto for the Wayland supporters.If it worked out that cleanly I think it would be a better environment, and there wouldn't be nearly as much angst to go around. Unfortunately I think there will be far to many lumps taken by users and developers who don't deserve them in this situation.

---

### Post by EgoGratis on 2013-06-28
> It's not that they couldn't change their minds, but I doubt they will  ever have the motivation to do so. Mir comes off as a bit of an insult  to people who have been working on Wayland ports of their Ubuntu  derivatives. It's only for use in Ubuntu and only for use with Unity.  Canonical is not interested in adapting Mir to other DEs either. Neither  side is giving the other any chance, but Canonical's point of view  strikes me as particularly arrogant.

They will/would have the motivation to do so if Canonical will/would give them that motivation. It's too early to say ATM what is the reach of Mir but if it would be used on 200 millions of devices in next few years and would be GPL licensed there would probably not be much reason not to use it... upstreams probably will/would change their minds. It's not true Canonical is not interested in other DEs adopting Mir currently other DEs are not interested in adopting Mir mainly because currently Mir is one purpose/distribution solution and that is about it and above all it's not finished yet to be used for this single purpose/distribution. About being arrogant i don't know about that they went their own way and that is about it for now.

> My name is quequotion. OP is someone on 4chan. qq would do.

AFAIK OP is quite common term describing original poster.

---

### Post by EgoGratis on 2013-06-28
> And, as duely noted elsewhere in this thread and in this forum, [that is exactly what happened]("http://vignatti.com/2013/03/05/ui-customization-on-wayland/") (see "A footnote about Canonical's Mir").

This is old and this was cleared up a while back.

> Valid concerns. The values may not be universally shared or even  recognized, and the precise quantization of "significant" is somewhat  impossible. Nonetheless, these decisions get made. Linus Torvalds is the  benevolent dictator of the kernel because he started it I suppose, X11  has been in use for over a decade because it hasn't been trumped yet,  people follow the fredesktop.org specifications because they exist, etc.  etc.

Yes and we are using Ubuntu for quite some years now and Mir is FOSS in the end!

---

### Post by castrojo on 2013-06-28
> **MadmanRB said:**
> Yes but 14.04 is supposed to kill of X fallback, as Unity will be tied into Mir.
This means a lot of borked things for ubuntu and making 14.04 the worst LTS in history, even worse then 12.04.

XMir will ship in 14.04. Window Managers/Desktops that don't support Mir natively will just use XMir and everything works.

---

### Post by EgoGratis on 2013-06-28
> XMir will ship in 14.04. Window Managers/Desktops that don't support Mir natively will just use XMir and everything works.

That plus as i do imagine for example KDE running on Xorg/Wayland will be possible regardless of the fact if it is officially supported/endorsed? Will wait and see.

---

### Post by quequotion on 2013-06-28
> **castrojo said:**
> XMir will ship in 14.04. Window Managers/Desktops that don't support Mir natively will just use XMir and everything works.
1. At how much performance cost? (We need empirical data, not theory; I know of only one developer on one computer that has any so far.)
2. Are you really sure everything works? (This is a theory that has been tested perhaps twice by one person on one computer.)
3. When/How will proprietary drivers get support? (The FOSS drivers aren't enough for most people with a discrete card.)
4. Is this a plan to gradually convince people to port to Mir? (Mir will have to prove itself to be equal to or better than Wayland, and Canonical will have to do some very creative marketing to win back the devs of other DEs).

---

### Post by EgoGratis on 2013-06-28
I bet you can't give 100% answers if i ask you the same about Wayland or better yet compositor talking Wayland. In the end i do imagine you will be able to test both by yourself and decide. Unity 8 probably won't support X11 anymore and you will not be able to use it on XWayland for example and this is the only limitation i see ATM.

P.S. But first we have to get there.

---

### Post by castrojo on 2013-06-28
> 1. At how much performance cost? (We need empirical data, not theory; I know of only one developer on one computer that has any so far.)

Within 10% so far, without optimization: [http://www.olli-ries.com/first-mir-benchmarks/](http://www.olli-ries.com/first-mir-benchmarks/)

> 2. Are you really sure everything works? (This is a theory that has been tested perhaps twice by one person on one computer.)

It'll land in Saucy soon, so I would say that it probably works. And if things don't work, we'll fix them.

> 3. When/How will proprietary drivers get support? (The FOSS drivers aren't enough for most people with a discrete card.)

Canonical have stated multiple times that they are talking to AMD/Nvidia for drivers, so I assume that discussions are happening. 

> 4. Is this a plan to gradually convince people to port to Mir? (Mir will have to prove itself to be equal to or better than Wayland, and Canonical will have to do some very creative marketing to win back the devs of other DEs).

Given the nature of Free Software I expect people will enable these desktops to work on Mir in the future.

---

### Post by grahammechanical on 2013-06-28
> It'll land in Saucy soon,

I am running Saucy on Xmir right now. And I plan to put in an install of all the flavours and add Xmir just to prove that it can be done. The only issue I see is that there is a slight delay in typing  response and moving the insertion point in documents.

From information recently released if a video card cannot support Xmir then an installation will use Xserver as fallback. So, all users are catered for.

Regards.

---

### Post by quequotion on 2013-06-28
> **castrojo said:**
> Within 10% so far, without optimization: [http://www.olli-ries.com/first-mir-benchmarks/](http://www.olli-ries.com/first-mir-benchmarks/)Interesting. These tests compare Unity/X and Unity/XMir. I'm surprised to see Unity/Mir left out as his tests are often so thorough. Is real Unity/Mir desktop functioning yet? I really wanted to know about the performance hit for non-Unity DEs with XMir however. Perhaps grahammechanical will have those statistics for us later. > It'll land in Saucy soon, so I would say that it probably works. And if things don't work, we'll fix them.Be careful what you assume. I've been tragically disappointed by show-stopping, *if-I-weren't-a-geek-I'd-just-give-up-on-linux-forever*, bugs on nearly every release date. In no particular order, the top three are: broken boot sequence, broken display system, or broken device drivers; always resulting in an *unusable* PC, and often leaving the system in an *undiagnosable* state. I usually end up wiping my upgraded installation and trying a fresh install, *only to get the same bugs*. When I finally do track down what was wrong, they have always been* known bugs* that were not listed in the release notes, every time. Canonical has made it clear that they're going to ship 13.10 with an incomplete Mir. I think they should make it very clear that *this release is for alpha testing* and not to be used on anyone's everyday computer because it's going to wreak havoc on users who will be in over their heads in some very unfamiliar waters; I wouldn't even publish the release on the main site.> Canonical have stated multiple times that they are talking to AMD/Nvidia for drivers, so I assume that discussions are happening. Indeed they have. I'd like to hear something from the manufacturers as well, but there's not been as much as whisper. The closest I could find was this inappropriately titled [Phoronix article ]("http://www.phoronix.com/scan.php?page=news_item&px=MTM5MjE")which is pure conjecture and likely to start rumours. If the manufacturers are indeed involved, perhaps they have reasons for keeping quiet.> Given the nature of Free Software I expect people will enable these desktops to work on Mir in the future.It won't be easy, if possible at all. Canonical's sudden flop on Wayland has garnered resentment from the very people who would be responsible for making those ports happen--they aren't going to be shaking hands with Mr. Shuttleworth anytime soon.

---

### Post by cariboo on 2013-06-29
> **EgoGratis said:**
> I wouldn't call it FUD it's just majority of users don't have needed information yet...

To me this is just more of the same thing we saw, when Unity first became the default DE. I'm personally excited by this development, and I'm in the process of setting up another Saucy partition, in order to try out the ppas.

---

### Post by quequotion on 2013-06-29
If negotiations between Canonical and AMD/Nvidia resulted in binary blobs that support both Mir and Wayland this would be a big plus. At least I'd be able to have a modern display server with my DE of choice and no compatibility layer sapping the performance. There's a rumour that Nvidia was working on a unified EGL driver that could support both, but no hard evidence as far as I've seen.

If they result in binary drivers that support only Mir and not Wayland, I don't think I'll be the only one even more upset about the situation. What I've read suggests that technologically, this would be a rediculous thing to do and that supporting one almost necessitates supporting both. It seems that it's unclear to what degree they will require different driver implementations, if any. Neither company is strongly motivated to support linux, and particularly to support three different display servers. I fear that if Mir support comes to the binary blobs without Wayland support, then there never will be Wayland support.

---

### Post by quequotion on 2013-06-29
> **cariboo907 said:**
> To me this is just more of the same thing we saw, when Unity first became the default DE. I'm personally excited by this development, and I'm in the process of setting up another Saucy partition, in order to try out the ppas. You may even recall me in particular being rather upset, and rather vocal in opposition to Unity. In the end, I found another desktop to use ([actually I pieced two together]("http://ubuntuforums.org/showthread.php?t=2124220")). I still don't like Unity, although it finally caught up to its hype *around version 5*. If Ubuntu/Mir doesn't provide a way for me to run the DE of my choice without a compatibility layer; I'll find another OS to use. I don't expect the first versions of Mir to be much more impressive than the first versions of Unity, particularly because Canonical is hyping it *exactly the same way*.

I'm not opposed to Mir's development out of fear or uncertainty or doubt, I am opposed to Mir's development from *bitter* and *disappointing* experience.

In fact, I'm probably not going to upgrade until the next LTS. Hopefully things will have changed and improved by then. I still have hope that Canonical will make room for Wayland when it's ready. I have no intention of using Mir unless it can prove itself better or equal to Wayland in design and functionality. Wayland still has the upper hand in being more complete and having more support.

---

### Post by MadmanRB on 2013-06-29
Well consider Mir is still new, but who knows what it can bring.
If Mir is a failure then it will fail, as long as fallbacks exist I think we will be fine.

---

### Post by monkeybrain2012 on 2013-06-29
I am not sure what is an "unsupported" card. I think all cards are supported just not all drivers. Does it mean that if you have anything other than an Intel card it will fall back to X in 13.10, assuming you will use the proprietary driver (even though you may not)?

It seems reckless to put xmir on 13.10  and simultaneously cutting short support of 13.04. So without speculating on what 14.04 will be like some people will be left with a broken system for 3 months unless downgrading to 12.04 or 12.10. It is not a pleasant prospect (many bug fixes in Unity 7 have not been backported to Precise and I doubt that they ever will be)

---

### Post by monkeybrain2012 on 2013-06-29
> **cariboo907 said:**
> To me this is just more of the same thing we saw, when Unity first became the default DE. I'm personally excited by this development, and I'm in the process of setting up another Saucy partition, in order to try out the ppas.

Not sure that I would agree. DE is mostly a cosmetic thing and it is rather trivial to swap one out for another, this time we are talking about core engineering of the system.

I will be excited to try it out too, but "trying it out" means that you have other options if it doesn't work and with 13.04 eol there is no option unless you downgrade to 12.04 or 12.10, or quit Ubuntu. Canonical is not going to get more testers (not enthusiastic ones anyway) by trying to force a (very)immature technology on a release and removing the option of not upgrading.

---

### Post by buzzingrobot on 2013-06-29
> **monkeybrain2012 said:**
> I am not sure what is an "unsupported" card... seems reckless to put xmir on 13.10...


As I read things, the fallback is to XMir and then to X.  That would seem to cover things. Now, how this is implemented is important, but I'm not sure all the "Everything Will Break!" predictions in this thread will really happen.

---

### Post by EgoGratis on 2013-06-29
> Is real  Unity/Mir desktop functioning yet?

No. On ARM devices maybe in a way but the test ATM would probably not tell us much regarding classical desktop DEs used on desktop PC.


> If negotiations between Canonical and AMD/Nvidia resulted in binary  blobs that support both Mir and Wayland this would be a big plus.

[EGL]("http://en.wikipedia.org/wiki/EGL_%28OpenGL%29").

> Neither company is strongly motivated to support linux

I don't agree because today i can buy most of the cards from this 2 companies and expect them to work under Linux. This does show both companies have quite strong motivation to support Linux given the fact what market share Linux has on the desktop.

> I have no intention of using Mir unless it can prove itself better or equal to Wayland in design and functionality.

First both or at least one of them should beat Xorg and we are not there yet.

> To me this is just more of the same thing we saw, when Unity first became the default DE.

Unity didn't replace GNOME 2 it replaced GnomeShell and not all GNOME 2 users are happy with GnomeShell either. 

> I really wanted to know about the  performance hit for non-Unity DEs with XMir however. Perhaps  grahammechanical will have those statistics for us later.

Unity 7 should probably not behave that much differently (running on XMir + Mir compared to running on just Xorg) compared to other X11 DEs.

---

### Post by tartalo on 2013-06-29
> **EgoGratis said:**
> Yes but you see Canonical would have to make/code this [wayland compositor] just like it is doing with Mir.

But they would have developed something compatible with the protocol everyone else is using, no one would be angry with Canonical, quite the opposite, and their work would be truly reusable.

---

### Post by EgoGratis on 2013-06-29
Yes maybe other would use it or maybe not. We will see soon how much DEs will or will not use Weston for example and will do things differently in the future. There is no guarantee anybody else would use solution Canonical would made and it could still be used just for Ubuntu/Unity and be compatible with Wayland protocol. K/X/Lubuntu... could still do it differently and they probably would do it differently. About XMir honestly i do believe K/X/Lubuntu... will not settle with this and will do things differently and i doubt everybody would just jump on solution coded for Unity if it would be Wayland compatible i think the situation would be quite the same as we have it now.

And who knows after a while best approaches could prevail and majority to settle on them and we would end up with something we can call suitable to be Xorg successor and it might not be just one solution. We don't have that yet regardless of what Canonical (did) decide and Mir and Wayland based solutions do and will in the end share and have much in common for starters GPU drivers!

---

### Post by MadmanRB on 2013-06-29
Weston?
You mean Weyland

---

### Post by 3rdalbum on 2013-06-30
> **MadmanRB said:**
> Weston?
You mean Weyland

Wayland is the protocol.

Weston is the server.

Wayland is to Weston, like X11 is to Xorg.

Actually one of the other worrying things about Weston is that it's only a "reference implementation". As long as Weston works, no matter how slow or few-featured or difficult-to-set-up it is, that's all the developers really need to do because it's only intended as a "reference" for other developers to actually implement a Wayland server.

AFAIK Weston and one man's fork of it are the only Wayland servers available. In other words, if Weston is not meant as an end-user product, and there are no end-user Wayland display servers currently, how much longer will we have to wait for one to actually get developed?

Mir is at least intended as the end-user server, not just "we'll leave it to someone else to write that".

---

### Post by tartalo on 2013-06-30
> **3rdalbum said:**
> Wayland is the protocol. Weston is the server.
(...)
Mir is at least intended as the end-user server, not just "we'll leave it to someone else to write that".

Sir Tim Berners-Lee didn't write the browser you are using, but a reference implementation. His merit isn't writing a couple of programs, but defining the standard that allows this conversation to happen independently of our software choices.

---

### Post by EgoGratis on 2013-06-30
> AFAIK Weston and one man's fork of it are the only Wayland servers  available. In other words, if Weston is not meant as an end-user  product, and there are no end-user Wayland display servers currently,  how much longer will we have to wait for one to actually get developed?

Probably in the end every DE will implement it's own solution to be Wayland/Mir compatible.

---

### Post by 3rdalbum on 2013-06-30
> **tartalo said:**
> Sir Tim Berners-Lee didn't write the browser you are using, but a reference implementation. His merit isn't writing a couple of programs, but defining the standard that allows this conversation to happen independently of our software choices.

That's fine, but when comparing the progress and "readiness" of Mir versus Wayland, you have to remember that Weston is not the end-user product. Mir is. People saying "They should just use Wayland" are forgetting that there is no end-user display server for Wayland.

Plus of course, Wayland/Weston's developers are much the same people as who have worked on Xorg in recent years. The most experienced people in developing a display server for Linux, are not actually writing one to ship with any distros. Who, then, do they expect to write the real end-user server?

---

### Post by EgoGratis on 2013-06-30
> The most experienced people in developing a display server for Linux,  are not actually writing one to ship with any distros. Who, then, do  they expect to write the real end-user server

They expect other to use Weston or to implement support for the protocol by themselve.

---

### Post by lykwydchykyn on 2013-06-30
> **3rdalbum said:**
> 
Actually one of the other worrying things about Weston is that it's only a "reference implementation". As long as Weston works, no matter how slow or few-featured or difficult-to-set-up it is, that's all the developers really need to do because it's only intended as a "reference" for other developers to actually implement a Wayland server.

AFAIK Weston and one man's fork of it are the only Wayland servers available. In other words, if Weston is not meant as an end-user product, and there are no end-user Wayland display servers currently, how much longer will we have to wait for one to actually get developed?


"Reference implementation" does not mean it can't be suitable for the end user; several popular programs in regular use are reference implementation -- for example, Bind, ISC dhcp server, and... oh yeah, **Xorg**.  Look'em up if you don't believe me.

Rest assured that whatever ends up shipping with distros will be written and edited to perform well, regardless of whether it's a reference implementation or not.

---

### Post by quequotion on 2013-07-01
> **monkeybrain2012 said:**
> Not sure that I would agree. DE is  mostly a cosmetic thing and it is rather trivial to swap one out for  another, this time we are talking about core engineering of the system.

I will be excited to try it out too, but "trying it out" means that you  have other options if it doesn't work and with 13.04 eol there is no  option unless you downgrade to 12.04 or 12.10, or quit Ubuntu. Canonical  is not going to get more testers (not enthusiastic ones anyway) by  trying to force a (very)immature technology on a release and removing  the option of not upgrading.A very important point indeed. This  is not going to be as much fun as having a go at it and then being able  to say "Well, it's not my thing" and installing something else. If it  works that will be great, but if it doesn't Canonical is going to  continue pushing it out with every new release regardless and they  aren't going to include alternatives (fallbacks like XMir and X11 are  not alternatives, they're sub-optimal stop-gap  solutions).> **EgoGratis said:**
> No. On ARM devices maybe in a way  but the test ATM would probably not tell us much regarding classical  desktop DEs used on desktop PC.So this is the state of Mir: it  doesn't work with the DE it's being designed for. Not yet. *Not at all*. Will it be ready for 13.10? *Probably not*,  but it's shipping out anyway as a testbed for 14.04. Considering the  size and experience of the team developing Mir, will there be a  full-fledged Unity/Mir desktop by the time 14.04 comes out? Anyone good  with crystal balls?> [EGL]("http://en.wikipedia.org/wiki/EGL_%28OpenGL%29").I've  been reading up on this myself. As the underlying technology behind  both, it suggests that a driver that supports either should support  both. There are technical differences between Wayland and Mir that I  don't fully comprehend however, and I'm not *certain* that EGL  support alone dictates support for both display servers. I hope it does,  I really really hope it does.> I don't agree because today i can  buy most of the cards from this 2 companies and expect them to work  under Linux. This does show both companies have quite strong motivation  to support Linux given the fact what market share Linux has on the  desktop.[There's some history you should be aware of]("http://en.wikipedia.org/wiki/Graphics_hardware_and_FOSS").  Not many years ago, ATI rebased their binary driver and dropped legacy  support for a number of cards. Some of those cards had been on the  market for less than a year--my Radeon X1550 among them. They did not  provide a separate legacy driver and the previously released driver was  incompatible with upcoming releases of Xorg. It became impossible for  many users, including myself, to upgrade Xorg and therefore to upgrade  our distributions without switching to the FOSS driver. The state of the  FOSS driver at the time was atrocious. *I tried*, for about a  week, but my PC became unusable for even the most basic purposes. On the  other hand ATI has been kind enough to release a lot of programming  specs and their developers have even made contributions to FOSS. The ATI  FOSS driver is in a much better state lately. Nvidia strictly *does not*  contribute to FOSS nor do they release programming specs for FOSS  developers to work with. A few months back Linus Torvalds exploded on  Nvidia in frustration over their lack of dedication to linux. The FOSS  drivers for nvidia are pure reverse engineering. On the other hand, they  are dedicated to providing binary drivers to support both modern and  legacy cards and they have been quick to provide linux users with  functionality and performance on-par with Windows (we even got FXAA *first*).  I've tried the FOSS drivers, which aren't too bad, but I prefer the  binary for obvious reasons. Both companies release a binary driver for  linux, but in some ways aren't taking FOSS or FOSS OS users seriously eg  are not taking linux seriously, but this is changing. Nvidia replied to  Torvalds that they are quite dedicated to supporting linux through  their proprietary, closed-source drivers and ATI continues to support  FOSS development.> **tartalo said:**
> But they would have developed  something compatible with the protocol everyone else is using, no one  would be angry with Canonical, quite the opposite, and their work would  be truly reusable.Bullseye.> **3rdalbum said:**
> Wayland is  the protocol.

Weston is the server.

Wayland is to Weston, like X11 is to Xorg.I'm not sure this  analogy works out. The underlying technology is not the same, which was  the purpose of developing Wayland. Wayland is both the protocol and the  server. Weston is a compositor, but not quite like X compositors  (compiz, compton, etc).> AFAIK Weston and one man's fork of it are  the only Wayland servers available.KWin and Mutter compositors  are in development. Wayland/KWin will bring Wayland support to KDE and  Wayland/Mutter could support a lot of different desktops (any GNOME  derivatives like MATE, Cinnamon, Pantheon, Gnome Classic,  etc).> Mir is at least intended as the end-user server, not just  "we'll leave it to someone else to write that".Not quite. Mir  isn't something end-users should even be aware of. Unity is intended be  the DE/compositor(?) running on top of Mir, and it isn't intended to be a  reference implementation. Canonical is going to develop a full product,  which will be convenient for users if it comes together, but cumbersome  for developers to port to other desktops. Weston serves to provide  thorough examples and documentation for working with Wayland rather than  a traditional desktop. There will be no such help available to  developers who might want to develop DEs based on  Mir.> **3rdalbum said:**
> That's fine, but when comparing the  progress and "readiness" of Mir versus Wayland, you have to remember  that Weston is not the end-user product. Mir is. People saying "They  should just use Wayland" are forgetting that there is no end-user  display server for Wayland.There's no end-user compositor.  Wayland is the display server; it's more or less ready--especially  compared to Mir. Currently KDE, GNOME, Tizen, and several other projects  are working on compositor implementations for end-users.> Plus of  course, Wayland/Weston's developers are much the same people as who have  worked on Xorg in recent years. The most experienced people in  developing a display server for Linux, are not actually writing one to  ship with any distros. Who, then, do they expect to write the real  end-user server?Everyone else, and they'll probably be  contributing as well. At least, they've provided Weston to serve as a  Wayland compositor handbook that will help other developers create their  own. Mir does not and likely will not have such useful examples to work  with.

---

### Post by rrich1974 on 2013-07-01
[http://news.softpedia.com/news/Nvidia-and-AMD-to-Provide-Support-for-Mir-Says-Canonical-363955.shtml](http://news.softpedia.com/news/Nvidia-and-AMD-to-Provide-Support-for-Mir-Says-Canonical-363955.shtml)

it is a bit old news, but it worths mentioning. that is due to the fact that ubuntu seems to have about half of the market share in the linux users.

---

### Post by cariboo on 2013-07-01
I've got Unity running on Mir on my system, I'd ask the op, why he hasn't set up an extra partition to try it out himself, instead of posting second hand information. I've tried video from all the providers, and done some photo editing, and aside from the two cursors, and a bit of a delay during keyboard input, for pre-alpha software, it works pretty well.

I'd also like to ask the op what his experiences with a [Rebecca Black ]("http://ubuntuforums.org/showthread.php?t=1906762") are, as it is the only working implementation of wayland, that is available from any source. 

He himself admits he doesn't like change, but you can't be a proper curmudgeon until you have experienced things you are complaining about yourself. :-D :-D :-D

---

### Post by quequotion on 2013-07-01
> **cariboo907 said:**
> I've got Unity running on Mir on my system, I'd ask the op, why he hasn't set up an extra partition to try it out himself, instead of posting second hand information. I've tried video from all the providers, and done some photo editing, and aside from the two cursors, and a bit of a delay during keyboard input, for pre-alpha software, it works pretty well.For some reason it bothers me when people use "op" in a forum where people don't post anonymously. I have a name, It's quequotion. In a pinch qq is fine (no relation to the chinese social network).
You're running Unity/Mir; not Unity/XMir? No one has posted any tests of this DE/DS. You may be the only person with this working. Please tell us more about your configuration.
As for setting up a test system, I'll get around to it eventually. This would mean:
1. Wiping and repartitioning my backup drive (the main drive is a RAID:0 which I dare not disturb), and I don't like to go without a backup very long.
2. Doing it in a virtual machine (not at all the most reliable way to test anything, let alone a display server).
3. Running the OS from a Live CD or a USB stick, which will lag.
> I'd also like to ask the op what his experiences with a [Rebecca Black ]("http://ubuntuforums.org/showthread.php?t=1906762") are, as it is the only working implementation of wayland, that is available from any source. Then ask me in the 2nd person and not the 3rd.
I'll see if I can run it from a Live CD.> He himself admits he doesn't like changeDid I say that? I don't really feel that way. Change can be good, when change is progressive. I don't think that Mir is a progressive change. I think it is going to isolate Ubuntu, and that isn't good for anybody.
> until you have experienced things you are complaining about yourself. :-D :-D :-DYou have a point. I should run some tests. Eventually I will, but I also have a job and a personal life. It takes far less time to post messages about my concerns than to setup a testbed system for punishment. It's also far less painful.

It's also important to me that the dsiplay server suppport proprietary binary drivers. Another reason for my opposition to Mir is that I hoped Canonical would back Wayland and encourage manufactures to do so as well. There's no guarantee that support for Mir will mean support for Wayland, so the key moment to reverse course is now, *before* Mir gets pushed onto millions of desktops.

---

### Post by tartalo on 2013-07-01
> **cariboo907 said:**
>  [Rebecca Black ]("http://ubuntuforums.org/showthread.php?t=1906762") (...)  is the only working implementation of wayland, that is available from any source.

If you fell inclined to test the Wayland waters there are currently several places you could start, these are some that I could remember, not that I tried them personally:

* [Maui](http://www.maui-project.org/en/about/maui/) is using Wayland today. 

* Kwin developer Martin Graeßlin explained how to [test KDE Plasma on Wayland](http://blog.martin-graesslin.com/blog/2013/06/starting-a-full-kde-plasma-session-in-wayland/ ) yourself, he does clearly warn that it's a hack.

* [Arch Linux](https://www.archlinux.org/) offers the possibility to use XWayland, it will replace your real X.

* The library that will in theory allow Mir to use Android drivers, libhybris, was actually developed for Wayland by a [Jolla](http://jolla.com/) engineer, Jolla is a company created by ex-Nokia engineers that worked on Meego, and you can preorder now the phone they will release towards the end of this year. Their OS, Sailfish OS, is based on [Mer](http://www.merproject.org/). If you know what you are doing Mer is an appropriate testbed for Wayland.

* The official [Plasma Active](http://plasma-active.org/) image is based on Mer too.

* This summer Phones and Tablets that use [Tizen](https://source.tizen.org/release/tizen-2.1) will hit the market. It's possible to run Elightenment on Wayland.

Did I forget anyone?

---

### Post by EgoGratis on 2013-07-01
> This  is not going to be as much fun as having a go at it and then being  able  to say "Well, it's not my thing" and installing something else.

Sure it will be. Probably it will be more fun because you will have much more choices when it comes to display servers and currently you don't have that.

> So this is the state of Mir: it  doesn't work with the DE it's being designed for. Not yet. *Not at all*. Will it be ready for 13.10? *Probably not*,   but it's shipping out anyway as a testbed for 14.04. Considering the   size and experience of the team developing Mir, will there be a   full-fledged Unity/Mir desktop by the time 14.04 comes out? Anyone good   with crystal balls?

Nobody said Unity 8 on Mir will be ready for Ubuntu 13.10 desktop (PC) usage by default. In Ubuntu 13.10 Unity 7 on top of XMir + Mir will be used. You where asking about benchmarks for pure Unity (8) on top of Mir and i answered to that! You don't need a crystal ball for that you can look back and see for your self what the question was.

> Not many years ago, ATI rebased their binary driver and dropped legacy   support for a number of cards. Some of those cards had been on the   market for less than a year--my Radeon X1550 among them. They did not   provide a separate legacy driver and the previously released driver was   incompatible with upcoming releases of Xorg. It became impossible for   many users, including myself, to upgrade Xorg and therefore to upgrade   our distributions without switching to the FOSS driver.

Yes i am well aware of that and i personally don't have any issues with that. This older cards are (officially) supported through FOSS driver and this works for me and because of that FOSS driver improved quite a bit and for that transitional phase you didn't have to upgrade Ubuntu you could use LTS release for a year or two with the blob and now when FOSS driver will get decent dynamic power management... Well now FOSS driver it's probably better option for this older cards than blob ever was.

 > Nvidia strictly *does not*  contribute to FOSS nor do they release programming specs for FOSS  developers to work with.

Yes they should do more when it comes to FOSS driver i agree but i can still use Linux + their cards as i said and expect it to work (except multi GPU Optimums like hardware).

And i will say it again ATM i do believe mayor GPU players have strong interest in providing decent Linux support! This is the point i was making and i don't agree mayor GPU players don't have strong interest in providing decent Linux support.

> Bullseye.

And then you (and other DEs too) would be more than happy to use Unity + Mir if Wayland compatibility would be maintained. Are you really sure because i doubt that!

> For some reason it bothers me when people use "op" in a forum where people don't post anonymously.

Standard procedure these days and i don't see nothing wrong with that.

---

### Post by quequotion on 2013-07-06
> **EgoGratis said:**
> Sure it will be. Probably it will be more fun because you will have much more choices when it comes to display servers and currently you don't have that.More choices perhaps, but reconfiguring a display server is not something you *ever* want end users to be doing. I have experience with that kind of thing, but it won't be conceivable for new users who are presented with a clumsy Unity/XMir desktop; it will be easier for them to install Windows and that is what they will do.> Nobody said Unity 8 on Mir will be ready for Ubuntu 13.10 desktop (PC) usage by default. In Ubuntu 13.10 Unity 7 on top of XMir + Mir will be used. You where asking about benchmarks for pure Unity (8) on top of Mir and i answered to that! You don't need a crystal ball for that you can look back and see for your self what the question was.No one has provided benchmarks for Unity/Mir because only one person is even running that DE. I made a point of not specifying version numbers to avoid confusion. Less important that what version of Unity and what version of Mir *may be working in the future* is the fact that current versions do not appear to be ready. In concession, one user has reported running some kind of true Unity/Mir desktop that seems to be functional, but it certainly doesn't have binary driver support and a number of applications are likely unstable.> Yes they should do more when it comes to FOSS driver i agree but i can still use Linux + their cards as i said and expect it to work (except multi GPU Optimums like hardware). And i will say it again ATM i do believe mayor GPU players have strong interest in providing decent Linux support! This is the point i was making and i don't agree mayor GPU players don't have strong interest in providing decent Linux support. I wouldn't mistake service for sincerity. They will play along only if GNU/Linux maintains a decent market share.> And then you (and other DEs too) would be more than happy to use Unity + Mir if Wayland compatibility would be maintained. Are you really sure because i doubt that!Your comment doesn't correlate to the statements on this point. Unity/Mir and Wayland compatibility is another, distinct issue. The comment I had replied to here pointed out that if Canonical had stuck to their commitment to develop and support Wayland then there would be no controversy. There would be no conflict or users and developers upset about this issue as Mir would never have existed. > Standard procedure these days and i don't see nothing wrong with that.Standard procedure on 4chan because it doesn't require names. It worries me to see customs from 4chan spread out across the internet. That is not a place where people should be learning manners or behavior.

---

### Post by EgoGratis on 2013-07-06
> Your comment doesn't correlate to the statements on this point.  Unity/Mir and Wayland compatibility is another, distinct issue. The  comment I had replied to here pointed out that if Canonical had stuck to  their commitment to develop and support Wayland then there would be no  controversy. There would be no conflict or users and developers upset  about this issue as Mir would never have existed.

But you and other DEs would probably still not be using it? It's a bit pointless then to debate strongly over the decisions made isn't it?

P.S. First somebody has to beat X11/Xorg in a meaningful way, EGL drivers need to evolve, Wayland protocol needs to mature, Mir needs to mature... then we will talk again what makes sense and what not.

---

### Post by tartalo on 2013-07-06
[QUOTE=EgoGratis] And then you (and other DEs too) would be more than happy to use Unity + Mir if Wayland compatibility would be maintained. Are you really sure because i doubt that! [/quote]
[QUOTE=EgoGratis]But you and other DEs would probably still not be using it? It's a bit pointless then to debate strongly over the decisions made isn't it?[/QUOTE]

You insist, so this seems important for you, but you are mixing different questions so it's a bit difficult to understand what you ask, let me try:

* Would other DEs besides Unity use Unity if Mir was Wayland compatible?

Err, no? At most some parts, like someone using Unity's HUD or something like that, but I've heard that reusing parts of Unity is difficult because of it's intricate design. 

* Would other DEs besides Unity use Mir as the default compositor if Mir was Wayland compatible?

Perhaps.

There are DEs that rely on X11 Window Managers that didn't develop themselves, like LXDE using Openbox. They do have plans for future Wayland compatibility so unless Openbox decides to move to Wayland they'll have to use something else, If Mir was Wayland compatible they could have considered it as an option, now I don't see it happening.

The DEs that develop their own X11 Window Managers already had plans to make them Wayland compatible, and that probably wouldn't change in the short term. But in the long term who knows, for example KDE is now recommending Gstreamer, which was a Gnome thing, these kind of reevaluations happen all the time, specially if they clearly benefit the users.

* Would users of DEs other than Unity use Unity if Mir was Wayland compatible?

More likely than with Mir being Wayland incompatible. Most that don't use Unity probably simply prefer other alternatives, but some can't use it because it only works properly in Ubuntu, and porting it will be more difficult after Mir. I don't really know if the people that have been trying to hack Unity in to Arch are doing it because of the challenge or because they actually like Unity as a DE, I also don't know if any people that like Unity have sacrificed it because what they don't like are Mir future plans, but people that liked Ubuntu as a whole did jump ship because of Mir not being Wayland compatible.

* Would users of DEs other than Unity use Mir if Mir was Wayland compatible?

Definitively yes. People make every kind of heterodox combinations: KDE on Openbox, XFCE on Compiz... So, why not?

What's important to understand is that current Mir plans close a lot of doors to Ubuntu users and would complicate developers' life if they chose to acknowledge it's existence. I have used the Word Wide Web to exemplify the importance of commonly agreed standards before and I'll do it again. You probably have heard about XAML and Silverlight, when everyone was discussing what we know today as HTML5 for rich interfaces in the web, Microsoft attempted to push their own thing instead, it was somehow "open" and there was a half working implementation for Linux too, Netflix used it, but it was an attempt to gain control of the web (again) and such things tend to fail in the end. Would I use Internet Explorer if they had backed HTML5 since the beginning, probably not, but that's not what matters, when there's a commonly agreed standard, which implementation I choose to use becomes irrelevant.

---

### Post by EgoGratis on 2013-07-06
> You insist, so this seems important for you, but you are mixing  different questions so it's a bit difficult to understand what you ask...

OP  said he does not use Unity that is why i asked him why does he have  strong opinion on something he does not use in the first place. He  insist Mir should be Wayland compatible right from the start and i asked  what purpose would that have and if he expects other DEs would jump on  the ship and use Mir. As long as common drivers are used for all  solutions i don't see a problem given the fact there will not be only  one display server or only one implementation to support Wayland  protocol anymore. Once Wayland matures i don't see why Mir could not  gain support for it and while maturing i don't see why Wayland protocol  couldn't implement support for something tested and used in Mir.

I think it's not difficult to understand the question and it doesn't need further explanation.

> Perhaps.

They  can still use Mir (add support) if it suits their purpose. About  Canonical being upstream for others and not only Ubuntu perhaps in the  future when things mature. Canonical started by positioning itself to  serve what upstreams have to offer to end users now this changed a bit  and they produce code for Ubuntu purposes and who knows in the future  they might become important upstream to serve others with the code too  and yes as strong upstream they will/would have stronger control over  it. What will/would they do with that control? I guess we will just have to wait and see how will/would they act as strong upstream because we are not there yet.

> There are DEs that rely on X11 Window Managers that didn't develop  themselves, like LXDE using Openbox. They do have plans for future  Wayland compatibility so unless Openbox decides to move to Wayland  they'll have to use something else, If Mir was Wayland compatible they  could have considered it as an option, now I don't see it happening.

The DEs that develop their own X11 Window Managers already had plans to  make them Wayland compatible, and that probably wouldn't change in the  short term.

If Mir matures and proofs itself i don't see  why support could not be added and the same applies for Wayland that  needs maturing too. First somebody has to beat X11/Xorg in meaningful  way, adding 10% overhead and not much benefit will not beat X11/Xorg  anytime soon for example. Who knows what will be the pace of Wayland/Mir  based solution in achieving this goal but i doubt anybody wants to  wait for this to happen for more than let's say 2 years in the future.

---

### Post by buzzingrobot on 2013-07-06
> **tartalo said:**
> 
... current Mir plans close a lot of doors to Ubuntu users and would complicate developers' life if they chose to acknowledge it's existence.

As a user, I have to admit I am not especially concerned if the lives of developers are complicated or not.  Developers make software.  If I like what they make, I use it.

As a user, I see three competing pieces of software here: X, Mir, Wayland.  Two of them aren't ready for use.  When they are, I'll make my judgement based on what I see.  If Distribution X with Wayland is best, I'll use it. ("Best" defined broadly, including access to applications that run on it.) If Ubuntu with Mir is best, I'll use it.  If something running X is best, I'll use that.

Competition is good.  I'm not feeling any of the angst about Mir that some folks seem to feel.

(Standards are good, too, usually.  But, they can be counterproductive when the need to remain faithful to an aging piece of software that enforces de facto standards stifles innovation and inmprovement.)

---

### Post by tartalo on 2013-07-06
> **EgoGratis said:**
> OP  said 

Please stop depersonalizing quequotion, he doesn't like it and I'd like you to respect it.

> As long as common drivers are used for all  solutions i don't see a problem

Drivers are just one part of the equation, an important one indeed, but there are others, like toolkits, DEs that previously worked on Ubuntu, other distributions... Mir departing from the agreed standard is very disruptive, and it will either give developers headaches or damage Ubuntu users' choices. There's still much to see, but the second option seems to be the one taking more weight (and it doesn't surprise me a bit).

> Once Wayland matures i don't see why Mir could not  gain support for it

In my opinion that would be a wise decision that shouldn't be delayed.

> I don't see why Wayland protocol  couldn't implement support for something tested and used in Mir.

Wayland is the agreed standard, if Mir developers come up with an idea that would benefit everybody I don't see either why that couldn't be added to the standard, bending an agreed standard to a "one distro only" solution is however quite a different thing.

> They  [other DEs] ]can still use Mir (add support) if it suits their purpose.

Not quite, Mir is not developed with anything but Unity in mind, there are contradictory messages about API / ABI stability ... They, Canonical, are not putting it easy for others to adopt Mir, and I don't really understand why they try to make users think otherwise. If there was no agreed standard adopting Mir as a de-facto standard could be a price someone might want to pay, but with Wayland already properly defined Mir is not very attractive.

> About  Canonical being upstream for others

Canonical has already been upstream for others, for example with upstart, or with lightdm. But with Mir it seems difficult, honestly.

---

### Post by EgoGratis on 2013-07-06
> Please stop depersonalizing quequotion, he doesn't like it and I'd like you to respect it.

It's not depersonalizing it's standard procedure.

> like toolkits

More work for Canonical.

 > DEs that previously worked on Ubuntu,  other distributions...

Will remain working in my opinion for foreseeable future just like they do now and there will be some new possibilities on how exactly to use them.

 > Mir departing from the agreed standard is very  disruptive, and it will either give developers headaches or damage  Ubuntu users' choices. 

I don't think users of Ubuntu will have less choices in foreseeable future probably there will be more choices but let's wait and see.

> In my opinion that would be a wise decision that shouldn't be delayed.

Wayland still needs time to mature and delay is something that will happen anyway.

> Wayland is the agreed standard, if Mir developers come up with an idea  that would benefit everybody I don't see either why that couldn't be  added to the standard, bending an agreed standard to a "one distro only"  solution is however quite a different thing.

But imagine Ubuntu Touch using SurfaceFlinger at the beginning on mobile devices and it worked? And imagine Mir would be Wayland compatible ATM and "qq" and other DEs not using it anyway... And imagine this that "agreed standard" and Mir are not yet suitable replacement for X11/Xorg ATM. First we have to get there.

> Not quite, Mir is not developed with anything but Unity in mind, there  are contradictory messages about API / ABI stability ... They,  Canonical, are not putting it easy for others to adopt Mir, and I don't  really understand why they try to make users think otherwise. If there  was no agreed standard adopting Mir as a de-facto standard could be a  price someone might want to pay, but with Wayland already properly  defined Mir is not very attractive.

You see being Wayland compatible right from the start would not made that much difference would it. That is why i do believe it's quite pointless to discus this before we have something that we can actually use in real world and to work better compared to X11/Xorg. 

> Canonical has already been upstream for others, for example with  upstart, or with lightdm. But with Mir it seems difficult, honestly.

Yes upstart is good example how first there was upstart then somebody else made something else and now we have 2 competing solutions and that is about it. The sky isn't falling.

---

### Post by neu5eeCh on 2013-07-07
If you're interested, this thread is essentially identical to the thread I started [here]("http://ubuntuforums.org/showthread.php?t=2127165") called [Mir vs. Wayland & effect on Linux "Ecosystem"?]("http://ubuntuforums.org/showthread.php?t=2127165") Maybe the two threads should be combined? 

Anyway, my impression is that Ubuntu is the 986 pound gorilla and that, like it or not, the other distros can either cling to Wayland -- and lose even more market share -- or adopt MIR. **My 2 Cents **(Canadian)**:** Companies like AMD and INTEL are _**not**_ going to be developing new drivers for Wayland **_and_** MIR. They're going to pick one and it's going to be MIR because that's where the market share is (or promises to be). 

Regardless of my preferences (and I really only want what works) a better title to this thread might be addressed to distros committing themselves to Wayland: *Stop this train before _you're_ derailed by _Wayland_*. I see a future where every distro that is not MIR-based is forced to rely on open source drivers or simply don't work on newer hardware. To make a very loose analogy, Ubuntu will be the Windows of the Linux-verse and the rest of the distros will be the marginal 1% (and that's probably how a nice little niche of linux users prefer it).

---

### Post by llanitedave on 2013-07-07
> **buzzingrobot said:**
> As a user, I have to admit I am not especially concerned if the lives of developers are complicated or not.  Developers make software.  If I like what they make, I use it.



If the developers are put off, they'll be more likely to make the software you like for some other system rather than Unity.

That said, I'm not feeling any sense of forboding.  It's not like Mir is going to suddenly make all previously developed software nonfunctional.  It's not the application developers that are going to be inconvenienced anyway.  They use standard GUI tools that are already compatible with X.  Mir will still have to allow all existing applications that run on the QT or Wx toolkits, for example.   It will have to be compatible with the graphic outputs of existing game and imaging applications.  It's the toolkit developers that will have to be kept happy.  If future versions of QT or Wx won't work on Mir, then neither will the applications that use them.  Application developers will either have to use toolkits developed specifically for Mir, or older versions that retained compatibility.  Otherwise, it's the maintainers of Mir that are going to be kept busy constantly backporting.

---

### Post by buzzingrobot on 2013-07-07
> **llanitedave said:**
> If the developers are put off, they'll be more likely to make the software you like for some other system rather than Unity.

I have no deep-seated preference to Unity or any other platform.  It's up to Canonical to make sure apps work on Mir. They have the incentive to do that, other developers don't. It's not like the OS X independent developer arena, where incomes depend on adapting to whatever new thing Apple rolls out.  

If Canonical doesn't make that happen, c'est la vie.

> Application developers will either have to use toolkits developed specifically for Mir, or older versions that retained compatibility.  Otherwise, it's the maintainers of Mir that are going to be kept busy constantly backporting.

It would make sense for Canonical to provide those toolkits. Ideally, they'd engineer some magic into Mir to handle the compatibility.

On the device front, I'd expect Ubuntu to be the gatekeeper for those apps, giving them the opportunity to weed out any that don't deliver on Mir.

---

### Post by EgoGratis on 2013-07-07
> Anyway, my impression is that Ubuntu is the 986 pound gorilla and that,  like it or not, the other distros can either cling to Wayland -- and  lose even more market share -- or adopt MIR.

I think we will be using Mir, X11/Xorg, Wayland based solutions for quite some time and there is no need for ultimatums like that.

 > **My 2 Cents **(Canadian)**:** Companies like AMD and INTEL are _**not**_ going to be developing new drivers for Wayland **_and_** MIR.

Sure they will as they already do in a way and this will only improve in the future.

---

### Post by buzzingrobot on 2013-07-07
> **EgoGratis said:**
> I think we will be using Mir, X11/Xorg, Wayland based solutions for quite some time and there is no need for ultimatums like that.


Seems more of a prediction than an ultimatum.

In any case, it's pointless to discuss market share when we're discussing desktop Linux,  There is no desktop Linux market.  A market is a place to buy and sell.  No one is buying and selling desktop Linux.

---

### Post by neu5eeCh on 2013-07-07
> **buzzingrobot said:**
> Seems more of a prediction than an ultimatum.

In any case, it's pointless to discuss market share when we're discussing desktop Linux,  There is no desktop Linux market.  A market is a place to buy and sell.  No one is buying and selling desktop Linux.

Right. It's a prediction. And you're right that there's no "desktop Linux market", but that's not the marketshare I was predicating.

> **EgoGratis said:**
> Sure they will as they already do in a way and this will only improve in the future.

Really? Name one.

In the meantime, while I hold my breath, here's [Phoronix]("http://www.phoronix.com/scan.php?page=news_item&px=MTE0NjI") calling from planet reality:

"AMD and NVIDIA will be unlikely to support Wayland/Weston until there's  any serious adoption of this next-generation display server to succeed  the X.Org Server on the Linux desktop. When there's benefits to Wayland  where they can justifying the support expense, the support will likely  come but not anytime in the near future -- not in 2012."

Unless Canonical goes out of business, the only "serious adoption" is going to be on MIR.

---

### Post by EgoGratis on 2013-07-07
> No one is buying and selling desktop Linux. 				

Not true. System76 does that for example and i doubt they serve the whole 1%. There are DELL laptops:

[http://www.ubuntu.com/partners/dell/dellxps](http://www.ubuntu.com/partners/dell/dellxps)

And every now and then you find hardware with preloaded Ubuntu (desktop) or some other Linux distribution.

> Really? Name one.

If we are talking about official support then Intel and AMD for example. I tested Wayland and Mir on both and both worked.

> Unless Canonical goes out of business, the only "serious adoption" is going to be on MIR.

Yes i think Mir should get some "serious adoption" in near future and probably Wayland based solutions will work on that hardware just fine. Both will use EGL.

---

### Post by EgoGratis on 2013-07-07
And said that regarding this thread i will just wait for some serious adoption and that is about it. This is basically what we all want to happen and it should help everybody.

Then we can talk again if something else makes sense or we did manage to pull it of in the right way.

---

### Post by neu5eeCh on 2013-07-07
> **EgoGratis said:**
> If we are talking about official support then Intel and AMD for example. I tested Wayland and Mir on both and both worked.


Neither company has indicated an intention to develop drivers for Wayland.

---

### Post by BigSilly on 2013-07-08
> **VTPoet said:**
> Neither company has indicated an intention to develop drivers for Wayland.

They've not indicated an intention to develop for Mir either. In fact, because both have been extremely quiet during all of this debate, it's pretty difficult to discern exactly what, if anything, they have in mind.

For me, I hope both Mir and Wayland will receive support from the graphics driver vendors. It's less of an issue for AMD users, as the open source driver is coming on a great deal of late as I'm led to believe. But for us Nvidia users, the waters are considerably murkier. I wouldn't be averse to moving to AMD should I need to. I want the option of continuing to use those "marginalised" distros (as VTPoet calls them) and also Ubuntu if I wish. I don't want to be beholden to one distro vendor. I didn't choose to move from Windows only to end up locked in somewhere else. If that means switching to a graphics card with a decent open source driver and my options intact, so be it.

---

### Post by EgoGratis on 2013-07-08
> **VTPoet said:**
> Neither company has indicated an intention to develop drivers for Wayland.

Not true Intel and AMD do provide (official) support for Wayland/Mir. How else would i be able to test both on Intel/AMD hardware if they wouldn't? About the blobs i don't quite get why somebody would think it's against the interest of AMD and Nvidia to offer support through blob it's just that currently nobody is using Mir/Wayland by default does it and what exactly would the blob be used for if it would exist?

---

### Post by neu5eeCh on 2013-07-08
> **BigSilly said:**
> ...it's pretty difficult to discern exactly what, if anything, they have in mind.

I don't think it's all that difficult. It's probably no different than the standards fight between Beta & VHS or Blu Ray & HD DVD. One thing I'd strongly bet against is AMD or INTEL developing for Wayland *and* MIR. They're going to pick one or the other. I think this is partly why Canonical (who has been lobbying them) is pushing MIR for the next release. My bet? Ubuntu is where the eyes are. MIR will get the proprietary drivers. Wayland won't.

---

### Post by neu5eeCh on 2013-07-08
> **EgoGratis said:**
> Not true Intel and AMD do provide (official) support for Wayland/Mir. How else would i be able to test both on Intel/AMD hardware if they wouldn't? 

Because you're probably not testing what you think you are. You're certainly not running proprietary drivers directly on Wayland or MIR. If you think you are, Phoronix would like to hear from you (as would a lot of other pundits in the Linux-verse).

---

### Post by quequotion on 2013-07-09
> **EgoGratis said:**
> But you and other DEs would probably still not be using it? It's a bit pointless then to debate strongly over the decisions made isn't it? Yes and no. I'm not delusional; I don't expect one forum thread to reverse a decision made by the head of the food chain at Canonical. I do think it important to express my point of view now in the event that circumstances chage in the future. Canonical has backed out of important commitments before, when they became impediments to further deployment of Ubuntu. If Mir becomes a hinderance, perhaps they will reconsider in the face of users who were concerned now and may be frustrated later.

> First somebody has to beat X11/Xorg in a meaningful way, EGL drivers need to evolve, Wayland protocol needs to mature, Mir needs to mature... then we will talk again what makes sense and what not. This is true. Although I'd rather see the resources dedicated to developing Mir be placed behind Wayland, I suppose we'll simply have to wait and see. I just hope this doesn't become another point where Canonical proceeds with their plan regardless of failing popularity, lacking usability, missing significance, zero portability, or highly-improbable adoptability (plenty of threads about those things elsewhere i suppose). *Sometimes* their strategy has actually worked.

---

### Post by EgoGratis on 2013-07-09
> One thing I'd strongly bet against is AMD or INTEL developing for Wayland *and*  MIR. They're going to pick one or the other. I think this is partly why  Canonical (who has been lobbying them) is pushing MIR for the next  release. My bet? Ubuntu is where the eyes are. MIR will get the  proprietary drivers. Wayland won't.

Intel investing that  much in Wayland and not providing support for it? Intel ALREADY supports  both you know that don't you? About only one FOSS OS specific EGL  driver blob... Well we will see won't we in near future if your theory  ads up. If Valve would use Mir + AMD/Nvidia blob for game box maybe but  generally speaking i think there will still be one blob on AMD and  Nvidia download page for X11/Xorg, Wayland based, Mir distributions. 

> Because you're probably not testing what you think you are. You're  certainly not running proprietary drivers directly on Wayland or MIR. If  you think you are, Phoronix would like to hear from you (as would a lot  of other pundits in the Linux-verse).                 

You should read what i wrote again. 

> Yes and no. I'm not delusional; I don't expect one forum thread to  reverse a decision made by the head of the food chain at Canonical. I do  think it important to express my point of view now in the event that  circumstances chage in the future. Canonical has backed out of important  commitments before, when they became impediments to further deployment  of Ubuntu. If Mir becomes a hinderance, perhaps they will reconsider in  the face of users who were concerned now and may be frustrated later.

Yes  i could agree about the points you made and to see them as valid concerns BUT i doubt decision can be reversed  in foreseeable future and because of that serious adoption is next  logical step.

> This is true. Although I'd rather see the resources dedicated to  developing Mir be placed behind Wayland, I suppose we'll simply have to  wait and see. I just hope this doesn't become another point where  Canonical proceeds with their plan regardless of failing popularity,  lacking usability, missing significance, zero portability, or  highly-improbable adoptability (plenty of threads about those things  elsewhere i suppose). *Sometimes* their strategy has actually worked.

I  don't know what will happen but because common drivers will probably be  used for both competing solutions i am more concerned in serious  adoption ATM then anything else!

---

### Post by ZoiaGuyver on 2013-07-10
I'm not normally one to get into these kinds of "debates" but with all the FUD about this "Wayland vs Mir" stuff I can't help but put my penny in.

X.org has been around for 26 years it was never intended to do what it does today and if you look at the way it works and what it works on, it is no more than a mass of hacks and band aids to keep it going. Wayland is a great direction to go for X.org and I'm certain will be a big success no matter what. Mir is the right way to go to achieve what "Ubuntu" want's to achieve, they are looking for a "unified" experience across many device formats. Wayland isn't going to cut it for what they need, so they are building something that can do it.

All this argument and people saying about projects being "stabbed in the back" is imo over the top and uncalled for. A lot of the people saying this stuff already hate or have hated Canonical anyways in the past. Unity was meant to be a "failboat" and Canonical should have stuck with Gnome, This has panned out to be the total opposite and Unity although not the success I would have liked it to have been, is still a major success the same will happen with Mir. In the early days it will prob have bugs and "usability" problems, you will probably see all the "naysayers" and "told you so" people out in strength, bashing Canonical and Ubuntu into the floor about how users will mass migrate (and they prob will at the start). Then a few releases down the line it will drop into the same as we see with Unity, people having to backtrack on things that had been said (even myself, I hated Unity at the start, Now I use it's pretty much daily).

I just want to bring up that no one in Canonical or from what I have seen posted want's Wayland to fail, what they do want though it for it to become the "De-facto" standard for Linux. Why is it so many hate the announcement of Mir (ok the way it was announced could have been better timed and worded) some I have seen want Mir to fail just so they can blame Canonical? Fragmentation is a word used a lot in the posts I have read and tbh Mir will cause no more fragmentation than Nvidia vs ATI/AMD has down the years.

People will take what works. If Mir does what Ubuntu wants it to (which im 110% sure it will, maybe not straight away but it will get there) then it's an achievement and advance for everyone. Ubuntu brought Steam to Linux (atleast as far as a supported Linux version goes). When Ubuntu switches to Mir with the current time investment and backing from Valve I cannot see Mir failing at all. 

This is being done "for us" its not "against us". We may not all agree on how or why but if we did then I would think the community had a lot more problems than we do now (mutual agreement on anything community wide is unheard of, there is always something someone dislikes).

Lets all just agree that we can't see the future and we don't know how things will pan out.

---

### Post by mikodo on 2013-07-11
Deleted.

---

### Post by mr john on 2013-07-12
I couldnt care less. If it works great. If not then there are plenty of other options available. Don't see why people are making such a big deal out of it.

---

### Post by Synthead on 2013-07-12
GPL software is GPL software.  Have you read the GPL license?  If Canonical wants to *copy their code*, make a minor change, and call it something they made up, *they can.*  Look at the forks of MySQL.  All the custom Linux kernels.  The list goes on.  As long as they comply with the licenses at-hand, nobody needs to worry about "borrowing," "ripping off," or otherwise acting outside of the GPL's purpose.  In fact, this kind of behavior is *encouraged*, and the developers who picked the GPL as their license agreed to its terms.

---

### Post by 3rdalbum on 2013-07-12
Forking anything is great - look at Libreoffice, MATE, Cinnamon, Nvidia/Kompozer/Bluegriffon and how well they are received. Writing a new text editor or video editor or desktop environment or display server is also great. Developers should be able to scratch their itch! Even with all this forking, the Linux desktop is not fragmented...

...until it is Canonical doing it, then suddenly it will destroy Linux and kill all the kittens of the world and cause the Earth to fall into the sun.

---

### Post by tartalo on 2013-07-13
> **3rdalbum said:**
> Forking anything is great - look at Libreoffice, MATE, Cinnamon, Nvidia/Kompozer/Bluegriffon and how well they are received. Writing a new text editor or video editor or desktop environment or display server is also great. Developers should be able to scratch their itch! Even with all this forking, the Linux desktop is not fragmented...

...until it is Canonical doing it, then suddenly it will destroy Linux and kill all the kittens of the world and cause the Earth to fall into the sun.

The thing isn't that Canonical is bad whatever they do, but that whoever doing what Canonical is doing now would be doing bad.

Replacing the display server implicates a lot of projects that need to follow, it has nothing to do with "I'll make another wysiwyg web authoring tool (kompozer) and let users decide whether they use it or not", the display server involves GPU drivers, toolkits, desktop environments... In a few words, everyone. If you take in account that everyone had already been discussing for years about Wayland as a replacement to X, and investing time on it, whoever came out the blue with something like Mir would be the bad guy, whoever.

In this case it was Canonical, they thought that, since they were such a popular distro, introducing an artificial incompatibility with other distros and DEs would benefit their income despite the problems caused to their own users. 

I'll repeat that just in case someone thinks that all this noise is because of the envy from other distro users: It's not, Mir will cause problems mostly to **Ubuntu** users, the ones that are most angry are the Ubuntu users or ex-users that understand the consequences of Canonical's plans.

My opinion is that either they miscalculated their own power, or they counted with losing a great amount of *desktop* users. After all, Ubuntu's business is in the phone now.

---

### Post by hansdown on 2013-07-13
Tartalo, thanks for your insight.

> I'll repeat that just in case someone thinks that all this noise is because of the envy from other distro users: It's not, Mir will cause problems mostly to Ubuntu users, the ones that are most angry are the Ubuntu users or ex-users that understand the consequences of Canonical's plans.

My opinion is that either they miscalculated their own power, or they counted with losing a great amount of desktop users. After all, Ubuntu's business is in the phone now. 

These are perhaps the wisest words in this thread.

I was stoked to hear of the ubuntu phone, and happy, that canonical could become "income generating".

I appreciate Mark Shuttleworth's funding, and personal hard work, but the developement priorities over the last few years, leaves me hankering for former times.

Personally, I no longer plan to buy an ubuntu phone.

I have been keenly following tizen developement, as they are upfront, and honest with their plans.

---

### Post by castrojo on 2013-07-14
> **tartalo said:**
> In this case it was Canonical, they thought that, since they were such a popular distro, introducing an artificial incompatibility with other distros and DEs would benefit their income despite the problems caused to their own users.

a) Distros and desktops are already incompatible.
b) The last place anyone would look to generate income would be a display server.

---

### Post by JDShu on 2013-07-14
> **tartalo said:**
> The thing isn't that Canonical is bad whatever they do, but that whoever doing what Canonical is doing now would be doing bad.


Let me preface by saying I agree completely, but I wanted to discuss some of the points you are bringing up.


> 
Replacing the display server implicates a lot of projects that need to follow, it has nothing to do with "I'll make another wysiwyg web authoring tool (kompozer) and let users decide whether they use it or not", the display server involves GPU drivers, toolkits, desktop environments... In a few words, everyone. If you take in account that everyone had already been discussing for years about Wayland as a replacement to X, and investing time on it, whoever came out the blue with something like Mir would be the bad guy, whoever.


Regarding drivers, my understanding from reading discussions elsewhere (namely r/linux and phoronix) is that as long as a gpu drivers supports EGL, then it will support Wayland/Mir/Whatever else. So this might not be a problem. 

In terms of toolkits and DEs, the question is whether they will support both Wayland and Mir. Obviously all the toolkits and DEs are supporting Wayland so there is no issues on that front. Additionally, Canonical will certainly support anything that Ubuntu needs downstream. The end result is that there will probably be no issues for most users. The only potential problem I could see is Canonical dropping the ball supporting various toolkits and applications which could harm Ubuntu users, but doesn't affect the ecosystem as a whole.

> 
In this case it was Canonical, they thought that, since they were such a popular distro, introducing an artificial incompatibility with other distros and DEs would benefit their income despite the problems caused to their own users. 


I think this is attributing too much malice to Canonical. More likely, Canonical wants control over their display server so that they can rapidly adjust to changing conditions instead of having to wait for Wayland community.

---

### Post by BigSilly on 2013-07-14
I'm no expert on this thing, but it seems to me that the idea driving both Mir and Wayland is that one way or another they offer a *better* solution than X. Either way these new display servers should be a better solution for Nvidia and AMD/ATI graphics driver devs to support over X.

I honestly don't see a future where either Wayland or Mir "wins" anything. I think both will co-exist happily and the driver vendors will support both, and I think the community is fretting itself unnecessarily over a potential "winner". Just imho, how it looks to me on the outside of the development community, as a user.

---

### Post by ikt on 2013-07-14
> **BigSilly said:**
> I'm no expert on this thing, but it seems to me that the idea driving both Mir and Wayland is that one way or another they offer a *better* solution than X. Either way these new display servers should be a better solution for Nvidia and AMD/ATI graphics driver devs to support over X.

I feel the same way about deb and rpm, both are better than source compiling in my opinion... yet for some reason there's no outage about half of linux distro's using RPM and the other half using DEB, this is by far the biggest incompatibility of them all, could you imagine if instead of all those innocent windows users downloading the source in .tar.gz's to extract and stare at in disbelief that in 2013 you can't just click and install a program, they all had .debrpm packages, which upon double clicking installed the program with whichever distro he or she used? But nobody says anything, rpm and deb are just accepted.

---

### Post by EgoGratis on 2013-07-14
> **tartalo said:**
> The thing isn't that Canonical is bad whatever they do, but that whoever doing what Canonical is doing now would be doing bad.

Replacing the display server implicates a lot of projects that need to follow, it has nothing to do with "I'll make another wysiwyg web authoring tool (kompozer) and let users decide whether they use it or not", the display server involves GPU drivers, toolkits, desktop environments... In a few words, everyone. If you take in account that everyone had already been discussing for years about Wayland as a replacement to X, and investing time on it, whoever came out the blue with something like Mir would be the bad guy, whoever.

In this case it was Canonical, they thought that, since they were such a popular distro, introducing an artificial incompatibility with other distros and DEs would benefit their income despite the problems caused to their own users. 

I'll repeat that just in case someone thinks that all this noise is because of the envy from other distro users: It's not, Mir will cause problems mostly to **Ubuntu** users, the ones that are most angry are the Ubuntu users or ex-users that understand the consequences of Canonical's plans.

My opinion is that either they miscalculated their own power, or they counted with losing a great amount of *desktop* users. After all, Ubuntu's business is in the phone now.

Yes it could go both ways it could "hurt" Ubuntu to some extend or it could make Ubuntu accepted and viable upstream in certain areas and i guess we will not have to wait too long to see the direction it will go.

---

### Post by Roasted on 2013-07-14
My 2c:

- Canonical is free to do what they wish, just as any other tech company/community is. I applaud them for trying something a bit different.
- Canonical acted incredibly foolish and arrogant in regard to releasing this news. Their behavior with nearly everything is somewhat disturbing. I hope they took notes to not repeat... any... of that in the future.
- If I were running Canonical, I'm not sure that choosing Mir would be a bad choice. The need for a unified experience could be more efficient with in-house development that cuts out a magnitude of middle-men. On the flip side, I wonder why they didn't fork Wayland to some degree and just use that. That being said, it sounds pretty definitive (based on what I read) that Mir's current status is thanks to years of Wayland development, which makes Mir seem like it was developed significantly faster than what it truly was. Some sources have already called it a fork. LOL?
- I used to love Unity, but the more nonsense lenses they cram into it, the more I lose interest in Unity all together. If me dropping Unity drops Mir, so be it.
- My lack of interest in Unity does not cause me any grief or hatred towards Canonical whatsoever. I still want them to be successful. Meanwhile, I simply use what works best for me. Ubuntu GNOME fits that bill 1000x over again for a long list of reasons.
- As long as there are no obnoxious support or compatibility issues, I won't disown Canonical. The day Mir gets Nvidia/Intel/AMD drivers while the rest of the world gets nothing, you can bet I'll rage something fierce. Candid opinion: If anybody 'deserves' anything in terms of driver support, I'd vote the Wayland crowd hands down. 

All of this is quite bitter sweet. I want them to succeed, but only if it doesn't directly demolish chances of further support coming from the notable companies I listed above to Wayland. Maybe I'm just a hippy where I want everybody to win and be successful, but like I said, not at the expense of the entirety of the Linux community outside of Ubuntu.

But again, just my 2c.

---

### Post by ZoiaGuyver on 2013-07-15
> **Roasted said:**
> 

All of this is quite bitter sweet. I want them to succeed, but only if it doesn't directly demolish chances of further support coming from the notable companies I listed above to Wayland. Maybe I'm just a hippy where I want everybody to win and be successful, but like I said, not at the expense of the entirety of the Linux community outside of Ubuntu.

But again, just my 2c.


Na your not a "hippy" (or maybe you are.. and I'm in the "hippy" camp aswell).

 I think Mir is a solution for "Ubuntu", they said in one post (i'll try and find the interview about it) that Wayland was trying to do "too much" and a lot of what it can achieve isn't needed for what Ubuntu want's (maybe wayland/westons feature set is getting a little like X?). I think all the worry over the driver support at the moment is pretty much a non-issue, Linux has always had a way of "Working with what you have" I can't see either project forgetting something as major as driver support (afaik at the moment both Wayland and Mir are planned to be well supported by the OSS drivers). If they get "official" support within the proprietary drivers I would def prefer to see Wayland get it first, Canonical/Ubuntu has done a lot for Linux in the sense of exposure, but if that exposure is to the detriment of other projects then it becomes a massive issue (I do not think in any way that is either the plan or goal of the projects, I think it just a "worst case scenario" people are thinking about).

 Linux is about "choice" and "freedom" these two projects have the ability to offer both.

---

