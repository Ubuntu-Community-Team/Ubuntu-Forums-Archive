---
title: "Is it possible to not use apt?"
date: 2009-04-16
forum: The Cafe
---

### Post by CJ Master on 2009-04-16
I'm just wondering...

Apt seems very slow, and way to verbose. Heck, I could come up with a better looking program then apt.

With what little experience I had with Arch, I really liked pacman. Is there any way to change this?

---

### Post by -grubby on 2009-04-16
Probably, but I imagine that apt is so integrated into the system it would cause some breakage or at the very least inconvienances.

---

### Post by Seventh Reign on 2009-04-16
Apt is slow???

Have you tried Portage? .. now THATS slow.

---

### Post by SunnyRabbiera on 2009-04-16
I personally never had issues with apt.

---

### Post by kerry_s on 2009-04-16
> **CJ Master said:**
> I'm just wondering...

Apt seems very slow, and way to verbose. Heck, I could come up with a better looking program then apt.

With what little experience I had with Arch, I really liked pacman. Is there any way to change this?

you must be using some slow repo's.
i agree pacman is much better once you get use to it.
why not just stick with arch? sure it takes some time to set up, but once that's done it's cake.

---

### Post by blithen on 2009-04-16
> **nathangrubb said:**
> Probably, but I imagine that apt is so integrated into the system it would cause some breakage or at the very least inconvienances.
Yeah exactly what I was thinking. You COULD do it, just would you really want the hassle of doing?

@CJMaster
What do you mean? Slow and verbose? Personally I think apt is very efficient. Could you explain a little more?

---

### Post by 4th guy on 2009-04-16
Try compiling from source. Now THAT's slow. :P

---

### Post by ssam on 2009-04-16
you could write you own script based on wget/curl and dpkg.

maybe you can figure out which bit of apt is slow. it has to do quite a lot for each install upgrade.
*download package list
*solve dependencies
*download packages
*unpack packages
*install files
*run install scripts/configuration
*clean up

i am not sure that their is a package manager that does all that faster.

if download bit is slow try some different mirrors. (system->administration->software-sources has a tool to select the best mirror)

if you don't like the verboseness then pipe the output to a file.
apt-get install foo >> apt.log
or use the graphical tools.

---

### Post by frodon on 2009-04-16
You can use aptitude if you wish, some prefer it over apt especially when it comes to remove installed softwares and related dependencies.

---

### Post by barbedsaber on 2009-04-16
I havn't used apt for around 2 months
why?
because I broke it. Was messing around with some config files, and I broke it.
Now it doesn't connect to any servers, just sits there.
I didn't bother fixing it because I was planning on upgrading to jaunty soon anyway, and I was doing a fresh install.
But, when you don't have apt, you miss it.
I wanted to install partimage today, it took over 20 minutes to do, should have take 2 minutes.

the moral of the story is apt > no apt
the sad part is, having just written this, I realised I probably could have used aptitude, ah well.

---

### Post by connorh123 on 2009-04-16
I don't think it's impossible to use an apt, considering it makes lives easier :)

---

### Post by 3rdalbum on 2009-04-16
Apt is fast compared to most other things out there. I haven't tried Pacman.

Dpkg can be frightfully slow on Ubuntu netbooks, but I don't think that's actually dpkg - I think that's the man-db which automatically gets refreshed after every package. There is probably some way of turning off the automatic man-db refreshing which should save time and save a bit of SSD wear and tear, but I haven't researched this yet.

---

### Post by SuperSonic4 on 2009-04-16
Pacman is the fastest thing I've tried. Mind you it's probably due to my whole internet speed going up around the same time as installing arch :p

apt is pretty good but it wouldn't be impossible to live without it, just inconvienient.

---

### Post by samjh on 2009-04-16
> **CJ Master said:**
> I'm just wondering...

Apt seems very slow, and way to verbose. Heck, I could come up with a better looking program then apt.

With what little experience I had with Arch, I really liked pacman. Is there any way to change this?

I don't think you can use anything other than apt on Ubuntu.  Apt is Ubuntu's (and Debian's) package management system.  The only other alternative is to do everything from source!

As for it being slow, apt-get or aptitude is lot faster than say... yast (OpenSUSE) or yum (Fedora/RHEL/CentOS).

---

### Post by Bölvaður on 2009-04-16
> **samjh said:**
> I don't think you can use anything other than apt on Ubuntu.  Apt is Ubuntu's (and Debian's) package management system.  The only other alternative is to do everything from source!

As for it being slow, apt-get or aptitude is lot faster than say... yast (OpenSUSE) or yum (Fedora/RHEL/CentOS).

incorrect, you are able to install other package managers, but there is no point as it will only handle the packages you will get after you install that package manager, and your current package manager (apt) will handle the rest.

When I first started out with ubuntu I installed yum and also packman when it became available to us.
And from that experience I can see how it is useless for most people.

---

### Post by Eisenwinter on 2009-04-16
I guess you can always write a bash script and make yourself an alternative package manager, one that installs programs from source.

Or, one that manages .debs (or whatever package method you wish to use) for you, independently of apt.

---

### Post by Dougie187 on 2009-04-16
You should try yum if you don't like slow and verbose. That is a lot more verbose than apt, and it is also a lot slower.

---

### Post by Simian Man on 2009-04-16
I don't know what you guys are talking about regarding yum.  It is about as fast as apt out of the box, and blows it away once you set up the fastest-mirror and presto plugins.  Also the output is much more readable than apt.  Installing packages with apt is like watching a program puke all over your terminal.  Pacman is also faster and has better output.

---

### Post by SomeGuyDude on 2009-04-16
> **kerry_s said:**
> you must be using some slow repo's.
i agree pacman is much better once you get use to it.
why not just stick with arch? sure it takes some time to set up, but once that's done it's cake.

Arch is like a car that has a 0-60 time of 2 seconds, can drive over speedbumps without rattling, has a beautiful sound system, but every few months catches on fire unexpectedly. If you don't mind dealing with that, the experience is great, but the last Xorg explosion almost got me to scrap Arch permanently.

---

### Post by chucky chuckaluck on 2009-04-16
when i used reiserfs in arch, pacman zoomed (more so than xfs and jfs). maybe using reiserfs in ubuntu might have the same effect on apt (just wondering. i have no idea if this is so).

---

### Post by billgoldberg on 2009-04-16
> **CJ Master said:**
> I'm just wondering...

Apt seems very slow, and way to verbose. Heck, I could come up with a better looking program then apt.

With what little experience I had with Arch, I really liked pacman. Is there any way to change this?

I think pacman is more verbose or around the same as apt.

Both perform as well on my system.

---

### Post by billgoldberg on 2009-04-16
> **chucky chuckaluck said:**
> when i used reiserfs in arch, pacman zoomed (more so than xfs and jfs). maybe using reiserfs in ubuntu might have the same effect on apt (just wondering. i have no idea if this is so).

Well I only use reiserfs and apt-get is as fast as pacman is on my desktop.

Doesn't Reiserfs deal better (read faster) with lots of small writes? That could speed up apt-get.

---

### Post by chucky chuckaluck on 2009-04-16
> **billgoldberg said:**
> Well I only use reiserfs and apt-get is as fast as pacman is on my desktop.

Doesn't Reiserfs deal better (read faster) with lots of small writes? That could speed up apt-get.

apparently, so. it was very fast with pacman, but slow as hell with cplay, so i ultimately switched back to xfs.

---

### Post by Polygon on 2009-04-16
pacman and apt both run at around the same speed on my system, sometimes apt takes a bit longer because some packages have lots of scripts that need to run.

but otherwise, who cares if its verbose? its not like you have limited space in your terminal or anything.

---

### Post by bobmatino17 on 2009-04-16
it is possible, your dealing with Linux, remember? You can have APT on an RPM based machine like Fedora, but it causes many, many, problems. APT is great, ive gone through heck with RPM even with how little ive used it. I would not suggest changing to any other package manager. Unless you want to have your computer having issiues.

---

### Post by wsonar on 2009-04-16
> **4th guy said:**
> Try compiling from source. Now THAT's slow. :P

yea took a couple day's to build gnome on a bsd box from ports



I've never had a problem with Apt- that's why I like debian It's defiantly an easy to use package management tool

---

### Post by SomeGuyDude on 2009-04-16
> **chucky chuckaluck said:**
> when i used reiserfs in arch, pacman zoomed (more so than xfs and jfs). maybe using reiserfs in ubuntu might have the same effect on apt (just wondering. i have no idea if this is so).

ext4 is pretty snappy as well.

---

### Post by calrogman on 2009-04-16
> **CJ Master said:**
> I'm just wondering...

Apt seems very slow, and way to verbose. Heck, I could come up with a better looking program then apt.

With what little experience I had with Arch, I really liked pacman. Is there any way to change this?

Just so you know, apt is a front end for dpkg, apt doesn't output anything, it's dpkg doing that.

---

### Post by Simian Man on 2009-04-16
> **bobmatino17 said:**
> APT is great, ive gone through heck with RPM even with how little ive used it. I would not suggest changing to any other package manager. Unless you want to have your computer having issiues.

Comparing apt to rpm isn't fair.  Apt should be compared to yum and rpm should be compared to dpkg.  Use dpkg directly and you will likely run into troubles too unless you know what you are doing.  But I agree that you should probably just use the tools your distro provides unless you wan breakage.

---

### Post by jenkinbr on 2009-04-16
I like the verboseness of APT.  I always skim through the output, looking for potential problems....

---

### Post by ghindo on 2009-04-16
Please don't say "X is faster than Y" unless you have some actual numbers to back it up.

---

### Post by Mulenmar on 2009-04-16
> **Eisenwinter said:**
> I guess you can always write a bash script and make yourself an alternative package manager, one that installs programs from source.

I. Want. That.

A Ubuntu-based Gentoo!! :popcorn:

---

### Post by Polygon on 2009-04-16
> **jenkinbr said:**
> I like the verboseness of APT.  I always skim through the output, looking for potential problems....

if you have an error, its like OMG OMG OMG ERROR ERROR CAN'T INSTALL 'X' BECAUSE 'Y' IS NOT THERE, ABORT ABORT!

its not THAT hard to spot =P

---

### Post by liamnixon on 2009-04-16
I know there's some hate floating around, but I think yum is terrific and that you should check out Fedora if you don't like apt (I don't either).  In my experience, yum was a bit faster than apt and the output is ***much*** better than apt.  It prints a neat list of programs to be installed, whereas apt is very hard on the eyes.

---

### Post by Kareeser on 2009-04-16
> **jenkinbr said:**
> I like the verboseness of APT.  I always skim through the output, looking for potential problems....

+1

I personally got used to the "verboseness" of apt. I don't notice it anymore, and skim over the static text.

---

### Post by RATM_Owns on 2009-04-17
There's a script somewhere to install Portage on any distro.

---

### Post by gnomeuser on 2009-04-17
I have to admit when I am on Ubuntu I really miss yum. The CLI tools seem to have much nicer output and a more natural syntax for interaction. I really have started to loath dpkg lately, it just seems so frail, just yesterday it's database got in a state where I couldn't do anything and there wasn't any helpful output to indicate the error. It took an hours worth of research just to be able to manage my packages again.. and all I did was apply updates.

No packaging system is close but I had to admit I really like yum for it's tools. The backend I probably would prefer something like Conary and for the overall vision of how packaging fits into the system Exherbo has some interesting ideas especially for user handling.

---

