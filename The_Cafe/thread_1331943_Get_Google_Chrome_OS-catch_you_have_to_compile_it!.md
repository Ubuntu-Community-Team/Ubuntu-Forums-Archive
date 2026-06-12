---
title: "Get Google Chrome OS-catch you have to compile it!"
date: 2009-11-19
forum: The Cafe
---

### Post by dvl300 on 2009-11-19
Yes you have to compile it from source code
[**Source**](http://sites.google.com/a/chromium.org/dev/chromium-os/building-chromium-os)
Getting and Building a Chromium-Based OS

Contents

1. 1 Prerequisites
2. 2 Get the source
3. 3 Build Chromium OS
4. 4 Make changes
5. 5 More information

Welcome to Chromium OS!

Our goal here is to give you an idea of how to get started.

Note: For all instructions, make sure you download the client into a local directory. Placing the source and compiling on a network partition will drive you nuts.

Note: These build instructions will evolve over time as the build system is improved. Make sure to periodically check back for the latest information.

Prerequisites
You need to have Linux. We currently support the following:

* Ubuntu (Hardy 8.04 or newer, Karmic 9.10 recommended)
* An account with root access (needed to run chroot and modify the mount table)
* Chromium prerequisites (needed to build a Chromium-based browser as part of building Chromium OS)

---

### Post by RATM_Owns on 2009-11-19
How is compiling a catch?

---

### Post by dragos240 on 2009-11-19
> **RATM_Owns said:**
> How is compiling a catch?

+1

I use gentoo and arch. So I compile many things. (arch meaning archlinux, and programs from the AUR).

---

### Post by Tipped OuT on 2009-11-19
> **RATM_Owns said:**
> How is compiling a catch?

> **dragos240 said:**
> +1

I use gentoo and arch. So I compile many things. (arch meaning archlinux, and programs from the AUR).

Because they're some average people (like me) who don't know how to compile things from source, nor want to waste time learning how.

---

### Post by dvl300 on 2009-11-19
> **RATM_Owns said:**
> How is compiling a catch?
Its just some people can't be bothered to, although i will be doing as soon as i have a full free day :D

---

### Post by dragos240 on 2009-11-19
> **Tipped OuT said:**
> Because they're some average people (like me) who don't know how to compile things from source, nor want to waste time learning how.

cd DIRECTORY
make
make install.

---

### Post by Tipped OuT on 2009-11-19
> **dragos240 said:**
> cd DIRECTORY
make
make install.

I don't even know what you want me to do with that information. "cd DIRECTORY", "make", "make install" ?????

I don't have even have Linux installed at the moment, so it doesn't even matter. Thanks though.

---

### Post by Wiebelhaus on 2009-11-19
I'm disappointed to hear someone say that learning something new is a waste of time.

---

### Post by Tipped OuT on 2009-11-19
> **Wiebelhaus said:**
> I'm disappointed to hear someone say that learning something new is a waste of time.

Waste of time when I could just double click an icon and install. I got things to do.

---

### Post by dvl300 on 2009-11-19
> **Wiebelhaus said:**
> I'm disappointed to hear someone say that learning something new is a waste of time.
well everyone is different, i mean Ive only been using Linux for six years, but i chose to learn Linux and i like it as its free! :D

---

### Post by themusicalduck on 2009-11-19
I don't think I've ever successfully compiled a program without some random cryptic error coming up after using 'make' :D

Although I'm still gonna give compiling chrome a go, not that I  expect it to work or anything..

---

### Post by dvl300 on 2009-11-19
i know what you mean lol :D

---

### Post by kreggz on 2009-11-19
the idea is to weed out people who aren't contributing. They just want developers looking at Chromium OS at this stage (i think)

---

### Post by Islington on 2009-11-19
learning how to build things is a waste of time? what next, reporting bugs is a waste of time?

---

### Post by Ric_NYC on 2009-11-19
> **tipped out said:**
> waste of time when i could just double click an icon and install. I got things to do.

+1

---

### Post by joey-elijah on 2009-11-19
If compiling and building this developers preview of ChromiumOS is too much then just wait until it launches...

...you will have to pay for the privilege of getting it mind as ChromeOS will ONLY be available on approved netbooks. No downloadable images for plucky people to install willy-nilly... you'll have to hope someone forks ChromiumOS for that...

---

### Post by RiceMonster on 2009-11-19
> **dragos240 said:**
> cd DIRECTORY
make
make install.

Yeah, it's ALWAYS that simple.

> **RATM_Owns said:**
> How is compiling a catch?

Do you really have to ask that question?

---

### Post by kevCast on 2009-11-19
> **Tipped OuT said:**
> Because they're some average people (like me) who don't know how to compile things from source, nor want to waste time learning how.
what is this i don't even

---

### Post by kpholmes on 2009-11-19
> **Wiebelhaus said:**
> I'm disappointed to hear someone say that learning something new is a waste of time.

i agree, i could see how some people dont have the time or maybe dont want to but to call it a waste is kinda over the edge.

---

### Post by Regenweald on 2009-11-19
For the same experience you could:
```

sudo add-apt-repository ppa:chromium-daily

```
then
```

sudo aptitude install chromium-browser

```

Since it's just a secure browser atop Ubuntu anyway. As an immediate and radical upgrade, you'll be able to save files to your hard disk ! WTF!

---

### Post by Tipped OuT on 2009-11-19
> **kevCast said:**
> what is this i don't even
???
> **kpholmes said:**
> i agree, i could see how some people dont have the time or maybe dont want to but to call it a waste is kinda over the edge.

We all have our opinions, but compiling something (as well learning to compile) is just a waste of time for me. 

Like I said before, I have things to do. You may have all the time in the world, but I don't.

If there's a more common easier alternative, like double clicking a file. Then I rather do that.

PS: I never said learning is a waste of time, I said learning to compile is a waste of time for me.

---

### Post by kpholmes on 2009-11-19
> **Tipped OuT said:**
> ???


We all have our opinions, but compiling something (as well learning to compile) is just a waste of time for me. 

Like I said before, I have things to do. You may have all the time in the world, but I don't.

If there's a more common easier alternative, like double clicking a file. Then I rather do that.

PS: I never said learning is a waste of time, I said learning to compile is a waste of time for me.

thats cool man. i dont think that everyone who runs linux should have to use the command line. the larger variety of users we have the better :D i dont expect some of my friends who ive turned to linux to use the CLI. 

+1 cause your from anaheim, im accross the street (costa mesa) haha. 
you should check out the california ubuntu users club

---

### Post by Tipped OuT on 2009-11-19
> **kpholmes said:**
> +1 cause your from anaheim, im accross the street (costa mesa) haha. 
you should check out the california ubuntu users club

Heyy, thanks. I'll check it out. :)

---

