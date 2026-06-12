---
title: "Idea for Desktop Environment"
date: 2007-12-13
forum: The Cafe
---

### Post by Achetar on 2007-12-13
OK, below is my idea for a new Desktop Environment (it is in a quote box for no real reason). I would appreciate feedback, constructive critisism (as in not things like 'we don't need another DE we have KDE/GNOME/Xfce4', more along the lines of: 'I think this should work differently, more like this'). Feel free to give other ideas and to say what you think of the ones I have.

> Phantom Desktop Environment (PhaDE)

General Description:
Phantom is a Desktop Environment resulting from the crossbreeding of ideas from KDE and Xfce4: Have eye-candy, but keep things moving at a fast clip. Plasma could possibly be used, as well as Compiz Fusion. It would ideally be platform independent, relying on the X server system.

Feature List:
*Mirage: Memory Manager
     *Memory Saver: Windows are saved to disk when not in use, and are stored on the 'Desktop'.
*Desk: Redefined 'Desktop'
     *Minins: Applets (clock, battery, etc.) on 'Desktop'
          *Restore: Applications may be restored from saved status by clicking them.
         *File Show: Text files stored on the 'Desktop' have their contents displayed
*Blitz: Window Manager (likely to be replaced with xfwm and/or Compiz Fusion)
          *Fast Mode: No frills, just the basic, think xfwm4
          *Normal Mode: Basics, with some eye candy, think Compiz Fusion with most effects disabled
          *Candy Mode: The average Compiz Fusion look, with some extras
          *Showoff Mode: Everything disabled, for high powered gaming-class computers
          *Support for Themes
          *Scribe Support
*Scribe: Scripting, think AppleScript or bash scripting for GUI apps
          *Enable automatic control of applications with Scribe support
          *AutoScribe: Records Mouse and Keyboard actions into a script
*Ghost: File Browser/Package Manager (may be replaced with Thunar w/ extra plugins (all of which will be custom, as they are currently nonexistent)
          *Low Memory Footprint
          *Modular Build, with plugin support
          *Complete Scribe support
          *Tab support
          *Theme support
          *Package Management, like Synaptic or Adept, based off aptitude
*Phantom: Launcher
          *Hidden until a key is pressed
          *Scribe Support
          *Hides itself when not in use to free memory

Detailed Description of Features:
*Mirage:
          Attempts to manage available memory as efficiently as possible, writing apps to disk when not in use for a set period of time, and allowing them to be restored to their former state. As well as tagging so that certain applications. *cough*Games*cough*
*Desk:
          A new kind of 'Desktop' with an emphasis on speed and showing thinks as if they were on your desk. If you have a paper on your desk, you have it their so that you can read it. If you have a CD on your desk, you have it their so you have it on hand. The computer 'Desktop' should work like that. The contents of text files are shown (possibly even ODT and RTF files) on the 'Desktop' like they would if they were physical and on your physical desktop, image files would show their images, etc. But applications, folders, and the likes would simply be shown as their icon.
*Blitz: (likely to be replaced with xfwm(for 'Fast Mode') and/or Compiz Fusion(for 'Normal Mode' on up))
          A window manager with easy to pick 'levels': Fast, Normal, Candy, and Showoff. It will be able to run quickly on older machines, while being able to have eye candy like Compiz Fusion.
*Scribe:
          Like bash or sh scripting for GUI apps. Support for scripting in an editor like mousepad, kwrite, or gedit for applications enabled with Scribe Support. But also having a recorder (AutoScribe) for those less tech-savvy or for applications the don't have Scribe Support. It is interpreted, and the scripts are flagged, or marked, whether you want to run them or edit them (flagging is a potential module for Ghost).
*Ghost: (most likely based off Thunar, possibly just Thunar with extra plugins)
          Ghost will be a file browser, like Thunar or Dolphin, with support for package managing functions like Synaptic or Adept. The package managing will be based around aptitude, like both Synaptic and Adept. Modules would include things like a movie player, a music player, a text editor, and a clipboard viewer. Modules would be enabled and disabled in a preferences menu. If Ghost crashes after a module is enabled or disabled and refuses to restart, starting from a terminal with the --barebones (or -b) option would allow you to start with the default modules temporarily enabled, allowing the user to revert back to their previous settings.
*Phantom:
          The launcher creates itself when a key-press (potentially the Super/Windows/Apple key) is detected by the launcher daemon. It appears as follows: a sphere in the center, surround by options shaped as wedges. When initially started, the sphere in the center would display the user icon and the wedges would show the various application categories. It will remember the last category you were in (optional) and would load that category on the next start. If there were more applications than the sphere/wedge format would allow, the bottom-most two wedges would be shown as arrows instead, and mouseovers (or clicking as an option) would cause the wedges to cycle around the sphere in the direction indicated by the arrow.

Also note that all the names I used are not set in stone and most likely will change. If you have a better idea for anything just post. If I get enough positive feedback I will set up a sourceforge project for it. Also note that I don't have much experience with X programming, but am good with C

Ghost is currently under development, and will be the first thing to have an Alpha release. I plan to get together a usable (alpha) version of everything built before getting started on eye-candy.

---

### Post by RussianVodka on 2007-12-13
Wouldn't it be better if you joined an already existing project?

Seeing as it takes teams of people years to make a DE. I doubt you'll be able to do all that by yourself.

---

### Post by Dr Small on 2007-12-13
The question is... can you make it ?

---

### Post by quinnten83 on 2007-12-13
Well, the man said not to bring him down.
I think if you want to do this project you should.
making OSS should be a contribution, but also a hobby.
Personally i have limited knowledge of all that is needed. What i do know is that when I open an "open dialog" window to select a file from in an application, e.g. GIMP, I don't see a thumbnail in GNOME.
I think that is definitely something that should be applied.

---

### Post by smartboyathome on 2007-12-13
Your description is like the one for the Enlightenment Desktop Environment/Window Manager. They focus on Eye Candy without sacraficing speed. I would say try that out first before you go on to create a new desktop environment.

---

### Post by phrostbyte on 2007-12-13
A lot of stuff in your desktop environment like "memory management" is typically handled by the kernel. Putting "windows" into the disc which are inactive for awhile is pretty much already done thanking to the paging system.

---

### Post by bruce89 on 2007-12-13
KDE + XFCE makes no sense, they are complete opposites.

---

### Post by Linuxratty on 2007-12-13
> **RussianVodka said:**
> Wouldn't it be better if you joined an already existing project?

Seeing as it takes teams of people years to make a DE. I doubt you'll be able to do all that by yourself.

 i agree with this...A lot of projects need help...Help get at least two done before you think of starting your own.

---

### Post by Prisma on 2007-12-13
Achetar, your ideas are quite interesting, though I must confess I know very little about DE development. What I do know is that it takes many years to a group of developers just to get a DE to a decent level of usability (KDE, Gnome, E17 have been in development for several years). Therefore, I agree with a previous poster about that would be better for you to join an existing project.

---

### Post by Achetar on 2007-12-13
I know, I have looked at Enlightenment, GNOME, KDE, Xfce4, and several others, but none seem quite right. What I was thinking was ripping code for part of it and writing code for others. And yes, I would probably end up writing some kernel source. But I can do that. The tough part would be the Desk. BTW, I have helped with Enlightenment and AfterStep.

---

### Post by bruce89 on 2007-12-13
> **Achetar said:**
> What I was thinking was ripping code for part of it and writing code for others (like what GNOME did with KDE).

What code did GNOME steal from KDE?

---

### Post by SunnyRabbiera on 2007-12-13
well I like the concept of having all the functionality of KDE but having the low memory usage of XFCE...
a KDE lite if you will

---

### Post by Andrewie on 2007-12-13
you can steal the KDE code then just modify it to make your environment, it has some good ideas but reinviting the wheel is stupid. 

I like applications getting stored on the hard drive, but keeping them in ram is faster.

<snip>

---

### Post by bruce89 on 2007-12-13
<no longer relavent>

---

### Post by Prisma on 2007-12-13
> **bruce89 said:**
> What code did GNOME steal from KDE?

Well, if something is free you can't steal it :lolflag:

---

### Post by bruce89 on 2007-12-13
> **Prisma said:**
> Well, if something is free you can't steal it :lolflag:

No, fair enough.

I can't think of anything that GNOME could have got from KDE. (especially since GNOME is mostly C, KDE mostly C++).

---

### Post by happysmileman on 2007-12-13
> **bruce89 said:**
> No, fair enough.

I can't think of anything that GNOME could have got from KDE. (especially since GNOME is mostly C, KDE mostly C++).

That's what i was thinking, I find it incredibly likely that the GNOME developers looked through KDE's code, maybe copy pasted a couple of parts (though probably ended up rewriting a lot to make it C and not C++)

But who cares, they were allowed, so whether or not they did doesn't matter, both got developed and that's the important thing.

---

### Post by Nekiruhs on 2007-12-13
> **bruce89 said:**
> What code did GNOME steal from KDE?
I don't think they did as one of the goals of the GNOME project was to opensource KDE and QT.

---

### Post by bruce89 on 2007-12-13
> **Nekiruhs said:**
> I don't think they did as one of the goals of the GNOME project was to opensource KDE and QT.

Was it? I was under the impression that is was to make a properly free DE. (KDE then wasn't properly free as QT was under some weird licence)

There was a LGPL reimplementation of QT, but it never really got off the ground.

---

### Post by Nekiruhs on 2007-12-13
> **bruce89 said:**
> Was it? I was under the impression that is was to make a properly free DE. (KDE then wasn't properly free as QT was under some weird licence)

There was a LGPL reimplementation of QT, but it never really got off the ground.
Sorry, not opensource they wanted to free KDE and QT. It wasn't a main goal, but none the less it was a goal. Yes their main goal was to create a truly free DE to compete with the nonfree KDE, they ended up doing that and freeing KDE.

---

### Post by molom on 2007-12-14
Go for it. If you can develop something fast (in a year or so) is would be really nice. Just some advice. Make something out of the usual. e16 wasn't very popular because it was a lot like blackbox. But when e17 came out and became stabler many people started to use it just because it was something out of the ordinary. The reason that it was out of the ordinary was because it was fast, full of eyecandy and functional. You could make for example something that is fast, uses 3d eyecandy instead of 2d eyecandy and make it functional. I wish you good luck.

Cheers,
molom

---

### Post by Achetar on 2007-12-14
Thanks for the support, molom. GNOME was based off of KDE code. ***Original*** KDE code. Not the new stuff. KDE was originally built using C I believe.

And yes I was planning on using 3D eye candy instead of 2D. And I was planning on ripping code from, say, KDE? And probably looking through GNOME and XFCE code to learn a bit more on how to implement some things. I will probably end up ripping code for Ghost from Thunar and Synaptic. And may end up using Compiz Fusion or Beryl for the WM, just toned down effects-wise. Or possibly xfwm for the WM. It does compositing, too.

Thanks again :)

---

### Post by GeneralZod on 2007-12-14
> **Achetar said:**
> Thanks for the support, molom. GNOME was based off of KDE code. ***Original*** KDE code. Not the new stuff. KDE was originally built using C I believe.

Er ... no part of this statement is correct, I'm afraid :) GNOME was started from scratch, using GTK as its toolkit.  KDE was always based on Qt, which has always been written in C++, and as has KDE itself.

---

### Post by Achetar on 2007-12-14
> **GeneralZod said:**
> Er ... no part of this statement is correct, I'm afraid :) GNOME was started from scratch, using GTK as its toolkit.  KDE was always based on Qt, which has always been written in C++, and as has KDE itself.

My apologies, I was mistaken. Thank you for correcting me (still... there is no shame in ripping code from an OpenSource Project!)

---

### Post by molom on 2007-12-14
> **Achetar said:**
> Thanks for the support, molom. GNOME was based off of KDE code. ***Original*** KDE code. Not the new stuff. KDE was originally built using C I believe.

And yes I was planning on using 3D eye candy instead of 2D. And I was planning on ripping code from, say, KDE? And probably looking through GNOME and XFCE code to learn a bit more on how to implement some things. I will probably end up ripping code for Ghost from Thunar and Synaptic. And may end up using Compiz Fusion or Beryl for the WM, just toned down effects-wise. Or possibly xfwm for the WM. It does compositing, too.

Thanks again :)

I would say using e17 code/base would be impressive because its possible to produce amazing eyecandy and still be lightweight. KDE on the other hand has poor eyecandy (without beryl or compiz) and still is one of the slowest DE's in the open source world. But it's your DE. You make the decision :D.

---

### Post by -grubby on 2007-12-14
I don't think this "ghost" app should do so much. I think it would be annoying and especially if it crashed. I don't like apps trying to do everything

---

### Post by Tundro Walker on 2007-12-14
The quintissential problem here, which folks are pointing out, is that it's easier to talk about things rather than do them.

So, it might be hard to get a group going on your idea if you're looking for such.  You'll have to start it on your own, like as a SourceForge project, and then when folks start checking it out, you might get some buy-in and development support from others.

However, that's not to discourage you from trying it.  Even if you kicked off your own project, and did a lot of things wrong on it (which is subject ... matter of opinion depending on who's checking it out), there's always the possibility that you might do something cool in a unique or better way.  Your project might turn into something great, or it might get scrapped.  But, if you have some really ingenious idea, folks will take notice and work it into their projects, or it might be the catalyst to bring them into your project.

The tricky part is, there's so many programming "things" these days (languages, DE, IDE's, etc) that it's hard to check them all out.  And, a lot of folks are either doing something just as a learning project, and end up with a run-of-the-mill "whatever" when they get done (it was a learning project, so it works like similar projects...nothing spectacular).  Other projects are just trying to delve into territory that's already been beaten to death...EG: window managers...seems there's tons of them out there, and while they range from minimalist to robust, it's rare you'll find someone create a new one out of the clear blue with some totally awesome, radically new innovative idea that turns the window manager world on its head...the "market's tapped out" so to speak.

But, I say roll with it.  Start small...make a baby-step list of things you'd like to do, and just focus on the core first.  Add in stuff you like, and make it fun for yourself.  Never know if you'll end up tackling some problem in a totally novel way that others can appreciate.

---

### Post by Achetar on 2007-12-15
About making Ghost do everything.. That is what the modules are for. If you don't want something disable it! And if you want something, enable it! (or if it hasnt been made yet convince me to do it!) I'm going to start this project with Ghost most likely. It will be the simplest. (rip code from Thunar, which already has module support, and add aptitude support w/ a GUI)

After that, hmmm, maybe a basic version of Phantom (to be improved upon of course). At first I just want a DE that just works and doesn't look awful. (I personally don't like how e17 looks).

Desk will probably one of the last things I tackle, as it will be the most complicated. 

And there have been people saying that writing programs to disk doesn't save memory. I thought about it, and I am going to test it and see. (though not first thing). If you have 5 different programs running, and you only use 4 of them, then say, after an hour the one you are not using will be written to disk, like if the computer were hibernating.

Also, yes, I was planning on working on this alone for now (I didn't even expect this much feedback). And you are right about the WM, Tundro Walker, I was planning on either using xfwm or Compiz, or including both and giving the option.

---

### Post by Xbehave on 2007-12-15
i like most of the ideas a few questions:
will you use qt/gtk for apps?
will you make it panel based? or wierd like E
how do you tell when to suspend a program?
ideas:
inline searching everywhere, dialogs to search text are a pain
being able to have an app on the desktop running (to save screenspace) 
active memory control: being able to reduce a programs memory usage limit while its running?




> **molom said:**
> I would say using e17 code/base would be impressive because its possible to produce amazing eyecandy and still be lightweight. KDE on the other hand has poor eyecandy (without beryl or compiz) and still is one of the slowest DE's in the open source world. But it's your DE. You make the decision :D.
say what? thats flame bait and ill take it
kde3 has lower memory usage than gnome
kde3 has more eye candy than gnome (or any WM i can think of (possible excluding enlightenment as i never got used to it))
kde4 has less memory useage than kde3 and responds faster
kde4 provides its own composting

---

### Post by MONODA on 2007-12-15
I have a suggestion. How about instead of minimizing to a panel, when you click a button, the window goes into the background like it does with scale. Also, if you could edit files while in that zoomed at view it would be great.
good luck

---

### Post by Xbehave on 2007-12-15
Also, if you could edit files while in that zoomed at view it would be great.
you could in beryl but compiz said it was a dirty hack, and binned the code!
wooo great merge \o/

---

### Post by molom on 2007-12-15
I understand how you don't like the looks of e17. But does that mean you cant use it's code? All I was talking about was it's speed to be able to handle different types of eye candy. If that speed can be used with your DE's looks imagine what you can produce.

---

### Post by DjBones on 2007-12-15
I think the most innovative ideas of yours like others have said could be realistically applied to teams that already exist..
like maybe working with the enlightenment team on your circular-wedge-menu as a feature to E17?
or possibly with konquerer to make an extension compatible as a package-manager..

---

### Post by Achetar on 2007-12-16
Just because I said I don't like how e17 looks doesnt mean I won't use code from it. I probably will.

Also KDE never ran well on my computer, maybe its just the hardware, i dont know.

And about Ghost, I am thinking about, instead of rewriting a File Manager, using Thunar with some custom modules (plugins, whatever).

I am playing around with Ghost, and there are basically three possible outcomes for it:
1. It won't take horribly long, and I will rip code from Thunar (or another File Manager)
2. It will take awhile because I can't easily use the Thunar code ( or any other file manager)
3. It won't take long because I use Thunar with some extra plugins.

Who knows. I am figuring on getting the smallest things done first, to show progress being made, which will attract devs. (If no progress is being made, then no one will want to join).

Thanks for all the ideas!

I also am thinking about using parts of the XFCE4 code (not the panel or desktop) and using Desk and not using a panel at all (I don't use panels, I use hotkeys, but I might ought to include a panel for those who don't like hotkeys i guess) and Phantom.

I will probably scrap Blitz in favor of xfwm and Compiz Fusion. Although, I may modify them to allow scripting support.

Thanks Again!

---

### Post by molom on 2007-12-23
Hows everything going with the progress?

---

### Post by Achetar on 2007-12-24
> **molom said:**
> Hows everything going with the progress?
It has turned out that I am rewriting a FM, using Glade and GTK+. It is coming along all right. I have 3 errors left to solve before I can compile it. Wish me luck! 

(When it works I will post the src up here)

---

### Post by slimdog360 on 2007-12-24
when you say 'scribe', do you actually mean 'scribes'? Im not trying to be a grammar nazi or anything, its just that you said scribe a number of times and was thinking that maybe you were talking about something else.

---

### Post by Achetar on 2007-12-24
No, I was just calling the scripting function 'Scribe' for now. If you have a better name I would love to hear it! (BTW, when I fixed one of the errors w/ Ghost, it came up with 30 more, still working on it, wish me luck!)

---

### Post by mikeym on 2008-01-09
Here is something minor - UI wise - that needs to be incuided from an early stage in a WM which I have been banging on about for ages, how about freeing up the menu display position? 

At the moment it's only really possible without a hack to have the menus display within a window, but it is a really intuitive step to move the menu up next to the other menus. Apart from anything else it frees up acres of space on screen.

---

### Post by thisllub on 2008-01-09
> **Achetar said:**
> 
After that, hmmm, maybe a basic version of Phantom (to be improved upon of course). At first I just want a DE that just works and doesn't look awful. (I personally don't like how e17 looks).

How does e17 look?
In my experience it looks exactly how I want it to look.

I have nothing on my desktop and one shelf with a clock in it.

The killer features in e17 are the Run Command dialog and the Client List Menu.

More keyboard use = more efficiency.

I don't want "desklets" they give me nothing.

---

### Post by Achetar on 2008-01-14
Ehh, I have been really busy lately, and not much has gotten done since my last post. Just wanted to update you on what was happening.

---

### Post by Achetar on 2008-01-23
I haven't worked on it much lately. Mostly because has gotten dull and monotonous. Anyway, if you have a hobby you should enjoy it or stop it. If anyone wants to write source for this, feel free to. I don't have much done on it (and I'm not even sure if I still have that, I had Windoze problems, it erased parts of my Ubuntu Partition). Thanks for the support, if I ever get to the point where I enjoy low-level programming, I will work on this. In the mean time I will probably just work on bug finding for Xfce, and convince them to do some of the stuff. Sorry if I disapointed you, but my forte is coming up with original designs, not building them. Expect to see me in the Xfce credits sometime!

---

### Post by molom on 2008-01-24
That is completely acceptable, especially when its a hobby you should enjoy it, at least you gave it a go and found out what its all about. Hope you have a good week.

Cheers,
molom

---

### Post by Terry of Astoria on 2008-01-26
Since switching (mostly) to Linux in 2000 I've pretty much used the default Desktop Environment in whatever distro I was using at the time - KDE in Mandrake was thought to be more "configurable" (hm. . .)  than Gnome. I tried Blackbox and liked it but never really used it much. Icewm and XFCE I saw on Vector Linux. Since finding Ubuntu Warty in 2004 I have used Gnome. I like it but this thread has encouraged me to try some other desktop environments. 
   Thank you very much indeed for sharing those ideas. It was a very fun and positive thread.

---

### Post by Achetar on 2008-01-27
Thanks, I hope you enjoy finding new DEs!

---

