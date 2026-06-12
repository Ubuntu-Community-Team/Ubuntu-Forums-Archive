---
title: "Ubuntu Light?"
date: 2009-08-22
forum: The Cafe
---

### Post by Lacrimo on 2009-08-22
As much as I love Ubuntu from the times I have run it - upwards of 6 months - I'm sticking to Arch Linux. Why? Arch isn't at all bloated. In fact, many people would consider it too devoid of features. An out-of-the-box install comes with little more than the kernel, basic daemons and services, and the package manager. All command line.

That minimalistic approach is great for me, I have the time, inclination and experience to do that without issue. There are, however, relatively few people that really want to get down and dirty using purely the command line to do work. There are, however, plenty of people in the world that don't need bluetooth support, Scanner support, a screen magnifyer and reader, a VoIP client, Rhythmbox, the entirety of open-office (I'd just put abiword in there), 300 card games they'll never play, big, bulky firefox or Seahorse (the encyption key program).

With Arch Linux running gnome, this firefox session and hellanzb going at full speed, I'm using ~300MB of RAM. Ubuntu out of the box running firefox and hellanzb used up ~550MB of RAM. That's certainly not bad - my tests with Windows 7 show it using ~800MB at rest - but it could be better if you cut a lot of the mostly unused features out of Ubuntu. There could at least be an 'Advanced' section when installing to deselect things you might not need. I know I don't need ekiga, CUPS, bluetooth, orca, rhythmbox, seahorse, a themed GDM, and the gnome-games package.

If Ubuntu wants to claim they will work on older hardware, they really should realease a light edition or allow modification of some of the superflous software it comes with.

---

### Post by .Maleficus. on 2009-08-22
Good luck modifying superflous software with Ubuntu.  A lot of the software is so tightly knit that uninstalling it would result in uninstalling all of Gnome.  For a lighter Ubuntu, you could try Xubuntu (though it's still pretty fat) or one of the newer spinoffs like Icebuntu or Lubuntu.  That doesn't really help if you want Gnome though.

Anyways, you basically just described why I switched to Arch too.

---

### Post by Lacrimo on 2009-08-22
I'm aware that even trying to get rid of Xsane == removing ubuntu-desktop as far as aptitude is concerned. I am hoping that the devs can fix that.

---

### Post by Labello on 2009-08-22
Hi,

I completely understand your concerns about all these apps/themes/settings you might not want. But did you know that you have got the possibility to install Ubuntu as a CLI-system as well and then add only the parts you need? I created a tutorial about this method and how to achieve a complete desktop starting with this CLI-setup. I also use this setup. It consumes 230mb RAM with Compiz enabled. So it is also pretty lightweight. It is lightweight but does not need that much amount of configuration as Arch does:

[http://ubuntuforums.org/showthread.php?t=1209904](http://ubuntuforums.org/showthread.php?t=1209904)

---

### Post by Lacrimo on 2009-08-22
Never noticed that option on the CD. Thanks for the info.Now if only Ubuntu had the meta-packages pacman does. Instead of pointing to a package, it points to a set of packages.

Now that's useful for me - as I don't mind a pure CLI environment to set up my system, but I was trying to appeal more to the masses. An option to get gnome/kde up and running out of the box, but without any additional software but synaptic, firefox/epiphany, and perhaps Totem/vlc. Doing so would help open ub Ubuntu to people still running P4s and maybe P3s.

The main problem with the fluxbuntu, lubuntu, whatever projects is that they aren't really a project of canonical, so support and the ability to be up to date is hokey at best.

If nothing else, Ubuntu should cut out everything but the basics from their netbook remix.

---

### Post by Nevon on 2009-08-22
> **Lacrimo said:**
> With Arch Linux running gnome, this firefox session and hellanzb going at full speed, I'm using ~300MB of RAM. Ubuntu out of the box running firefox and hellanzb used up ~550MB of RAM.
Lol. I'm running Ubuntu 9.04 right now, with Firefox, Pidgin, Compiz, Giver, Thunderbird, Caffeine, Guake and a bunch of other apps running, and I'm still only at 350mb ram used.

As for a light Ubuntu, you do have the barebones installation and build your own Ubuntu system. Apt does have some metapackages, but I don't know if they are the same as pacman's.

---

### Post by XubuRoxMySox on 2009-08-22
I have a super-lightweight Ubuntu/LXDE mixture with none of the stuff I don't want. I did a minimal Ubuntu (CLI) installation (minimal CD [here]("https://help.ubuntu.com/community/Installation/MinimalCD")), then added LXDE, Synaptic, Abiword, Gnumeric, Audacious, Firefox, and Thunderbird. Threw in a few codecs, done.

Much simpler than what I have heard about Arch, though perhaps not as lean and mean. But it flies along effortlessly on this old Dell Dimension desktop.

-Robin

---

### Post by Stan_1936 on 2009-08-22
> **Lacrimo said:**
> ....**That minimalistic approach is great for me**, I have the time, inclination and experience to do that without issue. There are, however, relatively few people that really want to get down and dirty using purely the command line to do work. There are, however, plenty of people in the world that don't need bluetooth support, Scanner support, a screen magnifyer and reader, a VoIP client, Rhythmbox, the entirety of open-office (I'd just put abiword in there), 300 card games they'll never play, big, bulky firefox or Seahorse (the encyption key program).....

Then you should do Ubuntu minimal + whatever you want.

I did a minimal install+ a light Gnome setup(the basics, installed some fancy theme engines/icons/sound drivers + HP printer drivers) and it sat at ~155MB RAM(idle).  Installation was a breeze.:guitar:

Now let's see Arch do that!

---

### Post by Stan_1936 on 2009-08-22
BTW, I'm siock of hearing all this hype about Arch.  IF you want more people to use it, then make it easier to install/setup.  If not, then quite frankly(in my opinion atleast), Arch will never come close to Ubuntu.

And there WILL be a large number of people that WON'T have a problem with that!

---

### Post by Regenweald on 2009-08-22
I usually do a minimal cd install, the minimal cd is about 11 megs for 64bit.  then install the Gnome-core desktop. Even then, I still remove packages that i don not need from Gnome-core. My system idles at around 240 megs, kind of heavy but i have 2 gigs of memory.

Any linux system can be made to be light. Replace gnome-core with LXDE or Enlightenment... boom.

---

### Post by demosthene1 on 2009-08-22
For a very interesting, very fun, super lightweight Ubuntu based distro try Crunchbang, or as it is commonly referred to, #!.

[#!]("http://crunchbanglinux.org/")

I love it. Very fast, very configurable, very stylish.

---

### Post by calrogman on 2009-08-22
> **Lacrimo said:**
> Now if only Ubuntu had the meta-packages pacman does. Instead of pointing to a package, it points to a set of packages.

You mean like, linux-image-generic, which always depends on the latest kernel or {k,x,ed}ubuntu-desktop.

PROTIP:  Ubuntu has meta-packages.

---

### Post by sefs on 2009-08-22
I have always thought that too many packages in Ubuntu were tied too closely to gnome/ubuntu-desktop.  packages like Firefox.  Frankly it reminds me of MS tactics of tying IE to its systems.  And it is angering.

Why when uninstalling a simple package do I need to install the whole system?  This has got to be bug #2 in Ubuntu.

---

### Post by Keyper7 on 2009-08-22
> **sefs said:**
> I have always thought that too many packages in Ubuntu were tied too closely to gnome/ubuntu-desktop.  packages like Firefox.  Frankly it reminds me of MS tactics of tying IE to its systems.  And it is angering.

Why when uninstalling a simple package do I need to install the whole system?  This has got to be bug #2 in Ubuntu.

The whole system? What are you talking about? ubuntu-desktop is simply a meta-package defining a set of default packages. If you don't like it, uninstall it and proceed to uninstall whatever else you want. It has a lot of dependencies but it's not a dependency of anything.

---

### Post by sefs on 2009-08-22
<post deleted see the one below> Ignore this.

---

### Post by sefs on 2009-08-22
> The whole system? What are you talking about? ubuntu-desktop is simply a meta-package defining a set of default packages. If you don't like it, uninstall it and proceed to uninstall whatever else you want. It has a lot of dependencies but it's not a dependency of anything.

Hmmm...maybe I just do not understand how it works. I like having ubuntu-desktop, otherwise I feel naked. Like leaving the house without trousers. Many times I needed to uninstall some seemingly simple package and I had to do the dance of removing ubuntu-desktop uninstalling the package then putting back on ubuntu-desktop to do more dancing of it pulling back in the package i have installed. This is not necessary is it?

> 
The whole system? 


Yes the whole system, because it feels as if that is what is happening whether it is happening or not. In any event it pisses me off every single time.

---

### Post by demosthene1 on 2009-08-22
I'm sorry, I don't understand this:

 Re: Ubuntu Light?
#! Ignore this. 

I meant to be helpful. For someone not as technically inclined as some, like me, [Crunchbang]("http://crunchbanglinux.org/") is a very good, light distro that does not hide the fact it is based on Ubuntu - unlike linux Mint. Lacrimo may find it helpful and fun. I use Ubuntu 9.04 as my main os on my laptop and desktop. On my eee pc 2g surf first gen netbook I run Crunchbang on an sd card, no problem.

Thanks!

---

### Post by bodhi.zazen on 2009-08-22
Arch and Ubuntu have different goals and you are comparing apples to oranges.

Ubuntu is trying to make it as easy as possible for new users migrating from Windows. As such it is going to be more bloated starting with the kernel (we want Ubuntu to run on as much hardware as possible) to bloatware. Bluetooth for example.

Arch is not targeting the same community and installing Arch would be nothing short of a nightmare for the average user migrating from windows.

In addition, you are comparing a Desktop install (Ubuntu) to a minimal install (Arch).

Start with the Ubuntu Minimal CD, it is much more comparable to Arch. Size is somethign like 10 mb and it is a net install of a minimal system. From there learn to build up. If you can install gnome / kde / *box on Arch, you can do the same in Ubuntu.

From there it depends on how you want to spend your time. Do you want to customize and build your own kernel ? Gentoo is probably best for tweaking your hardware.

Arch is a nice little distro, and pacman is an amazing tool.

At the end of the day, Linux offers choice, use the best tool for the task.

---

### Post by Warpnow on 2009-08-22
If you install a command line and type sudo apt-get install gnome/kde/xfce, then the next time you reboot you'll have gdm and upon logging in **just** the Desktop environment.

Ubuntu can do exactly the OP describes...

---

### Post by bodhi.zazen on 2009-08-22
> **Warpnow said:**
> If you install a command line and type sudo apt-get install gnome/kde/xfce, then the next time you reboot you'll have gdm and upon logging in **just** the Desktop environment.

Ubuntu can do exactly the OP describes...

Well not "exactly". There are some packages with a larger then needed dependency list and you may not know how to resolve them.

An example is php. The php5 package in Ubuntu is indeed quite complex and if you are not running apache, and you install php5, it will pull apache as a dependency. This is very annoying if you are trying to run lighttpd or nginx + php5.

the solution is to instead install php5-cgi.

Again I am giving one example, there are some packages that act similar, ie gnome rather then ubuntu-desktop, xfce rather then xubuntu-desktop.

It does take some time to learn your way around the repositories and what to install without pulling lots of dependencies.

In that case it is sometimes better to build from source rather then try to juggle the Ubuntu dependencies.

Getting back to php5, it is sometimes easier to compile php5 rather then keep wrestling with pulling the apache dependencies.

---

### Post by running_rabbit07 on 2009-08-22
> **Stan_1936 said:**
> BTW, I'm siock of hearing all this hype about Arch.  IF you want more people to use it, then make it easier to install/setup.  If not, then quite frankly(in my opinion atleast), Arch will never come close to Ubuntu.

And there WILL be a large number of people that WON'T have a problem with that!

I second that emotion. To me that is the same as a Windows user saying they want Ubuntu to work their way. If you want a lighter Ubuntu, start uninstalling stuff you don't like. Or, put 2 Arches together and have a happy meal.

> **bodhi.zazen said:**
> An example is php. The php5 package in Ubuntu is indeed quite complex and if you are not running apache, and you install php5, it will pull apache as a dependency. This is very annoying if you are trying to run lighttpd or nginx + php5..

I have noticed that Evolution does that too. I was going through Synaptic deleting Evolution and one of the deletions I was going to do had GNOME desktop as a dependency it was going to delete.

---

### Post by bodhi.zazen on 2009-08-22
> **running_rabbit07 said:**
> put 2 Arches together and have a happy meal.

:lolflag:

---

### Post by Crunchy the Headcrab on 2009-08-22
> **Nevon said:**
> Lol. I'm running Ubuntu 9.04 right now, with Firefox, Pidgin, Compiz, Giver, Thunderbird, Caffeine, Guake and a bunch of other apps running, and I'm still only at 350mb ram used.

As for a light Ubuntu, you do have the barebones installation and build your own Ubuntu system. Apt does have some metapackages, but I don't know if they are the same as pacman's.
I was wondering about this too.  I don't use anywhere near the amount of ram he's suggesting.  As for the lighter ubuntu, I totally agree that there should be some options in the installer to choose which packages you actually want.  That's part of the reason I'm using Fedora now.  I like that feature.  I used the Ubuntu net install and that wasn't too bad but it would be nice if there was a way to do a minimal install from a normal cd.

---

### Post by juancarlospaco on 2009-08-22
Arch is too Bloated, i prefer Ubuntu Minimal 9Mb ISO :)

---

### Post by running_rabbit07 on 2009-08-22
> **Nevon said:**
> Lol. I'm running Ubuntu 9.04 right now, with Firefox, Pidgin, Compiz, Giver, Thunderbird, Caffeine, Guake and a bunch of other apps running, and I'm still only at 350mb ram used..

Run all that on Vista and fill up about 1.5 Gigs of RAM

---

### Post by xArv3nx on 2009-08-22
> **juancarlospaco said:**
> Arch is too Bloated, i prefer Ubuntu Minimal 9Mb ISO :)

wat

---

### Post by Warpnow on 2009-08-22
> **xArv3nx said:**
> wat

There's a 10mb netinstall iso file.

---

### Post by sefs on 2009-08-22
> **demosthene1 said:**
> I'm sorry, I don't understand this:

 Re: Ubuntu Light?
#! Ignore this. 

I meant to be helpful. For someone not as technically inclined as some, like me, [Crunchbang]("http://crunchbanglinux.org/") is a very good, light distro that does not hide the fact it is based on Ubuntu - unlike linux Mint. Lacrimo may find it helpful and fun. I use Ubuntu 9.04 as my main os on my laptop and desktop. On my eee pc 2g surf first gen netbook I run Crunchbang on an sd card, no problem.

Thanks!

Hey, when I put that there it was not in reference to anything you said, I was just replacing/deleting a post that didnt get post well, I saw the symbol earlier and thought it looked cooled so I used it back as a place holder for deleted text (not smart).  I guess I should have just used something else :P

The ignore this was meant to mean ignore my botched post.

---

### Post by kk0sse54 on 2009-08-22
> **Stan_1936 said:**
> BTW, I'm siock of hearing all this hype about Arch.  IF you want more people to use it, then make it easier to install/setup.  If not, then quite frankly(in my opinion atleast), Arch will never come close to Ubuntu.

And there WILL be a large number of people that WON'T have a problem with that!

Who said anything about Arch wanting to come close to Ubuntu?

---

### Post by Warpnow on 2009-08-22
People like Arch because of its complex setup...

That's what it is. Its a distro you setup yourself rather than get preconfigured...

---

### Post by Keyper7 on 2009-08-22
> **sefs said:**
> Hmmm...maybe I just do not understand how it works.

Allow me to explain, then. :)

ubuntu-desktop is a *metapackage*, an empty package whose sole reason for existence is defining a list of dependencies. More precisely, it defines "the set of applications that come with Ubuntu by default". Having it installed basically means you have those applications.

Firefox is one of the applications that come with Ubuntu by default. If you uninstall Firefox, you *have* to uninstall ubuntu-desktop. Why? Because not having ubuntu-desktop means "I don't have all applications that come with Ubuntu by default", *which is exactly the case since you uninstalled Firefox*.

Now, the most important part: the removal of ubuntu-desktop *does not break anything*. By removing it you are simply stating you don't want to follow Ubuntu's choices for default applications, which is perfectly fine.

So, in conclusion: just uninstall ubuntu-desktop and be happy.

> **sefs said:**
> it feels as if that is what is happening whether it is happening or not

Oh, I can see it already:

Bug #2: I'm crazy and Ubuntu developers need to take this into consideration.

(just kidding ;))

---

### Post by TheNessus on 2009-08-22
> **Keyper7 said:**
> Allow me to explain, then. :)

Now, the most important part: the removal of ubuntu-desktop *does not break anything*. By removing it you are simply stating you don't want to follow Ubuntu's choices for default applications, which is perfectly fine.

So, in conclusion: just uninstall ubuntu-desktop and be happy.



Can that be seconded?

---

### Post by bodhi.zazen on 2009-08-22
> **Warpnow said:**
> People like Arch because of its complex setup...

That's what it is. Its a distro you setup yourself rather than get preconfigured...

Naw, if that was all there was to Arch it would not be popular.

If you have a solid foundation in Linux or you want to learn a bit under the gui, arch is perfect.

Sysadmin on Arch is fairly stri\aight forward and so it is easy to "take control" and configure it the way you want.

Second pacman is a great tool.

I do agree, if they wanted to to be more popular they would need to work on the installer.

But I do not think that is the goal of Arch.

---

### Post by Regenweald on 2009-08-22
The goal of the Arch developers is to make great OS and they achieve that. The goal of Arch fanboys, much like the Ubuntu ones is to be greatly annoying :)

---

### Post by TheNessus on 2009-08-22
> **Regenweald said:**
> The goal of the Arch developers is to make great OS and they achieve that. 

Nope they don't. Their goal is to *allow* people to make it a great OS.

If I'd tried configuring Arch myself, I won't get it work at all :)

---

### Post by entr3p on 2009-08-22
Wow. Comparing Arch to Ubuntu is pointless. Why? Because they were both created for two completely different reasons.

Ubuntu = Easy to use, newbie friendly Linux distro.
Arch = Do it yourself, only what you need distro.

It's like comparing a pen and an apple.

"Why does this pen taste like **** while I can't write using this damn apple!?!"

---

### Post by Grifulkin on 2009-08-22
My only problem that I have with Arch at the moment is when I try to start it in VBox it gets caught on loading udev and then finally finishes keeps going for a few seconds and then it aborts.  So I can't really check it out.

---

### Post by stwschool on 2009-08-22
Well I'm fairly early in the learning arch phase. I suspect that I could get similar speed and efficiency out of an Ubuntu minimal install, and the hardware support on Ubuntu is second to none, so in a way Arch is probably more hassle. For me, however, it's much like how some people like to build kit cars. It's then mine. It's also a great way to learn how stuff works under the hood. Now of course some people don't need that, but I love taking stuff apart and seeing what's inside, and this is no different.

Ubuntu is my primary OS, but for me, Arch is a fantastic learning tool.

---

### Post by stwschool on 2009-08-22
> **Grifulkin said:**
> My only problem that I have with Arch at the moment is when I try to start it in VBox it gets caught on loading udev and then finally finishes keeps going for a few seconds and then it aborts.  So I can't really check it out.
Weird, I don't get that problem (Ubuntu Host, Arch guest). It was networking that foxed me, but I've finally got that working and have sussed pacman so soon as I'm back at the office with a nice fast internet connection I can mess with that before eventually hitting a real install.

---

### Post by Grifulkin on 2009-08-22
> **stwschool said:**
> Weird, I don't get that problem (Ubuntu Host, Arch guest). It was networking that foxed me, but I've finally got that working and have sussed pacman so soon as I'm back at the office with a nice fast internet connection I can mess with that before eventually hitting a real install.

Yeah, I have no idea what the problem is, and I don't know enough to begin to find out.

---

### Post by stwschool on 2009-08-22
> **Grifulkin said:**
> Yeah, I have no idea what the problem is, and I don't know enough to begin to find out.
It's usually Fedora that craps out on me in that fashion, but I just don't get it. VBox is supposed to emulate a standard setup right? So it shouldn't really crap out like that. Stupid question I know but when you set up the vbox did you select Arch as the OS to go on it?

---

### Post by Grifulkin on 2009-08-22
> **stwschool said:**
> It's usually Fedora that craps out on me in that fashion, but I just don't get it. VBox is supposed to emulate a standard setup right? So it shouldn't really crap out like that. Stupid question I know but when you set up the vbox did you select Arch as the OS to go on it?

Well I gave it it's own virtual hard drive and set up its core image as the mounted drive.  But it still craps out, no clue.  I tried enabling different things like ACPI and I/O ACPI and enable PAE but still craps out and I can't see the last line before it aborts.

---

### Post by stwschool on 2009-08-22
> **Grifulkin said:**
> Well I gave it it's own virtual hard drive and set up its core image as the mounted drive.  But it still craps out, no clue.  I tried enabling different things like ACPI and I/O ACPI and enable PAE but still craps out and I can't see the last line before it aborts.
I'm stumped then :(

---

### Post by sefs on 2009-08-23
> **Keyper7 said:**
> Allow me to explain, then. :)

ubuntu-desktop is a *metapackage*, an empty package whose sole reason for existence is defining a list of dependencies. More precisely, it defines "the set of applications that come with Ubuntu by default". Having it installed basically means you have those applications.

Firefox is one of the applications that come with Ubuntu by default. If you uninstall Firefox, you *have* to uninstall ubuntu-desktop. Why? Because not having ubuntu-desktop means "I don't have all applications that come with Ubuntu by default", *which is exactly the case since you uninstalled Firefox*.

Now, the most important part: the removal of ubuntu-desktop *does not break anything*. By removing it you are simply stating you don't want to follow Ubuntu's choices for default applications, which is perfectly fine.

So, in conclusion: just uninstall ubuntu-desktop and be happy.



Oh, I can see it already:

Bug #2: I'm crazy and Ubuntu developers need to take this into consideration.

(just kidding ;))

That is the clearest I have heard it explained.  Thank you.  Although I still like having it installed.  It makes me feel warm at night.

---

