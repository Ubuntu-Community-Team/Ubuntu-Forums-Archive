---
title: "The Super KDE 4.6 thread"
date: 2010-12-01
forum: The Cafe
---

### Post by sandyd on 2010-12-01
KDE 4.6 is slated to be released January 26th.

Current improvements
[Beta 1]("http://www.kde.org/announcements/announce-4.6-beta1.php")
[Beta 2]("http://www.kde.org/announcements/announce-4.6-beta2.php")
[RC 1]("http://www.kde.org/announcements/announce-4.6-rc1.php")
[RC 2]("http://www.kde.org/announcements/announce-4.6-rc2.php")
Beta 2 will be released on Dec 8th
RC 1 will be released on Dec 22d
RC 2 will be released Jan 5th

Im currently using it from the Beta/RC packages, and aside from a few bugs, performance seems to have increased expoentially. Also, no 3 frame animations during minimizing/maximizing windows:P

Most things are quite smooth, except if you choose a transparent theme for your window borders, it will lag horribly.
Ive fixed the nolag demo, [s]should be up in a sec... (youtubes choking on vorbis again...)[/s]
[http://www.youtube.com/watch?v=wNZvnQXczpU](http://www.youtube.com/watch?v=wNZvnQXczpU)

---

### Post by aaaantoine on 2010-12-01
I remain unconvinced by that video, but I'll take your word for it.

4.5 broke compositing for me with my drivers at the time.  A couple days ago I ran an update to Mesa 7.9 and the Gallium based rendering (r300g) seemed to help, but at the moment it's running too jerky for me.

I prefer to use non-composited kwin for now, at least on this computer, at least until everything is better optimized.

(As a side note, I'm glad Gallium is finally in a usable state for r300.)

---

### Post by czr114 on 2010-12-01
While I don't personally use the KDE suite due to resource usage, excessive bells and whistles, the lack of some extensions, and Firefox being native GTK, I have heard great things about the latest Qt 4.7.

I've always been a GNOME loyalist.

Is it true what they're saying about the recent improvements to Qt finally eclipsing GTK+ 2 in speed and resource efficiency? If so, I might have to give a lightened KDE another chance.

---

### Post by sandyd on 2010-12-01
> **czr114 said:**
> While I don't personally use the KDE suite due to resource usage, excessive bells and whistles, the lack of some extensions, and Firefox being native GTK, I have heard great things about the latest Qt 4.7.

I've always been a GNOME loyalist.

Is it true what they're saying about the recent improvements to Qt finally eclipsing GTK+ 2 in speed and resource efficiency? If so, I might have to give a lightened KDE another chance.

Its much lighter, esp if its compiled against QT 4.7.1
I seem to be having a memory leak somewhere with QT 4.7.0, probably due to one of the darwin patches that were applied.

If you use firefox 4, you won't notice much of a difference, they seem to have improved the KDE integration somewhat.

---

### Post by aaaantoine on 2010-12-01
Eh, maybe?

htop says I'm using 1187MB, and I'm explicitly running Firefox with 6 tabs open, Pidgin, Akregator, Dolphin, and Kate.  I have the globe set up as my desktop background (that *can't* be light...), and I'm sure there's plenty of KDE stuff going on in the background as well.

It's not exactly conservative by my measure, but I suppose it could be worse.

---

### Post by NightwishFan on 2010-12-01
Super thread go! :) I recently have gone back recommending KDE as well as Gnome to interested parties. Great job KDE team.

---

### Post by czr114 on 2010-12-01
> **sandyd said:**
> Its much lighter, esp if its compiled against QT 4.7.1
I seem to be having a memory leak somewhere with QT 4.7.0, probably due to one of the darwin patches that were applied.

If you use firefox 4, you won't notice much of a difference, they seem to have improved the KDE integration somewhat.
Interesting. Do you mean much lighter than GTK+ 2 or lighter than older QT as of the 4.7.1 branch?

Are you a KDE dev?

FF4 is supposed to be bypassing widget toolkits and go directly to hardware accelerated rendering, so yes, it should be much better in that regard.

I've got Kubuntu torrenting now. It's definitely worth trying out. I'll see if I can get it to function like lightweight GNOME panels. I'm not really loyal to either suite's integrated applications, because I'm using Firefox/Thunderbird/OO/Pidgin as replacements for the bundled apps, so there would be no transition issues there.

Off the top of your head, do you know of any shell extension frontend for GPG like seahorse-plugins in GNOME?

---

### Post by TheNessus on 2010-12-01
> **sandyd said:**
> KDE 4.6 is slated to be released January 26th.

Current improvements
[Beta 1]("http://www.kde.org/announcements/announce-4.6-beta1.php")

Beta 2 will be released on Dec 8th
RC 1 will be released on Dec 22d
RC 2 will be released Jan 5th

Im currently using it from SVN, and aside from a few bugs, performance seems to have increased expoentially. Also, no 3 frame animations during minimizing/maximizing windows:P

Most things are quite smooth, except if you choose a transparent theme for your window borders, it will lag horribly.

Videos
[Minimizing/Maximizing no lag!]("http://www.youtube.com/watch?v=Ci_jG7T4FFw")

[Window Resizing no lag!]("http://www.youtube.com/watch?v=wvS_Zmie8JI")
I don't get it. The video (first one, didnt look at second) shows a lagging minimizing/maximizing.

---

### Post by aaaantoine on 2010-12-01
> **TheNessus said:**
> I don't get it. The video (first one, didnt look at second) shows a lagging minimizing/maximizing.

I think maybe if the videos were posted with frame rate that'd be more useful to me.

On my laptop, kwin compositing caps at 30fps.  Not pleasant, especially since it typically drops well below that.

---

### Post by sandyd on 2010-12-01
im having some issues with gallium r600.
recording sucks more than the classic driver.

Not suprising since all parts of the r600 driver are still WIP.

---

### Post by sandyd on 2010-12-01
> **czr114 said:**
> Interesting. Do you mean much lighter than GTK+ 2 or lighter than older QT as of the 4.7.1 branch?
**Its lighter than the previous verison of QT. Ive never used QT 4.7.0, nor gnome, so I can't comment.**

Are you a KDE dev?

FF4 is supposed to be bypassing widget toolkits and go directly to hardware accelerated rendering, so yes, it should be much better in that regard.

I've got Kubuntu torrenting now. It's definitely worth trying out. I'll see if I can get it to function like lightweight GNOME panels. I'm not really loyal to either suite's integrated applications, because I'm using Firefox/Thunderbird/OO/Pidgin as replacements for the bundled apps, so there would be no transition issues there.

Off the top of your head, do you know of any shell extension frontend for GPG like seahorse-plugins in GNOME?
**kgpg**


No,im not a KDE dev, im a person who has an interest in KDE, which is one of the reasons why I compile it from source code.

I get 510mb at desktop, but that might be beacause compiling from source optimizes the program for the specific computer.

---

### Post by urukrama on 2010-12-01
> **aaaantoine said:**
> htop says I'm using **1187MB**, and I'm explicitly running Firefox with 6 tabs open, Pidgin, Akregator, Dolphin, and Kate.  

:shock:

Is that what DEs use these days?

---

### Post by TheNessus on 2010-12-01
> **urukrama said:**
> :shock:

Is that what DEs use these days?

No, just Vista.                            And KDE4.5

---

### Post by Shining Arcanine on 2010-12-01
> **TheNessus said:**
> No, just Vista.                            And KDE4.5

If you have enough tabs open, you can get Chromium to use 2GB of RAM. That happens to me all the time. Thankfully, I have 8GB of RAM on my desktop. 8GB of RAM is nice because it lets me compile my entire OS, including Open Office, in a tmpfs.

---

### Post by sandyd on 2010-12-01
> **Shining Arcanine said:**
> If you have enough tabs open, you can get Chromium to use 2GB of RAM. That happens to me all the time. Thankfully, I have 8GB of RAM on my desktop. 8GB of RAM is nice because it lets me compile my entire OS, including Open Office, in a tmpfs.

oh, btw, don't upgrade to kde 4.6 since your using gentoo.

a LOT of GTK apps such as VLC, Opera will take a LONG time to open any file browser dialog due to 
```

KGlobal::locale::Warning your global KLocale is being recreated with a valid main component instead of a fake component

```
Just what I wanted.............

---

### Post by Shining Arcanine on 2010-12-01
Why would Gentoo have anything to do with an issue in KDE 4.6?

Also, Opera is a Qt application.

---

### Post by aaaantoine on 2010-12-01
> **urukrama said:**
> :shock:

Is that what DEs use these days?

Guess so.

If I close everything my RAM usage goes down to 836 MB.  Still a whole lot.

If I switch from the globe background to a straight image... RAM usage goes up to 850 MB, for some reason.

I know; it's a lot.  But I have a lot of free RAM to spare.  I'll let the devs still working with 1GB RAM figure out how to optimize for that case.

---

### Post by inobe on 2010-12-01
i have been testing since 3.5, every release is pleasing, keep em coming ;)

---

### Post by sandyd on 2010-12-01
> **Shining Arcanine said:**
> Why would Gentoo have anything to do with an issue in KDE 4.6?

Also, Opera is a Qt application.

I think that theirs a patch in the **official** beta 1 release, because no one is getting it there.

However, the patch is obviously not applied in the KDE overlays, which is the only way to get 4.6 (kde-meta-4.5.80). Im using that overlay. WWhich means no vlc for me... (except opening the file by right click)

---

### Post by Dustin2128 on 2010-12-01
I would try it, but I am suffering from a severe case of laziness.

---

### Post by inobe on 2010-12-01
> **Dustin2128 said:**
> I would try it, but I am suffering from a severe case of laziness.

i know the feeling, working 11 hours per day, coming home to family, take kids to park, have fun, get back home to spend quality time with the wife, maybe help her wash the dishes and various other things, now it's 11:03 pm, an hour and 1/2 till i hop in the sack, till then i will devote my remaining time testing, about 12:30 i will be out like a lite only to awake and repeat at 5:30 am :P

---

### Post by oobuntoo on 2010-12-01
> **Shining Arcanine said:**
> Why would Gentoo have anything to do with an issue in KDE 4.6?

Also, Opera is a Qt application.

VLC is also a Qt app.

---

### Post by NightwishFan on 2010-12-02
Also, I think there is no way KDE would require that much ram. Kubuntu 10.10 (KDE 4.5?) runs in a VM with 386mb of RAM.

---

### Post by CraigPaleo on 2010-12-02
> **NightwishFan said:**
> Also, I think there is no way KDE would require that much ram. Kubuntu 10.10 (KDE 4.5?) runs in a VM with 386mb of RAM.

It's my understanding that KDE uses more shared libraries but apps like System Monitor count the processes sharing them individually. 

If you run the *free -m* command it won't take this into account. It'll subtract cashed memory but shared memory is always 0. I don't know why. 

If you run the *top* command, it'll show the individual processes using shared memory in the SHR column but I have yet to find a way to find out how much is actually being shared and counted multiple times. 

At any rate, you're actually using much less ram than you're being told.

---

### Post by sandyd on 2011-01-11
KDE 4.6 RC2 released!

---

### Post by ilovelinux33467 on 2011-01-11
> **sandyd said:**
> KDE 4.6 RC2 released!

Running it on openSUSE 11.3. It rocks. Everything is fast, stable. Really happy. Can't wait to final release of KDE 4.6 on the 26th of January! :D

---

### Post by sandyd on 2011-01-11
> **oobuntoo said:**
> VLC is also a Qt app.
have fun :D
[https://bugs.kde.org/show_bug.cgi?id=260719](https://bugs.kde.org/show_bug.cgi?id=260719)

---

### Post by sandyd on 2011-01-12
bump

---

### Post by NightwishFan on 2011-01-12
> **sandyd said:**
> bump

Come on guys this is a super thread we need at least 10 pages! :)

---

### Post by Pogeymanz on 2011-01-12
You can't just throw out RAM usage numbers without stating how much RAM your machine has.

Have you ever noticed that some people report KDE using 1GB RAM, yet KDE will still run on a computer that has less than 1GB RAM?

Memory usage is like a gas: it expands to fit its container.

---

### Post by NightwishFan on 2011-01-12
```
Memory usage is like a gas: it expands to fit its container.
```

That is a good way to put it.

---

### Post by DeadSuperHero on 2011-01-13
> **sandyd said:**
> Its much lighter, esp if its compiled against QT 4.7.1
I seem to be having a memory leak somewhere with QT 4.7.0, probably due to one of the **darwin patches** that were applied.

> **darwin patches**

[SIZE="2"]> **darwin patches**[/SIZE]

[SIZE="5"]> **darwin patches**[/SIZE]

[SIZE="7"]> **darwin patches**[/SIZE]

KDE's available for [Darwin]("http://en.wikipedia.org/wiki/Darwin_(operating_system)") these days?

---

### Post by kaldor on 2011-01-13
> **DeadSuperHero said:**
> [SIZE="2"][/SIZE]

[SIZE="5"][/SIZE]

[SIZE="7"][/SIZE]

KDE's available for [Darwin]("http://en.wikipedia.org/wiki/Darwin_(operating_system)") these days?

I don't get the point of supporting Darwin.

---

### Post by Roasted on 2011-01-13
Will KDE ever be stable enough to use?

*ducks*

---

### Post by aaaantoine on 2011-01-13
> **Pogeymanz said:**
> You can't just throw out RAM usage numbers without stating how much RAM your machine has.

Have you ever noticed that some people report KDE using 1GB RAM, yet KDE will still run on a computer that has less than 1GB RAM?

Memory usage is like a gas: it expands to fit its container.

Well alrighty.  There are two common variables to take into account that may affect total RAM usage on my KDE laptop.  I failed to report total RAM because it's in my sig, but that may not have been perfectly clear.

I am running KDE on...

1. Arch Linux x86_64.
2. A laptop with 4GB RAM.

The numbers I read off were from free -m.  Right now I'm on my Ubuntu 10.10 i386 desktop, which is presently using... 1064MB.  But, looking at my memory monitor at the top, I think that includes the cache.  Here, have a look:
```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          3275       1064       2210          0        108        506
-/+ buffers/cache:        449       2826
Swap:         1610          0       1610

```So maybe I was including cache for the KDE numbers as well, which would explain why the RAM usage went *up* when I switched my desktop wallpaper from Globe to image.  If I can remember later, I'll post the complete free -m from a fresh KDE startup.

---

### Post by Spice Weasel on 2011-01-13
> **Roasted said:**
> Will KDE ever be stable enough to use?

*ducks*

It was, but they killed it with KDE4. :(

*ducks*

---

### Post by CraigPaleo on 2011-01-13
> **Roasted said:**
> Will KDE ever be stable enough to use?

*ducks*

KDE is marked for life because of 4.0 - 4.3. 
It's like the person who tried linux 10 years ago and thinks it's the same thing today. 

I've had no problems with KDE since 4.4. 

I installed the 4.6 RC yesterday and had one plasma crash when i was tinkering with the activities button. The good thing is that it didn't effect any of my open windows. Plasma simply restarted itself in about two seconds along with a bug report dialog. But that's acceptable for an RC.

---

### Post by CraigPaleo on 2011-01-13
> **kaldor said:**
> I don't get the point of supporting Darwin.

KDE aims to be cross-platform. It's being ported to Mac OS X and Windows but neither is complete.

---

### Post by DeadSuperHero on 2011-01-13
> **Spice Weasel said:**
> It was, but they killed it with KDE4. :(

*ducks*

It's actually been shockingly good on my laptop, both in stability and speed.

---

### Post by ilovelinux33467 on 2011-01-13
I find the current versions of KDE4 extremely stable to use (SC 4.4, SC 4.5, SC 4.6) - More stable than any other desktop environment in fact :)

KDE SC 4.6 release is getting closer - Can't wait!!! :D

---

### Post by ilovelinux33467 on 2011-01-13
> **CraigPaleo said:**
> KDE aims to be cross-platform. It's being ported to Mac OS X and Windows but neither is complete.

One of the reasons I like KDE so much - it aims to be cross-platform :D

---

### Post by BrokenKingpin on 2011-01-13
So I just tried KDE 4.5 for the first time since 4.2 (currently a Gnome user). I have to say I am liking it a fair bit. It performs great on my low powered netbook, even with KWin effects on. I am looking forward to 4.6... might even drag me away from Gnome eventually (especially with Gnome 3 around the corner).

---

### Post by CraigPaleo on 2011-01-13
> **BrokenKingpin said:**
> So I just tried KDE 4.5 for the first time since 4.2 (currently a Gnome user). I have to say I am liking it a fair bit. It performs great on my low powered netbook, even with KWin effects on. I am looking forward to 4.6... might even drag me away from Gnome eventually (especially with Gnome 3 around the corner).

There's a netbook GUI built in. It's in the System Settings under Workspace Behavior, Workspace, Workspace Type. But if you don't like Gnome 3, you might not like the netbook option.


__________________
_**Pardus at [Distrowatch]("http://distrowatch.com/pardus")**_

---

### Post by Dustin2128 on 2011-01-13
I think I'm ready to try it out. Any clue how one would upgrade from slack's 4.5?

---

### Post by CraigPaleo on 2011-01-13
> **Dustin2128 said:**
> I think I'm ready to try it out. Any clue how one would upgrade from slack's 4.5?

I've never used Slack but this may help. [http://slackblogs.blogspot.com/2011/01/kde-46-rc-2-released.html](http://slackblogs.blogspot.com/2011/01/kde-46-rc-2-released.html)

---

### Post by themarker0 on 2011-01-13
I run it with PC-BSD flawlessly.

---

### Post by ilovelinux33467 on 2011-01-13
> **Dustin2128 said:**
> I think I'm ready to try it out. Any clue how one would upgrade from slack's 4.5?

I also found this searching google. I haven't tried slackware so I don't know if it works or not:
[http://alien.slackbook.org/blog/kde-4-6-second-release-candidate/]("http://alien.slackbook.org/blog/kde-4-6-second-release-candidate/")

---

### Post by Pogeymanz on 2011-01-13
So, this cross-platform thing. Would KDE run on top of the default Windows/OSX interface? That would be horrible, but I can't imagine that Apple or Microsoft wrote the OS to allow other interfaces than the default.

Or are we just talking about the KDE app suite?

---

### Post by ilovelinux33467 on 2011-01-13
> **Pogeymanz said:**
> So, this cross-platform thing. Would KDE run on top of the default Windows/OSX interface? That would be horrible, but I can't imagine that Apple or Microsoft wrote the OS to allow other interfaces than the default.

Or are we just talking about the KDE app suite?

On Windows you can run KDE Plasma as well as KDE apps. Not sure about Mac.

---

### Post by smellyman on 2011-01-13
> **DeadSuperHero said:**
> It's actually been shockingly good on my laptop, both in stability and speed.

it is for me too, up until the point kwin crashes

---

### Post by CraigPaleo on 2011-01-13
> **ilovelinux33467 said:**
> On Windows you can run KDE Plasma as well as KDE apps. Not sure about Mac.

Correct. KDE can be set as the default shell in Windows. It can even be set for one user with no effect on the other users accounts. I don't think the Mac port is quite there yet.

If you don't use KDE, you can still run the apps. What's awesome is that they use the native widgets so they blend right in. 

Amarok on OS X. 

[IMG]http://amarok.kde.org/amarokwiki/images/8/8c/AmarokX_osx_style.jpg[/IMG]

---

### Post by BrokenKingpin on 2011-01-14
> **CraigPaleo said:**
> There's a netbook GUI built in. It's in the System Settings under Workspace Behavior, Workspace, Workspace Type. But if you don't like Gnome 3, you might not like the netbook option.
Yeah the netbook option was on by default (I guess it figured out it was on a netbook). I played with it a bit, but soon changed to the default desktop settings and am really enjoying that. I think this is where Gnome 3 is going to be lacking... there will be no one click to get my normal desktop back.

---

### Post by RiceMonster on 2011-01-14
> **Pogeymanz said:**
> So, this cross-platform thing. Would KDE run on top of the default Windows/OSX interface? That would be horrible, but I can't imagine that Apple or Microsoft wrote the OS to allow other interfaces than the default.

Or are we just talking about the KDE app suite?

Actually, you can replace the explorer shell on Windows. There have been many third party shells written, such as litestep, SharpEnviro or bb4win.

---

### Post by Roasted on 2011-01-14
Has anybody tried KDE 4.6 on a netbook? How has it done?

---

### Post by BrokenKingpin on 2011-01-14
> **Roasted said:**
> Has anybody tried KDE 4.6 on a netbook? How has it done?
I can't speak for 4.6, but I was surprised at how well 4.5 ran on my netbook.

---

### Post by Pogeymanz on 2011-01-14
> **RiceMonster said:**
> Actually, you can replace the explorer shell on Windows. There have been many third party shells written, such as litestep, SharpEnviro or bb4win.

Oh, I had no idea. I assumed that those all ran on top of explorer. Thank you for clearing that up for me.

<OFFTOPIC>
Does that mean it would be quite feasible to remove all of Explorer from Windows?
</OFFTOPIC>

---

### Post by cguy on 2011-01-15
I tried to install it myself.
I added the kubuntu beta backports ppa, ran a "sudo apt-get update", then "sudo apt-get upgrade".

Also tried the GUI stuff.
No updates available...

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by cguy on 2011-01-15
I tried to install it myself.
I added the kubuntu beta backports ppa, ran a "sudo apt-get update", then "sudo apt-get upgrade".

Also tried the GUI stuff.
No updates available...

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Why is this?

---

### Post by cguy on 2011-01-15
Oh, and I'm using Lucid

---

### Post by Spice Weasel on 2011-01-15
> **Pogeymanz said:**
> <OFFTOPIC>
Does that mean it would be quite feasible to remove all of Explorer from Windows?
</OFFTOPIC>

Yep! You can completely remove Internet Explorer +  Explorer with this program:

[http://www.litepc.com/](http://www.litepc.com/)

---

### Post by Spice Weasel on 2011-01-15
> **Pogeymanz said:**
> <OFFTOPIC>
Does that mean it would be quite feasible to remove all of Explorer from Windows?
</OFFTOPIC>

Yep! You can completely remove Internet Explorer +  Explorer with this program:

[http://www.litepc.com/](http://www.litepc.com/)

Microsoft like to pretend it isn't possible on XP and lower.

---

### Post by cguy on 2011-01-15
OK, it was fairly obvious why I had that problem, but I had a hard time accepting it: no KDE 4.6 [RC2] for Lucid; only for Maverick.

I ended up upgrading the distro (a hard decision to make; I initially intended to stay on Lucid for at least 1.5 years) and now I'm installing KDE 4.6 RC2.

---

### Post by Chame_Wizard on 2011-01-15
I am stuck at 4.4.5,for some strange reason upgrading to 4.5.5 doesn't work at all.Any ideas?

4.6 seems to be nice to use.:popcorn:

I am an advanced Linux user for almost a year now(the 20th of January 2010) btw.:lolflag:

---

### Post by cguy on 2011-01-15
You need to add the Kubuntu Backports PPA to your Software Sources in order to upgrade to KDE 4.5.

You need to upgrade to Maverick Meerkat and add the Kubuntu Backports Beta PPA to your Software Sources for KDE 4.6 {which is RC2, not final, atm}

---

