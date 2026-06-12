---
title: "ubuntu Studio - What's your take?"
date: 2007-05-28
forum: The Cafe
---

### Post by lakersforce on 2007-05-28
What do you think of this package?

I think it is pretty good. But there is WAY to many overlaping programs in the Audio suite, that part is poorly managed! That section should be divided into more packages.

I would like to see more diverse packages. For example a "web design" package with Audacity, Gimp, Inkscape and Bluefish.

---

### Post by MetalMusicAddict on 2007-05-28
> **lakersforce said:**
> What do you think of this package?
It's the bee's knee's. ;)
> I think it is pretty good. But there is WAY to many overlaping programs in the Audio suite, that part is poorly managed! That section should be divided into more packages.
The packages don't really overlap much. They were also picked by many who have worked with linux audio for years. The menu couldn't be restructured for v1. It should be in v2 but is more work than most will realize. ;)
> I would like to see more diverse packages. For example a "web design" package with Audacity, Gimp, Inkscape and Bluefish.
This won't happen as most of the tools are there in the -graphics package already and the ones that aren't are a simple apt-get away.

---

### Post by starcraft.man on 2007-05-28
I liked it a lot when I tried it, in VM. Only thing I got annoyed with it from was the default theme, I didn't like the shade of blue/black used and how the icons looked. Call me picky (and yes, I know I could have fixed it... >.>).

Apart from that it was nice when I tried it, I was thinking of installing to my computer some time soon when I have a moment.

Edit: To mateo: The reason for its existance is to show studio workers that there are many free quality apps for production tools. Not to mention it includes the low latency kernel, and you don't have to install it seperate, there are meta packages to install it over Feisty. It's a lot more useful than some other repackaged versions of Ubuntu IMO, like Ultimate edition.... >.>.

---

### Post by lakersforce on 2007-05-28
I still think a good choice would to put in "design packages". And a default installed "launcher" included in the default ubuntu install, so you could choose packages for you purpose. For example if I work with web it makes no sense that I get about 40 useless souund programs when I only need audacity (and yes, I know audacity and how to use apt-get, but thats besides the point). The point is I should, as a complete beginner, choose for example a "web design" package and then get only the programs I need for that and get them setted up to be ready for practical use.

And for example instead of choosing a "audio package", there should be a "Guitar studio" package and a "piano studio" packages and a "sound mixing" package. The package choices should be more concise, not painted as broad as they are.

---

### Post by MetalMusicAddict on 2007-05-28
> **lakersforce said:**
> I still think a good choice would to put in "design packages". And a default installed "launcher" included in the default ubuntu install, so you could choose packages for you purpose. For example if I work with web it makes no sense that I get about 40 useless sound programs when I only need audacity (and yes, I know audacity and how to use apt-get, but thats besides the point). The point is I should, as a complete beginner, choose for example a "web design" package and then get only the programs I need for that and get them setted up to be ready for practical use.
Well in that case you would only install the graphics meta and grab the last couple of apps you need. We really wont be able to please everyone. :)

> And for example instead of choosing a "audio package", there should be a "Guitar studio" package and a "piano studio" packages and a "sound mixing" package. The package choices should be more concise, not painted as broad as they are.

Have you installed Ubuntu Studio from disk? Thats the way its meant to be installed. The metas in the repos are merely a representation of those choices given in our installer. If we created metas for every type of recording that people do its simply too much work and really unnecessary to us.

You can use our installer to install a base system where you would get the audio settings we enable by default then grab the packages you want on top of that. :)

---

### Post by hakimaki on 2007-05-28
I love Ubuntu Studio.  I did a fresh install of it to overwrite my preexisting feisty base install.  Having tried other media distros such as Musix and Studio64, Im really happy with this release.  Many thanks to all who worked on the project!

On a side note, my computer runs faster with Studio installed than my previous Feisty install which im really not complaining about.  Was this expected and intentional by the developers?

---

### Post by MetalMusicAddict on 2007-05-28
> **hakimaki said:**
> On a side note, my computer runs faster with Studio installed than my previous Feisty install which im really not complaining about.  Was this expected and intentional by the developers?

It really shouldnt be. Underneath its the same Feisty. We remove apps from the base they you add what you want to focus on. Some have said the system feels faster using the -lowlatency kernel.

---

### Post by DJ Wings on 2007-05-28
I personally prefer dyne:bolic, as it runs much faster than Ubustu.

---

### Post by shen-an-doah on 2007-05-29
I like Studio. I haven't used it much yet as my year at uni is mostly over (just have write-ups to do, all the real work is done). Hopefully I'll be using it a lot more next year whiule doing my masters.

Also, the existence of Studio was one of the main inspirations for the project I started this year involving introducing music tech people to OSS. Hopefully I'll be able to involve Studio more as the project develops (as it is, I haven't done much, as it only came out a few days before I did the first workshop).

---

### Post by FeistyStyle on 2007-05-29
I currently just have most of the Ubuntu Studio software, like Ardour, JACK, and Gimp just installed to my Feisty Fawn distro

What are the advantages of the low latency kernel? and Studio can do anything Feisty can do right since it is still basically installed over Feisty?

---

### Post by shen-an-doah on 2007-05-29
> **FeistyStyle said:**
> I currently just have most of the Ubuntu Studio software, like Ardour, JACK, and Gimp just installed to my Feisty Fawn distro

What are the advantages of the low latency kernel? and Studio can do anything Feisty can do right since it is still basically installed over Feisty?

Low latency does what it says on the tin, really. [http://en.wikipedia.org/wiki/Latency_%28audio%29](http://en.wikipedia.org/wiki/Latency_%28audio%29)

You can record stuff on a normal kernel fine, but if anything happens, it's more likely to affect your recording than if you're using low latency (because there's more time for something to happen).

And as far as I'm aware, Studio can do everything Feisty can do. This should be definite if you've just installed it over your normal Feisty install.

---

### Post by FeistyStyle on 2007-05-29
K well then are there any down sides to Studio?

---

### Post by shen-an-doah on 2007-05-29
> **FeistyStyle said:**
> K well then are there any down sides to Studio?

Not that I can tell. When I first booted into the low latency Kernel, I couldn't use XGL/Beryl, but that may be because it's a different kernel, so I just needed to tell it to use the right driver for my video card. I haven't tried it again though as 3D effects isn't something you really need when doing audio recording...

---

