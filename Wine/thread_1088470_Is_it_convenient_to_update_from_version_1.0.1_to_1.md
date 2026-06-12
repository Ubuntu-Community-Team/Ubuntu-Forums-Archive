---
title: "Is it convenient to update from version 1.0.1 to 1.1.16?"
date: 2009-03-06
forum: Wine
---

### Post by El Potro on 2009-03-06
Hi everybody, I couldn't find information on the web and wanted to hear what would you (that for sure know more than me about this) do in my place.

I use some Win apps, like Photoshop CS 2 (Works OK) Virtualdub (Works but not that OK) Ares, Counter Strike, and Sound Forge 9 which doesn't work very well, though I've installed winetricks and so dotnet20, vcrun2005sp1, quicktime72 and wmp10. 

Sound Forge 9 presents glitches when I open the menus. The text on it completely disappears, so I don't know which option I'm pressing down.

I tried to install Worms Armageddon, or Worms World Party without luck.

Is it a good idea to update to version 1.1.16? Or is it unstable and proper to several changes? I have no idea on this topic, please give me some notions here. Any help will very appreciated!

Thanks,

Mauricio

---

### Post by ajgreeny on 2009-03-06
It should not be a problem.  I have had the latest version of wine ever since I started with ubuntu and added the wine repos
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) **hardy** main
If you run intrepid just use the appropriate distro version instead of **hardy**.

---

### Post by FrozenFox on 2009-03-06
Wine 1.1.16 is an 'unstable' version as defined by the wine devs. Whether or not it is literally unstable ('unstable' as far as software goes means new/untested, not necessarily actually unstable) for you really depends, but usually releases are pretty 'stable' for me. However, if you're going to wait for the next "stable" version before updating, you're probably going to be waiting a long time. As said above, it probably couldn't hurt, and it's not very difficult. You could probably downgrade if you wanted to afterward if you had too many problems, but i doubt you would.

Alternatively, if you update to 1.1.16, there's a program called PlayOnLinux with which can download and install/manage multiple/other (older or newer) versions of wine -locally-, such that you can use old versions (1.0.1) to run a program should 1.1.16 cause any problems you didn't have before. Note though that it's a little bit of a pain (or was, last i checked a few months ago) to set it up with other wine versions, but it can be done.

---

### Post by Meow27 on 2009-03-06
> **FrozenFox said:**
> Wine 1.1.16 is an 'unstable' version as defined by the wine devs. Whether or not is literally unstable for you really depends, but usually releases are pretty 'stable' for me. However, if you're going to wait for the next "stable" version before updating, you're probably going to be waiting a long time. As said above, it probably couldn't hurt, and it's not very difficult. You could downgrade if you wanted to afterward.

Alternatively, if you update to 1.1.16, there's a program called PlayOnLinux with which can download and install other (older or newer) versions of wine -locally-, such that you can use old versions (1.0.1) to run a program should 1.1.16 cause any problems you didn't have before. Note though that it's a little bit of a pain (or was, last i checked a few months ago) to set it up with other wine versions, but it can be done.

or you just use this
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by cogadh on 2009-03-06
PlayOnLinux lets you use more than one version of Wine at the same time. The Wine package archive doesn't let you do that at all, it just lets you replace one version of Wine with another.

As for ease of upgrading, just follow the instructions [here]("http://www.winehq.org/download/deb") and it will be practically effortless. Just be aware of what FrozenFox said about the meaning of "unstable". I certainly doesn't mean "broken" but it does mean the newer version could have new code in them that will break some things when it fixes others. It is the risk of being on the bleeding edge of Wine.

If you want to confirm whether or not an application works with Wine and what version works best, check the [Wine Application Database]("http://appdb.winehq.org/")

---

### Post by El Potro on 2009-03-07
Thank you all for your advices. I decided to take my chances so I downloaded the latest .deb package and tried to install it.

Forgive me for being such an ignorant but as soon as I try to install it, I find this impediment: Dependency is not satisfiable: libasound2.

But the package is already installed... this is weird.

Does anyone know the why?

---

### Post by cogadh on 2009-03-07
Not sure why that happens, but it shouldn't if you install using the repository instead of downloading the separate .deb package.

---

### Post by El Potro on 2009-03-08
Sorry, it was my mistake. I misunderstood which version of wine was running in this computer. I was downloading the Interpid Ibex .deb, instead of the Hardy's one.

Thank you cogadh.

PS: Have already installed it and Sound Forge 9, for instance, works WAY lot better!!

---

