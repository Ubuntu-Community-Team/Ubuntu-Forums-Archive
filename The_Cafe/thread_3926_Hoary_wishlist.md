---
title: "Hoary wishlist"
date: 2004-11-10
forum: The Cafe
---

### Post by MaZiNgA on 2004-11-10
Hey, new guy here...Just switched from Debian Sarge and I gotta say I LOVE this distro! Still I have just a few wishes for next release:
 
*Bootsplash
*Control Center
*Graphical Installer

It would be the perfect distro wouldn't it?

---

### Post by HungSquirrel on 2004-11-10
I disagree with the graphical installer bit.  I think the new Debian installer (which is what Ubuntu uses) is excellent and gets the job done.  With graphical installers, not all machines run the framebuffer correctly.

---

### Post by HiddenWolf on 2004-11-10
Bootsplash, definatly.
And (if crude) a stricter selection on what gets installed.

Why do I need 'laptop-detect' - 'laptop-mode', a few different types of print servers and spoolers, cron, fam, and more of these services.

I'm running a desktop, which is something that should be detected, so all laptop-related stuff can be deselected.
I'm running a workstation, so I find it annoying that there are multiple programs for everything which I cannot remove without breaking 'ubuntu-desktop' or 'ubuntu-base'

The same goes for games. I don't want to play tetris, or any of them, but they are pushed on me.

I would much rather like to see:
Strict selection.
one app each for
Internet, e-mail, word, spreadsheet/etc and then a minimal working solution. Say Firefox/Thunderbird/ rather than MozillaSuite/Evolution

For me, the same goes for Gimp. I will never use it, and I don't understand why it is default, rather than optional.

Linux distro's should focus on doing the core business right, and offering versatility for those who need it, but not offer the most feature-full enviornment possible.

We should try to offer a functional platform, rather than a wide range of options which might confuse the new user.

---

### Post by tanari on 2004-11-10
> Hey, new guy here...Just switched from Debian Sarge and I gotta say I LOVE this distro! Still I have just a few wishes for next release:

*Bootsplash
*Control Center
*Graphical Installer
and I want to see
*xDSL/PPPoE GUI configuration tools
*better cd burning app

---

### Post by HiddenWolf on 2004-11-10
[QUOTE=tanari]
*xDSL/PPPoE GUI configuration tools[/QUOTE]
Amen!

---

### Post by Lovechild on 2004-11-10
Bootsplash (and nothing silly like RedHat uses, I want to see no ugly kernel/bootloader/anything text, just a pretty Ubuntu logo and a progress bar.

X.org (done)

GNOME 2.10 (scheduled)

Better L10n/i18n including tools for providing it (gtranslator would be nice)

Full Mono support (this is a deal breaker for me, I need Mono and officially supported that is)

OpenOffice with the native widget/fileselector patches

Epiphany over Firefox (simple reason for me really, it's tightly integrated with GNOME and it's translations are easy to handle where as getting in on the translation team for Firefox is... tricky, besides I like epiphany better, it feels far simpler and to the point)

Graphical installer

Good support for bugreporting during testing phase (a little python app to file the bug and saerch for similar ones so I would have to work with the nastiness that is bugzilla - would be nice)

Firewall out of the box, like Fedora does

SELinux, like FC3's targeted policy maybe?

Drop the silly sudo stuff, I hate it so much, I want it dead - with sudo I can no longer trust my user account with an easy to remember password since it's the same I need for "root" - and sudo accomplices nearly nothing, learning the user about proper user right seperation would be a good thing.

Death to all OSS, use ALSA only, fix apps that doesn't like that

Coaster as default CD burning app, please assist developer in his quest to make a good burninator.

and so many things in addition, but I don't think realistically we can reach them all in the Hoary cycle without damaging the end product, SELinux alone takes real effort to get right.

---

### Post by MaZiNgA on 2004-11-10
[QUOTE=HungSquirrel]I disagree with the graphical installer bit.  I think the new Debian installer (which is what Ubuntu uses) is excellent and gets the job done.  With graphical installers, not all machines run the framebuffer correctly.[/QUOTE]

Well then why not put down a choice for text-based (if graphical goes wrong)? The reason I'd like it so much to see a graphical installer is that ubuntu is so polished and the installer is the only thing that screws up...

*X.org: Yeah!
*Choose Packages to be installed: Yeah!
*More packages: SELinux, Oo.org extensions, Coaster, Firewall, Bugzilla etc.: Agreed ,**but** it will take *time* (for the team to put them) and *space*  on the disk...
*Hey the sudo stuff is user-friendly. Windows users like it.

---

### Post by TravisNewman on 2004-11-10
Sudo is very powerful, but it needs to maybe have more configuration over the sudoers. Lots of people are talking about how adding more accounts screws stuff up.

Bootsplash yes, I love that idea, but with an option for verbose mode, of course.

Graphical installer, yes, as long as it can tell that it's not working and switch to the default installer, AND give the user the choice to begin with.

HiddenWolf, uninstalling ubuntu-desktop and ubuntu-base do nothing to the system. They're just meta-packages that depend on other packages. Simplifies the installation.

It'd be nice to have a few groups of packages required, and then ask if you want to install other things, like games, laptop support, etc, that HiddenWolf was talking about.

Firewall and SELinux, yes, but maybe not until Grumpy except for testing, you want that to be TIGHT before its released. If that goes, you're screwed.

CD Burning does need to be fixed up, at least the audio burning. MrBurns looks promising if someone picks it up. (Search the forum for MrBurns, it should pop up in the mailing list section). 

Now maybe a part of the installer where it says "You've installed all the packages you wanted from the cd, wanna check out what's online too?" And then *somehow* make a very usable (I hate the word user-friendly. Habit I picked up from my software engineering professor) interface for package selection.

Of course, what we say here probably won't make much of a difference. As one of the devs said, the people who are satisfied won't request anything because of complacency, so there's no way to get an accurate representation of what people want.

Personally, I'm happy with the way Ubuntu is going. It's the only distribution that ever made my fiancee want to use Linux, and after seeing me use it for a few days, she decided to go whole hog and got rid of Windows altogether! I know, I know, it's very rare for a girl to use Linux, especially someone who's never used any form of Unix/Linux before in her life, and though is computer savvy, isn't really computer proficient. But she's happy as hell with it, and if a distribution can make someone like my fiancee happy, it must be doing something right.

---

### Post by Lovechild on 2004-11-10
Additions:

User friendly updater like rhn-applet in Fedora

Freeciv 2.0 (it should be out by then and it really rocks hard)

Menu set to 24x24 icons for usability (since it's pratically impossible to notice the icon at 16x16 and icons are important for people with poor language skills).

Also if someone could look at how Novell Linux Desktop renders fonts, because it's simple sexy.

I would like to see Muine as the default music player with a gstreamer backend.

---

### Post by jdodson on 2004-11-10
[QUOTE=Lovechild
User friendly updater like rhn-applet in Fedora
[/QUOTE]

synaptic isnt too bad for that. 

someone mentioned a graphical boot screen, they are looking into that one, i saw the development report.  the graphical installer?  hmmm i thought i heard they were considering it.  as far as replacing package X for package Y, i dig what they provide personally, i only add a few things and use most of the defaults.  but then again i am a gnome lover so.... ;-)

---

### Post by HiddenWolf on 2004-11-11
[QUOTE=Lovechild]
Firewall out of the box, like Fedora does[/QUOTE]
Ubuntu does not have any ports listening to the outside, and thus should not need a firewall. Anyone who knows how to set up something that does listen, should know how to set up a firewall. At least that is the argument.

I would agree tho, I'd like to monitor incoming as well as outbound traffic. For a windows user it feels weird not to have a firewall installed.

[QUOTE=Lovechild]
Death to all OSS, use ALSA only, fix apps that doesn't like that[/QUOTE]
Oh, yeah, this is one sweet fantasy. For me, the same annoyance pops up when I see three different printing servers installed. cups, ltd etc.

---

### Post by HiddenWolf on 2004-11-11
[quote=panickedthumb]
HiddenWolf, uninstalling ubuntu-desktop and ubuntu-base do nothing to the system. They're just meta-packages that depend on other packages. Simplifies the installation.

It'd be nice to have a few groups of packages required, and then ask if you want to install other things, like games, laptop support, etc, that HiddenWolf was talking about.
[/quote]
I know it does nothing to the system. My annoyance is that they install so many things. As said I want to stick to ubuntu.
 I want to be able to come here with a close to default installation and be able to say. Damn, I like this distro, it makes good choices.
I want to come here and say. hey, I've got a near default install, so I am able to find help here.
Besides that, it just annoys me that one distribution needs twe systems for sound, two or three print services, all the laptop stuff, games, etc.

I want to be given the option. "do you want games / development / image editing / etc"
> =panickedthumb]
Firewall and SELinux, yes, but maybe not until Grumpy except for testing, you want that to be TIGHT before its released. If that goes, you're screwed.
Amen!
[QUOTE=panickedthumb]
Personally, I'm happy with the way Ubuntu is going.
[/quote]Amen!

---

### Post by daniels on 2004-11-11
> **HiddenWolf]Why do I need 'laptop-detect' - 'laptop-mode', a few different types of print servers and spoolers, cron, fam, and more of these services.[/QUOTE]laptop-detect is very, very, very, very, very, very small, and its sole purpose in life is to exit 0 if we're running on a laptop, and 1 if we are.  That's it.

You can remove laptop-mode if you want, but it's insanely difficult (and pointless) to have different installations for desktops and laptops.  Again, it's like one shell script.  If you really want a smaller installation, remove documentation or something.
> I'm running a desktop, which is something that should be detected, so all laptop-related stuff can be deselected.Um, without laptop-detect, we'd have no way to detect that you were running on a desktop.
> I'm running a workstation, so I find it annoying that there are multiple programs for everything which I cannot remove without breaking 'ubuntu-desktop' or 'ubuntu-base'I thought you said you wanted to be more strict on what was installed ...
> The same goes for games. I don't want to play tetris, or any of them, but they are pushed on me.My mum wants to play freecell or whatever, and so does yours, probably.

> Internet, e-mail, word, spreadsheet/etc and then a minimal working solution. Say Firefox/Thunderbird/ rather than MozillaSuite/EvolutionEr, we don't have multiple apps for these.  We have one web browser (Firefox said:**
> For me, the same goes for Gimp. I will never use it, and I don't understand why it is default, rather than optional.Because lots of people do.  I don't use Evolution, but I still see why it's included.

> Linux distro's should focus on doing the core business right, and offering versatility for those who need it, but not offer the most feature-full enviornment possible.

We should try to offer a functional platform, rather than a wide range of options which might confuse the new user.Yes, which is exactly why we're so obsessed with one CD.  Take a look at the selection of applications offered with other distributions, and compare.

---

### Post by Lovechild on 2004-11-11
Synaptic does nothing like what rhn-applet does, it does not sit in my tray and alert me of updates - synaptic is IMHO a horrible application and I would like to see a rewrite, maybe in python with a more gnome2'ish approach to package management, Havoc has some ideas listed for a project I think, abide it's for Fedora which is rpm based but maybe we could work together to get a truly great common package handler.

---

### Post by HiddenWolf on 2004-11-11
Sorry Daniels, got a bit too fanatical there. I agree that ubuntu is the slimmest distribution I've come across.

My main question at the moment is:
Why doesn't ubuntu offer the options during install..

Do you want image editing, yes/no
Do you want games, yes/no
Debian does it, and it is certainly not a major complication of the install procedure, looking at how smooth the other parts are.

Browsers:
Firefox, mozilla, (I can live with mozilla, Imho the browser should depend on the desktop, and not vice-versa, but ala)

What does a desktop need cron/fam for for instance? If you know how to use them, you can install them, right?
I know they are small, but it's not size that matters to me so much as speed.

Ofcourse you are, as are all distributions, very much limited by the very close interrelationships among packages. Which is a thorn in my eye, to be honest.
Anyhow, I'll hush.

---

### Post by mr_ed on 2004-11-11
[QUOTE=HiddenWolf]Oh, yeah, this is one sweet fantasy. For me, the same annoyance pops up when I see three different printing servers installed. cups, ltd etc.[/QUOTE]

Hear, hear!

Printing support is still abysmal in Linux.
I know it would take a lot of work to move all applications over to one printing system, but it's worth it in the end for all of Linux.

So far, this is the slickest Linux I've seen yet.  I agree that there's still a bunch of stuff that could be weeded out.

In the install, we could have a list of checkboxes for which meta-packages we'd like installed:  Default (all), laptop support, games, ...
and just have the default meta-package just depend on all the other meta-packages.

It would be good if the package selector is only on one screen, and lumped in at the same place as every other selection, so that Joe User can make his choices, and then let it install away.

Out of curiosity, why is Postfix installed?  Everybody I know uses their ISP's POP and SMTP access, or they use webmail.

BTW, I'm willing to help out.  :)

---

### Post by neutron on 2004-11-12
First I want to say that I really enjoy Warthy (coming from windowsxp). Thnx to the devs. Of course, there's always something which can be improved  :lol: 

The main things I'd like to see in Hoary are:

**bootsplash** - already planned I believe. I don't want to see cryptic kernel messages.
**xorg** - planned
**gnome 2.10** - planned (Finally audioburning integrated to Rythmbox, yah). This release should be much faster according to the devs.
**Custom Install** - it's already been said, although Ubuntu fits on one cd (nice) I'd like to be able to customize my install a bit, e.g. deselect Evolution
**Graphical installer** - like others said, plz offer a choice for installing in text- or graphical mode.
**Complete G-S-T** - I don't need a complete control center, but I was surprised that a few tools from the gnome-system-tools package in Gnome 2.8. I'd like to modify my grub configuration and runlevels by a GUI app.
Maybe include **autopackage ** - should be out at the end of this year. 

I've saved the most important one for last:

**OpenOffice.org 2.0** - I'm really curious about this one. It should be out in March. It should have neat features like tight integration into Gnome, way faster startup- and save time & much more. Somebody knows if this is planned for Hoary? Weird that no one else mentioned it. Am I the only one who think this is a major plus for Hoary?

Ubuntu was the first distro which made me started to use, and more important, like gnome! Excellent!

---

### Post by daniels on 2004-11-12
[QUOTE=HiddenWolf]My main question at the moment is:
Why doesn't ubuntu offer the options during install..[/QUOTE]Because people really shouldn't have to care -- right now one of the biggest advantages of Ubuntu is that it really, really, really, really doesn't ask questions unless it desperately needs to (the whole sudo thing came about as a result of working out how we could get rid of the root password question).

> What does a desktop need cron/fam for for instance? If you know how to use them, you can install them, right?
I know they are small, but it's not size that matters to me so much as speed.Regular tasks such as updatedb and all that sort of stuff -- it's not a slowdown if there's nothing actually using it.

---

### Post by daniels on 2004-11-12
[QUOTE=Lovechild]Synaptic does nothing like what rhn-applet does, it does not sit in my tray and alert me of updates - synaptic is IMHO a horrible application and I would like to see a rewrite, maybe in python with a more gnome2'ish approach to package management, Havoc has some ideas listed for a project I think, abide it's for Fedora which is rpm based but maybe we could work together to get a truly great common package handler.[/QUOTE]There is a notification applet planned, either separate or as part of Synaptic, but yeah; a little tool to say 'BING! UPDATES!' in your notification area.

And rewriting stuff in Python is not always a good idea.  You could write a replacement in Python and have it be ten times worse than Synaptic is.  While I still use apt-get from the command line (faster), out of the graphical tools, Synaptic's actually the best I've seen.

---

### Post by mr_ed on 2004-11-12
What about a little applet that allows you to start and stop services?
Samba already has a checkbox for that in network-admin.
If I added an "advanced" tab or something, would others use it?

---

### Post by TravisNewman on 2004-11-12
[QUOTE=mr_ed]What about a little applet that allows you to start and stop services?
Samba already has a checkbox for that in network-admin.
If I added an "advanced" tab or something, would others use it?[/QUOTE]
 That's APPARENTLY in gnome-system-tools but not included in Ubuntu. I asked this question somewhere, and my answer was "It's there, under Computer -> System Configuration -> Services" when I never had that. I guess he'd gotten a different version of the system-tools than is included in Ubuntu

---

### Post by oddabe19 on 2004-11-12
One thing I think would be really nice to see, is during installation a choice of what arch kernel you want to have installed... something like
```
Would you like to choose what base kernel you want? Y/N
(next screen)
Would you like...
2.6.9 - i386 click here (all platforms)
2.6.9 - i686 click here (PII, III, IV, Mobile and Celeron)
2.6.9 - k7 click here (Duron, Athlon, Athlon XP, Mobile Athlons)
2.6.9 - Big Mem click here (If you have over Xgig of memory)
2.6.9 - SMP click here (for 2 processors)

2.4.28 - Warning: NOT RECOMMEDED... (but an option.)

Add Headers/ Source? (33-ish meg Download) Y/N
```

That's something i've been bugging for and waiting for in almost all distros, but I think that Ubuntu would be way ahead if someone added that.

Graphical bootscreen
Decent burning app (k3b works... if you like having kde and qt... i don't.)
Gui install... as an option... but defaults regular install.
Faster composite (and more stable) for Xorg
A collection of wallpapers/ themes in default install
Gui to change login splash per user
Native NVIDIA (6629 is the latest) /ATI drivers Catalyst (i believe ATI's are native though)


Ubuntu is already way ahead... good choice of software, etc... it's just plain good... and hoary will be better.

---

### Post by TravisNewman on 2004-11-12
Yeah I don't know if you can autodetect which Kernel to install, but if that were possible, that would be very sweet. As it is, it would be nice to be able to have that as an option. Maybe something like "Would you like to select alternate kernel's to install? If you are unsure of your architecture, or don't understand what a kernel is, then select no."
But only in an expert install environment.
I do like keeping the questions to a minimum though. Maybe add that to the "Expert" installation, maybe not, it's not that much extra work.
But then that would take up more room on the CD, and I REALLY love the 1 CD philosophy.

---

### Post by daniels on 2004-11-12
[QUOTE=panickedthumb]Yeah I don't know if you can autodetect which Kernel to install, but if that were possible, that would be very sweet. As it is, it would be nice to be able to have that as an option. Maybe something like "Would you like to select alternate kernel's to install? If you are unsure of your architecture, or don't understand what a kernel is, then select no."
But only in an expert install environment.[/QUOTE]Definitely with the expert.  Again, by my metric, this would result in a call from my mum -- she doesn't know what she's running there.  If you know, then you probably know enough to be able to find a HOWTO and install the optimised kernel if you desperately want that last ounce of optimisation (FWIW, there are far better optimisations to be had elsewhere).

Every question we ask has to be quite excruciatingly justified -- the number of questions we currently ask is somewhat of a badge of pride.

> I do like keeping the questions to a minimum though. Maybe add that to the "Expert" installation, maybe not, it's not that much extra work.
But then that would take up more room on the CD, and I REALLY love the 1 CD philosophy.It would take up quite a large amount of room, yes, especially as all the modules (there's a hell of a lot!) need to be rebuilt.  So yeah, not much extra work, but not a massive payoff, and it would certainly extend us into the realm of two CDs (!).

---

### Post by TravisNewman on 2004-11-12
[QUOTE=daniels]
Every question we ask has to be quite excruciatingly justified -- the number of questions we currently ask is somewhat of a badge of pride.[/quote]
And it should be. It's the least amout of questions I've ever had to answer and still be presented with a powerful Linux distribution that doesn't feel like I have the restrictions of Windows. That says a lot. 

[QUOTE=daniels]
It would take up quite a large amount of room, yes, especially as all the modules (there's a hell of a lot!) need to be rebuilt.  So yeah, not much extra work, but not a massive payoff, and it would certainly extend us into the realm of two CDs (!).[/QUOTE]
Yeah, definitely not worth it, unless it tied into the network to download a new kernel, but if you've gotta do that, just get it later, right?

---

### Post by HiddenWolf on 2004-11-13
[QUOTE=panickedthumb]And it should be. It's the least amout of questions I've ever had to answer and still be presented with a powerful Linux distribution that doesn't feel like I have the restrictions of Windows. That says a lot. [/QUOTE]

my feelings exactly

---

### Post by TravisNewman on 2004-11-13
Rock on! It seems you've grown a little more accustomed to the way things are in Ubuntu now, HiddenWolf, you did want a lot more a few posts back yes?

Course, you did apologize for getting a little fanatical, so maybe it was temporary ;)

---

### Post by HiddenWolf on 2004-11-13
I would love to be able to install a leaner system yes.

Does not mean that ubuntu would have to cut things, but if you move all games from u-desktop to u-games, gimp/scanner/etc to u-graphics etc. and present me the option to install the packages I want/need, without them being in the default desktop, that'd be great.

My ideal situation:
ubuntu-base: basic stuff, no x, suitable for building server
ubuntu-desktop: base+(lean+mean)gnome
ubuntu-devel: mono/development progs (from universe, download them)
ubuntu-web-devel: decent set of ftp-client and php/asp/etc editor(s)
ubuntu-games: games/etc
ubuntu-graphics: everything needed to edit/scan/manipulate/whatever images

etc.

---

### Post by allen on 2004-11-13
i would second this. sounds like a great idea to split ubuntu-desktop virtual package up a little bit. just so i or my mum could give the games a quick uninstall or say bye to the graphics manipulation programs.

---

### Post by daniels on 2004-11-13
[QUOTE=allen]i would second this. sounds like a great idea to split ubuntu-desktop virtual package up a little bit. just so i or my mum could give the games a quick uninstall or say bye to the graphics manipulation programs.[/QUOTE]While I'm not such a fan of the extra question (having one *default* install is a really good idea in and of itself, IMO, but I'm happy to agree to disagree, since it's a matter of taste), I do like the theory of ubuntu-base, ubuntu-desktop, et al.

---

### Post by TravisNewman on 2004-11-13
[QUOTE=daniels]While I'm not such a fan of the extra question (having one *default* install is a really good idea in and of itself, IMO, but I'm happy to agree to disagree, since it's a matter of taste), I do like the theory of ubuntu-base, ubuntu-desktop, et al.[/QUOTE]
 Here's what I'd like to see. the "custom" grub option on the install cd essentially installs a minimal installation, from what I've gathered. I'd like to see that changed to "minimal" and the "custom" option used for exactly what HiddenWolf is talking about, and also adding them into "expert" (if they're not already there, I've never used that option). That way you keep the default install and get around the extra question, which, like I said before, is important for most users, but then the people installing server systems get "minimal," slightly more advanced users get "custom," and experts, obviously, get "expert." Make sense? Again, I don't PERSONALLY care either way, but I'm trying to help find common ground for every possible need that wouldn't get in the way of other peoples' needs, and would keep it all on one cd.

---

### Post by MaZiNgA on 2004-11-14
Just as an update, bootsplash **will**  be included in Hoary, not as a kernel patch but as an app named *upsplash*  which will be much cooler and safer! Hooraaaay!  \\:D/

---

### Post by TravisNewman on 2004-11-14
I did a google search for upsplash and nothing came up... is it something the Ubuntu devs are writing or what? You have any specs on it (how it works, etc)?

---

### Post by daniels on 2004-11-14
[QUOTE=panickedthumb]I did a google search for upsplash and nothing came up... is it something the Ubuntu devs are writing or what? You have any specs on it (how it works, etc)?[/QUOTE]Yeah, it's going to be written especially for Hoary; it was primarily designed by Paul Sladen, Nathaniel McCallum and myself at Oxford on whiteboards and by a lot of handwaving.  I think it should be on the wiki under HoaryHedgehog/usplash.  Would respond more but too tired, sorry.

---

### Post by TravisNewman on 2004-11-14
Nice, that sounds great. Thanks much!

---

### Post by HiddenWolf on 2004-11-14
[QUOTE=daniels]While I'm not such a fan of the extra question (having one *default* install is a really good idea in and of itself, IMO, but I'm happy to agree to disagree, since it's a matter of taste), I do like the theory of ubuntu-base, ubuntu-desktop, et al.[/QUOTE]

Oh, I'll agree to disagree.
for me the question doesn't have to be default.
Allow me to deselect what I don't want this way after the install in synaptic, or ask the extra question in expert install mode and you've ade me a happy man.

---

### Post by HiddenWolf on 2004-11-14
[QUOTE=panickedthumb]Nice, that sounds great. Thanks much![/QUOTE]

Any idea on when we can enjoy this goodie?

---

### Post by fng on 2004-11-14
The real url in the wiki is : [http://www.ubuntulinux.org/wiki/USplash](http://www.ubuntulinux.org/wiki/USplash)

---

### Post by TravisNewman on 2004-11-14
[QUOTE=fng]The real url in the wiki is : [http://www.ubuntulinux.org/wiki/USplash](http://www.ubuntulinux.org/wiki/USplash)[/QUOTE]
 I can't wait to play with that ;) just read over the wiki, man it looks pretty sweet

---

### Post by daniels on 2004-11-14
[QUOTE=HiddenWolf]Oh, I'll agree to disagree.
for me the question doesn't have to be default.
Allow me to deselect what I don't want this way after the install in synaptic, or ask the extra question in expert install mode and you've ade me a happy man.[/QUOTE]Yeah, sounds pretty reasonable -- I'll bring it up.  The other issue is that of alternatives (e.g. ubuntu-desktop depending on 'totem-gstreamer | totem-xine') so people can install other stuff and keep u-d.

---

### Post by daniels on 2004-11-14
[QUOTE=HiddenWolf]Any idea on when we can enjoy this goodie?[/QUOTE]Hopefully within the next couple of months.

---

### Post by TravisNewman on 2004-11-14
[QUOTE=daniels]Yeah, sounds pretty reasonable -- I'll bring it up.  The other issue is that of alternatives (e.g. ubuntu-desktop depending on 'totem-gstreamer | totem-xine') so people can install other stuff and keep u-d.[/QUOTE]
 Ooh, if you're bringing up the issue of alternatives... a lot of stuff I've tried to install tries to remove postfix and install sendmail, which also removes ubuntu-desktop.

---

### Post by zerohalo on 2004-11-14
A few posts back someone mentioned OpenOffice 2.0. If it's out by then I think it would be GREAT to include it in Hoary. 

If it can't make it by Hoary release, then perhaps it could be added to the Ubuntu Main repository later as package that users can upgrade to once it comes out.

A few other "wishes" for the default install package, though I realize this is a matter of taste:

- Mplayer (without the w32codecs, which users can install) instead of Totem
- SMBC  or xsmbrowser or something that browses Windows networks reliably: I'm sorry, but SMB in Nautilus still sucks. I and others (running Gnome 2.8 in FC3) have used it on various networks and it's flacky. Half the time it doesn't work (and when it hangs, it crashes Nautilus and eventually in some cases requires a full reboot). Maybe it works just fine on a network with a couple of computers, but on a network with Windows domain authentication, forget it--I haven't been able to get it working even once. SMBC, as "old style" as it is, actually works flawlessly. :-)
- Gaim+Gaim-Encryption
- Seahorse (even newbies want encryption these days, and GPG is included in the default install, so why not Seahorse)

----

As far as offering the user to select packages at install, I would add my agreement to Daniel's point about keeping a single default install. Here's an idea though of perhaps " compromise" solution:

Upon install, there's a basic default set of apps, as there is now. (Which is a pretty good selection, though I agree GIMP could be dropped since realistically how many people will use it? Games could also be dropped.) Then in the Menu system there could be an addition called "Add Package Selections" or something like that. It's a simple script that allows the user to select various package "groups" - along the lines of what HiddenWolf was talking about - "graphics, games, etc." Users select which package "groups" they want (without having to get into the details of which packages are in those groups like Anaconda does), then the script apt-gets all those packages for them. 
Optionally, this could be built into Synaptic, though the novice user might be a little scared off by Synaptic.

---

### Post by HiddenWolf on 2004-11-14
[QUOTE=daniels]Hopefully within the next couple of months.[/QUOTE]

Patience is a virtue! :-D

Thanks mate!

---

### Post by HiddenWolf on 2004-11-14
[QUOTE=daniels]Yeah, sounds pretty reasonable -- I'll bring it up.  The other issue is that of alternatives (e.g. ubuntu-desktop depending on 'totem-gstreamer | totem-xine') so people can install other stuff and keep u-d.[/QUOTE]

Thanks man. You'd really make me a happy man, doing that.

The alternatives, well, Ubuntu is the best I've seen in any distro so far, and I'm not so much of a diehard user I know all the good stuff out there. it's the occational program I run across that I'd like replaced.
Totem etc, with the other codec, it could run dvd's, but i'd break ubuntu-desktop.
I'll not complain about that too much.

Perhaps it's a good idea to add a sticky to allow for a central place to gather the discussion about alternatives etc?
I know, you'll get a thousand opinions, but this way, you get a thousand threads.

---

### Post by TravisNewman on 2004-11-14
[QUOTE=zerohalo]
If it can't make it by Hoary release, then perhaps it could be added to the Ubuntu Main repository later as package that users can upgrade to once it comes out.
[/QUOTE]

That won't happen... only security updates get added to stable/main

---

### Post by HiddenWolf on 2004-11-14
[QUOTE=panickedthumb]That won't happen... only security updates get added to stable/main[/QUOTE]

Ohh, well. It'll end up in Ubuntu sooner or later. If not hoary, then the next release.
Being an unstable-addict, that's fine by me :-)

Other users could just get it from unstable, then change sources.list back to stable, and be happy ever after.

---

### Post by bvc on 2004-11-14
I'd like control over the volume icon/s in the panel again. Seems they've hardcoded it or soemthing because none of my themes iconrc's change it. ](*,)

---

### Post by EdCrypt on 2004-12-18
[QUOTE=MaZiNgA]
*Graphical Installer
[/QUOTE]

Somebody please. help [this](http://www.debian.org/devel/debian-installer/gtk-frontend) 
 A gtk frontend to the debian-installer.

---

### Post by Ribs on 2004-12-18
[QUOTE=EdCrypt]Somebody please. help [this](http://www.debian.org/devel/debian-installer/gtk-frontend) 
 A gtk frontend to the debian-installer.[/QUOTE]That project looks dead to me. No updates in over a year.

In my humble opinion, a graphical installer should be the last things the devs should worry about. The text installer works, and it works damned well. It's easy to use. Yes, I agree, it's more ugly than a pretty graphical installer would be. But you only ever see it once (I hope!). You're only ever using it for half an hour max.

A graphical installer would be expensive; uses more memory, which therefore makes it slower. Uses precious space on the CD-Rom. Will take a lot of time and effort to get right.

The time and effort can be better spend elsewhere.

-Ribs.

---

### Post by EdCrypt on 2004-12-18
[QUOTE=Ribs]That project looks dead to me. No updates in over a year.
[/QUOTE]
That's why I said help.

[QUOTE=Ribs]
In my humble opinion, a graphical installer should be the last things the devs should worry about. The text installer works, and it works damned well. It's easy to use. Yes, I agree, it's more ugly than a pretty graphical installer would be. But you only ever see it once (I hope!). You're only ever using it for half an hour max.
[/QUOTE]
You don't need. I don't need. In the end, maybe no one **really** needs, but some people seems to **hardly** want. It can be simply optional.

[QUOTE=Ribs]
A graphical installer would be expensive; uses more memory, which therefore makes it slower. Uses precious space on the CD-Rom. Will take a lot of time and effort to get right.

The time and effort can be better spend elsewhere.
[/QUOTE]

I agree with you about the performance and space stuff, despite that I don't think it is soooo critical that something like this can't be done. And about time, if I learn  gtk, as I wish,  it is something i would wast **my** time  :-D

---

### Post by simonsmith.uk@gmail.com on 2004-12-19
[QUOTE=MaZiNgA]Hey, new guy here...Just switched from Debian Sarge and I gotta say I LOVE this distro! Still I have just a few wishes for next release:
 
*Bootsplash
*Control Center
*Graphical Installer

It would be the perfect distro wouldn't it?[/QUOTE]
 how about including  all the stuff needed for [common] connection to the web ? drove me crazy having to search for bits for my speedtouch modem. Other than this oversight Ubuntu is a real XP killer .... and better multimedia support would be nice

---

### Post by Ribs on 2004-12-19
[QUOTE=simonsmith.uk@gmail.com]and better multimedia support would be nice[/QUOTE]
I've heard that this is being worked on. Don't recall where I saw it tho  :-k

---

### Post by shimon on 2004-12-19
personally i wound like this following bug fixed
[[IMG]http://img75.exs.cx/img75/4025/bug0io.th.png[/IMG]](http://img75.exs.cx/my.php?loc=img75&image=bug0io.png)
root/sudo 
gtk+ are all wirod

---

### Post by eldrich_rebello on 2004-12-19
how about more language support?indian languages to be specific.would get a billion more users in no time :-D  :-D  :-D

---

### Post by EdCrypt on 2004-12-19
[QUOTE=eldrich_rebello]how about more language support?indian languages to be specific.would get a billion more users in no time :-D  :-D  :-D[/QUOTE]
If you are talking about the Live cd, I agree. My vote is to pt_BR

---

### Post by MaZiNgA on 2004-12-19
[QUOTE=shimon]personally i wound like this following bug fixed
[[IMG]http://img75.exs.cx/img75/4025/bug0io.th.png[/IMG]](http://img75.exs.cx/my.php?loc=img75&image=bug0io.png)
root/sudo 
gtk+ are all wirod[/QUOTE]
 Hmmm I must be blind but.....where is this bug exactly?? 
I've been staring about 10 minutes at the image and it seems cool...

---

### Post by TravisNewman on 2004-12-19
Ditto, maybe it's the different colored bar on the panel? I think that's because of an applet though, but I can't tell...

---

### Post by shimon on 2004-12-19
[QUOTE=MaZiNgA]Hmmm I must be blind but.....where is this bug exactly?? 
I've been staring about 10 minutes at the image and it seems cool...[/QUOTE]
the widgets there not following my root theme or personal

---

### Post by shimon on 2004-12-19
[QUOTE=panickedthumb]Ditto, maybe it's the different colored bar on the panel? I think that's because of an applet though, but I can't tell...[/QUOTE]
no its using a diffrent widget set here i'll sudo gtk-demo and have a normal one running you will see

---

### Post by shimon on 2004-12-19
[[IMG]http://img71.exs.cx/img71/1981/screenshot9sa.th.png[/IMG]](http://img71.exs.cx/my.php?loc=img71&image=screenshot9sa.png)

---

### Post by uggeli on 2004-12-21
[QUOTE=eldrich_rebello]how about more language support?indian languages to be specific.would get a billion more users in no time :-D[/QUOTE]


Or maybe 'better' languagesupport. I've complaining this earlier once but I say it once again. If you have to mix two languages so let it be english + the language what system is localized. In my system english + finnish would be ok, but for some reason there is allso swedish if I chooce finnish system. :D


And continuing my whislist to..

So many times mentioned bootsplash with verbose mode would be great. And if possible some 'tool' which makes easier for newbies to change backroundimage for bootsplash.  I really don't know how to add picture your own so I don't know is it even reasonable to do such kid 'tool'.

Hardware recognation could be little better, bit like in knoppix which got my integrated soundgard (via ac97 on msi k7t266pro board) work ok. With ubuntu warty & hoary 'beta' sound is working allso but soundquality is worse. And more models of usb-webcam working out of box would be superb.

More repositorys out of box or more packages to default repositorys so you don't have to edit sources.list file. Editing isn't hard part, but after fresh installation it  takes some time to find what resositorys you need to add. Sure there is universy ready, just commented but  'debian-merillat' and others you need to follow some how-to's should be there right out of box.

And some of newbies would like to use klik? It works in knoppix so I guess it's possible to add it in ubuntu. Klik is app like linspires click'n run.

SE-Linux and firewall.



Well I quess that's enough.. :D Hopefully some of those will be in Hoary and some others in later versions.. :) Thanks for great distro!

---

### Post by Gibbz on 2004-12-21
-the new gimp 2.2 i think it is...
-open office 2.xx i dont mind if its beta still by then :)
-firefox 1.0 as default browser
-ati/nvidia driver to be automatically installed during the installation, i really liked that about xandros, 3d works right away!
-the new ati/nvidia/nforce drivers if they ever come out
-wouldnt mind seeing a c++ IDE such as anjuta come in there also it can be hard to get linux ide running correctly....

---

### Post by deception on 2004-12-21
As more people install Ubuntu on laptops with wireless connections, I would like to see more WNIC drivers link linksys compiled into the kernel by default.

---

### Post by shimon on 2004-12-21
[QUOTE=Gibbz]-the new gimp 2.2 i think it is...
[/QUOTE]
already in debian/hoary
> 
-open office 2.xx i dont mind if its beta still by then :)

if its beta it will only have some stuff backported into the current version
> 
-firefox 1.0 as default browser

i wound rather see firefox 1.1 as its due in march and ubuntu hoary is frezzing in april
> -the new ati/nvidia/nforce drivers if they ever come out

they must or we have to all go back to xfree86 :( anyway all of them have made drivers for xorg beside ati which should be finished making one nowish
> -wouldnt mind seeing a c++ IDE such as anjuta come in there also it can be hard to get linux ide running correctly....
 it in universe and i hope it NEVER becomes part of a default install n00bs are not programmers and wound hate to see such an app installed

---

### Post by Gibbz on 2004-12-21
my brothers a linux n00b who programs in c++ his opengl engine, but it doesnt really need to work in linux anyway....

Would like to see 32bit software(emulated?) to run on the 64bit version, i know theres been some issues there....

include video lan(VLC) one of the best media players around!

---

### Post by Rhodan on 2004-12-22
Well from reading through all the posts, I'd like to see the following of what has already been mentioned
> 
A bootsplash - with an option for verbose mode.
A graphical installer - with a choice for text mode.
Being able to choose which packages are to be installed.
A choice of what arch kernel you want to have installed.
Firefox/Thunderbird/ rather than MozillaSuite/Evolution.
A decent CD/DVD burning app.
Native NVIDIA/ATI drivers

This is just my opinion so don't flame !  :D

---

### Post by charleyramm on 2004-12-22
Wow, i found the exact thread i was looking for. Ok here are my grievances:

 the wireless signal monitor doesn't go away when i unplug my wireless card
(love the wireless support mostly though)
also, the wireless signal monitor could 'link' to wireless config when clicked on. 
 
gstreamer0.8mad isn't installed by default, but rythmbox is. Rythmbox died quite badly when i used to throw mp3s at it, and most radio stations. So i installed xmms, and only later found out about 'gstreamer0.8mad' Which lets rythmbox handle mp3. 
 i dont really care why it it's in universe. mp3 is defacto standard. everyone uses it and if it doesnt work, out of the box, it is really annoying.   ](*,) 

Also, i think I heard this was sorted, but the menus are really confusing. for example, Synaptic is in Computer/ System configuration, but not in Applications/ System tools. 
 I actually like a lot of the menu layout, but it needs more though putting in to it. 
 
 i am not running hoary at the moment, so i might have missed things that are already 'in there'. But i am not a developer, im a user and im quite happy to stick with the current 'stable' version  until someone recommends I change. 

 I hope you can see this as constructive, as i haven't taken a lot of care to be nice in it. Just needed to get some points accross.   

 Thanks!

---

### Post by SKLP on 2005-01-07
My wishlist (am i missing something?):
       
       * USplash
       
       * "Laptop" Suspend
       
       * Sound system improvement:
             - complete removal of esd(because it sucks)
 - (kernel-level) oss emulation disabled by default (the module should remain), it needs to be removed IMO because it's not dmix-compatible IIRC
 - automatic dmix/asym if there's not enough channels available, i mean if you have 4 channels f.e it lets you use 3 channels normally and then if some app tries to access sound (the fourth) a dmixer is attached to channel 4, enabling unlimited alsa channel availability
     - all stuff in hoary/main should be compiled without oss and esd support and have alsa support working
     - aoss(or alsa-oss) should be included in main
       
 * OpenOffice.org 2.0 (+ langugage and dictionary should be installed [and selected as docs default language etc] according to what language you choose in the installer)
       
 * Firefox 1.1 (patched version that should use gecko thru shared memory instead of have its own duplicated codebase(like other apps like epiphany, monos gecko-sharp) to save memory, language packs installed based on installer lang, gnome open/save/print dialogs, the selected gnome theme's icons)
       
       * Patched Thunderbird (the same stuff as firefox) [evo should stay the default]
       
 * GStreamer fixes (I know this is not the gstreamer bugzilla but whatever): alsasink doesn't work for me unless i specify the device like this alsasink device=hw:0, that's a stupid bug...
       
       * Composite enabled by default... built-in metacity compositor (I know the current metacity compositor sucks)
   
   * A graphical installer would be nice (I really like the current installer but a graphical might be easier for newbies)
 
 * Reiser4 support in ubuntu kernels (something that would be nice is also a ck-based ubuntu-patched kernel, f.e something like linux-image-ck-k7)
       
       And by the way, thx very much for the current ubuntu, it's  the best distro yet!!
       Go ubuntu!
   
   EDIT: Added graphical installer

---

### Post by testament on 2005-02-03
It would be great if the hoary release featured those:

# supermount

# lmsensors 

#bootsplash

---

### Post by Lovechild on 2005-02-04
[QUOTE=testament]It would be great if the hoary release featured those:

# supermount

# lmsensors 

#bootsplash[/QUOTE]

Supermount is a dangerously wrong implementation of a good idea, we already provide what supermount does and more with HAL, pmount and g-v-m.

lm-sensors, I think the grander scheme is to use kevent and sysfs to get such information, I think that's the better option at least.

Bootsplash, seconded, there's the usplash effort but I haven't seen anything from their side and I'm beginning to doubt if it'll make Hoary.. disappointing

---

### Post by Dylanby on 2005-02-04
Another vote against esd.

Can't wait for polypaudio (Grumpy?).

---

### Post by Randabis on 2005-02-04
[QUOTE=Lovechild]
Bootsplash, seconded, there's the usplash effort but I haven't seen anything from their side and I'm beginning to doubt if it'll make Hoary.. disappointing[/QUOTE]
There's still a few months to go yet. I know the feature freeze is soon, but I think usplash would be an exception. I wonder what's going on with it at any rate, the usplashtodo hasn't been updated in a month.

---

### Post by jnoreiko on 2005-02-05
I think an installer partition tool that offers an option between "wipe everything" and "edit the partition table by hand".

SuSE has this -- it looks at the hard disks and suggests to the user what partitions are needed (eg boot, swap, and so on) and the user can then ok it or tweak it a little.

---

### Post by inuchan on 2005-02-05
Actually I 'd prefer either
# NO bootsplash
or 
# bootsplash with scrolling data down a side or at the bottom

Not having a bootsplash has saved me too many times for me to want one now.

---

### Post by daniels on 2005-02-05
You can disable usplash if you want to.

---

