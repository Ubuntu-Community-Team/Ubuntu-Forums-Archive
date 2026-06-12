---
title: "Linux From Scratch"
date: 2009-10-07
forum: The Cafe
---

### Post by Warpnow on 2009-10-07
So, I've been thinking about doing this. I have two machines at the moment. My nice, new, shiny core 2 duo e6750, and the machine it replaced- a pentium 2 300mhz machine. My thoughts are to use the older machine because, well, I don't want to mess up my primary machine. I've been using linux for 3-4 years, but still find myself boggled by things usually relating to the filesystem's structure, and I figure building a linux from scratch system will make me much more proficient in understanding linux.

What I wonder is...how large are the packages you have to compile for this? Will my old pentium 2 machine spend more time compiling packages than being worked on? I know some packages take quite a while.

How useful will my LFS system be? If I do it on my main machine, am I likely to eventually get to a point where the end product is comparable in stability and quality with Ubuntu or another distribution?

How long will it take me to get to that point?

Have any of you done it, what were your experiences?

---

### Post by scragar on 2009-10-07
I wouldn't recommend jumping right into LFS, start with something like arch, which gives you a command line, but a very good package manager, when you are sure you understand that try gentoo, which puts more in your hands and actually compiles the files itself, and if that works out for you finally move onto LFS and do everything yourself.
Compiling will take some time, but it really depends on what you want, gnome and KDE are large projects, so the source will take a long time to compile on slow machines, fluxbox or wmii however will not take nearly as long.

---

### Post by Bachstelze on 2009-10-07
You don't want to do a LFS on a 300 MHz CPU, it'll take forever. If I were you, I'd rather do it on the Core2 in a VM.

> **scragar said:**
> 
Compiling will take some time, but it really depends on what you want, gnome and KDE are large projects, so the source will take a long time to compile on slow machines, fluxbox or wmii however will not take nearly as long.

Even with wmii, you have to compile Xorg, which will take a while (not to mention GCC itself and all the compiling toolchain).

---

### Post by rsambuca on 2009-10-07
Yeah, I have to agree here.  I think LFS on that older rig would be a lesson in frustration and futility more than anything else, unless you are *extremely* patient.  You might try either Ubuntu minimal installation, where you add everything you want from a base install, or perhaps Arch if you want to start even more minimalistic.

---

### Post by Warpnow on 2009-10-07
I've done ubuntu minimal and arch installs. I might try Gentoo, though. I tried slackware in my first month or so in linux (never take advice over IRC, ever) and failed terribly. Might try that again first as well.

---

### Post by SomeGuyDude on 2009-10-07
If you were a fan of Arch but want a more involved distro, try CRUX.

---

### Post by rsambuca on 2009-10-07
I think I would definitely recommend Arch over Gentoo in your particular situation.  Both will give you similar results, but with Gentoo you will be waiting forever to compile all the programs, whereas with Arch you can install the binary packages.

---

### Post by Lukios on 2009-10-07
I second the VMWare suggestion on your new computer.

---

### Post by ynnhoj on 2009-10-08
> **Warpnow said:**
> I've been using linux for 3-4 years, but still find myself boggled by things usually relating to the filesystem's structure, and I figure building a linux from scratch system will make me much more proficient in understanding linux.
couldn't you also learn these things by reading some books? or, as others have mentioned, you could try using a different distro that requires you to get your hands dirtier. crux or gentoo might be good choices.

i imagine that linux from scratch could become a real headache; getting all the right tools compiled in order to use xorg would take long enough, and then what if you run into confusing dependency problems and you don't have a package manager to help you sort everything out? but if you're really a hands-on sort of person who's dead set on linux from scratch, then you might want to take Bachstelze's advice and do it in a vm on your newer computer. good luck, you're braver than i am! :]

---

### Post by Eisenwinter on 2009-10-08
> **SomeGuyDude said:**
> If you were a fan of Arch but want a more involved distro, try CRUX.
I second this.

I've heard great things about CRUX. If it's 64 bit build was available officially, not just as someone else's hack, I'd definitely check this distro out.

---

### Post by octesian on 2009-10-13
LFS is a great learning experience.  I loved doing it, but at the time I was on a dial-up connection so I didn't have the bandwidth to download X.  Also with limited bandwidth it was a pain in the buns to get all the source.  Other than that, compiling took a while (I was using an old Compaq laptop) but the experience was worth it.  It took me about 3 days (including a few "****it I'm startin over"s) to get to a working bash prompt.  I went straight from Ubuntu to LFS and I'll recommend it to anyone who has some spare time and wants to learn a lot.

Oh also lots of reading.

---

### Post by Exodist on 2009-10-13
> **Bachstelze said:**
> You don't want to do a LFS on a 300 MHz CPU, it'll take forever. If I were you, I'd rather do it on the Core2 in a VM.



Even with wmii, you have to compile Xorg, which will take a while (not to mention GCC itself and all the compiling toolchain).

I agree. I have played around with LFS. I even printed manuals out the wazzu.

In the end I realized that a non-gui install of debian or ubuntu with your own compiled kernel is just the same as building your own Linux OS. Plus a lot easier and faster.

---

### Post by earthpigg on 2009-10-13
if all else fails,

NetBSD's motto: *of course it will run NetBSD*.

[http://www.netbsd.org/ports/i386/hardware.html](http://www.netbsd.org/ports/i386/hardware.html)
> 
The minimal configuration for a NetBSD/i386 system requires 4M of RAM and about 40M of disk space. For a full installation (including source and X11), at least 8M of RAM and 200M of disk space are recommended. 

Any i386 or better CPU should work - genuine Intel or a compatible such as Cyrix, AMD, or NexGen. 

[http://www.netbsd.org/docs/guide/en/index.html](http://www.netbsd.org/docs/guide/en/index.html)

---

