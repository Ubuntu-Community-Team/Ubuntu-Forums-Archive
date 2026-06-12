---
title: "DesktopBSD, pretty sweet."
date: 2006-03-30
forum: The Cafe
---

### Post by dermotti on 2006-03-30
I installed DesktopBSD this weekend. Iits basically FreeBSD with a fancy installer, preinstalled KDE 3.5, and a graphical package manager.

So far im diggin it. The package manager is pretty sweet because you can choose to eithe rinstall the package from a binary or compile it yourself (just incase you need some special flags).


[http://www.desktopbsd.org](http://www.desktopbsd.org)

---

### Post by BarfBag on 2006-03-30
That's cool.  I've been tempted to try that out for a couple of months.  How fast and lightweight is it?  Does it have apt-get or an alternative to it?  I can't live without apt-get.  What form of packages does it use?

---

### Post by dermotti on 2006-03-30
Its uses a graphical front-end to freebsd ports. It works almost exactly like apt-get. It resoved all dependencies perfect. 

Its actually has some features that are better than apt-get. With apt-get you can only download precompiled binaries. With the DesktopBSD package manager you can choose either a precompiled binary, or compile the source.

That ability is pretty sweet,

---

### Post by magnusbb on 2006-03-30
[QUOTE=dermotti]Its actually has some features that are better than apt-get. With apt-get you can only download precompiled binaries. With the DesktopBSD package manager you can choose either a precompiled binary, or compile the source.[/QUOTE]

Well, as far as I know, this is also possible with apt. [http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html)

But does perhaps the ports system - of which I have heard many positive arguments - do this smoother, better and faster?

---

### Post by tageiru on 2006-03-30
[QUOTE=dermotti]Its uses a graphical front-end to freebsd ports. It works almost exactly like apt-get. It resoved all dependencies perfect. 

Its actually has some features that are better than apt-get. With apt-get you can only download precompiled binaries. With the DesktopBSD package manager you can choose either a precompiled binary, or compile the source.

That ability is pretty sweet,[/QUOTE]
Uh right, perhaps you should look into apt-get source and dpkg-buildpackage.

EDIT: Nevermind, magnusbb was faster.

---

### Post by dermotti on 2006-03-30
Through ports you just download it just like you would download a .deb binary package and it installs. Really smooth.

Honestly I have never attempted building from source via apt-get. But it looks to me like there is alot more steps involved (creating deb package etc etc).

---

### Post by Zodiac on 2006-03-30
What is the hardware support like?

I can imagine that being a nightmare...

---

### Post by nauseaboy on 2006-03-30
Dude, I'm gonna have to try that.

---

### Post by -Rick- on 2006-03-30
[QUOTE=Zodiac]What is the hardware support like?

I can imagine that being a nightmare...[/QUOTE]
Hardware support in fbsd isn't that bad. My WLAN works actually better in FreeBSD :)

---

### Post by dermotti on 2006-03-30
Everything on my system worked right out hte box.

And i was able to download the Nvidia driver right from the package manager. The driver worked automagically (besides putting "nvidia" in the xorg.conf).

---

### Post by doclivingston on 2006-03-30
[QUOTE=dermotti]Honestly I have never attempted building from source via apt-get. But it looks to me like there is alot more steps involved (creating deb package etc etc).[/QUOTE]

apt-get build-dep *packagename*
apt-get --build source *packagename*
dpkg -i *packagename*.deb


The first command installs the dependencies of the package. The second downloads the source package and build it. The third installs the newly built package - many things build multiple binary packages from one source package, so they may be multiple .debs to install.

There may be an even more automated way (such as a gui), but the above isn't exactly hard.

---

### Post by dermotti on 2006-03-30
Interesting. Ive never tried doing it via apt-get because I guess it was not really advetised to me ever that it was possible. Only Deb i have ever built was a kernel.

So then when you build Debs via apt-get, does it still resolve dependencies for you?

---

### Post by doclivingston on 2006-03-30
[QUOTE=dermotti]So then when you build Debs via apt-get, does it still resolve dependencies for you?[/QUOTE]

"apt-get build-dep" installs the *build dependencies* (what it required to build the package). I'm not actually sure what to do if there are (runtime) dependencies that aren't build dependencies. Run "apt-get -f install" after using dpkg to install it?

---

### Post by dermotti on 2006-03-30
When in stalled XFCE on DesktopBSD, i just clicked on XFCE and clicked install and walked away. Then the ports manager went out and installed/compiled all the dependencies automagically. And an hour later XFCE was ready. Pretty smooth....

---

### Post by macrohard on 2006-03-30
I'll have to give this one a shot, the only BSD I've tried so far is PCBSD. Itsnot bad for someone trying out BSD for the first time....:cool:

---

### Post by WildTangent on 2006-03-30
If I can install Gnome with this, I'm so trying it :D I've got FreeBSD on test system, but I dread installing it on a development machine because I can't quite remember how I did it...

-Wild

---

### Post by LinuxKid on 2006-03-31
[QUOTE=WildTangent]If I can install Gnome with this, I'm so trying it :D I've got FreeBSD on test system, but I dread installing it on a development machine because I can't quite remember how I did it...

-Wild[/QUOTE]
in your blog entry, maybe you could've gone into a little more detail (for me and for your own sake of knowing how you installed gnome)

---

### Post by LinuxKid on 2006-03-31
OSDir's got a screenshot tour of DesktopBSD
[http://osdir.com/Article8493.phtml](http://osdir.com/Article8493.phtml)

first shot:
[img]http://shots.osdir.com/slideshows/604/21.gif[/img]

looks > pretty sweet

---

### Post by tseliot on 2006-03-31
I can't install it on my ASUS a8v Deluxe as I get panic error a few after I insert the CD and the bootsplash is loaded (PC-BSD does the same). FreeBSD 6 doesn't have this problem.

Weird

---

### Post by helpme on 2006-03-31
[QUOTE=tseliot]I can't install it on my ASUS a8v Deluxe as I get panic error a few after I insert the CD and the bootsplash is loaded (PC-BSD does the same). FreeBSD 6 doesn't have this problem.

Weird[/QUOTE]
I think the current version of desktopbsd is based on freebsd 5.5.
Maybe this explains why freebsd 6 works, while desktopbsd doesn't.

---

### Post by Hamman on 2006-03-31
I prefer [PC-BSD](www.pcbsd.org). Their [package management system](http://www.pcbsd.org/?p=packages), PBI, is really interesting and IMO much better then apt, yum, ports and portage.

---

### Post by awakatanka on 2006-03-31
[QUOTE=Hamman]I prefer [PC-BSD](www.pcbsd.org). Their [package management system](http://www.pcbsd.org/?p=packages), PBI, is really interesting and IMO much better then apt, yum, ports and portage.[/QUOTE]
Cool another toy to play with, downloading it now.

---

### Post by Tatey on 2006-03-31
It's been a while since I've tinkered with FreeBSD. I'm definitely going to download an ISO and try it out on my laptop. It's in need of clean-up anyhow. Thanks for the information.

Cheers

---

### Post by Al3xanR0 on 2006-03-31
[QUOTE=dermotti]I installed DesktopBSD this weekend. Iits basically FreeBSD with a fancy installer, preinstalled KDE 3.5, and a graphical package manager.

So far im diggin it. The package manager is pretty sweet because you can choose to eithe rinstall the package from a binary or compile it yourself (just incase you need some special flags).


[http://www.desktopbsd.org](http://www.desktopbsd.org)[/QUOTE]

I just downloaded it can't wait to take it for a spin. Whoa! I meant the cd not the rooooooooooooom! :-#

---

### Post by hizaguchi on 2006-05-04
I installed it yesterday.  It is mind-numbingly fast on my laptop (well, compared to what I'm used to).  Noticably faster than Arch and definately Ubuntu.  But I'm not sold on the ports/packages system.  Alot of things don't have precompiled packages and the GUI installer doesn't seem to be compiling a port when it fails to find a package, which has pretty much made it useless to me since upgrading never gets completely finished.  This has led me to the command line, where I'm getting the hang of "portupgrade" and it's options, but I'm running into another problem: some packages installed from the CD are newer than the ones in the freeBSD CVS, which has a nasty habit of confusing the package management even further.

I'm determined to get it all straight though.  I may just install plain FreeBSD and see if that fixes some of my issues.

---

### Post by Super King on 2006-05-04
Looks nice. Do they have anything similar to a Linux 'live CD'?

---

