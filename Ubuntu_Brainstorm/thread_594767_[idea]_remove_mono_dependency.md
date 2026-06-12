---
title: "[idea] remove mono dependency"
date: 2007-10-28
forum: Ubuntu Brainstorm
---

### Post by mangar on 2007-10-28
currently, mono is installed by default, and enables only two programs by default: f-spot, and tomboy.

f-spot can be replaced by gThumb, tomboy can be replaced by notecase, and a few dozens of megabytes can be freed from the install cd.

---

### Post by smartboyathome on 2007-10-28
> **mangar said:**
> currently, mono is installed by default, and enables only two programs by default: f-spot, and tomboy.

f-spot can be replaced by gThumb, tomboy can be replaced by notecase, and a few dozens of megabytes can be freed from the install cd.

Tomboy is different than notecase, as it uses actual sticky notes, and F-Spot is used to integrate with digital cameras, is it not?

---

### Post by kellemes on 2007-10-28
I think Mono is a great development platform we will need to support, especially for porting Windows .NET applications to GNU/Linux (one of the goals).
If a heavy default install (some call this bloat) is an issue there are a lot of better distro's out there..

---

### Post by gnomeuser on 2007-10-28
Why.. Mono is a great Free Software platform, the applications rock - why should it be discriminated against?

---

### Post by Simon G Best on 2007-10-29
I'm uneasy with Mono, because of Miguel de Icaza, Microsoft and Novell.  I'd rather not have Mono on my system - and so I've removed it.  I didn't use F-Spot or Tomboy anyway.

Given Microsoft's FUD campaigns, it does seem sensible to ditch Mono.

---

### Post by gnomeuser on 2007-10-30
> **Simon G Best said:**
> I'm uneasy with Mono, because of Miguel de Icaza, Microsoft and Novell.  I'd rather not have Mono on my system - and so I've removed it.  I didn't use F-Spot or Tomboy anyway.

Given Microsoft's FUD campaigns, it does seem sensible to ditch Mono.

I have been around Linux for a decade now, if we removed every thing Microsoft complained a bit about then there would be nothing left. Unless you can provide real hard evidence that Mono is infringing on a patent then you acting as part of the FUD campaign.

Mono is good technology, it has never been proven to infringe on patents and even if it does we have  the OIN to protect us as well as the Mono teams dedication to working around such issues with they should arise.

Aside that applications like Banshee, Tomboy, F-spot and Beagle are great, I would be greatly angered if they disappeared for what I consider no good reason.

---

### Post by Simon G Best on 2007-10-30
> **gnomeuser said:**
> I have been around Linux for a decade now, if we removed every thing Microsoft complained a bit about then there would be nothing left. Unless you can provide real hard evidence that Mono is infringing on a patent then you acting as part of the FUD campaign.

I'm not suggesting we remove every single little thing that Microsoft suggests might be infringing.  But Mono is something of a special case - Miguel de Icaza and Novell.  There's a reason he has the kind of dodgy reputation he's got.

The concern that some people have is that things like Mono might be sort of like Trojan horses, where there'd be supposed patent infringements - except for, say, Novell's paying customers ;)  If anything, it's more about needlessly giving Microsoft and Novell extra FUD opportunities.

> Mono is good technology, it has never been proven to infringe on patents and even if it does we have the OIN to protect us as well as the Mono teams dedication to working around such issues with they should arise.

After Novell's dodgy deal with Microsoft?!?!?  Are you kidding?

> Aside that applications like Banshee, Tomboy, F-spot and Beagle are great, I would be greatly angered if they disappeared for what I consider no good reason.

Tomboy - "a desktop note-taking application which is simple and easy to use. It lets you organise your notes intelligently by allowing you to easily link ideas together with Wiki style interconnects."  Having removed Mono from my system, I find that selecting Tomboy for installation in Synaptic would result in an extra 37.3MB being used!  That's a lot of space for "a desktop note-taking application which is simple" - is it worth it?  Well, there are those other things you mentioned, so let's have a look.

Banshee - "an audio management and playback application for the GNOME Desktop, allowing users to import audio from CDs, search their library, create playlists of selections of their library, sync music to/from iPods, and burn selections to a CD."  That would need an extra 45.0MB.  Why not use, say, Rhythmbox instead?  My point there is that there are already alternatives that don't require bloating our systems with Mono.

F-spot - "meant to be an easy-to-use photo management application.  It allows for importing of your existing photo collections, tagging photos with identifiers, as well as doing simple edits of photos (e.g. rotating)."  39.7MB extra.  What about, say, gThumb?  GQview?  Etc?  Again, it just doesn't seem to justify the Mono bloat.

And finally, Beagle - "A desktop search util for indexing and searching user's data. At the moment, it can index filesystems, Gaim logs, Evolution mail and data, RSS and other."  That would need an extra 35.1MB.  But, when I upgraded to 7.10, "Gutsy Gibbon", I found I got this thing called Tracker instead, which sounds like it does much the same thing, but without the Mono bloat.

Mono really doesn't sound worth it from the small list of dependent packages you gave.  Even putting them all together, they'd take up an extra 65.6MB - for just four applications?!?!?

We can do better than emulate Microsoft bloat.  Let's just ditch the blubber, and reduce Novell-Microsoft FUD opportunities at the same time :D

---

### Post by gnomeuser on 2007-10-30
> **Simon G Best said:**
> I'm not suggesting we remove every single little thing that Microsoft suggests might be infringing.  But Mono is something of a special case - Miguel de Icaza and Novell.  There's a reason he has the kind of dodgy reputation he's got.

The concern that some people have is that things like Mono might be sort of like Trojan horses, where there'd be supposed patent infringements - except for, say, Novell's paying customers ;)  If anything, it's more about needlessly giving Microsoft and Novell extra FUD opportunities.



After Novell's dodgy deal with Microsoft?!?!?  Are you kidding?



Tomboy - "a desktop note-taking application which is simple and easy to use. It lets you organise your notes intelligently by allowing you to easily link ideas together with Wiki style interconnects."  Having removed Mono from my system, I find that selecting Tomboy for installation in Synaptic would result in an extra 37.3MB being used!  That's a lot of space for "a desktop note-taking application which is simple" - is it worth it?  Well, there are those other things you mentioned, so let's have a look.

Banshee - "an audio management and playback application for the GNOME Desktop, allowing users to import audio from CDs, search their library, create playlists of selections of their library, sync music to/from iPods, and burn selections to a CD."  That would need an extra 45.0MB.  Why not use, say, Rhythmbox instead?  My point there is that there are already alternatives that don't require bloating our systems with Mono.

F-spot - "meant to be an easy-to-use photo management application.  It allows for importing of your existing photo collections, tagging photos with identifiers, as well as doing simple edits of photos (e.g. rotating)."  39.7MB extra.  What about, say, gThumb?  GQview?  Etc?  Again, it just doesn't seem to justify the Mono bloat.

And finally, Beagle - "A desktop search util for indexing and searching user's data. At the moment, it can index filesystems, Gaim logs, Evolution mail and data, RSS and other."  That would need an extra 35.1MB.  But, when I upgraded to 7.10, "Gutsy Gibbon", I found I got this thing called Tracker instead, which sounds like it does much the same thing, but without the Mono bloat.

Mono really doesn't sound worth it from the small list of dependent packages you gave.  Even putting them all together, they'd take up an extra 65.6MB - for just four applications?!?!?

We can do better than emulate Microsoft bloat.  Let's just ditch the blubber, and reduce Novell-Microsoft FUD opportunities at the same time :D

A) You still have no shown that there is any reason to remove Mono. 

B) I'm totally serious Mono is great technology, I'm also serious about the fact that you nor anyone have actually showed the patent you think is infringed upon. I'm also serious about the fact that the policy of Mono being a community project funded in part by Novell is to workaround or defeat any patent concerns which are substantiated by evidence. And finally I'm serious about the OIN being a source of protection from any patent suit not just against Mono but against our entire stack, incidently Novell amongst many other companies donated both funding and patents to this foundation.

C) Just because you don't like these applications doesn't mean it's an argument to remove Mono. I personally use Banshee on a daily basis, it's the single most stable media player I have ever used and the iPod syncing is most functional I've been able to use (though not perfect). New technologies like the Mirage plugin is only found in Banshee and more such innovative stuff is being worked on precisely because Mono makes it easy to focus on making better applications. I also use Beagle, it works better than Tracker does for me, it does more - it uses a tiny bit more memory but that is a solvable issue regardless I have 2GB, on my current setup it is not a problem - I could see more pressing issues to fix such as getting Xesam hammered out and have applications using it, that way you could pick which indexing framework to use and they could actually become really useful instead of just being souped up desktop searching.

Mono stays till you show evidence to the contrary, untill such a time you are only helping the Microsoft FUD machine by doing their work for them proactively. If Microsoft wants Mono gone they will have to do it themselves not that they have any reason to do so, they would be attacking their own customers and hurting adoption of the .NET framework by doing so. So please, pretty please, just stop and think.

---

### Post by BungaMan on 2007-10-30
The idea in itself is pretty nice to have something cross-platform that runs without recompiling on all systems.  However, it is a *** Microsoft product because they filed only a part of the .NET framework for standardization.  Conveniently leaving out System.WinForms etc.  Microsoft has always tried to manipulate standards in a way that they offer a better, beyond the standards version to prevent cross-platform.  The .NET framework is no exception to that.  What Microsoft does hope for is that there will be implementations in Mono that will violate patents and allow to sue its users.  Close co-operation between Icaza, Novell and Ms developers certainly make it likely enough to happen.

What Icaza has developed so far is very nice, but no thank you.

---

### Post by Sisophon2001 on 2007-10-30
> **BungaMan said:**
> The idea in itself is pretty nice to have something cross-platform that runs without recompiling on all systems.  However, it is a half assed Microsoft product because they filed only a part of the .NET framework for standardization.  Conveniently leaving out System.WinForms etc.  Microsoft has always tried to manipulate standards in a way that they offer a better, beyond the standards version to prevent cross-platform.  The .NET framework is no exception to that.  What Microsoft does hope for is that there will be implementations in Mono that will violate patents and allow to sue its users.  Close co-operation between Icaza, Novell and Ms developers certainly make it likely enough to happen.

What Icaza has developed so far is very nice, but no thank you.

I doubt that any code in Linux uses the portions of mono that have not been files for standardisation. Certainly not the System.WinForms stuff that still has layout bugs. All the code I have seen uses gtk++ for GUI. Mono is an implementation of C#, and C# is no different than C++ in  that it is an ISO standardised language, free for everybody to implement. Mono is just one implementation, and there are others if you prefer them (DotGNO + Portable.NET).

Garvan

---

### Post by Simon G Best on 2007-10-30
Wow, gnomeuser, you really badly misunderstand this stuff.

> **gnomeuser said:**
> A) You still have no shown that there is any reason to remove Mono.

That sounds the wrong way round to me.  Shouldn't it be a question of whether or not there's sufficient reason to *include* things?  Basically, lack of sufficient reason for including it is reason enough to remove it.  And there are also the reasons I've already offered.

Again, a lot of bloat (65.6MB) for a handful of applications that have mostly (if not entirely) duplicated functionality seems like a good reason to drop Mono.  That space can be used by less wasteful stuff providing more functionality.

Also, again, it avoids needlessly playing into Microsoft's hands, but more on that below.

> B) I'm totally serious Mono is great technology.

That's yet to be seen.  So far, it looks like a copy of Microsoft bloatware.  It might be useful for porting .NET-dependent software that fell foul of Microsoft's well-known vendor lock-in ways, but other than that, it doesn't seem worth it.  If your tiny list of example applications is representative, it's clearly a waste of space.

> I'm also serious about the fact that you nor anyone have actually showed the patent you think is infringed upon.

That's really misunderstanding the game.  It's not really a matter of whether or not Microsoft actually has the patents it would have people believe it has.  It's a matter of Mono being used by Microsoft as a vehicle for creating FUD.  If we needlessly include Mono in every and any distribution, Microsoft gets to do more of its patent sabre-rattling - and for what gain to us?  Not much at all.  Ditching Mono is a cheap and effective way of dealing with some of that FUD.  Including Mono is a needless way of helping Microsoft to FUD.

> I'm also serious about the fact that the policy of Mono being a community project funded in part by Novell...

Ah, Novell.  The problem with Novell is they've already blown their reputation by doing their dodgy, GPL-evading and FOSS-disrespecting deal with Microsoft.  They're clearly not trustworthy.  They've already betrayed FOSS, so it's too late to harp on about all the good things they've supposedly done and are supposedly doing.

> C) Just because you don't like these applications doesn't mean it's an argument to remove Mono.

That's misconstruing my point.  I didn't even say I disliked them anyway, did I?  My point was that most, if not all, of the functionality is already provided by other, Mono-free software.  But for those who really do prefer the applications you mentioned, you could still have those applications in the community-supported repositories anyway.  Indeed, looking at Synaptic, it appears that Banshee already is!  Would it really be so terrible for you if the other three applications you listed were to join it?

> I also use Beagle, it works better than Tracker does for me, it does more - it uses a tiny bit more memory but that is a solvable issue regardless I have 2GB, on my current setup it is not a problem...

Uh, you're making it sound like you need a huge amount of RAM for Beagle to be usable!  Did you mean to do that?  It's making it sound terribly bloaty and wasteful - rather like Windows Vista ;)  Really, 2GB is a huge amount of RAM.  1GB is large.  One of the benefits of stuff like Ubuntu is supposed to be that it's not nearly as wasteful of computing resources as Microsoft stuff is.  I get the impression that you don't really understand that, yet.

(Actually, I regard FOSS as still tending to be somewhat wasteful.  I believe there's a lot of room for improvement.  It's not as bad as Microsoft stuff, but I do believe it could still be a lot, lot better.  Perhaps, then, it's not surprising that I use Xubuntu :) )

> Mono stays till you show evidence to the contrary, untill such a time you are only helping the Microsoft FUD machine by doing their work for them proactively. If Microsoft wants Mono gone they will have to do it themselves not that they have any reason to do so, they would be attacking their own customers and hurting adoption of the .NET framework by doing so. So please, pretty please, just stop and think.

Wow, you really don't understand this stuff.  Microsoft doesn't want "Mono gone", they want it to stay!  They want it in basically as many Linux-based systems as possible, so that they can then apply their FUD accordingly.  They actually want Linux-based systems to seemingly infringe their claimed patents.  It's fundamental to their patent-based FUD efforts.  It's part of how they try to deter people from moving to Linux-based systems (except, perhaps, things like Novell's SuSE).  Without Mono in Ubuntu, etc, Microsoft don't have that FUD opportunity.  Adding Mono to Linux-based systems is what's doing Microsoft's work for them.

---

### Post by gnomeuser on 2007-11-01
Simon, you are commiting a logical fallacy, the burden of proof is on the claimant. You have the burden of proof with regards to showing that Mono infringes on any patents. 

Till you get such basic debating skills worked out I think this debate it dead. 

Show me a single patent and I will refute it, work around it or if need be concede my point like any honest person would.

---

### Post by Simon G Best on 2007-11-01
This is silly now.  But if you want to play games of sophistry...

> **gnomeuser said:**
> Simon, you are commiting a logical fallacy, the burden of proof is on the claimant.

Interesting.  Let's see if you're consistent with yourself on that.

You claim:-

> You have the burden of proof with regards to showing that Mono infringes on any patents.

Prove it.  Prove that I have "the burden of proof with regards to showing that Mono infringes on any patents."  Prove your claim.

It's a claim I dispute for the following reasons.

Firstly, alleged patent infringement need not be the only reason for removing Mono.  It need not even be a reason for removing it, as there could be other good reasons for removing it.  I've already given the needless bloat reason for removing it, but, significantly, you've completely ignored that reason.  *That leaves my needless-bloat-based argument standing.*

Secondly, as I've previously pointed out, it's not a matter of whether or not there's sufficient reason to *remove* a piece of software, but whether or not there's sufficient reason to *include* it in the first place.  Or, to put it another way, the initial claim, implicit in Mono's inclusion - and which you're supporting - is that Mono should be included.  *You're yet to adequately justify that claim.*  I've already argued that there isn't sufficient reason to include the bloat of Mono, and that there isn't sufficient reason to play into Microsoft's FUD hands.  *It is interesting that you've completely ignored these points, leaving them standing.*

Thirdly, patents don't work that way anyway.  They apply whether a third party (me) proves they apply or not.  With patents, the obligation is with the potential infringer to respect and not infringe the patent.  So, if the burden of proof here lies with either of us, it lies with you.  You'll have to prove that including Mono wouldn't infringe, or induce infringement of, *any* relevant patents, whether they're held by Microsoft or not.  That's pretty much how patents are, I'm afraid.

Fourthly, you're calling on me to identify which, if any, patents are relevant, *even though Microsoft prominently refuses to publicly specify which, if any, patents are relevant.*  That vagueness, that lack of specificity, not only in which patents would allegedly be relevant, but also in which pieces of FOSS would supposedly be affected, is a basic part of Microsoft's patent FUD game.

You really do seem to be quite ignorant of the nature of Microsoft's patent FUD, and the special place that Mono, Novell and Miguel de Icaza have in it.  Microsoft wants to have people *Fear* possible patents, to be *Uncertain* as to what the truth is, and to have *Doubts* about FOSS.  As Mono is basically a copy of .NET, Mono is itself a key vehicle for carrying such (ptential) FUD into Linux-based systems such as Ubuntu.  Miguel de Icaza might have his own reasons for wanting Mono everywhere, but that doesn't mean he isn't playing into Microsoft's hands.

And Novell, his employer, have already done their dodgy, FUD-using deal with Microsoft anyway.  There really is good reason to regard Mono as (probably) being tainted and as coming from an untrustworthy source.

Ignoring these points isn't going to make them go away.

> Till you get such basic debating skills worked out I think this debate it dead.

Just as debating skills, or lack thereof, can't make the blue sky green, your sophistry isn't going to justify including Mono.  Just give it up.

---

### Post by Redth on 2007-11-01
I'm going to intentionally give my input from a very personal perspective.  This means disregarding any other points outside my own interest.  I know I share the same thoughts as at least a few other people.  Here it goes:

I'm by nature a windows user (I don't say enthusiast for a reason).  I don't especially feel loyalty to it, or love it, but I love a few things that run on it, that have kept me using it.

I've been coding C# for years and years, and before that, VB.NET, and before that VB.  I've spent several years coding java and c/c++ out of necessity (school mostly), and I wouldn't trade C# for Java any day of the week.  C# is just a much nicer language to code with, and .NET and Mono feel so much less slow/clunky than java.  

I'd love a better operating system than windows.  Ubuntu can be that OS, or OSX.  Right now I'm almost leaning towards OSX (besides its dependency to specific hardware) simply because there aren't a whole lot of users of OSX who will do anything in their power to keep the OS hard to use, and a monopoly on technologies.  I know you're not necessarily advocating stopping the mono project, simply making it an optional inclusion in ubuntu instead.  Quite frankly I wouldn't care either way, as long as I have the option to install it (heck, you have to install Sun's java after the base Ubuntu install if you really want it).  

I guess my point is, as a windows user looking to make a final push towards using Ubuntu (I've tried this every time a new Ubuntu has come out, since before 6.xx) on my desktop as my primary OS.  Mono is something I will be using and will be developing for.  It's something I'd love to see stay included in Ubuntu, Mono is a BIG draw to linux for me, without it, I wouldn't even consider.

---

### Post by Simon G Best on 2007-11-01
> **Redth said:**
> I know you're not necessarily advocating stopping the mono project, simply making it an optional inclusion in ubuntu instead. Quite frankly I wouldn't care either way, as long as I have the option to install it (heck, you have to install Sun's java after the base Ubuntu install if you really want it).

Yes, having it in a community-maintained "universe" repository would be fine.  That way, those who want to easily install it and use it (as well as dependent software) can do so, without Ubuntu itself (the official distribution) being, as it were, "contaminated" with it.

:)

---

### Post by Hairy_Palms on 2007-11-01
ive said this before on these forums, i see no reason to assume mon has any patent problems,
but the simple fact is most apps of reasonable complexity written in mono are bloated, banshee especially, they are noticeably slower to load than other apps and use on average double the memory of equivalent native apps.
F-spot is the one mono app that has any debatable reason being better than the competition, 
Banshee is f*cking awful, bloated slow and buggy as hell, it still whores ram after being left to run for any length of time but those bugs seem to be ignored, especially using its playlists cause numerous crashes. 
gnome panel already has sticky notes built into it, so tomboy isnt needed by default, and beagle is on an equal footing with tracker at the moment, but beagle has had a much longer development period. tracker will surpass it before hardy i surmise.
so to surmise dont care about patents, but mono has no compelling reason to be included by default, and installing 70MB of runtime for f-spot and the few advantages it has over the alternatives isnt worth it.

P.S. also to whovever said there only implementing standards obviously hasnt been following their development of VB.net and ASP.net technologies, which are not standards.

---

### Post by mangar on 2007-11-01
From my point of view, the problem was not the unproved, potential patent problem, but the ~60mb mono takes on the install CD, and having it as a ubuntu-desktop dependency.

---

### Post by T_W on 2007-11-01
REMOVE.  

I migrated from beagle to tracker with Gutsy.

Its amazing how much faster and efficient tracker is over beagle.

I have no interest in F-Spot or Tomboy and don't want this risky tech on my system.

---

### Post by pay on 2007-11-02
> **Simon G Best said:**
> Ah, Novell.  The problem with Novell is they've already blown their reputation by doing their dodgy, GPL-evading and FOSS-disrespecting deal with Microsoft.  They're clearly not trustworthy.  They've already betrayed FOSS, so it's too late to harp on about all the good things they've supposedly done and are supposedly doing.Novell have contributed alot to open-source. Right now they are developing an open source radeonhd driver, they have a few kernel hackers hired to develop linux drivers for companies for free, app armour and evolution. All these products are used or will be used in Ubuntu. I think that they made one bad choice but who knows, there could be some good that comes out of it. Only time will tell..

---

### Post by kragen on 2007-11-02
Chirst Simon G... do you feel like spreading any more fear today? Perhaps you can start a thread on how Ubuntu shouldnt include Open Office - after all Microsoft seem to think that violates 42 patents.

Mono are probably one of the projects least likely to infringe patents - after all they are emulating a Microsoft technology - if you think they do infringe patents, then go ahead and prove it, otherwise, stop causing a fuss.

IMO if we can get .Net applications running reliably under linux, that would be awesome - stop causing problems needlessly.

Oh - and it might not be upto you to give a good reason to remove it, but it is up to you to give a good reason to *include* gThumb, and if your reasons for including gThumb are to remove Mono, then surely you DO need to give a decent reason to remove Mono for your argument to hold any weight.

---

### Post by drf_av on 2007-11-02
Remove. Mono is heavy and I agree with Simon. It's not a matter of patents, Mono it's Microsoft technology. And if I wanted to use Microsoft technology, I'd use Windows instead.

---

### Post by kragen on 2007-11-02
Fine - uninstall Mono on your computer, but I dont think your anti-Microsoft hate-war is a real reason to change 2 default apps - it certainly does nothing to help the user experience.

---

### Post by st4rdr1ft3r on 2007-11-02
also java is heavier than mono

---

### Post by Corbelius on 2007-11-02
LOL! again this story? ](*,)

Mono is OPEN. Mono is based on ECMA standard. Mono is better than of Java and Python.

> **drf_av said:**
> Remove. Mono is heavy and I agree with Simon. It's not a matter of patents, Mono it's Microsoft technology. And if I wanted to use Microsoft technology, I'd use Windows instead.
[B]
Ok, then remove UPnP, USB, SMB[/B] and others... their are Microsoft tecnologies :roll:

> **Simon G Best said:**
> enough to remove it.  And there are also the reasons I've already offered.

Again, a lot of bloat (65.6MB) for a handful of applications that have mostly (if not entirely) duplicated functionality seems like a good reason to drop Mono.  That space can be used by less wasteful stuff providing more functionality.


A simply java browser plugin required 80mb... :roll:

---

### Post by drf_av on 2007-11-02
Are you sure USB is Microsoft? And anyway, I don't like to rely on something that can actually damage us. But maybe I'm wrong, time will tell. After all, if I don't want mono I can simply purge it. But, Corbelius, the point was not "Mono is heavier/lighter than java", the point was: Mono is heavy and it's on the install CD.

---

### Post by Hairy_Palms on 2007-11-02
> Mono is OPEN. Mono is based on ECMA standard. Mono is better than of Java and Python.
wrong, its only partly open, as soon as they started implementing asp.net and VB.net it is no longer entirely standards based, and besides weve all seen how much an ECMA standard is worth with the ridiculous OOXML spectacle.

> A simply java browser plugin required 80mb... 

a non-point, java isnt installed by default, and thats what the problem is,  its slower and has more overhead than the native apps that are perfectly good enough to replace them, without needing runtime environments that are one tenth of a 700MB disk

though i feel obliged to add, being microsoft technology doesnt make it bad. if you want mono install it by all means, but it should NOT be default.

---

### Post by st4rdr1ft3r on 2007-11-02
python and mono basic runtime environments are similar in size actually. python weighing in at 16.3mb and mono at 17.7mb.

---

### Post by soc on 2007-11-04
Remove.

In my personal opinion, it's not the question if Mono violates patents or not.
It's a simple matter of TRUST.
Why the hell should I trust Novell/Icaza? There is no single reason to do that, except foolish naivity.

Remember Icaza's "It's OK, as long as you download it from our Novell servers"!?

From a more general point of view, it's just ridiculous if we include the copy of a copy (.NET) and leave out the original (JAVA), which is being GPL'ed at the moment. (=company showing real interest in/supporting open source)

Remove Mono, and make it available like Java in the repos, for those MS shills and Icaza fanboys who want to play with it.

At least we would have the chance to include more useful things like build-essential, more printer drivers, more scanner firmware in the next release.

The next release will have LTS, so no place for mono in it.

---

### Post by st4rdr1ft3r on 2007-11-05
how is build-essential more useful for the general user?

---

### Post by drf_av on 2007-11-05
build-essential IS useful. Now suppose that you need to compile latest ndiswrapper to make your wireless card work = you have no internet. I don't think Mono will help you out. And anyway, compiling stuff from source is always useful.

---

### Post by mangar on 2007-11-05
That space can be used for including:

1. Elisa or Freevo - out of the box media center support.
2. Wine - for compatibility with legacy code.
3. Kino or pitivi - for home video editing.
4. inkspace - to complement Gimp.
5. propriety drivers - for out of the box 3d acceleration support.
6. screenlets, compiz fusion, gnome-launch-box, specto, gclipper, tilda, avant windows navigator, cairo-clock, xdekstopwaves, etc.

In short, there's no shortage of possible uses for the space that is currently used to include a note-taking applets, and a (meh) photo collection manager.

---

### Post by smartboyathome on 2007-11-05
> **mangar said:**
> That space can be used for including:

1. Elisa or Freevo - out of the box media center support.
2. Wine - for compatibility with legacy code.
3. Kino or pitivi - for home video editing.
4. inkspace - to complement Gimp.
5. propriety drivers - for out of the box 3d acceleration support.
6. screenlets, compiz fusion, gnome-launch-box, specto, gclipper, tilda, avant windows navigator, cairo-clock, xdekstopwaves, etc.

In short, there's no shortage of possible uses for the space that is currently used to include a note-taking applets, and a (meh) photo collection manager.

I don't agree that just because Microsoft uses .Net, then we shouldn't include it. That is like saying we shouldn't include the ability to use a touble click, or "Start button", because that was done by Microsoft. :rolleyes:

Though the space could be used for other apps. Ones I think about are glipper (like you said), screenlets, and drivers. I don't agree with Kino/Pitivi (that is what UbuntuStudio is for), or Inkscape (same), or Wine (too fast for development).

> **drf_av said:**
> build-essential IS useful. Now suppose that you need to compile latest ndiswrapper to make your wireless card work = you have no internet. I don't think Mono will help you out. And anyway, compiling stuff from source is always useful.

To most users, compile isn't THAT useful, as they will look around for a debian package or give up because they won't want to touch the terminal.

---

### Post by mangar on 2007-11-05
I really don't care about microsoft's potential patents. My only concern here is the space Mono takes on the install CD, that can be better used.

---

### Post by 23meg on 2007-11-05
The poll results are intriguing.

---

### Post by gnomeuser on 2007-11-06
> **23meg said:**
> The poll results are intriguing.

How so, we have 50% wanting to gut Ubuntu based on assertions of evidence which they do not produce. The other 50% argue to keep Ubuntu a diverse environment filled with good applications and they will allow equal space for each app and framework, method of development succeed on equal starting ground.

Frankly I'm frightened at the illogic going on here but the levels seem to reflect my view of the situation is a wider scope. A great deal of the debate seems to be closed off by closed minded stonewallers who only display the effects having been whipping into a frenzy rather than letting them rationally examine the evidence and make a case for greatest common benefit.

I mean we see topics like remove mono, and when they dig at the arguments for this it goes back to this deal. Yet when pressed only a few people really dug into the details of what that deal means and the statements made before and after by in this case Mono as a Free Software project with hefty community involvement.

I mean if we are just out to hate on Microsoft, and I don't deny they did a lot of bad stuff in the past.. but look at them now, they got certain licenses that forfill the open source definitions and are certified as such. We banged on them for years to document their file formats something we then proceeded to give them a lashing for. Sure they still need to learn but remove Steve Ballmer who attacks us regardless of what the heck is going on. It could be raining donuts and strippers at Microsoft HQ and he'd blame Linux for the pom poms not being sassy enough.

Now Novell are our friends, they are also a company, a company with a long history in the old 80's and 90's IT business model. They will comtinue to make deals, sadly they do not yet have a good grip of what kinds of deals will involve an emotional backlash. Novell also have really poor advocacy, they are really bad at having their projects and technologies getting the exposiour they deserve. A lot of cool stuff is going on at Novell, I'm fortunate to know certain of the people, I know where to go to figure out what's coming up. But they never frikking tell anyone, they don't go out and use the fact that they are pouring millions and millions into Linux. They are good citizens, they're not perfect, but your desktop works better because Novell helps make it that way by providing you the code Ubuntu packages up. Take just recently when we celebrated the demise of SCO, the day Novell got the statement that they were the true owners of the UNIX name, they issued a statement that they would never leverage that license against Free Software. Why don't we remember the good stuff?

I feel somewhat like that scene in Life of Brian.. what did the Romans ever do for us. Well what has Novell done for us, invested their business in their code completely (nobody should be kidding themselves, Novell cannot go back to being the close source netware vendor they used to be), they invested their cash in open development, they lend us their name to throw around when increasing awaeness of Open Source (much like Red Hat, Intel, AMD, IBM and many others do as well). They bring us expertise in design and usability, they have testing facilities to get real user feedback and they know how to do those tests and write them up for analysis. They are a founding member of the OIN. Before and after the deal Novell continues to pump millions into development that benefits everyone. 
Novell are on the scale, good guys, they made a few missteps but the overall total harm has by far been caused by our overreaction to what we might feel as the violation of our trust, the actual deal so far has had good and bad impacts - the worst to me is that for no good reason a fine framework is discriminated against for yet another debunked reason.

So no an equal spread is not interesting, it's just scary. An equal spread on the question "Hitler, innocent and cuddly like a baby rabbit" would be.

---

### Post by 23meg on 2007-11-06
[QUOTE=gnomeuser]So no an equal spread is not interesting, it's just scary.[/QUOTE]

I meant to say it's thought-provoking; not interesting in the "good" sense.

---

### Post by Simon G Best on 2007-11-06
> **gnomeuser said:**
> How so, we have 50% wanting to gut Ubuntu based on assertions of evidence which they do not produce. The other 50% argue to keep Ubuntu a diverse environment filled with good applications and they will allow equal space for each app and framework, method of development succeed on equal starting ground.

Not exactly spinning the results, there, are you?

And why are you ignoring the issue of wasteful bloat?  You say, "we have 50% wanting to gut Ubuntu based on assertions of evidence which they do not produce", even though I've already given results I got from Synaptic as evidence of wasteful bloat.  Why are you ignoring that issue?

> A great deal of the debate seems to be closed off by closed minded stonewallers who only display the effects having been whipping into a frenzy rather than letting them rationally examine the evidence and make a case for greatest common benefit.

"Rationally examine the evidence" of wasteful bloat, then, "and make a case for greatest common benefit", instead of ignoring that issue.

As we've already said, Mono takes up a lot of space for not much benefit.  That space could be freed up, and better use could then be made of it.  And for those who do want Mono, well, it can still be community maintained stuff in a "universe" repository.

> I mean if we are just out to hate on Microsoft, and I don't deny they did a lot of bad stuff in the past.. but look at them now, they got certain licenses that forfill the open source definitions and are certified as such. We banged on them for years to document their file formats something we then proceeded to give them a lashing for. Sure they still need to learn but remove Steve Ballmer who attacks us regardless of what the heck is going on. It could be raining donuts and strippers at Microsoft HQ and he'd blame Linux for the pom poms not being sassy enough.

You're sounding like a bit of a Microsoft apologist, there.  Or are you just *really, really naive* about Microsoft?

> Now Novell are our friends,

Really?

> they are also a company, a company with a long history in the old 80's and 90's IT business model. They will comtinue to make deals, sadly they do not yet have a good grip of what kinds of deals will involve an emotional backlash. Novell also have really poor advocacy, they are really bad at having their projects and technologies getting the exposiour they deserve. A lot of cool stuff is going on at Novell,

Now you're sounding like some sort of a Novell apologist.  Can I ask: what, if any, relationship do you have with Novell?  Or Microsoft?

> I'm fortunate to know certain of the people,

Does that include Miguel de Icaza?

> I know where to go to figure out what's coming up.

Do you mean you're some sort of "insider", or something?

> But they never frikking tell anyone, they don't go out and use the fact that they are pouring millions and millions into Linux. They are good citizens, they're not perfect, but your desktop works better because Novell helps make it that way by providing you the code Ubuntu packages up.

Do you do paid marketing/PR work for Novell, by any chance?  Or unpaid marketing/PR work?

> Take just recently when we celebrated the demise of SCO, the day Novell got the statement that they were the true owners of the UNIX name, they issued a statement that they would never leverage that license against Free Software. Why don't we remember the good stuff?

Actions speak louder than words.  They might say they're friends of FOSS, but their dodgy deal with Microsoft demonstrates otherwise.

But none of this changes the fact that Mono is wasteful bloat.

---

### Post by smartboyathome on 2007-11-06
> **Simon G Best said:**
> Not exactly spinning the results, there, are you?

And why are you ignoring the issue of wasteful bloat?  You say, "we have 50% wanting to gut Ubuntu based on assertions of evidence which they do not produce", even though I've already given results I got from Synaptic as evidence of wasteful bloat.  Why are you ignoring that issue?



"Rationally examine the evidence" of wasteful bloat, then, "and make a case for greatest common benefit", instead of ignoring that issue.

As we've already said, Mono takes up a lot of space for not much benefit.  That space could be freed up, and better use could then be made of it.  And for those who do want Mono, well, it can still be community maintained stuff in a "universe" repository.



You're sounding like a bit of a Microsoft apologist, there.  Or are you just *really, really naive* about Microsoft?



Really?



Now you're sounding like some sort of a Novell apologist.  Can I ask: what, if any, relationship do you have with Novell?  Or Microsoft?



Does that include Miguel de Icaza?



Do you mean you're some sort of "insider", or something?



Do you do paid marketing/PR work for Novell, by any chance?  Or unpaid marketing/PR work?



Actions speak louder than words.  They might say they're friends of FOSS, but their dodgy deal with Microsoft demonstrates otherwise.

But none of this changes the fact that Mono is wasteful bloat.

You can't say that it wastes bloat for nothing, as the stuff that you say wastes bload actually does something. Also,when I try to remove Tomboy and F-Spot, it says only 14 MB will be freed. How can that be very much space?

---

### Post by Simon G Best on 2007-11-06
> **smartboyathome said:**
> Also,when I try to remove Tomboy and F-Spot, it says only 14 MB will be freed. How can that be very much space?

Did you remove the many Mono packages as well?  I bet you didn't!

Let's see...

In Synaptic, when I select F-Spot and Tomboy for installation, it says, "46.7 MB will be used".  It also says there are 31 packages to be installed, because of all those Mono packages that F-Spot and Tomboy depend on as well.

Then, when I unmark F-Spot and Tomboy, it still leaves 29 packages to be installed, saying, "30.9 MB will be used".

That means, on my system, if I had F-Spot, Tomboy and Mono installed, and then I uninstalled F-Spot and Tomboy (but leaving Mono installed), I'd only free up 15.8 MB (similar to your 14 MB).  Removing all that Mono stuff as well, I'd free up another 30.9 MB, bringing the total up to 46.7 MB.

46.7 MB for F-Spot and Tomboy.

Is it worth it?  46.7 MB seems like a lot of space for just those two things.

---

### Post by st4rdr1ft3r on 2007-11-06
and the general user is going to understand how to do this...

---

### Post by smartboyathome on 2007-11-06
> **Simon G Best said:**
> In Synaptic, when I select F-Spot and Tomboy for installation, it says, "46.7 MB will be used".  It also says there are 31 packages to be installed, because of all those Mono packages that F-Spot and Tomboy depend on as well.

Then, when I unmark F-Spot and Tomboy, it still leaves 29 packages to be installed, saying, "30.9 MB will be used".

That means, on my system, if I had F-Spot, Tomboy and Mono installed, and then I uninstalled F-Spot and Tomboy (but leaving Mono installed), I'd only free up 15.8 MB (similar to your 14 MB).  Removing all that Mono stuff as well, I'd free up another 30.9 MB, bringing the total up to 46.7 MB.

46.7 MB for F-Spot and Tomboy.

Is it worth it?  46.7 MB seems like a lot of space for just those two things.

Ok, I opened it up and tried looking at removed every mono-related library in it, and it said that 30.9 mbs would be freed. But some of the libraries were GNOME libraries.

---

### Post by drf_av on 2007-11-07
no. Type sudo apt-get remove --purge libmono0. You won't break anything in gnome.

---

### Post by Simon G Best on 2007-11-07
> **smartboyathome said:**
> Ok, I opened it up and tried looking at removed every mono-related library in it, and it said that 30.9 mbs would be freed. But some of the libraries were GNOME libraries.

Stuff like libgnome2.0-cil, yeah?

From Synaptic:-

libgnome2.0-cil: "CLI binding for Gnome 2.16".  "This package provides assemblies that allow CLI (.NET) programs to use the Gnome and GnomeUI libraries 2.16."

So it's not actually a part of Gnome.  It's just so that "CLI (.NET) programs" - Mono - can use the Gnome libraries mentioned.  So, if you're not going to have Mono on your system, you won't need this package.

Much the same goes for libgnome-vfs2.0-cil, too, and other such "CLI binding" packages.

:)

---

### Post by drf_av on 2007-11-07
I notice that removing in libmono in Gutsy doesn't actually even break any metapackage.

---

### Post by Joh_ on 2007-11-07
> **drf_av said:**
> build-essential IS useful. Now suppose that you need to compile latest ndiswrapper to make your wireless card work = you have no internet. I don't think Mono will help you out. And anyway, compiling stuff from source is always useful.
Yeah, cause the average user would know how to compile ndiswrapper....

I really don't get what the issue is here tbh. I remember Ubuntu's slogan being "linux for humans" (unless it's changed) and it being aimed at the average computer user, not the techies. 52 year old Karen most likely won't know how to install F-Spot to manage her photos since she doesn't know she has to enable the universe repository for Mono. The thing that makes Ubuntu Ubuntu is it's ease of use and everything one might need comes pre-installed and when deciding what should be on the disk and what shouldn't, you should think about the end-users. The techies are the ones who will customize their installation to oblivion and as such, obviously they could uninstall Mono if they prefer to. However, the non-techies would rather have Mono installed by default and since they aren't as much into configuring and customizing (generally speaking), those are the ones one should go by.

I'd personally rather see Python go since I don't use any Python-apps and have a serious dislike for interpreted languages, but you don't see me nagging about it. Also, saying that it takes up too much place on the CD is a lame excuse. On my feisty-disk (couldn't find the gutsy one), the mono packages takes a grand total of 12.4 MB. You can't possibly say that's too much, or "one tenth of a 700MB disk".

On a last note, you make it sound like there are only 4 applications that use Mono. There's a [short list over at mono-project.com](http://www.mono-project.com/Software) of other software that uses it and that's not even complete.

---

### Post by amano on 2007-11-07
Well. This is one of the things that I changed my mind, but I cannot change the poll anymore.

Since neither Tomboy nor F-Spot are essential applications for a running system (F-Spot doubling some EOG and gThumb functionality) they don't need to be installed by default and thus shipped on the CD. And in conclusion Mono isn't needed on the CD either.

The space could probably be used in better ways, eg. offering more device drivers (the priority should be internet connection devices like usb modems and wlan devices since you cannot get drivers without a working connection).

I think that mono is a great and easy framework and more and more applications will use it, but at the present time it is not essentially needed and thus should be left out of the install disc. Installing it is easy enough.

This would be in line with  the Ubuntu philosophy to just ship a very basic system. And neither Tomboy nor F-Spot care for really basic needs and without them mono isn't needed either.

---

### Post by drf_av on 2007-11-08
> **Joh_ said:**
> Yeah, cause the average user would know how to compile ndiswrapper....


I think you don't get the point. First of all, compiling stuff from source isn't that hard. You have to issue 3 commands from terminal and, in case of ndiswrapper, you don't evn need to install anything else. And if you search in the forums or in the web you'll find a lot of guides. So please, if you really want to defend Mono, don't put it in comparison with build-essential. It is needed on CD until we get drivers working and ready to go on first install. While, as pointed somewhere else here, Mono apps aren't that useful (we speak of the average user, right? I bet half of Ubuntu's users don't even know what Tomboy is all about. I never knew about it before i was uninstalling it with Mono), and if you look around, there are a lot of alternatives (ok, maybe for F-Spot you need to search a bit deeper) non-Mono based.

---

### Post by sq377 on 2007-11-08
I'd like to see it removed.  All of the mono programs I've used seem really bloated.  Eye of Gnome with an image open, 9.0 MB.
F-spot with an empty database of images, 25.5 MB.

I realized f-spot has a bit more functionality, but for me it isn't worth the space and memory required to run it.  Maybe if mono becomes big enough that more applications use it, then it will make more sense.

I saw someone said we should remove python, and out of curiousity i typed into apt to see what I would get.
"WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  python-minimal python2.5-minimal (due to python-minimal)
0 upgraded, 0 newly installed, 336 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 920MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'"
I found this a bit funny, but so much depends on python it's just not even feasable to remove it.

Keep mono in the repositories, but It should not be installed by default while the space could be used better.

---

### Post by jARLAXL on 2007-11-08
i started watching the discussion because i saw some threads about mono and the .net applications.

i could call myself something less than average user (if you count that i know nothing about scripting except some matlab-proprietary code-if that counts and that i am a totally noob) so i decided to write my opinion as an average user and nothing more or less though it is not the opinion of every average user i guess. its just my opinion.

though i have an opinion about the icaza case i dont think that my opinion is very important. but i am telling you from now that if i didnt have that opinion i wouldn't vote at all just because i wouldnt check out this thread . thus i think that you will be mistaken if you try to make conclusions such as he says this because he is positive/negative about this matter.

ok so there is some software to remove or not. i dont even know what is mono precisely but as far as i got concerned the only application that i am using from mono is tomboy notes and this actually was before i decided to switch to the right click-->create document-->empty file "application"; well now i saw its the gedit editor.

apart that i guess that there are people who  love some apps out of it. to get to the point straightly and since average user was mentioned, here is my point of view:
i think that the most important applications for an average user and therefore for a user who is interested to switch into linux (if thats what it is wanted) are the ones that are most critical for their working environment. because no matter of what, everyone wants to have his/her job done well (though i dont agree with this point-that jobs should be done well- but this is another kind of topic.if you still want a clue:every job is proprietary and owned by boss).

so most users are concerned with the point:: "will i be able to  have compatibility with M$ office that 90% of people use it?" and this is an example from my experience from people that are willing to switch to linux for any reasons (among them: its simpler ,faster, reliable-all these are what they heard about). but the question remains how compatible are we with M$ users who are all around us and our job depends on it? and to tell you frankly i send them a copy of .doc document  from openoffice.org and a copy of pdf from openoffice.org as well so that they can compare.

i wouldnt say all these things if i didnt see in this thread that wine is an alternative to mono.

so in other words if it is really to be decided that something should be replaced then it should be said what is it to be replaced by..

there may be many things but what is best to replace with?

for my opinion some office compatibility software (specially the text editor and spreadshit and maybe database editor==wine?) is the best choice. though i have to admit i know nothing about wine as i am not using it at all.

apart that i am about to convert all mp3s to ogg and whoever sends me a .wmv or .avi gets a response like: please never send me junk again just because i dont like ugly codecs in my box. and nobody cares about that. they simply understand.

so thats my humble opinion about this topic. maybe i am wrong.

P.S. Removing mono doesnt mean that you cannot use it any more. just after you install k/x/ubuntu you just have to go -->system-->administration--->synaptic  (enter your pwd)--->search your favorite mono application or all of them check them to be installed and the press apply and confirm. i think an average user is able to do that and definately all those who are stuck with .NET (though i know none) as well.except if you have pstn/isdn. well in that case i have no idea how you obtain your new copy of ubuntu.

---

### Post by smartboyathome on 2007-11-08
Wine is not an alternative to mono. I would like it to be, though, so I could install .NET apps with their .exe installers.

---

### Post by gnomeuser on 2007-11-09
Mono if packaged correctly can be as small as 5-8 megs, this is comparable to most of our software. 

If you remove Mono naturally you will save space, you're also removing user visible functionality - something like Tomboy is extremely popular. I could make the same argument for removing OpenOffice.org - we have GNOME Office (lacks a presenter but we could write one or depend on Google Present). There's also KOffice both options which is technically plenty sufficient for people to get work done in +90% of cases. 

I don't have stats handy for Ubuntu but I'm betting removing Openoffice and replacing it with the online apps via prism or a more traditional approach like GNOME Office or KOffice. Not only would we save +100 megs (estimated feel free to correct me with accurate measurements) but the applications at least in the case of GNOME Office are orders of a magnitude better performant and offers collaboration features unheard of in OpenOffice.

If you remove Mono you take away real useful programs, you regress functionality, you provide an upgrade path that introduces less functional apps with now way to convert your data. I doubt users will be pleased.

Aside bloat which is obviously bogus - given that you could make that argument about OpenOffice as well.. why use OpenOffice - GNOME Office or Google Office offers the same functionality. Why use Firefox, WebKit is smaller, faster, better integrated. Picking default applications is a tricky game, it's impossible to please everyone but removing Mono in this case makes no sense what so ever.

So what's left against Mono.. patents, yet nobody has EVER shown that Mono actually infringes. And yes that burden of proof is on their shoulders. [ This](http://richarddawkins.net/social/index.php?mode=article&id=35) small Carl Sagan essay beautifully illustrates the problem of having a reversal in burden of proof. Reality simply does not work in a manner where in assertion makes a statement truth. So please I will shut up about the patent if I see a shed of evidence for this vile and damaging unsupported accusation.

In the interest of full disclosure as I was asked: I don't work for Microsoft, I don't work for Novell - infact I don't professionally work for anyone currently. I am however fortunate to be a semi well known figure in the Free Software community as part of that engagement naturally people tend to get social and I have had the pleasure of making friends with a lot of interesting people. I don't especially care who signs their paychecks, I debate technology and advocacy with them - it's what they work on that's interesting more so than anything.

---

### Post by Simon G Best on 2007-11-09
> **gnomeuser said:**
> If you remove Mono naturally you will save space, you're also removing user visible functionality - something like Tomboy is extremely popular.

Is it?  Can you provide some links?

> I could make the same argument for removing OpenOffice.org - we have GNOME Office (lacks a presenter but we could write one or depend on Google Present).

Interesting you should bring up Gnome Office, which includes Gnumeric.  Miguel de Icaza, again.

> I don't have stats handy for Ubuntu but I'm betting removing Openoffice and replacing it with the online apps via prism or a more traditional approach like GNOME Office or KOffice. Not only would we save +100 megs (estimated feel free to correct me with accurate measurements) but the applications at least in the case of GNOME Office are orders of a magnitude better performant and offers collaboration features unheard of in OpenOffice.

So now you're trying to sell us Gnome Office ;)  And you're *guessing* how much space would be saved, too!  Are you also guessing when you claim that Gnome Office's performance is "orders of a magnitude better" than OpenOffice?  Can you actually back up such claims?  If not, I *guess* that would leave your claims unfounded and best disregarded.

> If you remove Mono you take away real useful programs, you regress functionality, you provide an upgrade path that introduces less functional apps with now way to convert your data. I doubt users will be pleased.

"with *now way to convert your data*" really sounds like some sort of lock-in thing, like vendor lock-in.  Such lock-in is bad.  What we surely want is interoperability instead.  But if such Mono-based software lacks such interoperability, locking users into that software, then it's best avoided in the first place.

Oh, and it really sounds like you're trying to FUD the issue, there, too.

And you still seem to be ignoring the fact that Mono can still be made available as community maintained software in a "universe" repository.  It's simply not true, therefore, that removing Mono, etc, from Ubuntu itself would actually deny users the opportunity to use such Mono-dependent software.  You do seem to like ignoring that point.  Why?

> So what's left against Mono.. patents, yet nobody has EVER shown that Mono actually infringes.

Has anyone in this thread actually claimed that Mono infringes *any* Microsoft patents?  Or any patents at all?

You do seem to like bringing up that straw-man, instead of actually answering the real points that have already been made on the issue.  I could repeat them in this post, but I suspect you'll just ignore them - again.

> In the interest of full disclosure as I was asked: I don't work for Microsoft, I don't work for Novell - infact I don't professionally work for anyone currently. I am however fortunate to be a semi well known figure in the Free Software community as part of that engagement naturally people tend to get social and I have had the pleasure of making friends with a lot of interesting people. I don't especially care who signs their paychecks, I debate technology and advocacy with them - it's what they work on that's interesting more so than anything.

On the matter of people you know in relation to this stuff, I also asked, "Does that include Miguel de Icaza?"  What, if any, connection do you have with him?  Are you involved, at all, in the development of Mono?

---

### Post by smartboyathome on 2007-11-09
If you don't want anything to do with Miguel de Icaza? If not, then why not remove all of GNOME? Surely, they have developed a lot of stuff in it. Also, we can't go to KDE, as one of the developers might have worked some on it as well. Whats left, DWM? :rolleyes:

Also, you keep asking people who oppose you if they have any connection to him. Seems like you think that everyone should agree, and if not, they will a connection with him. Seems there's an air of "Lets get rid of anything to do with Microsoft!" here. :(

---

### Post by gnomeuser on 2007-11-09
I have exchanged emails with Miguel around the time the Novell-Microsoft deal mainly to get his input on questions I had and to help arrange an episode of Novell Open Audio that dealt with the common questions I heard from people around me. That is aside bug reports the only times I've had the pleasure of talking to Miguel, he is both an interesting person and he has a grip of technology I admire so I really wish I could say I lend his ear on a regular basis but that is not the case.

I don't work on Mono (aside filling bug reports) and my extend of involvement with the Mono codebase is limited to having produced a few patches to some C# apps when I hit an obvious bug. I also maintain a few Mono packages for Fedora.

Regardless I fail to see how that is relevant, I'm a free software contributor I have been for years - I get to know the people, stick around for a decade and you're bound to make a few good friends.

---

### Post by Hairy_Palms on 2007-11-10
> So what's left against Mono.. patents, yet nobody has EVER shown that Mono actually infringes. And yes that burden of proof is on their shoulders.  This small Carl Sagan essay beautifully illustrates the problem of having a reversal in burden of proof. Reality simply does not work in a manner where in assertion makes a statement truth. So please I will shut up about the patent if I see a shed of evidence for this vile and damaging unsupported accusation.

The recent winforms implementation by mono for example, winforms is a patented microsoft technology, and unlike the C#/.net patents which are ECMA standards and therefore available, MS has never given anyone the right to use those patents so in theory by implementing them your infringing, but like most things in patent law, noone knows for a fact anything until it goes to court. like i said before personally its not the most important factor for me

But that combined with the fact that mono is still bloated slow technology, is what decides it for me, also as stated the gnome-panel has a sticky notes application built in, meaning tomboy is duplicated functionality, f-spot is the only program that should even be considered for default, and its not worth the 65-70MB (1/10th of a CD) needed to include f-spot by default.

---

### Post by emperon on 2007-11-10
C# and Core library of .NET framework is not a property of Microsoft. The only patented technologies are Windows Forms , ASP.NET and ADO.NET. You can definitely develop applications without those. And as long as you don't use these you are 100% safe.
And finally Mono is Open Source , Java is NOT (Java 7 has not been released which will then later be named Open Java or Open JDK and sun will also promote its own Java version )

taken from : [http://www.mono-project.com/FAQ:_Licensing](http://www.mono-project.com/FAQ:_Licensing)
Could patents be used to completely disable Mono?

First some background information.

The .NET Framework is divided in two parts: the ECMA/ISO covered technologies and the other technologies developed on top of it like ADO.NET, ASP.NET and Windows.Forms.

Mono implements the ECMA/ISO covered parts, as well as being a project that aims to implement the higher level blocks like ASP.NET, ADO.NET and Windows.Forms.

The Mono project has gone beyond both of those components and has developed and integrated third party class libraries, the most important being: Debugging APIs, integration with the Gnome platform (Accessibility, Pango rendering, Gdk/Gtk, Glade, GnomeUI), Mozilla, OpenGL, extensive database support (Microsoft only supports a couple of providers out of the box, while Mono has support for 11 different providers), our POSIX integration libraries and finally the embedded API (used to add scripting to applications and host the CLI, or for example as an embedded runtime in Apache).

The core of the .NET Framework, and what has been patented by Microsoft falls under the ECMA/ISO submission. Jim Miller at Microsoft has made a statement on the patents covering ISO/ECMA, (he is one of the inventors listed in the patent): here ([http://web.archive.org/web/200304241.../msg00218.html](http://web.archive.org/web/200304241.../msg00218.html))

Basically a grant is given to anyone who want to implement those components for free and for any purpose.

For people who need full compatibility with the Windows platform, Mono's strategy for dealing with any potential issues that might arise with ASP.NET, ADO.NET or Windows.Forms is: (1) work around the patent by using a different implementation technique that retains the API, but changes the mechanism; if that is not possible, we would (2) remove the pieces of code that were covered by those patents, and also (3) find prior art that would render the patent useless.

Not providing a patented capability would weaken the interoperability, but it would still provide the free software / open source software community with good development tools, which is the primary reason for developing Mono.

The patents do not apply in countries where software patents are not allowed.

For Linux server and desktop development, we only need the ECMA components, and things that we have developed (like Gtk#) or Apache integration.
With the new Novell/Microsoft agreement, will the patent policy change?

Mono is a community project, and as such, we will continue to implement the policy of not integrating knowingly infringing code into Mono.

And we will continue to follow the steps outlined in the previous topic if code that potentially infringes is found: finding prior art, finding different implementation techniques, or if none of those are possible, removing the code from Mono.

---------------------------------------------------------------------------------------
Programming languages are tools. And they give us some abstraction level. I would classify :

Language....................... Abstraction Level

Machine Lang........................ 0
Assembly.............................. 1
C/C++ ................................... 2
Java/C# .................................3
Python, Ruby .........................4
LISP ...................................infinity

We choose a language according the to task and level of abstraction we require. Writing an operating system with LISP is pointless where as, writing an ERP with assembly is pointless as well.

Most Projects fall into the category between level 4 and 3. The main difference between level 4 and 3 is about statically typing or dynamic typing.

With statically typed languages you have compiler as a cop , that checks your code for preliminary compile time mistakes. This is more useful when the project is very large and iti hard to maintain and/or the developers are novice.

With dynamic languages, the language gives the developer more power (at the cost of Performance) , so it is more suitable for when developers are smarter and/or Project is not very large to maintain.

What .NET brings table, this is highly personal. Mono (and not .NET) is the best of the best of all development environments FOR ME. because of the following reasons:

1-) You have bunch of languages with dynamic and static typing that can interop: C#, VB.NET(it sucks I know), Boo (a statically typed language allowing dynamic typing), IronPyton, IronRuby(alpha available),Ruby.NET (Beta availbale), F# (first class functional language) and a lot of less popular ones like nemerle, lispdotnet, prolog.net...

2-) .NET framework is available in windows and gnome by default. Have you ever tried to deliver a python application to your customer who knows nothing about computers ? You cannot instruct them to install python easily. Even if you can sometimes deployment of 1000 computers are problematic. Most XP and all Vista computers already has .NET framework so it is easier to deploy cross platform applications

3-) java is the most popular language now according to TIOBE index: [http://www.tiobe.com/tpci.htm](http://www.tiobe.com/tpci.htm) But popularity does not make a language good (For eg. VB). Although .NET especially c# is highly inspired of java ( the reason C# was born because sun sued Microsoft for Visual J++), for many years, Sun's over protective behavior of java, damaged java community a lot. If you check the bug list of java you will see there are 3 - 4 years standing bugs. GUI development with java sucks.Although Sun recenlty Open sourced java recently , as everything Sun did so far, it is too little and too late. Java is destined to go where PHP and Cobol lies now

4-) Web Development with mono is breeze. What other choices we have ?
Java based framworks (look at item 3), PHP (is already dead), Ruby on Rails (this is a very nice framework but sorry not suitable for large applications, No unicode, no multithreading), Pythonic Frameworks like Django and Turbo Gears, these are also very nice but they are even worse than RoR. Still very nice for small to medium web development

5-) .NET library is large. Python library is also large, and available C librarires are huge. But with .NET you got all in one

6-) You've got the power of frameworks written for windows, like nhibernate, spring.net, db4o, nunit ...

7-) You've got the power of Java frameworks via IKVM. IKVM is a Java VM which can run on mono

Although it is Alpha, we've got Silverlight/moonlight: [http://www.mono-project.com/Moonlight](http://www.mono-project.com/Moonlight)

Note that I am not claiming Mono is better than Python.
These are my opinions what for Mono brings to the table

---

### Post by soc on 2007-11-10
I think what most mono fanboys don't understand is that people just don't want to participate in Microsofts little. If companies like Novell or persons like Icaza love to help Microsoft spreading FUD and lies, they can do it. But please understand that other people won't like it.

I often hear that Visual Studio is the best IDE around. Should we now all force the kernel developers to use it? How good the tool is doesn't count, if people get dependent to companies likings, which are known to be hostile gagainst them.

The myth that mono will make it possible to port .NET applications to a free operating system is a joke. The only thing it does is to help port Linux applications to Windows.

Is it legal to use GTK on Windows? Yes! How many will start writing an app with GTK# instead of Windows.Forms for Windows? Not many.
Is it legal to use Windows.Forms on Linux? No! (Only regarding to a country with people to stupid to count a piece of paper) How many will start writing an app with GTK#? Probably many.

Therefore it only helps one, single, large proprietary vendor.

---

### Post by qamelian on 2007-11-10
> **soc said:**
> I think what most mono fanboys don't understand is that people just don't want to participate in Microsofts little. If companies like Novell or persons like Icaza love to help Microsoft spreading FUD and lies, they can do it. But please understand that other people won't like it.

I often hear that Visual Studio is the best IDE around. Should we now all force the kernel developers to use it? How good the tool is doesn't count, if people get dependent to companies likings, which are known to be hostile gagainst them.

The myth that mono will make it possible to port .NET applications to a free operating system is a joke. The only thing it does is to help port Linux applications to Windows.

Is it legal to use GTK on Windows? Yes! How many will start writing an app with GTK# instead of Windows.Forms for Windows? Not many.
Is it legal to use Windows.Forms on Linux? No! (Only regarding to a country with people to stupid to count a piece of paper) How many will start writing an app with GTK#? Probably many.

Therefore it only helps one, single, large proprietary vendor.
First off you are wrong about porting apps. Some .NET apps are already in the process of being ported to Linux. The first one I read about the the Paint.NET app that seems to be getting very popular on Windows.

And it may not be legal to use Windows.Forms, but it is legal to create an open-source implementation. Happens all the time. 

And for those folks who have a problem with including Mono because de Icaza works for Novell and Novell has a relationship with Microsoft: where do you draw the line? Should we drop Gnome as well? Miguel de Icaza was the original motivating force behind Gnome, after all. 

By the way, it doesn't mean that you're a "fan-boy" just because you prefer some apps written in mono over similar apps not written in Mono. It just means you prefer those apps. Get over it.

---

### Post by amano on 2007-11-10
i can't see why this turns out to be a Mono discussion. The question should be if Tomboy and F-Spot should be shipped on the CD or not.

Mono is (in my eyes) a good thing and a full gnome install will feature it and all apps depending on mono will have mono to be installed. But currently only Tomboy and F-Spot depend on mono (in the minimal default setup), but I consider both of them rather as goodies than necessities to be featured in a minimal install...

Please let aside the discussion if mono is a good thing, or not.

But I think I know now, why I voted to keep mono in the first place ;)

---

### Post by teasum on 2007-11-10
> **amano said:**
> i can't see why this turns out to be a Mono discussion. The question should be if Tomboy and F-Spot should be shipped on the CD or not.

I couldn't agree more.  I would say, however, that in terms of desktop usability, F-Spot, even with its problems (I hate its default file structure for the 'photos' folder, for instance), is worth keeping in a default installation.  I say this even though I actually use *both* regularly, though I can see where Tomboy might feel a bit less necessary for the average user.

> **Hairy_Palms said:**
> But that combined with the fact that mono is still bloated slow technology, is what decides it for me, also as stated the gnome-panel has a sticky notes application built in, meaning tomboy is duplicated functionality, f-spot is the only program that should even be considered for default, and its not worth the 65-70MB (1/10th of a CD) needed to include f-spot by default.

While I can't speak to the 'bloated slow technology' claim, I don't think sticky notes and Tomboy constitute duplicated functionality, unless you also think gthumb and f-spot provide the same functionality as well.  They're both in a similar ballpark, but they're significantly different in my opinion.  To support that claim, I can honestly say I use *both* sticky notes and Tomboy--the former for reminders and quick notes, and the latter for structured note-taking, such as when I am working on a research project or presentation.  Still, I could see where Tomboy would not be seen by the typical user as necessary, and thus, could be installed only by those who want it.  

As for the space taken up by mono, which is needed for F-Spot, I agree that 65-70MB seems like a lot; however, I suppose the real question is how necessary one thinks F-Spot is to the default Ubuntu desktop.  A similar point was raised earlier about OpenOffice, I believe, which, although rather bulky and slow, is identified as necessary to the basic user in place of other, smaller office apps.  In my opinion, F-Spot, or an application with similar functionality, should be included in a default Ubuntu installation.

This is just my opinion, as I use both F-Spot and Tomboy regularly.  I agree, however, that the issue here is whether or not these two programs are worth keeping in a default Ubuntu installation.  In my opinion, they should, especially F-Spot.

---

### Post by Corbelius on 2007-11-11
Gutsy cd install.

Mono libraries on cd: 9 MB of space.

F-Spot on cd: 1,7 MB of space. 

Tomboy on cd: 2,3 MB of space.

:roll:

---

### Post by Simon G Best on 2007-11-11
> **smartboyathome said:**
> Also, you keep asking people who oppose you if they have any connection to him. Seems like you think that everyone should agree, and if not, they will a connection with him.

Nope.  I asked one person.  And it wasn't because he disagreed with me, but because of how he was coming across.  I wondered if, perhaps, he was astroturfing, or something like that.

---

### Post by Simon G Best on 2007-11-11
Thanks for answering my questions on this stuff :)

> **gnomeuser said:**
> I have exchanged emails with Miguel around the time the Novell-Microsoft deal mainly to get his input on questions I had and **to help arrange an episode of Novell Open Audio** that dealt with the common questions I heard from people around me.

(Emphasis mine.)  [Novell Open Audio]("http://www.novell.com/feeds/openaudio/"): "Connecting Novell users with what's going on inside and around the Novell universe."  It's a sort of Novell PR thing, by the looks of it.  So, you have been involved with Novell PR.

> I don't work on Mono (aside filling bug reports) and my extend of involvement with the Mono codebase is limited to having produced a few patches to some C# apps when I hit an obvious bug. I also maintain a few Mono packages for Fedora.

Right, so you actually are involved with Mono.

> Regardless I fail to see how that is relevant...

Really?  Not only are you involved with Mono, but you've also been involved with what seems to be some sort of Novell PR thing.

---

### Post by Simon G Best on 2007-11-11
> **Corbelius said:**
> Gutsy cd install.

Mono libraries on cd: 9 MB of space.

F-Spot on cd: 1,7 MB of space. 

Tomboy on cd: 2,3 MB of space.

:roll:

Can I ask how you get those figures, please?  I'd just like to check for myself :)

---

### Post by smartboyathome on 2007-11-11
> **Simon G Best said:**
> Thanks for answering my questions on this stuff :)



(Emphasis mine.)  [Novell Open Audio]("http://www.novell.com/feeds/openaudio/"): "Connecting Novell users with what's going on inside and around the Novell universe."  It's a sort of Novell PR thing, by the looks of it.  So, you have been involved with Novell PR.



Right, so you actually are involved with Mono.



Really?  Not only are you involved with Mono, but you've also been involved with what seems to be some sort of Novell PR thing.

So, you saying that just because he put a few patches into Mono, and made some packages for Fedora, that makes him biased? I could say the same thing about all the Ubuntu MOTU, and that their opinion doesn't matter, because they packaged programs for the repository. This thread is becoming more and more away from the point of removing mono.

> **Corbelius said:**
> Gutsy cd install.

Mono libraries on cd: 9 MB of space.

F-Spot on cd: 1,7 MB of space. 

Tomboy on cd: 2,3 MB of space.

:roll:

If you search for mono in synaptic, and remove all those mono libraries, then it turns out to be 30.9 MBs. Try it. :)

---

### Post by qamelian on 2007-11-11
> **smartboyathome said:**
> If you search for mono in synaptic, and remove all those mono libraries, then it turns out to be 30.9 MBs. Try it. :)

That is because the packages need to be decompressed during the install. The installed size will almost always be larger than the size of the packages on the CD. If you browse the packages on the alternate install CD, you can see the actual package sizes and determine how much space is really at issue on the disc.

---

### Post by gnomeuser on 2007-11-11
> **Simon G Best said:**
> Thanks for answering my questions on this stuff :)



(Emphasis mine.)  [Novell Open Audio]("http://www.novell.com/feeds/openaudio/"): "Connecting Novell users with what's going on inside and around the Novell universe."  It's a sort of Novell PR thing, by the looks of it.  So, you have been involved with Novell PR.



Right, so you actually are involved with Mono.



Really?  Not only are you involved with Mono, but you've also been involved with what seems to be some sort of Novell PR thing.

I'm tireing of your ad hominem attacks.

Anticipating a community "situation" I send in questions and an appeal to an indepth episode of Novell Open Audio precisely so we could focus on the many speculations surrounding the deal. This was right after the announcement, I feel it was right to let Novell answer the questions I heard and some I had myself. I fail so see how being a listener of a well known Linux podcast makes me Novell PR material. 

Same thing with regards to maintaining Mono packages for Fedora, I happen to use them, when I hit a bug I tend to want it to go away. I happen to be quite talented with regards to breaking software, on the occasions where I can fix the bugs I hit I'll damn sure do so - it's the power of Free Software.

The Mono runtime can be realistically reduced to 2.4 megs (packaged - 7 megs on disk) which is roughly 50% less than python and an order of magnitude less than Java (mostly due to Sun licensing terms which creates an all or nothing situation - technically we could reduce Java below it's current 34.5 megs packaged sized so let's avoid putting to much measure in this number). Sure if we pull in all of the Mono stack, along with development tools, documentation then it hits roughly 84 megs packaged but on the install CD we only a fraction of this. Mono easily fits in the same space or less than what we use for Python. I doubt this is a real issue, in case it is there are things we can remove that will not degrade enduser functionality, such as the Windows apps (which on my Gutsy x86_64 DVD takes up 18 megs).

---

### Post by mangar on 2007-11-11
Just FYI: 

Java is also being considered for removal / shrinkage from the install CD:
[https://blueprints.launchpad.net/ubuntu/+spec/openoffice.org-cd-reduction](https://blueprints.launchpad.net/ubuntu/+spec/openoffice.org-cd-reduction)

Now please, take the flameawar to the ubuntu- cafe, or to Slashdot..

---

### Post by pengu on 2007-11-12
dude, do you even know what mono really is? and what it can really do?

i challenge you do go though these forums and count up all the people requesting a windows program or functionality. All these people want linux ports of windows applications. Mono can do this. Think of the possabilities! Imagine a perfect world when mono is compleate and stable, hardware vendors can easily and quickly write up linux ports of there formaly windows-only hardware interfaces. (Think itunes, etc).

Now really consider what the linux community gains out of the so-far unjustified boycott of mono.

---

### Post by libervisco on 2007-11-12
I vote for removal, and here are my reasons.

1. It wastes space that could be used by a multitude of other programs. Mono applications seem to be quite a bit heavier than those written in something like C or python, from what I've seen. Considering that including Mono based applications gives them spotlight that further contributes to the propagation and continued development of Mono based software, as opposed to more efficiently developed software, it really does seem like a long term move in the wrong direction.

In other words, let's not go the way of the bloat. Let's make GNU/Linux applications both powerful and fast, not powerful at the expense of resource and energy waste.

2. Microsoft has been spreading FUD about Free Software infringing on their patents for quite a while. We should note that this FUD is actually being realized through lawsuits launched by their allies, like "IP Innovations" who recently filed a lawsuit against Novell and RedHat. So where does Mono fit in? It's reasonable to say that Mono shouldn't be treated any differently as any other potentially infringing software, which is, considering the bad nature of software patents, pretty much any software in existence.

However, despite the fact that any software could potentially infringe on somebody's patent, when we do recognize areas in which we know there is a higher likelihood of infringement going on, it may be at least prudent to be cautious. This caution, for example, is the reason why you don't see mp3 support installed by default on Ubuntu and other distributions. It is known that these are patented technologies so, regardless of whether a lawsuit would ever actually be filed, in the name of caution they are not included by default.

Situation with Mono is less certain than with mp3 codecs, but considering how close this technology is to Microsoft's and considering the very nature of Mono itself and Miguel De Icaza's history of essentially pro-Microsoft claims, there may be enough reason to be vary of it.

While stories about Mono being a trojan horse planted within the GNU/Linux world may sound like a mad conspiracy theory, there are quite a bit of little details which add up enough to at least make me pause and wonder.

What details?

- Miguel De Icaza's pro-MS claims.. it's gonna be very easy to find them. Just read his blog.

- A member of GNOME Project helping Microsoft manipulate the process of standardizing their bogus OOXML standard (Miguel is a high suspect here, obviously).

- Of course, the nature of the Mono project as an implementation of what is essentially a Microsoft platform.

- The whole Novell-MS deal which basically allows legal patent sharing between two companies under the exclusionary terms, exclusionary to distributions who didn't sign a deal, including Ubuntu. IF any patented code is to leak into Mono, it wouldn't be Novell who would be liable as much as other distros, again, including Ubuntu.

Now I know I'm dancing on a fine line between reasonable analysis or speculation and what some may call "FUD", but the fact that I admit this might at least help you take this with a more critical eye. Just think for yourself.

Cheers

---

### Post by smartboyathome on 2007-11-12
> **libervisco said:**
> In other words, let's not go the way of the bloat. Let's make GNU/Linux applications both powerful and fast, not powerful at the expense of resource and energy waste.

Fine then, lets also get rid of GNOME and use the terminal instead. After all, the GUI is "an expense of resource and energy waste". ;)

Anyway, this whole argument seems bogus to me. People have been saying it may someday infringe patents (especially the post before me), but fail to show patents NOW. And it may take some space, but 1/20th of the CD isn't that much.

---

### Post by st4rdr1ft3r on 2007-11-13
the only parts that infringe patents are the winforms, asp.net, vb.net and ado.net. the rest is ok, they have made sure they don't infringe patents and will just work around any that they have (if they have).

i mean linus actually admits that the kernel infringes on some patents i think.

---

### Post by CarpKing on 2007-11-13
On the patents issue, all I have to say is the following: when one gambles with the devil, one must never assume that one knows all the rules of the game.  

I have no problem with Mono itself.  The main thing that I don't like about its inclusion in Ubuntu is the use of so much space for two small programs that don't do much that couldn't be done in other programs that are already there.  I've never messed with Tomboy, but I doubt that F-Spot does anything that gThumb couldn't do with a little love.  It just seems like if we could leave these two in the repositories (they can even be in main), they would be easily accessible for those who want to use them, while space on the CD would be freed up for programs that add functionality.

---

### Post by libervisco on 2007-11-13
> **smartboyathome said:**
> Fine then, lets also get rid of GNOME and use the terminal instead. After all, the GUI is "an expense of resource and energy waste". ;).

Or even better, let's not use a computer at all! :P

Seriously, removing GNOME would remove a serious amount of functionality whereas Mono based applications would easily be replaced with something that matches or exceeds their overall value. That said, what's being asked for isn't anyhow equivalent to removing GNOME in whole. ;)

[quote=smartboyathome]Anyway, this whole argument seems bogus to me. People have been saying it may someday infringe patents (especially the post before me), but fail to show patents NOW. And it may take some space, but 1/20th of the CD isn't that much[/quote]

I didn't say "some day" I said it could be infringing right now or any time. That's just the nature of software patents. It is extremely hard to be absolutely sure that someone (including numerous patent trolls) hasn't patented an idea or an algorithm any programmer happens to use in his/her programs. How can you be sure?

That's a big part of the reason why there is a movement against legal existence of software patents in whole.

So no software can be proclaimed absolutely safe, not even Mono. In a contrary, when there are circumstances which allow someone to actually legally implement patented ideas, why would he not implement them? They say they're trying their best not to use Microsoft's patents, yet the deal with MS actually allows them to do exactly that.

However since the deal excludes other distributions from having part in it, while it may be safe for Novell users it is not safe for, say, Ubuntu users. Heck, Miguel has said it himself it's safe "as long as you get it from Novell"!

Sorry, but there is just too much smoke there for me to just put a blind eye and support continued propagation of Mono.

And when there are even technical arguments in favour of replacing Mono with something else which would actually result in more functionality for less footprint, I think it is a fairly compelling case for non-inclusion.

Thank you

---

### Post by Auria on 2007-11-13
> **libervisco said:**
> 
So no software can be proclaimed absolutely safe, not even Mono
... and not even the linux kernel, i suppose. we remove it? ;)

> **libervisco said:**
> 
And when there are even technical arguments in favour of replacing Mono with something else which would actually result in more functionality for less footprint, I think it is a fairly compelling case for non-inclusion.


that i agree.

---

### Post by DrMega on 2007-11-14
> **Simon G Best said:**
> I'm uneasy with Mono, because of Miguel de Icaza, Microsoft and Novell.  I'd rather not have Mono on my system - and so I've removed it.  I didn't use F-Spot or Tomboy anyway.

Given Microsoft's FUD campaigns, it does seem sensible to ditch Mono.

Microsoft have published the specification for the .NET framework, and it is their (official) intention that third parties should develop .NET for other platforms. Novell and a large base of independant developers have worked towards that goal, under the Mono project.

I think Mono is a great initiative. If we move towards platform independance (where practical), then you get a better pool of software to choose from which has to be good for all of us.

---

### Post by drf_av on 2007-11-14
DrMega: please, don't talk about an open .NET framework. Go ahead and read the licence. Next thing you'll do after reading that is purging everything that has a ".NET" in its name.

---

### Post by vambo on 2007-11-14
Could someone point me to a decent technical article on .NET. As far as I can judge it's technically a load of junk - why the fuss with this bloat-ware :confused::confused::confused:

---

### Post by DrMega on 2007-11-14
> **drf_av said:**
> DrMega: please, don't talk about an open .NET framework. Go ahead and read the licence. Next thing you'll do after reading that is purging everything that has a ".NET" in its name.

I'm familiar with the license. I develop in C\.net for a living. There are severe licensing restrictions on Visual Studio.net, and much of the what MS .Net encompasses (which includes various web services - MS .Net is not limited to the API), and many MS Windows specific elements. However the generic C# language, and the CLI has been accepted as an industry standard by ECMA, having been ratified by a number of organisations, including some of MS's competitors.

In MS's own publications, they state that they hope third parties will implement the .Net framework on other platforms.

All that said, if you feel that .Net is evil then of course you should purge all traces of it from your machine.

---

### Post by DoctorMO on 2007-11-14
I'm a biased, Free Software nut and I say:

Mono is bad, C# is a pointless technology born out of the bad blood between Microsoft and Sun with Microsoft trying to push VB into a Java state when it dumped it's J++; Come on you lazy programmers, stop wasting your time with tinker toys like C#/Mono and start developing real applications in C/C++, I mean dear god even Perl/Gtk+ would be a better choice than mono.

I don't like Microsoft, I don't want anything to do with them, I don't want to take advantage of their "great" technologies and will never accept them as trust worthy. These technologies are coded in bad faith. I don't even care about the technical aspects of the arguments presented here, I'm arguing that you should shun mono because it's from Microsoft and shunning everything Microsoft does is the moral thing to do.

Unfortunately I don't believe very many of those arguing for Microsoft/Mono in this case are really very moral, all they care about is technical worth. What a pity.

---

### Post by DrMega on 2007-11-14
OK, and now the facts.

> **DoctorMO said:**
> I'm a biased, Free Software nut and I say:

Mono is bad, C# is a pointless technology born out of the bad blood between Microsoft and Sun with Microsoft trying to push VB into a Java state when it dumped it's J++

Mono is nothing to do with Microsoft, but I will concede that .Net evolved after a fall out between Sun and MS when Sun won a case arguing that MS couldn't have their own version of Java for a period of two years. I wouldn't say it is pointless technology to have a language which goes some way to enforcing stable design while still allowing much of the freedom you get with C and C++

> **DoctorMO said:**
> I don't like Microsoft, I don't want anything to do with them, I don't want to take advantage of their "great" technologies and will never accept them as trust worthy.

Great. Use Mono instead then.

> **DoctorMO said:**
> Unfortunately I don't believe very many of those arguing for Microsoft/Mono in this case are really very moral, all they care about is technical worth. What a pity.

I don't think anybody is arguing for Microsoft Mono, especially considering there is no such thing. The Mono project is led by Novell with voluntary support from ordinary programmers at home.

As for the moral argument, sorry I don't get it. Are those that have Mono install in some way immoral? Is it immoral to reject the efforts of developers that just way a solid and standardised API? Should we reject Ubuntu because Mono is installed by default and because it is a corporate led development with support from volunteer developers, many of whom probably have day jobs developing for a living on MS's platform?

---

### Post by DoctorMO on 2007-11-14
> As for the moral argument, sorry I don't get it. Are those that have Mono install in some way immoral? Is it immoral to reject the efforts of developers that just way a solid and standardised API? Should we reject Ubuntu because Mono is installed by default and because it is a corporate led development with support from volunteer developers, many of whom probably have day jobs developing for a living on MS's platform?

I reject the community lead effort to waste time implementing any rubber stamped "standard" that happened to wander out of the hallowed halls of the ECMA; next you'll be telling me that OOXML is really great.

I don't think your getting the idea of what it means to be working with a tainted technology; I feel a deep sorrow for programmers that are enslaved to work on the windows platform but why should that translate into forcing their whims on the FLOSS community? Mono is tainted because it's ECMA, ECMA is tainted because it's a corrupt standards body that rubber stamps anything for the right price. Microsoft just happens to have a nice case of blood money to buy these standards and I want no part in them, nor do I want my operating system to include elements programmed in mono to be included by default.

There is legitimate concern that mono is neither warranted, needed or a worthwhile endever considering the many many other things that people could be bettering in the ubuntu operating system. From Mono is spawning all sorts of weird and wacky notions that it's some how ok to colaberate or in any way do business with Microsoft.

I'll need a hell of a lot of convincing to do business or in any way relate myself to people or organisations that have no morals (and no I do not want to hear about how companies have a duty to their share holders because thats just as good as a murders responsibility to the voices in his head)

Now I understand mono programmers have invested a lot of time and effort into learning and practicing this language; for them I can only offer my deepest sympathies and hope they can recover from the ailment and put the whole afair behind them.

---

### Post by DrMega on 2007-11-15
> **DoctorMO said:**
> I reject the community lead effort to waste time implementing any rubber stamped "standard" that happened to wander out of the hallowed halls of the ECMA; next you'll be telling me that OOXML is really great.

I don't think your getting the idea of what it means to be working with a tainted technology; I feel a deep sorrow for programmers that are enslaved to work on the windows platform but why should that translate into forcing their whims on the FLOSS community? Mono is tainted because it's ECMA, ECMA is tainted because it's a corrupt standards body that rubber stamps anything for the right price. Microsoft just happens to have a nice case of blood money to buy these standards and I want no part in them, nor do I want my operating system to include elements programmed in mono to be included by default.

There is legitimate concern that mono is neither warranted, needed or a worthwhile endever considering the many many other things that people could be bettering in the ubuntu operating system. From Mono is spawning all sorts of weird and wacky notions that it's some how ok to colaberate or in any way do business with Microsoft.

I'll need a hell of a lot of convincing to do business or in any way relate myself to people or organisations that have no morals (and no I do not want to hear about how companies have a duty to their share holders because thats just as good as a murders responsibility to the voices in his head)

Now I understand mono programmers have invested a lot of time and effort into learning and practicing this language; for them I can only offer my deepest sympathies and hope they can recover from the ailment and put the whole afair behind them.

Well, I hope you're ISP doesn't use an MS products. I see you're in London so no doubt your Internet connection is either via a BT line or a Virgin Media cable. They both use MS products so perhaps you'd better cancel your connection. Do you have a bank account? Better cancel it if you do, I happen to know that many (if not all) the UK based major banks use MS software. Like it or not, if you really mean it when you say you won't relate to or do business with companies with "no morals", your only practical alternative is to go and live in the woods, and use sharpened sticks to catch your dinner. Good luck with that.

---

### Post by DoctorMO on 2007-11-15
> Well, I hope you're ISP doesn't use an MS products. I see you're in London so no doubt your Internet connection is either via a BT line or a Virgin Media cable. They both use MS products so perhaps you'd better cancel your connection. Do you have a bank account? Better cancel it if you do, I happen to know that many (if not all) the UK based major banks use MS software. Like it or not, if you really mean it when you say you won't relate to or do business with companies with "no morals", your only practical alternative is to go and live in the woods, and use sharpened sticks to catch your dinner. Good luck with that.

I don't really care what my ISP uses, I don't have to deal with the problems; nor do I have to save the Banks from their folly. I do however have quite a lot to do with Ubuntu.

Besides one must stay focused on getting the job at hand done; We have no need to do business with Microsoft even via ECMA so I see no reason to willy nilly sacrifice integrity for them.

---

### Post by DrMega on 2007-11-15
> **DoctorMO said:**
> I don't really care what my ISP uses, I don't have to deal with the problems; nor do I have to save the Banks from their folly. I do however have quite a lot to do with Ubuntu.

Besides one must stay focused on getting the job at hand done; We have no need to do business with Microsoft even via ECMA so I see no reason to willy nilly sacrifice integrity for them.

Ok, but what about those that want to use Mono on Ubuntu, and those that use software that depends on the Mono API, whether the user realises it or not?

Perhaps one solution to this debate would be to leave Mono there in the default build, but provide an easy way to remove it if users don't want it. Perhaps via Synaptic.

---

### Post by smartboyathome on 2007-11-15
> **DrMega said:**
> Ok, but what about those that want to use Mono on Ubuntu, and those that use software that depends on the Mono API, whether the user realises it or not?

Perhaps one solution to this debate would be to leave Mono there in the default build, but provide an easy way to remove it if users don't want it. Perhaps via Synaptic.

Or perhaps everyone that doesn't want it could move to Gobuntu, as that is made to be COMPLETELY FREE.

---

### Post by DrMega on 2007-11-15
> **smartboyathome said:**
> Or perhaps everyone that doesn't want it could move to Gobuntu, as that is made to be COMPLETELY FREE.

I've just had a quick read about Gobuntu. It seems to solve this debate nicely. This is what makes Ubuntu great. A solid OS with flavours to suit all (or at least most) tastes.

---

### Post by gnomeuser on 2007-11-24
> **smartboyathome said:**
> Or perhaps everyone that doesn't want it could move to Gobuntu, as that is made to be COMPLETELY FREE.

And yet there is no reason why Gobuntu shouldn't be able to ship Mono... it's free software under the MIT/LGPL license. And despite this pointless debate going on and on.. I have yet to see a patent that is infringe and the only other arguments are "I don't like Microsoft" and "I don't like that applications", nothing that sticks with regards to the freeness of Mono.

Aside that, GCC has a CLR backend now.. that's means it now can translate into the common language .NET uses.. that's right .NET technology in a GNU project. What is the suggestion here.. that GNU knowingly included patented technologies without a valid license, in one of the base component for the entire system.. want us to remove GCC as well now that it's "tainted"?

---

### Post by thegnuguru on 2007-11-24
I say no because it could be used by ISV's in future. Why make it hard for people to switch to linux

---

### Post by puntarenas on 2007-12-06
[Moonlight](http://www.mono-project.com/Moonlight), Miguel de Icaza and Novell's Linux version of Microsoft [Silverlight](http://silverlight.net/) is estimated to be availiable in 6 months. Moonlight will heavily depend on Mono as Silverlight does on .NET.

I have no doubt Microsoft will strategically use Silverlight to chain Users even more within there Windows platform. Moonlight will just be another fig leaf for Microsofts monoploly and allow them to claim platform independency and interoperability with Free Software.

So will Ubuntu become another Microsoft henchman like Novell?

[x] remove mono

Ubuntu is more than just functionality, it is also a feeling of freedom and humanity to me. Leave me alone with Mono, Moonlight and other Microsoft crap, because they still are the worst enemy of our freedom.

---

### Post by smartboyathome on 2007-12-06
I see this pointless anymore. Arguements are because people don't want to be "connected to microsoft". Guess what? GNOME is connected to Microsoft via Novell. UBUNTU is even connected to microsoft through novell. I don't think that is a strong enough reason.

---

### Post by amano on 2007-12-06
> **puntarenas said:**
> [Moonlight](http://www.mono-project.com/Moonlight)
Ubuntu is more than just functionality, it is also a feeling of freedom and humanity to me.

That's just pointless trolling. Mono is completely free software. It is open source and patent free (unless proven otherwise).

If you personally feel subhuman with it, just uninstall it. Or use Gobuntu. But leave this discussion alone if can't contribute at least some sentences with substance.

---

### Post by gnomeuser on 2007-12-12
> **smartboyathome said:**
> I see this pointless anymore. Arguements are because people don't want to be "connected to microsoft". Guess what? GNOME is connected to Microsoft via Novell. UBUNTU is even connected to microsoft through novell. I don't think that is a strong enough reason.

News flash:

GCC has CLI support which is the .NET common language. We ship Samba which is also based on Microsoft technology. If you want to use technology without any connection to Microsoft I suggest turning off your computer and start rubbing sticks together I still think that predates their dominance and thus influence.

Really if you want to remove all influence from Microsoft I can compile you a list of the software you don't have to remove from Ubuntu, it will be shorter than the one that needs to be removed to fulfill that requirement I promise you.

Not everything Microsoft does it evil, and removing peoples ability to use Ubuntu in their existing infrastructure and transfer their skills is a really bad idea. Imagine removing Samba for a second.. let's think about that... or vfat support. That last one is really bad, it's Microsoft technology and it's used on pretty much every USB device, do you want people who plug in their portable music player or usb stick to have to reformat it and lose their data and also be unable to carry the same hardware to a windows machine afterwards.

It would be nice if we could get off this high horse where Microsoft is the devil, they are not. Sure they do bad things but we should only actually do something like this if there is reason to do so.

---

### Post by aquavitae on 2007-12-13
As far as I'm concerned its not a question of patents (which will be debated without resolution until MS tells us what the patents actually are)
> **Simon G Best said:**
> 
it's not a matter of whether or not there's sufficient reason to *remove* a piece of software, but whether or not there's sufficient reason to *include* it in the first place.
This says it all - why have an extra 60MB of stuff we don't need installing by default. I say make the default apps more lightweight, and if someone wants mono, banshee, tomboy, etc, install them from the repos.

---

### Post by unityofsaints on 2007-12-13
Hmm I don't know where 60 MB is coming from, on my system tomboy+f-spot+all mono libs is 23 MB. I'm running Gutsy 7.10

---

### Post by gnomeuser on 2007-12-15
> **aquavitae said:**
> As far as I'm concerned its not a question of patents (which will be debated without resolution until MS tells us what the patents actually are)

This says it all - why have an extra 60MB of stuff we don't need installing by default. I say make the default apps more lightweight, and if someone wants mono, banshee, tomboy, etc, install them from the repos.

So you are telling me we should also remove Firefox and replace it with Epiphany+webkit and kill OpenOffice in favor of GNOME Office. (actually we agree here - but I doubt our arguments would be the same)

Seriously, you are arguing "I don't like the applications and thus want to hamper an entire framework", I for once like Banshee, Beagle, F-spot, Tomboy and many other of the apps Mono provides me. Additionally your space requirement is based on false data, nowhere near 60 megs of compressed data is used on the CD for Mono and Mono apps.

You should also show that applications written in C or Python are infact functionality equaliant, more resource efficient over time and as stable. 

(for reference Rhythmbox on my machine using the same size database uses twice the memory Banshee uses and it crashes quite often. They are not functionality equal either, here each has advantages though so let's call that a toss up.)

---

### Post by plun on 2007-12-15
Well, this FSF fundamentalism just destroys for Linux.

We lives in a **commercial world** and must understand it. 

To fight Novell and Mono just hurts....   IMHO

---

### Post by hanzomon4 on 2007-12-15
> **mangar said:**
> currently, mono is installed by default, and enables only two programs by default: f-spot, and tomboy.

f-spot can be replaced by gThumb, tomboy can be replaced by notecase, and a **few dozens of megabytes can be freed** from the install cd.

For what? What do we need that this "freed up space" would allow us to include?

---

### Post by smartboyathome on 2007-12-15
By the way, I don't think notecase is anywhere NEAR as functional as Tomboy.

---

### Post by gnomeuser on 2007-12-16
> **plun said:**
> Well, this FSF fundamentalism just destroys for Linux.

We lives in a **commercial world** and must understand it. 

To fight Novell and Mono just hurts....   IMHO

This is where we disagree, I consider myself a FLOSS advocate, I have strong views on distributing binary modules because it makes a lot of things really hard or impossible. But Mono is Free Software under the LGPL/MIT licenses, there is nothing wrong with it, calling it non-free is simply  not factually correct.

It's not pro-Free Software, it's anti-Microsoft at all costs. Besides Red Hat, Novell, Mandriva, Canonical, Xandros, Oracle all make good livings from Free Software, nothing in the model prevents commercial interests. Even Richard Stallman in the pre internet days used to sell backup tapes of the Emacs sourcecode to people who couldn't download it. 

Fighting Novell hurts primarily because a lot of the code used on the Ubuntu desktop these people love, is directly from the Novell guys. Novell also bet their business on Free Software, they can't go back to selling Netware. Their option is making this work or dying, I think they are doing really well so far, they managed to convince AMD to release ATI specifications and get them to phase out their closed source driver. They have given us tons of code and lend us expertise in testing, QA and usability we haven't had access to. They even hired people to do work that benefits everyone like letting Greg Kroah Hartmann work fulltime on the Linux Driver Project which gets more developers for the kernel while also getting us drivers for hardware under the GPL. They pay developers to work on a lot of things like Mono, OpenOffice, Evolution, GNOME and KDE. So what if they made the business decision to work with another company to get better interoperability and some legal candy both companies can market (and that is all the deal is really, it's not a sordid bribe or the end of the world.) Novell are good guys.

---

### Post by 23meg on 2007-12-16
[QUOTE=plun]Well, this FSF fundamentalism just destroys for Linux.

We lives in a commercial world and must understand it.
[/QUOTE]

I have to say this:

This "FSF fundamentalism" line you're taking every chance to use is getting annoying. Watch where you use it. Painting the FSF as a bunch of closed-minded fundamentalists is spreading misinformation.

The FSF explicitly supported Mono before the Novell - Microsoft deal. Now, they're still mostly fine with the ECMA-standardized parts of it, and their own DotGNU project actually uses some of those parts. There's been some animosity between de Icaza and the FSF, but that actually happened because apparently (according to de Icaza) the FSF loved Mono so much that they announced it as the GNU Mono project.

If you're going to complain about "fundamentalism", I suggest you build reasoned arguments against it, with proper and specific examples, instead of just whining about how much it hurts and associating it with one institution. Equating the FSF with fundamentalism and taking every chance to reinforce that association is no good.

---

### Post by hanzomon4 on 2007-12-16
I'm not that political in the Foss sense but I understand the reaction to Novell's MS deal. It undermines the philosophy that built this baby by buckling under phantom threats. Now while this may be a good business decision for them it cuts away at the credibility of foss which ultimately cuts away at what Novell's products are built on. That legal candy, in so many words, leaves the impression that every other Linux distro and the various software projects it incorporates is somehow doing something illegal. It really seems like a passive aggressive way for MS to say what they have been saying for years in regards to Linux. For Novell it gives them an added selling point over redhat and with it perhaps the ability to do somethings that would be illegal if done by other Linux distros. This is great for Novell but, in my **lay** opinion, it hurts everyone else  a little.

But just to make clear(again and again and again) my point on the matter, Mono is cool. The Mono apps we have are terrific(beagle, fspot, banshee, tomboy), Gnome has included tomboy in it's default setup, developers love it and that love translates into fun stuff for me. I have no problem with including opensource projects based on ideas by or with the cooperation of MS.

---

### Post by plun on 2007-12-16
> **23meg said:**
> I have to say this:

If you're going to complain about "fundamentalism", I suggest you build reasoned arguments against it, with proper and specific examples, instead of just whining about how much it hurts and associating it with one institution. Equating the FSF with fundamentalism and taking every chance to reinforce that association is no good.

Well... we have a situation with real educated FSF members which I respect to 100%, but I do not respect some users running around in every forum in the world and spreading FUD and fundamentalism.

I also really dislike this sort of sites... [http://boycottnovell.com/](http://boycottnovell.com/)

I have asked this before and **where is sabdfl  ?**  The community needs some sort of consensus about this.

Thanks !

---

### Post by 23meg on 2007-12-16
[QUOTE=plun]Well... we have a situation with real educated FSF members which I respect to 100%, but I do not respect some users running around in every forum in the world and spreading FUD and fundamentalism.[/QUOTE]

Then address those users themselves.

[QUOTE=plun]I also really dislike this sort of sites... [http://boycottnovell.com/](http://boycottnovell.com/)[/QUOTE]

Me too.

[QUOTE=plun]I have asked this before and where is sabdfl ? The community needs some sort of consensus about this.
[/QUOTE]

Email him and ask. He may not get back to everyone, since he gets too much email; if that's the case, ask him on IRC at the next Ubuntu Open Week.

---

### Post by plun on 2007-12-16
> **23meg said:**
> Then address those users themselves.


Ok.. but this Poll is a big example on this....just FUD without deeper facts
and knowledge. Really primitive way to handle this challenge.

"Remove Mono" , Why... ??

You can have a "Singing in the rain" approach or  a Ostrich and try to 
hide your head in the sand and hope for the best..:)

Or a  Ubuntu developer and members consensus... but not a community consensus... just sad..:(

Ok about MarksS....[http://www.markshuttleworth.com/](http://www.markshuttleworth.com/)

---

### Post by gnomeuser on 2007-12-16
> **plun said:**
> 
I have asked this before and **where is sabdfl  ?**  The community needs some sort of consensus about this.


How is the spacedudes word a consensus?

---

### Post by 23meg on 2007-12-16
[QUOTE=plun]Ok.. but this Poll is a big example on this....just FUD without deeper facts
and knowledge. Really primitive way to handle this challenge.[/QUOTE]

In any case, the FSF doesn't have representatives in this thread. People are voicing their own opinions.

[QUOTE=gnomeuser]How is the spacedudes word a consensus?[/QUOTE]

[http://www.ubuntu.com/community/processes/governance](http://www.ubuntu.com/community/processes/governance)

---

### Post by 23meg on 2007-12-16
[QUOTE=plun]Or a Ubuntu developer and members consensus... but not a community consensus... just sad..[/QUOTE]

It's hard, if not impossible, to reach community-wide consensus with such a polarizing issue as this.

---

### Post by plun on 2007-12-16
> **gnomeuser said:**
> How is the spacedudes word a consensus?

Well, someone with deeper knowledge and visions (also position) must start a more creative discussion about this challenge.

This discussion should lead to a consensus for the Ubuntu community.

For this "spacedude" I  have the deepest respect,  for his work with Ubuntu and Free Software. 

You seems to be a Fedora user so I doesn't understand your interest in Ubuntus way to do things or what packages which are within Ubuntus distribution and repo  :confused:

---

### Post by 23meg on 2007-12-16
> **plun said:**
> 
You seems to be a Fedora user so I doesn't understand your interest in Ubuntus way to do things or what packages which are within Ubuntus distribution and repo  :confused:

One can be both a Fedora and Ubuntu user, and be equally involved in each, you know?

---

### Post by plun on 2007-12-16
> **23meg said:**
> One can be both a Fedora and Ubuntu user, and be equally involved in each, you know?

Well, lets keep it as an internal Ubuntu community challenge.....step 1 :)

I don't think that Fedora users likes that other dists users interferes in their way to doing things and tells them within Fedoras forum.

Linux Foundation can maybe take a part in the whole Linux community and of course FSF.

This is just a mess for the moment...:)

PS Maybe to change setiings and add Ubuntu if he is running Ubuntu...:)  Proud Ubuntu user..  :guitar:DS

---

### Post by gnomeuser on 2007-12-16
> **plun said:**
> 
For this "spacedude" I have the deepest respect, for his work with Ubuntu and Free Software. 

You seems to be a Fedora user so I doesn't understand your interest in Ubuntus way to do things or what packages which are within Ubuntus distribution and repo  :confused:

I have to support Ubuntu users - even if I am a Fedora user and developer.

Besides, I can take an interest in the direction Ubuntu takes, especially if like this removing Mono thing, is based on fallacious argumentation and bad data. 

And one mans opinion, regardless of your respect for him, does not make a consensus. Mark stating facts might however calm the waters a bit which would be good. However if a person will listen when Mark says the same thing I do but not when I do, I think that says more about that person (and apologies to Mark for assuming he shares my view of the facts - the same would be true assuming we disagreed and someone changed their mind based solely on his authority)

---

### Post by plun on 2007-12-16
> **gnomeuser said:**
> 
And one mans opinion, regardless of your respect for him, does not make a consensus. Mark stating facts might however calm the waters a bit which would be good. However if a person will listen when Mark says the same thing I do but not when I do, I think that says more about that person (and apologies to Mark for assuming he shares my view of the facts - the same would be true assuming we disagreed and someone changed their mind based solely on his authority)

OK

Of course it doesn't make a consensus from one man, a consensus is always something you must discuss and check different opinions
and then you build an acceptance for something.

For me MS, Novell, Linspire and so on are  "So what ? "... MS are smart and this is business.

We must be smarter and just fix our software, it maybe hurts to
work with some proprietary code for a while but nothing can beat
open source in the long run.

The major risk we takes is that Linux is it own worst enemy and 
fights MS and itself instead of fixing software... out of the box working PCs with Linux.
 
Also if consensus is to ban everything from Novell, thats it, no more discussions.  

:)

---

### Post by russo.mic on 2007-12-25
You know,  Guys, given the fact that harddrive space is LESS THAN 1$ a gigabyte, are we really calling 65 MB bloat?  

you can't even buy a jumpdrive that small.

Merry X Mas!

Russo

---

### Post by vexorian on 2007-12-25
We don't have any WINE app installed by default and WINE does not come in ubuntu by default. I do not understand why should treatment to MONO be different.

It doesn't have any sense to make ubuntu dependant on some risky technology as MONO, 

And MS vocally treats MONO as a patent lawsuit mine (see mentions of MONO in patent deals.) So my vote is a forced yes.

---

### Post by smartboyathome on 2007-12-25
> **vexorian said:**
> We don't have any WINE app installed by default and WINE does not come in ubuntu by default. I do not understand why should treatment to MONO be different.

It doesn't have any sense to make ubuntu dependant on some risky technology as MONO, 

And MS vocally treats MONO as a patent lawsuit mine (see mentions of MONO in patent deals.) So my vote is a forced yes.

Again, why get rid of a good technology which will get more applications here because of FUD?

---

### Post by atomkarinca on 2007-12-25
Here's my 2 cents:

If we want to remove the mono dependencies just because they are bloated and replaced with "better" alternatives, then -as mentioned- why not remove OOo and have Gnome Office? I believe OOo isn't the purest open-source application out there.

If we want to remove the dependencies because we hate Microsoft, then... wait a minute! Mono isn't developed by Microsoft and I haven't seen a proof that says it infringes any licences. Why should we miss a cross-platform oppurtunity just because of some i-see-them-happening-in-the-future infringes?

For these reasons I don't want it to be removed from the Live CD. Even if I didn't love Tomboy, I would still think this way.

---

### Post by gnomeuser on 2007-12-25
> **vexorian said:**
> We don't have any WINE app installed by default and WINE does not come in ubuntu by default. I do not understand why should treatment to MONO be different.

It doesn't have any sense to make ubuntu dependant on some risky technology as MONO, 

And MS vocally treats MONO as a patent lawsuit mine (see mentions of MONO in patent deals.) So my vote is a forced yes.

Do not pass GO, do not collect 200$. 

Mono and WINE are completely different technologies. Mono aims to implement the .NET standard whereas WINE is a reimplementation of the Windows API. 

Till such a time as the Mono patent trolls provide evidence for their claim, my claim will be that I have an invisible fire spewing dragon in my room, following their backward and faulty logic the burden of proof is on them to prove that is not the case.. 

The fact that Ballmer opens his mouth is nothing new.. he did that before the Microsoft-Novell deal and he would have done it even if they hadn't signed that agreement.. Wanna help provide a list of their attacks on Linux the past 5 years, Microsoft live partly in this fantasy world wherein they believe they own everything. Yet they are also smart enough to know that is not the case but they talk a big game every once in a while.. never actually sues or provides evidence. This way they can presure people without actually running the risk of suing.

Fact, Microsoft has only offensively used patent lawsuits twice, and never against Free Software. They have been hit by them often.. they have no interest what so ever in attacking any Free Software in court, if they do that the OIN will automatically launch countersuits and take them down with us.. They would also be suing companies which their clients depend on such as Red Hat (name me a Fortune 500 that doesn't depend on Linux for something). A patent lawsuit against Free Software makes no sense, threatening with one however makes all the sense in the world. It is the single most effective and riskfree way they have to hinder our progress, just spread FUD.. we can't stop them from making these claims and it seems to work, we are fearful everytime it happens and their stock price certain doesn't hurt whenever they line up the guns. Not to mention that when they do this, the public preceives Linux as being a legal risk, which is all they need to keep people from switching.

---

### Post by emperon on 2007-12-26
> **gnomeuser said:**
> Do not pass GO, do not collect 200$. 

Mono and WINE are completely different technologies. Mono aims to implement the .NET standard whereas WINE is a reimplementation of the Windows API. 

Till such a time as the Mono patent trolls provide evidence for their claim, my claim will be that I have an invisible fire spewing dragon in my room, following their backward and faulty logic the burden of proof is on them to prove that is not the case.. 

The fact that Ballmer opens his mouth is nothing new.. he did that before the Microsoft-Novell deal and he would have done it even if they hadn't signed that agreement.. Wanna help provide a list of their attacks on Linux the past 5 years, Microsoft live partly in this fantasy world wherein they believe they own everything. Yet they are also smart enough to know that is not the case but they talk a big game every once in a while.. never actually sues or provides evidence. This way they can presure people without actually running the risk of suing.

Fact, Microsoft has only offensively used patent lawsuits twice, and never against Free Software. They have been hit by them often.. they have no interest what so ever in attacking any Free Software in court, if they do that the OIN will automatically launch countersuits and take them down with us.. They would also be suing companies which their clients depend on such as Red Hat (name me a Fortune 500 that doesn't depend on Linux for something). A patent lawsuit against Free Software makes no sense, threatening with one however makes all the sense in the world. It is the single most effective and riskfree way they have to hinder our progress, just spread FUD.. we can't stop them from making these claims and it seems to work, we are fearful everytime it happens and their stock price certain doesn't hurt whenever they line up the guns. Not to mention that when they do this, the public preceives Linux as being a legal risk, which is all they need to keep people from switching.

Well said !!!

---

### Post by plun on 2007-12-26
> **gnomeuser said:**
> Do not pass GO, do not collect 200$. 

The fact that Ballmer opens his mouth is nothing new.. he did that before the Microsoft-Novell deal and he would have done it even if they hadn't signed that agreement.. Wanna help provide a list of their attacks on Linux the past 5 years, Microsoft live partly in this fantasy world wherein they believe they own everything. 

Well, that Ballmer again  and MS...:)

Everything is about if the commercial ADS industry will adopt 
Silverlight or not. Not a little OS called Linux with tons of dists  :)

.Net have been a fiasco for MS and SIlverlight will probably also be it..:) Why should a developer switch from Adobes Flash or Suns Java...:confused:

But its for sure important that not Novell drives any progress before we see how it goes.... if the commercial market adopt Silverlight we must also adopt it...  Easy... IMHO

---

### Post by vexorian on 2007-12-27
> **gnomeuser said:**
> Do not pass GO, do not collect 200$. 

Mono and WINE are completely different technologies. Mono aims to implement the .NET standard whereas WINE is a reimplementation of the Windows API. 

Till such a time as the Mono patent trolls provide evidence for their claim, my claim will be that I have an invisible fire spewing dragon in my room, following their backward and faulty logic the burden of proof is on them to prove that is not the case.. 

The fact that Ballmer opens his mouth is nothing new.. he did that before the Microsoft-Novell deal and he would have done it even if they hadn't signed that agreement.. Wanna help provide a list of their attacks on Linux the past 5 years, Microsoft live partly in this fantasy world wherein they believe they own everything. Yet they are also smart enough to know that is not the case but they talk a big game every once in a while.. never actually sues or provides evidence. This way they can presure people without actually running the risk of suing.

Fact, Microsoft has only offensively used patent lawsuits twice, and never against Free Software. They have been hit by them often.. they have no interest what so ever in attacking any Free Software in court, if they do that the OIN will automatically launch countersuits and take them down with us.. They would also be suing companies which their clients depend on such as Red Hat (name me a Fortune 500 that doesn't depend on Linux for something). A patent lawsuit against Free Software makes no sense, threatening with one however makes all the sense in the world. It is the single most effective and riskfree way they have to hinder our progress, just spread FUD.. we can't stop them from making these claims and it seems to work, we are fearful everytime it happens and their stock price certain doesn't hurt whenever they line up the guns. Not to mention that when they do this, the public preceives Linux as being a legal risk, which is all they need to keep people from switching.
I see no need to ever grow a dependence to it, if an user wants to install that stuff he may just ... install it, why include it by default and ... make default gnome apps require it, totally beats me.

> Again, why get rid of a good technology which will get more applications here because of FUD?
Good technology? I am not saying "get rid of it", I am saying "don't install it by default" and promote it over python, java, C++ and any other thing without such risks for Linux apps development...

--

People thinking that MONO would actually get more applications to work on Linux, are missing some things:

[list]
[*] System.Windows.Forms , that's not part of the ECMA "open standard" in other words MS can seriously sue over it and prevent you from using it, thus it is not installed by default anyways. Visual Studio .net is the sort of IDE that will almost force you to use windows.forms , in other words, currently installing MONO by default, alone DOES NOT allow you to use 99% of the .net apps out there.

[*] ActiveX "components" it is crazy how many good .net apps out there (RSSBandit comes to mind) use that crap, and they make it non-portable.

[*] ".net app, winapi installer"... (which requests a certain .net version, NO , not MONO)

[*] .net 3.0  (and 4.0 and 5.0 and 6.0 and everyother .net version that will allow MS to fight us with an advantage, and zombie .net developers WILL use new features from the newest .net).

[*] XNA (a.k.a "you don't have directx on your .net clone", stop trying...)

[*] MS SQL Server dependency: many .net apps out there (specially from the relevant set) 
 has this SQL server dependency, most importantly, my country's tax application which supposedly was coded in .net and should work with MONO, doesn't , because of the installer, some stupid ActiveX component and, most importantly, the SQL Server requirement.
[/list]

--
> **gnomeuser said:**
> Do not pass GO, do not collect 200$. 

Mono and WINE are completely different technologies. Mono aims to implement the .NET standard whereas WINE is a reimplementation of the Windows API. 
Thanks for the information... I was just saying that a lot of people were supporting MONO to stay included by default because it allows you to run more apps. In this case WINE and MONO fulfill the same sort of objective.

---

### Post by fwilliams on 2007-12-30
Taken from happysmileman post:

 Re: Get rid of Mono
Quote:
"Mono is a free implementation of Microsoft's language C#. Microsoft has declared itself our enemy and we know that Microsoft is getting patents on some features of C#. So I think it's dangerous to use C#, and it may be dangerous to use Mono. There’s nothing wrong with Mono. Mono is a free implementation of a language that users use. It's good to provide free implementations. We should have free implementations of every language. But, depending on it is dangerous, and we better not do that."

From RMS.
Quote:
"On 2 November 2006, Microsoft and Novell announced a joint agreement whereby Microsoft agreed to not sue Novell’s customers for patent infringement.[9] According to Mono project leader Miguel de Icaza,[10] this agreement extends to Mono but only for Novell developers and customers. It was criticized by the free software community because it violates the principles of giving equal rights to all users of a particular program"


So unless you work for, or pay Novell, it is not at all Free software. All it does to everyone else is introduce patent concerns and I'm not going to use it, hopefully others won't either

---

### Post by smartboyathome on 2007-12-30
Which is why I say we get rid of the double click, and a lot of other stuff Microsoft patented. But people don't like that. I don't think we are in trouble now, so we should leave it. It may be put on watch though just in case.

---

### Post by fwilliams on 2007-12-30
Seriously gnomeuser, what about the following do you not understand?

From RMS.
Quote:
"On 2 November 2006, Microsoft and Novell announced a joint agreement whereby Microsoft agreed to not sue Novell’s customers for patent infringement.[9] According to Mono project leader Miguel de Icaza,[10] this agreement extends to Mono but only for Novell developers and customers. It was criticized by the free software community because it violates the principles of giving equal rights to all users of a particular program"

---

### Post by gnomeuser on 2007-12-31
> **fwilliams said:**
> Seriously gnomeuser, what about the following do you not understand?

From RMS.
Quote:
"On 2 November 2006, Microsoft and Novell announced a joint agreement whereby Microsoft agreed to not sue Novell’s customers for patent infringement.[9] According to Mono project leader Miguel de Icaza,[10] this agreement extends to Mono but only for Novell developers and customers. It was criticized by the free software community because it violates the principles of giving equal rights to all users of a particular program"

Both RMS and Eben Moglen have been allowed to review the complete text of the agreement, something you have not, and the statement released is that the agreement since it extends only to the customers and not the companies involved does not infringe the GPL.. and get this, it doesn't infringe GPLv3 either. Novell have stated that if such a clash is ever found the problem is with their deal not the GPL and the agreement will have to be altered. No such clash has been found. 

The deal is legal, it does not turn Mono into non free software that Novell act in what they believe is the best interest of their customers. 

Mono remains a community project, like it was before Novell bought Ximian and if Novell should cease contributing to Free Software tomorrow, Mono will continue as Free Software under the GPL/LGPL/MIT license scheme they currently use. 

And again I repeat that if Mono is infringing, then GCC is as well since it just got Common Language Intrastructure (CLI) support. Not to mention that Samba (itself a Microsoft based technology and of the utmost importance for Linux as a whole), just got documentation from Microsoft without any patent clearance what so ever.

Microsoft technology is all around us, or at least technology Microsoft has had a hand in developing. You can't get away from it.

I will repeat for the final time, before you mouth off about patent infringement in Mono again, show me the patent number.. it's that simple, just show me where it infringes. In a year of the Novell-Microsoft deal nobody has been able to do that, nor before this deal when the same argument was used against Mono. The burden of proof is entirely on your side.. Put up or shut up.

Mono is great technology, robbing users and developers of it by treating it as a second class citizen and constantly spreading FUD about it not to mention the company that funds it's development (and half the desktop you are currently using - Novell are big investers in both GNOME and KDE remember?).

So where is your evidence, not retorik or personal bias against Microsoft and Novell? I'm waiting.. 

So what does the deal really mean.. if Microsoft decides to sue Novell for patent infringement, the lawsuit will not harm their customers. The same is true for the case of Microsoft infringing on Novells patents, no Microsoft customers get harmed in the crossfire. But as is clear the companies themselves still have to exact the same level of care to not infringe on patents as always.. since they can sue each other even under this agreement. At the same time Novell became founding signatories in the Open Invention Network, donating both patents and money as well as pledging to use their patents in counter suits should any OIN signatories be the target of a patent lawsuit.. So if any Free Software project gets sued, we have protect through the reality of the ensuing MAD (which given that Software Patents exist is the best we can do to ensure they are not used while we fight for governments to ban their existance.. a fight we currently seem to be slowly winning fortunately).

Still we come back to you not understanding the deal in question and still not presenting the world with the patents Mono infringes. So why should we discriminate against Mono?

---

### Post by fwilliams on 2007-12-31
Only to Novell customers.

---

### Post by st4rdr1ft3r on 2007-12-31
> **fwilliams said:**
> Only to Novell customers.

nice argument...

---

### Post by Riverine on 2008-01-04
The effect of Mono on the community is already divisive (witness this thread).  As more packages and more developers become dependent upon mono this split in the community will widen.   

Busting up a community and diluting developer resources are two things that Microsoft couldn't hope to accomplish with a patent suit.

---

### Post by chandru.in on 2008-01-05
I have read the other threads speaking of mono removal.  Still I thought this is a right place to bring it to motice of community.

I can't show the exact patents which Mono would infringe for 2 reasons.

[LIST=1]
[*]MS has not yet revealed which are those 235 patents.  If finding the exact patent was so simple, FOSS developers would have easily worked around them.  Patents are dangerous because they are not easy to find.
[*]I don't live in US.
[/LIST]

**Why mono is bad?**

[LIST=1]
[*]Class libraries of Mono are licensed under MIT license.  this particular license speaks nothing of patents.  It means if necessary, even Novell can sue Mono users.  I read the piece on Mono site about why GPL/LGPL cannot be used as they would make proprietary development on Mono difficult.  That is fine. But why didn't Novell choose Apache license which talks of patents or for that matter any other open-source license which deals with patents.
[*]For those who didn't know, MS-Novell deal provides protection to Novell on Mono too.  But, MS-Xandros deal does not protect Xandros from Mono, I smell something fishy here.
[*]Novell funds Mono development.  It is a business house which has proved will use MS closeness to kill other Linux distros.  Now what is the guarantee that it will not push MS patent infringing code into Mono in future?  **Can those asking for proof prove this?**
[*]As many said Mono wastes space on the live CD.
[/LIST]

**What can be included in the space which can be freed?**

[LIST=1]
[*]A decent CD/DVD burning app like brasero.
[*]A file association editor like assogiate
[*]Mobile management s/w like wammu
[/LIST]

**What to do about Tomboy?**

If the community can spend so much effort and time to develop something as complex as Mono, definitely re-writing Tomboy in plain GTK+ or Python should be easy.

**Why including Java is more reasonable than Mono?**

Please I'm not saying include it.  Just saying it is not as dangerous as Mono.

[LIST=1]
[*]Sun has released it under GPL (mostly).
[*]Sun has been supporting Openoffice.
[*]Sun can be trusted not to sue users.  Yes they say Solaris is better than Linux.  But it is just normal business claim on technical grounds (which may or may not be true).  But they don't say Linux infringes N of Sun's patents.
[/LIST]

**Why OO and Samba are not same as Mono?**

They are needed to interoperate with Windows users.  Mono is not.  If you say Mono will help in porting .Net apps in Linux, you must be kidding or you need a break.  Mono is not a complete .Net implementation and can never be.  Which .Net developer do you think will take care to ensure Mono compatibility.

Can you tell me Java apps which worked well on GNU's Java implementation?  It is just impossible.  Thats why I was happy when Java was GPLed.

So no need for Mono on the CD.  Leave it in the repos.

---

### Post by 23meg on 2008-01-05
I've merged this thread into the Mono discussion thread in Ubuntu Idea Pool, since it's not specific to Hardy, most of the arguments are redundant with those in that thread, and Ubuntu Idea Pool is the place for brainstorming and ideas. Posts in "request" form don't belong to that forum either (read the forum header notice), and especially with such a central and polarizing issue as this, *requesting* your demand to be acted upon without consensus is not realistic.

---

### Post by chandru.in on 2008-01-05
There is another risk in pushing Mono.  There have been several claims by FUD creators that open-source lacks innovation.  Now Mono would become another example for them to cite.

Instead time would be more usefully spent if we push and polish our own home-grown innovative languages like Python and Ruby.

---

### Post by eragon100 on 2008-01-05
I use banshee a lot. If it doesn't work anymore in Ubuntu, I will go to ubuntu based freespire

---

### Post by smartboyathome on 2008-01-05
Like I said, if we remove one piece of software for functionality which helps the community and infringes patents, why not remove them all? After all, Microsoft patented the double click, and Novell worked on GNOME and KDE. Maybe we should all move to awesome because microsoft hasn't touched it?

---

### Post by chandru.in on 2008-01-05
I don't say remove it completely.  Just remove it from the Live CD to have more useful apps.

---

### Post by smartboyathome on 2008-01-05
That space argument has been argued before, and it has been shown that it would only free up 40MBs, which can fit maybe 1-2 programs more (which isn't worth the loss of functionality in my book).

---

### Post by chandru.in on 2008-01-05
Novell is not evil as long as it doesn't help MS spread FUD.  can u answer all point in my long post?

Y is mono class libs under MIT?

---

### Post by smartboyathome on 2008-01-05
The MIT license is still considered a free license since the source is freely available. See [here]("http://www.gnu.org/philosophy/license-list.html") (Expat License)

---

### Post by chandru.in on 2008-01-05
Yes there are several free licenses.  License is just a legal doc.  There is no mention of patent protection in MIT.  Both GPL and LGPL have.  Again Mono explains why they can't be used.  But y didn't it use Apache License which allows proprietary development and covers patents.

Also, how do u know that Novell will not push MS patent infringing code into Mono as its business is safe from MS litigation

---

### Post by smartboyathome on 2008-01-05
Maybe because the Mono guys don't feel like relicensing it under the GPL or Apache licenses. Also, that same point could be said about GNOME or KDE. How do you know that Novell won't push patent infringing code into either of those?

Seriously, the whole argument is based around speculation that MS "may sue us!". I think that people are being too cautious (which isn't a good thing to do in a war like what is going on now).

---

### Post by chandru.in on 2008-01-05
They have much less control over KDE or Gnome.  Mono is very much their own.  Moonlight which is gonna come on top of Mono is patent encumbered.  Gnome is actually contaminated by Mono now.  Hope at least KDE stands against Mono just as it is against OOXML (at least before it gets ISO mark).

---

### Post by smartboyathome on 2008-01-05
Ok, first off, Moonlight won't affect Mono, it will be its own program. Just because it is built on top of Mono doesn't mean it will cause mono itself to be infringing patents. Also, I am all for Mono since developers don't have to learn a new language when they move to Linux (this can save a buisiness $100s).

---

### Post by chandru.in on 2008-01-05
I just said Novell will not think twice about using its MS-Novell deal to thwart open-source competition.

Why was Java not pushed this much?  It would also have meant the same thing.  Y not push an alternative for AIR?

---

### Post by smartboyathome on 2008-01-05
Because Java is a memory hog, and I don't think that it will be included in Ubuntu until is is fully free.

---

### Post by chandru.in on 2008-01-05
Gij was a incomplete implementation of Java.  Mono is an incomplete implementation of .Net.  I see no difference in freedom here.  Icedtea is an almost complete implementation of Java why not include it?

Do u have any numerical data proving identical application Java uses more memory than Mono.  If so give me the two version of the identical apps let me check it out.

---

### Post by smartboyathome on 2008-01-05
I don't have java apps installed on my computer, so I can't do that. But when I worked with Java before in a programing class, and did the same in .Net, I noticed less disc searching with .Net than Java.

---

### Post by chandru.in on 2008-01-05
That is because.  .Net libs are loaded on windows during startup, Java libs are not.  .Net uses more memory indirectly in that way.

Did u try running the same code on Mono?

---

### Post by smartboyathome on 2008-01-05
No, because I don't program much anymore (I took the class when I was 9, and forgot it). I am starting to get into python anyway. :)

Also, about your other post:
> **chandru.in said:**
> I the space can be used for nearly 65 MB of Mono, why can't a small amount be given for brasero.

What exactly makes Mono so much more important for a desktop user than brasero?

Why INCLUDE brasero when it isn't needed on the CD? Mono provodes more libraries for more programs. Brasero does not. I would say keep brasero to the DVD (as I said in the other thread) and keep mono on the CD.

---

### Post by chandru.in on 2008-01-05
Now I'm happy u r in Python.  Yes that is an open-source innovation.

Please stop spreading FUD about Java using more memory than Mono when u have not made a real analysis.

Mono provides libs fine.  Let it come from repos not probs.  But brasero gives an important desktop functionality.  Let me stop this here.  I feel the threads have mixed up contents.

---

### Post by gnomeuser on 2008-01-05
> **chandru.in said:**
> 

[*]MS has not yet revealed which are those 235 patents.  If finding the exact patent was so simple, FOSS developers would have easily worked around them.  Patents are dangerous because they are not easy to find.


I have a billion patents.. pay me please. A claim means nothing, you are basically endorsing the mafia way of selling insurance here. The patent system is convoluted yes but never the less you can search them and you had a year to do so, yet nobody has found a single patent that Mono infringes on.

Futhermore the policy of the Mono project is that if a patent is potentially infringed upon they will workaround it or attempt to invalidate it. Just like any other Free Software project.

[QUOTE=chandru.in]
[*]I don't live in US.
[/LIST]
[/quote]

Neither do I, but that doesn't proclude me from research

[QUOTE=chandru.in]
**Why mono is bad?**
[/quote]

Your personal opinion

[QUOTE=chandru.in]
[*]Class libraries of Mono are licensed under MIT license.  this particular license speaks nothing of patents.  It means if necessary, even Novell can sue Mono users.  I read the piece on Mono site about why GPL/LGPL cannot be used as they would make proprietary development on Mono difficult.  That is fine. But why didn't Novell choose Apache license which talks of patents or for that matter any other open-source license which deals with patents.
[/quote]

The license was picked by Ximian, as you know Mono predates the Novell-Microsoft deal and Novell' involvement with Linux. The MIT license is a widely deployed and well understood license which is certified as an OSI Free Software license. What's the problem.

[QUOTE=chandru.in]
[*]For those who didn't know, MS-Novell deal provides protection to Novell on Mono too.  But, MS-Xandros deal does not protect Xandros from Mono, I smell something fishy here.
[/quote]

No, it provides protection for Novells customers, not Novell itself. Microsoft can still sue Novell for patent infringement and vice virsa. This means that Novell has to issue the same caution as any other company when implementing software.. the exact same.

Additionally OIN provides patent protection for all of us for all cases not just Microsoft doing something extremely unlikely, but I mentioned that so this was an oversight yes?

[QUOTE=chandru.in]
[*]Novell funds Mono development.  It is a business house which has proved will use MS closeness to kill other Linux distros.  Now what is the guarantee that it will not push MS patent infringing code into Mono in future?  **Can those asking for proof prove this?**
[/quote]

See above, I only stated that more than a dozen times in this thread already, did you even read the prior posts?

[QUOTE=chandru.in]
[*]As many said Mono wastes space on the live CD.
[/quote]

Saving a few megs is of little relevance..  I explained this earlier.. I'm beginning to thing you didn't read the thread at all.

[QUOTE=chandru.in]
**What to do about Tomboy?**

If the community can spend so much effort and time to develop something as complex as Mono, definitely re-writing Tomboy in plain GTK+ or Python should be easy.
[/quote]

And the point about Tomboy being reimplemented has been raised, if it is so easy then why don't you go do it. Meanwhile the rest of us will go use Mono to innovate. There was nothing like Tomboy before Mono, notice how fast a Mono based app grows up and gets a community. That is part of why we want Mono to be available, it's a good tool, the apps we produce with it rapidly becomes stable and featureful not to mention that they often bring innovation to the Linux desktop.

[QUOTE=chandru.in]
**Why including Java is more reasonable than Mono?**
[/quote]

It's entirely rational to include Java, it's a widely deployed platform we should support it. Sadly a GPL'ed version of a full Java is still a bit off especially since Red Hat are the only ones investing in completing and attempting to build a community around a GPL'ed java. Did I mention that Mono actually runs Java apps via IKVM.. well it does and it's so good at it that the Brazilian military use it to run much of their Java software instead of any of the Java platforms.

[QUOTE=chandru.in]
Please I'm not saying include it.  Just saying it is not as dangerous as Mono.
[/quote]

So zero > zero.. interesting

[QUOTE=chandru.in]
[*]Sun has released it under GPL (mostly).
[*]Sun has been supporting Openoffice.
[*]Sun can be trusted not to sue users.  Yes they say Solaris is better than Linux.  But it is just normal business claim on technical grounds (which may or may not be true).  But they don't say Linux infringes N of Sun's patents.
[/quote]

Sun actually have sued people more times than Microsoft over patent infringement and they heavily protect their innovations with patents. Their support of OpenOffice is practically the form of a dictatorship in that they require copyright assignment. Finally they did not release all of Java under the GPL, a fully functional GPL Java is still a ways off and only Red Hat are currently really investing in making and testing this. 

Once Java is ready, it needs well tested bindings for our stack, something that is currently lacking or atrociously undertested. Then we need to start developing applications.

Yet all of this is here now with Mono and as stated no risk to Mono has been proved.

[QUOTE=chandru.in]
**Why OO and Samba are not same as Mono?**

They are needed to interoperate with Windows users.  Mono is not.  If you say Mono will help in porting .Net apps in Linux, you must be kidding or you need a break.  Mono is not a complete .Net implementation and can never be.  Which .Net developer do you think will take care to ensure Mono compatibility.
[/quote]

Funny cause Novell is actually doing good business porting Windows programs to Linux and then selling the companies in the long end of the tail a Linux solution. Quite a lot of effort has gone into making this dead easy, so a lot of applications will run unaltered, some require small changes but Mono is helping companies move to Linux.. which I hope we can agree is a good thing.

[QUOTE=chandru.in]
Can you tell me Java apps which worked well on GNU's Java implementation?  It is just impossible.  Thats why I was happy when Java was GPLed.
[/quote]

Now you are just lying.. Eclipse and Azureus both very complex Java programs worked just fine using gcj and were infact available in the repos for Fedora (because we did the work on gcj and patching the apps). Plenty of software worked with GCJ and they had good API coverage, which is why the gapping holes in the GPL'ed Java is being filled out with GCJ code.

However GCJ was the only way we could have Java support under open terms, and that requires investment somthing only Red Hat was willing to do. We are all happy Sun elected to do the right thing, but for years they did not and we had to provide an alternative under a suitable license.. We cannot count on the next Sun seeing the light 10 years down the lane. Mono is here now, it's under Free Software licenses, it has plenty of active development, bindings to our stack and it brings both new coders as well as great new apps to the Linux desktop.

[QUOTE=chandru.in]
So no need for Mono on the CD.  Leave it in the repos.[/QUOTE]

Mono is an important bit of technology, it bring good applications to the platform and it's developed actively. Discriminating against it seem wrong especially since you are willing to use GCC which by your standards also potentially infringe Microsoft patents (again I welcome you to read the thread). Pulling it from the CD would be a mistake, an insult not to mention entirely unfounded in reason or fact.

---

### Post by zenwalker on 2008-01-05
I wonder why people always thing java is memory hog and .net isnt? You guys have to understand the hidden stuffs here. .Net runs on native windows API almost. Many of its API are already been present in winnie OS. So it will maek use of itself. Hence you feel its very fast. But damn, its buggy and slow when you do a production system guys! Java isnt like that. It has to use its own graphic renderriong system API's to display GUI stuffs and several APIs to run with out using any natively present API. So thats where java's power existis. There isnt any great in showing that apps run faster by making use of the existing stuffs.

---

### Post by chandru.in on 2008-01-05
> Finally they did not release all of Java under the GPL, a fully functional GPL Java is still a ways off and only Red Hat are currently really investing in making and testing this.

They couldn't release those parts only because it was licensed by them from third parties.  Also, can u cite a page where Jonathan Schwartz/Scott Mc Nealy claimed FOSS violated so many of their patents?  They have sued companies implementing commercial spin-offs of Java not FOSS ones.

> Now you are just lying.. Eclipse and Azureus both very complex Java programs worked just fine using gcj and were infact available in the repos for Fedora (because we did the work on gcj and patching the apps). Plenty of software worked with GCJ and they had good API coverage, which is why the gapping holes in the GPL'ed Java is being filled out with GCJ code.

Eclipse in Fedora works only because it is patched for GCJ.  Try downloadinf Eclipse europa from eclipse site and run it on Ubuntu.  It gives errors in loading so many plugin, which run fine on Sun/IBM's Java 1.5.

I have tried.  So u too try before calling me a liar.

---

### Post by chandru.in on 2008-01-05
> No, it provides protection for Novells customers, not Novell itself. Microsoft can still sue Novell for patent infringement and vice virsa. This means that Novell has to issue the same caution as any other company when implementing software.. the exact same.

Novell may be sued by MS.  But their customers are protected.  So if they include MS patented stuff they can provide legal guarantee to their customers which others can't.

MS will never sue Novell directly as they'd be counter-sued by Novell.

---

### Post by zenwalker on 2008-01-05
@Gnomeuser,

What is the point of wasting 50MB of space for just 4 applications support when there is an alternative? As you said in the first or second post, just becoz you use that doesnt mean that those apps and mono are great tools right? The same way we can think of reducing the disk space and makign it less blaoted by providing the other equvilent best alternative for those packages which dont rely on mono, thus resulting in saving 50MB space which can be used to fill up by some other!

---

### Post by smartboyathome on 2008-01-05
> **zenwalker said:**
> @Gnomeuser,

What is the point of wasting 50MB of space for just 4 applications support when there is an alternative? As you said in the first or second post, just becoz you use that doesnt mean that those apps and mono are great tools right? The same way we can think of reducing the disk space and makign it less blaoted by providing the other equvilent best alternative for those packages which dont rely on mono, thus resulting in saving 50MB space which can be used to fill up by some other!

Like I said, it would be saving 40MBs of space. And that could be filled up by a few programs, but it would basically all be taken by alternatives to the same programs we are using now, thus making that argument nil. Instead, we should encourage companies to port their stuff over from Windows to Linux, and watch the users follow! Mono makes it cheaper and easier.

---

### Post by chandru.in on 2008-01-05
Does Mono support COM, Activex, etc?

I'm sure several Windwos apps use them.  Again Mono is not a complete implementation of .Net.  So not all .Net apps can be ported over easily to Mono.

---

### Post by zenwalker on 2008-01-05
> **smartboyathome said:**
> Like I said, it would be saving 40MBs of space. And that could be filled up by a few programs, but it would basically all be taken by alternatives to the same programs we are using now, thus making that argument nil. Instead, we should encourage companies to port their stuff over from Windows to Linux, and watch the users follow! Mono makes it cheaper and easier.

Always need not be filled up by same apps buddy!! We can choose some other packages which might be missing in the Live cd. If users starts to make request for the packages, then you would come to know what kinds of apps is missing. So those kinds can be filled in. But i do agree that it wont happen always  ;)

---

### Post by smartboyathome on 2008-01-05
You are right, they can't be ported over EASILY, but it does make it EASIER to port them than to have them switch the whole program to another language and basically rewrite the whole thing.

---

### Post by smartboyathome on 2008-01-05
> **zenwalker said:**
> Always need not be filled up by same apps buddy!! We can choose some other packages which might be missing in the Live cd. If users starts to make request for the packages, then you would come to know what kinds of apps is missing. So those kinds can be filled in. But i do agree that it wont happen always  ;)

Yeah, and when the time comes for Mono to be left, then it will. But that isn't know, since it does help buisinesses, which would attract more people (see my last post).

---

### Post by gnomeuser on 2008-01-05
> **zenwalker said:**
> @Gnomeuser,

What is the point of wasting 50MB of space for just 4 applications support when there is an alternative? As you said in the first or second post, just becoz you use that doesnt mean that those apps and mono are great tools right? The same way we can think of reducing the disk space and makign it less blaoted by providing the other equvilent best alternative for those packages which dont rely on mono, thus resulting in saving 50MB space which can be used to fill up by some other!

As I explained earlier those number are taken from uncompressed installs. Mono can be packaged in such a way that it takes up less space than Python (please go back and check). Removing Mono will not magically save 50 megs on the CD, that is just false.. 

There are plenty of ways to slim down the CD, removing the Windows programs e.g. Investigating better compression for the deb pacages.. all of which would save more space than remove Mono.

---

### Post by chandru.in on 2008-01-05
Why has COM and Activex not yet been ported?  Hey what about apps written in VB .Net?

Remember unlike C#, VB is not a standard under ECMA.  So it is risky.

---

### Post by chandru.in on 2008-01-05
@gnomeuser

Have u changed your mind about calling me a liar ot not?

What about the point I made about Novell's intentions?

---

### Post by smartboyathome on 2008-01-05
> **chandru.in said:**
> Why has COM and Activex not yet been ported?  Hey what about apps written in VB .Net?

Remember unlike C#, VB is not a standard under ECMA.  So it is risky.

Apps written in VB .Net can be partially ported with the wholes fixed in normal .net (which would still make for less struggle than trying to rewrite the whole thing). ActiveX and COM are patented, aren't they? And ActiveX especially was a huge security risk on Windows when it was integrated with Internet Explorer.

---

### Post by smartboyathome on 2008-01-05
> **chandru.in said:**
> @gnomeuser

Have u changed your mind about calling me a liar ot not?

What about the point I made about Novell's intentions?

Novell has helped the Open Source community a lot. It helped get both GNOME and KDE where they are today, and are a big contributor to both. If they were to destroy open source, don't you think they would have done it already?

---

### Post by zenwalker on 2008-01-05
> **smartboyathome said:**
> Novell has helped the Open Source community a lot. It helped get both GNOME and KDE where they are today, and are a big contributor to both. If they were to destroy open source, don't you think they would have done it already?

Well Novell might not do that to OSS, but what if M$ does it from behind? Dont ya thing M$ always being fishy with what ever they do? ;)

---

### Post by chandru.in on 2008-01-05
> Apps written in VB .Net can be partially ported with the wholes fixed in normal .net (which would still make for less struggle than trying to rewrite the whole thing).

I thought Mono was claimed to be safe becoz it provided only C# which is an ISO language.  If it offers VB .Net, there is risk.

> ActiveX and COM are patented, aren't they? And ActiveX especially was a huge security risk on Windows when it was integrated with Internet Explorer.

Hey but just like Mono, they can help a lot more in porting windows apps.

Novell will not destroy open-source, as it will be a suicide.  They will kill Red Hat, Canonical, etc.

---

### Post by gnomeuser on 2008-01-05
> **chandru.in said:**
> @gnomeuser

Have u changed your mind about calling me a liar ot not?

What about the point I made about Novell's intentions?

You said it was impossible, clearly that was not true. Complex programs requires patches as do all programs to fit into a distro (even admitted so in the quoted section). I have run plenty of Java programs unaltered using gcj. So no, I still think you are misrepresenting gcj.

I answered that question already, read my original reply.. 

Now do you insist on moving the goal posts here? You asked for someone to answer your original questions I did, in response you move the goalposts. Clearly if you keep reformulating your "Novell is evil" argument I will give you the same reply, understand the deal in question works and look at the facts.

---

### Post by smartboyathome on 2008-01-05
> **zenwalker said:**
> Well Novell might not do that to OSS, but what if M$ does it from behind? Dont ya thing M$ always being fishy with what ever they do? ;)

Just because of that deal does not mean that Novell would be controled by Microsoft. I am sure that, if anything, Novell would try to protect open source from Microsoft, along with Redhat.

---

### Post by chandru.in on 2008-01-05
I'd like to hear from gnomeuser about his current opinion about my honesty.

---

### Post by chandru.in on 2008-01-05
sorry he posted a bit faster

---

### Post by chandru.in on 2008-01-05
When u need patches to run Java program on a particular implementation, it is no more a real alternative for Java.  Java is all about WORA.  So I did not misrepresent gcj.  In fact I like the way it helps open JDK now.

---

### Post by chandru.in on 2008-01-05
I just meant Mono can never provide a real alternative for .Net and hence its aim to promote porting of .Net apps to Linux is not achieveable.

---

### Post by gnomeuser on 2008-01-05
> **chandru.in said:**
> I thought Mono was claimed to be safe becoz it provided only C# which is an ISO language.  If it offers VB .Net, there is risk.


Which goes to show just how little research you have done

[QUOTE=chandru.in]
Hey but just like Mono, they can help a lot more in porting windows apps.

Novell will not destroy open-source, as it will be a suicide.  They will kill Red Hat, Canonical, etc.[/QUOTE]

Where is your evidence for this wild and insulting conspiracy claim?

---

### Post by chandru.in on 2008-01-05
I did not do less research.  It is just a sarcasm to prove Mono is risky.

Novell's ads are my proof.  They project Suse's ability to interoperate with Windows as the main advantage.  Now only they could provide it as a result of their MS deal.  Finally EU has forced MS to reveal their protocols.  But Novell used the deal to thwart Red hat's enterprise image.

---

### Post by eragon100 on 2008-01-05
Don' thrwo mono out! Moonlight depends on it! several big movie companys are already using microsoft silverlight for their online movies. If I can't watch those movies on ubuntu, i will switch back to windows, or goe tu suse or freespire or whatever. And believe me, there are a lot of people out there who ust like me have no problem using closed-source software, including nearly everyne who just switched from windows or mac, or who are still using and you're trying to convert to ubuntu. I can assure you that as soon as it becomes widely known that ubuntu doesn't support things like moonlight and even tons of linux-native aps, such as the afore-mentioned banshee, f-spot and tomboy notes, it won't be long before ubuntu isn't the most popular distribution on distrowatch anymore, and suse is, GPL or not:mad::mad::mad::mad::mad::mad:

---

### Post by Auria on 2008-01-05
> **eragon100 said:**
> Don' thrwo mono out! Moonlight depends on it! several big movie companys are already using microsoft silverlight for their online movies. If I can't watch those movies on ubuntu, i will switch back to windows, or goe tu suse or freespire or whatever. And believe me, there are a lot of people out there who ust like me have no problem using closed-source software, including nearly everyne who just switched from windows or mac, or who are still using and you're trying to convert to ubuntu. I can assure you that as soon as it becomes widely known that ubuntu doesn't support things like moonlight and even tons of linux-native aps, such as the afore-mentioned banshee, f-spot and tomboy notes, it won't be long before ubuntu isn't the most popular distribution on distrowatch anymore, and suse is, GPL or not:mad::mad::mad::mad::mad::mad:

come one calm down... this discussion was about knowing whether it should be there by default, I don't think anyone said it should be forbidden to install it

---

### Post by eragon100 on 2008-01-05
Yeah you're right. But Ubunt is for people (including myself) who want to have an out-of-the-box system. There shuold be no need to install additional software, definitely not to run popular native linux applications.

Plus, lots of reviews about ubuntu concentrate on saying how easy it is to play mp3, dvd etc. If you couldn't even run native linux applications anymore, those reviews will probalby be negative about future versions of ubuntu, recommending windows or other distro's. You won't get many new users then.

And finally, if mono isn't a part of the default install anymore, then tomboy note, f-spot and banshee can't be too. Ubuntu is made for people who don't know much about computers, like my granny. If those people are now using ubuntu 7.10, they won't like it if in the next release they will have a completely different photo mangaer, notes program, and music player. They would have to learn new things. And they don't want to learn new things, that's why they choose ubuntu in the first place. They just want to chat with their childen in Australia using pidgin or Amsn, and listen to music with rhytmbox, which they can use.

---

### Post by emperon on 2008-01-05
> **chandru.in said:**
> I just meant Mono can never provide a real alternative for .Net and hence its aim to promote porting of .Net apps to Linux is not achieveable.

It is already an alterntive. Almost all asp.net web apps work on mono and portable to windows. almost all non Gui code works. most of the gui code works too. Examples

ASP.NET : Any ASP.NET 2.0 web application you can try (except web parts using ones). MS AJax, MS ajax control tool kit. also are cross platform

non GUI libraries: The following libraries are cross platform and tested both on windows and linux : NHibernate, log4net, Rhino Mocks, db4o , Castle Project, 
boo

GUI code: NUnit, NClass, Paint.NET , Reflector (all are windows forms applications originally designed for windows and non trivial)

So although there is no 100% compability for mono and .net, for vast majority of cases it is more than enough.

Finally mono only consumes 23 MB on CD (including tomboy etc).

Lastly Java is not yet GPL'ed. This is for Java 7 which  has not been released yet. Also Sun will maintain it's own java as a seperate branch
[B]
Again we see some people do very little research before commiting their ideas.[/B]

---

### Post by chandru.in on 2008-01-06
@eragon100

It is not about whether silverlight is closed or not.  It is about the patent risk involved in using Silvelight on Linux distros which have not signed a deal with MS.  If you want Ubuntu too to sign a deal, then may be Silvelight can be used on Ubuntu.

> Plus, lots of reviews about ubuntu concentrate on saying how easy it is to play mp3, dvd etc.

MP3 and DVD are easy on Ubuntu but they don't come by default.  Anyway I don't think even moonlight will come by default.  This is about Mono.

@emperon

ASP .Net and VB .Net are not ISO standard languages like C#.  So implementing C# with mono may not pose legal issues, but implementing ASP .Net and VB .Net are risky.  Even if they don't directly infringe patents, it will allow two FUDs to be promoted easily.

[LIST=1]
[*]FOSS depends on commercial s/w houses for innovation.
[*]Ballmer would continue ranting about patents more easily.  Remember it may not matter to home users but for businesses it matters and will give the advantage to MS and Novell alone.
[/LIST]

**Will Mono help porting?**

I don't think Mono can help in porting applications to Ubuntu.  What makes ISV port is market share.  Market share can be increased only by providing unique new features which Windows lacks.  Adobe ported Photoshop and other products to Mac OS X not because OS X did not need learning new language.  It was because Mac OS X became popular among artists.  Adobe Reader it self was ported to Linux because of demand not because of one less language/library to learn.

Ubuntu needs to innovate on its own (it has done many so far) to gain market share thus make ISVs write cross-platform code.

---

### Post by chandru.in on 2008-01-06
Porting of apps has a good example in the web.  The number of IE-only sites has greatly reduced after invasion of Firefox.

Firefox did not gain mind and market share by providing a free IE clone.  It gained it by creating a really cool browser which made IE look like a toy.  This made webmasters port (aka re-design) their sites to work on non-IE browsers.

Same applies here.  If we can provide a really more powerful alternative and make Linux gain the market share, developers would happily learn Python/Ruby/GTK+ libs and port their apps to Liunx.

---

### Post by smartboyathome on 2008-01-06
I don't agree with what you said, chandru.in. First off, it DOESN'T pose a threat because of patents, so it spreads FUD like what you are saying (it may someday infringe patents or may make Microsoft/Ballmer/etc say it infringes patents). If Microsoft ever did come after Ubuntu/Mono/etc, then IBM, Google, HP, and the rest of the companies holding patents for open source programs could go after Microsoft for all their infringed patents.

About it not helping being ported, it DOES help because it will take longer for a program to be ported if the company has to spend more money hiring new people to program for them or training their current programers to use a new language than it would if they used a lot of their old code and filled in the bits that don't work or need to be changed.

Also, just because Ubuntu is using a bit from Mono which impliments Microsoft's language doesn't mean that it is copying Microsoft. Firefox had to use Bookmarks, which IE used, does that mean it was copying IE? No. They implimented a way to import bookmarks from IE into Firefox, does that mean it wasn't innovating? It is only after it can do everything that its opponent can do and more that it started innovating full time. Ubuntu is in the same boat, it is trying to catch up to Microsoft before it starts innovating full time. There are still many things which work with Microsoft but don't work with Ubuntu, and there are functions that Microsoft has that Ubuntu doesn't have yet.

---

### Post by chandru.in on 2008-01-06
Did u mean that I spread FUD?

Fisrt off, I don't think FOSS is playing catch up with MS.  We have excellent tools like Python and Ruby (which MS is copying in the form of IronPython).  I just said FUD creators (many tech journalists) would have another point to say FOSS copies.

If Ubuntu is trying to catch up with MS, it must concentrate on more important things like these,

1. Auto-detecting widescreen resolutions.
2. Providing better file association editing capabilities like changing icons of files of particular type easily.

---

### Post by smartboyathome on 2008-01-06
Yes, it still is, and that is why people aren't on Ubuntu mainstreem yet. But just because FUD creators would have something to complain about doesn't mean we should throw it out. If Ubuntu was so worried, wouldn't it throw out Compiz Fusion because it could give someone to complain about, as it has plugins which copy Microsoft AND Macs. Also, what about KDE, or to an extent GNOME? Each looks like Windows and sort of like OSX, respectively, and they could complain Linux isn't innovating, its copying another DE. I don't think that Ubuntu should try to JUST copy, but it isn't, it is becoming better while filling in the holes which shorten the gap between Windows and Mac, and Linux. They are making the move easier for developers as well as users. What if a company didn't WANT to rewrite their program in another language? They wouldn't want to until Ubuntu had something like 80% of the market share of computers because it wouldn't be profitable (since they would be losing money due to retraining/hiring new programmers). If we leave mono in, on the other hand, then companies would think harder about porting their apps to Linux, since they would only have to do a little patchwork, versus a full rewrite (and for some huge programs, that isn't possible).

And I wasn't saying you were spreading FUD, just that there is a lot of FUD spread about Mono.

---

### Post by chandru.in on 2008-01-06
I think I spent lot of time on this.  Anyway, even if there may be applications ported in future, I don't think there is any point in including it in the live CD today.  Leave it in the repos and when some killer app of Windows is ported to Linux **using Mono**, mono can then be included if that killer application is worth including in the live CD.  Until, then repos are the right place for Mono to live, while we improve our own technologies like Python and Ruby.

---

### Post by [h2o] on 2008-01-06
I consider Tomboy to be a killer app. I think that enough justifies having mono on the CD. And no, I don't have any issues with mono, neither technology-wise or ideologically. If there is a problem I am quite sure they will be taken care of appropriately by the developers of either Mono (to fix it) or Ubuntu (to remove it, if the problem is unfixable).

If Ubuntu is shipping some software that you for some reason do not like, then perhaps looking for some other distribution might be a good option? There is plenty of them around.

---

### Post by chandru.in on 2008-01-06
Tomboy may be a killer app, but it is not something ported from windows (many said Mono is needed mainly for porting windows apps).  It is a Linux killer app which could have very well been written in Microsoft independent languages like Python.

Yes if Novell pushes too much of patent infringing code into Mono, Ubuntu can remove it but by that time apps like tomboy would be very mature and losing them would be a great loss to Linux.  It is always better to handle risk at an early stage than wait till it becomes a threat.

I don't want to move away from Ubuntu because as a distribution with a nice bug #1, it is great.

---

### Post by smartboyathome on 2008-01-06
If tomboy can be written in Python, then by all means write one which does all that tomboy does. It isn't a matter that tomboy CAN be written in that language, it is just the time of the developers. Not everyone can spend hours writing a program and then have to build it again because some person says that it can be built using python instead of building on it.

---

### Post by chandru.in on 2008-01-06
True.  I understand.  But hey I remember ppl started Gnome only becoz KDE was risky as it needed Qt, which was not free then.  Mono may be free as such today.  But it is dependant on .Net (non-free) for its future direction.

I would have started with Python version if I knew Python so well.  Unfortunately I have just started learning it.

---

### Post by smartboyathome on 2008-01-06
Then until you start working on it, don't expect others to. And until Tomboy and F-Spot are ported, don't expect mono to come out.

---

### Post by chandru.in on 2008-01-06
I at least hope you'd accept that Mono's future plans is dependent only on where MS takes .Net and Python doesn't have that problem.

---

### Post by smartboyathome on 2008-01-06
Mono does depend on .Net somewhat, but it also can impliment old specs making things that aren't compatible with Windows compatible with Linux.

And while python doesn't have that problem, it still has the problem of not everyone on windows knowing it.

---

### Post by chandru.in on 2008-01-06
But it cannot add new features which can give an edge on Linux.

---

### Post by smartboyathome on 2008-01-06
Yes it can. Do you not call tomboy and F-Spot "features"? I do. Yes, it doesn't make all new commands for Linux, but it does impliment a commonly known language.

---

### Post by chandru.in on 2008-01-06
Hey I know many developers who do not know C# too.  Apple Mac OS X is happily gaining market share without worrying about not everyone windows knowing Cocoa.

Tomboy anf F-spot are nice apps built using Mono.  They are not features of Mono itself.

---

### Post by [h2o] on 2008-01-06
> **chandru.in said:**
> But it cannot add new features which can give an edge on Linux.
The question is whether it needs to do that to have some kind of "right to live".
It does what it shall and obviously quite good since a lot of ppl choose to program with it.
As far as I know there hasn't been any new features put into C to give it "an edge on Linux" lately either ;)

---

### Post by chandru.in on 2008-01-06
C is very different from Mono.  I don't mind having a C# compiler through Mono as it is an ISO language just as C and C++.

But the risk is in the class libraries, which Mono depends heavily on.

When I said edge I meant it cannot have its own development path without depending on the activities of an enemy of Linux.

---

### Post by emperon on 2008-01-06
mono's extra features from .net includes the following (they are part of mono but .net and no counterpart in .net)

    *  Gtk# ([http://gtk-sharp.sf.net):](http://gtk-sharp.sf.net):) Bindings for the popular Gtk+ GUI toolkit for UNIX and Windows systems. Other bindings are available: Diacanvas-Sharp and MrProject. 

    * #ZipLib ([http://www.icsharpcode.net/OpenSource/SharpZipLib/Default.aspx):](http://www.icsharpcode.net/OpenSource/SharpZipLib/Default.aspx):) A library to manipulate various kinds of compressed files and archives (Zip and tar). 



    * Mono.Directory.LDAP / Novell.Directory.LDAP: LDAP access for .NET apps. 

    * Mono.Data: We ship support for PostgreSQL, MySQL, Firebird, Sybase ASE, IBM DB2, SQLite, Microsoft SQL Server, Oracle, and ODBC data sources. 

    * Mono.Cairo: Bindings for the Cairo ([http://www.cairographics.org](http://www.cairographics.org)) rendering engine (Our System.Drawing is implemented on top of this). 

    * Mono.Posix / Mono.UNIX: Bindings for building POSIX applications using C#. 

    * Mono.Remoting.Channels.Unix: Unix socket based remoting 

    * Mono.Security: Enhanced security and crypto framework 

    * Mono.Math: BigInteger and Prime number generation 

    * Mono.Http: Support for creating custom, embedded HTTP servers and common HTTP handlers for your applications. 

    * Mono.XML: Extended support for XML 

    * Remoting.CORBA ([http://remoting-corba.sourceforge.net/):](http://remoting-corba.sourceforge.net/):) A CORBA implementation for Mono. 

    * Ginzu: An implementation on top of Remoting for the ICE ([http://www.zeroc.com](http://www.zeroc.com)) stack

---

### Post by chandru.in on 2008-01-07
I'm not a Mono developer exactly so I cannot comment directly on these.

But some of them are not really extensions, they are just Linux/Unix equivalents for certain technologies used by .Net (GTK#, LDAP, Cairo and Unix sockets).

I'm sure MS will not sue Red Hat, canonical, IBM or HP directly, for the fear of counter suits.

Can someone confirm that MS will not sue startups using Mono over the VB .Net and ASP .Net parts which are not ISO standards?  Also, MS has patents outside US too.  Will OIN help small companies outside US, which use Mono?

These questions are genuine ones, not arguments.  So please clarify my doubts.

---

### Post by emperon on 2008-01-07
> **chandru.in said:**
> I'm not a Mono developer exactly so I cannot comment directly on these.

But some of them are not really extensions, they are just Linux/Unix equivalents for certain technologies used by .Net (GTK#, LDAP, Cairo and Unix sockets).

I'm sure MS will not sue Red Hat, canonical, IBM or HP directly, for the fear of counter suits.

Can someone confirm that MS will not sue startups using Mono over the VB .Net and ASP .Net parts which are not ISO standards?  Also, MS has patents outside US too.  Will OIN help small companies outside US, which use Mono?

These questions are genuine ones, not arguments.  So please clarify my doubts.

They are not .NET Equivalents. because mono already has most of .net things. 

And your question: ASP.NET , Winforms and ADO.NET are patentted technologies by MS. Although their implementations has done with carefully investigating for possible patent infringes,  the answer is no. Note that however It is extremely unlikely that MS will sue you for this. Finally I cannot say, they can't do it or they can do it. I am aware there are some major companies using mono /ASP.NET

The good thing is actually you don't have to use any of these technologies and still develop web applications. (As long as you extend HTTPHandler ...) .

However ,For gnome parts applications like Tomboy and F-spot , gtk# you are 100% safe.

I think the best thing would be dropping a mail list to mono-devel-list , if you want to be sure.

---

### Post by chandru.in on 2008-01-07
Thanks for the patient reply.  Just one more Q.  Does Ubuntu Live CD ship with support for ASP .Net and ADO .Net too or is it just the C# and GTK# related stuff.

I'm not able to make this out from the names of the packages installed.  R these packages the ones providing these?

libmono-system-data2.0-cil
libmono-system-web2.0-cil

Can you shed some light on this too?

---

### Post by st4rdr1ft3r on 2008-01-07
web provides the asp.net stuff for sure.

---

### Post by chandru.in on 2008-01-07
Thanks for the clarification

---

### Post by st4rdr1ft3r on 2008-01-07
after a quick read, data is indeed ado.net, i've never bothered learning the terminology.

---

### Post by chandru.in on 2008-01-07
K thanks for that too.

---

### Post by neighborlee on 2008-02-12
> **T_W said:**
> REMOVE.  

I migrated from beagle to tracker with Gutsy.

Its amazing how much faster and efficient tracker is over beagle.

I have no interest in F-Spot or Tomboy and don't want this risky tech on my system.

I totally agree,  especially considering the memory footprint, MB usage on install CD and fact gnome already has a note taker; to me the M$ FUD machine behind MONO is only a surplus bonus for removing mono ;)

cheers
nl

---

### Post by smartboyathome on 2008-02-12
Those arguments have been heard and people said that it doesn't take up much of the CD and the functionality it provides over other apps is great enough to leave it in.

---

### Post by neighborlee on 2008-02-12
> **smartboyathome said:**
> Those arguments have been heard and people said that it doesn't take up much of the CD and the functionality it provides over other apps is great enough to leave it in.

I dont agree at all , at least according to the voting results and last time I checked, this was a democracy :)

I found beagle to be VERY slow not to mention what it does to ones HD from all the nasty 'swapping', and nasty slowdown to my system.  It is also a fact as I recall that fedora ? removed it entirely so  that does beg the question, as  I also  recall they noted it was not stable .  I 'dont need' fspot and notetaking is already in gnome  so coupled with the 100MB or so usage on install CD, and the 'fact' that M$ has not released all the patent specs I dont understand why ubuntu would consider leaving it in.  If someone wants it its a simple  apt-get install and I agree also build-essential is FAR more important ;)

The facts for removing it far outweigh those for leaving it in unless people around here dont like facts ;)

cheers
nl

---

### Post by chandru.in on 2008-02-12
There quite a few Mono lovers here.  They have even entered other threads and suggested that Rhythmbox be replaced by Banshee, though the poll was about Exaile (A far more feature-rich player than Banshee).

So no point arguing here.  :-(

---

### Post by smartboyathome on 2008-02-12
> **neighborlee said:**
> I dont agree at all , at least according to the voting results and last time I checked, this was a democracy :)

I found beagle to be VERY slow not to mention what it does to ones HD from all the nasty 'swapping', and nasty slowdown to my system.  It is also a fact as I recall that fedora ? removed it entirely so  that does beg the question, as  I also  recall they noted it was not stable .  I 'dont need' fspot and notetaking is already in gnome  so coupled with the 100MB or so usage on install CD, and the 'fact' that M$ has not released all the patent specs I dont understand why ubuntu would consider leaving it in.  If someone wants it its a simple  apt-get install and I agree also build-essential is FAR more important ;)

The facts for removing it far outweigh those for leaving it in unless people around here dont like facts ;)

cheers
nl

It doesn't take 100MBs of CD space. And Fedora is a different distro with different goals. You might not need F-Spot, but what about others? There are probably many, many people who use it to organize their pics. And GNOME's panel note program isn't NEARLY as feature rich as Tomboy.  Build-essential is not as important, because Ubuntu does not want people to compile.

Also, this isn't a democracy. Ubuntu is a meritocracy (see [here]("http://www.ubuntu.com/community/processes/governance")). It does not always go by what the users want. And by the poll, there is no clear winner or loser, just a simple majority of removing it (which imo isn't enough to take it out).

---

### Post by chandru.in on 2008-02-12
May I know the real merits of Mono which Python/Java doesn't provide?

---

### Post by smartboyathome on 2008-02-12
Like said before, it provides most of the implimentation of .Net, allowing more programs to be ported in less time than having to rewrite the whole thing in a new language (which basically means starting from scratch). And acting like they should HAVE to write it from scratch will just keep the businesses porting programs even farther away from Linux.

---

### Post by chandru.in on 2008-02-12
Porting apps is fine.  But very little chance.  Do u think all .Net developers write their .Net code keeping in mind which subset is implemented by Mono.

Also, I have no issues in leaving mono in repos.  It deserves a place in repos.  If I'm going to use a windows program ported using mono, I'll happily download it.  After all it not so huge (by your words) so downloading is not that difficult.

---

### Post by 23meg on 2008-02-12
[QUOTE=neighborlee]and I agree also build-essential is FAR more important[/QUOTE]

[QUOTE=smartboyathome] Build-essential is not as important, because Ubuntu does not want people to compile.[/QUOTE]

build-essential is on the CD.

---

### Post by nfm on 2008-02-12
.NET is a part of MS OS, therefore mono is part of MS and it's evil. I would rather have C\C++\Python apps instead of inefficient .NET. I like Banshee because of nice startup screen and how it connects to last.fm showing similar artists & top tracks. While using it and changing radio station or mp3s it keeps randomly crashing and freezing. But other than that it uses to much memory and it's slow. .NET is something with should avoid at all costs, C# by itself is alright. .NET to me is garbage.

---

### Post by neighborlee on 2008-02-13
> **23meg said:**
> build-essential is on the CD.

That is odd but good to know; I and many others clearly were not aware of this  , because I dont recall at all apt-get install telling me to insert CD, but I believe you np and thx for info.

I can say with total certainty that I always removed beagle , hating the nasty nasty hit my HD always took from indexing,though windows  never seems to do that at all, go figure.

Its clear also from fedora removing beagle that its certainly NOT the best technology and I'd go so far as to say one of THE worst.  OPensuse and fedora users are  DEFinitely not happy with it either if you check out this thread:

[http://linux.derkeiler.com/Mailing-Lists/SuSE/2008-01/msg01320.html](http://linux.derkeiler.com/Mailing-Lists/SuSE/2008-01/msg01320.html)

[http://www.digg.com/linux_unix/HowTo_Remove_or_Disable_Beagle_in_Fedora_Core_6](http://www.digg.com/linux_unix/HowTo_Remove_or_Disable_Beagle_in_Fedora_Core_6)

[http://forums.fedoraforum.org/forum/showthread.php?t=176291&highlight=beagle](http://forums.fedoraforum.org/forum/showthread.php?t=176291&highlight=beagle) < as you seee here from  Wayne's post..EVEN FEDORA, the hardcore 'testing distro' does NOT install beagle anymore now starting with fedora 8 so yet again another indication of how  WELL .NET apps are written and how silly it is for anyone to suggest using them when so many People have troubles with them.  There are great alternatives TO THEM and considering that you save almost 50MB in  diskspace so something else could just as well fit on CD, and the totally IFFY patent crap we all know and love so well I see no reason whatsoever to include this. I mean tracker is already in place n ow in ubuntu so whats up with the rest ? :))

Its clear most users here dont want it , and its good to hear from the community :)

THe fact that .NET isn't fullly disclosed, and the weird 'deal' with novel, and considering they recently sued novel and redhat, its at the very least disconcerting.

Why bother supporting a nonstandard ( winforms is not oss is it ? ), when java is now free and soon to be used 'as' a standard (icedtea ). Java even has its own game engine ( jME ) which looks very decent so this java  scare is unworthy ;)

"" Mono's strategy for dealing with any potential issues that might arise with ASP.NET, ADO.NET or Windows.Forms is: (1) work around the patent by using a different implementation technique that retains the API, but changes the mechanism; if that is not possible, we would (2) remove the pieces of code that were covered by those patents, and also (3) find prior art that would render the patent useless. ""

work around the patent ??

also: from hairy_Palms

"" wrong, its only partly open, as soon as they started implementing asp.net and VB.net it is no longer entirely standards based, and besides weve all seen how much an ECMA standard is worth with the ridiculous OOXML spectacle.
"" < if true this also is of great concern isn't it , and what about the latest M$ suit of redhat and suse , is that stilll going on...

cheers
nl

---

### Post by smartboyathome on 2008-02-13
If Mono isn't good, then tell me a great replacement for F-Spot that does everything it does? As far as I know, F-Spot is one of the best photo organizers for Linux.

Also, tell me an app that has as many features, and is as well organized as Tomboy?

---

### Post by 23meg on 2008-02-13
As has been said, Ubuntu is shipping Mono only in an effort to support the two default applications that require it: F-Spot and Tomboy. In the light of this fact, some homework for the anti-Mono people: find out whether these two applications actually implement any non-ECMA standardized parts of Mono, such as Windows.Forms. While the existence of these parts can be arguments against Mono itself, whether they can be arguments against the inclusion of Mono in Ubuntu by default (which is what this thread is supposed to be about) depends on whether they're actually used in Ubuntu.

---

### Post by neighborlee on 2008-02-13
> **smartboyathome said:**
> If Mono isn't good, then tell me a great replacement for F-Spot that does everything it does? As far as I know, F-Spot is one of the best photo organizers for Linux.

Also, tell me an app that has as many features, and is as well organized as Tomboy?

zim is an alternative for Tomboy. For starters, it does have wiki-style hyperlinks thus seems to be more feature complete then Sticky Notes. From the feature comparison between Tomboy and Sticky Notes:

    *

      Tomboy has note synchronization: (already mentioned) to be accomplished with conduit or any other generic sync framework (e.g. rsync, etc.)
    *

      Tomboy has export to HTML: zim includes this feature
    *

      Tomboy has Wiki-like linking in notes: zim includes this feature
    *

      Tomboy can do rich text formatting.: zim includes this feature
 

on fspot vs g-thumb:

Overall, these applications are very much similar and including both of them does not make much sense. Having both could make some users confused as their functionality is so similar. I think the handling of movies by gThumb makes gThumb the winner in features. Most people who have a digital camera are going to eventually try the take a movie feature in it. Being able to easily import that into Ubuntu is very important for them.

Its clear for reasons of patent , features and CD space , memory usage and stability that there is no reason to utilize MONO. It can easily be handled through synaptic.

cheers
nl

---

### Post by Jan-Nik on 2008-02-13
> **neighborlee said:**
> There are great alternatives TO THEM and considering that you save almost 50MB in  diskspace so something else could just as well fit on CD, and the totally IFFY patent crap we all know and love so well I see no reason whatsoever to include this.

AFAIK it's only 9 MB:
```
jhasse@jnsamsung:~$ sudo apt-get install f-spot tomboy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil
  libmono-system2.0-cil libmono0 libmono2.0-cil libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil
Suggested packages:
  libsqlite0 libmono-winforms2.0-cil
The following NEW packages will be installed:
  f-spot libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil
  libmono-system2.0-cil libmono0 libmono2.0-cil libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil tomboy
0 upgraded, 13 newly installed, 0 to remove and 0 not upgraded.
Need to get **9022kB** of archives.
After unpacking 30.2MB of additional disk space will be used.
Do you want to continue [Y/n]? 
```

---

### Post by smartboyathome on 2008-02-13
> **neighborlee said:**
> zim is an alternative for Tomboy. For starters, it does have wiki-style hyperlinks thus seems to be more feature complete then Sticky Notes. From the feature comparison between Tomboy and Sticky Notes:

    *

      Tomboy has note synchronization: (already mentioned) to be accomplished with conduit or any other generic sync framework (e.g. rsync, etc.)
    *

      Tomboy has export to HTML: zim includes this feature
    *

      Tomboy has Wiki-like linking in notes: zim includes this feature
    *

      Tomboy can do rich text formatting.: zim includes this feature
 

on fspot vs g-thumb:

Overall, these applications are very much similar and including both of them does not make much sense. Having both could make some users confused as their functionality is so similar. I think the handling of movies by gThumb makes gThumb the winner in features. Most people who have a digital camera are going to eventually try the take a movie feature in it. Being able to easily import that into Ubuntu is very important for them.

Its clear for reasons of patent , features and CD space , memory usage and stability that there is no reason to utilize MONO. It can easily be handled through synaptic.

cheers
nl

Actually, gThumb doesn't include any way to ORGANIZE AND TAG photos for easy viewing. F-Spot does a wonderful job of this. F-Spot also is a photo organizer for ie digital cameras, while gThumb is only a photo viewer.

Tomboy looks nicer overall than Zim in my opinion. Zim organizes stuff similar to sections in a book's table of contents, while Tomboy organizes stuff in "notes", which in my opinion is easier to understand and looks better. Couple that with all the features it has besides the sticky note panel item and you got a great program which in my opinion is more worth keeping.

> **Jan-Nik said:**
> AFAIK it's only 9 MB:
```
jhasse@jnsamsung:~$ sudo apt-get install f-spot tomboy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil
  libmono-system2.0-cil libmono0 libmono2.0-cil libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil
Suggested packages:
  libsqlite0 libmono-winforms2.0-cil
The following NEW packages will be installed:
  f-spot libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil
  libmono-system2.0-cil libmono0 libmono2.0-cil libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil tomboy
0 upgraded, 13 newly installed, 0 to remove and 0 not upgraded.
Need to get 9022kB of archives.
After unpacking **30.2MB** of additional disk space will be used.
Do you want to continue [Y/n]? 
```

Its 30 mbs, I bolded the actual number you should be looking at. It will take away a lot less from the install cd (approx. 3x less), meaning it will probably free only ~10 mbs of space.

---

### Post by neighborlee on 2008-02-13
> **smartboyathome said:**
> Actually, gThumb doesn't include any way to ORGANIZE AND TAG photos for easy viewing. F-Spot does a wonderful job of this. F-Spot also is a photo organizer for ie digital cameras, while gThumb is only a photo viewer.

Tomboy looks nicer overall than Zim in my opinion. Zim organizes stuff similar to sections in a book's table of contents, while Tomboy organizes stuff in "notes", which in my opinion is easier to understand and looks better. Couple that with all the features it has besides the sticky note panel item and you got a great program which in my opinion is more worth keeping.

Its 30 mbs, I bolded the actual number you should be looking at. It will take away a lot less from the install cd (approx. 3x less), meaning it will probably free only ~10 mbs of space.

IMO,  thats fine, but its not enough to warrant extra space on a CD ( name  your amount, even 1 is too much when alternatives clearly exist ) and extra bloat, patent problems, memory consumption and stability problems, not to mention   that all other distros are also having trouble with it &/or completely removing it. I guess for them being able to yum install f-spot is enough ;) ( dont EVEN get me started on SUSE where trying to remove mono/fspot -whatever- is  met with TONS Of dependency  issues--I guess they try to LOCK you in ;) <no thanks>

The facts speak loudly against mono and  the community clearly  has more saying we dont want it, and its also  those of other distros as well,  as I noted.  You can't pin the requirement of an entire  bloated, patent encumbered, buggy memory consumptive codebase on the merits of a few 'looks nicer' opinions , especially when the 'few' features they might have extra, are easiliy coded into 'current' , existing FOSS applications ;).  

I never bother with spot when I want to bring in pictures from my     d-camera or wherever ( though  gthumb being able to handle animations is clearly a superior feature and one I was not aware of ), and I never use tomboy notes but thats just me..Im willing to bet most people dont either ;  and we definitely know what happened to beagle  o_0 .

cheers
nl

---

### Post by smartboyathome on 2008-02-13
> **neighborlee said:**
> IMO,  thats fine, but its not enough to warrant extra space on a CD ( name  your amount, even 1 is too much when alternatives clearly exist ) and extra bloat, patent problems, memory consumption and stability problems, not to mention   that all other distros are also having trouble with it &/or completely removing it. I guess for them being able to yum install f-spot is enough ;) ( dont EVEN get me started on SUSE where trying to remove mono/fspot -whatever- is  met with TONS Of dependency  issues--I guess they try to LOCK you in ;) <no thanks>

The facts speak loudly against mono and  the community clearly  has more saying we dont want it, and its also  those of other distros as well,  as I noted.  You can't pin the requirement of an entire  bloated, patent encumbered, buggy memory consumptive codebase on the merits of a few 'looks nicer' opinions , especially when the 'few' features they might have extra, are easiliy coded into 'current' , existing FOSS applications ;).  

I never bother with spot when I want to bring in pictures from my     d-camera or wherever ( though  gthumb being able to handle animations is clearly a superior feature and one I was not aware of ), and I never use tomboy notes but thats just me..Im willing to bet most people dont either ;  and we definitely know what happened to beagle  o_0 .

cheers
nl

I have never experienced a crash with F-Spot or Tomboy, so the stability issues are FUD imo. There also aren't any patent problems. Show me where it infringes a patent. It doesn't take up much memory for me, either. Just because other distros can remove it, but Ubuntu doesn't have to.

The community hasn't said that it wants to remove it, look at the poll, only 56% want it removed. The people who want it removed are more vocal, though. It has just as much right to be in Ubuntu as perl (which would be needed for Zim).

---

### Post by CarpKing on 2008-02-14
> **smartboyathome said:**
> Actually, gThumb doesn't include any way to ORGANIZE AND TAG photos for easy viewing. F-Spot does a wonderful job of this. F-Spot also is a photo organizer for ie digital cameras, while gThumb is only a photo viewer.

You can assign any number of "categories" to an image, which sounds a lot like tags to me.  Also, gThumb does in fact deal with digital cameras.  In fact I think in Gutsy it is the default for that purpose.  It always pops up when I plug mine in, and I don't recall ever setting it to do so.

---

### Post by 23meg on 2008-02-14
FYI, gThumb has been removed from the default install in Hardy.

---

### Post by cb951303 on 2008-02-14
Simon G Best: Why don't we remove GNOME too since it's been started by Miguel de Icaza too :)

---

### Post by neighborlee on 2008-02-14
> **23meg said:**
> FYI, gThumb has been removed from the default install in Hardy.

If it has I wont be using ubuntu anymore..exactly who do I ask for reason WHY this was done ?

cheers
nl

---

### Post by 23meg on 2008-02-14
[QUOTE=neighborlee]If it has I wont be using ubuntu anymore..exactly who do I ask for reason WHY this was done ?[/QUOTE]

You don't have to ask anyone; it's written in a blueprint drafted months ago. The goal is reducing duplication in the LTS release in order to lighten up the maintenance load for the long support period. See the relevant blueprint; lots of other libraries and applications were removed as well:

[https://blueprints.launchpad.net/ubuntu/+spec/hardy-reducing-duplication](https://blueprints.launchpad.net/ubuntu/+spec/hardy-reducing-duplication)

---

### Post by neighborlee on 2008-02-14
> **cb951303 said:**
> Simon G Best: Why don't we remove GNOME too since it's been started by Miguel de Icaza too :)

Well isn't that one of the silliest suggestions I"ve ever seen..gnome/gtk is lgpl which affords the most freedom as compared to kde/qt..I think its clear which one should be removed and which one supported if we come at it from that perspective.ONe is entirely free and one has 'hooks'  .hm kinda like .net ;)

cheers
nl

---

### Post by pro-rsoft on 2008-02-14
Please keep gThumb in.... I like gThumb because it starts 10x faster than f-spot, if i quickly want to view/resize an image i don't have the patience to start a heavy program. Also, eog is basically the same as gThumb but has less features.

---

### Post by smartboyathome on 2008-02-14
> **neighborlee said:**
> Well isn't that one of the silliest suggestions I"ve ever seen..gnome/gtk is lgpl which affords the most freedom as compared to kde/qt..I think its clear which one should be removed and which one supported if we come at it from that perspective.ONe is entirely free and one has 'hooks'  .hm kinda like .net ;)

cheers
nl

Mono is completely free and is licensed under the GPL. So you can't say it "isn't free enough to be in Ubuntu".

---

### Post by neighborlee on 2008-02-14
> **smartboyathome said:**
> Mono is completely free and is licensed under the GPL. So you can't say it "isn't free enough to be in Ubuntu".

"  Microsoft product because they filed only a part of the .NET framework for standardization. Conveniently leaving out System.WinForms etc  "

If .NET is so 'open' why was winforms not filed for standardization ?

I am not trying to be cute here, I really want to know , because it does seem sillly to pretend that something is open, if part of it is not.

you all just attempt to gloss over relevant issues by not commenting on them,what about this:

also: from hairy_Palms

"" wrong, its only partly open, as soon as they started implementing asp.net and VB.net it is no longer entirely standards based, and besides weve all seen how much an ECMA standard is worth with the ridiculous OOXML spectacle.
"" < if true this also is of great concern isn't it , and what about the latest M$ suit of redhat and suse , is that stilll going on...

I would like to know what others think about this and if it affects mono in ubuntu or not....

cheers
nl

---

### Post by smartboyathome on 2008-02-14
> **neighborlee said:**
> "  Microsoft product because they filed only a part of the .NET framework for standardization. Conveniently leaving out System.WinForms etc  "

If .NET is so 'open' why was winforms not filed for standardization ?

I am not trying to be cute here, I really want to know , because it does seem sillly to pretend that something is open, if part of it is not.

you all just attempt to gloss over relevant issues by not commenting on them,what about this:

also: from hairy_Palms

"" wrong, its only partly open, as soon as they started implementing asp.net and VB.net it is no longer entirely standards based, and besides weve all seen how much an ECMA standard is worth with the ridiculous OOXML spectacle.
"" < if true this also is of great concern isn't it , and what about the latest M$ suit of redhat and suse , is that stilll going on...

I would like to know what others think about this and if it affects mono in ubuntu or not....

cheers
nl

It should not affect Ubuntu at all. If I heard right, Microsoft hasn't said which patents the companies violate, so it might not be about mono.

---

### Post by cb951303 on 2008-02-14
> **neighborlee said:**
> Well isn't that one of the silliest suggestions I"ve ever seen..gnome/gtk is lgpl which affords the most freedom as compared to kde/qt..I think its clear which one should be removed and which one supported if we come at it from that perspective.ONe is entirely free and one has 'hooks'  .hm kinda like .net ;)

cheers
nl

should we assume that WINE is not free too? since it's covered with "hooks" all over?

mono is just an open source implementation of .NET (well some of it) it's GPL'ed and doesn't have any hooks. Why can't you enjoy it? :)

---

### Post by Simon G Best on 2008-02-14
This thread's still going?

> **smartboyathome said:**
> The community hasn't said that it wants to remove it, look at the poll, only 56% want it removed.

"Only 56%"?  Whereas an enormous 44% want to keep it.  Clearly the community wants to keep Mono, as only a majority want to remove it from the default installation.

But seriously: if 56% isn't enough to justify removing Mono, then how on earth can 44% be enough to justify keeping it?  It can't.

Mono fans: just give it up.

---

### Post by CarpKing on 2008-02-14
> **neighborlee said:**
> If it has I wont be using ubuntu anymore..exactly who do I ask for reason WHY this was done ?

cheers
nl

You can always install it again (I'm sure it will still be in the repos).  In fact, if you upgrade it probably won't be uninstalled.

---

### Post by smartboyathome on 2008-02-15
> **Simon G Best said:**
> This thread's still going?



"Only 56%"?  Whereas an enormous 44% want to keep it.  Clearly the community wants to keep Mono, as only a majority want to remove it from the default installation.

But seriously: if 56% isn't enough to justify removing Mono, then how on earth can 44% be enough to justify keeping it?  It can't.

Mono fans: just give it up.

56% is only a simple majority. In order to be removed (in my opinion) at least 70% of people should want to remove it. 44% of people is quite a lot that want to keep it.

The people who want to get rid of mono should give up. It is staying in Ubuntu for now until there are programs written without mono which can replace them to the dev's liking.

---

### Post by 23meg on 2008-02-15
> **Simon G Best said:**
> This thread's still going?



"Only 56%"?  Whereas an enormous 44% want to keep it.  Clearly the community wants to keep Mono, as only a majority want to remove it from the default installation.

But seriously: if 56% isn't enough to justify removing Mono, then how on earth can 44% be enough to justify keeping it?  It can't.

Mono fans: just give it up.

People who have voted on a random forum thread != "The community"

---

### Post by neighborlee on 2008-02-15
> **23meg said:**
> FYI, gThumb has been removed from the default install in Hardy.

It would seem from:

[https://blueprints.launchpad.net/ubuntu/+spec/hardy-reducing-duplication](https://blueprints.launchpad.net/ubuntu/+spec/hardy-reducing-duplication)

that not all that much discsussion was centered around the merits of what was proposed here.

This was all decided on the merit of   'it looks prettier' and has a few more   features than gthumb ?

[http://gthumb.sourceforge.net/features.html](http://gthumb.sourceforge.net/features.html) < like what..tell me what that is and Ill start talks with the devleoper to create them.

While Im at it,  shall we  discuss why everyone on MONO side has ignored these as I would like to know what makes fpsot and tomboy so amazing and programmed so well to keep, while beagle seemed to         be weighed down in misery  like a nova sun.

[http://linux.derkeiler.com/Mailing-L.../msg01320.html](http://linux.derkeiler.com/Mailing-L.../msg01320.html)

[http://www.digg.com/linux_unix/HowTo..._Fedora_Core_6](http://www.digg.com/linux_unix/HowTo..._Fedora_Core_6)

[http://forums.fedoraforum.org/forum/...ghlight=beagle](http://forums.fedoraforum.org/forum/...ghlight=beagle)

I have no problem with change as long as its viable as discussed from  all angles and has the support of a  clear majority of devleopers and users. This  might be a meritocracy, but at the end of the day the 'users' voices shall not be  flattened strong.

cheers
nl

---

### Post by 23meg on 2008-02-15
[QUOTE=neighborlee]It would seem from:

[https://blueprints.launchpad.net/ubu...ng-duplication](https://blueprints.launchpad.net/ubu...ng-duplication)

that not all that much discsussion was centered around the merits of what was proposed here.[/QUOTE]

It's been discussed at length on the ubuntu-devel-discuss mailing list and desktop team meetings.

[QUOTE=neighborlee]This was all decided on the merit of 'it looks prettier' and has a few more features than gthumb ?[/QUOTE]

Who said that? Where do you get that idea?

---

### Post by neighborlee on 2008-02-15
> **23meg said:**
> It's been discussed at length on the ubuntu-devel-discuss mailing list and desktop team meetings.

I dont recall seeing BM discussed in any REAL length , so that needs resolved ( unlesss I missed it )

[/quote]Who said that? Where do you get that idea?[/QUOTE]

[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-January/003101.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-January/003101.html)

I also see no real discussion on the gquigs remove-mono notice, and he seemed VERY surprised to see gthumb removed in favor of fspot ,unless he was just asleep at the wheel.

I think BM looked wondeful, and FAR nicer ( feature wize not sure ) than fspot, but SHRUG then its java :)

cheers
nl

---

### Post by 23meg on 2008-02-15
[QUOTE=neighborlee]I dont recall seeing BM discussed in any REAL length , so that needs resolved ( unlesss I missed it )[/QUOTE]

You can resolve it by bringing it up if you have good arguments for its inclusion. 

[QUOTE=neighborlee]https://lists.ubuntu.com/archives/ub...ry/003101.html[/QUOTE]

That's one person's comment. There are other comments as well.

[QUOTE=neighborlee]I also see no real discussion on the gquigs remove-mono notice, and he seemed VERY surprised to see gthumb removed in favor of fspot ,unless he was just asleep at the wheel.[/QUOTE]

The fact that gThumb and F-Spot have partially overlapping functionality has been discussed for a long time, ever since F-Spot was included by default, without any necessary association with Mono. It's evident that ideally one of these applications has to go; the reason this is being resolved now is that we're having an LTS release. If you volunteer to do a comprehensive, unbiased, technical comparison of both software on factual (not anecdotal) grounds, taking features, bug history and security into account, I'm sure people will pay attention and evaluate it.

---

### Post by Ratatosk on 2008-02-16
Oh dear, I just recently returned to Linux and felt very good about it. And then I stumbled upon this topic that had previously slipped past me. (That is, I remember reading about Mono a while ago and then only thought about it as yet one more nice and interesting development on Linux.)

So, struck with panic, I first paged through a couple of discussion threads on this, and then went on to google for more info. And, although a few of my initial fears have been alleviated slightly, I voted yes with conviction on this one.
In other words: Don't *pre-install* Mono! By all means, include it in the repositories, main if you like, but, please, please, **don't *preinstal*l it!**

(And if it is absolutely impossible to achieve this until next release, at least please make it a commitment to work in that direction. I.e. seek replacements for F-Spot and Tomboy and, whatever you do, at least don't add any furter Mono stuff!)
__________

Amazingly, considering how much has been written about this, I don't think I have so far seen anyone respond to what by far seems to be the major concern with Mono. (I have seen a number of people *state* the problem, though, and apologies if I have just been blind and missed a response to it.)


[FONT="Arial"][SIZE="4"]**1) Non-issues**[/SIZE][/FONT]

First, allow me to brashly brush aside what I perceive to be mostly or wholly non-issues:
[INDENT]- The **technical capabilities** of Mono? I have no doubt it is "way cool" in this respect.
 
- The **space** taken up by Mono and applications? The MB's of the specifically included stuff, hardly a big problem. (Though, more generally, it does seem that Mono-applications tend to take up much more space than corresponding non-Mono applications.)

- An intrinsic **evil of Microsoft**? No, not that either. In fact, I think Microsoft may be decidedly better than most other companies would have been in its position. Just one example: Although Microsoft has acquired vast numbers of the thoroughly evil and destructive things called software patents, this could originally be seen largely as a mere defense against in particular IBM, who has even more of them.[/INDENT]


[FONT="Arial"][SIZE="4"]**2) Microsoft and the free software community**[/SIZE][/FONT]

Absence of Microsoft intrinsic evil obviously doesn't mean there is no problem. Everybody who isn't completely blind (/devoted to Microsoft) knows there is one, though not so much with Microsoft itself as with its position. ***See [[COLOR="Blue"]bug #1[/COLOR]]("https://launchpad.net/ubuntu/+bug/1")!*** (And power corrupts, remember?)

Furthermore, the community around Linux, and other open and free (as in [[COLOR="Blue"]libre, *not* merely gratis[/COLOR]]("http://en.wikipedia.org/wiki/Gratis_versus_Libre")) software, is in a particularly delicate spot. After all, there isn't that much else left of the competition to Microsoft. Microsoft's view on the [[COLOR="Blue"]GPL license[/COLOR]]("http://en.wikipedia.org/wiki/GNU_General_Public_License") - and the software based on it (including Linux) - has for a long time been truly exceptional, likening it to cancer, virus, communism etc. And it seems that Microsoft has in the very latest years decided to even further step up its efforts to squash it. If, in the past, there was the perceived safety of Linux moving mostly "below the radar" of Microsoft, that definitely isn't true anymore.

In the context of explaining .NET in 2002, according to [[COLOR="Blue"]New York Times[/COLOR]]("http://query.nytimes.com/gst/fullpage.html?res=9C00EED71338F936A15754C0A9649C8B63"), Microsoft had this to say:
> Microsoft also warned today that the era of ''open computing,'' the free exchange of digital information that has defined the personal computer industry, is ending.
 
The company is trying to influence an industry consortium called the Trusted Computing Platform Alliance, which has been trying to create a new standard that will build a cryptographic key system into future personal computers.
And the following articles give a detailed insight into Microsoft's new war:
[INDENT]- [[COLOR="Blue"]*This is War*[/COLOR]]("http://www.forbes.com/forbes/2004/0816/065_print.html") - Forbes (Victoria Murphy),  16 Aug 2004

- [[COLOR="Blue"]*Microsoft takes on the free world*[/COLOR]]("http://money.cnn.com/magazines/fortune/fortune_archive/2007/05/28/100033867/") - Fortune (Roger Parloff), 14 May 2007[/INDENT]

What happened in between those two articles was of course the disgraceful [[COLOR="Blue"]Microsoft-Novell deal[/COLOR]]("http://www.groklaw.net/article.php?story=20070930081040440"), 2nd Nov 2006. (The Forbes article seems in some ways to almost forebode it, quoting the Microsoft spokesperson as identifying Novell to be the then biggest threat to Microsoft, and describing the [[COLOR="Blue"]FUD[/COLOR]]("http://en.wikipedia.org/wiki/Fear%2C_uncertainty_and_doubt")-bullying of customers of Linux-vendors as one of the tactics employed.)

---

### Post by Ratatosk on 2008-02-16
[FONT="Arial"][SIZE="4"]**3) .NET on Linux**[/SIZE][/FONT]

The following is the early history as far as I have been able to piece it together. (Unfortunately, when writing this, many old public discussions and news articles, that might have been available on the web at the time, seem now to be lost. Also, much of the DotGNU and Portable.NET sites seem to be currently inaccessible, in particular FAQ's and wiki.) Anyway...

[SIZE="3"]**First, there was one...**[/SIZE]
Surprisingly (to me at least), the first and original free project, with the aim of a free framework for .NET applications on Linux (and Mac too), was not Mono at all but **Portable.NET** - commonly known as "**Pnet**". It was initiated by Australian developer Rhys Weatherley and made public (with a pre-alpha release) [[COLOR="Blue"]on Freshmeat[/COLOR]](http://freshmeat.net/projects/pnet/) **13 Mar 2001**.

Among those who had been in early contact with Rhys, and studied his .NET research and C# compiler solution, was Miguel de Icaza of Gnome fame. And, from what I understand, Rhys and others had expected him to continue to work with the Portable.NET project. Instead, de Icaza enlisted the help of (most of) his team of programmers in Ximian (the company of which he was co-founder) to do - silently, behind closed doors - some development on their own.

[SIZE="3"]**...then there were two.**[/SIZE]
In July, Miguel de Icaza and Ximian went public. A new, Ximian-led, open-source project, called "**Mono**" was created, and de Icaza announced [[COLOR="Blue"]the news on the dotnet mailing list[/COLOR]](http://discuss.develop.com/archives/wa.exe?A2=ind0107b&L=dotnet&T=0&F=&S=&P=21344), **9 July 2001** - without a mention of Rhys or Portable.NET. (By clicking "next in topic" you can follow the ensuing discussion.) Disregarding all the inane ramblings from Microsoft devotees about free software and GPL being communism and anti-commercialism etc. (see Microsoft FUD above), developers Jay Freeman ("Saurik") and Kunle Odutola expressed some interesting criticism. Long replies were given by first Miguel and then Rhys, again highly interesting.

[SIZE="3"]**DotGNU/Pnet vs. Ximian Mono**[/SIZE]
Two months earlier, yet another project had been formed, **DotGNU**, which however had a somewhat different focus and wider goals than the Portable.NET and Mono projects. Whereas Pnet and Mono dealt solely with the actual framework - compiler, runtime engine and class libraries - the primary concern of DotGNU was initially the web services that could be run on this framework - in particular the so called HailStorm, later ".NET My Services", of Microsoft, that at the time seemed threatening to give Microsoft unprecedented control over the web.

The idea of the DotGNU had been [[COLOR="Blue"]presented **7 May 2001** on a mailing list[/COLOR]](http://lists.topica.com/lists/FreeDevelopers/read/message.html?mid=1706624263&sort=d&start=2200) for free software developers, and it was blessed by FSF as an official GNU project in July, simultaneously with the, then created, Mono project (called "Gnu Mono" in [[COLOR="Blue"]FSF's initial press release[/COLOR]](http://www.linuxdevices.com/news/NS9684069071.html)). Why the older Portable.NET was overlooked by FSF I can only guess, but presumably it must have seemed natural to support Miguel de Icaza, front figure of Gnome, the GNU desktop. (Incidentally, de Icaza seems to have been [[COLOR="Blue"]affronted rather than flattered by this GNU support[/COLOR]](http://www.internetnews.com/dev-news/article.php/3361991) - apparently feeling that FSF had stolen his spotlight - and Mono has consistently been pushed as a Ximian-only - now Novell - project.) Very soon, though, 27 July, Portable.NET merged with DotGNU and became - by far - its most important sub-project.

Though Ximian was clearly way ahead of the DotGNU/Pnet idealists in the area of marketing, the two projects seem, for a long time, to have been roughly equal in technical development level (each with its strengths and weaknesses). This was to change after August 2003, when Novell bought Ximian and de Icaza suddenly had some 20 full-time developers, paid by Novell, at his disposal where he had previously had less than a handful.

[SIZE="3"]**Differences**[/SIZE]
The two projects differ in technical design as well as in goals and philosophy.

Technically, although primarily a .NET-compatible framework, DotGNU Pnet has from the start aimed for independence from languages and bytecode formats defined by Microsoft - or by any single one else. Thus its compiler (written in C) can already compile both C# and C (apparently in the same source file even) and aims to support compiling into other bytecode formats than .NET CIL - including Java and Perl 6 Parrot bytecode. And, similarly, its (as of yet only at v0.1.0) JIT is designed to support direct handling of more than one bytecode format.

By contrast, the Mono project has more unreservedly devoted itself to .NET. For one thing, its C# compiler is, interestingly, itself written in C#, originally bootstrapped from MS .NET but now self-compiling (and compiles only C#). And the Mono support for running Java bytecode comes only in the form of a .NET application (Java VM that runs on top of .NET/Mono).

The goals and philosophy could perhaps be summarized as the Ximian-led project looking more to commercial interests where the GNU project looks to principles. Originally, de Icaza seems to have considered adoption of the MS .NET technology primarily as just a tool for increasing the productivity of his Ximian programmers, whereas Rhys Weatherley had from the start stated a wish to check Microsoft's control over the new system. Thus Mono was more focused on emulating Microsoft's .NET were DotGNU prioritized standard compliance. And Mono was decidedly less worried about licensing issues than DotGNU. For one thing, in Pnet source, particularly dangerous parts (outside the standard) were apparently from the start clearly separated from the standard parts. This wasn't initially a concern in Mono, although it is now supposedly addressed.

[SIZE="3"]**Mono stance on software patents and licensing**[/SIZE]
A further example: In October 2003, Norbert Bollow of DotGNU wrote to the Mono mailing list and [[COLOR="Blue"]proposed cooperation[/COLOR]](http://lists.ximian.com/pipermail/mono-list/2003-October/016268.html) against the threat of MS patents.

[[COLOR="Blue"]The response of Miguel de Icaza[/COLOR]](http://ml.osdir.com/gnu.dotgnu.developer/2003-10/msg00054.html) to this was (disregarding a couple of insults: accusations of dishonesty and lacking programming knowledge) to make it clear that he wasn't interested in any such cooperation. And the stated reasons were in part that he didn't believe in any legal threats, but also that, according to de Icaza... 
> "if Microsoft in fact owns patents to the technology and they require the licensing of those, we are willing to license those for the sake of our users and customers".
It is noteworthy that de Icaza made this statement with the resources of a big company behind him. Just two months earlier, Novell had bought his company Ximian, and de Icaza was now a Novell man. For that matter, it seems that Novell in 2006 actually did what de Icaza had suggested in 2003. Mono is specifically mentioned in [[COLOR="Blue"]the joint letter from Microsoft and Novell[/COLOR]]("http://www.microsoft.com/interop/msnovellcollab/open_letter.mspx") to be one of the Linux applications to be made legally safe only through their deal. (Later, [[COLOR="Blue"]Novell still officially denied[/COLOR]]("http://blogs.zdnet.com/BTL/?p=3988") any valid Microsoft patents on anything in their Linux distribution, of course.)

Also, compare Miguel de Icaza's statement regarding licensing of Moonlight (the Mono-version of MS Silverlight) [[COLOR="Blue"]on his own blog pages[/COLOR]]("http://groups.google.com/group/tiraniaorg-blog-comments/browse_thread/thread/2a07b8b50038d8c8"):

Eduardo Robles Elvira, 5 Sep 2007:
> Will I have to suffer the shadow of Microsoft patents over Silverlight when using or developing Moonlight?Miguel de Icaza, 6 Sep 2007:
> Not as long as you get/download Moonlight from Novell which will include patent coverage.
Even if paying off Microsoft might be OK to Novell, though, it would of course be unacceptable to Linux distributors and users in general (the free software community).

---

### Post by Ratatosk on 2008-02-16
[FONT="Arial"][SIZE="4"]**4) Microsoft .NET patents**[/SIZE][/FONT]

There has clearly been a lot of speculation as to the substance of Microsoft 's recently claimed 235 software patents on the (standard desktop) Linux system.
When it comes to Microsoft's *own* system, on the other hand - the .NET framework - it is a different story. No one needs to doubt that .NET is positively soaked in MS patents.

English [[COLOR="Blue"]translation at Eupat.ffii.org[/COLOR]]("http://eupat.ffii.org/gasnu/microsoft/") of a German [[COLOR="Blue"]article in Heise online[/COLOR]]("http://www.heise.de/newsticker/meldung/25564") (12 Mar 2002) - and note that this was *after* the CLI and C# parts of .NET were already ratified ECMA standards:
> Responding to questions about the opening-up of the .NET framework, Ballmer announced that there would certainly be a "Common Language Runtime Implementation" for Unix, but then explained that this development would be limited to a subset, which was "intended only for academic use". Ballmer rejected speculations about support for free .NET implementations such as Mono: "We have invested so many millions in .NET, we have so many patents on .NET, which we want to cultivate."

And, a year later, this:
[INDENT][[COLOR="Blue"]***MS patents .Everything***[/COLOR]]("http://www.theregister.co.uk/2003/02/11/ms_patents_everything/") - The Register (Andrew Orlowski), 11 Feb 2003.
[/INDENT]
Then also:
[INDENT][[COLOR="Blue"]*MS Gets 2 New Patents*[/COLOR]]("http://www.groklaw.net/article.php?story=2005010406110017") - Groklaw (Pamela Jones), 4 Jan 2005 
[/INDENT]
Note that the links in these articles, to the US patent database, don't work any longer. The first one can be found [[COLOR="Blue"]here[/COLOR]]("http://appft1.uspto.gov/netacgi/nph-Parser?Sect1=PTO1&Sect2=HITOFF&d=PG01&p=1&u=/netahtml/PTO/srchnum.html&r=1&f=G&l=50&s1='20030028685'.PGNR.&OS=DN/20030028685&RS=DN/20030028685"), however, and the two patents in the second article are [[COLOR="Blue"]here[/COLOR]]("http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO1&Sect2=HITOFF&d=PALL&p=1&u=/netahtml/PTO/srchnum.htm&r=1&f=G&l=50&s1=6836883.PN.&OS=PN/6836883&RS=PN/6836883") and [[COLOR="Blue"]here[/COLOR]]("http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO1&Sect2=HITOFF&d=PALL&p=1&u=/netahtml/PTO/srchnum.htm&r=1&f=G&l=50&s1=6836884.PN.&OS=PN/6836884&RS=PN/6836884"). (In order to view the images - i.e. scanned pages - you need a TIFF plugin; I used Mozplugger together with GQView, both from the repositories.)
 
The first (".Everything") patent is still pending, but most published applications tend to be granted, it seems. The two patents of the second article have already been granted.

I also took a look among patents myself and quickly found more on .NET. For instance, there is a whole series of patents under the title "Application program interface for network software platform", with US patents 6920461, 7013469, 7017162, 7117504 and 7165239 so far granted, and published patent applications 20030028685 (the ".Everything" patent), 20030167277, 20030167355, 20030167356, 20030172196, 20030177282, 20050240943, 20050246716 and 20070100967 on their way.

([[COLOR="Blue"]This is the page[/COLOR]]("http://www.uspto.gov/patft/index.html") from where you can search for yourself among already issued US patents as well as those on their way.)

Again, it seems crystal clear to me that for anything and everything in .NET (/Mono) that is at all possible to tie to a patent, Microsoft will have one. It is after all their technology.



[FONT="Arial"][SIZE="4"]**5) The real issue**[/SIZE][/FONT]

Despite this, many assume .NET to be legally safe, based on Microsoft having turned parts of it (C# and the CLI) into ECMA and ISO standards. Not that this in itself is enough, since ECMA and ISO (unlike W3C) generally only require [[COLOR="Blue"]RAND[/COLOR]]("http://en.wikipedia.org/wiki/Reasonable_and_non-discriminatory") terms on what patent licensing might be required for implementations (such as Mono) of their standards. RAND is good for big companies, but in itself more or less useless for individual developers, minor to mid-size companies or for the free software community. For the C# and CLI standards, though, Microsoft seems to have added a promise of royalty-free licensing of their patents.

Before jumping to conclusions, though, I think would be very worthwhile to ponder the following articles:
 
[LIST][*][[COLOR="Blue"]*MS Stance on CLR Patent Raises Thorny Questions*[/COLOR]]("http://dotnet.sys-con.com/read/38836.htm") - .NET Developer's Journal (Derek Ferguson), 27 Mar 2003

[*][[COLOR="Blue"]*Will C# benefit Microsoft, or the industry?*[/COLOR]]("http://www.builderau.com.au/program/java/print.htm?TYPE=story&AT=320269113-339024620t-320000991c") - David Berlind, 16 Oct 2002 (originally in ZDNet, but now I can only find it on Builder AU)

[*][[COLOR="Blue"]***Why Mono is Currently An Unacceptable Risk***[/COLOR]]("http://www.gnome.org/~seth/blog/mono") - Seth Nickell, lead of Gnome UI development (among other things), 19 May 2004[/LIST]
(And, to avoid any confusion, when Seth Nickell speaks of a "Trojan horse", he is obviously not referring to malware in the technical sense; again, this discussion has little to do with technology, it's all about politics and law.)
__________

Furthermore, even more or less disregarding the legal issues, there is the general question of the long-term wisdom in attempting to chase Microsoft's platform at the expense of non-Mono/Microsoft platforms (java, python). From the article [[COLOR="Blue"]*Red Hat Doesn't Want Mono*[/COLOR]]("http://www.internetnews.com/dev-news/article.php/3644981") (Internetnews.com, 21 Nov 2006) :
> "We don't like the fact that though it's very easy to write stuff in Mono and port to Windows, it's very difficult to take Windows applications and move them back over to Linux," Berman said.

This aspect was more fully laid out in an article on Mono (and DotGNU), by Neil Davidson of Red Gate Software: [[COLOR="Blue"]*Mono and dotGNU: what's the point?*[/COLOR]]("http://www.theregister.co.uk/2004/02/11/mono_and_dotgnu_whats/") - The Register, 11 Feb 2004. Unfortunately his argumentation had the fault of being in parts overly derisive, in particular ignoring the significance of free(dom) as opposed to free (gratis) software (and hence the importance of the self-hosting C#-compiler of Mono), and, for those parts, he got loads of well-earned criticism. But I have yet to see anyone respond to the main points:> DotGNU's motivations include stopping Microsoft from achieving monopolistic control of web services. Getting people to adopt C# probably isn't a good way of accomplishing this. Every Java devotee that dotGNU converts to the C# cause is actually increasing Microsoft's stronghold.

Even if Mono or dotGNU gets 99 percent of the way there, that's not enough. It's the extra 1 percent that matters. It's the boring stuff like adding serialization capabilities to classes, implementing good security, and documenting class libraries that makes C# and .NET viable.
...
People involved in these projects seem to be convinced that they are working to break Microsoft's perceived monopoly.* But how is porting a Microsoft platform to Linux going to achieve this? How is making C# a standard on Windows and Linux going to hurt Microsoft? Far from being alarmed, Microsoft execs encourage this activity, making a lot of the .NET source code available under the ROTOR program. Their enemies are now working, for free, to extend Microsoft's monopoly onto new platforms.

If, in Microsoft's wildest dreams, C# on Linux kills Java, and Sun or IBM accuses Microsoft of abusing a monopoly position, all Microsoft will need to do is point at Mono (and hence Novell) and dotGNU. Can you imagine it? Novell executives testifying for Microsoft in some hypothetical anti-trust case?**

If the open source versions of .NET start to struggle, then Microsoft will probably just bail Novell out with $150 million or so like it did Apple. Of course, Microsoft can enforce its patents any time if it ever feels *really* threatened. 
* To this, [[COLOR="Blue"]Miguel de Icaza responded[/COLOR]]("http://dotnet.sys-con.com/read/44032.htm") that isn't among Mono's goals to break Microsoft's monopoly.
** This article was written before the Microsoft-Novell deal.
__________

In brief, I don't doubt for a minute that Mono can be a short-term way of bringing more cool software to Linux. But I fear the possible long-term effects. (I found Seth Nickell's nailbiter "The Horror Story" totally believable.)
Or put differently:
[LIST=1]
[*]Each .NET-developer that Mono lures from Windows to Linux = good.
[*]Each Linux-native developer that Mono lures from Python, Java etc. to a more or less Microsoft-dominated/controlled platform = bad, very, very bad![/LIST]
The thing is, for the purpose of item 1, I don't see the point of having Mono pre-installed. I am sure any developer should be clever enough to find out for himself/herself how to install it when needed.

For the purpose of item 2, on the other hand, *not* providing Mono (and hence *no Mono-applications*) pre-installed will make for at least some threshold against favoring Mono over Python or Java when it comes to native development. (Java isn't pre-installed, remember?)

By pushing Mono applications, it seems to me that Ubuntu supports a ".NET-ification" of the Linux platform. And I think what makes many people very uneasy (certainly me) is the thought that by using/supporting Ubuntu we too will in our turn - even if only by a small measure - take part in this.

---

### Post by sloggerkhan on 2008-02-16
I do think it seems odd to include mono by default when only 2 default applications, both of which have reasonable alternatives, use it.

---

### Post by Ratatosk on 2008-02-16
> **23meg said:**
> The fact that gThumb and F-Spot have partially overlapping functionality has been discussed for a long time, ever since F-Spot was included by default, without any necessary association with Mono. It's evident that ideally one of these applications has to go; the reason this is being resolved now is that we're having an LTS release. If you volunteer to do a comprehensive, unbiased, technical comparison of both software on factual (not anecdotal) grounds, taking features, bug history and security into account, I'm sure people will pay attention and evaluate it.
Was there made "a comprehensive, unbiased, technical comparison of both software on factual (not anecdotal) grounds, taking features, bug history and security into account"?
(Is the decision to choose F-Spot over gThumbs based on that?)

If so, would it be possible for us to see it?
(I think that would be very helpful to the discussion.)

---

### Post by sloggerkhan on 2008-02-16
> **Ratatosk said:**
> Was there made "a comprehensive, unbiased, technical comparison of both software on factual (not anecdotal) grounds, taking features, bug history and security into account"?
(Is the decision to choose F-Spot over gThumbs based on that?)

If so, would it be possible for us to see it?
(I think that would be very helpful to the discussion.)

Well, my thought is that gThumb could also be used in place of Eye of gnome Image Viewer, not just as a replacement for f-spot.

---

### Post by 23meg on 2008-02-16
> **Ratatosk said:**
> Was there made "a comprehensive, unbiased, technical comparison of both software on factual (not anecdotal) grounds, taking features, bug history and security into account"?
(Is the decision to choose F-Spot over gThumbs based on that?)

If so, would it be possible for us to see it?
(I think that would be very helpful to the discussion.)

Not pronouncedly, although these can't not have been considered. The change was discussed on the mailing lists, in at least one desktop team meeting (logs and minutes are available), and probably at length at UDS and on IRC during spec discussions. If someone wants to do a more formal review, it can contribute to the transparency of the procedure, and make it possible to re-evaluate the decision.

---

### Post by Fbot1 on 2008-02-17
I think it definitely should be removed, Tomboy doesn't seem like something many people will use and F-Spot kinda sucks. I think that Wine would better serve more people.

---

### Post by sloggerkhan on 2008-02-17
> **Fbot1 said:**
> I think it definitely should be removed, Tomboy doesn't seem like something many people will use and F-Spot kinda sucks. I think that Wine would better serve more people.

WTH.... Wine!!????
Is this post sarcasm?

---

### Post by Jan-Nik on 2008-02-17
> **sloggerkhan said:**
> WTH.... Wine!!????

Wine would let user start some windows applications out of the box. And its size is something about 10 MB, so why not?

---

### Post by Fbot1 on 2008-02-17
> **sloggerkhan said:**
> WTH.... Wine!!????
Is this post sarcasm?

It would be more useful then Tomboy and F-Spot.

---

### Post by sloggerkhan on 2008-02-17
Yeah. Let's all help mislead windows users into thinking linux will be windows for free and all their windows programs will work fine.

It's ludicrous to even consider including wine in the default install. It doesn't even work without troubleshooting for most programs I've ever tried using with it. I always just end up deleting it if I install it.

---

### Post by smartboyathome on 2008-02-17
> **sloggerkhan said:**
> Yeah. Let's all help mislead windows users into thinking linux will be windows for free and all their windows programs will work fine.

It's ludicrous to even consider including wine in the default install. It doesn't even work without troubleshooting for most programs I've ever tried using with it. I always just end up deleting it if I install it.

Not only that, but it is updated every few weeks so it would become outdated very fast. My opinion still stands.

---

### Post by Fbot1 on 2008-02-17
> **sloggerkhan said:**
> Yeah. Let's all help mislead windows users into thinking linux will be windows for free and all their windows programs will work fine.

It wouldn't really be misleading them.

---

### Post by smartboyathome on 2008-02-17
> **Fbot1 said:**
> It wouldn't really be misleading them.

It would, since WINE allows you to run some windows programs in Linux, people would think their favorite programs would run and get mad at Ubuntu for lying when they didn't.

---

### Post by julian67 on 2008-02-17
I voted No because mono is free software released under free licenses,  and anyone who claims it's tainted by patent violations should either show some hard facts or be disregarded.  Apparently the Linux kernel and almost everything else we use is allegedly also violating numerous patents but the complainants never quite make it to court do they? Except SCO and they got well and truly and very publicly defeated.  

F-Spot has rapidly developed into an amazing application. If you're still running the Feisty or Gutsy default versions you're in for a treat when you get up to date.

p.s I use both gthumb and f-spot and f-spot has important functionality that gthumb does not have (multiple versions of images, raw+jpeg merge, extremely slick integration with gimp and ufraw, timeline viewing and it's also better (imo) in areas such as tagging, viewing (the magnifier is excellent) and it has some very good and easy simple edit tools for the inexperienced (red eye tool for example). Gthumb and F-Spot are not imo all 100% directly comparable once you really examine and use them extensively, though they certainly overlap in many areas. Gthumb is a much better choice on older or low powered hardware and F-Spot is excellent for anyone with a half decent PC built in the last 5 years.

---

### Post by steve196 on 2008-02-17
I think such a huge system like mono preinstalled is not a good idea, unless it is a centerpiece of the whole setup. I think avoiding bloat is crucial considering the direction in which computers are developing (smaller and cheaper instead of faster and better).The eee and the xo are the examples of what i think will be the next generation of computing. And they will shrink further once their native operating systems get better adapted to the scarce environment. Big libraries for small software will becoma a problem.

---

### Post by julian67 on 2008-02-17
> **steve196 said:**
>  considering the direction in which computers are developing (smaller and cheaper instead of faster and better).The eee and the xo are the examples


That's not the direction in which computers are developing, just a tiny, tiny subset.  In fact we see bigger and bigger monitors, more powerful processors (dual or even multi-core), more RAM running at higher speeds, GPUs alone with more resources than a good desktop of 3 years ago and so on. Smaller is not better if you need a big screen for graphics work. Somehow I doubt a 7" screen is going to become a "must have" for anyone working with images, though it might be big enough for looking at your tomboy stickies ;-)

---

### Post by smartboyathome on 2008-02-17
Ubuntu isn't aiming to be smaller and cheaper. If that is the way computers are developing, people will shift from Ubuntu to another distro, but until then it seems like Ubuntu is doing something like since it pretty much is the biggest distro out there.

---

### Post by SuperMike on 2008-02-17
> **Simon G Best said:**
> I'm uneasy with Mono, because of Miguel de Icaza, Microsoft and Novell.  I'd rather not have Mono on my system - and so I've removed it.  I didn't use F-Spot or Tomboy anyway.

Given Microsoft's FUD campaigns, it does seem sensible to ditch Mono.

Spot on. Couldn't agree more.

---

### Post by julian67 on 2008-02-17
> **SuperMike said:**
> Spot on. Couldn't agree more.

on that basis we need to get rid of the Linux kernel too. Hey let's all run the GNU Hurd and no applications!!!! Yay!

---

### Post by sloggerkhan on 2008-02-17
> **julian67 said:**
> on that basis we need to get rid of the Linux kernel too. Hey let's all run the GNU Hurd and no applications!!!! Yay!

I think the basis should be that supporting an MS created language supports MS, not that it infringes on their patents. I don't care about software patents.

---

### Post by julian67 on 2008-02-17
Supports them how? They don't own or control mono or derive revenue from it.  It's more likely that they dislike mono and feel annoyed by its existence if they feel moved to mutter and grumble about patent infringement.  It's free software, which is antithetical to everything they stand for and sell. I can't see a *rational* reason for disliking a language based on who first wrote it. Language itself is neutral.  If people have non-rational reasons for disliking/hating something that's up to them, but they can't reasonably expect others to accomodate those feelings by changing/abandoning perfectly legitimate activity.

---

### Post by sloggerkhan on 2008-02-17
> **julian67 said:**
> Supports them how? They don't own or control mono or derive revenue from it.  It's more likely that they dislike mono and feel annoyed by its existence if they feel moved to mutter and grumble about patent infringement.  It's free software, which is antithetical to everything they stand for and sell. I can't see a *rational* reason for disliking a language based on who first wrote it. Language itself is neutral.  If people have non-rational reasons for disliking/hating something that's up to them, but they can't reasonably expect others to accomodate those feelings by changing/abandoning perfectly legitimate activity.

Or they think mono programmer == new c# coder if only they can get them to jump over.

---

### Post by SonicSteve on 2008-02-17
I don't see any good or compelling reason to remove it. I see good reasons to keep it though.
1. Internet is using more and more mono apps.
2. There are good apps for Gnome that use it. 
3. Even if this vote was official, unless you have 85% or better one way of the other you shouldn't make a move.

---

### Post by Fbot1 on 2008-02-17
> **smartboyathome said:**
> It would, since WINE allows you to run some windows programs in Linux, people would think their favorite programs would run and get mad at Ubuntu for lying when they didn't.
...and they would then look stupid because no such promise would have been made. You're missing the point, we should try to figure what would be more useful.

---

### Post by smartboyathome on 2008-02-17
> **Fbot1 said:**
> ...and they would then look stupid because no such promise would have been made. You're missing the point, we should try to figure what would be more useful.

For some who have their programs supported _with the version in the repos_. A lot of programs aren't supported under wine, and it still is very buggy. I would say it should stay out of Ubuntu, it is even buggier than Compiz imo.

---

### Post by sloggerkhan on 2008-02-17
> **SonicSteve said:**
> 
3. Even if this vote was official, unless you have 85% or better one way of the other you shouldn't make a move.

This is kinda funny. Apply it to all kinds of things (politics) and you'd start getting some ugly situations.

---

### Post by Fbot1 on 2008-02-17
> **smartboyathome said:**
> For some who have their programs supported _with the version in the repos_. A lot of programs aren't supported under wine, and it still is very buggy. I would say it should stay out of Ubuntu, it is even buggier than Compiz imo.

I wouldn't say it's that buggy.

---

### Post by smartboyathome on 2008-02-17
> **sloggerkhan said:**
> This is kinda funny. Apply it to all kinds of things (politics) and you'd start getting some ugly situations.

Though this isn't politics, and if you remove mono 'n friends then people might get mad because they liked the programs mono provided (and according to the poll, there are tons of people who do).

---

### Post by smartboyathome on 2008-02-17
> **Fbot1 said:**
> I wouldn't say it's that buggy.

It can be. Try installing google talk. Also, a friend tried using WOW with it, and it was unstable.

---

### Post by Fbot1 on 2008-02-17
> **smartboyathome said:**
> It can be. Try installing google talk. Also, a friend tried using WOW with it, and it was unstable.

I've tried WoW with Wine, it was stable but it looked like crap.

---

### Post by julian67 on 2008-02-17
I read through most of this thread again and the prime motivation by many of the people who object to mono is a very strong & unpleasant personal (or as personal as you can get without actually knowing someone) hatred for Miguel de Icaza. So stop using Gnome, de Icaza co-founded it to create a *free* desktop alternative to the (then) not-quite-free KDE.  He's also contributed to the Linux kernel. How does that taste? And if you hate Novell so badly then you had better quit using Open Office because they contribute a lot to that. Also Samba, Novell has been a huge contributor.  Samba is btw a free implementation of Microsoft networking protocols and services....gasp!!! horror!!!  Let's not forget Evolution, that had better be stripped out of Ubuntu too.  I appreciate that there are reasons why the disk (CD) size of mono and the performance of some mono based apps might not appeal to everyone but this  thread contains some of the most unpleasant expressions I've seen on Ubuntu forums.  Anyone who really has such apparently high principles and such a loathing for a person who has contributed so much to free software that the FSF gave him an award should really not be comfortable using the man's works at all.  Not Gnome, not Linux.

---

### Post by chandru.in on 2008-02-17
> **smartboyathome said:**
> Mono is completely free and is licensed under the GPL. So you can't say it "isn't free enough to be in Ubuntu".

Please, Mono fans definitely need to check their facts before arguing.  Mono is licensed under MIT license not GPL.  Ask them to release it under GPL/LGPL/Apache license or any other license which clearly states about patent licensing and I'll immediately say Mono is fine.

In its current license it is a grave risk waiting to kill users.  Legally the MIT license doesn't even guarantee that Novel themselves will not sue Mono users (though there is little chance of this happening).  You never know, if in the next patent deal with Novell, MS asks them to sue Ubuntu users they may do it.  You may call me a conspiracy theorist.  But, people who said Novell is getting cozy with MS, prior to the deal, were called conspiracy theorists too.

Please check you facts before u cry so much for Mono.

---

### Post by Fbot1 on 2008-02-17
> **chandru.in said:**
> Please, Mono fans definitely need to check their facts before arguing.  Mono is licensed under MIT license not GPL.  Ask them to release it under GPL/LGPL/Apache license or any other license which clearly states about patent licensing and I'll immediately say Mono is fine.

In its current license it is a grave risk waiting to kill users.  Legally the MIT license doesn't even guarantee that Novel themselves will not sue Mono users (though there is little chance of this happening).  You never know, if in the next patent deal with Novell, MS asks them to sue Ubuntu users they may do it.  You may call me a conspiracy theorist.  But, people who said Novell is getting cozy with MS, prior to the deal, were called conspiracy theorists too.

Please check you facts before u cry so much for Mono.

[http://en.wikipedia.org/wiki/Mono_(software)#License](http://en.wikipedia.org/wiki/Mono_(software)#License)

---

### Post by chandru.in on 2008-02-17
Mono without class-libraries is nothing but a piece of ****.  Now the critical part (class libraries) are licensed under MIT.  They give reasons for not choosing GPL/LGPL but why not Apache?  MIT says nothing about patents Apache does.

---

### Post by Fbot1 on 2008-02-17
> **chandru.in said:**
> Mono without class-libraries is nothing but a piece of ****.  Now the critical part (class libraries) are licensed under MIT.  They give reasons for not choosing GPL/LGPL but why not Apache?  MIT says nothing about patents Apache does.

I dunno. I don't think that's an issue though (not yet at least). Mono has been around for a long time and if they are going to sue they sure are taking their time.

---

### Post by Simon G Best on 2008-02-17
Why do defenders of Mono insist on sticking with the patent straw-man?  :mad:

> **julian67 said:**
> on that basis we need to get rid of the Linux kernel too. Hey let's all run the GNU Hurd and no applications!!!! Yay!

Nope.

Firstly, the Linux kernel isn't based on Microsoft technology.  Mono is.  Mono, after all, is a reimplementation of .NET.

Secondly, Development of the Linux kernel is led by Linus Torvalds.  His reputation is squeaky clean when it comes to Microsoft.  Development of Mono is led by Miguel de Icaza, employed by Novell which has done that dodgy deal with Microsoft.  That alone raises questions.  And de Icaza himself has not helped matters.

As for the patent straw-man: again, as I've previously said, it's not really the supposed threat of patents that's the real problem.  Mono is a **FUD** opportunity for Microsoft (and Novell).  Yes, the FUD relates to claimed patents, but it's the FUD that's significant.  And crucial to the FUD is that Mono is significantly, fundamentally based on Microsoft technology.  *That* is the key difference that defenders of Mono keep ignoring, no matter how many times these kinds of clarifications get made.  They just want to pretend it's only about the supposed patents.

It isn't even necessary for Microsoft to have *any* patents relating to Mono.  While such patents, real or imaginary, might be helpful to Microsoft in their *FUD* efforts, they can still FUD on the basis of Mono being significantly based on .NET.

The problem with needlessly including Mono in Ubuntu is that it needlessly - and easily avoidably - gives Microsoft and friends that easy opportunity to claim - quite plausibly - that Ubuntu comes with unauthorised inclusion of reimplemented Microsoft technology.  (Never mind that such authorisation isn't even required for it to be legal and safe.  The FUDsters just don't like to mention such points.)

It's bad enough that so-called software patents allow the FUDsters - including Microsoft - to claim that Linux infringes hundreds of patents.  There's really no need to add to the problem by needlessly including such things as Mono.

I predict that this clarification - that it's *not* the claimed patents, but the FUD opportunities, that are significant - will, again, be ignored by Mono defenders.  I predict that they will continue to bring up and knock down that old patent straw-man again and again.  I predict that they will continue to call for the FUDster-claimed patents to be identified, *even though that ignores the real point.*

I also predict that the Mono defenders will continue to ignore the fact that this is just about whether or not to include Mono *in the default installation.*  They do seem to like to ignore the fact that Mono can still be included in the repositories for those who want or need it.  Instead, they like to pretend that if it's not going to be in the default installation, it's going to be unavailable altogether, or too difficult, or whatever.  At least, that's the way they come across to me.

Basically, I predict that these clarifications will again be disregarded and ignored (and, I dare say, misconstrued) by the Mono defenders.  I'll let others draw their own conclusions as to why they would do that.

---

### Post by Fbot1 on 2008-02-17
> **Simon G Best said:**
> 
... crucial to the FUD is that Mono is significantly, fundamentally based on Microsoft technology...
It isn't even necessary for Microsoft to have *any* patents relating to Mono.  While such patents, real or imaginary, might be helpful to Microsoft in their *FUD* efforts, they can still FUD on the basis of Mono being significantly based on .NET.
...

Actually, they would need patents.

---

### Post by smartboyathome on 2008-02-17
FUD is not the problem. They can claim all they want, but they need evidence to go to court and sue mono (or ubuntu users, or whatever). Microsoft already spreads FUD about Linux, do you think getting rid of a few (very good) programs for ones with less functions and less development just because the language was made popular by others? They can claim that they own the patent to the double click (they do, actually), and sue us because of that, should we get rid of that? After all, it is based on Microsoft tech as well.

---

### Post by Simon G Best on 2008-02-17
> **julian67 said:**
> Supports them how? They don't own or control mono or derive revenue from it.  It's more likely that they dislike mono and feel annoyed by its existence if they feel moved to mutter and grumble about patent infringement.

It's a FUD opportunity.  Microsoft probably want all Linux-based distributions to include things like Mono, because things like Mono are significantly and prominently based on Microsoft technology.  That gives them a wonderful FUD opportunity - *which they've already been taking advantage of.*  It's not a mere *theory* that Microsoft *might* like to spin such things as Mono for their own FUD, *because it's already been happening.*  When they "mutter and grumble about patent infringement", *that's part of the FUD.*

Let's not forget that, in the past, Microsoft have said that if people are going to use pirate software, Microsoft want that software to be Microsoft software.  They want people to get "addicted" to it as if it's a drug.  Then, when Microsoft manage to defeat the pirates, the "addicts" start buying from Microsoft.

This is a known Microsoft strategy, because Microsoft actually explained it like this themselves.

Those of us who understand this are therefore sensibly wary of Mono.  We know Microsoft well enough to know that they really are that devious and cynical.

If you really do believe that Microsoft actually does dislike Mono in the way you describe, then you're simply too naive to really understand our concerns about Mono and our distrust of Novell.

Microsoft do indeed hate Linux, the GPL, and so on.  And so they *do* want it to be "contaminated" with Microsoft stuff.  At the very least, they want people to *believe* that it's "contaminated", that it contains "unauthorised" derivatives and reimplementations of Microsoft technology, because then the **F**ear, **U**ncertainty and **D**oubt about possible legal problems, and the like, might deter people from moving away from "safe" Microsoft.  That's why they've spent years pushing such FUD about alleged patent infringements and the like.

In short: Microsoft *do* want Mono in Ubuntu, in the hope that their FUD will then deter people from considering Ubuntu.

---

### Post by SonicSteve on 2008-02-17
> **sloggerkhan said:**
> This is kinda funny. Apply it to all kinds of things (politics) and you'd start getting some ugly situations.

I wouldn't apply it to all things. Let me explain it this way. Take a sample of 100,000 Linux users. Lets say that half of them will care about about a vote like this. 15% of those 50,000 users translates to 7.5% of your user base. On a decision about mono, perhaps not a big deal. I'm just saying that a decisive vote based on 51% to 49% is obviously too close. The comfort line has to be drawn somewhere. 85% still leaves potentially 15% unhappy. 

To be honest though I've been rethinking my position on the mono issue. One fear I have is that if mono becomes too popular microsoft will have a lever to manipulate with. I don't like giving them anymore control over my computer than they already have. 

I'm now in the undecided camp.

---

### Post by Simon G Best on 2008-02-17
> **Fbot1 said:**
> Actually, they would need patents.

No, they don't actually need relevant patents in order to be able to FUD.  They just need to get people *fearing* possible patents (even if none really exist).  They just need to establish *uncertainty* as to whether or not they hold any relevant patents.  They just need to create *doubts* in people's minds as to the legal safety of using Ubuntu.  *Fear.*  *Uncertainty.*  *Doubt.*  That's why it's abbreviated to "FUD".  The feared patents need not actually be real at all.

---

### Post by Fbot1 on 2008-02-17
> **Simon G Best said:**
> No, they don't actually need relevant patents in order to be able to FUD.  They just need to get people *fearing* possible patents (even if none really exist).  They just need to establish *uncertainty* as to whether or not they hold any relevant patents.  They just need to create *doubts* in people's minds as to the legal safety of using Ubuntu.  *Fear.*  *Uncertainty.*  *Doubt.*  That's why it's abbreviated to "FUD".  The feared patents need not actually be real at all.

That's not an issue though. They couldn't straight-up sue them anyway.

---

### Post by chandru.in on 2008-02-17
Mono lovers almost always mention Samba as an implementation of MS technology to advocate Mono.  Samba is no doubt a re-implementation of MS technology.  But it is used for the sole purpose of interoperating with Windows.  If someone uses it for Linux-Linux networking, it makes no sense.

On the same line, there is no problem in having Mono in repos and using it to run Windows apps ported over to Mono.  However, using it to run Linux's killer apps makes no sense.  It creates unnecessary dependence on MS technology.

---

### Post by smartboyathome on 2008-02-17
Simon G West:
Fine, lets get rid of the double click then. And the taskbar with start button. They have patented both and can spread FUD with them, too. Also, lets get rid of stuff like an e-mail client, and a web browser, as they can claim that they violate patents as well. *rolls eyes*
I think people are being overly cautious on this, and as a result are trying to eliminate good apps (yes, Mono does provide some good apps, try FSpot on hardy if you don't believe me).

---

### Post by smartboyathome on 2008-02-17
> **chandru.in said:**
> Mono lovers almost always mention Samba as an implementation of MS technology to advocate Mono.  Samba is no doubt a re-implementation of MS technology.  But it is used for the sole purpose of interoperating with Windows.  If someone uses it for Linux-Linux networking, it makes no sense.

On the same line, there is no problem in having Mono in repos and using it to run Windows apps ported over to Mono.  However, using it to run Linux's killer apps makes no sense.  It creates unnecessary dependence on MS technology.

Then how about you port the programs that Ubuntu uses to something like Python? Surely, that will save a great bit of space by getting rid of mono. After all, they are only two programs.

---

### Post by st4rdr1ft3r on 2008-02-18
Surely removing mono is just giving in to the potential FUD?

---

### Post by steve196 on 2008-02-18
In the real world nobody cares if Manuel de Icaza (did i spell that right) is a good or a bad guy  or what nonsense Steve Ballmer can put in his speeches if Mono is left in or not.
The point is: Using such a big library for two small programs shows a troubling direction. Putting something big in because it does something big is one thing. Putting something big in because two tiny programs need it shows exactly the kind of philosophy, that got Windows Vista in trouble. People reject Vista mainly because they discover, that their shiny brandnew machine is as slow as their old one because inefficiencies eat up all those resources. Now Ubuntu isn't anywhere near as bad, but bringing in a huge library for two tiny programs shows a trend of "resources are not a problem anyway" which is the same thing that got Vista in trouble.

---

### Post by julian67 on 2008-02-18
> **Simon G Best said:**
> Why do defenders of Mono insist on sticking with the patent straw-man?  :mad:

Nope.

Firstly, the Linux kernel isn't based on Microsoft technology.  Mono is. 

So is samba, why is no-one screaming for that to be removed?  

> **Simon G Best said:**
> Mono, after all, is a reimplementation of .NET.

Secondly, Development of the Linux kernel is led by Linus Torvalds.  His reputation is squeaky clean when it comes to Microsoft.  Development of Mono is led by Miguel de Icaza, employed by Novell which has done that dodgy deal with Microsoft.  That alone raises questions.  And de Icaza himself has not helped matters.

any facts or are you only up for character assassination?

> **Simon G Best said:**
> As for the patent straw-man: again, as I've previously said, it's not really the supposed threat of patents that's the real problem.  Mono is a **FUD** opportunity for Microsoft (and Novell).  Yes, the FUD relates to claimed patents, but it's the FUD that's significant.  And crucial to the FUD is that Mono is significantly, fundamentally based on Microsoft technology.  *That* is the key difference that defenders of Mono keep ignoring, no matter how many times these kinds of clarifications get made.  They just want to pretend it's only about the supposed patents.

It isn't even necessary for Microsoft to have *any* patents relating to Mono.  While such patents, real or imaginary, might be helpful to Microsoft in their *FUD* efforts, they can still FUD on the basis of Mono being significantly based on .NET.

The problem with needlessly including Mono in Ubuntu is that it needlessly - and easily avoidably - gives Microsoft and friends that easy opportunity to claim - quite plausibly - that Ubuntu comes with unauthorised inclusion of reimplemented Microsoft technology.  (Never mind that such authorisation isn't even required for it to be legal and safe.  The FUDsters just don't like to mention such points.)

It's bad enough that so-called software patents allow the FUDsters - including Microsoft - to claim that Linux infringes hundreds of patents.  There's really no need to add to the problem by needlessly including such things as Mono.

I predict that this clarification - that it's *not* the claimed patents, but the FUD opportunities, that are significant - will, again, be ignored by Mono defenders.  I predict that they will continue to bring up and knock down that old patent straw-man again and again.  I predict that they will continue to call for the FUDster-claimed patents to be identified, *even though that ignores the real point.*

I also predict that the Mono defenders will continue to ignore the fact that this is just about whether or not to include Mono *in the default installation.*  They do seem to like to ignore the fact that Mono can still be included in the repositories for those who want or need it.  Instead, they like to pretend that if it's not going to be in the default installation, it's going to be unavailable altogether, or too difficult, or whatever.  At least, that's the way they come across to me.

Basically, I predict that these clarifications will again be disregarded and ignored (and, I dare say, misconstrued) by the Mono defenders.  I'll let others draw their own conclusions as to why they would do that.

There's more fud in these posts than MS usually manages in a whole campaign. And btw for anyone who might have got the contrary impression from some people here the MIT License is an open source license. [quote="wikipedia"]The MIT License is a free software license originating at the Massachusetts Institute of Technology (MIT). It is a permissive license, meaning that it permits reuse within proprietary software on the condition that the license is distributed with that software, and GPL-compatible, meaning that the GPL permits combination and redistribution with software that uses the MIT License[/quote]

As long as software is under a free license there's no ethical reason to purge it from a GNU/Linux distribution.  If people have an emotional reaction to it that is purely a personal issue for them.

---

### Post by deepclutch on 2008-02-18
mono must be removed from Gnome for the sake of God!:x it is an unwanted gum pasted on Gnome!make mono as optional ,dont compile Gnome with any mono lib as dep. thank you!

My Debian and Ubuntu box is free of mono!Miguel is totally going in the wrong direction by porting .net via mono to Linux :evil: I hope his service in developing Gnome Desktop is more relevant rather than doing this M$ .net porting :x

---

### Post by julian67 on 2008-02-18
so now we have god and chewing gum involved. Anyone have an argument based on something actually related to reality (i.e. commonly accepted to exist outside of your own mind/feelings/fears/aversions/prejudices)? The CD disk space one was pretty good but so far that seems to be the extent of rational objections.

---

### Post by SonicSteve on 2008-02-18
I know this borders on spreading FUD but it does factor into the decision of whether or not it is wise to include anymore MS tech into Ubuntu/Linux than is neccessary.

This quote comes from Forbes which was linked to previously in this thread. I'm posting it this way incase it was skipped over by some readers.
[http://www.forbes.com/forbes/2004/0816/065.html](http://www.forbes.com/forbes/2004/0816/065.html) 
fourth paragraph.

> Taylor, 34, is Microsoft's top Linux strategist. He speaks regularly at conferences for open-source programming, so called because anyone can examine and make changes to the underlying source code. (The guts of Microsoft's software, by contrast, have long been closely guarded.) He reads Linux-themed Web newsgroups daily and often phones around to Silicon Valley investors who are funding open-source software.

Entrepreneurs in the industry smile at the mention of his name because they know, for one thing, that Taylor is a straight-up, nice guy, but also that his real job is to better understand Linux so Microsoft can do a better job of crushing it

If it is there end goal to "better understand, and crush Linux" this needs to be factored into our decisions. The truth is that we need to do exactly what they are doing. We need to better understand them so we know when something is FUD, and when it's something to be wary of.

In the case of MONO, I still sit undecided. As long as it doesn't end up being a lever that microsoft can use to control Linux, or displace better technology in the name of interoperability then  perhaps it could be a good thing. 

The question can be this, might Linux be able to use MONO against Microsoft? Can we port more and more apps from windows, making it easier to transition users from MS to Linux?

---

### Post by smartboyathome on 2008-02-18
> **steve196 said:**
> In the real world nobody cares if Manuel de Icaza (did i spell that right) is a good or a bad guy  or what nonsense Steve Ballmer can put in his speeches if Mono is left in or not.
The point is: Using such a big library for two small programs shows a troubling direction. Putting something big in because it does something big is one thing. Putting something big in because two tiny programs need it shows exactly the kind of philosophy, that got Windows Vista in trouble. People reject Vista mainly because they discover, that their shiny brandnew machine is as slow as their old one because inefficiencies eat up all those resources. Now Ubuntu isn't anywhere near as bad, but bringing in a huge library for two tiny programs shows a trend of "resources are not a problem anyway" which is the same thing that got Vista in trouble.

Just to let you know, those "two tiny programs" are not lacking features. In fact, they are plentiful in them. And mono 'n friends don't take up much ram. the only mono program that does is beagle, and that is not even included. Could you suggest to me another Photo _Manager_ (not viewer) which has all the features that FSpot does? Can you do the same for mono, as well as have it look just as nice (no, Zim does not look as nice)? If so, then submit them for inclusion in Ubuntu and you can have your wish.

---

### Post by neighborlee on 2008-02-18
> **julian67 said:**
> so now we have god and chewing gum involved. Anyone have an argument based on something actually related to reality (i.e. commonly accepted to exist outside of your own mind/feelings/fears/aversions/prejudices)? The CD disk space one was pretty good but so far that seems to be the extent of rational objections.

[http://www.eweek.com/c/a/Linux-and-Open-Source/Microsofts-OpenSource-Trap-for-Mono/](http://www.eweek.com/c/a/Linux-and-Open-Source/Microsofts-OpenSource-Trap-for-Mono/)

This looks interesting.

Here is a fedora discussion with very similar  views:

[http://forums.fedoraforum.org/forum/showthread.php?t=168185&highlight=beagle](http://forums.fedoraforum.org/forum/showthread.php?t=168185&highlight=beagle)

which  leads here:

[http://boycottnovell.com/2007/10/03/mono-death-trap/](http://boycottnovell.com/2007/10/03/mono-death-trap/)

and points to :

Update: Miguel de Icaza praises Microsoft about the move but cannot hide his disappointment with the choice of licence. It is subtle, yet transparent.

Is there any  consideration given to PNET ? :

[http://www.gnu.org/software/dotgnu/danger.html](http://www.gnu.org/software/dotgnu/danger.html) < from 

[http://www.gnu.org/software/dotgnu/pnet.html](http://www.gnu.org/software/dotgnu/pnet.html)

Why was pnet never considered  ?

You  can also take this in :
[http://www.devxnews.com/article.php/3644981](http://www.devxnews.com/article.php/3644981)

which comes from here:
[http://forums.fedoraforum.org/forum/showthread.php?t=168185&page=3&pp=15&highlight=beagle](http://forums.fedoraforum.org/forum/showthread.php?t=168185&page=3&pp=15&highlight=beagle)

Redhat is steering clear of MONO and I wonder does that concern anyone at all ????

cheers
nl

---

### Post by neighborlee on 2008-02-18
> **smartboyathome said:**
> Just to let you know, those "two tiny programs" are not lacking features. In fact, they are plentiful in them. And mono 'n friends don't take up much ram. the only mono program that does is beagle, and that is not even included. Could you suggest to me another Photo _Manager_ (not viewer) which has all the features that FSpot does? Can you do the same for mono, as well as have it look just as nice (no, Zim does not look as nice)? If so, then submit them for inclusion in Ubuntu and you can have your wish.

Tell that to these people whom clearly state , that even tomboy eats resources; but gosh its just a note taker what harm could it possibly do ?

[http://forums.fedoraforum.org/forum/showthread.php?t=168185&page=3&pp=15&highlight=beagle](http://forums.fedoraforum.org/forum/showthread.php?t=168185&page=3&pp=15&highlight=beagle)

cheers
nl

---

### Post by decoherence on 2008-02-18
Just to add to that...

[http://www.mono-project.com/Contributing](http://www.mono-project.com/Contributing)

From the section "Important Rules"

    *  If you have looked at Microsoft's implementation of .NET or their shared source code, you will not be able to contribute to Mono. 

That in conjunction with Microsoft's constant grumblings about intellectual property, is enough to send me running!

---

### Post by smartboyathome on 2008-02-18
> **neighborlee said:**
> Tell that to these people whom clearly state , that even tomboy eats resources; but gosh its just a note taker what harm could it possibly do ?

[http://forums.fedoraforum.org/forum/showthread.php?t=168185&page=3&pp=15&highlight=beagle](http://forums.fedoraforum.org/forum/showthread.php?t=168185&page=3&pp=15&highlight=beagle)

cheers
nl

It only takes up 20MBs of system memory on my computer. It is 20mbs, but that shouldn't matter much, as it would basically not be felt unless you are on an (ie) 256mb system, which is too small for Ubuntu anyway.

---

### Post by Fbot1 on 2008-02-18
> **smartboyathome said:**
> ...Could you suggest to me another Photo _Manager_ (not viewer) which has all the features that FSpot does? ...

Excluding KDE programs, there aren't but, a lot of those features seem useless for most people

> **smartboyathome said:**
> ...Can you do the same for mono, as well as have it look just as nice (no, Zim does not look as nice)? If so, then submit them for inclusion in Ubuntu and you can have your wish.

They both took okay to me. Regardless, that sort of note taking seems silly to me anyway.

---

### Post by smartboyathome on 2008-02-18
The features in both programs may seem useless to you, but may not to others. Also, I use the notetaking program to do notes for some of my classes.

---

### Post by neighborlee on 2008-02-18
> **smartboyathome said:**
> The features in both programs may seem useless to you, but may not to others. Also, I use the notetaking program to do notes for some of my classes.

You can add them via synaptic instead of having them forced on those who dont want them nor their overhead or patent issues. ( yes I said patent issues as regardless what  you say RHEE does not include MONO and never will. - seems they are the only ones paying attention lately while everyone else skims with blinders on )

cheers
nl

---

### Post by chandru.in on 2008-02-18
Hey I got an idea which Mono lovers can start working on immediately.  MS released something called Aero.  Ditch our own FOSS innovation called compiz-fusion.  Now work on re-implementing Aero for Linux on top of Mono.

Hey this (according to ur theory) would help more people use Linux as they will be familiar with it already.  Which means they don't have to learn one more thing for using Linux.

---

### Post by smartboyathome on 2008-02-18
> **neighborlee said:**
> You can add them via synaptic instead of having them forced on those who dont want them nor their overhead or patent issues. ( yes I said patent issues as regardless what  you say RHEE does not include MONO and never will. - seems they are the only ones paying attention lately while everyone else skims with blinders on )

cheers
nl

Fine, but I still know I am not the only one who uses it, look at the results of this poll. More than likely, the people who are happy with mono won't vote and the people who aren't will.

---

### Post by smartboyathome on 2008-02-18
> **chandru.in said:**
> Hey I got an idea which Mono lovers can start working on immediately.  MS released something called Aero.  Ditch our own FOSS innovation called compiz-fusion.  Now work on re-implementing Aero for Linux on top of Mono.

Hey this (according to ur theory) would help more people use Linux as they will be familiar with it already.  Which means they don't have to learn one more thing for using Linux.

Using FSpot and Tomboy are not like implimenting Aero. You should talk to novell about that since they are already doing Silverlight.

---

### Post by st4rdr1ft3r on 2008-02-18
> **smartboyathome said:**
> Using FSpot and Tomboy are not like implimenting Aero. You should talk to novell about that since they are already doing Silverlight.

He was being a sarcastic idiot, not at all serious about implementing aero.

---

### Post by chandru.in on 2008-02-18
> **smartboyathome said:**
> Using FSpot and Tomboy are not like implimenting Aero. You should talk to novell about that since they are already doing Silverlight.

Now you would soon suggest moonlight be included by default just coz it is open and forget the fact that only Novell can distribute it.

---

### Post by smartboyathome on 2008-02-18
> **chandru.in said:**
> Now you would soon suggest moonlight be included by default just coz it is open and forget the fact that only Novell can distribute it.

I never said such a thing. I just said that if you want Aero implimented, talk to Novell, since they are porting Silverlight. Mono by itself is fine, but some programs that use it aren't.

---

### Post by gnomeuser on 2008-02-18
> **chandru.in said:**
> Now you would soon suggest moonlight be included by default just coz it is open and forget the fact that only Novell can distribute it.

... No you are wrong. Moonlight is under a number of OSI approved licenses and is freely distributable by anyone. If you want a valid license for VC-1 support you need to get the Novell approved copy. It's no different than say shipping with the Fluendo MP3 plugin (or as Novell does with SLED, Helix with mp3 a licensed).

Would you please do some research before spreading FUD?

---

### Post by gnomeuser on 2008-02-18
> **chandru.in said:**
> Hey I got an idea which Mono lovers can start working on immediately.  MS released something called Aero.  Ditch our own FOSS innovation called compiz-fusion.  Now work on re-implementing Aero for Linux on top of Mono.

Hey this (according to ur theory) would help more people use Linux as they will be familiar with it already.  Which means they don't have to learn one more thing for using Linux.

Look up strawman argument please.

---

### Post by julian67 on 2008-02-18
> **gnomeuser said:**
> Look up strawman argument please.

but strawman argument..... that's the closest they get to being rational! seems cruel to point it out :)

---

### Post by Simon G Best on 2008-02-18
How about a compromise?

There are those who, for whatever reason, want Mono to be included, to continue to be available.

There are those who, for whatever reason, don't want Mono included, and don't want Ubuntu to become dependent on Mono.

A reasonable, sensible compromise would be to keep Mono in the repositories, and to remove it from the default installation.  That way, those who want Mono still have it available, and those who object to its inclusion can leave it uninstalled.  Mono can be easily available without Ubuntu becoming dependent on it.

Of course, this has been proposed since pretty much the start of this thread (if not the very start).  I predict that proponents of Mono will continue to refuse such compromise, wanting to have it all their own way, and expecting everyone else to compromise instead.

(For the record: if I had it all my own way, Mono wouldn't even be in the repositories at all.  I've agreed to the compromise of keeping it in the repositories since very early on in this thread.)

---

### Post by julian67 on 2008-02-18
I like the other "compromise" where *you* remove it if you don't like it. I think you need to check the meaning of compromise, it's rather different from " trying to sound conciliatory in order to get what you earlier insisted upon".  It's not like a decision is going to be made by Canonical (or you, me or anyone else here) by reading this thread so it's a totally pointless proposition you make anyway. Or do you imagine we're all sitting at Shuttleworth Villas deciding the fate of the free software world ????  Invade Redmond at dawn! Surpise SAS & Green Beret attack on Cupertino just after teatime! Pigs to be seen flying past in formation by bedtime!!!

---

### Post by 23meg on 2008-02-18
[QUOTE=Simon G Best](For the record: if I had it all my own way, Mono wouldn't even be in the repositories at all. I've agreed to the compromise of keeping it in the repositories since very early on in this thread.)[/QUOTE]

Correction: if you had it all your own way, Mono wouldn't exist at all.

---

### Post by Fbot1 on 2008-02-18
> **23meg said:**
> Correction: if you had it all your own way, Mono wouldn't exist at all.

Play nice

---

### Post by chandru.in on 2008-02-18
> **gnomeuser said:**
> ... No you are wrong. Moonlight is under a number of OSI approved licenses and is freely distributable by anyone. If you want a valid license for VC-1 support you need to get the Novell approved copy. It's no different than say shipping with the Fluendo MP3 plugin (or as Novell does with SLED, Helix with mp3 a licensed).

Would you please do some research before spreading FUD?

Could you please explain the content here,

[http://www.mono-project.com/Moonlight#Licensing](http://www.mono-project.com/Moonlight#Licensing)

They also point to an MS covenant to Novell.  Which means if I get it from another place there are undefined troubles waiting for me.

Come on Mono lovers, for heavens sake stop making Linux's future dependent on MS

---

### Post by 23meg on 2008-02-18
> **Fbot1 said:**
> Play nice

I thought I was? That's just what I deduce from Simon G Best's posts so far.

[QUOTE=chandru.in]Come on Mono lovers, for heavens sake stop making Linux's future dependent on MS[/QUOTE]

And you should stop asking loaded questions and building straw man arguments. Not everyone arguing for keeping Mono is a "Mono lover".

---

### Post by julian67 on 2008-02-19
The fact that people disagree with you does not mean the debate is not open, nor does it mean that everybody else is wrong.  It only looks that way to people who are unable to conceive of an opinion different from their own having any validity.

---

### Post by julian67 on 2008-02-19
> **neighborlee said:**
> OH, and another reasoned response adding even more to the muck and mire of an already totally useless thread by now.  And just exactcly where did you deduce this almighty reasoning from ?  I gave absoolutely no information in any of my posts for such logic to spew from your mouth , yet here  it is in all its glory and it adds nothing but mayhem and discord  to the discussion.  

cheers
nl

The inclusion of Mono is worth discussing but not on a religious basis. It *is* free software so the debate can only reasonably be about technical issues such as performance, disk size, development, available apps (popularity,demand, features etc), integration with Gnome/Ubuntu and on that level there are some valid reasons for some to prefer something else.  I don't mind the resource useage or disk size because for me it's a price worth paying for the functionality I get, but I appreciate that others may prefer a different balance.  I don't run Mono on my old Pentium-M laptop where I prefer Gthumb (on antix with Debian Sid) but I do run it on my desktop because it has the *awesome power* of an athlon 2700 and 1 GB DDR 400 which despite its low specs is perfectly capable of having Gimp, F-Spot, browser, audio player, amule, email client etc all run at the same time on Xubuntu.  Ubuntu runs Gnome which suggests to me that  high performance on old hardware is not the goal. If the most important criterion was performance then the Gnome DE itself would have to be removed. Imo F-Spot and Tomboy are perfectly appropriate in terms of function and performance for a modern distro running Gnome, particularly one which has a focus on new users. Gthumb is very nice but as an organiser with its libraries and catalogues it's not nearly as user friendly as other photo managers such as F-Spot or  Digikam.

---

### Post by PmDematagoda on 2008-02-19
This thread is getting ugly and the latest posts are not even to the thread title.

This thread is temporarily closed.

---

### Post by 23meg on 2008-02-19
*[Insert statement on difficulty of written communication with people one doesn't know]*

Really, can't you take what I said as a factual and slightly humorous passing comment? That's what I intended it as, but I'm not going to jump on you for not interpreting it as such.

> **neighborlee]How is this conducive to peaceful and logical compromising discussions, - or heck said:**
> 

I very much care that it happens; my posting history, which you can check out with a search, should stand as proof of the fact that I do. But I didn't mean this particular comment to be conductive to any serious goal. It was meant as tongue-in-cheek; maybe I should have used a smiley. The signal to noise ratio of these forums can definitely accommodate such posts by everyone every once in a while[SIZE="1"] *(Edit: with this I meant that the signal to noise ratio is already low; not that it's high enough to allow going off topic at times) *[/SIZE].

[QUOTE=neighborlee]I once thought ubunty was the way to go, but it seems I was comletely mistaken.

not so much cheer atm it seems.
no wonder gthumb was railroaded out.
good going Mark you really hired some winners here.

There's a clear rationale in the removal of gThumb, which I pointed to you, and you didn't address. Now you're turning it into name calling material. If you enjoy it, go on, but I don't think the thread will last too long in that case. 

And no, I'm not hired by Mark.

> **neighborlee]It's not what you deduce at all from SImon's focus to get some unity here, - its what you deduce as a means to an end of your rigid stance on MONO as was made entirely eivdent by the lack of open debate on the topic and continual ignoring of much facts presented in this entire thread.[/QUOTE]

1) I don't have a "rigid stance" on Mono. I actually am close to having no well defined stance at all said:**
> NO, what happened is you slipped up, and decided to center your discussion on the negative instead of the 'compromise' which leads to unity. Simon might not like mono and indeed 'wish' it was not in existence but the fact you pointed to the negative shows where your head is on all of this. Way to go your about as transparent as glass.

I can't have "slipped up", because I didn't go into an argument. I merely asked some questions and made some remarks on things others have said. Just so you know, I cherish Simon's position just as much as gnomeuser's, and I've learnt things from both their posts that I didn't know before, so I'm happy to have read them. 

But I'm not responsible for bringing "unity" to the discussion any more than you are. And I have just as much right to comment on things others say as you do.

[QUOTE=neighborlee]It is therefore now VERY clear that this discussion, and the consideration of getting gthumb back and mono as a apt-get opt-in is totally in jeopardy.[/QUOTE]

You're lumping together unrelated happenings in an effort to make it all look like a conspiracy. I don't find that convincing, simply because I know the facts behind the individual things you're trying to connect. As I said before in other words, if you have good arguments in favor of gThumb (you'll need some other data than the fact that it doesn't depend on Mono), gather them and present them. People will give you an ear, assuming you keep it civil and factual.

[QUOTE=neighborlee]You have now lost all credibility and you need to remove yourself from the discussion , if indeed your serious about ubuntu's welfare.[/QUOTE]

Unless you step back from your rash and unfounded attacks, I will remove myself from the discussion for my own sanity. If the name calling continues, I'll report the relevant posts. And I apologize for my remark, which apparently didn't come across as I had intended it.

---

### Post by PmDematagoda on 2008-02-19
This thread has been reopened.

Please try and maintain respect and politeness for others and also stick to the topic from here onwards.

---

### Post by vexorian on 2008-02-21
So, I'll recapitulate.

1. Do not include MONO by default.
2. Discourage usage of MONO for applications that could as well be native C++ apps or pygtk apps, SERIOUSLY. 

MS' .net involves bloat and problems requiring you to windowsify the system, MONO is possible great to run a VERY small subset of .net apps from ubuntu, so it might be a good idea to keep it in the repository with that "supported" logo. Just don't include it or apps by default.

I think [this](http://beranger.org/index.php?page=diary&2008/02/20/10/22/59-simple-mental-exercise-identify-) should be enough reason to worry.

If default gnome apps keep getting more and more into MONO and Novell uses money to make the MONO apps superior feature-wise than the normal ones, then we need to invest in native apps. Novell is likely to do that since they have the exclusivity in MS' deals about MONO, no other "vendor" has MS' blessing to distribute MONO.

Don't come and tell me that there aren't patent issues with MONO, cause there are. MS' deal with Novell specifically mentions their cooperation and that Novell will then be able to distribute MONO thanks to the deal. It is exclusionary at best. If you like MONO and MONO apps and really don't think there's any risk... then just install them after you install ubuntu, but keep my default ubuntu clear of these windows things. Thanks.

**Edit**
Accepting MONO as platform for default apps included in ubuntu sounds about like a bad thing, should Ubuntu be seen as a windows copy cat? Why not just make native apps anyway? It would be interesting to see an OS with no native apps and only things that are ported to it, I wouldn't have respect for it, and unfortunately this is where gnome is heading. In my opinion Ubuntu does not deserve that and does not have to follow gnome's fate.

**In conclusion**
MONO is fine as a compatibility layer, but there is a reason ubuntu's main apps aren't win32 apps that are to work on WINE, there's a reason Linux2Linux networks don't use samba, there's a reason OpenOffice does not save in MS' binary formats by default. So, keep it as an optional package, it IS a bad idea to make it an irremovable core package like it is right now.

It is clear there's an attempt to make Linux lose its identity, the fact they are trying to change the OS so it includes a bunch of .exe and .dll files should be an alarm, I don't think Linux losing its identity is something that is worth to see just because some guys in the gnome foundation are MS' technology fans.

---

### Post by Jan-Nik on 2008-02-21
> **vexorian said:**
> this[/url] should be enough reason to worry.

Ehm... just because they use Windows' file extensions that's a reason to worry??
Normal users shouldn't see anything inside /usr at all.

---

### Post by julian67 on 2008-02-21
> **vexorian said:**
> So, I'll recapitulate.



Thank you for capitulating...and more than once! It seems the discussion is settled. 

capitulate, dictionary.com: > 1.	to surrender unconditionally or on stipulated terms.
2.	to give up resistance: He finally capitulated and agreed to do the job my way.

---

### Post by smartboyathome on 2008-02-21
> **vexorian said:**
> So, I'll recapitulate.

1. Do not include MONO by default.
2. Discourage usage of MONO for applications that could as well be native C++ apps or pygtk apps, SERIOUSLY. 

MS' .net involves bloat and problems requiring you to windowsify the system, MONO is possible great to run a VERY small subset of .net apps from ubuntu, so it might be a good idea to keep it in the repository with that "supported" logo. Just don't include it or apps by default.

I think [this](http://beranger.org/index.php?page=diary&2008/02/20/10/22/59-simple-mental-exercise-identify-) should be enough reason to worry.

If default gnome apps keep getting more and more into MONO and Novell uses money to make the MONO apps superior feature-wise than the normal ones, then we need to invest in native apps. Novell is likely to do that since they have the exclusivity in MS' deals about MONO, no other "vendor" has MS' blessing to distribute MONO.

Don't come and tell me that there aren't patent issues with MONO, cause there are. MS' deal with Novell specifically mentions their cooperation and that Novell will then be able to distribute MONO thanks to the deal. It is exclusionary at best. If you like MONO and MONO apps and really don't think there's any risk... then just install them after you install ubuntu, but keep my default ubuntu clear of these windows things. Thanks.

**Edit**
Accepting MONO as platform for default apps included in ubuntu sounds about like a bad thing, should Ubuntu be seen as a windows copy cat? Why not just make native apps anyway? It would be interesting to see an OS with no native apps and only things that are ported to it, I wouldn't have respect for it, and unfortunately this is where gnome is heading. In my opinion Ubuntu does not deserve that and does not have to follow gnome's fate.

**In conclusion**
MONO is fine as a compatibility layer, but there is a reason ubuntu's main apps aren't win32 apps that are to work on WINE, there's a reason Linux2Linux networks don't use samba, there's a reason OpenOffice does not save in MS' binary formats by default. So, keep it as an optional package, it IS a bad idea to make it an irremovable core package like it is right now.

It is clear there's an attempt to make Linux lose its identity, the fact they are trying to change the OS so it includes a bunch of .exe and .dll files should be an alarm, I don't think Linux losing its identity is something that is worth to see just because some guys in the gnome foundation are MS' technology fans.

Microsoft never came out and said WHICH patents Novell was breaking, though, and thus it could be a bluff for all we know.

Also, like I keep saying, make a replacement for F-Spot which has all its features in another language, and Ubuntu may consider it. As of hardy, F-Spot is the default photo manager, and  until there is one which is better (note, GThumb is not the answer, the devs took it out for a reason), it won't happen. Do the same with Tomboy (and Zim is not a "drop-in replacement").

---

### Post by chandru.in on 2008-02-21
Wow!  Linux goes in the right direction.

We have bunch of DLLs and EXEs now.  Come on nay sayers (who are actually more sensible) Windows users would feel more comfortable with .exe and .dlls.  Do u think people would try and understand permission bits (though it is a main reason for better security model of UNIX)?

Mono is also very important for porting killer apps of Linux back to Windows (forget the fact that killer apps of Windows are not ported to Linux) so that MS can increase its market share (if at all it finds some more users).

Hope Mono developers with Novell's fullest blessing build a distribution which represents each partition with an alphabet.  Then no more /etc, /usr, /boot, etc.  It will have these directories (sorry FOLDERS), C:\Program Files, C:\NOVEL_LINUX, C:\Documents and Settings.

Yay!! I just suggested a Linux distribution which soooo many windows users would love to use (after all they'd feel more confortable).

---

### Post by chandru.in on 2008-02-21
> **smartboyathome said:**
> Microsoft never came out and said WHICH patents Novell was breaking, though, and thus it could be a bluff for all we know.

If it was really a bluff which no one would care, Novell wouldn't have signed a deal and tout MS interoperability as the primary strength of SLED and SLES.  It did the deal because true or not there will be a set of users who would believe FUD to avoid potential risk.

> **smartboyathome said:**
> Also, like I keep saying, make a replacement for F-Spot which has all its features in another language, and Ubuntu may consider it.

Playing catch up is actually a disease.  If it happens within FOSS communities it is even more worthless.

As I noted often, copying MS technology to defeat them will never ever work out.  Firefox threatened IE because it did things better.  Not because it copied every pixel of IE.

Now if you tell me Mono can do things differently from Microsoft too (unless it does a subset alone), u must be kidding.  Then it will no longer be a .Net re-implementation.

---

### Post by Jan-Nik on 2008-02-21
> **chandru.in said:**
> Wow!  Linux goes in the right direction.

We have bunch of DLLs and EXEs now.  Come on nay sayers (who are actually more sensible) Windows users would feel more comfortable with .exe and .dlls.  Do u think people would try and understand permission bits (though it is a main reason for better security model of UNIX)?
As I said: Normally users wont look in /usr/lib.

> Mono is also very important for porting killer apps of Linux back to Windows
Why? Gtk+ and Qt work on Windows too. Shall we remove them?

> (forget the fact that killer apps of Windows are not ported to Linux)
Yes, and probably because they aren't written in C#.

---

### Post by smartboyathome on 2008-02-21
> **chandru.in said:**
> Playing catch up is actually a disease.  If it happens within FOSS communities it is even more worthless.

As I noted often, copying MS technology to defeat them will never ever work out.  Firefox threatened IE because it did things better.  Not because it copied every pixel of IE.

Now if you tell me Mono can do things differently from Microsoft too (unless it does a subset alone), u must be kidding.  Then it will no longer be a .Net re-implementation.

F-Spot and Tomboy (the only two apps that use Mono) do not copy MS technology. While it is true that Mono ports .Net, it doesn't mean that it is bad. It is not a good practice to avoid trading features and ideas between OSes to make each OS better or stronger. If we keep living in fear of MS, we will be the ones hurting from it. F-Spot is a great Photo Manager, and I haven't seen another one like it which develops jsut as quickly. Same with Tomboy for Notetaking. People who are scared of MS can uninstall it, while everyone else can use it to their liking.

---

### Post by julian67 on 2008-02-21
What is the **rational** objection to _a file extension_???? It's just a file extension. I know it's very odd to see something.exe running as a process in Linux, but so what? Is there anything beyond an emotional respose here? Something that can be expressed with reference to (commonly accepted) objective reality as opposed to your subjective feelings about MS and Novell? If you want people to come over to your point of view you need to persuade us on some basis other than how you personally feel agitated at the sight of a .exe or .dll or a  joke about an extremely unlikely hypothetical file structure. It's quite a good joke but not persuasive....only a joke.

---

### Post by chandru.in on 2008-02-21
> **Jan-Nik said:**
> As I said: Normally users wont look in /usr/lib.


Why? Gtk+ and Qt work on Windows too. Shall we remove them?


Yes, and probably because they aren't written in C#.

GTK+ and Qt are not supported by Microsoft at any point in history.  But .Net is straight from MS.  .Net comes pre-installed in Vista.  So, theoretically Mono apps would run with just a slight re-compile.

But GTK+ and Qt are very different.  They need to be obtained separately.  GTK+ and Qt are not in any shape or form based on MS tech.  So there is very little control MS has on them.  But MS can break Mono any time by changing .Net.  Again, if you believe Windows developers would think about Mono when developing with .Net, you are fooling yourself.  They'd continue to build apps using the latest and greatest feature in .Net.  Mono can never ever be 100% compatible with latest .Net release.

If history matters, Samba developers were clear on how MS dealt with SMB.  MS keeps .NEt as open spec only to kill Java.  Once that's done, it will slowly close-up critical parts leaving Mono a crippled .Net.

---

### Post by chandru.in on 2008-02-21
> **julian67 said:**
> What is the **rational** objection to _a file extension_???? It's just a file extension. I know it's very odd to see something.exe running as a process in Linux, but so what? Is there anything beyond an emotional respose here? Something that can be expressed with reference to (commonly accepted) objective reality as opposed to your subjective feelings about MS and Novell? If you want people to come over to your point of view you need to persuade us on some basis other than how you personally feel agitated at the sight of a .exe or .dll or a  joke about an extremely unlikely hypothetical file structure. It's quite a good joke but not persuasive....only a joke.

The file system structure was pure sarcasm (or rather joke).  My problem is not really with file suffixes.  It is about how much Mono is capable of making Linux look Microsoftish.  Linux is literally loosing its identity here.

Last time I checked Mac OS X was gaining market share much faster than Linux did after Vista's disappointments and Leopard release.  But it has no Mono thing by default.  This shows the real place Linux developers needs to focus for gaining mind and market share is elsewhere and not re-implementing MS technologies.

---

### Post by deepclutch on 2008-02-21
^what you said is reality.M$ cannot help OSS; :D they can pretend (like mono).

Errmm...this mono thing is crippling default ubuntu.
I believe Gnome CAN live with out .net and mono.may be Mr.Miguel understands :rolleyes:

---

### Post by julian67 on 2008-02-21
> **chandru.in said:**
> 
MS keeps .NEt as open spec only to kill Java.  This is an assertion of your opinion, not a fact. > **chandru.in said:**
> Once that's done, it will slowly close-up critical parts leaving Mono a crippled .Net.This is also an assertion of your opinion, not a fact. 

It's actually impossible to discuss these things by asserting our opinions and demanding others accept them as fact. You might be right, you may in future be *proven* right (or not) , but right now if you want to persuade people of your point of view this isn't enough to be taken seriously by people who do not already agree with you.

---

### Post by chandru.in on 2008-02-21
> **julian67 said:**
> This is an assertion of your opinion, not a fact.

I quoted something about what happened in the case of Samba.  Did u even bother to read up and find out what it was?

---

### Post by julian67 on 2008-02-21
> **chandru.in said:**
> I quoted something about what happened in the case of Samba.  Did u even bother to read up and find out what it was?

you didn't quote anything and you offered no reference. If you'd like to expand your point with more information and/or a reference I'll perhaps be able to appreciate what you were trying to say.

---

### Post by chandru.in on 2008-02-21
See the third non-bold paragraph.

[http://news.zdnet.com/2424-9595_22-164801.html](http://news.zdnet.com/2424-9595_22-164801.html)

---

### Post by Jan-Nik on 2008-02-21
> **chandru.in said:**
> GTK+ and Qt are not supported by Microsoft at any point in history.  But .Net is straight from MS.  .Net comes pre-installed in Vista.  So, theoretically Mono apps would run with just a slight re-compile.
GTK+ and Qt apps should also work on Vista with a slight re-compile. Python is available on Windows, Java is available on Windows, C++ is available on Windows (and with boost all of the functionality like file operations, too).

> But GTK+ and Qt are very different.  They need to be obtained separately.  GTK+ and Qt are not in any shape or form based on MS tech.  So there is very little control MS has on them.  But MS can break Mono any time by changing .Net.
Yes they could, but this would not affect apps like F-spot or tomboy at all, because they are developed for Mono.
And if Microsoft would break the API, then all .Net applications for Windows won't work with Windows, too. So this is very unlikely to happen.

> Again, if you believe Windows developers would think about Mono when developing with .Net, you are fooling yourself.
Do you think F-Spot and Tomboy developers want to port their applications to Windows? No they don't. KDE 4 wants to do that, shall we remove KDE 4 then?

> They'd continue to build apps using the latest and greatest feature in .Net.  Mono can never ever be 100% compatible with latest .Net release.
That's true, but we are talking about applications like F-Spot and Tomboy. They use Gtk# anyway, so it's unimportant if the newest WinForms are supported.

---

### Post by julian67 on 2008-02-21
> **chandru.in said:**
> See the third non-bold paragraph.

[http://news.zdnet.com/2424-9595_22-164801.html](http://news.zdnet.com/2424-9595_22-164801.html)

thank you. It's a good article and one I had read before (as well as hearing Jeremy Allison discuss the subject on Linux podcasts, I think on tllts). Basically you assume that MS will follow the same pattern of behaviour, this is unproven but perfectly possible so let's assume it to be true for the sake of argument. The effect would be on interoperability and principaly the ability to port Mono apps to MS; it would become very difficult or even impossible for some mono applications, and make no difference at all to other mono projects, but would make mono redundant in those terms (because .net and mono would gradually become incompatible). As far as I can see this would be inconvenient but not disasterous. Mono and its apps would still be viable on the free desktop but probably development would slow down or even cease on the cross platform projects and some might be inclined  to turn to alternative applications. Those do exist and there is no sign that the existence of mono is hampering the development of applications such as gThumb and Digikam (in reference to F-Spot).  I think the samba situation was far more serious because it concerned the ability to run Linux/BSD/Solaris and MS all in the same environment. Basically MS were trying to force a monoculture (no pun intended ha ha) in enterprise environments by crippling the ability of non MS installed computers to communicate with their systems. It seems to me that the very worst that can result from MS pursuing a similar method in the case of Mono is that a lot of users might have to go through the inconvenience of exporting databases (if possible) and files to another set of applications and some mono developers would need to find something else to do with their time. It wouldn't be a crippling blow, but an inconvenience. 

Factors that may be relevant are the various pressures on MS (mostly exerted by the EU and a few US states) to force them into behaving ethically and legally with regard to interoperability and adherence to standards. Time will tell, but even MS seems to realise it cannot flout laws indefinitely and today's news sees them making more moves towards complying with EU legislation (apparently) [http://news.bbc.co.uk/1/hi/business/7257411.stm](http://news.bbc.co.uk/1/hi/business/7257411.stm) Of course it may just be the MS marketing machine and as the EU Commision says > "The Commission would welcome any move towards genuine interoperability," it said.

"Nonetheless, the Commission notes that today's announcement follows at least four similar statements by Microsoft in the past on the importance of interoperability."  they may not be sincere, but certainly the legal environment is much more difficult for them these days and the EU seems far less likely to roll over than the US govt.

---

### Post by Buffalo Soldier on 2008-02-21
For those who say there are no **rational**, **logical **or **legal** reasons for Microsoft to use Mono as a weapon undermine GNU/Linux. When have Microsoft let **rational**, **logical **or **legal** get in the way of spreading FUD such *"Linux is violating Microsoft intelectual property"*, *"Linux = communism"* and etc.

Have we forget that it is an organization that has historically in the past proven to us that they have no problem ***hitting below the waist*** when it comes to killing of competition?

---

### Post by chandru.in on 2008-02-21
> **Jan-Nik said:**
> GTK+ and Qt apps should also work on Vista with a slight re-compile. Python is available on Windows, Java is available on Windows, C++ is available on Windows (and with boost all of the functionality like file operations, too).

If all of them work on Vista at same level as .Net, there is no need for Mono.  Anyway developers would use them and need for Mono in porting is muted,  But the fact is not so.  .Net is tightly integrated into Vista.  These others are not.

> **Jan-Nik said:**
> Do you think F-Spot and Tomboy developers want to port their applications to Windows? No they don't. KDE 4 wants to do that, shall we remove KDE 4 then?

KDE4 wants to port but it is their own set of libraries which MS has no distant influence over.

---

### Post by chandru.in on 2008-02-21
> **julian67 said:**
> As far as I can see this would be inconvenient but not disasterous. Mono and its apps would still be viable on the free desktop but probably development would slow down or even cease on the cross platform projects and some might be inclined  to turn to alternative applications. Those do exist and there is no sign that the existence of mono is hampering the development of applications such as gThumb and Digikam (in reference to F-Spot).

The inconvenience is unnecessary.  I highly respect F-Spot and Tomboy they are wonderful apps.  It is unfortunate that they are based on a MS controllable technology.  They don't hamper development of non-mono apps.  They have anearly no effect in Digikam which is an excellent program in itself.  But same is not the case for gThumb.  In Hardy gThumb is going to be removed from default install.  This means the user feedback flowing to gThumb will take a slight hit, thanks to Mono-based F-Spot's dominance (again I respect F-Spot as an independent application).

---

### Post by Simon G Best on 2008-02-21
> **Jan-Nik said:**
> Ehm... just because they use Windows' file extensions that's a reason to worry??

It's just a symptom.  It's what it's a symptom of that's worrying some people.

> Normal users shouldn't see anything inside /usr at all.

Incorrect.  Normal users are supposed to be able to see inside /usr.  It's what /usr is there for, and why it's called "/usr".  It's where the programs, libraries, etc, for normal users go.  If normal users couldn't see inside it, they wouldn't be able to do anything much at all.

An experiment you might like to try *on a suitable test system* is to do the following as root:-

```
chmod o-r /usr
```

Then see what that does for normal users.  See if they can even log on to such a system.  And if they can, see what, if any, applications they can run.

---

### Post by steeleyuk on 2008-02-22
> Incorrect. Normal users are supposed to be able to see inside /usr. It's what /usr is there for, and why it's called "/usr".

Wrong! /usr actually stands for "Unix System Resources".

Kind of going off-topic here...

---

### Post by Simon G Best on 2008-02-22
> **steeleyuk said:**
> Wrong! /usr actually stands for "Unix System Resources".

Well, if you're going to get picky about it...

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/usr.html]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/usr.html"):-

> /usr usually contains by far the largest share of data on a system. Hence, this is one of the most important directories in the system as it contains all the user binaries, their documentation, libraries, header files, etc.... X and its supporting libraries can be found here. User programs like telnet, ftp, etc.... are also placed here. In the original Unix implementations, /usr was where the home directories of the users were placed (that is to say, /usr/someone was then the directory now known as /home/someone). In current Unices, /usr is where user-land programs and data (as opposed to 'system land' programs and data) are. The name hasn't changed, but it's meaning has narrowed and lengthened from "everything user related" to "user usable programs and data". As such, some people may now refer to this directory as meaning 'User System Resources' and not 'user' as was originally intended.

But even if "/usr" is taken to mean "User System Resources", the fact remains that the contents are, by and large, supposed to be readable by ordinary users.  That was my point.

> Kind of going off-topic here...

"Pedantic" is probably a better description of such quibbling of the meaning of "/usr".

---

### Post by julian67 on 2008-02-22
> **chandru.in said:**
> The inconvenience is unnecessary.  I highly respect F-Spot and Tomboy they are wonderful apps.  It is unfortunate that they are based on a MS controllable technology.  They don't hamper development of non-mono apps.  They have anearly no effect in Digikam which is an excellent program in itself.  But same is not the case for gThumb.  In Hardy gThumb is going to be removed from default install.  This means the user feedback flowing to gThumb will take a slight hit, thanks to Mono-based F-Spot's dominance (again I respect F-Spot as an independent application).

I'm not sure I agree that mono is "controllable" by MS. It seems that if they behave unethically and renege on various publicly stated strategies/assurances (and this is all perfectly possible) then it *might* become impossible to continue porting mono apps to Windows. I think someone else pointed out earlier that many of the mono apps are developed without any intention of porting to MS, this includes F-Spot afaik. Yes gThumb might take a small hit, this is the same for any app that loses its place in as a distro default as happens sometimes but Ubuntu !=Linux.

---

### Post by neighborlee on 2008-02-22
> **julian67 said:**
> I'm not sure I agree that mono is "controllable" by MS. It seems that if they behave unethically and renege on various publicly stated strategies/assurances (and this is all perfectly possible) then it *might* become impossible to continue porting mono apps to Windows. I think someone else pointed out earlier that many of the mono apps are developed without any intention of porting to MS, this includes F-Spot afaik. Yes gThumb might take a small hit, this is the same for any app that loses its place in as a distro default as happens sometimes but Ubuntu !=Linux.

This thread continues to ignore much of what was posted on  here:

[http://ubuntuforums.org/showthread.php?t=594767&page=25](http://ubuntuforums.org/showthread.php?t=594767&page=25)

Why is that ?

I dont see why we can't debate earnestly, what clearly someone went to great lengths to reveal.

23meg said  'not pronouncedly'...I gotta wonder what exactly he meant by that..if a decision was made to remove gthumb for upcoming hardly, I would earnestly hope it was more than just pronouncedly,- but by the fact that so much of what was posted on the URL I offered was not once debated could be taken as indicative of why gthumb 's removal is being considered. ( at least that is how it looks to me anyway,  and lets be clear im NOT trying to offend anyone just stating opinions as I see iot;  I dont want yet another post jailed due to another  misunderstanding. )

cheers
nl

---

### Post by 23meg on 2008-02-22
[QUOTE=neighborlee]23meg said 'not pronouncedly'...I gotta wonder what exactly he meant by that..[/QUOTE]

What I meant was that the planned removal (by "planned" I mean planned ahead for months and stated on a blueprint), was evaluated and acted upon by the desktop team in a meeting, whose logs and minutes are available. There wasn't a detailed survey of the sort I mentioned dedicated to F-Spot vs. gThumb only, which is precisely why I suggested that someone did it, upon seeing that there were people who weren't satisfied about this change. But that doesn't mean that the respective merits and shortcomings of both F-Spot and gThumb weren't considered, and I actually can't imagine why they wouldn't be.

[QUOTE=neighborlee]but by the fact that so much of what was posted on the URL I offered was not once debated could be taken as indicative of why gthumb 's removal is being considered.[/QUOTE]

1) Your URL is probably incorrect

2) I cited multiple times why gThumb's removal was being considered: all its use cases are covered by Nautilus, EOG and F-Spot, and there's an initiative to reduce duplication before the LTS release. You could always have raised a counter argument, or asked that the decision be re-evaluated by coming up with a good analysis of the situation. Right now we're just gossiping after the fact.

---

### Post by neighborlee on 2008-02-22
> **23meg said:**
> What I meant was that the planned removal (by "planned" I mean planned ahead for months and stated on a blueprint), was evaluated and acted upon by the desktop team in a meeting, whose logs and minutes are available. There wasn't a detailed survey of the sort I mentioned dedicated to F-Spot vs. gThumb only, which is precisely why I suggested that someone did it, upon seeing that there were people who weren't satisfied about this change. But that doesn't mean that the respective merits and shortcomings of both F-Spot and gThumb weren't considered, and I actually can't imagine why they wouldn't be.



1) Your URL is probably incorrect

2) I cited multiple times why gThumb's removal was being considered: all its use cases are covered by Nautilus, EOG and F-Spot, and there's an initiative to reduce duplication before the LTS release. You could always have raised a counter argument, or asked that the decision be re-evaluated by coming up with a good analysis of the situation. Right now we're just gossiping after the fact.

Probably incorrect meaning you didn't even try it or what is going on here anyway ?( because I just  went to the URL I posted and its  just 'fine') . Id' really prefer that you not engage in such tactics because that would be against the rules of this forum and that might land your post  in jail.

cheers
nl

---

### Post by 23meg on 2008-02-22
Probably incorrect meaning that I clicked on it, and got to the same page I was on; since you used the word "someone", I thought you were referring to a specific post, and mis-pasted the URL.

I'm not engaging in any tactics; I'm simply having trouble understanding you, pointing to a possible typo or mis-paste and asking you to rephrase. It happens all the time in online conversations. Your prejudice that I'm constantly conspiring against you in some way is only making me less motivated to respond to you.

So, clarify without personal attacks now: do you mean the discussion on the last page in general? What exactly is it that was revealed and that should have been considered when the decision regarding gThumb was made?

---

### Post by neighborlee on 2008-02-23
> **23meg said:**
> Probably incorrect meaning that I clicked on it, and got to the same page I was on; since you used the word "someone", I thought you were referring to a specific post, and mis-pasted the URL.

I'm not engaging in any tactics; I'm simply having trouble understanding you, pointing to a possible typo or mis-paste and asking you to rephrase. It happens all the time in online conversations. Your prejudice that I'm constantly conspiring against you in some way is only making me less motivated to respond to you.

So, clarify without personal attacks now: do you mean the discussion on the last page in general? What exactly is it that was revealed and that should have been considered when the decision regarding gThumb was made?

[http://ubuntuforums.org/showthread.php?t=594767&page=25](http://ubuntuforums.org/showthread.php?t=594767&page=25) < this page.

There is a massive , and well structured post on that page, starting with the first post , so I guess you just glanced my post and missed the URL entirely, and I suspect many others may be doing similar things as I have not seen any replies to them as yet.

cheers
nl

---

### Post by morningboat on 2008-02-23
Remove.

It's just ridiculous if we include the copy of a copy (.NET) and leave out the original (JAVA), which is being GPL'ed at the moment. (=company showing real interest in/supporting open source).

Here are a list of reasons:
1. Influence:
In my personal opinion, it's not question whether Mono developed by Novel or some other companies. Microsoft is the father of .Net system, and has the greatest influence on this platform, and the most importantly, the developers! Following their decision and market stragy is not a good idea for Mono, since MS' benefit is totally different from the open source world.

On the other hand, Sun has much less influence on the Java's future, compared with .Net by MS. Java's development is influence by JCR, and GLPed now. It's a better choice to choose Java to largely avoid the control by the company. Meanwhile, you can improve the Java's specification by JCR.

2. Legacy standards:
Java applet and Java applications are deployed on a much larger scale than .Net. If someone really use the Ubuntu for daily life, sooner or later, he needs to install Java actually. A lot of online banking system pages, broker systems, application, etc. require Java's support, such as [Citibank]("http://www.citibank.com/us/index.htm"), [Interactive Broker]("http://www.interactivebrokers.com/ibg/main.php"), Blogbridge, [CrossFTP]("http://www.crossftp.com"), etc. It is a common headache for beginners to download big Java package and integrate the Java with the web browser. Install this by default is the best way to improve the user's experience.

On the other hand, .Net is noramlly not used in the Internet scale, and most of its applications can be replaced by the native GUI applications. In case of the enterprise level systems, the administrator should be able to install the Mono system by his knowledge.

3. Performance:
.Net and Java, or Python all use JIT compiler and VM for during the runtime. The performance is similar to these systems. Java often has similar performance to, if not better than .Net, and much better performance than Python. There is no reason to dump Java due to its performance issue.
.Net, Java and Python's runtime package size is similar, 13~17Mb or so. There is no reason to exclude any one to the other due to size issues.

According to the above reasons, replace Mono by Java is a much better choice. The thing to do: provide Java applet integraiton in Web Browser, and Java Web Start integtation in the system. The next release will have LTS, so no place for mono in it.

---

### Post by smartboyathome on 2008-02-23
Let me ask everyone who wants mono removed this:
Say .Net weren't developed by Microsoft, but by some other company (for the sake of argument, lets call this company A). Say Microsoft opposed company A and didn't like it. Would you say Mono is ok to include, even if the patenting issues stayed the same?

Also, would you say that F-Spot and Tomboy would be okay to include in Ubuntu if it were based off of some other language (lets call it language X)?

---

### Post by chandru.in on 2008-02-23
> **smartboyathome said:**
> Say mono weren't developed by microsoft,

Is Mono developed by Microsoft?  I thought it was done by Novell.

---

### Post by smartboyathome on 2008-02-23
I meant .net, sorry about that, edited my post.

---

### Post by chandru.in on 2008-02-23
Jokes apart, I wouldn't mind if the CEO of company A did not spread FUD about n number of patents violated by FOSS.  If he did I'll hate it even then.

If they were written in a FOSS language independent of any technology developed by FOSS haters, I'd love them.  Even today I love F-Spot and Tomboy.  It just irritates me that they are indirectly dependent on #1 Linux hater.

---

### Post by smartboyathome on 2008-02-23
Ok, so even though .Net is developed by Microsoft, it doesn't mean it is dangerous. It is just a hate of Microsoft that makes people want to have Mono removed. Mono isn't exactly based on .Net, but C#, an open language, and isn't really dependant on MS. If they changed .Net durastically enough to make Mono incompatible, they would also destroy programs that run on it.

---

### Post by 23meg on 2008-02-23
> **neighborlee said:**
> There is a massive , and well structured post on that page, starting with the first post ,

Massive post starting with the first post?   

> **neighborlee said:**
>  so I guess you just glanced my post and missed the URL entirely, and I suspect many others may be doing similar things as I have not seen any replies to them as yet.
l

No, I read your entire post, and I clicked on your URL, as I've said before; you seem to have missed that part entirely. I've set 30 posts to be shown per page in my preferences, so this thread is actually 12 pages long for me, and when I click on your link that's supposed to take me to page 25, I'm actually taken to page 12, which is this same page. So it's impossible for me to understand which post you're referring to. Hence my asking you to point to the specific post(s) that you referred to; understood? Will you do that now? You can just give me a post number if you wish, and I'll look at it.

---

### Post by neighborlee on 2008-02-23
> **23meg said:**
> Massive post starting with the first post?   



No, I read your entire post, and I clicked on your URL, as I've said before; you seem to have missed that part entirely. I've set 30 posts to be shown per page in my preferences, so this thread is actually 12 pages long for me, and when I click on your link that's supposed to take me to page 25, I'm actually taken to page 12, which is this same page. So it's impossible for me to understand which post you're referring to. Hence my asking you to point to the specific post(s) that you referred to; understood? Will you do that now? You can just give me a post number if you wish, and I'll look at it.

They are #241, 242 and 243.

cheers
nl

---

### Post by Simon G Best on 2008-02-24
> **smartboyathome said:**
> Let me ask everyone who wants mono removed this:
Say .Net weren't developed by Microsoft, but by some other company (for the sake of argument, lets call this company A). Say Microsoft opposed company A and didn't like it. Would you say Mono is ok to include, even if the patenting issues stayed the same?

Novell - and Mono is very much a Novell thing - would still have that dodgy deal with Microsoft.  It wouldn't be as effective when it comes to their FUD, but Novell would still have Mono as a potential opportunity to gain a FUD-based advantage over competitors such as Canonical.  I'd probably still be unhappy about Mono being included by default in Ubuntu, though.  I still wouldn't want Ubuntu to needlessly give Microsoft and Novell an unnecessary and easily avoidable FUD advantage.

Perhaps you're thinking of going on to refer (again) to other projects that involve interoperability with Microsoft stuff, and which Novell contributes to.  Yes, Novell does contribute, and has contributed, to a number of projects, but merely contributing to a project is not the same as actually running the project and "owning" the project.  And seeking interoperability with Microsoft stuff when it's needed is not the same as needlessly relying on reimplementations of Microsoft stuff when there are viable alternatives readily available.  So I don't think things like Samba and OpenOffice.org would really count as truly comparable to Mono.

Even so, I'd still prefer interoperability stuff, such as Samba, not to be included by default.  Having it available in the repositories would be a good thing, as it's then easily available for those who need or want it.  But it's the sort of interoperability stuff that doesn't really need to be included in the default installation, so I'd probably prefer it to be left out of the default installation accordingly.

> Also, would you say that F-Spot and Tomboy would be okay to include in Ubuntu if it were based off of some other language (lets call it language X)?

.NET and Mono aren't languages.  But anyway, if F-Spot and Tomboy were, say, written in C++ and based on Gtk+, etc, I probably wouldn't oppose their default inclusion in Ubuntu.  But neither would I mind if they weren't included by default, either.

---

### Post by Simon G Best on 2008-02-24
> **smartboyathome said:**
> Ok, so even though .Net is developed by Microsoft, it doesn't mean it is dangerous. It is just a hate of Microsoft that makes people want to have Mono removed.

No, it just isn't that simplistic.  I know you'd like it to be, because then you could just dismiss opposition to Mono as being based on mere emotional hatred, or something easily dismissable and unsubstantial like that.  But it must already be clear, from the various arguments put forward in this long thread, that's it's nothing so simplistic.  Please don't pretend it's something as simplistic as "just a hate of Microsoft", because it clearly isn't.

For me, Novell's dodgy deal with Microsoft is the real problem.  So, when Novell seeks to gain FUD-based advantages due to that dodgy deal, *and* pushes Mono as more than just a way of helping people port .NET stuff beyond Microsoft Windows, I am wary and unwilling to be a part of it.  That's simply not the simplistic "just a hate of Microsoft" that you were hoping for.

> Mono isn't exactly based on .Net, but C#, an open language, and isn't really dependant on MS. If they changed .Net durastically enough to make Mono incompatible, they would also destroy programs that run on it.

Talk about never learning from history.  Microsoft have a long history of changing their stuff in ways that happen to break other stuff.  It's one of the things they're notorious for.

---

### Post by gnomeuser on 2008-02-24
> **Simon G Best said:**
> No, it just isn't that simplistic.  I know you'd like it to be, because then you could just dismiss opposition to Mono as being based on mere emotional hatred, or something easily dismissable and unsubstantial like that.  But it must already be clear, from the various arguments put forward in this long thread, that's it's nothing so simplistic.  Please don't pretend it's something as simplistic as "just a hate of Microsoft", because it clearly isn't.

For me, Novell's dodgy deal with Microsoft is the real problem.  So, when Novell seeks to gain FUD-based advantages due to that dodgy deal, *and* pushes Mono as more than just a way of helping people port .NET stuff beyond Microsoft Windows, I am wary and unwilling to be a part of it.  That's simply not the simplistic "just a hate of Microsoft" that you were hoping for.


You have been asked repeatedly to provide the evidence for this claim of "dodginess" in the face of the aspects of mono having me explained to you as well as the aspect of the deal that concern this debate. And you have not done so.

Now you are just moving the goalpost, you don't define dodgy, you assume the deal fits this criteria, you tend assume that Mono will serve some sort of dark conspiratorial part in some scheme..

A -> B -> C and so on... without A being proven true or the slippery slope you produce being proven. 

Worse in the process you are advocating discrimination and alienation of a growing number of developers and users by taking away their tools and applications.

Learn how to debate please, you spout logical fallacies and vague claims and then claim the burden of proof is on us to prove you wrong.. sorry it doesn't work that way, you have to prove beyond reasonable doubt that there is a valid case for removing Mono and discriminating against it's users and developers.. not to mention defaming well respected community members and corporate contributors.

In 37 pages of this back and forth, no such case has been made, every point raised has been refuted (and raised again as if nothing happened - just look at how many times since I explained the details of the deal it has been mentioned as evil). 

Admins can we please close this, no intelligence is bound to come from continuing to beat this dead horse. The decision has been made to support Mono in Ubuntu, the spec to remove it has been reviewed and rejected. Mono stays deployed in Ubuntu, no indication otherwise what so ever.

---

### Post by Ratatosk on 2008-02-24
I do get rather tired of the frequent labeling with words such as "hatred" and "irrationality" of most every objection to making Mono a standard part of our OS. (This is what the discussion is all about, no less.) (And, to be sure, this is not directed primarily at smartboyathome.)

Recognizing Microsoft to now be the main enemy of the free software world has nothing to with hatred or irrationality, quite the contrary, I would say.
And neither, for the record, am I a "hater" of Novell or Miguel de Icaza. I have always felt grateful for much of the stuff funded by Novell, and, always a happy Gnome user, I appreciate what de Icaza did with it. Until now suddenly becoming aware of the Mono problem, I had absolutely no bones to pick with de Icaza.

But to answer the latest question by smartboyathome:

> **smartboyathome said:**
> Let me ask everyone who wants mono removed this:
Say .Net weren't developed by Microsoft, but by some other company (for the sake of argument, lets call this company A). Say Microsoft opposed company A and didn't like it. Would you say Mono is ok to include, even if the patenting issues stayed the same?
I would still vote not to make Mono a standard part of our OS (remove from pre-installed stuff). And it isn't the "developed by" that scares me in itself so much as the "controlled by" that comes with it.
Again, however, MS is a particularly dangerous bed fellow.

> **smartboyathome said:**
> Also, would you say that F-Spot and Tomboy would be okay to include in Ubuntu if it were based off of some other language (lets call it language X)?
If this was only about programming languages, I would have no problems with pre-installing F-Spot or Tomboy. But Mono is a whole MS .NET-based software platform that to some extent (depending how it will be used) merges Linux with Windows (allows the same executables to run on both).

________________________________________


Happy to see that someone read my previous posts, by the way, even if longwinded. ;)

Though the confusion about the attempted link to them was less fun, of course. (One would assume copying and pasting from the address field of the browser should basically always work, but I seem to recall similar linking problems when visiting another forum.) The following links with post numbers, rather than page numbers, should - hopefully - always work, though:
[LIST]
[*][**Start**](http://ubuntuforums.org/showthread.php?p=4341133#post4341133),
[*][middle](http://ubuntuforums.org/showthread.php?p=4341137#post4341137),
[*][end](http://ubuntuforums.org/showthread.php?p=4341145#post4341145).
[/LIST]

EDIT: gnomeuser, I'll get back to you. ;)

---

### Post by julian67 on 2008-02-24
> **Simon G Best said:**
> 
Even so, I'd still prefer interoperability stuff, such as Samba, not to be included by default.  Having it available in the repositories would be a good thing, as it's then easily available for those who need or want it.  But it's the sort of interoperability stuff that doesn't really need to be included in the default installation, so I'd probably prefer it to be left out of the default installation accordingly.


I appreciate your consistency on this but can only believe you're in an extremely tiny minority.  Interoperability is crucial for most people and especially businesses. For the home/small business desktop user there's been a lot of effort in Ubuntu to make Samba browsing and sharing easier and I doubt many people see it as anything other than essential. It's certainly one of the outstanding features of Ubuntu that even from the live environment the user can be browsing network shares with just a couple of clicks, and once installed can set up their shares just as easily (usually). All my computers run Xubuntu or Debian (occasionally other distros) but I have to be able to share with others who haven't made the choice to use free software.  I think that's absolutely typical.  Samba is anyway becoming ubiquitous, being used in all kinds of networked storage devices, so I'm not sure it's something you can avoid using one way or another.

edit: to quote Ubuntu.com > Everything you need on one CD, which provides a complete working environment. Additional software is available online.

The graphical installer enables you to get up and running quickly and easily. A standard installation should take less than 25 minutes.

Once installed your system is immediately ready-to-use. On the desktop you have a full set of productivity, internet, drawing and graphics applications, and games.

A desire to *lessen* interoperability by default is entirely counter to the aims of the Ubuntu distro. I'm not even sure there *exists* a distro that might have this as a goal. I guess you might be more comfortable using a distro that lets you build your system from base, because several of your preferences suggest that you will always have ethical conflicts as along as you use Ubuntu or  any of the well known distros that aim to make interoperability *easier* by default.

---

### Post by Simon G Best on 2008-02-24
> **gnomeuser said:**
> You have been asked repeatedly to provide the evidence for this claim of "dodginess" in the face of the aspects of mono having me explained to you as well as the aspect of the deal that concern this debate. And you have not done so.

[http://www.groklaw.net/staticpages/index.php?page=20061218045851480]("http://www.groklaw.net/staticpages/index.php?page=20061218045851480")

> Now you are just moving the goalpost, you don't define dodgy, you assume the deal fits this criteria, you tend assume that Mono will serve some sort of dark conspiratorial part in some scheme..

I'm not assuming these things.  What Microsoft gets out of the deal with Novell is no secret.  And Novell wouldn't have done that deal if it didn't think it could also benefit.  It's known to be an attempt to effectively circumvent the GPLv2, which is a big part of why the deal was so unpopular with much of the community.

> A -> B -> C and so on... without A being proven true or the slippery slope you produce being proven.

I wasn't able to make sense of that sentence.

> Worse in the process you are advocating discrimination and alienation of a growing number of developers and users by taking away their tools and applications.

Not so.  I'm not advocating anything of the sort.  On the contrary, I've already said, a number of times, that I have no objection to Mono remaining available in the repositories.  As I'm sure you know, you're simply misrepresenting my position there.

---

### Post by Simon G Best on 2008-02-24
> **julian67 said:**
> I appreciate your consistency on this but can only believe you're in an extremely tiny minority.  Interoperability is crucial for most people and especially businesses. For the home/small business desktop user there's been a lot of effort in Ubuntu to make Samba browsing and sharing easier and I doubt many people see it as anything other than essential.

Okay, if it's necessary for many users, then it's necessary.  I have no objection to necessary interoperability stuff being included by default.  I'm actually in favour of it.  I only said I'd prefer stuff *that isn't necessary* to be left out of the default installation.  Perhaps Samba was the wrong example, but my point remains unchanged.

> A desire to *lessen* interoperability by default is entirely counter to the aims of the Ubuntu distro.

I'm not seeking to lessen interoperability.  I just don't want interoperability to turn into unnecessary dependence.

---

### Post by pshah.mumbai on 2008-02-24
I have been reading about this issue lately...

Very sad at the way MONO has crept into gnome.

I want it out (atleast the vendors shouldnt distribute it) - keep it in optional repositories if needed.

I have already remove cli packages from default ubuntu and everything that has to do with mono.

Lets keep GNOME as a Free software.

---

### Post by julian67 on 2008-02-24
> **pshah.mumbai said:**
> I have been reading about this issue lately...

Very sad at the way MONO has crept into gnome.

I want it out (atleast the vendors shouldnt distribute it) - keep it in optional repositories if needed.

I have already remove cli packages from default ubuntu and everything that has to do with mono.

Lets keep GNOME as a Free software.

Gnome & Mono are *both* free software and both distributed under free software licenses. Mono uses the MIT license.  The license is approved  as a free software license by the [FSF](http://www.fsf.org/) but is not a copyleft license.  

[http://en.wikipedia.org/wiki/Mit_license](http://en.wikipedia.org/wiki/Mit_license)

It seems many people are  affected by the fear, uncertainty and doubt propagated by persons who would like us all to believe that mono is not free software. btw X.org is also distributed under the MIT license. I hope you love your terminal emulator  ;-)

---

### Post by pshah.mumbai on 2008-02-24
C# standards are not compatible with free software. That makes mono standing on a shaky ground.

---

### Post by julian67 on 2008-02-24
> **pshah.mumbai said:**
> C# standards are not compatible with free software. That makes mono standing on a shaky ground.

even if there is a C# compiler, a Common Language Runtime just-in-time compiler, and a full suite of class libraries, all available as free software? 

I found this article [FSF Announces Support of Free Software Projects to Replace Components of Microsoft .NET](http://www.gnu.org/press/2001-07-09-DotGNU-Mono.html) where the FSF announces its support for the Mono and DotGNU projects, describes the aims and why the two projects complement each other. It mentions > The Mono Project is a community initiative to develop a Free Software, GNU/Linux-based version of the Microsoft .NET development platform. Incorporating key .NET compliant components, including a C# compiler, a Common Language Runtime just-in-time compiler, and a full suite of class libraries, the Mono Project will enable developers to create .NET applications and run them on Windows or any Mono-supported platform, including GNU/Linux and Unix.  also > Richard M. Stallman, founder of the GNU project and president of the Free Software Foundation, said: "With Mono and DotGNU, we hope to provide good alternatives to components of .NET, ones that will respect your freedom, and your privacy. You will be able to use the facilities of Mono and DotGNU either with, or without, the Internet, and using servers of your choice."...................Stallman added: "Mono will enable you to run your C# programs on the free GNU/Linux operating system using exclusively free software. With Mono, you will be able to use C# if you wish, without surrendering your freedom to study, share, change, and generally control all the software that you use." It seems to me that those goals are being achieved.

---

### Post by pshah.mumbai on 2008-02-24
Not really...sorry i fail to see it that way. 

> [http://www.gnome.org/~seth/blog/mono](http://www.gnome.org/~seth/blog/mono)

Miguel has repeatedly stated that the patents necessary to implement the standards ECMA-334 (C#) and ECMA-335 (CLI) are available from Microsoft "RAND + Royalty Free". This seems like an effective open patent grant and encouraged me initially that we could do Mono. I really like Mono. Its terrific technically, and I'd love to be able to use it. But two problems upon further consideration the past couple months:

   1. I've not seen an official statement by Microsoft that will let me trust the royalty free assertion. I think we are remiss if we do not assume Microsoft is looking for ways to, quite frankly, screw us. So unless there is a statement from Microsoft that they will have to stick to in a court, I feel (at the very least) uncomfortable.

   2. "RAND + royalty free", can still seriously screw Free Software. I think this is more important than the first point. Even with RAND + royalty free you still have to execute a license agreement with Microsoft, and license agreements can stipulate things that are RAND from a corporation perspective but still screw over Free Software. Also, there is evidence that key Microsoft people are already aware of (or planned?) incompatibilities between the licensing scheme for C#/CLI and, at least, the GPL. The eye of Sauron is upon us. RAND + royalty free is very different from a patent grant.

In short, we are in an adversarial situation. Microsoft does not want us to succeed. Thus we cannot trust Microsoft, even if we'd like to, and must consider Mono based upon the question "What is the worst thing MS can reasonably do?". We can only trust Mono if we are convinced Microsoft doesn't have weasel room. The current situation appears, to me, to have lots of weasel room. The technical merits of Mono are basically irrelevant if its a trojan horse in the long term.

---

### Post by julian67 on 2008-02-24
> **pshah.mumbai said:**
> Not really...sorry i fail to see it that way.

ok but the article is entitled "Why Mono is *Currently* An Unacceptable Risk" (my italics) and  those doubts were expressed almost 4 years ago. The bulk of the article is made up of hypothetical scenarios that the author feared at the time. As far as I can tell none of those scenarios played out. Perhaps it would be more helpful to focus on the situation as it is now (and how progress/future is seen now) rather than basing views on old hypotheses which did not actually become reality. There's an interesting faq at mono-project.com which is worth reading. One of the questions posed is "8.3 Do you fear that Microsoft will change the spec and render Mono useless?" Anyway you can read the answer for yourself.

---

### Post by pshah.mumbai on 2008-02-24
Same doubts still stand...microsoft has still failed to address those issues.

Its not about the specs if you read the quote again.

"The General Assembly of Ecma shall not approve recommendations of Standards which are covered by patents when such patents will not be **licensed by their owners on a reasonable and non-discriminatory basis**."

[http://www.ecma-international.org/memento/codeofconduct.htm](http://www.ecma-international.org/memento/codeofconduct.htm)

Did a little bit of digging. ECMA does not give you open patent grant. Still need to get a license from microsoft to implement those C# standards.

---

### Post by Simon G Best on 2008-02-24
> **julian67 said:**
> I found this article [FSF Announces Support of Free Software Projects to Replace Components of Microsoft .NET](http://www.gnu.org/press/2001-07-09-DotGNU-Mono.html) where the FSF announces its support for the Mono and DotGNU projects, describes the aims and why the two projects complement each other.

That press release is dated 2001, years before Novell's deal with Microsoft.

As for the question of whether or not Mono is truly free, I think that's really to do with Novell's deal with Microsoft, rather than a question of whether or not the copyright licences are Free Software licences.  It's not enough for just the copyright licences to be Free Software licences; if there are patents as well, but no Free Software *patent* licence, then it's not necessarily Free Software.

If (as Microsoft would have us believe) there are valid patents covering aspects of Mono, then Free Software *copyright* licences are not necessarily enough for the software to be Free in practice.  While the deal with Microsoft provides coverage for customers of Novell, it's not something that those customers can then, in turn, freely convey to subsequent recipients of copies of the software.  That raises questions of how Free Mono truly is, despite the fact that the *copyright* licences are Free Software licences.

That deal that Novell did with Microsoft really is rather murky, and does conflict with the spirit of Free and Open Source Software.  It's hardly surprising that there are now quite a few people who would rather not regard Mono as Free Software, even though the copyright licences are Free Software licences.

[There's plenty more about this stuff at Groklaw.]("http://www.groklaw.net/staticpages/index.php?page=20061218045851480")

---

### Post by julian67 on 2008-02-24
> **Simon G Best said:**
> 

If (as Microsoft would have us believe) there are valid patents covering aspects of Mono, then Free Software *copyright* licences are not necessarily enough for the software to be Free in practice. 

You could say the same thing about the Linux kernel or Open Office (Microsoft do). I do appreciate the other points you make but  MS making assertions of patent ownership/violation of patents without ever offering any substantive proof (or even evidence) is intended by them to introduce our old friends fear, uncertainty and doubt into the equation. I'm not sure what anyone can do except rely on the law and the enforcement of the copyrights asserted by the licenses.  The alternative would seem to be to abandon crucial technologies such as the kernel merely on the basis of unfounded assertions and allegations, which the protagonist refuses to validate by testing in court.

---

### Post by mangar on 2008-02-24
I'll throw my 0.02 local currency *thunk*
Relaying on competitor's technology is never a good idea, since it gives them leverage over your product - this is not oss/propriety related, but simple business  logic.

A simple and slightly non-related example - Nokia screwed Motorla quite well with their acquisition of Trolltech, since Motorola used Qtopia to create their user interface; Now they probably need to rebuild their entire UI stack, since Nokia can simply refuse to sell them new licenses.

Same with Mono - the best possible outcome will be - f/oss will have another VM based language, that is more or less java, with minor modifications - interoperability can be easily broken at any point by Microsoft, simply by moving forward with their code base, and having Mono constantly running several years behind it, implementation wise.
The only benefit I see for that approach is re-usage of existing talent pool in the .net developer community, and using their skills for developing foss software, but this scenario have several major weaknesses:

1. the code base will not be fully compatible with Microsoft's .net implementation, so those developers will have to learn the differences.

2. I don't see the motivation for someone who chose a propriety language to create foss code.

3. Mono will always be inferior to .net, simply by its catching-up, following the leader existance, so the number of people who'll use it will remain limited. (personally, I use tomboy and gnome-do a lot, and from looking at the Mono website, there's a grand total of about 20 product that use Mono [http://www.mono-project.com/Companies_Using_Mono#Who_uses_Mono.3F](http://www.mono-project.com/Companies_Using_Mono#Who_uses_Mono.3F)).

---

### Post by mangar on 2008-02-24
Current .net version: 1.0, 1.1, 2.0, 3.0, 3.5
mono is currently mostly compatible with 1.1

---

### Post by julian67 on 2008-02-24
[ Do you fear that Microsoft will change the spec and render Mono useless?]("http://www.mono-project.com/FAQ:_General#Do_you_fear_that_Microsoft_will_change_the_spec_and_render_Mono_useless.3F")

> **No.** Microsoft proved with the CLI and the C# language that it was possible to create a powerful foundation for many languages to inter-operate. We will always have that.

Even if changes happened in the platform which were undocumented, **the existing platform would have value on its own.**
Are you writing Mono from the ECMA specs?

Yes, we are writing them from the ECMA specs and the published materials in print about .NET.  (my bolds)

There's at least one person out there with no fear, uncertainty or doubt :-)

---

### Post by pshah.mumbai on 2008-02-24
Putting mono in ubuntu/gnome is not a good idea in long run. Let it remain on repositories for those who want mono apps.

It would be nice to keep it optional and not force it on gnome/ubuntu users.

Maybe parts of kernel are affected by patents, They can be removed if need arises. But mono is a different issue where it is totally dependent (language itself) on not so clear non-technical issues.

---

### Post by julian67 on 2008-02-24
> **pshah.mumbai said:**
> Putting mono in ubuntu/gnome is not a good idea in long run. Let it remain on repositories for those who want mono apps.

It would be nice to keep it optional and not force it on gnome/ubuntu users.

Maybe parts of kernel are affected by patents, They can be removed if need arises. But mono is a different issue where it is totally dependent (language itself) on not so clear non-technical issues.

I don't see any part of the distro as being *forced* on users. Of course you can't do without the GNU base and Linux kernel and associated tools but mono can be uninstalled (as you have done). It doesn't have any adverse affects (if you don't want the functionality of the apps it supports) and if the worst case scenarios envisaged by some here actually came to pass then it would be a simple thing to remove it and start seeking/creating alternatives. The language exists, MS can't retrospectively uncreate it. Like the mono faq states, if it became incompatible with its analogues in the proprietary world then "the existing platform would have value on its own." If that value was not perceived by the distros to be great enough then there would be reason for finding, or even creating, suitable replacement applications, perhaps not with the same feature sets initially, who knows? There are numerous distros, even numerous derivatives of Ubuntu, we do have a choice.  Meanwhile applications like Tomboy and F-Spot are providing unique and valuable features (or sets of features) and meet all the requirements to be freely distributable.

---

### Post by deepclutch on 2008-02-24
I hope tomboy and F-spot be ported to GTK2+ :-| .
**monobuntu** will be a good idea for mono fans ;) as with kabuntu for kde,xubuntu for xfce etc :D

Let the default Ubuntu(Gnome) be released without mono dep. :) then we all lived happily thereafter ;)

---

### Post by Simon G Best on 2008-02-24
> **julian67 said:**
> You could say the same thing about the Linux kernel or Open Office (Microsoft do). I do appreciate the other points you make but  MS making assertions of patent ownership/violation of patents without ever offering any substantive proof (or even evidence) is intended by them to introduce our old friends fear, uncertainty and doubt into the equation. I'm not sure what anyone can do except rely on the law and the enforcement of the copyrights asserted by the licenses.  The alternative would seem to be to abandon crucial technologies such as the kernel merely on the basis of unfounded assertions and allegations, which the protagonist refuses to validate by testing in court.

That's ignoring relevant differences between Mono and those other projects that have already, previously been pointed out.  It's also a matter of treating the issue as if it has to be either one extreme or the other - it doesn't.  Just because we need to include some stuff (the kernel, for example), it doesn't mean we therefore have to include everything else as well (such as Mono).

A crucial difference that's worth emphasising is that Novell don't have much of an incentive to *avoid* whatever patents Microsoft might have.  If anything, Novell potentially stands to benefit from not avoiding such patents, due to that deal it did with Microsoft.  It would be stupid for us to needlessly, avoidably help them with such FUD.

It's not the same with other things, such as the Linux kernel and OpenOffice.org, because Novell's just another contributor to such projects.  Other contributors, and those actually running those projects, do have an interest in being careful when it comes to patents.  But Novell is not merely a contributor to Mono.  Mono is basically a Novell project, is it not?  That's quite different.

Since Novell lost a lot of the community's trust by doing their deal with Microsoft, there are plenty of us who don't trust Novell to avoid whatever patents Microsoft might have.  I don't expect Microsoft to actually assert any of its patents, as it seems Microsoft prefers clouds of FUD instead, but I don't want to help Microsoft generate such FUD clouds, either.

Mono is such an obvious candidate for a patent infringement trojan - even if it really is just a bluff - that including it in the default installation really does seem unwise.  And it's a lot less necessary than, say, the Linux kernel.  Including it in the default installation really does seem like an unnecessary and easily avoidable way of helping Microsoft and Novell with their FUD.

FUD is bad.  Let's not help Microsoft and Novell create even more of it when we have an easy opportunity to avoid doing so.

---

### Post by Simon G Best on 2008-02-24
> **julian67 said:**
> There's at least one person out there with no fear, uncertainty or doubt :-)

Bad example, as he and Novell, his employer, stand to potentially benefit from the FUD.

---

### Post by reverseblade on 2008-02-24
> **mangar said:**
> Current .net version: 1.0, 1.1, 2.0, 3.0, 3.5
mono is currently mostly compatible with 1.1

This is incorrect. Although mono has missing libraries .NET 3.5 is mostly there in mono.

---

### Post by julian67 on 2008-02-24
> **Simon G Best said:**
> Bad example, as he and Novell, his employer, stand to potentially benefit from the FUD.

Bad example? It depends if you believe someone has to be disinterested to also be right about something or honest.

---

### Post by CarpKing on 2008-02-24
> **23meg said:**
> all its use cases are covered by Nautilus, EOG and F-Spot

Animated gifs are not supported by any of those (unless there's a change to EOG that I didn't hear about).

---

### Post by pshah.mumbai on 2008-02-25
> I don't see any part of the distro as being forced on users. Of course you can't do without the GNU base and Linux kernel and associated tools but mono can be uninstalled (as you have done). It doesn't have any adverse affects (if you don't want the functionality of the apps it supports) and if the worst case scenarios envisaged by some here actually came to pass then it would be a simple thing to remove it and start seeking/creating alternatives. The language exists, MS can't retrospectively uncreate it. Like the mono faq states, if it became incompatible with its analogues in the proprietary world then "the existing platform would have value on its own." If that value was not perceived by the distros to be great enough then there would be reason for finding, or even creating, suitable replacement applications, perhaps not with the same feature sets initially, who knows? There are numerous distros, even numerous derivatives of Ubuntu, we do have a choice. Meanwhile applications like Tomboy and F-Spot are providing unique and valuable features (or sets of features) and meet all the requirements to be freely distributable.

Mono does remain - but not on default setup. This is a very bad idea.

No one is saying to remove mono completely. So whats the objection about ? We just want that it shouldnt be included in the default install.

---

### Post by 23meg on 2008-02-25
> **neighborlee said:**
> They are #241, 242 and 243.

cheers
nl

Thanks; I had read those posts in full when they were posted. Now, how do you think they should have figured into the decision to remove gThumb?

---

### Post by 23meg on 2008-02-25
> **CarpKing said:**
> Animated gifs are not supported by any of those (unless there's a change to EOG that I didn't hear about).

Good point. I've added a comment to [the relevant bug]("https://bugs.launchpad.net/ubuntu/+source/eog/+bug/35545") and increased its importance.

---

### Post by Simon G Best on 2008-02-25
> **julian67 said:**
> Bad example? It depends if you believe someone has to be disinterested to also be right about something or honest.

That's simply mischaracterising my position.

It's not a matter of Novell merely not being "disinterested".  Novell has already sought to take advantage of the patent FUD by doing its deal with Microsoft.  It is now party to the FUD.  Their lack of Fear, Uncertainty and Doubt is hardly reassuring!

---

### Post by julian67 on 2008-02-25
> **Simon G Best said:**
> That's simply mischaracterising my position.

It's not a matter of Novell merely not being "disinterested".  Novell has already sought to take advantage of the patent FUD by doing its deal with Microsoft.  It is now party to the FUD.  Their lack of Fear, Uncertainty and Doubt is hardly reassuring!

I agree that the Novell/MS deal is unfortunate and unethical (though they were skilled enough to ensure it was legal) and am happy that the revised GPL addresses the issues it raises by making a similar future deal impossible, and also by the gradual de facto invalidation of the agreement as more and more projects adopt GPL v3), but I'm yet to be convinced that the deal taints all the FOSS projects either sponsored by Novell or those to which Novell contributes. (I think the supposition that the deal does taint Novell's contributions is a central part of people's objections to Mono, aside from the reservations expressed about performance/disk size).

---

### Post by Simon G Best on 2008-02-25
> **julian67 said:**
> I agree that the Novell/MS deal is unfortunate and unethical (though they were skilled enough to ensure it was legal) and am happy that the revised GPL addresses the issues it raises by making a similar future deal impossible, and also by the gradual de facto invalidation of the agreement as more and more projects adopt GPL v3), but I'm yet to be convinced that the deal taints all the FOSS projects either sponsored by Novell or those to which Novell contributes. (I think the supposition that the deal does taint Novell's contributions is a central part of people's objections to Mono, aside from the reservations expressed about performance/disk size).

Well, there are those who believe that it does somehow taint Novell's stuff, and there are those who believe that it doesn't, but who believe that the fear of tainting is part of the FUD.  I'm probably in the latter category.

The theory, as I understand it, is that Pointy-Haired Bosses (PHBs) (the original PHB is a character in Dilbert cartoon strips, sort of a technically ignorant middle manager character) will want to "play it safe", and avoid things like Mono - unless it's from a "safe" vendor like Novell.  It's easier to simply avoid Mono-"contaminated" distributions such as Ubuntu than it is to get into all the nitty-gritty of how things actually stand legally.  And lawyers are very good at advising that there are no legal certainties until a court actually rules on something.

Of course, we can go on and on about how Microsoft won't specify which patents it refers to, how Novell's deal with Microsoft is probably not all it's cracked up to be, how things probably wouldn't stand up in court if Microsoft did litigate, and so on, but that just confirms, to the PHBs of this world, how complicated - and therefore uncertain - it all is.  It's just so much easier, and "safer", to just play it safe and buy from Novell rather than getting Mono-"contaminated" distributions from elsewhere.

So, while including Mono in Ubuntu by default might not taint Ubuntu in an IP-infringement sense, it does still taint it in a FUD sense.  Including it in Ubuntu gives PHBs, and the like, a powerful "reason" for buying from Novell instead, or at least for avoiding Ubuntu.  I really don't want to help Microsoft and Novell do that.

---

### Post by julian67 on 2008-02-25
From what I've read the MS/Novell deal is already showing cracks due to the 2 different corporations' understanding of how Novell products containing GPL v3 code in current/future versions are affected by the deal. It's clear from the news reports of Ubuntu adoptions in enterprise (i.e French parliament), several other governments, and Dell  working on certifying Ubuntu for all its server products (as well as selling PCs/laptops with Ubuntu pre-installed) that some important and high profile organisations are not deterred.

---

### Post by pshah.mumbai on 2008-02-25
> From what I've read the MS/Novell deal is already showing cracks due to the 2 different corporations' understanding of how Novell products containing GPL v3 code in current/future versions are affected by the deal. It's clear from the news reports of Ubuntu adoptions in enterprise (i.e French parliament), several other governments, and Dell working on certifying Ubuntu for all its server products (as well as selling PCs/laptops with Ubuntu pre-installed) that some important and high profile organisations are not deterred.

I second that. Few year back it wouldnt have mattered much - but seeing the current and future state and more large scale deployments coming up it would have been a wiser move to avoid mono in the default setup.

---

### Post by pshah.mumbai on 2008-02-25
> From what I've read the MS/Novell deal is already showing cracks due to the 2 different corporations' understanding of how Novell products containing GPL v3 code in current/future versions are affected by the deal. It's clear from the news reports of Ubuntu adoptions in enterprise (i.e French parliament), several other governments, and Dell working on certifying Ubuntu for all its server products (as well as selling PCs/laptops with Ubuntu pre-installed) that some important and high profile organisations are not deterred.

I second that. Few year back it wouldnt have mattered much - but seeing the current and future state and more large scale deployments coming up it would have been a wiser move to avoid mono in the default setup.

The bad is much more than the good.

---

### Post by smartboyathome on 2008-02-25
> **pshah.mumbai said:**
> I second that. Few year back it wouldnt have mattered much - but seeing the current and future state and more large scale deployments coming up it would have been a wiser move to avoid mono in the default setup.

Though, for a home user, they won't care if mono is installed or not (unless they live in fear of microsoft like a lot of current Ubuntu users), and cooperations can remove Mono if they don't need the apps that it provides.

---

### Post by neighborlee on 2008-02-25
> **smartboyathome said:**
> Though, for a home user, they won't care if mono is installed or not (unless they live in fear of microsoft like a lot of current Ubuntu users), and cooperations can remove Mono if they don't need the apps that it provides.

So your saying ignorance of a given situation merits not being protected from it ?

hm somehow I doubt thats what your getting at ;)

cheers
nl

---

### Post by neighborlee on 2008-02-25
> **julian67 said:**
> From what I've read the MS/Novell deal is already showing cracks due to the 2 different corporations' understanding of how Novell products containing GPL v3 code in current/future versions are affected by the deal. It's clear from the news reports of Ubuntu adoptions in enterprise (i.e French parliament), several other governments, and Dell  working on certifying Ubuntu for all its server products (as well as selling PCs/laptops with Ubuntu pre-installed) that some important and high profile organisations are not deterred.

We'll see but its doubtful if you read the M$ attorny's opinion on it ( his opinion of course is all ) ,,,but its also very relevant at least to most of us that care about all of this, that novel paying money to M$ for patent infringement is certainly one more reason to steer clear of MONO because obviously here novel is saying yes we are infringing.  Isn't $40 MIL alot of moola ( continuing through to 2011 ) to pay someone if your clean like most FOSS is ? ;)

I'm completely and totally for FOSS even if M$ does it, but ahm when Redhat   clearly steers away from something like this, shouldn't the rest of us consider  being duly warned ?

[http://news.zdnet.co.uk/software/0,1000000121,39246774,00.htm](http://news.zdnet.co.uk/software/0,1000000121,39246774,00.htm) < how about this ? ;)

"The Fedora Foundation is a community of users who have a common interest in many technologies. Mono is a technology of interest to this community and the group has decided to include Mono in Fedora Core 5," said the spokesperson. "At this time, Red Hat has no plans for the endorsement or productisation [sic] of Mono."

" It is also possible that legal worries delayed adoption on Red Hat's part. Microsoft holds a number of patents around the .Net framework, which Mono could potentially infringe. Miguel de Icaza, the founder of the Mono project, said in an interview in 2004 that although the project team do not think the product infringes any Microsoft patents, it is difficult to be fully sure due to the number of patents held by Microsoft and the complexity of their claims. "

 I realize its from 2006, but Redat is still not embracing MONO.

cheers
nl

---

### Post by neighborlee on 2008-02-25
> **23meg said:**
> Thanks; I had read those posts in full when they were posted. Now, how do you think they should have figured into the decision to remove gThumb?

One of the claims from his posts I found  really distrubing was:

"  Among those who had been in early contact with Rhys, and studied his .NET research and C# compiler solution, was Miguel de Icaza of Gnome fame. And, from what I understand, Rhys and others had expected him to continue to work with the Portable.NET project. Instead, de Icaza enlisted the help of (most of) his team of programmers in Ximian (the company of which he was co-founder) to do - silently, behind closed doors - some development on their own.  "

...then there were two.
In July, Miguel de Icaza and Ximian went public. A new, Ximian-led, open-source project, called "Mono" was created, and de Icaza announced the news on the dotnet mailing list, 9 July 2001 <

so I'm just wondering what happeneed, that PNET which seems fro initial discovery to be superior to MONO, that Miguel decided not to help Rhys and    enlisted Novels help to get developers on staff for MONO ...

Anyway,- ...Ratatosk went to alot of trouble and I think he deserves this be talked about, or at the very least those supporting MONO without  reserve be willing to address all his concerns; if not on these forums then a IRC chat or 'something'.

cheers
nl

---

### Post by smartboyathome on 2008-02-25
> **neighborlee said:**
> We'll see but its doubtful if you read the M$ attorny's opinion on it ( his opinion of course is all ) ,,,but its also very relevant at least to most of us that care about all of this, that novel paying money to M$ for patent infringement is certainly one more reason to steer clear of MONO because obviously here novel is saying yes we are infringing.  Isn't $40 MIL alot of moola ( continuing through to 2011 ) to pay someone if your clean like most FOSS is ? ;)

I'm completely and totally for FOSS even if M$ does it, but ahm when Redhat   clearly steers away from something like this, shouldn't the rest of us consider  being duly warned ?

[http://news.zdnet.co.uk/software/0,1000000121,39246774,00.htm](http://news.zdnet.co.uk/software/0,1000000121,39246774,00.htm) < how about this ? ;)

"The Fedora Foundation is a community of users who have a common interest in many technologies. Mono is a technology of interest to this community and the group has decided to include Mono in Fedora Core 5," said the spokesperson. "At this time, Red Hat has no plans for the endorsement or productisation [sic] of Mono."

" It is also possible that legal worries delayed adoption on Red Hat's part. Microsoft holds a number of patents around the .Net framework, which Mono could potentially infringe. Miguel de Icaza, the founder of the Mono project, said in an interview in 2004 that although the project team do not think the product infringes any Microsoft patents, it is difficult to be fully sure due to the number of patents held by Microsoft and the complexity of their claims. "

 I realize its from 2006, but Redat is still not embracing MONO.

cheers
nl

Do the patents stand in the UK? Just wondering, because I noticed all the companies that Microsoft has been going after so far have been U.S. companies (which Canonical is not).
Also, just because one company does something means others should? So since all the other companies are signing deals with MS that means all should, right?

---

### Post by Simon G Best on 2008-02-25
> **smartboyathome said:**
> Do the patents stand in the UK? Just wondering, because I noticed all the companies that Microsoft has been going after so far have been U.S. companies (which Canonical is not).

US patents apply in the US, and generally don't apply beyond the US.  Whether they apply to Canonical doesn't depend on whether Canonical's a US company or not.  US patents apply in the US, and that applies to Canonical just as much as it applies to IBM.

---

### Post by chandru.in on 2008-02-25
> When the full list for patents becomes available, the question is what will open-source vendors do if they find pieces that have historically infringed: will they choose to license and be the recipients of the community wrath, or will they hold their grounds and risk a lawsuit?

[http://www.news.com/8301-13580_3-9876425-39.html]("http://www.news.com/8301-13580_3-9876425-39.html")

Sounds like the beloved developer of Mono is helping spread FUD to ensure that his employer can use their deal to gain advantage.

:popcorn:

---

### Post by MaxCharge on 2008-02-25
> **chandru.in said:**
> 
Sounds like the beloved developer of Mono is helping spread FUD to ensure that his employer can use their deal to gain advantage.


Assuming you mean this quote (Emphasis added):

> 
• Miguel de Icaza, founder of the GNOME project and a Novell programmer working on Mono, an open-source implementation of Microsoft's .Net software: "As a chess move, it is a fascinating one...**On the surface it looks very good. (There are) lots of things that we want to interoperate with--Office, SQL Server, SharePoint.** Getting the documentation to everyone sounds great, and it seems like they are serious about doing more interoperability work...When the full list for patents becomes available, the question is what will open-source vendors do if they find pieces that have historically infringed: **will they choose to license and be the recipients of the community wrath, or will they hold their grounds and risk a lawsuit?"**

Which part is fud? If it turns out you *have* and *are* infringing on a patent, surely you'd do something about it? I don't see FUD in the highlighted paragraphs, which appear to be the two most important parts of that snippet.

---

### Post by smartboyathome on 2008-02-25
Actually, I just read in the paper today that they will not be sued for infringing lawsuits, as long as it is not used commercially. Kudos for microsoft with a half step in the right direction.

---

### Post by MaxCharge on 2008-02-25
I just want to link [this thread]("http://ubuntuforums.org/showthread.php?t=707184") here so i can get feedback. I've read through about a dozen pages of this thread before i got lost trying to find understand exactly what issues people have. If we, as a group, can explicitly lay out the issues in a clear concise way, its possible they can be dealt with.

For example, if a big issue is the size of the default mono installation, that can be dealt with. Mono is in components, we just need to remove components which are not needed by the other bundled mono apps. A fairly minimal mono is a mere 3.4MB download, 8MB installed. Mono itself only has a dependency on glib, which every system already has.

For a detailed look: [http://www.meebey.net/jaws/?gadget=Blog&action=SingleView&id=Hello_World_how_small_can_you_get](http://www.meebey.net/jaws/?gadget=Blog&action=SingleView&id=Hello_World_how_small_can_you_get)

So, please detail your issues.
Thanks.

---

### Post by SonicSteve on 2008-02-25
I'm not trying to minimize this discussion but man does it feel like we're spinning our tires. The more I read about this the more I feel I just don't have the required knowledge of the intricacies involved to make a wise decision. 

In the end I think we would agree keeping mono would be a win if;
1. more people felt at home in Linux because of familiar apps 
- the con of this is that it's already happening without mono's help. Gimp, firefox, openoffice. These 3 apps helped introduce me to Linux and opensource.
2. Python survives and thrives (assuming it deserves to, in not a programmer I really don't know except from what others say)
3. Microsoft doesn't turn around and close the interoperability door a few years into things (which I suspect they will). It just seems too much to believe that they've changed from hiring a team to better know Linux towards the goal of defeating it, to now embracing the opensource that they once referred to as cancer. I believe the hidden agenda is alive and kicking. 
Certainly the founder of Opera browser is doubting Microsoft's sincerity 
[http://www.theregister.co.uk/2005/02/11/hakon_on_ms_interroperability/](http://www.theregister.co.uk/2005/02/11/hakon_on_ms_interroperability/) 
He knows far more about it than I do.

In the end it comes down to pros and cons, can microsoft really be trusted? Is mono really worth investing in. Is there an opportunity to use mono to the advantage of opensource? Perhaps removing mono is just a fearful knee jerk reaction. It would a terrible shame to miss out on an opportunity because of fear. 

I'll ask this question again,
We have some very tallented programmers, is it completely impossible to use Mono/ .net to linux's advantage? 
Just a few thoughts.

---

### Post by Simon G Best on 2008-02-26
> **smartboyathome said:**
> Actually, I just read in the paper today that they will not be sued for infringing lawsuits, as long as it is not used commercially. Kudos for microsoft with a half step in the right direction.

That's not even half a step in the right direction - but they want you to think so, and you're falling for it.

Microsoft knows that allowing "Free" and "Open Source" Software for only noncommercial use is something of a contradiction.  It's neither Free nor Open Source Software if it can't be used commercially.  Their "half step in the right direction" is a false concession.  It's a part of their propaganda campaign to confuse and mislead, to make it look like they're being reasonable and cooperative when they're actually spreading FUD about commercial use of Free and Open Source Software.

By saying that they will not sue "as long as it is not used commercially", they are saying, by clear implication, that they may sue for commercial use.  It is a thread of litigation, very thinly disguised as "half step in the right direction".  So it really is yet another example - and a very clear and transparent one - of typical Microsoft FUD.  And yet you say, "Kudos for microsoft".

---

### Post by MaxCharge on 2008-02-26
> 
Firstly, i wanted to split this out from that other thread which is a raging discussion on whether mono should be included in Ubuntu or not. If a mod thinks it really should be part of that discussion, i'll dump this thread and start the discussion in there. It's just i have a very specific question in mind and i don't want it to get swamped in that thread.

First, a few guidelines:
1) I do do not want to hear about how great Mono is or how great X is. Everyone has their own opinion. Let's assume everything is great in a technical sense.
2) I do not want to hear anything that doesn't have a link to back it up. If you make a claim about something, make sure you can back it up. Links to rants in blogs aren't acceptable.
3) I do not want to hear that M$ is evil and is out to take over the world. I know they are a convicted monopoly, but that's not relevant to this question.
4) I do not want to hear about other issues you have with other applications/libraries that use Mono. For example, just because application X exists and it's bad doesn't mean mono should be removed.
My very specific question is:


What exactly is it in mono that you want removed? Secondly, why do you want those specific components removed


A) The JIT and .NET environment, as standardised here
B) The C# language itself, as standardised here
C) The ECMA'ed class libraries, which i believe are also covered here
D) The non-ECMA'ed libraries such as Winforms
E) The .NET libraries which facilitate interop with native linux libraries such as GTK#, glib# etc
F) The third party applications such as Banshee, Beagle, Fspot etc

I think that covers all the obvious ways to split up the mono stack, so tell me (assuming you want mono removed from Ubuntu by default), why is it you want these components removed. What is your argument.



[quote="Simon G Best"]
You ask "why", having already refused to allow whole categories of possible answers!
[/quote]

Let me clarify what exactly i don't want to hear:

1) I do not want to hear an argument along the lines of "mono is great, therefore we should include it". Or "mono is crap, we shouldn't include it", with nothing to back that up. 

If you want to claim that, you'd need to provide technical reasons why mono is great or crap **on a technical level** as compared to other available languages. I haven't seen that mentioned anywhere here when making either of those claims.

As we're talking about a live CD here, i suppose that you'd need to show that the features offered by the mono-using applications are all available in competing non-mono applications.

2) Pretty self explanatory - that just means i don't want junk. Any joe soap can rant about X and Y, but unfortunately that doesn't make any of it true. Linking to a dozen blogs of people ranting won't lend credence to your argument.

3) If you're argument is "Microsoft is evil, therefore we don't want mono", that's not an argument. MS are a convicted monopoly, that is well known. However, mono is not Microsoft. It's not owned by microsoft any more than portable.net is.

If you think that MS has some legal claim on mono, then give some kind of evidence to that claim. Then you have a legitimate argument. I suppose if you were using this as a reason to remove mono, you'd have to show that mono is actually at a noticeably higher risk than other applications at infringing patents, especially portable.net.

4) All i'm saying is that you can't use OOXML as an argument to remove mono. For example, If you deem that Moonlight is against the FOSS principles, that's a reason to not include Moonlight, **not** a reason to remove mono. Mono is a separate entity.

Does that help?

---

### Post by chandru.in on 2008-02-26
> **smartboyathome said:**
> Actually, I just read in the paper today that they will not be sued for infringing lawsuits, as long as it is not used commercially. Kudos for microsoft with a half step in the right direction.

You are right.  But hey any popular distribution which helps promoting Linux is nothing but commercial (Red Hat, Ubuntu (Canonical), Mandriva, Xandros, etc.)

---

### Post by smartboyathome on 2008-02-26
Actually, Ubuntu isn't commercial. Commercial (in this case) is selling it for profit.

---

### Post by chandru.in on 2008-02-26
The word "commercial" is defined differently in differen nations' laws.  Canonical does provides service around Ubuntu.  This is nothing but first class commerce.  So may be Canonical will have to stop providing support.  Then it wud soon go out of business.

---

### Post by smartboyathome on 2008-02-26
In this case, providing support does not break the microsoft suing deal. It is just providing services, the product itself is still noncommercial (at least in the U.S.).

---

### Post by Simon G Best on 2008-02-26
> **smartboyathome said:**
> Actually, Ubuntu isn't commercial. Commercial (in this case) is selling it for profit.

Firstly, that's really missing the point.  Secondly, it's too narrow a definition of what counts as "commercial".  Thirdly, you're relying on Microsoft being reasonable and consistent in its use and application of the word "commercial".

I'll deal with the second and third points first, and get them out of the way.

Last year, I bought a Dell Inspiron 530n with Ubuntu 7.04 preinstalled - that's clearly commercial.  And then I used it, with Ubuntu, in the course of providing consultancy services.  That, again, was commercial, as I was selling those services and using Ubuntu to provide those services.  I was making commercial use of Ubuntu.  Canonical provides Dell with copies of Ubuntu as part of a commercial arrangement to sell support services in relation to Ubuntu.  So even there Canonical's provision of Ubuntu to Dell is part of a commercial arrangement.  Both Canonical and Dell have made commercial use of Ubuntu.

The point, there, is that there's more to "commercial" than just "selling it for profit."  And relying on Microsoft to be reasonable and consistent with its use of the word "commercial" is hardly realistic.  This is Microsoft we're talking about.

But it's the first point that really matters.  As I say, the stuff about what counts as "commercial" is really missing the point.

It doesn't matter whether or not Microsoft's attempt to limit the use of Linux-based systems to noncommercial uses affects Ubuntu.  It doesn't really matter whether or not it affects Canonical.  Such a limitation is simply in contradiction to Ubuntu being Free and Open Source Software.  Giving Microsoft kudos for trying to impose such a limitation suggests that you're not really a friend of Free and Open Source Software, but a foe.  Or, at the very least, that you don't really understand what Free and Open Source Software is, or what the point of it is.

But, I note from your profile, that you're just 14.  So I'll give you the benefit of the doubt, and, at the risk of seeming patronising, I'll assume that you're just yet to learn enough about this stuff.

---

### Post by Simon G Best on 2008-02-27
At [Groklaw]("http://www.groklaw.net/"), there's currently a News Pick that looks like it's about what smartboyathome has recently been commenting about.

Here, again, are two of smartboyathome's recent comments:-

> **smartboyathome said:**
> Actually, I just read in the paper today that they will not be sued for infringing lawsuits, as long as it is not used commercially. Kudos for microsoft with a half step in the right direction.

> **smartboyathome said:**
> Actually, Ubuntu isn't commercial. Commercial (in this case) is selling it for profit.

The Groklaw News Pick quotes [Patent Pledge for Open Source Developers]("http://www.microsoft.com/interop/principles/osspatentpledge.mspx"), apparently first published on the 22nd February.  Here's the part Groklaw quoted, with emphasis added by me:-

> To benefit from this promise, You must be a natural or legal person participating in the creation of software code for an open source project. An "open source project" is a software development project the resulting source code of which is freely distributed, modified, or copied pursuant to an open source license *and is not commercially distributed by its participants.* If You engage in the commercial distribution or importation of software derived from an open source project *or if You make or use such software outside the scope of creating such software code, You do not benefit from this promise for such distribution or for these other activities.*

In the Groklaw News Pick, PJ remarked:-

> Microsoft has come up with its own proprietary definition, if I may call it that, of Open Source projects.

Since Microsoft is clearly trying to redefine the term "open source" so as to limit it to software that the "source code of which ... is not commercially distributed by [the creating project's] participants", it's fair to say that Microsoft is trying to redefine the term "open source" to mean something significantly different to the terms "Free Software" as defined by the FSF and "Open Source" as defined by the Open Source Initiative.

Like I said, in my previous comment, those who would give Kudos to Microsoft for this are not being good friends to Free and Open Source Software.

Let's take a more detailed look at that "Patent Pledge for Open Source Developers".  The first line looks interesting (emphasis mine):-

> Microsoft irrevocably promises not to assert any Microsoft *Necessary Claims* against you as an open source software developer ("You") for making, using, importing, or distributing any implementation *of a Covered Specification* ("Covered Implementation"), subject to the following.

What is a "Necessary Claim"?  What is a "Covered Specification"?

The start of the second paragraph answers these questions:-

> To clarify, "Microsoft Necessary Claims" are those claims of Microsoft-owned or Microsoft-controlled patents that are necessary to implement the Covered Specification. "Covered Specifications" are listed below.

And, at the end of the "Patent Pledge", we do indeed find (with emphasis in the paragraph (not the heading) added by me):-

> **Covered Specifications (the promise applies individually to each of these specifications):**

“Open Protocol Specifications” (as published at msdn.microsoft.com/openprotocols or its successor site) for *the protocols implemented in the current and future versions of Windows Vista including the .NET Framework,* Windows Server 2008, SQL Server 2008, Office 2007, Exchange 2007, and Office SharePoint Server 2007, *that are used by any other Microsoft product to connect with these products.*

Does that cover Mono?  Well, if it's implementing "the protocols implemented in the current and future versions of Windows Vista including the .NET Framework ... that are used by any other Microsoft product to connect with these products", then yes, as long as the only "Microsoft-owned or Microsoft-controlled patents" that cover aspects of Mono "are necessary to implement the Covered Specification."  But if there's another way to implement such a patent-encumbered aspect of Mono, then it's not "necessary", and so this "Patent Pledge" wouldn't apply.

Note, in particular, the limitation to "protocols implemented in the current and future versions of Windows Vista".  "Protocols".  **"Protocols".**  "protocols ... that are used by any other Microsoft product to connect with these products."  **It's just the protocols!**  And what's more, it's just "the protocols implemented in the current and future versions of Windows Vista", which means implementations covered by this "Patent Pledge" need to be sufficiently up-to-date.

Is Mono just the covered protocols?  Is it sufficiently up-to-date?  Is this "Patent Pledge" really any good for Ubuntu?

Returning to the main body of the "Patent Pledge", we see, in the second paragraph, that Microsoft clarify what they mean when they use the word "commercial".  In particular, there's this:-

> Software is deemed to be commercially distributed within the meaning of this promise when the distributor derives revenues in connection with the distribution, such as from subscriptions, updates, or user-based connection fees or from services that are contractually required for a customer to obtain the current version and/or updates of the software product in question.

Now, what was smartboyathome saying "commercial" meant?  He was, at best, very badly mistaken!  I'll give him the benefit of the doubt and assume he wasn't deliberately trying to deceive us.

This "Patent Pledge" is a good example of why we simply can't trust Microsoft when it comes to Free and Open Source Software.  It's a pledge that supposedly accommodates Free and Open Source Software, yet does so in a way that tries to redefine "open source" to mean something fundamentally different.  It's naive at best to expect Microsoft to be reasonable and play by the rules - they even want to sneakily redefine other people's terminology!

Like I said in my previous comment, those who would give kudos to Microsoft for their "Patent Pledge" are either badly mistaken, or are opponents of Free and Open Source Software.

When it comes to such things as Mono, those who want to limit discussion to purely technical matters would have us blinkered and blinded to Microsoft's games.  Such mindless dogmatism, where we ignore where Mono's coming from simply because the copyright licences happen to be Free Software and Open Source licences, is unwise at best.  There's no need for us to ignore the attempts by Microsoft, and others, to subvert and pervert such things as "Free Software" and "Open Source".

Of course, ideally, we certainly should be able to make decisions on what to include in the default installation on purely technical, licencing and user-oriented grounds, *but Microsoft and Novell aren't letting it be that simple.*  Fortunately, a Free and Open Source Software copyright licence does not actually *oblige* us to use, accept or distribute such software.  After all, the point of Free Software is *freedom*, and that includes the freedom to decline such software *for whatever reason we like.*  So, insisting on limiting the possible reasons for rejecting Mono in the ways that some here have tried is simply inconsistent with what Free and Open Source Software fundamentally is in the first place.  *If we don't like where the software's coming from, we don't have to accept it.*

---

### Post by plun on 2008-02-27
> **Simon G Best said:**
>  There's no need for us to ignore the attempts by Microsoft, and others, to subvert and pervert such things as "Free Software" and "Open Source".
[/i]

Why not... :confused:

We have a group of users which burn their time with MS hate instead of
making Open Source software better... and boycott Novell campaigns.

Looks really good.
[http://www.monodevelop.com/Release_notes_for_MonoDevelop_1.0_Release_Candidate_1](http://www.monodevelop.com/Release_notes_for_MonoDevelop_1.0_Release_Candidate_1)

Also Trolltech understands this...
[http://trolltech.com/](http://trolltech.com/)

"To eat or to be eaten"... this is just business...

---

### Post by julian67 on 2008-02-27
> **plun said:**
> Why not... :confused:

We have a group of users which burn their time with MS hate instead of
making Open Source software better... and boycott Novell campaigns.

Looks really good.
[http://www.monodevelop.com/Release_notes_for_MonoDevelop_1.0_Release_Candidate_1](http://www.monodevelop.com/Release_notes_for_MonoDevelop_1.0_Release_Candidate_1)

Also Trolltech understands this...
[http://trolltech.com/](http://trolltech.com/)

"To eat or to be eaten"... this is just business...

I agree. Unfortunately this debate (if it is a debate) has seen persons not opposed to mono being Ubuntu default being characterised as  "mono lovers" "mono fanboys" "microsoft fanboys" "Microsoft apologist" "Novell apologist".  There are statements such as "If companies like Novell or persons like Icaza love to help Microsoft spreading FUD and lies, they can do it",   we've been told of "Miguel De Icaza's history of essentially pro-Microsoft claims", seen questions posed such as "Can I ask: what, if any, relationship do you have with Novell? Or Microsoft?" and "Do you do paid marketing/PR work for Novell, by any chance? Or unpaid marketing/PR work?"

We've also seen the founder of Gnome characterised as "dodgy". 

These are all genuine quotes, easily found in this thread.

This by the way is all in the first 7 pages, the thread is now at page 42, but it's enough to get an idea of whether this is a debate or something else. It looks to me more like a set of non-negotiable demands, accompanied by negative characterisations,  unpleasant insinuations and even accusations...aka ad hominem attack.  This is all clearly to be seen in the quotes above and more extensively in the thread as a whole, it's not a matter of my opinion. There's a lot of energy going into this and even abusive pm sent (I received a very nasty one complete with foul language, since dealt with by a moderator). 

I use mono and do not object to it.  I *do* object to this leading me to being labelled (with others) as a mono/MS/Novell fanboy/lover/apologist which are terms expressing  derision, animosity, and ridicule.  Doing this also makes the protagonists (in my eyes) less and less credible as any reasonable points or facts they *might* use to support their view become obscured and ultimately discredited.

---

### Post by Simon G Best on 2008-02-27
Looks like you're trying to paint your opponents as mud-slingers.  In fact, you're cherry-picking your quotes in order to mischaracterise your opponents that way.

> **julian67 said:**
> These are all genuine quotes, easily found in this thread.

Okay, let's see...

> "mono lovers"

A term used by chandru.in.  I don't think anyone else has actually used that term.  I agree it's not terribly helpful.  Neither was the following mischaracterisation, from plun, quoted by you, in the comment you were replying to:-

> a group of users which burn their time with MS hate

Back to your comment:-

> "mono fanboys"

soc, in one post.

> "microsoft fanboys"

No one seems to have used that term.  At least, searching for it hasn't yielded any results.  So if it's a genuine quote, as you claim, in which comment did you find it?

> "Microsoft apologist"

[That was me]("http://ubuntuforums.org/showpost.php?p=3716848&postcount=37"); I'll quote the relevant bit here (in which I'm quoting and replying to gnomeuser):-

> [QUOTE]I mean if we are just out to hate on Microsoft, and I don't deny they did a lot of bad stuff in the past.. but look at them now, they got certain licenses that forfill the open source definitions and are certified as such. We banged on them for years to document their file formats something we then proceeded to give them a lashing for. Sure they still need to learn but remove Steve Ballmer who attacks us regardless of what the heck is going on. It could be raining donuts and strippers at Microsoft HQ and he'd blame Linux for the pom poms not being sassy enough.

You're sounding like a bit of a Microsoft apologist, there. Or are you just really, really naive about Microsoft?[/QUOTE]

Back to your comment:-

> "Novell apologist".

Me again, same post.  Here's the relevant bit, again in which I'm quoting and replying to gnomeuser:-

> [QUOTE]Now Novell are our friends,

Really?

> they are also a company, a company with a long history in the old 80's and 90's IT business model. They will comtinue to make deals, sadly they do not yet have a good grip of what kinds of deals will involve an emotional backlash. Novell also have really poor advocacy, they are really bad at having their projects and technologies getting the exposiour they deserve. A lot of cool stuff is going on at Novell,

Now you're sounding like some sort of a Novell apologist. Can I ask: what, if any, relationship do you have with Novell? Or Microsoft?[/QUOTE]

Back to your comment again:-

> There are statements such as "If companies like Novell or persons like Icaza love to help Microsoft spreading FUD and lies, they can do it",

Well, by doing that deal that Novell did with Microsoft, Novell has, in a way, helped Microsoft spread "FUD and lies".  That's a big part of why many in the community were so unhappy with it.

> we've been told of "Miguel De Icaza's history of essentially pro-Microsoft claims",

[That was libervisco]("http://ubuntuforums.org/showpost.php?p=3760739&postcount=70"), the part you quoted being this:-

> Situation with Mono is less certain than with mp3 codecs, but considering how close this technology is to Microsoft's and considering the very nature of Mono itself and Miguel De Icaza's history of essentially pro-Microsoft claims, there may be enough reason to be vary of it.

Back to your comment:-

> seen questions posed such as "Can I ask: what, if any, relationship do you have with Novell? Or Microsoft?" and "Do you do paid marketing/PR work for Novell, by any chance? Or unpaid marketing/PR work?"

[Me again, same post as before.]("http://ubuntuforums.org/showpost.php?p=3716848&postcount=37")

The reason I asked gnomeuser those questions is because, in the comment I was responding to, I got the impression that he *might* have been astroturfing, or something.  Rather than just launch such an accusation straight away, I asked questions instead.

> We've also seen the founder of Gnome characterised as "dodgy".

[Me, in one comment.]("http://ubuntuforums.org/showpost.php?p=3667891&postcount=7")  Here's what I actually said:-

> I'm not suggesting we remove every single little thing that Microsoft suggests might be infringing. But Mono is something of a special case - Miguel de Icaza and Novell. There's a reason he has the kind of dodgy reputation he's got.

Perhaps a more "diplomatic" way for me to have put it would have been to say he's "controversial".

Anyway, that one example seems to be the only example of de Icaza being "characterised" as having a "dodgy" kind of reputation.  There are plenty of examples of me characterising Novell's deal with Microsoft as "dodgy", though.  I do think de Icaza's gained a bit of a reputation for being, at least, "controversial", and I do think there are reasons for this.  His employer's dodgy deal with Microsoft is certainly a part of it, as is [his position on MS OOXML]("http://slashdot.org/comments.pl?sid=293507&cid=20547277").  There are plenty of people, including me, who don't entirely trust him, and it's de Icaza himself who has inspired our distrust.

Back to your comment:-

> These are all genuine quotes, easily found in this thread.

This by the way is all in the first 7 pages, the thread is now at page 42, but it's enough to get an idea of whether this is a debate or something else.

What you're doing is you're selectively finding the worst-looking quotes, taking them out of their original contexts, and putting them all together so as to paint your opponents as nothing but mud-slingers - yet, in doing that, that's exactly what you're resorting to yourself.  Indeed, you go on to say:-

> It looks to me more like a set of non-negotiable demands, accompanied by negative characterisations,  unpleasant insinuations and even accusations...aka ad hominem attack.  This is all clearly to be seen in the quotes above and more extensively in the thread as a whole, it's not a matter of my opinion. There's a lot of energy going into this and even abusive pm sent (I received a very nasty one complete with foul language, since dealt with by a moderator).

But, by taking the quotes out of their original contexts, and focussing just on those quotes, you ignore the real points being made, the substantial arguments being put forward, and so on.  You're cherry-picking from your opponents posts so as to paint your opponents in the worst possible light - *and so as to accuse your opponents of "negative characterisations,  unpleasant insinuations and even accusations...aka ad hominem attack"!*

I mean, let's look at this.  I posted [some analysis of Microsoft's "Patent Pledge"]("http://ubuntuforums.org/showpost.php?p=4413853&postcount=414") so as to enlighten smartboyathome, and others, as to the devious word-games that Microsoft plays.  [plun, in response to that]("http://ubuntuforums.org/showpost.php?p=4414300&postcount=415"), rather than deal with the substantial points I made in my comment, ignored almost all of it and, instead, chose to mischaracterise me and others as "a group of users which burn their time with MS hate".  And then, when you respond to his comment, you start by saying that you agree with him!  *And now you're criticising your opponents for "negative characterisations,  unpleasant insinuations and even accusations...aka ad hominem attack"?*

You may well be right that some of the labels thrown about have been unhelpful and unwarranted.  But raising such criticism *in order to mischaracterise your own opponents* simply makes you as bad as you're making your own opponents out to be.

---

### Post by plun on 2008-02-27
> **julian67 said:**
> 
I use mono and do not object to it.  I *do* object to this leading me to being labelled (with others) as a mono/MS/Novell fanboy/lover/apologist which are terms expressing  derision, animosity, and ridicule.  Doing this also makes the protagonists (in my eyes) less and less credible as any reasonable points or facts they *might* use to support their view become obscured and ultimately discredited.

Well, perhaps there is a risk with Novell/MS but its up on another level.

The key issue is good open source software that can be used without any hazzle for everyone, from newbie to experienced user.

I cannot see any reason for a user to choose Windooze now(except gaming) and its just to go on with this work including to work also with the Novell folk. They also love open source and free software.

Just tragic when some Linux users makes a internal Linux war about this, it just hurts Linux and makes MS stronger...

---

### Post by julian67 on 2008-02-27
All those comments/quotes are real and found in the 1st 7 pages of the thread. Easily found either with the thread search facility, or more conveniently with google (no time limit on repeat searches). The pm I received contains the charming line "and dont bother contacting me ill just delete because I dont want to be contaminated by anything that spews from your mouth ever again." (despite the fact that I had not contacted the author, nor did I reply to him).  Like I said before I don't think this is a debate, but in fact a set of non-negotiable demands accompanied by emotional outbursts, personal attacks, unjustified characterisations of everyone who doesn't agree with the protagonists, strawman and ad hominem assertions and so on. And anyway the question of mono's inclusion and status isn't decided at ubuntuforums so the demands are in fact futile as they are not addressed to anyone who could act on them if action was actually merited.

---

### Post by mangar on 2008-02-27
[https://wiki.ubuntu.com/No-Mono-by-Default](https://wiki.ubuntu.com/No-Mono-by-Default)
(wasn't started by me, and I haven't changed anything there).

I think that enumerating reasons pro/against in an orderly fashion will generate better result than arguing and calling each other names.

Have fun, play nice. *fake mature adult voice*

---

### Post by julian67 on 2008-02-27
I have actually learned a lot in this thread but for reasons outlined above i feel it's become futile (if it wasn't always so) so I'm out.

---

### Post by Simon G Best on 2008-02-27
> **julian67 said:**
> All those comments/quotes are real and found in the 1st 7 pages of the thread.

And you cherry-picked them to paint your opponents in the worst light possible.

Just suppose, just hypothetically, that I was to follow your example and cherry-pick quotes from your posts.  The results might be something like the following.

> **julian67 said:**
> If people have non-rational reasons for disliking/hating something that's up to them,

"non-rational"?  "hating"?  That's how you describe your opponents?

> **julian67 said:**
> If people have an emotional reaction to it that is purely a personal issue for them.

"emotional"?  "a personal issue"?  That's how you characterise those you disagree with?

> **julian67 said:**
> that's the closest they get to being rational! seems cruel to point it out :)

Again, you seem to want to paint your opponents as lacking rationality.

> **julian67 said:**
> The inclusion of Mono is worth discussing but not on a religious basis.

Ah, now it's religion.  You opponents are irrational and acting on "a religious basis."  That's how you portray your opponents.

> **julian67 said:**
> Anyone have an argument based on something actually related to reality (i.e. commonly accepted to exist outside of your own mind/feelings/fears/aversions/prejudices)?

Another example of painting your opponents as irrational.

> **julian67 said:**
> Is there anything beyond an emotional respose here?

Oh, now you're painting your opponents as being merely "emotional".  Irrational, religious, emotional...

Let's lump it altogether, a bit like you did, and see how it looks:-

[LIST]
[*]"If people have non-rational reasons for disliking/hating something that's up to them,"
[*]"If people have an emotional reaction to it that is purely a personal issue for them."
[*]"that's the closest they get to being rational! seems cruel to point it out :)"
[*]"The inclusion of Mono is worth discussing but not on a religious basis."
[*]"Anyone have an argument based on something actually related to reality (i.e. commonly accepted to exist outside of your own mind/feelings/fears/aversions/prejudices)?"
[*]"Is there anything beyond an emotional respose here?"
[/LIST]

See?  By selectively quoting you - just as you've done to your opponents - I can make it look like you just keep on making ad hominem attacks, repeatedly painting your opponents as irrational, emotional, religious.  Of course, there's a lot more to your posts than those few, misrepresentative examples.  And, as you must know from cherry-picking quotes yourself, there was a lot more to the posts you quoted from, too.  A lot more.  And yet you cherry-picked those quotes to make your opponents look as bad as possible.

---

### Post by PmDematagoda on 2008-02-27
This thread seems to have run it's course from the posts I am seeing now, so to prevent another ugly scene this thread is locked, perhaps permanently.

---

