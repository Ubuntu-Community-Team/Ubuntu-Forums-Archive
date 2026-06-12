---
title: "Been thinking of making my own distro"
date: 2009-03-16
forum: The Cafe
---

### Post by SunnyRabbiera on 2009-03-16
As the future gets more uncertain for my personal life, I am thinking of making my more public life more active to make up for my own personal drought.
Lately I have been thinking of just giving it in and start making my own linux distro.
I dont think Ubuntu really has any direction right now it seems, I have been getting more distant from Ubuntu and branching out a bit.
As of right now I am considering doing this:
Take a simple base of Ubuntu/Debian packages (as I am most familiar with a debian system), put them together and start working on my own distro.
I am considering doing this:
Making it ubuntu based to start off with, then branch off into a more debian like release scheduel.
I am probably going to base it on Hardy as I feel intrepid too unsturdy.
It will be KDE 3 based, since Kubuntu is not going to be LTS with its 8.04 release and will end official support in October, this new distro will pick up the slack where it will leave off.
It will ship with Synaptic instead of adept, it will also ship with firefox and Thunderbird.
In a way it will be more like Simplymepis as opposed to Kubuntu, at least in terms of packaging, I will debate on rather if I should just ship flash and codecs by default.
I live in the US but to be honest, I dont give a crap.
If Adobe, Microsoft and every other greedy company wants to sue me let them go ahead.
I am mainly considering this distro because of Kubuntu's decisions to cut support for A hardy release in october, because they were silly enough to hop into the KDE 4 bandwagon.
I just dont know anymore, I like Ubuntu, I like its community but the distro itself seems to be cloudy in its future.

---

### Post by Kosimo on 2009-03-16
Good luck dude ;)

---

### Post by SunnyRabbiera on 2009-03-16
Thats mam actually :D
The Avatar throws people off.

---

### Post by pwnst*r on 2009-03-16
> **SunnyRabbiera said:**
> I will debate on rather if I should just ship flash and codecs by default.
I live in the US but to be honest, I dont give a crap.
If Adobe, Microsoft and every other greedy company wants to sue me let them go ahead.


not sure about this attitude, but i'd try your distro when it's beta time.

---

### Post by JackieChan on 2009-03-16
Put Songbird, VLC, Skype, Kino, Record my desktop, and Openoffice 3 as default programs. Be sure to make the default torrent client kTorrent (i've found it to much much better than what Ubuntu gives). Give Firefox the flash and java plugins automatically, it's annoying having to install them. Oh, and don't forget to configure it to automatically be able to read zip files. ;)

Good luck!

---

### Post by Vince4Amy on 2009-03-16
> It will ship with Synaptic instead of adept, it will also ship with firefox and Thunderbird.

How about KPackageKit implement PackageKit into your distro.

> It will ship with Synaptic instead of adept, it will also ship with firefox and Thunderbird.

To keep things legal here's an idea. Make a couple of simple bash scripts which can be executed on double click, then if people want the codecs or flash this script will install it, it will also show a legal disclaimer beforehand.

---

### Post by rasmus91 on 2009-03-16
> not sure about this attitude, but i'd try your distro when it's beta time.

Watch out man!

I'd try your distro when the beta is out :)

---

### Post by damis648 on 2009-03-16
Good Luck. I will for sure try your distro out if you go through with it. :popcorn: Right now Ubuntu is still perfect for me, though I might go to Arch or something different at some point.

---

### Post by pwnst*r on 2009-03-16
> **rasmus91 said:**
> Watch out man!

I'd try your distro when the beta is out :)

...for?

---

### Post by Mehall on 2009-03-16
I'll try it!

Can I just ask though...


will you have *some* KDE 4.2.1 support at least? I like KDE4.2.1, and it IS where things are headed. Even if the point is to have a better supported distro, it's best to get ready for future changes,

Just like Debian has "stable" and "testing", so should you.

Just my $0.02

---

### Post by Bölvaður on 2009-03-16
> **Mehall said:**
> I'll try it!

Can I just ask though...


will you have *some* KDE 4.2.1 support at least? I like KDE4.2.1, and it IS where things are headed. Even if the point is to have a better supported distro, it's best to get ready for future changes,

Just like Debian has "stable" and "testing", so should you.

Just my $0.02

perhaps that may be too much work :-/

the codecs shouldn't come right off the live cd, but should be hard to not install them "by accident". To minimize all effort to put into that you can just have bash script on the desktop that installs everything and then deletes it self after checking if flash and mp3 has been installed... like a simple beginning, looking forward to the gui later on in life.

Would preload be in as default?

---

### Post by tbroderick on 2009-03-16
> **SunnyRabbiera said:**
> 
I just dont know anymore, I like Ubuntu, I like its community but the distro itself seems to be cloudy in its future.

Why not help (K)Ubuntu by joining the development team instead?

---

### Post by Simian Man on 2009-03-16
Gosh just the other day I was thinking there aren't enough Debian-based distros.</sarcasm>  But seriously, changing the packages included by default does *not* make a new distro.  What are you hoping to gain by this?

---

### Post by SunnyRabbiera on 2009-03-16
> **Mehall said:**
> I'll try it!

Can I just ask though...


will you have *some* KDE 4.2.1 support at least? I like KDE4.2.1, and it IS where things are headed. Even if the point is to have a better supported distro, it's best to get ready for future changes,

Just like Debian has "stable" and "testing", so should you.

Just my $0.02

KDE 4 support will be limited, until I feel it has reached a level where its become mature and stable I will include it.
KDE 4 is promising dont get me wrong but a lot of people still dislike it, or feel it still too experimental.
Granted KDE 4.2.1 is pretty neat but in terms of functionality its still behind KDE 3.


> **Bölvaður said:**
> perhaps that may be too much work :-/

the codecs shouldn't come right off the live cd, but should be hard to not install them "by accident". To minimize all effort to put into that you can just have bash script on the desktop that installs everything and then deletes it self after checking if flash and mp3 has been installed... like a simple beginning, looking forward to the gui later on in life.

Would preload be in as default?

I will think about it, maybe I will just load medibuntu by default and let people decide for themselves.

> **tbroderick said:**
> Why not help (K)Ubuntu by joining the development team instead?

Well because they are not relying on LTS releases I dont think I can get my foot in the door with my ideas.
I think I might be too radical minded for them

> **Simian Man said:**
> Gosh just the other day I was thinking there aren't enough Debian-based distros.</sarcasm>  But seriously, changing the packages included by default does *not* make a new distro.  What are you hoping to gain by this?

You misunderstand, I am not making a simple repackage here.
It will start off as one granted because I would only have myself as a developer and maintainer.
Once I get the ball rolling on it I will try to get more developers on board.
I dont have a lot of money to hire a lot of developers, and maintaining a repository is a heavy task.
This new distro will start off as a simplistic remix of packaging but as I gain more interest I hope to gain more allies and more developers.
I am probably going to wind up being like PCLinuxOS's Texstar, starting off with packages for an already existing distro (for him it was mandriva)
And then branch off on my own once I get a small team of developers.
I am only going to start with a debian base because its what I know, I know how to build, create and even maintain my own debian packages.
Its what I am familiar with.
This distro will start off as a small side project like all linux's do but I hope to expand.

---

