---
title: "Why is it still so important to have a Qt/GTK-only set of applications installed?"
date: 2011-06-29
forum: The Cafe
---

### Post by murderslastcrow on 2011-06-29
I used to understand this problem, since the integration of GTK and Qt applications in either main environment (GNOME and KDE) was a huge issue. But with QGtkStyle and Oxygen-gtk (and dbus), it seems that both sides have a case where, if they were not a Linux user before, they would scarcely notice any difference between Qt and GTK applications.

Aside from applications like Kopete, Amarok, and Empathy, which have new features that integrate directly into their primary DE, it seems that most of the issues come down to a difference in opinion on application design, and downright dogmatism.

VLC and Skype are good examples of Qt applications people don't seem to have an issue installing in GTK-based environments, and GIMP and Inkscape are fairly popular even on KDE. Firefox is XUL based and seems to be perfectly fine for everyone, even though its look really does have much left to desire. Open/Libre-Office also fit in this category.

So with this in mind, if you do have a tendency not to install Qt or GTK applications on your computer, why not? I'd sure like to know a good reason aside from loyalism or disagreement over design ethics, as there are many GTK and Qt applications which don't have any ties to GNOME or KDE, or their HIGs.

I'm merely curious, since I feel like I've missed a huge, obvious issue preventing people from using two toolkits. Unity 2D is a good example of a reason why I don't understand the necessity to separate them. I still see a lot of users saying "I won't install that because it's a Qt/GTK application."

---

### Post by handy on 2011-06-29
I run both QT & GTK app's on my Arch/Openbox/Xfce4-panel box(s). Openbox uses GTK, though after I enlarged the fonts on the QT app's I don't see them as, or think of them as being different to those that are GTK, which is great.

---

### Post by Henry Flower on 2011-06-29
The thread title would make more sense without the 'Why', in which case the answer is no.

Two possible reasons for those who are concerned about it: looks; and having more packages than necessary installed on your system.  The latter is only likely to be an issue if you either have a small disk to work with (USB install, for example) or if you update a lot (many Arch users, for example).

---

### Post by doas777 on 2011-06-29
VLC like to staticly link everything so thats why it has no issue.

I don;t really have a problem having the QT runtime installed on a gnome system, though I do try to avoid it if possible. whats the point of overcomplicating your system after all?

---

### Post by aaaantoine on 2011-06-29
I use both.  The problem with having both is that it requires two heavy sets of libraries, and (concerning Unity 2D specifically) with Ubuntu trying to fit everything on a 650MB CD, this reduces the number of useful tools that come out of the box.

There's also the matter of shared resources.  2 GTK apps are more likely to share resources than a GTK and a Qt app.

---

### Post by jhonan on 2011-06-29
> **murderslastcrow said:**
> So with this in mind, if you do have a tendency not to install Qt or GTK applications on your computer, why not?
Force of habit. I just got used to installing apps specific to the DE. If I'm running gnome, I'll avoid apps with 'k' in the name, if I'm running kde, I'll avoid apps with 'g' in the name... :)

Also, before I install an app, I see how many libraries etc. get downloaded, and if it looks like it's bringing 100 libraries along for the ride, I'll tend to avoid it in case it breaks something else - Unlikely I know, but it's what I'm used to.

Not to mention the issues I had in earlier versions of trying to keep the theming consistent across GTK and Qt apps (okay, I know this is a non-issue now, but it left a bad taste in my mouth)

---

### Post by Pogeymanz on 2011-06-29
> **handy said:**
> I run both QT & GTK app's on my Arch/Openbox/Xfce4-panel box(s). Openbox uses GTK, though after I enlarged the fonts on the QT app's I don't see them as, or think of them as being different to those that are GTK, which is great.

Openbox does not use GTK...

---

### Post by santaslittlehelper on 2011-06-29
I use to care but the integration feels pretty seamless today so I use whatever app I find best be it Qt or GTK.

---

### Post by ScionicSpectre on 2011-06-29
I tend to use the best application for the job, even if it's an open source Windows application in WINE. Like some other users, I only really consider it a problem if it's dragging in a thousand dependencies- not because of space requirements, but because if I have a problem (however unlikely) it may be a lot more difficult to narrow down to something specific. And, some libraries activate daemons and require resources that, if I'm using multiple applications, may push my RAM and CPU use up a tiny bit. Still, I don't think this is as much of an issue for users of modern hardware, which is getting cheaper by the day.

Also, I guess if more users installed across toolkits more often, it might compel the developers to use up more space for libraries on the LiveCD. However, it seems from the talk amongst developers that Mark was considering using Qt in the future, anyway, using the best application, regardless of where it comes from. So this may be likely to happen anyway.

---

### Post by 3Miro on 2011-06-29
Main issue is the resource use. In order to run both GTK and QT simultaneously, you need to load both sets of libraries in the RAM. Thus native apps tend to load faster and be considerably lighter.

The integration is not perfect either, native apps interact better with DE specific services and settings. Also, there are some drag and drop issues. Those two used to be a much bigger issue, but not anymore.

---

### Post by handy on 2011-06-29
> **Pogeymanz said:**
> Openbox does not use GTK...

Mine does.

---

### Post by CraigPaleo on 2011-06-29
[Wikipedia]("http://en.wikipedia.org/wiki/Comparison_of_window_managers") says only Metacity and Xfwm use Gtk+. However, LXDE uses Openbox and Gtk+. Perhaps that's where the confusion arises.

---

### Post by GeneralZod on 2011-06-29
There are no references to GTK inside the OpenBox source code.  One of its test-cases is a very small PyGtk app, though.

Edit:

It uses glib and Pango, though.

---

### Post by el_koraco on 2011-06-29
Well, to avoid the prevasive bloat, of course.

---

### Post by murderslastcrow on 2011-06-29
If toolkit libraries are 'bloat', I'd love to hear what else in a default Ubuntu install is also bloat. Depending on your perspective, extra themes, unused codecs, new-style toolbars, certain configuration utilities, and a few default libraries could be bloat.

Of course, that's absolutely no excuse for adding anything more. For the most part, the stuff included in base installs of K/X/Ubuntu are entirely necessary. I think 'pervasive' may be a pretty strict adjective to describe Qt or GTK libraries, however.

---

### Post by ScionicSpectre on 2011-06-29
From what I've read, it seems that this is mostly a case-by-case issue for not using certain applications or libraries, not a general rule of thumb anymore. Just like how people pick and choose WMs and other components of their desktops to keep unnecessary cruft out.

I've seen really old computers with all the junk under the Sun installed, running simultaneously and decently enough not to be problematic. It sort of reminds me of how Windows XP applications look on Windows 7, and how colored icons look next to monochrome ones in a taskbar. It's fine for most people, but not the perfectionist.

I think a lot of Linux users are desktop-perfectionists on a personal level, not necessarily dogmatically motivated to segregate toolkits.

---

### Post by el_koraco on 2011-06-29
> **murderslastcrow said:**
> If toolkit libraries are 'bloat', I'd love to hear what else in a default Ubuntu install is also bloat. Depending on your perspective, extra themes, unused codecs, new-style toolbars, certain configuration utilities, and a few default libraries could be bloat.

Of course, that's absolutely no excuse for adding anything more. For the most part, the stuff included in base installs of K/X/Ubuntu are entirely necessary. I think 'pervasive' may be a pretty strict adjective to describe Qt or GTK libraries, however.

Dude, it's like you're not using Linux. Anything that wants to pull more than 2 MB worth of dependencies is bloat (I wasn't serious in the first post, just to clarify).

---

### Post by Simian Man on 2011-06-29
Because the whole point of Linux is to be able to brag about your "free -m".

---

### Post by Bachstelze on 2011-06-29
It is not and never was. Since day 1, I have always been running GTK apps in KDE or Qt apps in Gnome. If you like a program, it makes zero sense to refrain from using it just because it uses a different toolking that your environment.

---

### Post by murderslastcrow on 2011-06-29
D: I must have ALL THE TOOLKINGS at my disposal! Mwahahahaaaa!! *evil grin* (sorry, I'm a jerk sometimes, and I want toolkings to be real)

But yeah, you're right el_koraco, as far as open source libraries go, 2 MB is pretty egregious.

---

### Post by Tibuda on 2011-06-29
> **handy said:**
> Mine does.

Not Openbox itself, but Obmenu and Obconf do.

```
% pacman -Si openbox 
Repository     : community
Name           : openbox
Version        : 3.4.11.2-2
URL            : http://openbox.org
Licenses       : GPL
Groups         : lxde
Provides       : None
[B]Depends On     : startup-notification  libxml2  libxinerama  libxrandr
                 libxcursor  pango
Optional Deps  : pyxdg: for the xdg-autostart script[/B]
Conflicts With : None
Replaces       : None
Download Size  : 286.70 K
Installed Size : 2020.00 K
Packager       : R
Architecture   : x86_64
Build Date     : Fri Sep 3 09:47:16 2010
MD5 Sum        : 9a0a8121cad5264b52595f54c3575b8d
Description    : A window manager for the X11 windowing system
```




Back on topic, I just tend to like Gtk+ apps, but I use Qt apps like Skype and LyX because they are great.

---

### Post by Bandit on 2011-06-29
> **Pogeymanz said:**
> Openbox does not use GTK...

The applications he may be running could tho..

---

### Post by Barrucadu on 2011-06-29
It's not important. I use only Gtk+ programs, but that's just because I have very few graphical applications installed, and the few I do just so happen to use Gtk+&#8212;if any were Qt, I would also use Qt.

---

### Post by el_koraco on 2011-06-29
It would be nice if all the toolkits had their king.

---

### Post by simpleblue on 2011-06-29
I'm about to pull as shameless plug. Sorry to do this you but I love it and I wanna share the love :p:

For those out there that are KDE purests and would like a KDE only distro I would recommend Chakra Linux. One of it's main goals is to be GTK-free (and they have done their best to take this very seriously. To my knowledge they are the only distro that does this. Correct me if I'm wrong), and so you'll find yourself basking in all-out KDEness to your hearts desire.

It's been called "Easy Arch" as it's built ontop of Arch with the super-fast Pacman package management system and does not require you to be a brain surgen to install it.

---

### Post by Bachstelze on 2011-06-29
> **simpleblue said:**
> One of it's main goals is to be GTK-free

That is ridiculous.  I can understand why people would want a distro without proprietary software, but a distro without GTK is just excluding a large portion of the Free Software world just for the sake of "KDE purism".  It baffles me how the Linux community can be so exclusive sometimes...

---

### Post by ScionicSpectre on 2011-06-29
Well, it makes as much sense to be Qt-centric as it does to be GTK-centric. It's not like there are that many fewer useful applications for Qt, although GTK applications certainly have gotten more free advertising since Ubuntu started out with GTK and continues to use it extensively.

The problem with Chakra is that it doesn't use the Arch repositories. Pacman's great, but it's kinda' pointless without the packages in Arch. I don't really understand the purpose of their 'bundle' system. Appset-Qt is a decent graphical installer if KPackageKit won't do, and it supports AUR installation which is sweet.

But who knows? It's been about a year since I tried Chakra, so they might've changed and gone rolling-release with the official Arch repositories after all. KDE in Arch is by far the best KDE I've ever used, though. For some reason, it's just way faster than in openSUSE or Kubuntu (might be due to the default rendering mode in X or something simple and obvious).

---

### Post by Bachstelze on 2011-06-29
> **ScionicSpectre said:**
> Well, it makes as much sense to be Qt-centric as it does to be GTK-centric. It's not like there are that many fewer useful applications for Qt, although GTK applications certainly have gotten more free advertising since Ubuntu started out with GTK and continues to use it extensively.

I never used Chakra but there is a world between "Qt-centric" and "GTK-free". Which one is it then?

---

### Post by handy on 2011-06-29
The human weakness for chauvinism, in the extreme could be the end of us. We really do need to identify it in our selves, question its value & rise above it every chance we get.

I call that evolution.

---

### Post by forrestcupp on 2011-06-29
I have never cared. I used to run Qt apps in Gnome even before they had themes that made them look seamless. Sometimes it felt out of place, but it was worth it to get some great apps.

---

### Post by CraigPaleo on 2011-06-29
> **ScionicSpectre said:**
> 

But who knows? It's been about a year since I tried Chakra, so they might've changed and gone rolling-release with the official Arch repositories after all. .

As far as I know, they aren't using the Arch repos because Arch's updates were breaking Chakra -  KDE mod to be specific.

---

### Post by BrokenKingpin on 2011-06-29
I usually stick to Gtk apps because that is what I am familiar with, and to avoid bringing in a lot kde/qt dependencies.

---

### Post by NightwishFan on 2011-06-29
On a modern system you would not even notice the difference. Though there is no point wasting space and memory if you do not need to.

---

### Post by handy on 2011-06-29
It makes no noticeable performance difference to my Arch system having both of the QT & GTK essentials installed. Nor does having both sets loaded & being used.

I think that unless you have an old system with very limited storage capacity & RAM, that this is really a non issue.

Both systems work great individually & together.

---

### Post by CraigPaleo on 2011-06-29
The only difference I notice is the application start-up times on my six year old computer. It might not even be noticeable on newer hardware.

---

### Post by handy on 2011-06-30
> **CraigPaleo said:**
> The only difference I notice is the application start-up times on my six year old computer. It might not even be noticeable on newer hardware.

My No.2 box is running Arch also, it is pushing 7 years old. It has no noticeable problems running QT/GTK either, smooth as glass actually. :)

---

### Post by ScionicSpectre on 2011-06-30
I'm just glad to see the days of avoiding Qt applications because 'KDE is heavy' (a completely unrelated subject) are over. If Qt can run on Symbian, I'm sure it can run on an old computer decently enough, but again it depends entirely on the application. From what I've seen, outside of videogames and 3D software, most Linux applications don't exceed 256 MB of RAM for minimum requirements.

If you can't afford a computer that good, I'll buy you one. I'm pretty sure you can get that for pennies. But I know how it feels to resurrect an old computer just for the sake of it. Sometimes I get old computers just to see how far I can push them before they choke. XD

---

### Post by BrokenKingpin on 2011-06-30
> **handy said:**
> It makes no noticeable performance difference to my Arch system having both of the QT & GTK essentials installed. Nor does having both sets loaded & being used.

I think that unless you have an old system with very limited storage capacity & RAM, that this is really a non issue.

Both systems work great individually & together.
It really depends on the applications. If the application is a QT application that uses a lot of KDE libraries, it will bring in a large number of libraries. If it just uses QT with no KDE libs then it isn't a big deal at all.

I have no problems installing a QT app if there is no GTK alternative, but more often than not there is, so why bring in extra libs and dependencies if I don't have to?

---

### Post by capink on 2011-06-30
I don't want to hijack this thread, but I want to know people thoughts about a related question:

Would it be OK if distros chose the best application regardless of the desktop environment it belongs to? e.g. include Amarok or k3b in gnome centric distros.

I know one obstacle of this happening in Ubuntu is that insist on shipping CDs instead of DVDs, so the added dependencies will be a huge penalty size-wise. But what about other distros?

---

### Post by handy on 2011-06-30
> **BrokenKingpin said:**
> It really depends on the applications. If the application is a QT application that uses a lot of KDE libraries, it will bring in a large number of libraries. If it just uses QT with no KDE libs then it isn't a big deal at all.

I have no problems installing a QT app if there is no GTK alternative, but more often than not there is, so why bring in extra libs and dependencies if I don't have to?

Even though I run an Arch minimal Openbox desktop system, I really don't give two hoots about how many libs & other dependencies the tools that I choose to use bring in. I have plenty of HDD space & 6GB of RAM on Box.1 & 2GB of RAM on Box.2. 

It is Arch, so at least I'm only bringing in what I want & not having other stuff foisted upon me by distro creators.

My computer is a tool that does what I want it to do, not the other way around.

---

### Post by 3Miro on 2011-06-30
> **capink said:**
> I don't want to hijack this thread, but I want to know people thoughts about a related question:

Would it be OK if distros chose the best application regardless of the desktop environment it belongs to? e.g. include Amarok or k3b in gnome centric distros.

I know one obstacle of this happening in Ubuntu is that insist on shipping CDs instead of DVDs, so the added dependencies will be a huge penalty size-wise. But what about other distros?

Make them optional, I don't like when default apps are from mixed toolkits. (although I think they should be available if you want them)

Also, the "best" apps is very subjective. When it comes to XD burning, xfburn (or brasero) is all that I need, I have no need for k3b. Also, I could never figure out how to use Amarok.

I wouldn't like it if a distro goes out of its way to make it hard to mix toolkits, but I also don't like it when they mix toolkits by default.

---

### Post by Random_Dude on 2011-06-30
I didn't even knew VLC and Skype were Qt applications. :o
I just use what I need.

BTW, is it just me or there are more GTK applications than Qt?

Cheers :cool:

---

### Post by NightwishFan on 2011-06-30
KDE was very popular until some Gnome centric distributions such as Ubuntu and Fedora took off. I would guess it might be 60-40. ;)

Edit: Did a very unscientific search of Debian repos using tags. Guess I was a bit off but then again this really proves nothing.

Packages tagged as QT: 1079
Packages tagged as GTK: 2214

---

### Post by 3Miro on 2011-06-30
> **Random_Dude said:**
> 
BTW, is it just me or there are more GTK applications than Qt?

Cheers :cool:

When QT and KDE first came to the scene, they were not considered "free" software. This changed later. QT is still largely under the control of QT Software (formally Trolltech) and hence you will see a tendency for commercial applications to use QT, while community ones tend to use GTK.

---

### Post by capink on 2011-06-30
> **3Miro said:**
> Also, the "best" apps is very subjective. When it comes to XD burning, xfburn (or brasero) is all that I need, I have no need for k3b. Also, I could never figure out how to use Amarok.

I did not mention amarok or k3b to imply that they are the "best". They were just random examples. Actually I never used Amarok or any similar program (banshee, rhythmbox ...). And when I used to burn CD/DVDs nero was my choice.

---

### Post by 3Miro on 2011-06-30
> **capink said:**
> I did not mention amarok or k3b to imply that they are the "best". They were just random examples. Actually I never used Amarok or any similar program (banshee, rhythmbox ...). And when I used to burn CD/DVDs nero was my choice.

And I am just giving an example of how the default application set can never make everyone happy. I find one set of apps good for me and other people will like others. People should have the option to use whatever they want, but I think that the default application set should avoid mixing toolkits.

---

### Post by murderslastcrow on 2011-06-30
@3Miro, I think he was suggesting that certain distros/spinoffs, not Ubuntu in particular, might like to include a Qt or GTK application in GNOME or KDE, respectively.

It's arguable that GIMP doesn't have a very suitable alternative in Qt, and Firefox, despite being based on XUL, is included by default in dozens of distributions. Some people prefer Amarok to Banshee, Rhythmbox, Exaile, etc., but may also prefer GNOME to KDE. So the question (as I understood it) is that, if this were preferred more widely later on, wouldn't it be fine, if space were not an issue, to make that decision default, despite the bringing in of other toolkits/libraries?

Also...

> QT is still largely under the control of QT Software (formally Trolltech).

In [this article]("http://labs.qt.nokia.com/2011/05/09/thoughts-about-qt-5/"), third paragraph, it's mentioned that open governance (in the works for a while) is going to be the default development method. Soon, Qt won't be controlled by Nokia/Trolltech, for all intents and purposes.

---

### Post by 3Miro on 2011-06-30
> **murderslastcrow said:**
> @3Miro, I think he was suggesting that certain distros/spinoffs, not Ubuntu in particular, might like to include a Qt or GTK application in GNOME or KDE, respectively.


The point was about including mixed toolkit apps because those apps are "best". My point was that there is no such thing as "best" default app as those are too subjective.

> 
It's arguable that GIMP doesn't have a very suitable alternative in Qt, and Firefox, despite being based on XUL, is included by default in dozens of distributions. Some people prefer Amarok to Banshee, Rhythmbox, Exaile, etc., but may also prefer GNOME to KDE. So the question (as I understood it) is that, if this were preferred more widely later on, wouldn't it be fine, if space were not an issue, to make that decision default, despite the bringing in of other toolkits/libraries?


I agree that some apps really have no alternative. Firefox/Chromium are too far ahead of other browsers and Gimp is unparalleled in features, however, if we are dealing with apps that are sufficiently close (Amarok vs Rhythmbox), then there is no reason to mix the toolkits. Keep the default "pure" and let the user decide if they want to mix.

> 
In [this article]("http://labs.qt.nokia.com/2011/05/09/thoughts-about-qt-5/"), third paragraph, it's mentioned that open governance (in the works for a while) is going to be the default development method. Soon, Qt won't be controlled by Nokia/Trolltech, for all intents and purposes.

The current level of corporate control over QT explains why QT is often used in proprietary software. It is good to know that QT is becoming more free.

---

### Post by Random_Dude on 2011-06-30
> **3Miro said:**
> When QT and KDE first came to the scene, they were not considered "free" software. This changed later. QT is still largely under the control of QT Software (formally Trolltech) and hence you will see a tendency for commercial applications to use QT, while community ones tend to use GTK.

I didn't know that.
Thanks for the explanation. ;)

Cheers :cool:

---

### Post by ScionicSpectre on 2011-06-30
I thought KDE SC was community software? I guess you're saying that you'll see a tendency for every kind of developer to use Qt, and for commercial entities to stay away from GTK? Yeah, I definitely see that. I think Minitube is a good example of both in action- free and open source for Linux, paid for other platforms.

---

### Post by Tibuda on 2011-06-30
> **handy said:**
> It is Arch, so at least I'm only bringing in what I want & not having other stuff foisted upon me by distro creators.

I don't really think this is true for Arch. [Many Arch packages depends on stuff that are not really required]("http://www.youtube.com/watch?v=flmX9GYwyiI"). I don't really care, "lightweight" is not why I use Arch.

---

### Post by el_koraco on 2011-06-30
> **ScionicSpectre said:**
> I thought KDE SC was community software? 

Yeah, but QT is not equal to KDE.

---

### Post by Tibuda on 2011-06-30
> **ScionicSpectre said:**
> I think Minitube is a good example of both in action- free and open source for Linux, paid for other platforms.

Like XChat, but it uses Gtk+.

---

### Post by Bachstelze on 2011-06-30
> **ScionicSpectre said:**
> I think Minitube is a good example of both in action- free and open source for Linux, paid for other platforms.

That is not true. Only the Windows and Mac OS X *binaries* of Minitube are payware. The source code is always available and you can compile it on any platform you want. If you couldn't, it wouldn't be Free Software. Same for Xchat, there are some free Windows builds of it.

---

### Post by handy on 2011-06-30
> **Tibuda said:**
> I don't really think this is true for Arch. [Many Arch packages depends on stuff that are not really required]("http://www.youtube.com/watch?v=flmX9GYwyiI"). I don't really care, "lightweight" is not why I use Arch.

I think you are being pedantic & nit picking. Most people would know what I meant, which was that only the tools & applications that I choose to install are installed. Also, there are no extra overheads re. GUI system configurations tools unless a user chooses to install such.

In general Arch tries not to modify anything that comes down from upstream unless for some reason the dev's absolutely have to, this may or may not add to the number of dependencies required, I don't know, nor do I care?

---

### Post by Tibuda on 2011-07-01
> **handy said:**
> I think you are being pedantic & nit picking. Most people would know what I meant, which was that only the tools & applications that I choose to install are installed. Also, there are no extra overheads re. GUI system configurations tools unless a user chooses to install such.

That is possible for any distro. [Ubuntu included]("http://www.psychocats.net/ubuntu/minimal").

---

### Post by 3Miro on 2011-07-01
> **ScionicSpectre said:**
> I thought KDE SC was community software? I guess you're saying that you'll see a tendency for every kind of developer to use Qt, and for commercial entities to stay away from GTK? Yeah, I definitely see that. I think Minitube is a good example of both in action- free and open source for Linux, paid for other platforms.

KDE is community build freedom software developed on top of the QT toolkit.

QT is a set of libraries that are "free as in freedom", but under the control of Nokia. murderslastcrow noted that this is about to change.

---

### Post by handy on 2011-07-01
> **Tibuda said:**
> That is possible for any distro. [Ubuntu included]("http://www.psychocats.net/ubuntu/minimal").

Glad to hear it. :)

---

### Post by wizard10000 on 2011-07-01
> **forrestcupp said:**
> I have never cared. I used to run Qt apps in Gnome even before they had themes that made them look seamless. Sometimes it felt out of place, but it was worth it to get some great apps.

This.

I wonder how many KDE purists really turn their nose up at synaptic - or how many GNOME users blacklist k3b because it uses Qt libraries  :D

There are some nice tools out there but I don't think either GTK or Qt has a compete set of the best stuff you can use ;)

---

### Post by NightwishFan on 2011-07-01
I most definitely use Synaptic on KDE. :) On Debian based distros you can use "apt-get --no-install-recommends install" to cut out a few non-essential dependencies. I need this to have the software center work right on debian kde.

---

### Post by el_koraco on 2011-07-01
> **NightwishFan said:**
> I most definitely use Synaptic on KDE. :) On Debian based distros you can use "apt-get --no-install-recommends install" to cut out a few non-essential dependencies. I need this to have the software center work right on debian kde.

How is Debian with introducing packagekit as a backend, btw?

---

### Post by NightwishFan on 2011-07-01
> **el_koraco said:**
> How is Debian with introducing packagekit as a backend, btw?

[http://packages.debian.org/search?keywords=packagekit&searchon=all&suite=all&section=all](http://packages.debian.org/search?keywords=packagekit&searchon=all&suite=all&section=all)

Packages for it seem to be hitting Wheezy (testing).

---

### Post by el_koraco on 2011-07-02
Nice. I wonder what they're gonna do with the KDE version for Wheezy when it goes stable - whether they're gonna stay with the current setup, go with packagekit, or hit a Muon-aptdaemon integration like Kubuntu.

---

### Post by wizard10000 on 2011-07-02
> **el_koraco said:**
> Nice. I wonder what they're gonna do with the KDE version for Wheezy when it goes stable - whether they're gonna stay with the current setup, go with packagekit, or hit a Muon-aptdaemon integration like Kubuntu.

muon's already in wheezy - I just don't know if it's the default package manager.  It wasn't a couple months back when I gave wheezy a spin.

---

