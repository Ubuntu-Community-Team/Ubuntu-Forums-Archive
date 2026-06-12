---
title: "You know what's quite sad?"
date: 2005-05-20
forum: The Cafe
---

### Post by Lowe on 2005-05-20
There seems to be no perfect distro, one that suits all my needs and does what I want it to do, i've tried almost everyone of the top distro's at Distrowatch and some of them had certain stuff i liked, but there wasn't one that had everything i like. I'm going to go through the main ones and tell me what YOU think.

Slackware: 

Pros:Nice no pissing around install, very fast and stable and so far the fastest one to boot that i've tried. Most things seem to install from source easier, i dunno why.

Cons: No decent package manager, while it doesn't seem like much of a problem when you go to install something like VLC you'll run into a lot of problems, it's just too much of a pain to get it how you want it.

Fedora:

Pros: Really nice welcoming distro.

Cons: RPM 

Debian:

Pros: Well, if there is any distro that comes the closest to my needs it's definetly debian. Loads of packages, easy to install all my Video and music apps without too much fuss. The net install almost let's you  build everything how you want it.

Cons: Still seems out of date and i don't really like their release schedule.

Ubuntu:

Pros: Fast, easy to install and does most things out the box.

Cons: I feel it limits you to using gnome, you would have to go to a lot of hassle just to remove it.

Well that's it, out of all the distro's i've tried they feel like the only ones worth mentioning, there is still two distro's i want to try mainly being Archlinux and Gentoo which i still cannot seem to install. Gentoo really looks like something i would like, so it's quite a shame. So i'm just curious, do you think there is a perfect distro that suits almost all your needs? Oh and by the way, i've formatted 25 times in two weeks jumping from distro to distro and i can't sink my feet into any for longer than a day or two. I'm hoping the new debian stable will be really good, but for now i don't know what i'll do, maybe continue to distro hop?

I'm just intrested to see peoples opinions here and since this seems like the friendlist community, i wanted to discuss it here.

---

### Post by the_clown on 2005-05-20
> Cons: I feel it limits you to using gnome, you would have to go to a lot of hassle just to remove it.
Type "custom" at the initial CD-ROM boot prompt during the install. This will install only the base packages, after which you can install only what you need, using 'aptitude' or 'apt-get'.

---

### Post by testingubuntu on 2005-05-20
Fedora  has apt, yum smartpm &synaptic. 

There are HUGH repositories out there for rpm based distros 

dag wieers  <-- over 30000 packages alone here
freshrpms 
ATrpms 
jpackage

then again I use Fedora Core for my server So I know 
June 6th Fedora Core 4 release date!

Gentoo  Hope you like compiling everything from source.  the only good thing i can see from Gentoo is that there isn't a new version released it just keeps getting uipdated.

---

### Post by Lowe on 2005-05-20
[QUOTE=the_clown]Type "custom" at the initial CD-ROM boot prompt during the install. This will install only the base packages, after which you can install only what you need, using 'aptitude' or 'apt-get'.[/QUOTE]

Cheers, i'll try that out tonight on my new drive see if i feel more comfortable. 

> Fedora has apt, yum smartpm &synaptic. 

Maybe i'll try it again some other time, but for me it seemed quite hard still to get everything i wanted. Mind you, the only repository i had was freshrpms. I can't say i've given it a good testing.

---

### Post by jerome bettis on 2005-05-20
i would not recommend gentoo ... 12 hours into a ~14 hour make cycle + portage error = more swearing than you can imagine.   it does somethings well but there's just too many bugs (bleeding edge?) and it can be very frustrating, especially when the devs say "we dunno what's going on here, just install something similar instead..."  ok i'll just use ubuntu then :-P

if your only gripe with ubuntu is gnome why not try kubuntu?

---

### Post by bored2k on 2005-05-20
Perfect distro: Linux from scratch.

Do I like it ? no. Could you like it ? probably. Negative aspects ? you.

---

### Post by Lowe on 2005-05-20
[QUOTE=jerome bettis]i would not recommend gentoo ... 12 hours into a ~14 hour make cycle + portage error = more swearing than you can imagine.   it does somethings well but there's just too many bugs (bleeding edge?) and it can be very frustrating, especially when the devs say "we dunno what's going on here, just install something similar instead..."  ok i'll just use ubuntu then :-P

if your only gripe with ubuntu is gnome why not try kubuntu?[/QUOTE]

Not a big KDE fan, i'm more into Fluxbox. Just put my new harddrive in, and now my dvd writter has gone kinda crazy and is making lot's of noise, i didn't even touch it. :(

---

### Post by nuopus on 2005-05-20
Too bad you havent tried ArchLinux. It installs similar to slackware but has one of the best package managers with dependency checking ... and since it does recursive uninstalls, you can intall KDE and GNOME to choose which you like, then recursively uninstall the entire KDE in one command.

Just like slackware you get just a base command prompt, and if you want gnome you just pacman -S gnome which will install gnome 2.10.1 along with xorg and everything you need.

If you want OpenOffice 2 ... just pacman -S openoffice2.

Greatest thing about arch is when you pacman -S mplayer, you get mplayer along with all of its dependencies AND the full win32 codec pack all of a sudden. No messing around with crap ... if you want to play wmv files, you just pacman -S mplayer and you are done codec and all .. simple.

Arch Linux is by far the most perfect distro out there if you know what programs you want and attempt to learn pacman. I still recommend Ubuntu to the complete beginners though, or people who dont have a good Internet connection.

OH ... and they (arch) even has a tool called hwd that can detect all of your hardware and create howtos on the fly for exactly how you should configure just about all of your hardware, and not just examples ... its tailored to your stuff.


[QUOTE=Lowe]There seems to be no perfect distro, one that suits all my needs and does what I want it to do, i've tried almost everyone of the top distro's at Distrowatch and some of them had certain stuff i liked, but there wasn't one that had everything i like. I'm going to go through the main ones and tell me what YOU think.

Slackware: 

Pros:Nice no pissing around install, very fast and stable and so far the fastest one to boot that i've tried. Most things seem to install from source easier, i dunno why.

Cons: No decent package manager, while it doesn't seem like much of a problem when you go to install something like VLC you'll run into a lot of problems, it's just too much of a pain to get it how you want it.

Fedora:

Pros: Really nice welcoming distro.

Cons: RPM 

Debian:

Pros: Well, if there is any distro that comes the closest to my needs it's definetly debian. Loads of packages, easy to install all my Video and music apps without too much fuss. The net install almost let's you build everything how you want it.

Cons: Still seems out of date and i don't really like their release schedule.

Ubuntu:

Pros: Fast, easy to install and does most things out the box.

Cons: I feel it limits you to using gnome, you would have to go to a lot of hassle just to remove it.

Well that's it, out of all the distro's i've tried they feel like the only ones worth mentioning, there is still two distro's i want to try mainly being Archlinux and Gentoo which i still cannot seem to install. Gentoo really looks like something i would like, so it's quite a shame. So i'm just curious, do you think there is a perfect distro that suits almost all your needs? Oh and by the way, i've formatted 25 times in two weeks jumping from distro to distro and i can't sink my feet into any for longer than a day or two. I'm hoping the new debian stable will be really good, but for now i don't know what i'll do, maybe continue to distro hop?

I'm just intrested to see peoples opinions here and since this seems like the friendlist community, i wanted to discuss it here.[/QUOTE]

---

### Post by nuopus on 2005-05-20
Problem with Fedora Core is if you want things like mplayer WITH win32 codecs, mp3 playback and ability to play DVD movies you have to research and add repositories ... not to mention the installation of apt.

In ArchLinux ... you just pacman -S mplayer to get everything including DVD playback without repository hunting 

And out of all of the other distros, it has the most up-to-date packages including OpenOffice2.


[QUOTE=testingubuntu]Fedora  has apt, yum smartpm &synaptic. 

There are HUGH repositories out there for rpm based distros 

dag wieers  <-- over 30000 packages alone here
freshrpms 
ATrpms 
jpackage

then again I use Fedora Core for my server So I know 
June 6th Fedora Core 4 release date!

Gentoo Hope you like compiling everything from source. the only good thing i can see from Gentoo is that there isn't a new version released it just keeps getting uipdated.[/QUOTE]

---

### Post by DJ_Max on 2005-05-20
All of the distributions you've named were not made for you. Therefore, in your eyes they will not be perfect. If you want a perfect distro, make one yourself. Otherwise use whats there.

I like compiling from source(best way IMO), so I use Gentoo often. Everyone doesn't appreciate software specifically for their systems, so Gentoo wouldn't be a choice.

---

### Post by silver on 2005-05-20
Vector Linux. 

[http://www.vectorlinux.com](http://www.vectorlinux.com)

Loosely based on Slackware. Has VASM (Vector Administrative and Services Menu) and SlApt package management system. Fluxbox, IceWM and XFCE for window managers. v.5.0 is in beta 2 as of last night.

---

### Post by Lowe on 2005-05-20
> **silver]Vector Linux. 

[http://www.vectorlinux.com](http://www.vectorlinux.com)

Loosely based on Slackware. Has VASM (Vector Administrative and Services Menu) and SlApt package management system. Fluxbox, IceWM and XFCE for window managers. v.5.0 is in beta 2 as of last night.[/QUOTE]
Thanks, something new to try.  said:**
> All of the distributions you've named were not made for you. Therefore, in your eyes they will not be perfect. If you want a perfect distro, make one yourself. Otherwise use whats there. 

Oh believe me, if i could i would make my own, but that will never happen. It's just weird because most people find one that is almost the perfect match, while im struggling. Well i'll test out vectorlinux see what it's like.

---

### Post by poofyhairguy on 2005-05-20
[QUOTE=Lowe]
Cons: I feel it limits you to using gnome, you would have to go to a lot of hassle just to remove it.[/QUOTE]


I love using XFCE+Ubuntu on an old box of mine.

---

### Post by Xian on 2005-05-20
[QUOTE=Lowe]Slackware: Cons: No decent package manager, while it doesn't seem like much of a problem when you go to install something like VLC you'll run into a lot of problems, it's just too much of a pain to get it how you want it[/QUOTE]
Look at [Rubix Linux](http://www.rubix-os.org/). 
Slackware-based with pacman for software management.

---

### Post by Lowe on 2005-05-20
[QUOTE=Xian]Look at [Rubix Linux](http://www.rubix-os.org/). 
Slackware-based with pacman for software management.[/QUOTE]

Really like the look of that, thanks a lot for the link. Downloading it too.

---

### Post by bruizer on 2005-05-20
[QUOTE=Lowe]There seems to be no perfect distro, one that suits all my needs and does what I want it to do, i've tried almost everyone of the top distro's at Distrowatch and some of them had certain stuff i liked, but there wasn't one that had everything i like.[/QUOTE]
Many different distros built by many different people for many different reasons. There is no one perfect flavor. However, the great thing about linux is that no matter who creates a flavor, they will tell you exactly how they created it and allow you to add or subtract as you see fit.

Don't like what's in the box? No problem, rebuild and recompile!

Thanks for the interesting read!

---

### Post by totalshredder on 2005-05-21
I haven't heard any mention of Mandriva or Mepis. They're two solid distros that are worth a shot! I might even try Ark linux, it's starting to look pretty sweet :)

Good Luck

(I'm downloading this rubix linux. Very Sweet.)

---

### Post by nuopus on 2005-05-21
[QUOTE=totalshredder]I haven't heard any mention of Mandriva or Mepis. They're two solid distros that are worth a shot! I might even try Ark linux, it's starting to look pretty sweet :)

Good Luck

(I'm downloading this rubix linux. Very Sweet.)[/QUOTE]

Eck mepis. This distribution does not give you a choice. You must use KDE. Yes they have GNOME too, but once you install it you are left with no feeling but disgusted. Its implementation is abismal at best, and they make it look like crap. At least say your distribution is KDE based and leave GNOME out, instead of allowing GNOME users to use MEPIS and give them a sub-standard one. Slackware for example, made the move of taking GNOME out completely because they didnt want to support both .... I respect that more than the way Mepis handles it ... "Lets leave these craps for the dogs".

At least Ubuntu comes with a great looking GNOME, but if you feel you want KDE, you can install a great looking KDE. Arch is the same way .... you have your choice and both are great.

---

### Post by totalshredder on 2005-05-21
[QUOTE=nuopus]Eck mepis. This distribution does not give you a choice. You must use KDE. Yes they have GNOME too, but once you install it you are left with no feeling but disgusted. Its implementation is abismal at best, and they make it look like crap. At least say your distribution is KDE based and leave GNOME out, instead of allowing GNOME users to use MEPIS and give them a sub-standard one. Slackware for example, made the move of taking GNOME out completely because they didnt want to support both .... I respect that more than the way Mepis handles it ... "Lets leave these craps for the dogs".

At least Ubuntu comes with a great looking GNOME, but if you feel you want KDE, you can install a great looking KDE. Arch is the same way .... you have your choice and both are great.[/QUOTE]

The guy obviously doesn't want gnome :roll: A lot of people like mepis, I see no reason why he couldn't like it as well. 

Luke

---

### Post by nuopus on 2005-05-21
[QUOTE=totalshredder]The guy obviously doesn't want gnome :roll: A lot of people like mepis, I see no reason why he couldn't like it as well. 

Luke[/QUOTE]

Well I guess it is a personal preference ... me personally, I just really hate KDE! lol. I was disappointed when a friend told me to try MEPIS after me telling him I hate KDE. He said .. "Well you can just install GNOME", so I figure ya ... "lots of other distros provide both so why not!". Boy was I dead wrong!

If anyone out there thinks they way to try MEPIS because you THINK you can install GNOME on there .... you can! Just prepare to be disgusted at their implementation of it. OR .. do it from scratch from source or just use a debian repo. But if your gonna start doing that, why use MEPIS?

---

### Post by Kyral on 2005-05-22
If you wanna go Gentoo without having to fight through all the crap of compiling, then use VidaLinux. Its basically the Anaconda Installer on a Stage3 Gentoo Install. Very quick install. Only thing is, it doens't seem to like my hardware right now. And Gentoo is also coming out with a graphical installer.

I hope you find the right Distro for you :D

---

