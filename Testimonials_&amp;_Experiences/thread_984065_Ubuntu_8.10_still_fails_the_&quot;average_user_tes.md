---
title: "Ubuntu 8.10 still fails the &quot;average user test&quot; (on a Dell Latitude D620)"
date: 2008-11-16
forum: Testimonials &amp; Experiences
---

### Post by Kethinov on 2008-11-16
I installed Ubuntu 8.10 Intrepid Ibex on a Dell Latitude D620. This is a fairly decent laptop to use Linux on, as the hardware is fully supported.

The good news first: Ubuntu's installer is great. No complaints. And all my hardware worked out of the box. Good stuff.

However, Ubuntu still fails what I call the "average user test" with its out of the box experience. After a clean install, these are the issues I encountered that would be pretty damning for the average user:

**Severe bugs**
[LIST]
[*] Random CRC errors on boot: "crc error, system halted." A software update seems to have made this problem go away.

[*] Adding a second DVI monitor (a 52" Samsung 1080p TV in my case) did not work correctly. Setting it as a second monitor resulted in extremely glitched behavior, such as viewport limitations, inability to drag windows beyond arbitrary points, etc, and desktop effects stopped working. *(Setting the dual monitors to clone, or with one monitor enabled and the other monitor disabled [in either combination] worked correctly.)*

[*] When a game is full screened (such as Frozen Bubble) the mouse cursor remains visible and is stuck in the center of the screen. I appear to not be the only one who's seen this. See also: [http://ubuntuforums.org/showthread.php?p=5989420](http://ubuntuforums.org/showthread.php?p=5989420) - this is actually a regression. I did not have this problem with Hardy Heron.

[*] Trackpad speed and mouse speed should be separate settings. At present, it is impossible to have a setting which doesn't make one too fast or the other too slow.

[*] Kubuntu and Xubuntu 8.10 do not have an option for disabling trackpad tap-click (GNOME does, however.)
[/list]

**Less severe bugs**
[list]
[*] Plugging in a USB hard drive with general data on it caused a dialog to pop up saying "you have inserted a picture CD"

[*] Opening my USB hard drive in nautilus shows a dialog at the top which says "these files are on a picture CD"

[*] Sometimes message bubbles overlap, e.g. "updates available" and "restricted drivers available." Only one should be shown at a time.

[*] Transitions from boot to login screen to logged in often require X11 to be started/restarted creating a very choppy un-smooth transition. Sometimes users see terminal output for a second or so. This is an extremely poor user experience. X11 should NEVER be started/stopped except on boot/shutdown. (See Windows/Mac OS X user experience)
[/LIST]

**Bad defaults**
[list]
[*] Compact view in nautilus handles long filenames poorly, behavior akin to Finder or Windows Explorer's list view in Win XP would be more appropriate.

[*] Trackpad tap-click should be disabled by default. (Tapping the trackpad makes a click... very bad user experience due to frequent accidental "clicks.")

[*] New windows should never open maximized by default. Most don't, but I encountered a few that did. On a 1920x1200 screen or similar, this looks terrible.

[*] Never beep the system bell. Turn that off by default. There's nothing worse than the obnoxiously loud system bell going off in a quiet room.

[*] Multiple desktops is a power user feature, it should be off by default (and thus the gnome panel widget should be hidden)

[*] CompizConfig Settings Manager should be installed by default and buried into an "advanced" portion of the desktop effects options

[*] Default resize mode in CompizConfig Settings Manager should be set to "Normal" not "Rectangle"

[*] Default text editor for opening text files in Kubuntu should not be kate.
[/list]

**Aesthetics**

Criticism of Ubuntu's brown/orange theme is not new. However, it must be said once again that it is not very attractive. The new default wallpaper is better than Hardy's, but like the rest of the theme is still too brown/tan/orange. I recall seeing a version of this image with a great deal more color. Some reds and blacks, nice contrast. Why wasn't that version used? Why do we have to colorize it brown before shipping the OS?

Points in the theme's favor: the widgets and icons look great. This means all a user has to do to "fix" the look and feel of Ubuntu is going into the prefs and change the colors from brown/orange to pretty much anything else (I prefer blue) and set a different wallpaper. Both tasks are relatively simple. However, the default theme should be more attractive. Most ordinary users won't change it.

One final complaint: When are the theme folks gonna learn how to anti alias the rounded corners on windows? These pixelated corners look horrible.

---

### Post by paul101 on 2008-11-16
use kubuntu :)

---

### Post by AllenGG on 2008-11-16
Although I agree with you in part, none of the above additions you invoked could be accomplished easily in any other distro.  
And plugging in a USB external HDD or memory stick causes many complications in most MS Windows boxes.
Recently I did a "clean" install on a new Dual core system and was up, running and on the Internet in 12 minutes.
But, your criticisms make sense. The average "new" user is somewhat more computer savvy and more demanding.

---

### Post by Swagman on 2008-11-16
Can't say I've had random CRC errors

Hang on.. I'll just plug in my 16gb pendrive.....

Nope... [**No issues**](http://i261.photobucket.com/albums/ii45/Outcast_Aussie/pendrive.jpg) <----Screeny

Pop up bubbles overlapping **IS** an annoyance... agreed

Not too fussed about theme. Can be changed easily.

---

### Post by init1 on 2008-11-16
Yeah, I've noticed a few. For example, if I download a .deb and select open, it give me an error. It works fine if I download it and then run it, but I think it might confuse some beginners.

---

### Post by Skripka on 2008-11-16
> **paul101 said:**
> use kubuntu :)

Bingo.  

My box was up and running 8.10 (from a wiped system partition) in about 15 minutes and ownloading updates via wireless.  GPU was autdetected, monitor native resolution was autodetected and used on install (yay for 16080X1050), external drives work fine as they should.  Overlapping pop-up bubbles can be annoying, but that is it.  Nvidia 177.80 drivers work like a charm with KDE4 in Ibex.....


Is it just me or does it seem that on Ibex, Gnome users are getting lots of problems?

---

### Post by Tamlynmac on 2008-11-16
I wonder if many these issues are more of an annoyance than an actual bug.

As for the theme - does anyone continue to use the original theme? Most Ubuntu users are free spirits and modify their systems immediately upon installation. At least all users I know do. Which is the very heart of OSS, "if you don't like it modify it". I sincerely believe that should be our motto.

I do agree that a number of your issues sound extremely annoying.

---

### Post by Mr. Picklesworth on 2008-11-16
I totally agree with you on a lot of these points. You'll be happy to know that a lot of this stuff is being addressed!

Personally, I think Compiz should be gone by default in your suggestions. After all, you suggest having only a single desktop by default, and Compiz's default effects in Ubuntu are mostly to do with switching desktops. (Everything else is done -- often just as well and occasionally better -- by Metacity's compositor). That would also remedy all window management issues since Compiz is simply not a good window manager. It may also fix your mouse cursor issue.

Removing the virtual desktops by default, though, is something I disagree with. It is a very powerful feature; something we should promote and encourage, not disappear because "it's different". Possibly a popup explaining the concept to users when they first change desktops or click on the applet would do the trick, although that could be completely terrifying. An introductory slideshow in the installer could explain the idea, too. Thanks for the reminder!

Nice point about Compact view. The selected file should have its name expand, overlapping other icons. (I believe other file browsers do that). A bit weird how much it takes to see the full filename at the moment.

Message bubbles are meant to stack, not overlap, and they usually do. That's a funny bug... perhaps one pesky program isn't using libnotify, instead displaying message bubbles its own ugly way. Not much can be done if that's the case, except giving said program's authors a stern talking to (and not shipping it by default since said program clearly does not integrate into the desktop). That, or it could be a bug with the notifications :)
On that topic, I noticed an issue where, when notifications appear with the screensaver running, they flicker into view for a moment before disappearing. That needs to be smarter. Either they should be totally invisible until the screensaver is exited (at which point even the timered ones are still there with a timestamp on them for good measure), or they should appear, smoothly, above the screensaver for a few seconds.

I haven't had any programs open maximized for me, but some think their "normal" unmaximized version should consume the entire screen, which is completely bizarre and a serious usability issue (since it demands that the user resize the window himself, only after figuring out that it is indeed not maximized via the tricky to detect hints to that end). We need the window manager to be cleverer with that, finding a good unmaximized size on its own.

Funny thing with "you have inserted a picture CD". That's actually a really awesome feature for camera memory cards, but it has never incorrectly claimed them to be on a CD for me (and is never wrong in figuring it out), instead saying stuff more along the lines of "[this media contains digital photos]("http://bp2.blogger.com/_Vi7TqTLw_Tw/SJiKyoDaRdI/AAAAAAAAAMg/Cf7H26BiYm8/s1600-h/WowNautilus.png")". Are your devices loaded with pictures or organized exactly like a photo CD would be? It could be a localization issue that has your strings always saying "CD". (Mine is en-CA).
It would be nice if Nautilus autodetected different kinds of content on inserted media, then had an extensible library with lots of context-sensitive actions, and blended them all together into a single information bar. For example, a single volume has Photos, Backups, Settings, Software *and* Music, and there are actions that can be performed automatically for each one!

I agree about the system beep. Something neat to note is you can adjust that in the volume control; just enable the PC Speaker track and turn it down. It *should* be at 10% or muted by default. A lot of software is incorrectly using that instead of triggering the newer beep sound (which is played through real speakers).

I don't agree with disabling tab to click, although we do need better touchpad options out of the box since the current set does not do our beautiful Synaptics driver justice. For example, it completely supports two finger and three finger tapping, scrolling with two fingers (although that one is a tad wobbly with some touchpads), and circular scrolling. That is, drawing a circular gesture to scroll which means you can keep scrolling forever. It is completely natural and totally cool.
Most of that stuff is disabled by default, although if I recall correctly three and two finger tapping is there from the start.

> Transitions from boot to login screen to logged in often require X11 to be started/restarted creating a very choppy un-smooth transition.You may want to check out Kernel Mode Setting, which is coming in 2.6.29 (Jaunty). Fedora 10 has this working by default with ATI cards, and Intel is also just finishing up support. NVidia, as always, is lightyears behind standards compliance, instead opting to write their own standards to look like they're trying.
Kernel mode setting means that the mode does not change when you switch virtual terminals, log out, start / stop X or any of that because it is set properly from the start in the kernel! It is at the heart of [Fedora's Plymouth graphical boot]("http://www.phoronix.com/scan.php?page=article&item=fedora_plymouth&num=1"), which rivals the Mac in smoothness.

Yah that's right, it doesn't just avoid display mode changing, it **cross-fades** into GDM, and then the excellent new-fangled GDM (used in Fedora) performs a perfect, smooth transition into the user's GNOME desktop (thanks to it using entirely the same technologies as the GNOME desktop). Alas, I can't quite experience it with my NVidia card, but as I understand it logging out has the same level of smoothness.

---

### Post by kspncr on 2008-11-16
You can't possibly be arguing that most users agree that what you listed as "bad defaults" are really bad defaults. It completely depends on the user and is completely subjective. I suppose you do speak for everyone, right...

You also mention a dual-monitor setup. I definitely wouldn't say the "average user" has a dual-monitor setup.

On a second thought, whatever.

---

### Post by cariboo on 2008-11-16
I would have to say that everything that the OP calls severe bugs are just minor annoyances, and the rest could be classed as annoyances. You should maybe re-title this "average windows user test".

Jim

---

### Post by Melindrea on 2008-11-17
I haven't really had any of those problems on Ibex, but possibly I've been lucky.

As for virtual desktops, I call that one of the best features, and one that should be encouraged for all to use - great when you have a smaller screen, like my laptop (I tend to have things on at least 2 out of 4 desktops, sometimes I have things on all 4 of both of my computers, working on).

I may be unique, but I really, really love the dark theme. Up until only a few days ago, I had the standard background image (recently changed to Ubuntu-Tan), and the DarkRoom theme. Once I figure out how to change so that the DarkRoom theme (ish) doesn't screw up Firefox's colours, I will be using that on my hardy install aswell.

---

### Post by Kethinov on 2008-11-17
Thanks everyone for the responses. I'm glad this stirred up some kind of discussion. Let me take a moment to respond to everything I feel is relevant. You had a lot to say, so I have a lot to respond to...

--

> **paul101 said:**
> use kubuntu :)

There are two reasons why this is a bad answer.

1. Kubuntu was worse. There is documentation regarding this in my original post. (Largely because it had most of the same problems and some new ones of its own.)

2. Ubuntu, for better or worse, standardized on GNOME. Most people are going to use Ubuntu. Not Kubuntu, not Xubuntu, not etcBuntu. Other flavors should be *options for power users*, not solutions to basic usability issues and bugs.

> **AllenGG said:**
> none of the above additions you invoked could be accomplished easily in any other distro.

All that means is it's a damn shame that the most usable distro has all these problems, still, after all this time.
  
> **AllenGG said:**
> And plugging in a USB external HDD or memory stick causes many complications in most MS Windows boxes.

Not really...

> **Swagman said:**
> Can't say I've had random CRC errors

In addition to the early, more frequent times I encountered them, I seem to be able to reproduce it whenever the computer is shutoff improperly (e.g. by abruptly shutting the power off).

> **Swagman said:**
> Hang on.. I'll just plug in my 16gb pendrive.....

Nope... [**No issues**](http://i261.photobucket.com/albums/ii45/Outcast_Aussie/pendrive.jpg) <----Screeny

This is not surprising. My hardware is quite different. I'm using external USB hard drives. The bug may be isolated to incorrectly identifying those and work just fine with pen drives. Or it could be incorrectly identifying my particular brand of drives. Nevertheless, it does happen. Every time.

> **Tamlynmac said:**
> I wonder if many these issues are more of an annoyance than an actual bug.

Are you kidding me? Most of these would be *show stoppers* for the kinds of "average users" I'm thinking about. You know, the kinds that aren't tech savvy *at all*. Let's review:

[list]
[*] When they see "CRC error" they take the laptop to the shop.
[*] When they need to rig their laptop to a projector or a TV for a presentation and the OS can't handle it, they get an OS that can.
[*] When full screen games can't be played because a giant mouse cursor in the center of the screen won't go away, they find an OS that doesn't have this problem.
[*] When they can't separately configure the speed of their trackpad and their mouse, resulting in one of the two always being too fast or too slow, they're annoyed to such a degree that they either live without one of the two, or get another OS.
[/list]

Now, as for the rest of the stuff on my list? Sure. Annoying, not show stopping. But definitely profoundly unprofessional and doesn't make Linux look like a very attractive alternative to its competition. People will *pay* to not be this annoyed.

> **Tamlynmac said:**
> As for the theme - does anyone continue to use the original theme? Most Ubuntu users are free spirits and modify their systems immediately upon installation. At least all users I know do. Which is the very heart of OSS, "if you don't like it modify it". I sincerely believe that should be our motto.

Two problems with this:

1. Don't you think that the fact that "most people" who use Ubuntu right now are changing the theme is some pretty strong evidence that it's a bad theme, and thus a bad default?

2. "If you don't like it, modify it" has been the Linux motto for a long time. It's one of the reasons Linux doesn't catch on. People want computers that, forgive the cliche, "just work." This includes them having sane defaults and looking attractive *out of the box.* The only reason Ubuntu does as well as it does is because competing distros are so much worse. That's pretty sad.

> **Mr. Picklesworth said:**
> I totally agree with you on a lot of these points. You'll be happy to know that a lot of this stuff is being addressed!

Indeed. A lot of the stuff that comes out of Mark Shuttleworth's mouth makes me giddy. It's just sad that every release seems to not deliver...

> **Mr. Picklesworth said:**
> [Disabling Compiz] may ... fix your mouse cursor issue.

It does not.

> **Mr. Picklesworth said:**
> Removing the virtual desktops by default, though, is something I disagree with. It is a very powerful feature; something we should promote and encourage, not disappear because "it's different".

It's not different anymore. OSX and Windows both have the feature now and it's off by default for a very good reason. The average computer user doesn't understand this feature. And anyone who does understand this feature will also be savvy enough to know how to turn on advanced preferences.

The absolute worst user experience I've seen so far with multiple desktops is associating the scroll wheel to desktop switching when the scroll wheel is triggered over an empty desktop area. I've seen a number of users who have no idea what multiple desktops are accidentally trigger a switch to another desktop and then panic, thinking they've lost all their work.

> **Mr. Picklesworth said:**
> I agree about the system beep. Something neat to note is you can adjust that in the volume control

I'm aware. The problem is it should definitely be off by default. And what's worse, is when you go to turn it off with the option you describe, the system bell still fires whenever you shut down the computer. So turning it off only turns it off for some situations, not all. In order to disable it globally, you still have to use the terminal...

> **Mr. Picklesworth said:**
> I don't agree with disabling tab to click

Touchpads have varying degrees of sensitivity. On my laptop, it's very, very hard to use the touchpad without triggering accidental clicks. Thus, turning this feature off is essential. Moreover, again, this is a power user feature. Users associate touchpads with dragging the mouse, not clicking. Buttons are for clicking, not touchpads.

> **Mr. Picklesworth said:**
> although we do need better touchpad options out of the box since the current set does not do our beautiful Synaptics driver justice. For example, it completely supports two finger and three finger tapping, scrolling with two fingers (although that one is a tad wobbly with some touchpads), and circular scrolling.

Agreed. Don't get me started on this one. Ubuntu needs to have all the support for the crazy gesturing that comes out of the box on MacBooks (where hardware supports it).

> **Mr. Picklesworth said:**
> You may want to check out Kernel Mode Setting, which is coming in 2.6.29 (Jaunty). Fedora 10 has this working by default with ATI cards, and Intel is also just finishing up support. NVidia, as always, is lightyears behind standards compliance, instead opting to write their own standards to look like they're trying.
Kernel mode setting means that the mode does not change when you switch virtual terminals, log out, start / stop X or any of that because it is set properly from the start in the kernel! It is at the heart of [Fedora's Plymouth graphical boot]("http://www.phoronix.com/scan.php?page=article&item=fedora_plymouth&num=1"), which rivals the Mac in smoothness.

Yah that's right, it doesn't just avoid display mode changing, it **cross-fades** into GDM, and then the excellent new-fangled GDM (used in Fedora) performs a perfect, smooth transition into the user's GNOME desktop (thanks to it using entirely the same technologies as the GNOME desktop). Alas, I can't quite experience it with my NVidia card, but as I understand it logging out has the same level of smoothness.

Wow that sounds really cool. I look forward to seeing it in Ubuntu!

> **kspncr said:**
> You can't possibly be arguing that most users agree that what you listed as "bad defaults" are really bad defaults. It completely depends on the user and is completely subjective.

Let's run down the list.

[list]
[*] Long filenames in Nautilus list view: this is a terrible user experience for anyone who has a lot of files which all start out with the same 10-20 character string. In Windows, the columns widen to accommodate the longest filename. In Mac OS X, they trim the middle of the string, not the end. Both are better than what Nautilus is doing.
[*] Trackpad tap-click: see my responses above for further substantiation on why this is a bad default.
[*] New windows should never open maximized by default: do I really need to go into greater detail on this one?
[*] Never beep the system bell: see my responses above for further substantiation on why this is a bad default.
[*] Multiple desktops: see my responses above to for further substantiation on why this should be disabled by default.
[*] CompizConfig Settings Manager should be installed by default: you could probably talk me down from this one, as it's a power user feature. But it's one of the most commonly installed third party apps after a fresh install. Burying it under an advanced tab sounds a hell of a lot more convenient than having to install it.
[*] Default resize mode: in both Windows and OS X when you resize windows, they resize. They don't get a blue box drawn around them until you let go of the resize handle. The irony here is very, very old versions of Windows and Mac OS behaved like this because there were not enough system resources to refresh the window during a resize. This default makes Linux look antiquated, even though it's a "desktop effect" feature.
[*] Kate should not be a default text editor in KDE because most people aren't opening arbitrary text files to write code. Why isn't kwrite or something similar the default?[/list]

> **kspncr said:**
> You also mention a dual-monitor setup. I definitely wouldn't say the "average user" has a dual-monitor setup.

Average users connect laptops to secondary displays *all the time*. Whether it's a monitor on their desk, a projector a the office, or their TV this is absolutely *critical* functionality that the average user *does* expect to be easy.

> **cariboo907 said:**
> I would have to say that everything that the OP calls severe bugs are just minor annoyances, and the rest could be classed as annoyances. You should maybe re-title this "average windows user test".

Jim

The degree of ambivalence this post has attracted is very concerning. Is the Linux community really this disconnected with the average user?

---

### Post by Skripka on 2008-11-17
> **Kethinov said:**
> 
Let's run down the list.

[list]
[*] Long filenames in Nautilus list view: this is a terrible user experience for anyone who has a lot of files which all start out with the same 10-20 character string. In Windows, the columns widen to accommodate the longest filename. In Mac OS X, they trim the middle of the string, not the end. Both are better than what Nautilus is doing.
[*] Trackpad tap-click: see my responses above for further substantiation on why this is a bad default.
[*] New windows should never open maximized by default: do I really need to go into greater detail on this one?
[*] Never beep the system bell: see my responses above for further substantiation on why this is a bad default.
[*] Multiple desktops: see my responses above to for further substantiation on why this should be disabled by default.
[*] CompizConfig Settings Manager should be installed by default: you could probably talk me down from this one, as it's a power user feature. But it's one of the most commonly installed third party apps after a fresh install. Burying it under an advanced tab sounds a hell of a lot more convenient than having to install it.
[*] Default resize mode: in both Windows and OS X when you resize windows, they resize. They don't get a blue box drawn around them until you let go of the resize handle. The irony here is very, very old versions of Windows and Mac OS behaved like this because there were not enough system resources to refresh the window during a resize. This default makes Linux look antiquated, even though it's a "desktop effect" feature.
[*] Kate should not be a default text editor in KDE because most people aren't opening arbitrary text files to write code. Why isn't kwrite or something similar the default?[/list]


The degree of ambivalence this post has attracted is very concerning. Is the Linux community really this disconnected with the average user?

Who are we building an OS for?

The "average" user?  Who knows how to turn a computer on, start programs, and open Youtube?

Converts, who want a free OS, they can do what they want with?
  
People who know what they are doing on computers?  A demographic ranging from experienced linux users (but still not programmers), all the way up to programmers?

People who are totally ignorant of computers?  People who don't know how to say "GUI", and are barely comfortable turning a box on, much less using it?


If you want a different file manager, get a different file manager.  There are MANY.  I ran an E17 DE for a while, but I hated the file manager-so I installed KDE4 Dolphin.  You don't like Kate being the default, then change the default---same as you would under Windows or Mac.  You want Compiz installed-you instal it.  You don't like the window beavior-then change the window behavior.  You don't like it, it is easily changed, most of the time.

Linux is made such that there is no "One Look" to Linux, it looks and functions how the user wants it to.  There is no perfect Vanilla-one-size-fits-all-Anything (clothes, car, shoes, houses....).  The best thing to do in which case-is to offer the tools to make a user-fitted OS, Which Linux does quite well.

You talk about aesthetics as being a reason to turn on Compiz be default--MOST XP users HATE HATE HATE eye-candy, that is their demographic.  Most OSX users love it.  There are different demographics and different tastes, as well as many tiers of hardware where Compiz crashes computers.  I personally think it should be turned off by default and uninstalled, as the number of times I got it to work well and right, I can count on a hand with no fingers.


What are you grinching about?  There are some buggy behaviors cited-but I'd first question the integrity of your LiveCD, as many of those (i.e. pen/external drive problems) I have never seen before.  Presuming for a minute, that the behavior you are seeing, being buggy are problems-report them.  Bug fixes only happen when devs know there are problems.  Also Ibex is less than a month old.  NO OS EVER was perfect when it was a month out the door.  WinXP flopped-and everyon though it was a dumb idea.  MacOS X.1,X.2, X.3, X.4, and X.5 wew ALL VERY buggy until version 10.x.3 or 4 (Experienced Mac OS users warn new adoptees to not expect stability for that long, BTW).

It sounds like you want an OS perfectly suited for you without you, your abilities, and your aesthetics without having to raise a finger-tip of effort to get it.  Sorry, it does not exist.  Simple fact.  Linux has all the funcionality and tools to get it though, if you put some effort into making it.  

When you write an OS for the lowest common denominator-no one with any computer skill will want to use it, or develop for it.  

[QUOTE=]
"Linux is not user-friendly. It _is_ user-friendly. It is not ignorant-friendly and idiot-friendly."
[/QUOTE]

---

### Post by Mr. Picklesworth on 2008-11-17
Have you filed a bug for your external hard drive, by the way? The bug is in HAL (*maybe* Nautilus), so make sure you put it at the right place. They are generally quite responsive to these sorts of misdetection bugs :)
Oh, and let's hope DeviceKit is indeed capable of magic.

Still not convinced about disabling virtual desktops by default. Arguably, people have more trouble with iconifying windows, but once they learn the usefulness of that feature they do it all the time... (Except me; I just bump them to other desktops).

---

### Post by Kethinov on 2008-11-17
> **Skripka said:**
> Who are we building an OS for?

The "average" user?  Who knows how to turn a computer on, start programs, and open Youtube?

Converts, who want a free OS, they can do what they want with?
  
People who know what they are doing on computers?  A demographic ranging from experienced linux users (but still not programmers), all the way up to programmers?

People who are totally ignorant of computers?  People who don't know how to say "GUI", and are barely comfortable turning a box on, much less using it?

All of the above, and despite what your post implied, these crowds are not mutually exclusive to target. As is done in Windows and Mac OS X, the correct strategy is to use defaults the lowest common denominator prefer and leave the customization up to the more advanced users. Linux has it backward. The defaults are bad for just about everybody, thus everybody is forced to customize whether or not they are advanced users.

> **Skripka said:**
> There are some buggy behaviors cited-but I'd first question the integrity of your LiveCD, as many of those (i.e. pen/external drive problems) I have never seen before.

Due to the CRC error problem, I questioned the integrity of my LiveCD as well. Consequently, I took my LiveCD to numerous different computers and ran the "verify CD" option on boot. The CD checks out. Further investigation leads me to conclude these issues are with the OS, not the installation of it.

> **Skripka said:**
> Ibex is less than a month old.  NO OS EVER was perfect when it was a month out the door.

Linux has been around since 1991. X11 has been around since the 80s. You'd think with *nix on the desktop being this old and Linux on the desktop being nearly as old, it'd be in a somewhat more usable state by now. Hell, even if you want to limit to a single distro, Ubuntu's been around since 2004 and in 4 years has still not managed to rival Windows or OS X in terms of user experience. I don't really think there are any excuses for this and I think we as a community need to stop being in denial about it before we can move on and collectively produce a polished product capable of rivaling the competition on the desktop.

> **Skripka said:**
> WinXP flopped-and everyon though it was a dumb idea.

Yeah, the most used OS in the history of humanity was a huge flop. Right.

> **Skripka said:**
> MacOS X.1,X.2, X.3, X.4, and X.5 wew ALL VERY buggy until version 10.x.3 or 4 (Experienced Mac OS users warn new adoptees to not expect stability for that long, BTW).

Not to the degree that Ubuntu and every other Linux distro has been buggy during its *entire lifespan*.

> **Skripka said:**
> It sounds like you want an OS perfectly suited for you without you, your abilities, and your aesthetics without having to raise a finger-tip of effort to get it.  Sorry, it does not exist.  Simple fact.  Linux has all the funcionality and tools to get it though, if you put some effort into making it.  

I've been using Linux on the desktop for a decade. I'm well accustomed to putting some effort into making it work. I've even contributed to open source projects on occasion. I'm also a hell of a lot more aware of how Linux is perceived by regular people than you appear to be. Attitudes like yours are one of the biggest reasons this OS isn't mainstream.

You and I, we'd continue to use Linux if we had to compile our own kernels. But what I really want is to see the elderly using it, and children. And people who aren't very computer savvy using it. It has nothing to do with what's best suited for me. Linux has been best suited for me for a very long time. I just want to make it best suited for people not as computer savvy as me too.

> **Skripka said:**
> When you write an OS for the lowest common denominator-no one with any computer skill will want to use it, or develop for it.

And once you realize you're wrong on this one, maybe my argument will start making sense to you. Windows and Mac OS X have much, much larger computer savvy user bases than Linux does. Even Mac OS X alone probably has more users "with computer skills" than Linux does. This sort of elitist argument that somehow Linux would be diminished if regular people could use it is both wrong and wholly counterproductive.

> **Mr. Picklesworth said:**
> Have you filed a bug for your external hard drive, by the way? The bug is in HAL, so make sure you put it at the right place. They are generally quite responsive to these sorts of misdetection bugs :)

Where can I file? I can make a quick bug report later. Should be relatively trivial to get the exact hardware specs. Also wouldn't be a bad idea to have some sort of feature in the OS somewhere to file bugs without having to know what the bug filing website is. They might get more reports that way.

> **Mr. Picklesworth said:**
> Still not convinced about disabling virtual desktops by default. Arguably, people have more trouble with iconifying windows, but once they learn the usefulness of that feature they do it all the time... (Except me; I just bump them to other desktops).

You know, I'm not wholly convinced either, even though it's my argument. But I can tell you one thing, the default out of the box experience favors multiple desktops too heavily. Being able to accidentally switch desktops a number of different ways is bad. I like that there are many ways to make use of this feature, but you've got to admit it's pretty damn confusing for less computer savvy users. The defaults should not be making it easy to accidentally trigger it. At the very least, the "scroll wheel over the desktop" method of switching desktops should be disabled.

---

### Post by aysiu on 2008-11-17
It should be mentioned that in Mac OS X, if you use the column view then long filenames get truncated in the middle.

---

### Post by Kethinov on 2008-11-17
Yeah, I mentioned that already. It's a much better user experience than just cutting it off whenever the space runs out because in the case of lots of filenames that all start with the same thing, at least it's possible to identify the files based on their endings.

It's also worth noting that of all my complaints, this is probably the most nitpicky. Compact view isn't even on by default, so this issue barely matters. But it was something I noticed so I figured it was worth mentioning.

---

### Post by aysiu on 2008-11-17
> **Kethinov said:**
> Yeah, I mentioned that already. It's a much better user experience than just cutting it off whenever the space runs out because in the case of lots of filenames that all start with the same thing, at least it's possible to identify the files based on their endings. I have never found the cutting off (whether in the middle or the end) at all helpful in file browsers. I really wish, regardless of platform, that UI developers would avoid this behavior altogether.

---

### Post by Kethinov on 2008-11-17
I tend to agree, which is why I prefer the list view in Windows Explorer which will widen the columns to accommodate the longest file.

However, usability studies have shown that if you have to cut off the text somewhere, it's statistically more likely to be effective if done in the middle. That's why Apple does it this way.

---

### Post by aysiu on 2008-11-17
I'm also a fan of the list view in Explorer (I use Windows at work).

What annoys me most about column view in Finder is that double-clicking on the column border doesn't automatically expand it so you can see the full filename. You have to manually drag the column wider with your mouse.

---

### Post by Skripka on 2008-11-17
> **Kethinov said:**
> All of the above, and despite what your post implied, these crowds are not mutually exclusive to target. As is done in Windows and Mac OS X, the correct strategy is to use defaults the lowest common denominator prefer and leave the customization up to the more advanced users. Linux has it backward. The defaults are bad for just about everybody, thus everybody is forced to customize whether or not they are advanced users.


I disagree. I like most of the KDE defaults, and I know many who do too.  My windows don't default to maximized, they never did as I recall.  I resize my windows, I see the entre window resize not just the outline window decor.  But that is KDE and not Gnome.  Of course, if one doesn't like it-it is quite easy to change.

[QUOTE=]
Yeah, the most used OS in the history of humanity was a huge flop. Right.
[/QUOTE]

Having used computers for as long as you have, surely you remember the overtures people were singing about XP when it initially came out-it wasn't really until SP1 that people started becoming reasonable accepting of it and its ways...People were clinging to their Windows 2000 like they do XP now.  When XP 1st came out, people thought it would be what Vista has turned out to be---now you have difficulty tearing it out of peoples cold dead hands after SP2 and SP3.  This is what I was speaking of-I apologize if it didn't come out as articulte as that.

[QUOTE=]
And once you realize you're wrong on this one, maybe my argument will start making sense to you. Windows and Mac OS X have much, much larger computer savvy user bases than Linux does. Even Mac OS X alone probably has more users "with computer skills" than Linux does. This sort of elitist argument that somehow Linux would be diminished if regular people could use it is both wrong and wholly counterproductive.
.[/QUOTE]

Most people chafe against either Windows or Mac. or both.  They try to be on size fits all.  I hate many of the GUI standards in OSX-and worse I can't change it at all (I know many who feel the same).  I think the Start menu before Vista's indexed search (which they stole from KBFX and Linux) to be one of the worst GUI interface designs in history; trying to find things in Control Panel in any Windows version is a counterintuitive nightmare (until you flat out memorize what is what) especially since each consecutive version of Windows changes what things are called.   People accept these things though for compatability though.  Not because they are good ideas.

 I hate Finder in Mac, and I find Explorer on Win to be avery inelegant tool (Folder view plasmoids and Dolphin are much more capable and better designed tools).  PS-mice should ALWAYS have more than 1 mouse button. :) 


The best one can do in writing as OS is have as many customizations as possible- to make things sane for the individual.  Trying to make a one-size-fits-all DE is a nightmare.  What is sane and reasonable for some people is backwards to others.   As exampled by the opines of multiple desktop switching on this thread.

---

### Post by Tamlynmac on 2008-11-17
> 
Kethinov
Two problems with this:

1. Don't you think that the fact that "most people" who use Ubuntu right now are changing the theme is some pretty strong evidence that it's a bad theme, and thus a bad default?

2. "If you don't like it, modify it" has been the Linux motto for a long time. It's one of the reasons Linux doesn't catch on. People want computers that, forgive the cliche, "just work." This includes them having sane defaults and looking attractive *out of the box.* The only reason Ubuntu does as well as it does is because competing distros are so much worse. That's pretty sad.

1. No I don't. The volume of available themes for Ubuntu/Linux is phenomenal. As I indicated each and every individual has the ability to modify/personalize their desktop. This in my opinion is one of the attractions to Ubuntu (OSS). I doubt that whatever theme Canonical used as a default would satisfy all users or even the majority.
2. The fundamental concept of OSS is flexibility. I suggest if an individual requires and is comfortable in a fixed environment they should seek alternatives outside the OSS community. I've installed Ubuntu on numerous systems for friends and family and generally they are inspired by their new found ability to customize the environment. It's an adventure in creativity. They actually become more familiar with the system as they personalize and I believe system confidence improves with interaction. You implication that the default theme should meet the expectations of the majority is fundamentally flawed, based on individual interpretation. I sincerely doubt that the majority of existing  individual users would agree on any one  theme.
 

 I would agree if the default theme was mandatory and permanent – as this would have an impact on all users. However, the option of customization is paramount to OSS and IMHO should never be altered. If an individual is comfortable in a fixed environment, then I would strongly recommend an alternative OS. As you indicate, one that just works for them. I don't believe Ubuntu is for everyone and the concept that any OS will function and meet the expectations perfectly OOTB on all systems for all people (IMO) is not realistic. Your statement that one of the primary reasons Ubuntu/Linux “doesn't catch on” (the ability to modify) is fundamentally why many users enjoy the OS. I for one don't wish to see Ubuntu corrupted by perception. Just so you know I'm not a computer geek or IT guru. We have five home systems counting 2 laptops and all five are running Hardy. No one in my immediate family is a computer geek and yet we all use this OS daily. From ages 7 to lets just say over 50. I find it amazing that all of us made the transition without any serious complications or issues. Each and everyone of us have personalized our desktop accordingly and truly enjoyed doing so.

---

### Post by Kethinov on 2008-11-17
> **Skripka said:**
> Trying to make a one-size-fits-all DE is a nightmare.  What is sane and reasonable for some people is backwards to others.

Not really. Certainly there's a "you can't please everybody" aspect to this business, but Windows and Mac OS X do a very good job of pleasing the vast majority of their users. That's why the vast majority of their users don't seek to change the themes, or most of the default settings.

Now keep in mind, most of the problems I pointed out in my original post are things that both Windows and Mac OS X do much the same way but differently from Ubuntu's default. If those two "very different" operating systems can agree on such things, doesn't that say a lot about them probably being good defaults that Linux should adopt too?

It's simply naive to talk about how much you personally hate Windows and Mac OS X's defaults to try and frame the issue as somehow being wholly subjective. Of course there's subjectivity involved, but the bottom line is what the global majority considers usable is what needs to be the default. And the global majority doesn't think that Linux' defaults are quite as usable as its competition. End of story.

> **Tamlynmac said:**
> 1. No I don't. The volume of available themes for Ubuntu/Linux is phenomenal. As I indicated each and every individual has the ability to modify/personalize their desktop.

People aren't changing their theme because there are so many available. They're changing their theme because they dislike the default. And when more people are changing the theme than keeping it, it's a good sign that it's a bad default.

> **Tamlynmac said:**
> I doubt that whatever theme Canonical used as a default would satisfy all users or even the majority. ... You implication that the default theme should meet the expectations of the majority is fundamentally flawed, based on individual interpretation. I sincerely doubt that the majority of existing  individual users would agree on any one  theme.

It does with Windows and Mac OS X users. See my responses above to Skripka.

> **Tamlynmac said:**
> I suggest if an individual requires and is comfortable in a fixed environment they should seek alternatives outside the OSS community. ... If an individual is comfortable in a fixed environment, then I would strongly recommend an alternative OS.

Charming. Otherwise, "if you want good defaults, don't use Linux." Yep, that's the key to making Linux a success.

> **Tamlynmac said:**
> I've installed Ubuntu on numerous systems for friends and family and generally they are inspired by their new found ability to customize the environment. It's an adventure in creativity. They actually become more familiar with the system as they personalize and I believe system confidence improves with interaction.

Cute. But lets take a step back from the lollipops for a moment and realize this is the equivalent of teaching someone how to mod their own car. Obviously, most people couldn't care less about car modding. They want their car to "just work." Most people feel the same way about computers too.

And if you're expecting some kind of hobbyist revolution that will sail all of Earth's population into a happy hacker (the Stallman sense of the word) utopia where everybody is hacking (the Stallman sense of the word) their OS because customizing things is fun, you'll be sorely disappointed.

The only people who bother with that are computer enthusiasts like you and I. The average user wants usable defaults and a computer that "just works."

> **Tamlynmac said:**
> the option of customization is paramount to OSS and IMHO should never be altered. Your statement that one of the primary reasons Ubuntu/Linux “doesn't catch on” (the ability to modify) is fundamentally why many users enjoy the OS.

I am not suggesting removing your ability to customize things. I'm suggesting changing the defaults so ordinary users aren't forced to experience what you enjoy so much. Because most of them won't enjoy it. Believe it or not, most people don't get their jollies customizing mouse behavior, changing themes, and rearranging toolbars.

> **Tamlynmac said:**
> I don't believe Ubuntu is for everyone

In its present state, you're absolutely right. If the things I mentioned in my original post are fixed, along with probably quite a few more things, then it can be. Ubuntu is Linux for "human beings." I'd say that our ultimate goal here is that it should be for everyone.

> **Tamlynmac said:**
> and the concept that any OS will function and meet the expectations perfectly OOTB on all systems for all people (IMO) is not realistic.

Well then, somebody call up Mark Shuttleworth and tell him to change Ubuntu's slogan from "Linux for human beings" to "Linux for people that like to customize stuff." Clearly he's in the wrong business. ;)

---

### Post by cardinals_fan on 2008-11-17
> **Kethinov said:**
> Not really. Certainly there's a "you can't please everybody" aspect to this business, but Windows and Mac OS X do a very good job of pleasing the vast majority of their users. That's why the vast majority of their users don't seek to change the themes, or most of the default settings.

No, that's because the vast majority of their users don't actually care about the window borders on a computer that they just use for web browsing and checking email.

---

### Post by Skripka on 2008-11-17
> **Kethinov said:**
> Not really. Certainly there's a "you can't please everybody" aspect to this business, but Windows and Mac OS X do a very good job of pleasing the vast majority of their users. That's why the vast majority of their users don't seek to change the themes, or most of the default settings.

Now keep in mind, most of the problems I pointed out in my original post are things that both Windows and Mac OS X do much the same way but differently from Ubuntu's default. If those two "very different" operating systems can agree on such things, doesn't that say a lot about them probably being good defaults that Linux should adopt too?

It's simply naive to talk about how much you personally hate Windows and Mac OS X's defaults to try and frame the issue as somehow being wholly subjective. Of course there's subjectivity involved, but the bottom line is what the global majority considers usable is what needs to be the default. And the global majority doesn't think that Linux' defaults are quite as usable as its competition. End of story.



You're missing the point though.  People don't use Windows and Internet Explorer because they are GREAT ways of doing things or great tools for said.  

They use them because they are OEM installed on a vast majority of computer hardware sold--and because they just want something that turns on and lets them type word processor docs and surf Facebook or Myspace or Youtube.  That is your average user.  They are niether pleased nor disppleased on the whole--they don't notice the box is even there.  And as both Microsoft and Mac take a "Our way or the Highway" approach to configuration--people knuckle up and learn to deal with really stupidly designed interfaces.  Both HAVE no themes, both have little to no customization possibilities.

If people had to partition and install their own OS after purchasing a computer, Microsoft would go out of business quick.



Just because both Evil Empires have really stupid interface defaults doesn't mean Linux should too.  Much of it IS subjective-both Apple and Microsoft have two VERY different visions of how a desktop environment should work.  They share some commonalities of functions and concepts-but the executions are VERY different.  Should Linux drop support for hardware older than 3 years for each successive version of their OS too?  

Tabbed browsing was around what 10 years before it became a Safari and Microsoft default?  Mac has taken up virtual desktops-and odds are Microsoft will soon too, I'd wager-it is a GREAT tool for anyone working with multiple windows of different softwares on any kind of project. ...I'd wager Apple's Dashboard and the Plasma equivalent on Vista both existed in Linux far before they became defaults on either....the same with 64-bit computing.

---

### Post by Tamlynmac on 2008-11-17
Kethinov

"most people couldn't care less about car modding"
"The only people who bother with that are computer enthusiasts like you and I. The average user wants usable defaults and a computer that "just works.""
"It does with Windows and Mac OS X users."
"Believe it or not, most people don't get their jollies customizing mouse behavior, changing themes, and rearranging toolbars."

You continually speak for "others" and I would personally appreciate it if you would substantiate these statements with numbers or actual facts - links showing where you acquired this information and based on what poll or questionnaire. Especially terms like "most people" as I doubt either of us can actually speak for "most people". I certainly can not and would not.

Or are you just making assumptions based on your own personal experiences and interactions? If so, please define that.

---

### Post by pmwhite on 2008-11-18
I have to agree about usability. I too was able to get it installed (after I tried a few things) but the bottom line for most people is: 'how simple is this to use.'

I know people who have been using computers for years and seem to have little in the way of issues they can't resolve by themselves and if they can't then they probably know someone who can. This does not seem to be the case with ubuntu. It's not a true criticism of the OS but just a general observation. I have read often in these forums that some of the posters are causing themselves issues by wanting to stick to doing things in a particular way. This is likely true but people are creatures of habit and shouldn't be faulted for wanting to stick to the 'tried and true way'. 

On wikipedia the term usability in human-computer interopability is defined as: 'In human-computer interaction...usability usually refers to the elegance and clarity with which the interaction with a computer program...is designed'. 

I don't find ubuntu that user friendly. Yes I can find answers to questions I have but the average user doesn't want to have to search for answers and feels (rightly or wrongly) that they shouldn't have to. 

The bottom line for me is simply that while a good OS for techies ubuntu is not always a great choice (aside from cost) for an average user. 


Just my 2 cents worth so don't bother flaming me.

---

### Post by Skripka on 2008-11-18
> **pmwhite said:**
>  Yes I can find answers to questions I have but the average user doesn't want to have to search for answers and feels (rightly or wrongly) that they shouldn't have to. 



No they shouldn't.  

On the other hand when your options are waiting on a call-help line from a manufacturer on hold for hours on end, that you have to pay a warranty fee to get.....or a resource like this forum here that is free to use.  It is a no brainer which is better

---

### Post by Tamlynmac on 2008-11-18
> Skripka
I don't find ubuntu that user friendly. Yes I can find answers to questions I have but the average user doesn't want to have to search for answers and feels (rightly or wrongly) that they shouldn't have to. 

The average user? I doubt any new user will be 100% comfortable with an OS they've never used. It takes time and learning to become familiar with a new software package. The more familiar we get with software the more user friendly it should become (hopefully). I doubt many of us that used Windows for the first time found it friendly, until we became familiar with it's operations. IMO evaluating user friendliness should be based on how rapidly someone can interact with the software and if the functions they require are available and easy to use. 

What is the benchmark for user friendly (a hammer)? Hopefully, someone can answer, as I don't know. Is comparison the only way to benchmark "user friendly"?

I believe terms like "user friendly" can only apply after we become familiar with the system. It's been my experience with individuals installing Ubuntu for the first time, they found it extremely friendly after learning how to use it. Like many things in life an indoctrination period is required and a learning curve applies. It's also been my experience that the learning curve differs for each individual.

---

### Post by aysiu on 2008-11-18
> **pmwhite said:**
> 
I know people who have been using computers for years and seem to have little in the way of issues they can't resolve by themselves I know people like this, too, but they're in the minority.

The vast majority of people I know (personally or professionally) cannot handle their own computer problems (and, yes, they are Windows and Mac users, not Ubuntu users). They ask me for help or the tech department at work for help. Or they pay the Geek Squad for help.

If you believe most people can solve their own problems, try running a school without a tech department or helpdesk. The school will implode.

>  and if they can't then they probably know someone who can. Oh, whoops. Missed this part. That just goes without saying, though, doesn't it? If the vast majority of Windows users know other Windows users, they're bound to find someone who's knowledgeable about Windows. And all Mac users I know also know Mac users they can turn to for help. I am the only Ubuntu user I know in person (not online).

That doesn't mean Ubuntu as an OS is deficient in some way. It just means that it's not widely used, and so the best way to find other users is online in a help forum or mailing list.

---

### Post by hyper_ch on 2008-11-20
> **init1 said:**
> Yeah, I've noticed a few. For example, if I download a .deb and select open, it give me an error. It works fine if I download it and then run it, but I think it might confuse some beginners.
Why should a beginner download a .deb file from some place?

> **pmwhite said:**
> On wikipedia the term usability in human-computer interopability is defined as: 'In human-computer interaction...usability usually refers to the elegance and clarity with which the interaction with a computer program...is designed'. 

I don't find ubuntu that user friendly. Yes I can find answers to questions I have but the average user doesn't want to have to search for answers and feels (rightly or wrongly) that they shouldn't have to.
I find Linux/Ubuntu is way more user friendly than Windows or OS X. However there is only one way to find out which one is the most user friendliest:
(1) Get a group of xxx people from very low to very high age
(2) Erase all their memories with regard to computer
(3) Give them a properly setup system and a task list
(4) Measure how long it takes them to accomplish that
(5) Erase their computer memories again and redo step 3 and 4 with the other two systems

pmwhite: You can't get out of Windows way... you will get in contact and you will familarize yourself to a degree with it. When you then start using something else it is not "userfriendly" for you because of your previous experience.

---

### Post by Tamlynmac on 2008-11-22
> hyper_ch
(2) Erase all their memories with regard to computer
(5) Erase their computer memories again and redo step 3 and 4 with the other two systems

I would really appreciate it if you would post the print and operational manuals for the device that you would use to accomplish this. I have a number of situations where that device could really benefit me. Assuming it can be tuned to erase specific memories other than just computer.
:lolflag:

---

### Post by nuken on 2008-11-22
I can honestly say that 8.1 has surpassed my expectations. the 64-bit has came so far in just a few years. Some linux to windows issues are still there, but none that are major. Ubuntu has set the standard for linux distros. Quick, easy install. Runs fast and error free. The only issues I really have are not the fault of linux but of Microsoft. Office would be nice to have on Linux and network printing to a Windows machine sucks. Open Office works fine for most every need I have at home, but not at work. Non the less, Ubuntu is great and I appreciate all the work done by the community...

---

### Post by frankleeee on 2008-11-22
Could you define "average user" and the slide rule used to measure it. I have a Dell inspiron 4100 the only problem I have had is the network manager which was easily fixed. I have the advantage of never having used anything but Linux so I don't have any expectations of any other operating system. I am all to average in the end.;)

---

### Post by Sef on 2008-11-22
>  				 				**[B]Re: Ubuntu 8.10 still fails the "average user test"** [/B] 			
 			

The average user buys their system preinstalled and never installs another one.

---

### Post by 3rdalbum on 2008-11-22
Average user where? In India, many people do their very first computer classes on Linux.

---

### Post by frankleeee on 2008-11-22
> **Sef said:**
> The average user buys their system preinstalled and never installs another one.

Exactly. ;)

---

### Post by Skripka on 2008-11-22
> **3rdalbum said:**
> Average user where? In India, many people do their very first computer classes on Linux.

Not here in NowHere, USA.  It is all Windows, or increasingly Mac.

---

### Post by Tamlynmac on 2008-11-23
> Skripka
Not here in NowHere, USA.  It is all Windows, or increasingly Mac. 	

Obviously, not all in NowHere - Unless you don't consider yourself a resident.LOL

I truly enjoyed your sign. Just how dumb have we become??? That's scary.... The inference is that somewhere it rains "dry water"....OMG
:lolflag:

---

### Post by smithbt5 on 2008-11-25
Yep - Well it looks like Windows Vista failed the average user test too.

---

### Post by JinStevens on 2008-11-25
> **smithbt5 said:**
> Yep - Well it looks like Windows Vista failed the average user test too.

It fails on if you're trying to install it on older hardware.  I'd say it would pass if you get it pre-installed.

My 68 year old parents like Vista. They bought a Dell tower and had me hook it up. They liked that Vista picked up and installed drivers for their printer and allowed them to fairly painlessly connect their digital camera to the computer to transfer pictures to the hard drive.

My parents:

* don't know how to update their own drivers (nor would they ever update any driver as long as the current one worked reasonably well)
* don't know how to connect the computer to their ISP/cable modem (I did that)
* does know how to hook up their external monitor to the back of the computer and plug the computer's power cord into a surge protector
* primarily use the computer for Internet browsing, email and word processing
* on occasion will put in a music CD or movie DVD into the DVD player
* couldn't understand the purpose behind Vista's User Access Control and had me disable it immediately

As long as Ubuntu came pre-installed, I think my parents could use it. However, I couldn't see them changing to Ubuntu because what they have works for them.

---

### Post by mrboojive on 2008-11-25
The average Ubuntu user is a power user, or, at the very least, someone who wants to be a power user. I don't think tap to click or multiple desktops are "power user" features, but even if they are, it is entirely appropriate to have some power user features enabled by default.

---

### Post by sneeks on 2008-11-25
i think at the end of the day,its horses for courses,and as many have said the average user just wants to surf,mail and maybe play either low end games on-line or play the latest one's.
now even though it pain's me to say it,xp and sometimes vista does this flawlessly.
and i say again as some have said if Linux was pre-installed we would have no problem,its just that the average user has no choice whatsoever.
they go to a pc shop and its there already,the pain come to them over the time of ownership,and it's the cash type of pain.
if a vista owner does not like it,they can plead with the supplier for a go back disk for xp,not saying there will be any drivers eaisly available.
so i get these people calling me and have to charge them not only for my time but also a new OS.
as for dell compatibility,its never been that great,and some times the stuff that you should have inside your pc is not the one you should have.
now i know this for a fact as i work closely with a dell reseller,and sometimes what you see is not what you get.(read over your contract,bill of sale,etc.)
now, i have installed ibex on a dell latt d 620,and have not had any of the bad bugs,etc you seem to have,yes some of the options are not to your likeing but the idea of Linux is that you can change things to suit yourself.
another point is that ibex is a learning release,its not a LTS,hardy is the stable one,and my advice to you would be to stick to hardy for at least 4-6 months,so they can iron and starch it.
but also please do file the bugs you find as it will ultimately help us all to have a Linux distro that some of the masses will consider and hopefuly will get some big boys pre-installing it. 
that was my 10 bobs worth.
im outta here....peace to all except bill..

---

