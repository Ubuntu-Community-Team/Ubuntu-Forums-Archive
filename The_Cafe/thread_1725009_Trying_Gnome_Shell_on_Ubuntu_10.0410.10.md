---
title: "Trying Gnome Shell on Ubuntu 10.04/10.10"
date: 2011-04-09
forum: The Cafe
---

### Post by Nonno Bassotto on 2011-04-09
Is there a way to try the new Gnome Shell on Ubuntu 10.04 or 10.10? Ideally I would like to have up to date packages (the final release of Gnome 3 was out a few days ago) and it should be an alternative desktop environment, so I could choose at login whether to use that or plain Gnome 2, without repercussions on the Gnome 2 behaviour.

I know an experimental PPA exists, but it is only for Ubuntu 11.04, and I'm not sure whether it could break anything.

---

### Post by el_koraco on 2011-04-09
well, you could build it from source.

---

### Post by DeadSuperHero on 2011-04-09
I seem to recall a Gnome 3.0 PPA. It just broke a lot of Gnome 2.x stuff when I installed it, because it replaced a lot of my current libraries.

> [https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)

---

### Post by mikewhatever on 2011-04-09
> **DeadSuperHero said:**
> I seem to recall a Gnome 3.0 PPA. It just broke a lot of Gnome 2.x stuff when I installed it, because it replaced a lot of my current libraries.

That's cause the ppa is for Natty 11.04. Don't think there ever will be a way to try Gnome3 on older Ubuntu versions, at least not non-destructively.

---

### Post by Nonno Bassotto on 2011-04-09
Ok, so there is another option. I don't want to dist-upgrade right now, but it would be fine to install Ubuntu 11.04 together with my current Ubuntu.

The only thing that worries me is the home: will I able to share it? I would like to avoid having two different versions of whatever program I absolutely need (say evolution, firefox, nautilus, shotwell...) with incompatible configurations, be it in dotfiles or in gconf, thus breaking it maybe in both environments.

Any advice for this?

---

### Post by mikewhatever on 2011-04-09
Not sure why you want a shared home just for trying Gnome3. You might remove it after a day or two, or the installation might not work at all.
I'd suggest running Fedora15 from a cd/usb. It should have the latest Gnome - perfect for testing and no commitments.

---

### Post by Nonno Bassotto on 2011-04-09
I already tried Gnome 3 from a live CD, and I like it. I actually want to try whether I can use it for daily work. And for that I need to use my actual home.

If it works fine, I will wipe out my current Ubuntu install. Otherwise the new 11.04 with the Gnome 3 PPA

---

### Post by gnomeuser on 2011-04-09
The GNOME3 PPA still has a lot of work to do, currently you have to do a lot of hand tweaking to get it installed correctly. Even then your GNOME3 experience is still not going to be as integrated as what the liveUSB distros offer since Ubuntu is patched head and toe for things like Application Indicators which.. well screws things up.

As for earlier versions of Ubuntu I think hand compiling using e.g. jhbuild is your best bet.

For now I would recommend waiting a few weeks to let things settle down and give the PPA maintainers time to gut all the Ubuntu specific tech patches from the required packages.

---

### Post by Merk42 on 2011-04-09
If you just want GNOME Shell in 10.10 [here are directions to build from source](http://ubuntuforums.org/showthread.php?t=1603874)
Though I do agree with gnomeuser that your best bet is probably just wait for 11.04 to be released at the end of the month and the GNOME 3 PPA to stabilize.

---

### Post by Nonno Bassotto on 2011-04-09
The fact is that I do NOT want to upgrade to 11.04 until I'm sure that Gnome 3 works fine for me (Unity does not). So I'd need a way to try it out for more than half an hour on a live cd, and actually do some work with it.

---

### Post by NightwishFan on 2011-04-09
I still recommend you build from source. It lets you use existing gnome 2 applications and the shell and a few bits of gnome 3 stuff on top. The best tutorial I found is here:
[http://ubuntuforums.org/showthread.php?t=1603874&highlight=gnome-shell](http://ubuntuforums.org/showthread.php?t=1603874&highlight=gnome-shell)

It worked for me on Debian Testing.

---

### Post by bardor on 2011-04-09
gnome3 in ubuntu 10.10 is gnome2 with and old gnome3 shell atleast that is what i got not what i was expecting, tested a fedora based livecd on a netbook there i got full gnome3 desktop as it looks on gnome3.org, i allso ran archlinux in virtualbox and installed gnome3 from testing repos and i got a nice new gnome2 like fallback interface, so id say if you want real gnome 3 now i would not use ubuntu.:o

---

### Post by irv on 2011-04-09
Glad I read through this thread. I backed off:  I had already added the ppa:gnome3-team/gnome3 to my repository but I didn't launch Gnome 3 by replacing the gnome-shell, so I removed the ppa and I will just stay with 2.32.0 unitl the finial release of 11.04.
Thanks for all the advice.

---

### Post by wolfen69 on 2011-04-09
> **gnomeuser said:**
> The GNOME3 PPA still has a lot of work to do, currently you have to do a lot of hand tweaking to get it installed correctly.

Huh? I installed gnome3/shell without a hitch. All I did was add the ppa and
```
sudo apt-get dist-upgrade
```
```
sudo apt-get install gnome-shell
```
Been running perfect without a problem. But then again, I do this on an extra hard drive so I have nothing to lose.

---

### Post by gnomeuser on 2011-04-09
> **wolfen69 said:**
> Huh? I installed gnome3/shell without a hitch. All I did was add the ppa and
```
sudo apt-get dist-upgrade
```
```
sudo apt-get install gnome-shell
```
Been running perfect without a problem. But then again, I do this on an extra hard drive so I have nothing to lose.

This is a sign of how rapidly the problems of packaging are getting ironed out. Only a few days ago it was much more problematic to get to a working GNOME3 desktop with correct theming.

---

### Post by irv on 2011-04-09
wolfen69 what version of Ubuntu are you running it on?

---

### Post by DeadSuperHero on 2011-04-09
> **gnomeuser said:**
> This is a sign of how rapidly the problems of packaging are getting ironed out. Only a few days ago it was much more problematic to get to a working GNOME3 desktop with correct theming.

Absolutely. I see this as nothing but good news.

---

### Post by wolfen69 on 2011-04-09
> **irv said:**
> wolfen69 what version of Ubuntu are you running it on?

I installed it on top of Xubuntu 11.04

---

### Post by Supergoo on 2011-04-10
I have heard that Ubuntu us not playing well with Gnome 3 now, if you want to get a good Idea you might want to use Fedora. Thats what I am running right now and it looks pretty good.

---

### Post by irv on 2011-04-10
> **wolfen69 said:**
> I installed it on top of Xubuntu 11.04

Yes I have been hearing good things about Gnome3 in 11.04, but not so in 10.04 and 10.10 because of the repositories being for 11.04. This is causing problem in these versions.

---

### Post by JDShu on 2011-04-10
> **Supergoo said:**
> I have heard that Ubuntu us not playing well with Gnome 3 now, if you want to get a good Idea you might want to use Fedora. Thats what I am running right now and it looks pretty good.

Agreed. Fedora 15 is very stable for me right now.

---

### Post by Redsandro on 2011-05-03
> **irv said:**
> Yes I have been hearing good things about Gnome3 in 11.04, but not so in 10.04 and 10.10 because of the repositories being for 11.04. This is causing problem in these versions.

Too bad. I really like Gnome Shell, but I want to stick to LTS (10.04) for my work machine. I would like to have Gnome 3 Shell but not compromise the stability of my machine, which non-LTS releases have proven to do again and again.

---

### Post by achilleas.k on 2011-05-26
> **Redsandro said:**
> Too bad. I really like Gnome Shell, but I want to stick to LTS (10.04) for my work machine. I would like to have Gnome 3 Shell but not compromise the stability of my machine, which non-LTS releases have proven to do again and again.

Same situation here. I've been contemplating going over to Fedora 15, but I'd rather stick with Ubuntu 10.04 because I don't feel like setting up my OS these days.

I'm probably just going to backup everything, install gnome-shell on 10.04 and see how that goes. If it all goes to hell, then I'll think about whether I'll restore the backup or move to Fed 15.

I'll let you know how that goes. :)

---

### Post by Zlatan on 2011-05-26
> **achilleas.k said:**
> Same situation here. I've been contemplating going over to Fedora 15, but I'd rather stick with Ubuntu 10.04 because I don't feel like setting up my OS these days.

I'm probably just going to backup everything, install gnome-shell on 10.04 and see how that goes. If it all goes to hell, then I'll think about whether I'll restore the backup or move to Fed 15.

I'll let you know how that goes. :)

if you just want some change, try [docky]("http://do.davebsd.com/wiki/Docky") :)

---

### Post by irv on 2011-05-26
> **Redsandro said:**
> Too bad. I really like Gnome Shell, but I want to stick to LTS (10.04) for my work machine. I would like to have Gnome 3 Shell but not compromise the stability of my machine, which non-LTS releases have proven to do again and again.
I don't know what you use for a work machine, but what I do with mine is keep two hard drive and use one for testing and if I get everything working the way I want, I just stick with it. Works for me.

By the way I am back to 11.04 with Unity. I have done so customizing and I am getting to like it.

What I am waiting for now is 11.10 to see if it come with Unity and or Gnome 3. I think it is only a matter of time that someone will come along with Ubuntu running Gnome 3 as the DE. and hopefully all the bug will be minimized.

Also, who know maybe Ubuntu will be released with a polish up Unity. Only time will tell. One thing in closing, I do not plan to leave Ubuntu as my distro of choice.

---

### Post by Zlatan on 2011-05-27
> **irv said:**
> I don't know what you use for a work machine, but what I do with mine is keep two hard drive and use one for testing and if I get everything working the way I want, I just stick with it. Works for me.

By the way I am back to 11.04 with Unity. I have done so customizing and I am getting to like it.

What I am waiting for now is 11.10 to see if it come with Unity and or Gnome 3. I think it is only a matter of time that someone will come along with Ubuntu running Gnome 3 as the DE. and hopefully all the bug will be minimized.

Also, who know maybe Ubuntu will be released with a polish up Unity. Only time will tell. One thing in closing, I do not plan to leave Ubuntu as my distro of choice.

Unity **IS** Gnome3

---

### Post by wolfen69 on 2011-05-27
> **irv said:**
> I don't know what you use for a work machine, but what I do with mine is keep two hard drive and use one for testing and if I get everything working the way I want, I just stick with it. Works for me.


Bingo. I always have 3 drives, and everything backed up twice. Then I have fun installing stuff.

---

### Post by wolfen69 on 2011-05-27
> **Zlatan said:**
> Unity **IS** Gnome3

Huh?

---

### Post by Zlatan on 2011-05-27
> **wolfen69 said:**
> Huh?

Meh, I mean that Ubuntu will anyway come with Gnome3 and Unity interface. Gnome3 **is not** an interface.

---

### Post by wolfen69 on 2011-05-27
> **Zlatan said:**
> Meh, I mean that Ubuntu will anyway come with Gnome3 and Unity interface. Gnome3 **is not** an interface.

Wow. it's amazing how we all see things differently.

---

### Post by 23dornot23d on 2011-05-27
[B][http://en.wikipedia.org/wiki/GNOME](http://en.wikipedia.org/wiki/GNOME)

GNOME[/B] (pronounced [/&#609;&#712;no&#650;m/]("http://en.wikipedia.org/wiki/Wikipedia:IPA_for_English"), or sometimes [/]("http://en.wikipedia.org/wiki/Wikipedia:IPA_for_English")[n]("http://en.wikipedia.org/wiki/Wikipedia:IPA_for_English#Key")[o&#650;]("http://en.wikipedia.org/wiki/Wikipedia:IPA_for_English#Key")[m]("http://en.wikipedia.org/wiki/Wikipedia:IPA_for_English#Key")[/]("http://en.wikipedia.org/wiki/Wikipedia:IPA_for_English"))[[1]]("http://en.wikipedia.org/wiki/GNOME#cite_note-0")[[2]]("http://en.wikipedia.org/wiki/GNOME#cite_note-1") is a [desktop environment]("http://en.wikipedia.org/wiki/Desktop_environment") / [graphical user interface]("http://en.wikipedia.org/wiki/Graphical_user_interface") that runs on top of a computer [operating system]("http://en.wikipedia.org/wiki/Operating_system").

---------------------------------------------

**Gnome-Shell** at the moment is the only desktop taking advantage of the new
Gnome 3 interface.

**UNITY** AFAIK ..... is on Gnome 2.32.


If you want to try them both ...... the 64 bit Dvd will let you run them together - still in testing and works on Nvidia - but may give you some idea of what Gnome Shell is like
hope this helps in some way ..... its a big download at 1.6 Gig though.

---

### Post by Zlatan on 2011-05-27
> **23dornot23d said:**
> [B][http://en.wikipedia.org/wiki/GNOME](http://en.wikipedia.org/wiki/GNOME)

GNOME[/B] (pronounced [/&#609;&#712;no&#650;m/]("http://en.wikipedia.org/wiki/Wikipedia:IPA_for_English"), or sometimes [/]("http://en.wikipedia.org/wiki/Wikipedia:IPA_for_English")[n]("http://en.wikipedia.org/wiki/Wikipedia:IPA_for_English#Key")[o&#650;]("http://en.wikipedia.org/wiki/Wikipedia:IPA_for_English#Key")[m]("http://en.wikipedia.org/wiki/Wikipedia:IPA_for_English#Key")[/]("http://en.wikipedia.org/wiki/Wikipedia:IPA_for_English"))[[1]]("http://en.wikipedia.org/wiki/GNOME#cite_note-0")[[2]]("http://en.wikipedia.org/wiki/GNOME#cite_note-1") is a [desktop environment]("http://en.wikipedia.org/wiki/Desktop_environment") / [graphical user interface]("http://en.wikipedia.org/wiki/Graphical_user_interface") that runs on top of a computer [operating system]("http://en.wikipedia.org/wiki/Operating_system").

---------------------------------------------

**Gnome-Shell** at the moment is the only desktop taking advantage of the new
Gnome 3 interface.

**UNITY** AFAIK ..... is on Gnome 2.32.


If you want to try them both ...... the 64 bit Dvd will let you run them together - still in testing and works on Nvidia - but may give you some idea of what Gnome Shell is like
hope this helps in some way ..... its a big download at 1.6 Gig though.

OK, show me Gnome3 interface without Gnome-shell...
And Unity will be on top of Gnome3 in Ocelot.

---

### Post by 23dornot23d on 2011-05-27
> **Zlatan said:**
> OK, show me Gnome3 interface without Gnome-shell...
And Unity will be on top of Gnome3 in Ocelot.


I am afraid you got me there ......

Its a little like telling someone to remove the hands off of a clock ..... and looking
at the clock face - 

It shows absolutely nothing looking at a blank clock face with no hands on it 

Even though the mechanism is working behind the scenes .....

But the mechanism - the _***[interface]("http://en.wikipedia.org/wiki/Interface_%28computing%29")***_ it is still there and still works ...... :confused:

So it is still the interface .......

Cannot wait for [_[COLOR=Red]**Oneiric Ocelot**[/COLOR]_]("http://www.techdrivein.com/2011/05/6-important-changes-in-next-ubuntu-1110.html") ...... this is cutting edge - we are the leaders of the pack
what is going on here .....

No waiting around the clock is ticking ..... even though it may have no hands ......

Oh well the music played on ...... :guitar:


We need innovation ...... something on a Cloud and everything written in Java-Script ...
we dream of the future ahead ......

---

### Post by irv on 2011-05-27
> **Zlatan said:**
> OK, show me Gnome3 interface without Gnome-shell...
And Unity will be on top of Gnome3 in Ocelot.

I sure hope you are right. (Fact or Fiction)!

---

