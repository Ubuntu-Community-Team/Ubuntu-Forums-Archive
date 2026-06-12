---
title: "My Perfect Package Manager Would..."
date: 2011-04-07
forum: The Cafe
---

### Post by beastrace91 on 2011-04-07
Finish the sentence.

Anyone who has been in the world of Linux for more than a minute knows there is a good deal of choice when it comes to package manager. What is your package manager of choice and why?

Why do you prefer to use RPM/dpkg/apt-get/yum/pacman/emerge/<insert random package manager here> over others out there?

~Jeff

---

### Post by fuduntu on 2011-04-07
> **beastrace91 said:**
> Finish the sentence.

Anyone who has been in the world of Linux for more than a minute knows there is a good deal of choice when it comes to package manager. What is your package manager of choice and why?

Why do you prefer to use RPM/dpkg/apt-get/yum/pacman/emerge/<insert random package manager here> over others out there?

~Jeff

I prefer RPM, it's cleaner than dpkg, simpler to build and manage an RPM package, and it supports package verification flag (-V).

I wouldn't have a preference of apt over yum if apt supported the "whatprovides" function, but it doesn't so yum wins here.  Unfortunately, yum execution is slower.

---

### Post by Lucradia on 2011-04-07
Why do I need a perfect package manager when the current one I use works? For me, Synaptic and APT and whatever Package my distro takes are fine (DPKG, RPM, YUM, whatever.)

I don't need to be special.

---

### Post by beastrace91 on 2011-04-07
> **Lucradia said:**
> I don't need to be special.

It's not about being "special" its about continuing to improve upon our technology/software.

~Jeff

---

### Post by Lucradia on 2011-04-07
> **beastrace91 said:**
> It's not about being "special" its about continuing to improve upon our technology/software.

~Jeff

If it works, don't fix it?

---

### Post by beastrace91 on 2011-04-07
> **Lucradia said:**
> If it works, don't fix it?

Windows XP "works". Does it work well? No, but it works. That being said I did not post this to argue with trolls, so please if you are not going to contribute to the actual discussion please go be off topic elsewhere.

~Jeff

---

### Post by undecim on 2011-04-07
I was actually thinking about this yesterday while trying to work through dependency hell for a compiled program. I've even thought about writing my own frontend to dpkg that would do what I want.

A few things I would like to see:

[LIST]
[*]Concurrent downloads from multiple mirrors.
[*]Easily configurable bittorrent/p2p downloading and temporary mirroring (e.g. so when I download a large game like Nexuiz and my brother wants to play it, too, it's easy for him to download the package from my computer on LAN; I know there are ways to do this, but the keyword here is "easy")
[*]Installation while downloading (i.e. download the dependencies first. Install the dependencies while the main package is downloading)
[*]Package "tiers". (e.g., main packages like GIMP, Firefox, etc. that the user would intend to install would be tier 1. High level dependencies and dev tools, like python and certain CLI tools are tier 2, libs are tier 3, core system is tier 4.) This way, I could view only Tier 1 packages to look for an application, tier 2 for dev stuff, etc. A package recommend or suggest would never automatically install a package from a higher tier. 
[*]Union recommends/suggests. Some packages only make sense to install when two other packages are installed. For example, a plugin to show your current rhythmbox song in pidgin only makes sense if you have those two installed. If you install 1, then when you install the second, that package should be a recommend or a suggest. Or, a package might be configured to automatically install iff it has a certain number of packages suggesting or recommending it.
[/LIST]

---

### Post by mips on 2011-04-07
be just like Pacman.

---

### Post by unknownPoster on 2011-04-07
> **Lucradia said:**
> If it works, don't fix it?

One could argue that current package managers don't work. yum is fairly slow, apt's dependency resolution could be better, pacman doesn't have signed packages, etc. No software is or will ever be perfect, but why not try to improve it?

The moment you become complacent with current software is the moment innovation and improvements stop.

---

### Post by WRDN on 2011-04-07
The main feature I would love to see in package managers is delta packages - this way, you only download the package difference, between your installed version and an updated version of an application. See [Yum presto]("http://fedoraproject.org/wiki/Releases/FeaturePresto") for an example of this.

---

### Post by LowSky on 2011-04-07
yaourt... I like that I can type the name of a program and get a list of packages. Very helpful if you want to see add-ons available.

---

### Post by Simian Man on 2011-04-07
The apt tools also have horrible interfaces compared to yum and pacman.  The commands are harder to remember and the output formatting is awful.  Yum is my favorite, it has a great interface, great feature set and is not that slow - though I wouldn't complain if it were faster :).

---

### Post by mamamia88 on 2011-04-07
be able to install all updates without breaking manually installed nvidia drivers

---

### Post by fuduntu on 2011-04-07
> **WRDN said:**
> The main feature I would love to see in package managers is delta packages - this way, you only download the package difference, between your installed version and an updated version of an application. See [Yum presto]("http://fedoraproject.org/wiki/Releases/FeaturePresto") for an example of this.

Yum has this capability today as long as the delta metadata has been created for the repository and is actively updated as packages are added changed and removed.

---

### Post by el_koraco on 2011-04-07
> **WRDN said:**
> The main feature I would love to see in package managers is delta packages - this way, you only download the package difference, between your installed version and an updated version of an application. See [Yum presto]("http://fedoraproject.org/wiki/Releases/FeaturePresto") for an example of this.

conary from rpath and foresight does this by default.

---

### Post by Simian Man on 2011-04-07
> **el_koraco said:**
> conary from rpath and foresight does this by default.

Yum does in Fedora too since the Presto plugin has come default since F11.

---

### Post by el_koraco on 2011-04-07
my bad, didn't even notice the last sentence. 
well, maks sense, from what i've read, conary was envisoned as a yum clone, "rpm managing done right". haven't tried it yet, but the impressions i've been able to read are pretty good.

---

### Post by jerenept on 2011-04-07
```
wget http://software-website.org/downloads/program.tgz
tar -xzf program.tgz
cd ~/program
sudo ./configure
make
sudo make install
```

Otherwise, portage (from Gentoo or Sabayon)

---

### Post by earthpigg on 2011-04-07
this is a fantasy land question. so here i go, off to fantasy land.

...have all of the below be mostly pointy-clicky, like USC.

...be seamlessley integrated with the bittorrent protocol or similar. 

...have a slider that i can set, to throttle my upstream to zero if i choose.

...have strong and barely moderated review process, like android market.

...also be integrated with relevant forums. google-like algorithms decide what threads show up, if the user has this enabled. (or, hell, just route it through a google advanced search.)

...allow sandboxed package installations. permanent GUI fakeroot. (so i can have different versions of the same package along with duplicate depends n levels deep, and compare and contrast them. if i choose. it would be nice if i could easily have firefox 4.0 with Sun Java alongside firefox 3.6 with icedtea. ditto for openoffice and libreoffice.)

...allow me to select how many levels of recursion i want to go with depends when doing the above.

...include an option to get as detailed and nitty gritty as synaptic gets, without having to quit software center (for example) and then start synaptic.

...seamlessley integrate packages of other formats and from other repositories either in or not in sandbox mode, if i choose. Arch Users Repo, for example, alongside CentOS repos. and in ultimate fantasy world: android market. (the sandboxing is pretty critical for this part of my fantasy-land.) the AUR was the best part of Arch, for me.

...keep track of when the last time anything accessed any part of given a package was.

...when a novice user first starts it, though, none of this is visible. it looks just as friendly as USC until you open the preferences.

---

### Post by galacticaboy on 2011-04-07
A merge between apt-get and RPM.

---

### Post by beastrace91 on 2011-04-07
> **mamamia88 said:**
> be able to install all updates without breaking manually installed nvidia drivers

That only happens when you change kernels... Just disable kernel updates.

Thanks for all the suggestions folks, some really good stuff here! Needless to say I have begun working on something with a small team :) Might be awhile till we have something to show for it, but we want to make we get it right before unleashing it into the wild!

~Jeff

---

### Post by earthpigg on 2011-04-07
> **beastrace91 said:**
> That only happens when you change kernels... Just disable kernel updates.

Thanks for all the suggestions folks, some really good stuff here! Needless to say I have begun working on something with a small team :) Might be awhile till we have something to show for it, but we want to make we get it right before unleashing it into the wild!

~Jeff

oh, i didn't realize someone was actually working on something based on this thread. lol. in that case, i shall prioritize:

-GUI sandboxing options.
-GUI options of installing packages from non-native-format repositories using alien or similar. I want AUR!
-Dynamically make various gnome themes available from various different websites appear in the package manager!

That last one isn't a huge game-changer, but it is probably the easiest to implement - having a documented accomplishment is great for a team's morale. I'd use it.

---

### Post by Zerocool Djx on 2011-04-07
I could go with anything really,.. but I just wish there was one universal one. Like Windows had Zip for a while then RaR took over. RPM is pretty basic to use, but I still prefer tar. I guess it's about preference, but just as anything else with Linux, someone always has to be special, hence the million different versions of Linux Vs everyone working together.

---

### Post by juancarlospaco on 2011-04-07
> **galacticaboy said:**
> A merge between apt-get and RPM.

Thats already done a long time ago by Canonical and Conectiva.
Manage RPM and DEB, If you want to try: 
```
sudo apt-get install smartpm
```

---

### Post by mamamia88 on 2011-04-07
> **beastrace91 said:**
> That only happens when you change kernels... Just disable kernel updates.

Thanks for all the suggestions folks, some really good stuff here! Needless to say I have begun working on something with a small team :) Might be awhile till we have something to show for it, but we want to make we get it right before unleashing it into the wild!

~Jeff

but i like to have the latest kernel

---

### Post by beastrace91 on 2011-04-07
> **mamamia88 said:**
> but i like to have the latest kernel

Then don't complain about kernel modules breaking when you change kernels. This has nothing to do with your package manager /offtopic

~Jeff

---

### Post by mamamia88 on 2011-04-07
fair enough

---

### Post by zer010 on 2011-04-07
> **undecim said:**
> I was actually thinking about this yesterday while trying to work through dependency hell for a compiled program. I've even thought about writing my own frontend to dpkg that would do what I want.

A few things I would like to see:

[LIST]
[*]Concurrent downloads from multiple mirrors.
[*]Easily configurable bittorrent/p2p downloading and temporary mirroring (e.g. so when I download a large game like Nexuiz and my brother wants to play it, too, it's easy for him to download the package from my computer on LAN; I know there are ways to do this, but the keyword here is "easy")
[*]Installation while downloading (i.e. download the dependencies first. Install the dependencies while the main package is downloading)
[*]Package "tiers". (e.g., main packages like GIMP, Firefox, etc. that the user would intend to install would be tier 1. High level dependencies and dev tools, like python and certain CLI tools are tier 2, libs are tier 3, core system is tier 4.) This way, I could view only Tier 1 packages to look for an application, tier 2 for dev stuff, etc. A package recommend or suggest would never automatically install a package from a higher tier.
[*]Union recommends/suggests. Some packages only make sense to install when two other packages are installed. For example, a plugin to show your current rhythmbox song in pidgin only makes sense if you have those two installed. If you install 1, then when you install the second, that package should be a recommend or a suggest. Or, a package might be configured to automatically install iff it has a certain number of packages suggesting or recommending it.
[/LIST]

^THIS ^.^d
It sounds like some great features for any type of PM, GUI or CLI.  I'm just getting into Fedora so I haven't scratched the surface of yum/rpm yet so I'm still kinda partial to apt/dpkg...

---

