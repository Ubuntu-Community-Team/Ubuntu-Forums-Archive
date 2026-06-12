---
title: "Help selecting a lightweith OS"
date: 2009-11-04
forum: The Cafe
---

### Post by rigao on 2009-11-04
Hello everybody.

Some time ago I bought a new laptop and my niece, who is 11 years old, is going to inherit my old one.

This laptop is old, and I want her to have a pleasant linux experience (it will be her first OS, no windows pollution, so I think we can make her a big linux fan :D) so, although Xubuntu works, I want to try something different. Can you help me?

What do I require?

1.- It must be stable, because I won't be around to solve things. Maybe I can log in remotely, but it must work reasonable well.

2.- It must have locales, because she does not understand english.

3.- It must be able to put a bottom panel for no use, because the last lines of the screen don't work.

4.- It must have access to as much educational software as possible, as I want her to use this laptop as a teaching tool mainly.

Regarding all this points, I was thinking in Masonux, as some guy in this forum pointed it to me, and it seems to meet all the points (specially it will have access to ubuntu repositories, so every piece of software in ubuntu will be easily accessible with apt-get). 

Anyway, it does not have karmic yet, so I was lucking to some other distros:

Arch: ok, I can spend all the time it takes to configure it perfectly, but, will I be able to install locales and educational software?

Is there another distro worth looking at which meet my needs?


Laptop specifications: 40Gb hhd. 512Mb RAM. AMD at 1250MHz i think.

---

### Post by Bunnybugs on 2009-11-04
Puppylinux is very lighweight:P

but check out [www.linux.com](www.linux.com)

there are all distro's listed!

---

### Post by cascade9 on 2009-11-04
On those specs, for a young not-that-into-pcs-now person, I would use ubuntu minimal install. 

Its IMO one the the easiest OSes to learn, and fancy stuff like arch etc might be good for experienced PC users, or people who have used linux before, but its not as user friendly as ubuntu.

---

### Post by Penguin Guy on 2009-11-04
Masonux looks like a good OS, although I've never actually used LXDE. Defiantly not Arch - doesn't matter if you can configure it or not, it's designed for people who know what they're doing.

---

### Post by Paqman on 2009-11-04
> **cascade9 said:**
> I would use ubuntu minimal install. 


Me too. Why reinvent the wheel? Just use the system you're already familiar with. It's not hard to get Ubuntu down to about 100MB or less, and would run fine on a 512MB machine.

---

### Post by SomeGuyDude on 2009-11-04
> **Penguin Guy said:**
> Masonux looks like a good OS, although I've never actually used LXDE. Defiantly not Arch - doesn't matter if you can configure it or not, it's designed for people who know what they're doing.

This. I would argue that Arch is one of the lowest-maintenance distros out there, but part of that is because the user is expected to know their way around and set things up solidly. Updating/configuring is done via command line, and it's an unwritten rule that before major updates you read up on the main site and the forums to make sure everything's gravy.

I vote Ubuntu minimal if the OP is okay with doing the setup. Openbox as well. In my experience once things are all set, most people take to OB pretty smoothly.

---

### Post by mivo on 2009-11-04
Well, if you set up Arch in a (for you) perfect way, and everything works, there is no need to update it frequently. This is only true if you install all the educational software for her and she won't download anything from the repositories by herself, but that is a possible issue (and a way to break things) with most distros. The advantage of Arch is that you can perfectly (for your needs) set it up the way you want it and make it very lean and fast (I've really come to enjoy xfce4 lately).

If you want her to pull software from the repository, Ubuntu may be a safer choice, since she is less likely to accidentally update the entire system. :)  But if it is going to be a locked down system, I'd go with Arch and build something nice and beautiful by myself.

---

### Post by Xbehave on 2009-11-04
> **mivo said:**
> Well, if you set up Arch in a (for you) perfect way, and everything works, there is no need to update it frequently.Sure if you don't mind running a vulnerable browser or im client or ssh or kernel or w/e else gets updated because of a security vulnerability. 

I would agree with SomeGuyDude, I would also setup key based ssh login so you can fix problems remotely and either login regularly to update the system or set it to autoupdate (with backports disabled and security enabled)

---

### Post by Warpnow on 2009-11-04
> **SomeGuyDude said:**
> I vote Ubuntu minimal if the OP is okay with doing the setup. Openbox as well. In my experience once things are all set, most people take to OB pretty smoothly.

+1 if you know how. If you don't, then use Masonux or Sprii, which are both just someone doing that for you. Masonux is LXDE, whereas Sprii is Icewm. Both have their advantages. I believe IceWM is more lightweight as a package because LXDE adds a few apps to openbox, but the difference will be negligible. LXDE might be better for a windows refugee as it resembles slightly XP, whereas IceWM looks a bit more like 95/98 by default. I personally prefer ICEwms themes to LXDEs, though...IceWMs themes are more different from each other.

Puppy linux is also amazing. I would definitely give it a try, but puppy linux has annoying package management.

---

### Post by mivo on 2009-11-04
> **Xbehave said:**
> Sure if you don't mind running a vulnerable browser or im client or ssh or kernel or w/e else gets updated because of a security vulnerability. 

Jaunty still only had 3.0.x in the repository, didn't it? And 8.04, a LTS, shipped with FF 3.0 Beta 4.

He didn't mention a browser, though I don't think there would be a huge security risk if he installed Midori or even the latest version of FF and the browser doesn't get updated in the next six months. 

But as I said, if it's not a locked down system, I'd go with a minimal install of Ubuntu too, or, depending on the specs, with UNR.

---

### Post by rigao on 2009-11-04
> **Warpnow said:**
> +1 if you know how. If you don't, then use Masonux or Sprii, which are both just someone doing that for you. Masonux is LXDE, whereas Sprii is Icewm. Both have their advantages. I believe IceWM is more lightweight as a package because LXDE adds a few apps to openbox, but the difference will be negligible. LXDE might be better for a windows refugee as it resembles slightly XP, whereas IceWM looks a bit more like 95/98 by default. I personally prefer ICEwms themes to LXDEs, though...IceWMs themes are more different from each other.

Puppy linux is also amazing. I would definitely give it a try, but puppy linux has annoying package management.

I don't really know how to do a minimal ubuntu installation. I always download the alternate ubuntu CD and install through it. This is why I thought it would be better to use Masonux, which, as you say, is somebody making it for me.

Sprii could be too, I guess i will download both and give it a try in my virtual machine, to see what i like the best. I don't care much about the resemblances as she never used windows before (ok, maybe she knows the browser, but that's it), but I'm searching for the most noob friendly setup.

As someone tell, arch could be feasible if I install everything perfect, because it is not on my plan to let her install things... at least not right now, when she may break something... but, I doubt I will be able to configure it exactly with no flaws. 

Now I will have problems connecting with her machine, because most likely she will have dynamic IP. Is there a way to bypass this, or do I need her to tell me the IP every time? Because it's difficult to explan a 11 year old girl how to retrieve an IP...

---

### Post by Mehall on 2009-11-04
im more than a little surprised no one has mentioned the number 19 on distrowatch, crunchbang.
no karmic yet, but the jaunty release looks good and works great!
and since its ubuntu based, you have access to all those repo's.

---

### Post by HappinessNow on 2009-11-04
> **rigao said:**
> Hello everybody.

Some time ago I bought a new laptop and my niece, who is 11 years old, is going to inherit my old one.

This laptop is old, and I want her to have a pleasant linux experience (it will be her first OS, no windows pollution, so I think we can make her a big linux fan :D) so, although Xubuntu works, I want to try something different. Can you help me?

What do I require?

1.- It must be stable, because I won't be around to solve things. Maybe I can log in remotely, but it must work reasonable well.

2.- It must have locales, because she does not understand english.

3.- It must be able to put a bottom panel for no use, because the last lines of the screen don't work.

4.- It must have access to as much educational software as possible, as I want her to use this laptop as a teaching tool mainly.

Regarding all this points, I was thinking in Masonux, as some guy in this forum pointed it to me, and it seems to meet all the points (specially it will have access to ubuntu repositories, so every piece of software in ubuntu will be easily accessible with apt-get). 

Anyway, it does not have karmic yet, so I was lucking to some other distros:

Arch: ok, I can spend all the time it takes to configure it perfectly, but, will I be able to install locales and educational software?

Is there another distro worth looking at which meet my needs?


Laptop specifications: 40Gb hhd. 512Mb RAM. AMD at 1250MHz i think.MacPup Opera, MacPup Foxy or any other Puppy Linux variant.

---

### Post by mivo on 2009-11-04
There is also Puppy Linux, which is sort of cute and comes with a happy theme. :) I carry around a stick with Puppy on it (works really well, and even saves sessions on the stick), and I was/am quite impressed by it. It can also be installed on the HDD. It is very light, but offers a complete system with a ton of applications for all areas. (Has a repository, too.)

---

### Post by Mehall on 2009-11-04
the problem with puppy is, not everything has been packaged like what you get with ubuntu.

---

### Post by Tibuda on 2009-11-04
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by Warpnow on 2009-11-04
> **rigao said:**
> I don't really know how to do a minimal ubuntu installation. I always download the alternate ubuntu CD and install through it. This is why I thought it would be better to use Masonux, which, as you say, is somebody making it for me.


You can do a minimal install from the alternate CD if you want to try it out. At the selection screen hit f4 and hit "Install Command Line System". Then install whatever Desktop environment you want, and a login manager (slim, kdm, gdm, ect), and you're set.

> **rigao said:**
> 
Sprii could be too, I guess i will download both and give it a try in my virtual machine, to see what i like the best. I don't care much about the resemblances as she never used windows before (ok, maybe she knows the browser, but that's it), but I'm searching for the most noob friendly setup.


LXDE has a seldom used app called lxlauncher which is an eeepc like menu that runs instead of a background image. Makes finding applications alot easier. Might be worth trying.

> **rigao said:**
> 
As someone tell, arch could be feasible if I install everything perfect, because it is not on my plan to let her install things... at least not right now, when she may break something... but, I doubt I will be able to configure it exactly with no flaws. 


I'd stay away from arch because of the possibility of new packages breaking old ones. At least with ubuntu you only have to worry about that every six months.

> **rigao said:**
> 
Now I will have problems connecting with her machine, because most likely she will have dynamic IP. Is there a way to bypass this, or do I need her to tell me the IP every time? Because it's difficult to explan a 11 year old girl how to retrieve an IP...

You need to use something like dyndns to assign a domain name to her machine. Ever visited a website called *.dyndns.org, *.homelinux.org, or about a million other seemingly very common domains with subs that are usually usernames? They're using a program called dyndns to link their dynamic IP to a static domain name.

Check out dyndns.org

---

### Post by rigao on 2009-11-04
> **Warpnow said:**
> You can do a minimal install from the alternate CD if you want to try it out. At the selection screen hit f4 and hit "Install Command Line System". Then install whatever Desktop environment you want, and a login manager (slim, kdm, gdm, ect), and you're set.



LXDE has a seldom used app called lxlauncher which is an eeepc like menu that runs instead of a background image. Makes finding applications alot easier. Might be worth trying.


You need to use something like dyndns to assign a domain name to her machine. Ever visited a website called *.dyndns.org, *.homelinux.org, or about a million other seemingly very common domains with subs that are usually usernames? They're using a program called dyndns to link their dynamic IP to a static domain name.

Check out dyndns.org

You are very very helpfull. I will make sure to keep this post where i wont loose it.

I will give it a try to the lxlauncher, see how it does. And for sure will look deeply into dyndns.org, this could be the perfect solution.

About going into minimal ubuntu installation, it really sounds great (it remains me the way arch is made), but I think I will have to do it another time, too much distros I have to try now ;)

---

### Post by xuCGC002 on 2009-11-04
[CrunchBang]("http://crunchbanglinux.org/") is a must-look.

---

### Post by chucky chuckaluck on 2009-11-04
arch is not the setup nightmare it's often said to be and, as it's a rolling release distro, you install it once and that's it.

---

### Post by SomeGuyDude on 2009-11-04
Compared to Ubuntu? It's hellacious. Not to mention if something breaks (which does happen), you're expected to be able to identify and diagnose the problem pretty much on your own. When Xorg went kerflooey earlier this year the boards had the attitude of "well if you aren't able to dig through Xorg logs then maybe Arch isn't for you."

---

### Post by rectagonal on 2009-11-04
Ive had nothing but positive experiences with Zenwalk Linux. Its normally what I use when I need something lightweight.

---

### Post by Hallvor on 2009-11-04
Debian Lenny with LXDE should be good.

---

### Post by xpod on 2009-11-04
You could try doing a minimal *buntu installation and then installing the [lubuntu-desktop](http://gilir.wordpress.com/2009/10/29/lubuntu-9-10-and-plan-for-lucid/) package, which also uses LXDE.

I already have a minimal install of sorts on this particular laptop so i just installed the lubuntu-desktop package from there and logged back in to LXDE.I`m still using it now, over 24 hours later, and i`ve not even moved that bottom panel up top yet:p

---

### Post by Xbehave on 2009-11-04
> **Hallvor said:**
> Debian Lenny with LXDE should be good.
Lenny has a very old kernel, I ran into problems with wifi using it (not a problem as I can install a newer one, but that doesn't sound like the case here), and installing prop drivers is harder (not really a problem as there will not be a kernel update that breaks them for years, once you've installed them if you use lenny)

off-topic:
> **SomeGuyDude said:**
> ...to dig through Xorg logs...
erm is there a good guide to digging through xorg logs, I've always found them too verbose to be useful

---

### Post by snowpine on 2009-11-04
> **rigao said:**
> 1.- It must be stable, because I won't be around to solve things. 

X/K/Ubuntu 8.04 Hardy Heron, the current Long Term Support (stable) release. Or Debian Lenny.

With all due respect to the creators of CrunchBang/Sprii/Masonux (which are all very cool remixes), they are small, independent projects that haven't been around very long and have no guarantee of future support. If you install one of the top distros (again, my vote is Ubuntu LTS or Debian Stable), the odds are much better she'll receive many years of support and stability. Also there are more resources and tutorials available for the major distros.

The specs on that computer are enough to run a full-featured distro like Ubuntu; no need to keep things particularly "lightweight."

---

### Post by SomeGuyDude on 2009-11-04
Well, really, Crunchbang and its ilk aren't exactly separate distros. They're just remixes of Ubuntu that come packed with custom package sets. Once you're on it, really you should be piggybacking on whatever release of Ubuntu it's built on. We're not talking an overhaul like Mint.

---

### Post by Hallvor on 2009-11-04
> **Xbehave said:**
> Lenny has a very old kernel, I ran into problems with wifi using it (not a problem as I can install a newer one, but that doesn't sound like the case here), and installing prop drivers is harder (not really a problem as there will not be a kernel update that breaks them for years, once you've installed them if you use lenny)

off-topic:

erm is there a good guide to digging through xorg logs, I've always found them too verbose to be useful

It is an old computer. It probably doesn`t need a brand new kernel. As to proprietary drivers, that may or may not be necessary. Since it is an old computer there is a good chance that everything works out of the box. And once installed, there is little maintainance for the next couple of years.

But if you need a brand new kernel (because of brand new hardware) and proprietary drivers, an Ubuntu base install with LXDE is probably easier to set up.

Edit: With 512 MB RAM, Debian should also run XFCE, Gnome and KDE 3.5 quite well.

---

### Post by snowpine on 2009-11-04
> **SomeGuyDude said:**
> Well, really, Crunchbang and its ilk aren't exactly separate distros. They're just remixes of Ubuntu that come packed with custom package sets. Once you're on it, really you should be piggybacking on whatever release of Ubuntu it's built on. We're not talking an overhaul like Mint.

Yes and no. An Ubuntu 9.04 user who upgrades will have Ubuntu 9.10. A CrunchBang 9.04 user who upgrades to 9.10 will have a broken system (at the moment). In other words, the remixes are *based on* Ubuntu, but they are not *supported by* Canonical. There is no guarantee that the "custom package sets" will be viable over time, if Canonical's goals diverge from those of the remix. :)

CrunchBang is on it's 5th release (hooray!), but for every success story, there is a failed remix (like Fluxbuntu) that has one buggy release, then vanishes.

---

### Post by Xbehave on 2009-11-04
> **mivo said:**
> Jaunty still only had 3.0.**x** in the repository, didn't it? And 8.04, a LTS, shipped with FF 3.0 Beta 4.

He didn't mention a browser, though I don't think there would be a huge security risk if he installed Midori or even the latest version of FF and **the browser doesn't get updated in the next six months**. 
I don't know what the security record of Midori is but FF will be updated in the next 6 months. The reason you called it 3.0.**x** is because there are a lot of security updates for firefox, since FF3.0.0 was released on June 17, 2008 there have been 15 point releases, they represents 15 security patches/critical bugs that is almost one a month. Now if your the kind of person who runs arch updating once a month probably isn't an issue, but if you want to leave a computer setup that will update itself you want those updates to only be critical/security updates.

---

### Post by das928 on 2009-11-04
I would suggest Vector Linux Lite. It is stable and very fast. It comes with a choice of IceWM or JWM and it will really fly on a machine with those specs.

---

### Post by sertse on 2009-11-05
I'm suprised Arch has the educational software the OP is asking? Arch's community of packagers isn't exactly the type where educational software is their first priority.

---

### Post by Warpnow on 2009-11-05
> **sertse said:**
> I'm suprised Arch has the educational software the OP is asking? Arch's community of packagers isn't exactly the type where educational software is their first priority.

I think most of these replies are to the thread title not the thread.

---

### Post by earthpigg on 2009-11-05
would it come off as biased if i voted for Masonux, too, as it's creator? :D

> With all due respect to the creators of CrunchBang/Sprii/Masonux (which are all very cool remixes), they are small, independent projects that haven't been around very long and have no guarantee of future support.

the 9.04 release of all of the above will be supported for 18 months. 8.04 releases, where they exist, will be supported for 36 months. at which point, yes, a reinstall will be needed in all cases if you wish to continue with repo access.

continued long term support is indeed a big deal for commercial interests with non-nerd-people who will have to be retrained (which is expensive). 

if you are the nerd, a distro is a distro when it comes to support and it's ***all*** about hardware support, the repos, and what does/doesn't come preinstalled (and the implications of the preinstalled stuff). 

^
|
| in my opinion - and that is reflected in my remix... the last of those three is all that differs from vanilla ubuntu. 

moving on: 

whichever ubuntu remix you select ill recommend three apps to get you started... gcompris, tux paint, and tuxtype. im 26, but i still think they are a blast.

it will be worth your while to set up ssh with it. even if she doesn't break anything, it will allow you to install/introduce new stuff/software to her.

---

### Post by SomeGuyDude on 2009-11-05
> **Warpnow said:**
> I think most of these replies are to the thread title not the thread.

Or they're responses to three of the four criteria that the OP listed because how in the hell are we supposed to know what software the OP is referring to?

You can pretty easily search Arch's repos and the AUR if you want to know what's available, but to say "educational software" doesn't really help us in helping you.

---

### Post by earthpigg on 2009-11-05
> **SomeGuyDude said:**
> to say "educational software" doesn't really help us in helping you.

good point.

ill toss a suggestion out there....

take a gander at what comes with these metapackages for ideas:

[http://packages.ubuntu.com/jaunty/ubuntu-edu-preschool](http://packages.ubuntu.com/jaunty/ubuntu-edu-preschool)

[http://packages.ubuntu.com/jaunty/ubuntu-edu-primary](http://packages.ubuntu.com/jaunty/ubuntu-edu-primary)

[http://packages.ubuntu.com/jaunty/ubuntu-edu-secondary](http://packages.ubuntu.com/jaunty/ubuntu-edu-secondary)

[http://packages.ubuntu.com/jaunty/ubuntu-edu-tertiary](http://packages.ubuntu.com/jaunty/ubuntu-edu-tertiary)

:D

---

### Post by SomeGuyDude on 2009-11-05
I'm not really going to start slogging through the Arch repos package-by-package to see what is and isn't included. I picked a few at random (qcad, inkscape, parley) and they're in there.

---

### Post by SushiR on 2009-11-05
Crunchbang - very nice configured openbox and a good app selection with all the benefits of ubuntu repos.

---

### Post by earthpigg on 2009-11-05
> **SomeGuyDude said:**
> I'm not really going to start slogging through the Arch repos package-by-package to see what is and isn't included. I picked a few at random (qcad, inkscape, parley) and they're in there.

i have found that the AUR and conventional repos together include everything i could ever want.

depending on the AUR, of course, requires that you are willing to completely depend on the community. thus, anyone who's livelihood depends on their computer being stable... continue keep an Ubuntu thumb drive around.

(i am a fan of extremes for my personal life. draw two perpendicular lines with two arbitrary-but-related scales associated with each. i live on the four extreme corners, but have little use for anything else. including derivatives: debian stable - ubuntu - arch - FreeBSD. all the distros i need for anything i can conceive.)

---

### Post by mivo on 2009-11-05
> **Hallvor said:**
> Edit: With 512 MB RAM, Debian should also run XFCE, Gnome and KDE 3.5 quite well.

Xfce4 isn't much heavier than LXDE. A fresh install with the Xfce4 standard applications, and wcid (instead of network manager), htop and Midori runnning, uses about 69 MB RAM. It's much closer to LXDE than to Gnome or KDE. Xubuntu doesn't give an accurate idea of Xfce4's weight and footprint (too much Gnome stuff). I think many people who try Xfce4 install plenty of Gnome pieces too, like panels, NM, login manager, etc., all of which contribute to the bloat (wcid works so much better for me than NM).

---

### Post by sliketymo on 2009-11-05
gOS.

---

### Post by linux phreak on 2009-11-05
May i suggest [wattOS]("http://www.planetwatt.com/")

---

