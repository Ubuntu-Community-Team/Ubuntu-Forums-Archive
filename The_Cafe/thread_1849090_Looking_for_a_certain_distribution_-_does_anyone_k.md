---
title: "Looking for a certain distribution - does anyone know what I should look for?"
date: 2011-09-23
forum: The Cafe
---

### Post by ClientAlive on 2011-09-23
Hi,

I'm hoping to identify a Linux distribution that fits a certain criteria. I was hoping someone here might have an idea what would work for me.

I have a desktop with bare drives in it (well, formatted in ext4, but nothing on there) and I want to build a system from scratch but actually using that machine to do it. I was hoping there's a distro out there that can run live from usb or cd and has all the tools in it I would need for configuring and compiling a kernel and compiling the other programs I'll need right-onto-that-machines-drive. Using that machine (not some other, second machine).

I thought, if I can find the right distro for it, I could run live, not worry about chroot, and just compile right-to the formatted drive/ partition. I don't want to install a system on it in order to compile a system on it because then I'd have that mess to deal with in the end. And I would strongly prefer to use that machine and compile right to it rather than create the things on another machine and copy them over.

I know about Linux from Scratch and I'm reading the book. It's just that It's a 300 odd page book and I'm not certain they mean the same thing I do when they use the phrase "from scratch." I was hoping I wouldn't have to read 300 pages just to find out I was wrong about the meaning.

I'd sure appreciate some guidance on this one.

Thanks.

---

### Post by jmate24 on 2011-09-23
all versions of Ubuntu that have a Live (Desktop) CD version can be created for a boot disk and you can run programs on it and save your data to it if you have a large enough USB/Thumb drive. i have put Ubuntu 10.10 on mine before and have been able to run it for presentations and the like from school computers. it saves me time.

First i need your PC's specs and how many and what size are your hard drives. Because we possibly can give you either a Raid or an LVM setup so that you can maximize your storage space.

---

### Post by ClientAlive on 2011-09-24
> **jmate24 said:**
> all versions of Ubuntu that have a Live (Desktop) CD version can be created for a boot disk and you can run programs on it and save your data to it if you have a large enough USB/Thumb drive. i have put Ubuntu 10.10 on mine before and have been able to run it for presentations and the like from school computers. it saves me time.

First i need your PC's specs and how many and what size are your hard drives. Because we possibly can give you either a Raid or an LVM setup so that you can maximize your storage space.

Oh, I have plans to use MDADM for a RAID 5 array but I need to build the system first. That's what I was after is a way I can do that without having to do it on a separate system. I found out that LFS (Linux from Scratch) has a live cd that's supposed to have everything you need on it to compile the kernel and other programs right onto the system. (There is no installation of anything on that other system - the desktop - that I want to build the system on). Hopefully the LFS live cd will do the trick for me.

I didn't realize it before about 20 min ago but I guess most distros have what it takes to compile - right out of the box.

I didn't really think about how maybe I didn't explain very well.

The computer I'm typing this on is a different computer than the one I want to build a system on. The one I want to build the system on is my desktop and it's drives are "bare".

---

### Post by dcstar on 2011-09-24
> **ClientAlive said:**
> Oh, I have plans to use MDADM for a RAID 5 array but I need to build the system first. That's what I was after is a way I can do that without having to do it on a separate system. I found out that LFS (Linux from Scratch) has a live cd that's supposed to have everything you need on it to compile the kernel and other programs right onto the system. (There is no installation of anything on that other system - the desktop - that I want to build the system on). Hopefully the LFS live cd will do the trick for me.

I didn't realize it before about 20 min ago but I guess most distros have what it takes to compile - right out of the box.

I didn't really think about how maybe I didn't explain very well.

The computer I'm typing this on is a different computer than the one I want to build a system on. The one I want to build the system on is my desktop and it's drives are "bare".

There is no point whatsoever in "compiling" because ALL distros provide pre-compiled software for you.

---

### Post by patryk77 on 2011-09-24
I do believe LFS would be the one to give you the most control, though when I last used it, it was a ridiculously painful process to get it working (but that was at least 5 years ago and on a slow PC).

An alternative would be Gentoo, which I believe would help automate a big part of the process while still giving you a lot of options to configure packages before they are compiled/installed. 

[http://en.wikipedia.org/wiki/Gentoo_Linux](http://en.wikipedia.org/wiki/Gentoo_Linux)

Finally, this should probably go under Other Community Discussions - Other OS/Distro talk as it's not Ubuntu related ;)

---

### Post by patryk77 on 2011-09-24
> **dcstar said:**
> There is no point whatsoever in "compiling" because ALL distros provide pre-compiled software for you.

That is simply misguided, and not really helping to answer OP's question.

[QUOTE=Wikipedia]There are normally no precompiled binaries for software, continuing the tradition of the ports collection,[2] although for convenience, some software packages (such as Mozilla Firefox and LibreOffice) are also available as precompiled binaries for various architectures where compiling would otherwise be very time consuming.[/QUOTE]

---

### Post by Elfy on 2011-09-24
Thread moved to The Community Cafe.

---

### Post by coffeecat on 2011-09-24
@ClientAlive, I agree with patryk77's suggestion to have a look at Gentoo. The live CD contains enough of an environment to compile your Gentoo system after you have unpacked the stage 3 tarball. After some configuration you do need to chroot into your minimal Gentoo system from the CD to configure enough (particularly a kernel) so that you can boot into it. More links here:

[http://www.gentoo.org/](http://www.gentoo.org/)

[http://www.gentoo.org/doc/en/handbook/](http://www.gentoo.org/doc/en/handbook/)

Their forums are quite friendly and active - last time I used them that is.

---

### Post by el_koraco on 2011-09-24
Gentoo, Funtoo, that's what you're looking for. Although I don't think Funtoo has its own Live CD yet, they recommend other Live CDs for building the system. If you wanna do a full install from scratch, chrooting is gonna be the least of your problems.

---

### Post by CharlesA on 2011-09-24
Another +1 to Gentoo from me.

---

### Post by 3Miro on 2011-09-24
LFS is way too much work for one person. You can build a system for the experience, but maintaining it would be too much work.

Gentoo is the next closest thing.

Gentoo has its own LiveDVD, however, you can install Gentoo from any liveCD/USB, just read their documentation.

---

### Post by ClientAlive on 2011-09-25
> **patryk77 said:**
> I do believe LFS would be the one to give you the most control, though when I last used it, it was a ridiculously painful process to get it working (but that was at least 5 years ago and on a slow PC).

An alternative would be Gentoo, which I believe would help automate a big part of the process while still giving you a lot of options to configure packages before they are compiled/installed. 

[http://en.wikipedia.org/wiki/Gentoo_Linux](http://en.wikipedia.org/wiki/Gentoo_Linux)

Finally, this should probably go under Other Community Discussions - Other OS/Distro talk as it's not Ubuntu related ;)


Want to hear something funny? It is Gentoo that I'm after. Well, let me take that back . . .  It is Xen that I'm after but I want to use Gentoo as my dom0 for Xen. Thing is, I want to actually build the thing up from scratch. LFS is cool but they aren't after the same end result that I am (so I'm having to kind of piece information together from few different sources).

So yeah, I want to build my system from scratch, the system I want to end up with is not the same as the one LFS has you end up with, and I want to use the bare computer the system will go on to do the compiling. That's where I'm at. I learned enough about compiling so far to really be dangerous (that's ok though because it's my computer for experimenting - starting with nothing got nothing to lose). So I know enough to be dangerous but now I'm trying to figure out how to set up my environment to do it the way I'm wanting to.

Best thing I could figure is run some distro live and use it to do my compiling (if it ran from memory that would just be icing on top of the cake). Just not sure what the best one to use would be. Some things that I think are important?

~ Very minimal yet with all the neccessities for this type of thing
~ Uses bash and not some other shell I'm not familiar with
~ Runs from RAM would just be awesome (but not a deal breaker if it didn't)


I've run that LFS (the mini version of it) just to check it out and it seems odd for some reason. Gives me the impression it's somehow . . .  not normal, or would be a challenge to use.

---

### Post by ClientAlive on 2011-09-25
> **patryk77 said:**
> I do believe LFS would be the one to give you the most control, though when I last used it, it was a ridiculously painful process to get it working (but that was at least 5 years ago and on a slow PC).

An alternative would be Gentoo, which I believe would help automate a big part of the process while still giving you a lot of options to configure packages before they are compiled/installed. 

[http://en.wikipedia.org/wiki/Gentoo_Linux](http://en.wikipedia.org/wiki/Gentoo_Linux)

Finally, this should probably go under Other Community Discussions - Other OS/Distro talk as it's not Ubuntu related ;)


> **coffeecat said:**
> @ClientAlive, I agree with patryk77's suggestion to have a look at Gentoo. The live CD contains enough of an environment to compile your Gentoo system after you have unpacked the stage 3 tarball. After some configuration you do need to chroot into your minimal Gentoo system from the CD to configure enough (particularly a kernel) so that you can boot into it. More links here:

[http://www.gentoo.org/](http://www.gentoo.org/)

[http://www.gentoo.org/doc/en/handbook/](http://www.gentoo.org/doc/en/handbook/)

Their forums are quite friendly and active - last time I used them that is.


I'm sorry, I didn't get what was being suggested (about using the Gentoo cd). I guess I knew they have a live cd but I didn't grasp what it was or did. Actually, I had assumed it was just another 'push the button and install it for you' deal - that's what it was. If that live cd lets you do some building of your own I'll have to take a good look at that.

Thanks for pointing that out for me.

:D

> **el_koraco said:**
> Gentoo, Funtoo, that's what you're looking for. Although I don't think Funtoo has its own Live CD yet, they recommend other Live CDs for building the system. If you wanna do a full install from scratch, chrooting is gonna be the least of your problems.


Hi el_koraco. Thanks for the heads up.

):P

---

