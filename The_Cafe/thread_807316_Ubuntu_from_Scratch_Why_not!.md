---
title: "Ubuntu from Scratch?? Why not!"
date: 2008-05-25
forum: The Cafe
---

### Post by shane2peru on 2008-05-25
Ok, first you are probably thinking, are you crazy?  Well, perhaps I am.  I'm not a computer programmer, I just really like computing.  Ever since I have started using Linux about 4 or 5 years ago, I have really enjoyed the 'freeness' of it.  The cost and the ability to tinker, tweak, and change the system to what you want.  I have successfully installed Gentoo 2 or 3 times, and have dabbled in Slackware as well.  I say all of that to say this.  I enjoy building the system, and have a more slim line running machine.  It is the upkeep of that system that in the end kills me. ;)  That is what always keeps me coming back to Ubuntu.  I love Ubuntu for it's simplicity, and a ton of other reasons (I'm too content with Debian style to switch).  Sooo, what I would love to do is, build an Ubuntu system, that would be compatible with the LTS repos to keep my system up to date.  Essentially I would be going through all the steps the dev's do, just that the system would be setup to exclusively run on my system, not all the other systems that have about 1000 things that I will never use.  Is this possible?  or I'm I just dreaming?  If you know of a good set of instructions to do such I thing I would love to read through them.  I love the documentation of Gentoo, it is very straightforward!  Thanks!

Shane

PS  of course I would dual boot, to get the system built with the ultimate goal of swapping over to that system completely.

---

### Post by kef_kf on 2008-05-25
you can try the minimal cd: [https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")

it may not be what you had in mind, but i think its pretty close.

---

### Post by cb951303 on 2008-05-25
yep, get the minimal cd, start adding packages an configure it to your liking, then compress the harddisk image so that you can use it later

---

### Post by fatality_uk on 2008-05-25
[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

---

### Post by shane2peru on 2008-05-25
> **kef_kf said:**
> you can try the minimal cd: [https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")

it may not be what you had in mind, but i think its pretty close.

Hmmmmm, that is close, but not quite enough.  I guess building the kernel around your system is the core of what I'm talking about.   However it is closer.  I guess, if all else fails, I could go with that, and rebuild my kernel, however, there is so much enabled in the kernel that it is hard to try and figure out what I don't need. :)  I would be better off with a bare-bones kernel and start adding things as I need it. 

> **fatality_uk said:**
> [http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

This looks like a very interesting site.  I will certainly have to check this out!!!  I briefly looked at it, and I think it is a little closer to what I'm looking for.  Just wish it was more 'Ubuntu' directed.  :)  Will definitely check it out though!

Shane

---

### Post by klange on 2008-05-25
Meh, getting all the way to Compiz should be enough for me this summer. An entire compatible Ubuntu install? Probably not going to happen. Plus, I despise the number of apps they install to /usr.

---

### Post by shane2peru on 2008-05-26
> **cb951303 said:**
> yep, get the minimal cd, start adding packages an configure it to your liking, then compress the harddisk image so that you can use it later

OK, I take back what I said earlier, this seems to be the closest thing I will get for Ubuntu/Debian style system.  :)  If I get this and then rebuild the kernel to get rid of all the extra, and then build each item that is installed, I should have a system that is as close as what I'm looking for that still keeps me tied to Ubuntu.  Thanks.  I will have to give this option a spin.

Shane

---

### Post by BobLand on 2008-05-26
One advantage of Linux from Scratch is you literally build it from scratch.  What you will learn by doing this is understanding what goes into a system and how to customize it down to the bare metal.

You can build it from their iso or go out and find the various modules scattered on the net.  You will learn a lot of compiling tricks and face many a frustrated moment when things don't go as planned.

Support is excellent.  

In the end, you can make your own distro of linux or make a ubuntu/debian distro -- your choice!

Try it, you'll like it!
bobland

---

### Post by shane2peru on 2008-05-26
> **BobLand said:**
> One advantage of Linux from Scratch is you literally build it from scratch.  What you will learn by doing this is understanding what goes into a system and how to customize it down to the bare metal.

You can build it from their iso or go out and find the various modules scattered on the net.  You will learn a lot of compiling tricks and face many a frustrated moment when things don't go as planned.

Support is excellent.  

In the end, you can make your own distro of linux or make a ubuntu/debian distro -- your choice!

Try it, you'll like it!
bobland

I will probably check it out, thanks!

Shane

---

### Post by mips on 2008-05-26
Imho Arch might be a better option.
If you like compiling then Gentoo but it seems to hard to keep going.

---

### Post by FuturePilot on 2008-05-26
There's something called [apt-build]("http://freshmeat.net/projects/apt-build/")

---

### Post by ssam on 2008-05-26
for customising the kernel see
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

for building packages, and adding you own patches have a look at
[https://wiki.ubuntu.com/MOTU/School](https://wiki.ubuntu.com/MOTU/School)

---

### Post by shane2peru on 2008-05-26
> **mips said:**
> Imho Arch might be a better option.
If you like compiling then Gentoo but it seems to hard to keep going.

Someone brought that to my attention too, it is a thought, but not deb based. :(  

> **ssam said:**
> for customising the kernel see
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

for building packages, and adding you own patches have a look at
[https://wiki.ubuntu.com/MOTU/School](https://wiki.ubuntu.com/MOTU/School)

I have been on that page, and the directions are somewhat unclear, there is sooooo much stuffed enabled for the kernel, I don't know what to dis-able.  :)  It looks as though this kernel was built for over 1000 different hardware setups.  I'm going to really look at LinuxFromScratch, that seems to be the best setup, at least they have a very interesting book to read through. :)

Shane

---

### Post by Dr Small on 2008-05-26
Just because Arch is not deb based should be no reason to try it. I found Arch's PKGBUILD files much simpler and more efficient.

Arch is the way to go if you like to build your system from scratch.

---

### Post by d.kusummmanth@gmail.com on 2008-05-26
> **fatality_uk said:**
> [http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

crap site. it sucks.

---

### Post by d.kusummmanth@gmail.com on 2008-05-26
> **shane2peru said:**
> Ok, first you are probably thinking, are you crazy?  Well, perhaps I am.  I'm not a computer programmer, I just really like computing.  Ever since I have started using Linux about 4 or 5 years ago, I have really enjoyed the 'freeness' of it.  The cost and the ability to tinker, tweak, and change the system to what you want.  I have successfully installed Gentoo 2 or 3 times, and have dabbled in Slackware as well.  I say all of that to say this.  I enjoy building the system, and have a more slim line running machine.  It is the upkeep of that system that in the end kills me. ;)  That is what always keeps me coming back to Ubuntu.  I love Ubuntu for it's simplicity, and a ton of other reasons (I'm too content with Debian style to switch).  Sooo, what I would love to do is, build an Ubuntu system, that would be compatible with the LTS repos to keep my system up to date.  Essentially I would be going through all the steps the dev's do, just that the system would be setup to exclusively run on my system, not all the other systems that have about 1000 things that I will never use.  Is this possible?  or I'm I just dreaming?  If you know of a good set of instructions to do such I thing I would love to read through them.  I love the documentation of Gentoo, it is very straightforward!  Thanks!

Shane

PS  of course I would dual boot, to get the system built with the ultimate goal of swapping over to that system completely.
[SIZE="3"]
Excellentttttttttttttttt POSt:)[/SIZE] [FONT="Lucida Sans Unicode"][COLOR="Blue"]I can't thank u enough for posting such an excellent thread.[/COLOR][/FONT] I never knew that u could do the stuff which u spoke about.

---

### Post by shane2peru on 2008-05-26
> **Dr Small said:**
> Just because Arch is not deb based should be no reason to try it. I found Arch's PKGBUILD files much simpler and more efficient.

Arch is the way to go if you like to build your system from scratch.

It isn't that I don't want to try Arch, it doesn't fit into my original post.  I don't mind building from scratch, but I want to end up with a system that is then maintained.  It would be like building Ubuntu from scratch and then letting them do the upkeep.  IT is the maintaining the distro that kills me.  Building it around my system (the base of the distro) that I really like, that gives me a good base to run off, and then the packages can be added.  Essentially (if I understand everything correctly) it would give me a more dynamic, slick or trimmed down Ubuntu, that can use the Ubuntu packages/repos.  That is I guess the gist of what I'm looking for.  Not that I wouldn't try Arch, it just doesn't fit into that scheme of things.

Shane

---

### Post by shane2peru on 2008-05-26
> **d.kusummmanth@gmail.com said:**
> [SIZE="3"]
Excellentttttttttttttttt POSt:)[/SIZE] [FONT="Lucida Sans Unicode"][COLOR="Blue"]I can't thank u enough for posting such an excellent thread.[/COLOR][/FONT] I never knew that u could do the stuff which u spoke about.

This is one of the Great things about Linux!!!  It is FLEXIBLE :)  Explore the possibilities and learn!  I have tried Gentoo (great documentation), Slackware (fun, but never got all the updates done), Arch is another (I have yet to try this one) great one for learning what is under the hood.  There is another Called, Debian from Scratch (this is where I got my idea) however I didn't find good documentation on that, and didn't understand it.  Google it and you will find a page or two for ideas.

Shane

PS, the LFS site isn't much, but their book seems to be very detailed.

---

### Post by smartboyathome on 2008-05-26
> **d.kusummmanth@gmail.com said:**
> crap site. it sucks.

I find it very good if you want to learn the inner workings of Linux, or if you want to create your own from-scratch lightweight livecd (Puppy or one of the small distros started out from this).

> **shane2peru said:**
> It isn't that I don't want to try Arch, it doesn't fit into my original post.  I don't mind building from scratch, but I want to end up with a system that is then maintained.  It would be like building Ubuntu from scratch and then letting them do the upkeep.  IT is the maintaining the distro that kills me.  Building it around my system (the base of the distro) that I really like, that gives me a good base to run off, and then the packages can be added.  Essentially (if I understand everything correctly) it would give me a more dynamic, slick or trimmed down Ubuntu, that can use the Ubuntu packages/repos.  That is I guess the gist of what I'm looking for.  Not that I wouldn't try Arch, it just doesn't fit into that scheme of things.

Shane

Arch does do this. They use pacman, which is similar to apt, but builds from source, thus optimizing further. Everything is automated (except if you go with yaourt, which you have to get your hands dirty sometimes).

---

### Post by myusername on 2008-05-26
there is a thing i found called debian from scratch (dfs) and no im not getting this mixed up with lfs. the only thing is that their documentation sucks :(

---

### Post by smartboyathome on 2008-05-26
Actually, you could probably use LFS, and then install apt and everything else (making packages for them along the way) from source. What good this would do, I would not really know, since it is already possible to apt-get source -b everything (which fetches the source code and builds it).

---

### Post by shane2peru on 2008-05-26
> **smartboyathome said:**
> Actually, you could probably use LFS, and then install apt and everything else (making packages for them along the way) from source. What good this would do, I would not really know, since it is already possible to apt-get source -b everything (which fetches the source code and builds it).

The good that it would do, is make my original install more streamlined for my system by building the kernel around my hardware (or even potential hardware)  and eliminating all the extra stuff, like ATI, Nvidia, and a whole bunch of hardware I don't own.  :)  Thus eliminating a lot of bulk right at the start, then I could do as you say, and build everything on my system. :)  Time consuming, but in the end I have a software built for my system. 

Shane

---

### Post by smartboyathome on 2008-05-26
You can already do this. Install Ubuntu minimal, recompile the kernel, and use the source command above. Same thing.

---

### Post by shane2peru on 2008-05-26
> **smartboyathome said:**
> You can already do this. Install Ubuntu minimal, recompile the kernel, and use the source command above. Same thing.

Yes that is what I have looked at too.  Have you ever recompiled an Ubuntu kernel?  It comes with about everything under the sun enabled or modularized in.  So going through that and disabling things is, well, hmm, let's just say it may be easier to start with a new kernel.  I couldn't figure out what to eliminate! lol, there was so much stuff in there it was unbelievable.  When I setup my kernel for Gentoo, it was easy, go enable this this and that for your hardware, and you are all set. :)  The reverse of that is a little tougher.

Shane

---

### Post by smartboyathome on 2008-05-27
If it is easier to start with a new one, download a new one from the linux site and compile that one. :)

---

