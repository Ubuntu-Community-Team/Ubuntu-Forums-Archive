---
title: "Linux from scratch."
date: 2005-09-03
forum: The Cafe
---

### Post by kagashe on 2005-09-03
Hi,

Today I googled "How to build your own Linux distribution?" and reached
[Linux from scratch (LFS)](http://www.linuxfromscratch.org/).

I found that the site is not only for developers but even for newbies.

I would like to know whether anyone has tried LFS or its other variants to build
a Linux distribution or just for learning how Linux operating system actually works.

kagashe

---

### Post by KingBahamut on 2005-09-03
Ive run the LFS build before. 

Honestly if thats what you want to do I found building Gentoo alot easier and with less complication. 

Ive done builds of most of , if not all of the source dists, OneBase, Gentoo, SourceMage, Sorcerer, and LFS. 

Of those, Onebase and Gentoo are the easiest to build.

---

### Post by kagashe on 2005-09-03
> Honestly if thats what you want to do I found building Gentoo alot easier and with less complication. My purpose is to learn the process and I find all the guidance available (in documents) on LFS site. Do I get such step by step guidance for Gentoo?
I also found this most recent review on tuxmachines:
[http://www.tuxmachines.org/node/2482](http://www.tuxmachines.org/node/2482)
and I am encouraged to devote time and try.

kagashe

---

### Post by KingBahamut on 2005-09-03
Gentoo build is a lot easier, if thats what your asking, yes.

---

### Post by kagashe on 2005-09-03
[QUOTE=KingBahamut]Gentoo build is a lot easier, if thats what your asking, yes.[/QUOTE]
 Hi,

I am not asking what is easy or difficult. What I mean is since LFS is necessarily to be built from scratch all the documentation exists on its site. When I look at documentation on Gentoo site it is only about installing the pre built packages like Ubuntu isn't it?

I am not a developer so how can I build Gentoo from source?

kagashe

---

### Post by DJ_Max on 2005-09-03
[QUOTE=kagashe]Hi,

I am not asking what is easy or difficult. What I mean is since LFS is necessarily to be built from scratch all the documentation exists on its site. When I look at documentation on Gentoo site it is only about installing the pre built packages like Ubuntu isn't it?

I am not a developer so how can I build Gentoo from source?

kagashe[/QUOTE]
 Gentoo is a source distribution. So when you install it, you are building everything from source.

---

### Post by skoal on 2005-09-03
[QUOTE=kagashe]I found that the site is not only for developers but even for newbies.[...][/QUOTE]
Yes, sir! Kagashe, LFS is an exceptional tool I highly recommend for _anyone_ new to Linux.  Why do I call it a tool?  Well, it gives you just that - everything you need to build a linux distro.  The documentation is exceptional and the mailing lists are very constructive.  *If you take the time to read all the information while your source is compiling off in a chroot env, at the end of the day, you will become quite adept at Linux System Administration*.  

Compare and Contrast (the _intent_ of LFS vs. Gentoo):

1. It's one thing to compile from source, it's yet another to actually read what's in GNU coreutils (for example).  Gentoo doesn't provide you that. You're left to research that on your own.  Basename, dd, dirname, du, mknod, nice, tac, tee, and many more - how many Gentoo users are familiar with those immediately after the install?  Furthermore, how many even know where those were installed (without using 'which', or the like)?

2. LFS holds your hand along the way, Gentoo just gets you up and running.

3. LFS explains to you what you are installing, and more importantly, _why_.  Gentoo, N/A.   At the end of the day, how many Gentoo users can claim they understand the linux toolchain? It provides you valuable insight as you peer into the beating heart of linux, which is _not_ the kernel.  Everything single app, including the kernel itself, relies upon that toolchain.

4. LFS documentation reads much more like a instruction pamplet (or a book).  Gentoo is more like a skeleton technical manual.

5. LFS = total control over your system.  Gentoo = partial.

6. LFS = bastardized package manager using tar+scripts (if needed).  Gentoo = powerful emerge.  That's really the only "advantage" Gentoo has over LFS, but even still, you can accomplish the same by installing your own package manager in LFS. 

7. < and many more >

It's been ~5 years since I last used LFS religiously.  Unfortunately, a _lot_ of content has been stripped (as of late) from prior LFS documentation, but the underlying premise is still intact - your distro, your rules.

I would recommend LFS over Gentoo any day, for anyone...

\\//_

---

### Post by phen on 2005-09-03
welcome in the geek-versum!

(i think i stay over here, turn off my pc and go for beer,music and girls now :-)

---

### Post by N'Jal on 2005-09-03
> beer,music and girls now 

*reminises Ah good days*
*real world hits* shit man I'm 18 single and actually know what's being talked about. What's more worrying when I'm my dad's age my age generation will be asking what VHS are. ARGH!!!

---

### Post by matthew on 2005-09-03
[QUOTE=N'Jal]*reminises Ah good days*
*real world hits* shit man I'm 18 single and actually know what's being talked about. What's more worrying when I'm my dad's age my age generation will be asking what VHS are. ARGH!!![/QUOTE]
Dude, I still own music on vinyl and I remember when television was something that was broadcast over the "airwaves" and you felt pretty good if you lived in a city that had more then 4 channels: ABC, CBS, NBC and PBS. Oh, yeah, I used to watch in black & white because we didn't get a color tv until I was about 10.

---

### Post by darkmatter on 2005-09-03
LFS was one of the best learning experiences I've had.

---

### Post by kagashe on 2005-09-03
Hi,

Thanks KingBahamut for making this thread a debate. I have just started learning what is a "source" distribution, what is "rpm" distribution and what is "deb" distribution. What is Mandriva's package manager, what is Synaptic package manager and now "emerge".

Thanks DJ_Max now I know why Gentoo is for developers and advance users (not for newbies)

Thanks skoal for nice explaination.

Thanks phen, N'Jal and matthew for making it a Community Chat.

Now I am prepared to take on LFS and/or Gentoo.

But I have a limit of 1 GB per month on my ISP account and extra per MB rate is very high.
I just checked that I can't manage LFS download of about 150 MB till this month's account ends on Sep 19th. I have to wait for another 16 days.

This month I tried to upgrade to Breezy and used around 500 MB and I failed to upgrade. But that is another story. I have decided to wait now till Breezy CD is released.

Thanks darkmatter for adding your views.

What a nice, lively community we have here.  :grin: 

kagashe

---

### Post by kagashe on 2005-10-06
Hi,

I have installed LFS. I have also installed BLFS upto Xorg-6.8.2.
I am now stuck up at XFCE installation. I can login to XFCE desktop but when I move the mouse on XFCE panel the Xserver shuts down. There is LFS forum on LinuxQuestions.org where I am getting support.

It is very good learning experience.

kagashe

---

### Post by skoal on 2005-10-06
kagashe, check out the LFS mailing lists.  They're invaluable.  Also, I believe most of those problems are addressed in their "hints" section.

\\//_

---

