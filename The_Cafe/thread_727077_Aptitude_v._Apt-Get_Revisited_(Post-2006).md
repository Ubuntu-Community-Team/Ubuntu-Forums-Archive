---
title: "Aptitude v. Apt-Get Revisited (Post-2006)"
date: 2008-03-17
forum: The Cafe
---

### Post by Arthur Archnix on 2008-03-17
> **aysiu said:**
> In my experience, uninstalling applications in Ubuntu does not bork the system. If there are related programs I accidentally uninstall, I can usually just reinstall them with no harm done. The removal process does not taken program settings with it. Frankly, I haven't had this problem since I stopped using *aptitude*.

At the risk of going OT, you're hardly the first to imply bad things about aptitude, but I've never seen any hard data to back it up.

The official debian user guide says that aptitude is now the preferred method of adding and removing programs. Is ubuntu going in this direction or not?

---

### Post by aysiu on 2008-03-17
> **Arthur Archnix said:**
> At the risk of going OT, you're hardly the first to imply bad things about aptitude, but I've never seen any hard data to back it up. Well, I actually used to be quite an advocate of *aptitude* before Edgy Eft added *autoremove* to *apt-get*, but I saw too many cases where *aptitude* tried to remove too many packages the user didn't want removed. Here are some cases I was able to dig up, but I've seen more than that:
[http://ubuntuforums.org/showthread.php?t=108814](http://ubuntuforums.org/showthread.php?t=108814)
[http://ubuntuforums.org/showthread.php?t=291928](http://ubuntuforums.org/showthread.php?t=291928)
[http://ubuntuforums.org/archive/index.php/t-228684.html](http://ubuntuforums.org/archive/index.php/t-228684.html)

---

### Post by Arthur Archnix on 2008-03-17
For non-experts like myself the differences between them are confusing, with some saying use apt-get, and others saying use aptitude. Information on the net also varies.

For my part, your links are two years old, so I am sketical. Also, there is [this]("http://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html#s-aptitude"):
>  Note that aptitude is the preferred program for package management from console both for package installations and package or system upgrades.
and [this]("http://www.debian.org/doc/manuals/debian-reference/ch-package.en.html"):
> aptitude is now the preferred text front end for APT, the Advanced Package Tool.  It remembers which packages you deliberately installed and which packages were pulled in through dependencies; the latter packages are automatically de-installed by aptitude when they are no longer needed by any deliberately installed packages.  It has advanced package-filtering features but these can be difficult to configure.
and lastly, [this]("https://help.ubuntu.com/community/AptGetHowto"):
> aptitude - Curses viewer of packages installed or available. Aptitude can be used from the command-line in a similar way to apt-get, but only for some commands - install and remove being the most common. However, because aptitude keeps track of more information than apt-get does, it can be considered better at install and remove operations.

I don't pretend to know much about the differences, or which is better. But I see many people who I presume to know a great deal, like yourself, who say use apt, and then I see links like these that make me wonder what's going on.

---

### Post by greymongrey on 2008-03-17
aptitude seems to be more for debian proper, at least it seems that way to me. I use sidux and their devs say never use aptitude with it but always use apt-get. I don't think you can go wrong with apt-get.

---

### Post by aysiu on 2008-03-17
You're right that those threads are kind of old, but then again I and others have been telling people for a while not to use *aptitude*, so the likelihood of the threads appearing again recently is low (after all, if all instructions say to use *apt-get*, why would you use anything else?).

That said, it's very possible that *aptitude* has been improved upon recently and no longer has this problem of being "too smart" and removing a whole bunch of packages you don't want removed.

I haven't seen any downside to using *apt-get*, so I will just say to use *aptitude* at your own risk. *aptitude* may or may not work well now, but I know *apt-get* does, and I will continue to recommend it.

---

### Post by Arthur Archnix on 2008-03-17
Well, I think I ought to use whatever the Ubuntu dev's use. And I think that that's apt-get. In any event,  here are a few useful threads that are relevant to my interests...all should be taken with a grain of salt.

[Blog post]("http://pthree.org/2007/08/12/aptitude-vs-apt-get/") about aptitude versus apt-get by[ Aaron Toponce]("https://launchpad.net/%7Eatoponce")

[Debian Forum Poll]("http://forums.debian.net/viewtopic.php?t=24920&postdays=0&postorder=asc&vote=viewresult") about which package manager is used, though you have to add synaptic users to the apt-get pile since according to information here, [synaptic calls apt-get]("http://forums.debian.net/viewtopic.php?t=24135&highlight=aptitude+aptget").

Finally, the [apt manual]("http://www.debian.org/doc/manuals/apt-howto/"), and the [aptitude]("http://algebraicthunk.net/%7Edburrows/projects/aptitude/doc/en/pr01.html") user manuals.

Until such time as this gets straightened out by the devs, I think I'll adopt your approach aysiu and use apt: it has a long history of use and is pretty much a known quantity.

Oh and thanks for moving this to its own thread.

---

### Post by capink on 2008-03-17
As aysiu pointed out aptitude sometimes removes packages that you do not want to remove. This behaviour can be turned off by typing the command:

```
sudo aptitude keep-all
```

But then, that would beat the main advantage of using aptitude, which is the ability to remove packages installed to satisfy dependencies when they are no longer needed. apt-get autoremove is not as effecient IMHO, it just don't remove all these packages.

And then comes the argument of not needing to remove cruft packages because they do not do any harm and because disk space is cheap now. For most users this argument is valid and that is why it is recommeded for beginners to use apt-get instead of aptitude because it is safer.

But I need to keep my system as small as it can get. And aptitude gives me total control over what packages are installed in my system.

---

### Post by blithen on 2008-03-17
Hmm. I aways thought apt-get was just a gui version of aptitude. Guess not. Though The only time I have used aptitude was to quicky search for an obscure package. I have used it to autoremove some stuff. And it removed a TON of stuff I  never wanted to remove. Needless to say it ended up me re-installing(Yay for a home parition!) And I have never used it to install/remove anything.

---

### Post by regomodo on 2008-03-17
> **blithen said:**
> Hmm. I aways thought apt-get was just a gui version of aptitude.

? A gui of aptitude? Are you thinking of synaptic and apt

---

### Post by bruce89 on 2008-03-17
> **regomodo said:**
> ? A gui of aptitude? Are you thinking of synaptic and apt

Apt is a frontend to dpkg. Aptitude is a frontend to apt.

As long as you disable "automatically install recommended packages", aptitude's great.

---

### Post by Arthur Archnix on 2008-03-17
> **bruce89 said:**
> Apt is a frontend to dpkg. Aptitude is a frontend to apt.

As long as you disable "automatically install recommended packages", aptitude's great.

I don't know how technically accurate that is. It appears in wikipedia, but the aptitude manual says "**aptitude** is a featureful package manager for Debian GNU/Linux       systems, based on the renowned apt package management       infrastructure.  **aptitude** provides the functionality of       **dselect** and **apt-get**, as well as many additional features not       found in either program." That says to me that they are different programs that do the same job, differently. By way of analogy, Ubuntu is not a front-end to debian, even though its based on it.

Here's an interesting [thread]("http://linux.derkeiler.com/Mailing-Lists/Debian/2007-11/msg00090.html") from the author of aptitude, who says he worries that the idea that aptitude removes too much is gaining the status of urban legend.

Here's a newbie doc on [how to use aptitude]("http://newbiedoc.berlios.de/wiki/Aptitude_-_using_together_with_Synaptic_and_Apt-get"), as well as a bunch of other interesting and useful information.

If I were to draw any conclusions from my brief foray into the subject, I would hazard a guess that aptitude is a perfectly good package manager, and if you have the time and are inclined to do so you should learn about it and feel quite good about using it.

I also think that if you want to use it you SHOULD take the time to read about it and learn how to, since it is not simply calling apt-get in the background, nor does it behave exactly the same way.

And of course, you should not feel any pressing need to learn how to use it and start using it. Apt will continue to do fine job for you, and for me, since it's what I'll be using.

/my two cents. 
//please correct me if I'm mistaken on any point.

---

### Post by bruce89 on 2008-03-17
> **Arthur Archnix said:**
> Here's an interesting [thread]("http://linux.derkeiler.com/Mailing-Lists/Debian/2007-11/msg00090.html") from the author of aptitude, who bemoans the fact that aptitude removing too much is gaining the status of urban legend.

So it appears that you should either only use apt, or only aptitude. Seems fair enough.

Anyway, I usually use the *aptitude* GUI, not the command line way (just execute *aptitude* with no arguments), so I know what it's going to do (and change it if it's wonky).

---

### Post by jken146 on 2008-03-17
I use aptitude exclusively, and have never had any problems with it.

---

### Post by aysiu on 2008-03-17
Calling it an urban legend is an unfounded accusation. I have seen with my own eyes (on both my installation and others' who have posted on these forums) *aptitude* being overzealous about removing packages and not necessarily warning you of it beforehand.

Now if the author of *aptitude* wants to explain exactly how and when *aptitude* has been improved to avoid these problems, then I'd be perfectly willing to give it another chance, but to simply call it an urban legend is just turning a blind eye to a real problem.

I'm not going to go out of my way to bad-mouth *aptitude*, but if people ask about it, I will tell it like it is, and I will continue to recommend *apt-get* because I know it works.

---

### Post by Arthur Archnix on 2008-03-17
Well, perhaps I'll quote a larger section of the relevant passage so that I don't accidentally cause a misundertanding between aysiu and the author of aptitude :twisted:


>  **One dude says:** this bothers me, since I mostly use aptitude. When I need a build-dep or source, I'm concerned that later aptitude may wipe something inadvertantly. Do you know if there are plans to implement these commands into aptitude? Or will apt-get always remain, so that its not a problem?

**Aptitude Author says**: aptitude shouldn't wipe out packages installed with apt-get, period full stop.

**Some guy:** you know, that wasn't fair of me. I was once concerned about that problem, but have subsequently learned that it really doesn't happen. So i apologise if that came across wrong.

**Author:** No, I just come down hard on this meme because it seems to have taken on a life of its own and I'd like to squash it before it grows up into a full-blown urban legend.I've not read anything that would lead me to believe that he denies it's behaved badly in the past. My only point is that, given the rather slow development cycle of Debian, the fact that is has attained the status of "preferred method" speaks pretty highly to the fact that your previous experiences with it may have been addressed.

That being said, I agree that apt-get just works, and that no one should feel they need to start using aptitude. To return to my original comment, I just wish an ubuntu dev would weigh in on the issue on a community wiki page explaining what they use, why, and how to swtich correctly if you're going to. Maybe I'll head over to the ubuntu idea bank, or idea storm and submit that myself. :)

---

### Post by aysiu on 2008-03-17
Well, as I said before, I don't go out of my way to bad-mouth *aptitude*. I'm not on a crusade against it.

However, the *urban legend* label is misused, even with that context.

The problem either used to exist and still does.

Or it used to exist and no longer does because they fixed something.

If they didn't fix something, it still is a problem, not an urban legend.

Either way, it's up to the developers to say they've fixed a problem. If they don't prove they've fixed it, and I already have another solution (*apt-get*) that works all the time, then I don't see the need to advocate for *aptitude* or do extensive testing to see whether the problem still exists or not.

---

### Post by bapoumba on 2008-03-17
Things would get better if apt-get (relying on dpkg's log to know what is installed etc..) and aptitude (using its own log) would share a common file to log actions. Problems come up when using one and the other alternatively.
I use aptitude only, but usually recommend apt-get if I want a terminal output because new members mainly use synaptic.

---

### Post by qazwsx on 2008-03-17
APT gives decision more power for user (Is it good or  bad? It depends).
APTITUDE is not very good tool for Debian Sid (like sidux). 
APT is more reliable.
APTITUDE may be faster tool to get your work done.
You can't use APTITUDE without APT.

---

### Post by capink on 2008-03-17
> **qazwsx said:**
> 
You can't use APTITUDE without APT.

Contrary to common belief apt is not apt-get. apt-get is a frontend of apt just like aptitude. To paraphrase:

You can't use APT-GET without APT
You can't use APTITUDE without APT

as both are just frontends for apt. apt-get come as the default frontend included in the same package, but it is not apt.

Also a lot of people think of the awful ncurses GUI when they think about aptitude. But aptitude can be used from the terminal as  command, and that is where it really shines.

---

### Post by bruce89 on 2008-03-17
> **capink said:**
> Also a lot of people think of the awful ncurses GUI when they think about aptitude.

At least it's obvious what it is going to do with its GUI compared to the command way.

I like the interface by the way.

---

### Post by unutbu on 2008-03-17
You know how programs like GIMP, Wesnoth and Google Earth have a hint dialogue box pop up at start up? Wouldn't it be nice if Ubuntu had one for new users? In particular, it would be nice to warn new users that they should choose to either use apt-get/synaptic or aptitude but not both.

(Yes, I know if I want it I'm welcome to program it, and it probably would not be that hard. I could steal most of the code from a GTK demo. It'd just be a text field with a close, next, previous and never show me again button. And it could read a text file filled with hints... And I could start a thread requesting submissions for hints... Yeah... cool... hmmm... Hey, did someone already think of this?)

---

### Post by bruce89 on 2008-03-17
> **unutbu said:**
> You know how programs like GIMP, Wesnoth and Google Earth have a hint dialogue box pop up at start up? Wouldn't it be nice if Ubuntu had one for new users? In particular, it would be nice to warn new users that they should choose to either use apt-get/synaptic or aptitude but not both.

I've always hated "tip of the day" dialogues, I'd rather have a usable program than a messy one with hints.

---

### Post by ubuntu-freak on 2008-03-18
> **bruce89 said:**
> So it appears that you should either only use apt, or only aptitude. Seems fair enough.

 
Yes, and that's why I object to new users being given "sudo aptitude install/remove" commands.
 
Nathan

---

### Post by forrestcupp on 2008-03-18
> **bruce89 said:**
> 
Anyway, I usually use the *aptitude* GUI, not the command line way (just execute *aptitude* with no arguments), so I know what it's going to do (and change it if it's wonky).
I think the ncurses interface for aptitude is horrid.  It's ugly and inefficient.  Things like Synaptic are much better.

> **aysiu said:**
> Calling it an urban legend is an unfounded accusation. I have seen with my own eyes (on both my installation and others' who have posted on these forums) *aptitude* being overzealous about removing packages and not necessarily warning you of it beforehand.
aysiu used to be one of the biggest proponents of aptitude on these forums.  When someone changes stance in such an exaggerated way, there's a reason for it.  It's unwise to dismiss that kind of experience.

> **reassuringlyoffensive said:**
> Yes, and that's why I object to new users being given "sudo aptitude install/remove" commands.
 
+1

---

### Post by greymongrey on 2008-03-22
I was playing around with Debian testing this past week and I decided to use only aptitude. In short order I had problems. Maybe I was the problem because I never had used it before. I wiped out testing and re-installed and then used apt-get and I never had any problems. To me, it seems apt-get is more stable and more usable. I know I use it in sidux all the time (rather than any helper scripts because I like to see what is going on) and I never have any problems.

I say use what works for you, however.

---

