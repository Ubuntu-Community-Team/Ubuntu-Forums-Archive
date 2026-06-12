---
title: "Considering Ubuntu software development"
date: 2012-08-07
forum: Testimonials &amp; Experiences
---

### Post by noname222 on 2012-08-07
Hi, I am the owner of a software company in the gaming space.  We are considering branching out into Ubuntu.

When I first saw Windows 8, I knew Microsoft was heading in a bad direction, and everything I've heard since then from them has been worse.  I do not like my work being relegated to "legacy app" status.  The fact they could think it was a good idea to risk the Windows development ecosystem to chase after smart phone trends...if they're that incredibly dense, I don't feel comfortable depending on them in the future.  In that context, an open-source OS not tied to one company's stupid decisions seems very appealing, if it works right.

An operating system is a platform for developing and using applications.  Your primary customers, in my opinion, are application developers.  If you have a good development environment, you will get good applications, and your consumer base comes from that.  Nobody uses Windows because they care about the underlying architecture.  They use it to run applications that won't run elsewhere.

I tried Ubuntu (the latest 12.04) for the first time in about three years yesterday.  Since I am comfortable with OSX, it all felt very familiar.  The file explorer was pleasant to use, which is one of the most important aspects.  However, I already noticed two UI glitches at a very basic level.

First, when I hover the mouse over the text on a file in the file explorer, when in "compact" view mode, the hover effect does not occur until I am at the base line of the text, like this: ______.  If I hover over the bottom of a letter that extends below that line, the cursor is not considered hovered.  (i.e. the letters g, p, q, etc.).  It's hard to explain, but I found it very annoying.

Second, when you drag a window to the top and maximize it, it's easy to quickly move the mouse back down and an offset from the place where you grabbed the window occurs.  I have programmed many UI elements and these are simple basic bugs I would never let ship in a commercial product.

I find it bothersome that Ubuntu includes features like "Ubuntu One" (which I would never use in a million years), and puts effort into a new interface (Unity), when they have simple problems at the most basic level.  This indicates to me their priorities are wrong, and that they may be more interested in chasing consumer trends than in creating a stable and usable OS.

I hope the Ubuntu team will focus more on basics like driver support and the file system, and not get caught up in consumer trends.  The progression of development goes like this:

Operating system (file system, drivers) -> Development tools (Visual Studio, Xcode) -> Applications -> Consumers

Aesthetics are also very important.  An OS is a visual interface, and if the interface is repulsive, it does affect the user.  Your interface is not visually pleasing.  This is not a superficial complaint, because the look and feel of the OS interface affects every application that runs within it.  In all honestly, I could design something that looked better, and I'm a programmer with no artistic skill.

It's my hope that maybe Ubuntu will become a solid and usable development environment.  I had a great experience with Windows XP, but Microsoft has gone mad, and I don't think something as basic and low-level as an OS should be a commercial product tied to any single company.

There's an awful lot of resentment built up against Microsoft, and both consumers and developers are largely terrified of their new "vision".  People are looking for an alternative, and that starts by providing developers with a solid foundation to build on.

Thanks.

---

### Post by Merk42 on 2012-08-07
Welcome, though this seems more like a testimonial.

> **noname222 said:**
> First, when I hover the mouse over the text on a file in the file explorer, when in "compact" view mode, the hover effect does not occur until I am at the base line of the text, like this: ______.  If I hover over the bottom of a letter that extends below that line, the cursor is not considered hovered.  (i.e. the letters g, p, q, etc.).  It's hard to explain, but I found it very annoying.
Canonical (who make Ubuntu) don't make the file explorer Nautilus. GNOME does. I wasn't able to reproduce the issue you have, but you can file a bug about it [here](https://bugzilla.gnome.org/browse.cgi?product=nautilus)

> **noname222 said:**
> Second, when you drag a window to the top and maximize it, it's easy to quickly move the mouse back down and an offset from the place where you grabbed the window occurs.  I have programmed many UI elements and these are simple basic bugs I would never let ship in a commercial product.Unity, however, **is** made by Canonical, so you can file that [here](https://bugs.launchpad.net/unity)
> **noname222 said:**
> I find it bothersome that Ubuntu includes features like "Ubuntu One" (which I would never use in a million years), and puts effort into a new interface (Unity), when they have simple problems at the most basic level.  This indicates to me their priorities are wrong, and that they may be more interested in chasing consumer trends than in creating a stable and usable OS.Again, putting the blame on the wrong people. Drivers are either put into the Linux Kernel or made by the device manufacturers themselves. What device(s) were you having trouble with?

> **noname222 said:**
> 
Aesthetics are also very important.  An OS is a visual interface, and if the interface is repulsive, it does affect the user.  Your interface is not visually pleasing.  This is not a superficial complaint, because the look and feel of the OS interface affects every application that runs within it.  In all honestly, I could design something that looked better, and I'm a programmer with no artistic skill.What specifically do you not like? As it is, your comment isn't very helpful and is arguably insulting.

---

### Post by noname222 on 2012-08-07
> **Merk42 said:**
> Welcome, though this seems more like a testimonial.
I don't follow.  What product am I endorsing?

> Canonical (who make Ubuntu) don't make the file explorer Nautilus. GNOME does. I wasn't able to reproduce the issue you have, but you can file a bug about it [here](https://bugzilla.gnome.org/browse.cgi?product=nautilus)
It doesn't matter.  If it's in the Ubuntu's distribution, it's Ubuntu's problem.  If they are relying on a third party that is putting out buggy software, they should stop relying on that party.  The file explorer is one of the most basic aspects of an OS.  I would never outsource such a fundamental component in any software I make.  It's not like a file explorer is hard to write, anyways.

> Unity, however, **is** made by Canonical, so you can file that [here](https://bugs.launchpad.net/unity)
Again, putting the blame on the wrong people. Drivers are either put into the Linux Kernel or made by the device manufacturers themselves. What device(s) were you having trouble with?
My general perception is that graphics, sound, and network drivers have problems with all Linux distributions.  I have not done any in-depth testing to investigate this.

> What specifically do you not like? As it is, your comment isn't very helpful and is arguably insulting.
-Having a text menu that partially obscures the text title, in the main menu bar...that's just awful.
-The close / minimize / maximize buttons are ugly.  They are okay in grayscale, but when colorized orange, they look like something from the 1990s.
-Orange is offensive, at least the way they have it implemented here.  There should be a setting to change the accent color at least.
-Window shadows should be lighter and spread over a larger area.  OSX goes to an extreme with this, but right now they are too dark and focused.  It just makes things look blurry.
-Many icons are blurry.  Antialiasing should only be one pixel thick.  Any more than that, and it becomes blurry.

I'm actually a big fan of dark UI themes, which Ubuntu partially does with the windows and menu bar.  They are easier on the eyes when doing artwork.  Here's an example of a dark theme done right:
[img]http://upload.wikimedia.org/wikipedia/en/1/1a/3dsmax_2010_800px.png[/img]

Toolbars do not have any clear division.  In the image below, it isn't clear which button the "undo" text belongs with.  This is awful:
[img]http://www.iloveubuntu.net/sites/default/files/field/image/gedit_dashboard_%2012.04%201.png[/img]

Again, I don't care who this program is made by.  If it ships with Ubuntu, it's Ubuntu's problem.  With a dark theme like this, I suggest using grayscale toolbar buttons.  They look great in 3ds max, and it cuts down your artwork cost because it's easier to produce aesthetically pleasing icons.  If the author of this program can't fix it, write your own text editor.  If that means you ship with a more basic text editor with fewer features, that's fine.  Just make sure everything you have implemented is done really really well.  Windows Notepad looks far better than this text editor, because it knows its own scope of features and sticks to what it can do well.

The window bar / toolbar division also needs more contrast.  Next to the white background below it, the difference between the two is lost and it just looks like one solid mass of gray.  When you have a light area next to a dark area, the dark area always loses definition.

Windows corners appear round but are not antialiased.  If you can't do proper alpha blending, you shouldn't use round corners.

If you put more effort into the appearance of the UI, it wouldn't be that hard to produce something that would blow away Windows and OSX.  Ballmer's insistence that every background be white is one of the big problems I have with post-XP Windows.  An attractive dark theme (even partially, as Ubuntu does it now) would appeal to programmers, artists, and gamers.    The UI is very important to me, because that's what I look at all day.


The most important thing I have learned in software development is to limit the number of things you attempt, but make any feature you officially support really really good.  The worst thing you can do is try to support everything under the sun, and do a lousy job of it all.  Once you define a limited scope of what you're going to do, then all your effort goes into doing that right, and you get a high-quality product.  If you don't limit the scope of what you're attempting, your effort goes in random directions and you end up with a result that doesn't make anyone happy.

So ask yourself, where is the biggest market segment that I can potentially make happy?  (Gamers, developers.)  What do they value?  Then you weigh all features against this customer you are trying to please and drop efforts that don't directly correlate.

---

### Post by coffeecat on 2012-08-07
[quote="noname222"]Your interface is not visually pleasing.[/quote]

[quote="noname222"]write your own text editor. If that means you ship with a more basic text editor with fewer features, that's fine. Just make sure everything you have implemented is done really really well.

If you put more effort into the appearance of the UI[/quote]

Please read [the sticky]("http://ubuntuforums.org/showthread.php?t=1921679").  

> The forum membership, staff included, are volunteers. Most are ordinary users. This is not the place to address concerns to Canonical, the Ubuntu design team or the developers, nor is it the place for bug reports.

[quote="noname222"]I don't follow. What product am I endorsing?[/quote]

A member of staff moved your post to "Testimonials and Experience" because this is the most appropriate place for what is not a support question.

> **Ubuntu Testimonials & Experiences **Here is your opportunity to tell other forum members about your experience of Ubuntu. 

---

### Post by Simian Man on 2012-08-07
The Linux eco-system is very different from that of Windows or Apple.  It's totally decentralized with each project being developed and maintained by different people.  Linux distributions are so called because for the most part they are just distributing the work of others.  There are downsides to this as there is much less ownership of problems and less cohesiveness overall.  But there are upsides such as the ability to replace major parts of your system.  For example, I would never use the default Unity desktop because I agree that it is ugly and buggy.

If you're looking for a system that is integrated, cohesive and predictable, Linux is probably not for you.

---

### Post by Kalanac on 2012-08-07
Linux distro's don't work like that :)  You don't have "here is your linux distro, you are stuck with these things...FOR ETERNITY!"

Linux is highly customizable and a distro is just one collection of hundreds of possibilities.  Just find a distro that closely matches what you want then tweak it accordingly.  We're a very eclectic bunch, possibly one of the reasons it's difficult to make us mainstream, but hey, we like it like that.

Your points on the UI are opinions, I like the orange, I dare say there are others who do and lots of people who don't.  Thankfully we can change the stuff we don't like.

As a game developer thinking of working with Linux, you need to concentrate more on stuff like languages and libraries than distros.  As I mentioned, distros are very varied to begin with and then generally customized further by the user so finding two linux set ups that are entirely alike would be like finding identical snowflakes :)

Your point on drivers is one which is largely out of open source hands and the responsibility of the hardware vendors.  There are open source driver projects, but they need to reverse engineer the closed source drivers and work from a narrow starting point.  Saying that, the teams that are out there do amazing work, especially when they do it for free.  Some vendors work well with Linux (like Intel and nVidia) so support is MUCH better.

In general I've had very few driver problems which couldn't be solved with a bit of elbow grease.

Linux isn't quite ready to replace things like Windows for your average user just yet, but this is mostly because of third parties.  Projects like Ubuntu are a MASSIVE step forward in making Linux more accessible to less tech savvy users, but until third parties begin to think of Linux support as more than an afterthought we're always going to be lagging behind a little in areas like media and gaming.

To compensate for that though, we have talented and passionate developers, an awesome and supportive community and freedom :)

---

### Post by QIII on 2012-08-07
Please do not take this as any attempt to invalidate your concerns because the community does understand them.

The Linux ecosystem is one of a la carte choices and you can even create your own totally unique dishes.  Canonical, like everyone else, includes what is available.  The "it's Ubuntu's problem" misunderstanding arises from a misunderstanding of the ecosystem.  All Linux distros mix and match initial default components they choose and all of those components have their inconsistencies and problems.   Users are not strictly bound to what is included and can install another component in the place of one that they do not prefer.  I doubt that among Linux users of any distro you would find any two who, after 6 months of use, have identical configurations.

Unity is just one Desktop Environment and it can be exchanged with any of a dozen others.

No distro has thousands of paid employees as does Microsoft.  They usually operate with a very small number of employees (some have none at all) and are otherwise community efforts.  And we aren't Canonical employees (unless one or two of them stops by from time to time.)

There is continuous improvement being made, of course.  But no distribution is perfect. 

Again, I am not poo-pooing your legitimate concerns.  But this is a completely different ecosystem than Microsoft and it is best to leave assumptions based on familiarity with that world behind to avoid frustration in this.

---

### Post by noname222 on 2012-08-07
I purposely said we are considering Ubuntu development, not Linux.  I would go as far as making the software check for Ubuntu, and quit if it's running on another Linux-based OS.  The reason for this is because we have a chance at making Ubuntu users happy, but there's no way we can ensure our software works well with and looks good on all Linux-based operating systems.  I think the Ubuntu team realizes this, and thus distances themselves from the name "Linux".

Dodging responsibility for components of the OS is nonsense.  Someone makes the final decision what goes into each distro, and that person is responsible for everything the distro contains.

Choice, in and of itself, is a bad thing.  It's a cost.  The only reason people ever want choice is because they are not happy with the current option, and they hope choice will lead to a good result.  So what they want is a good result, and choice is only a vehicle to arrive there.  Watch this to see why that is wrong.  No, really, please watch it, this was a revelation to me:
[http://www.youtube.com/watch?v=VO6XEQIsCoM](http://www.youtube.com/watch?v=VO6XEQIsCoM)

---

### Post by Kalanac on 2012-08-07
You really don't get us do you?  That's OK, we're pretty strange.  Just spend a while getting to know the Linux community at large and how we work.

I dare say most folks would be horrified by any software that shuts down just because you're not running the right distro.  

Choice is a great thing!  There will never be a universal utopia because everyone would argue about what colour the sky should be.  What is great for one person is horrid for another.  Assuming that there is one perfect choice for everyone is at best short sighted and at worst arrogant.

EDIT: Interesting video by the way :)  I get the paralysis point when it comes to picking a DVD to watch or something like that.

---

### Post by Simian Man on 2012-08-07
Choice is great for people when they are interested in the thing in question, but not when they just want to use it.  For people who just want to use computers, I agree that having the choice of dozens of window managers, file managers, panels, and so on is insanity.  But I and many others like to tinker with computers and this choice makes it fun.

There are other times where I hate choice.  Buying tires for example.  I don't care what kind of tires my car has, but there are probably tons of people who do.

If you make software that will bomb out if it detects a non-Ubuntu setup, you're going to really tick off Linux users.  Moreover, it won't really help you increase your software's reliability because distros don't matter that much.  Two different distros with the same desktop and the same version of glibc are more alike then two versions of Ubuntu, a few years apart, running different desktops.

If you want to develop for Linux, you'll have to adjust to the way things are done.  It's not too hard to make a package that runs the same independent of the distro and library versions being run.  Static linking for example makes it easier.

---

### Post by QIII on 2012-08-07
Writing software that only works on Ubuntu would set you on the fast track to failure in being adopted by the Ubuntu community.

That would surely be perceived as more representative of another ecology.

Understand that I do not indict Microsoft's products.  They can be frustrating, but are no more so than some Linux issues.  Business practices are another subject and I won't get in to that.

The point is that there is a Microsoft ecosystem and a Linux ecosystem (and Apple and BSD...).  They are distinct.  It is unfair to each to make assumptions that one should be like the other or that anything that applies to one should apply to another.

Although there are some things that are limited in scope because they have not been ported to another package management system (Kestrel HPC, which only works with .deb based systems last I cheked, comes to mind), in the Linux ecosystem, single OS specificity by design would be practically anathema.

---

### Post by Kalanac on 2012-08-07
Just a few points that have occurred to me after watching that video you linked:

He mentions their being some magical balance point when choice becomes too much choice.  It occurs to me that that point occurs when your knowledge of the other choices diminishes.  Knowledge of the other choices is limited by some factor or other.  In his example of the salad dressings, the limiting factor would be money as you'd have to buy (or maybe sample) every single one to know which was the best.  Your expectations would be calibrated against reality.  For my example of DVD's the limiting factor is time.  I wouldn't want to watch every single DVD just to be able to pick a single one :)

For open source software we have the benefit that most of it is free (as in beer) so we can trial several options and pick the one we like.  In proprietary software situations we get limited by cost and generally when you've paid for one you're unlikely to swap it out for another one for fear of wasting money.

Therefore we get a large number of choices, but the opportunity to try a large number of those choices without having to commit resources to them.


As to your point of only developing for Ubuntu:

That's not how it's done in Linux land.  When software uses certain libraries we call that a dependency.  Linux software isn't usually bundled with dependencies, we download and install them separately.  Package managers like aptitude check for these dependencies and download them when installing the primary package.

So let's say you make a game that uses the pygame library and the person who is installing your game doesn't have it.  Aptitude would make a note of this, ask the user if they're happy to install pygame then, assuming the user is fine with that, it downloads and installs pygame.  Pygame is a linux library and will work on any distro (assuming they meet the dependencies :)) but isn't necessarily included in every distro by default.  Even on distros that don't use package managers, it's still possible to download and install the dependency in the manner appropriate to that distro even if it is via tarball compilation.

---

### Post by noname222 on 2012-08-07
> Therefore we get a large number of choices, but the opportunity to **try a large number of those choices** without having to commit resources to them.
How is that not a cost?  It's a cost I am unwilling to pay.  I will not try any other Linux-based operating system besides Ubuntu, and will not try any other desktop besides the default one, because I cannot afford the time cost of doing so.

---

### Post by Kalanac on 2012-08-07
Then start liking orange :)

---

### Post by QIII on 2012-08-07
> **noname222 said:**
> How is that not a cost?  It's a cost I am unwilling to pay.  I will not try any other Linux-based operating system besides Ubuntu, and will not try any other desktop besides the default one, because I cannot afford the time cost of doing so.

That is a choice and it is yours to make.

---

### Post by Simian Man on 2012-08-07
> **noname222 said:**
> How is that not a cost?  It's a cost I am unwilling to pay.  I will not try any other Linux-based operating system besides Ubuntu, and will not try any other desktop besides the default one, because I cannot afford the time cost of doing so.

Then either get used to the default or don't use it.  What else do you expect?

You came to Linux because you didn't like the direction Windows is going.  The fact that Microsoft has full and total control over the platform is a bad thing when you don't like the decisions being made.  The reason that Linux doesn't have this problem is because the development process is decentralized and users are free to use the software they want.

It seems like you want to have your cake and eat it too.

---

### Post by juancarlospaco on 2012-08-07
Sir, everything you enumerated is configure-able on this platform without software patchs by an experienced user.

The Proprietary GUInterface you posted is Fugly for it what meant to be, but the Gedit GUInterface is just ok for what it meant to be, if you are using Gedit as an IDE for production work, you are doing it wrong.

Libre Drivers are very good, for Proprietary ones blame the Company that makes the Hardware.

Just a humble Game Developer.

---

### Post by Iowan on 2012-08-07
Ubuntu is based on Debian, and has a few subsets as well - Xu-, Lu-, Ku- buntu to name only a few. Mint is in there somewhere, too. I saw a mind-boggling map of the Linux tree once - don't remember where I saw it. You're free (as in freedom) to develop software that includes/excludes whatever distros/flavors you like. :)

---

### Post by arunb on 2012-08-08
orange looks good on Ubuntu, so does the maximise and minimise buttons on the window. I also like Unity better than Gnome. 

So far I haven't faced any problems with Unity (and also with Gnome).

thanks
a

---

### Post by Bigtime_Scrub on 2012-08-09
1. If you don't like your default theme then change it. It is not that hard. You can set it all emo black if you want. This is a nonissue. 

2. I've never had the issue you had with nautilus.

3. I haven't had any driver issues in years. Most things work out of the box and what is missing is easily added. What year are you in? 2001? Even if the proprietary driver for something is not available there are open source ones that work out of the box for most things. 

4. Blaming Ubuntu or really any other distro for upstream issues in nonsense. Take it up with the package maintainers upstream.

5. Choice is a good thing and what makes Linux strong. You can call Ubuntu anything you want and avoid the word Linux, but at the end of the day that is exactly what Ubuntu is, Linux. 

You have no idea what Linux users are like or the thought processes that go into everything. If you want to write stuff for Ubuntu and no one else that is fine, that's your choice but you will most likey not succeed in Linux land with that attitude though. 

Join the community and be welcome. If you expect everyone else to comform to some corporate desktop thinking hit the bricks.

---

### Post by mastablasta on 2012-08-09
> **noname222 said:**
> How is that not a cost? It's a cost I am unwilling to pay. I will not try any other Linux-based operating system besides Ubuntu, and will not try any other desktop besides the default one, because I cannot afford the time cost of doing so.
 
Huh?
 
Oh, because other desktops are so radically different? :confused:

---

### Post by 3rdalbum on 2012-08-10
> **noname222 said:**
> 

It's my hope that maybe Ubuntu will become a solid and usable development environment.  I had a great experience with Windows XP

Sorry, but if you think Windows XP gives users a "great experience" then I think you may be confusing what's "familiar" and what's "good".

Windows XP certainly doesn't give me a good experience. If it was up to me I'd purge it from the face of the earth - it's horrible. Really really horrible.

---

### Post by PaulInBHC on 2012-08-10
XP works fine for what I do. Big step up from Win98.

What to do when it is no longer supported?

---

### Post by Tamlynmac on 2012-08-10
In case no one's noticed, the OP hasn't posted/responded for 3 days. Perhaps, they accomplished that which they intended. 

It's obvious the OP either had a limited understanding of Linux and was under the impression that each distro was a stand alone entity like MS. With no link to Linux other than being a part of the community. Or?

What ever the OP's motive was, it appears they have stopped communicating.

---

### Post by rg4w on 2012-08-11
noname222, at the risk of annoying my fellow Ubuntu friends here I rather liked your post and agree at least in part with much of what you wrote.  I might word it differently, and I suspect that if worded differently a good may here might even agree with much of it.

What distinguishes your perspective from that of many of the posters here is that you're a developer who makes your money selling software.  As such, you need to keep a keen eye on return-on-investment, and you're not the first to question the value of porting an app to Linux given the wide range of system configs in the ecosystem.

Indeed, you're in good company: Valve is porting steam to Ubuntu.  Whether it runs on any other Linux distro doesn't seem a priority for them at this stage.  They recognize that Ubuntu has by far the largest percentage of end-users in the Linux world, and given the cost of trying to support every possible configuration they're focusing on this market leader to get started.

From the Valve blog:

> Why Ubuntu? There are a couple of reasons for that. First, we’re just starting development and working with a single distribution is critical when you are experimenting, as we are. It reduces the variability of the testing space and makes early iteration easier and faster. Secondly, Ubuntu is a popular distribution and has recognition with the general gaming and developer communities. This doesn’t mean that Ubuntu will be the only distribution we support. Based on the success of our efforts around Ubuntu, we will look at supporting other distributions in the future.[http://blogs.valvesoftware.com/linux/steamd-penguins/](http://blogs.valvesoftware.com/linux/steamd-penguins/)

As for the various UI nit-picks you noted, those who've been reading this forum for a while are familiar with many of them. You're not alone in suggesting that Ubuntu could benefit from making sure the must-haves (like basic hardware compatibility) are rock-solid before exploring UI nice-to-haves (like the global menu bar).

The focus on Ubuntu based on its leadership position becomes in some ways a bit of a self-fulfilling prophesy in the ways tipping points do, because of its unusual UI:  integrating with Unity sometimes requires apps to be modified specific for that DE in ways that otherwise work just fine on any other distro.

Global menu bar is one example:  if you use GTK or QT your menu bar will be automatically exported to the global menu bar, but if you use any other GUI toolkit, such as apparently Firefox, LibreOffice, and others use, the app will need to be modified to provide an experience consistent with what Ubuntu users have come to expect.

All that said, there are two factors that distinguish the Ubuntu process from that of Microsoft and Apple:

1. Most Win and Mac users got their OS when they got their computer, and most Ubuntu users install it on a system designed for something else.  This is changing as more OEMs come on board, but it's a long, slow process, and in the meantime we have to accept that there will always be some hardware issues on some computers since the system isn't designed to run Ubuntu.  In fact, when we consider how few people got Ubuntu preinstalled, it's rather amazing that it works as well as it does.

2. Microsoft and Apple fund the entire OS R&D through sales revenue, while Ubuntu is given away for free.   This is not a bug, it's a feature, but it may be counter-intuitive for those accustomed to proprietary OSes:  Ubuntu is one layer on top of a very tall stack of other people's software, from the kernel to Debian and much more.  By not having to write absolutely everything from scratch, it takes only a multimillionare to make a world-class OS like Ubuntu. ;)  But it also means a much larger ecosystem than any single distro could garner alone, since every distro serves a useful role for someone.  And at the core, GUI stuff and a few other components aside, for the most part Linux is Linux - if you know the directory structure and the basic logic of the OS, that knowledge is directly transferrable to any Linux distro.

Ubuntu is only as strong as the larger Linux community it depends on, and thankfully that community is a tremendous powerhouse.  So while Linux is diverse in ways that some might call "fragmented", that diversity is also its strength.

It's maddening to get used to when coming from the world of single-owner OSes, but as you spend more time with the community the value of this will become ever clearer.  From time to time it seems a bit of a hodge-podge, but ultimately it's coming together remarkably well given the various parties involved in making it happen.

---

### Post by noname222 on 2012-08-11
> In case no one's noticed, the OP hasn't posted/responded for 3 days. Perhaps, they accomplished that which they intended. 
Sorry, but no one here is in a decision-making capacity, so it's useless to argue about the development approach of Ubuntu.  I feel that the Ubuntu team should continue distancing themselves from Linux and take more responsibility not to include low-quality applications with their distro, but until the Ubuntu team makes that decision, I would expect their fan base to insist that everything is flawless.

What gets referred to as "freedom" by a lot of people here seems like a failure to take responsibility, and reluctance to stick to any decision.  In software development, you have to make hard decisions about who you are and what you care most about, and then let those values guide the engineering process.  If you fail to make those decisions, you end up with, well, what Linux is today: Trying to be all things to all people, and failing at everything.  Frankly, Linux is still struggling to be as good as Windows 98 by many measures.  Before you get mad at that statement, let me point out that if you can't take criticism you shouldn't be developing software.

Still, there is potential there, and programmers I talk to are intrigued by the idea of Ubuntu-based software.  I'll keep playing with it and see what we come up with.

> It's maddening to get used to when coming from the world of single-owner OSes, but as you spend more time with the community the value of this will become ever clearer. From time to time it seems a bit of a hodge-podge, but ultimately it's coming together remarkably well given the various parties involved in making it happen.
Thanks for the feedback.

---

### Post by Petro Dawg on 2012-08-11
> **noname222 said:**
> Sorry, but no one here is in a decision-making capacity, so it's useless to argue about the development approach of Ubuntu.  I feel that the Ubuntu team should continue distancing themselves from Linux and take more responsibility not to include low-quality applications with their distro, but until the Ubuntu team makes that decision, I would expect their fan base to insist that everything is flawless.

What gets referred to as "freedom" by a lot of people here seems like a failure to take responsibility, and reluctance to stick to any decision.  In software development, you have to make hard decisions about who you are and what you care most about, and then let those values guide the engineering process.  If you fail to make those decisions, you end up with, well, what Linux is today: Trying to be all things to all people, and failing at everything.  Frankly, Linux is still struggling to be as good as Windows 98 by many measures.  Before you get mad at that statement, let me point out that if you can't take criticism you shouldn't be developing software.

Still, there is potential there, and programmers I talk to are intrigued by the idea of Ubuntu-based software.  I'll keep playing with it and see what we come up with.


Thanks for the feedback.
I don't understand; if you are a software developer who has issues with the the Ubuntu development team, then why not arrange a meeting with those who in charge of making the decisions in which you seem to have taken issue? 

Complaining to the community/user base isn't going to get anyone anywhere.  Are you just trying to get turn people away from Ubuntu?  Or are you trying to get the community to force development in the way that is most profitable for you?  

If you are looking to maximize profit, then Ubuntu/Linux is probably not for you; as most of it's users tend to admire people contributing their ideas freely for the good of the community, above the good of their own pocket book.

---

### Post by overdrank on 2012-08-11
Thanks for sharing. thread closed

---

