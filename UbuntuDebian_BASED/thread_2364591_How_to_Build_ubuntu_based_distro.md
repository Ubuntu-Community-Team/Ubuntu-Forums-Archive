---
title: "How to Build ubuntu based distro"
date: 2017-06-25
forum: Ubuntu/Debian BASED
---

### Post by tuxheroo on 2017-06-25
Hello Guys

I'm Searching for a way to build a custom ubuntu distro for me 
and i don't know from where to get started can you help me 
to start building my own ubuntu based distro

---

### Post by howefield on 2017-06-25
The "*Ubuntu Development Version*" forum is for postings regarding the current development release, at the moment 17.10.

Seeing as you want to create an Ubuntu based distribution thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by Bucky Ball on 2017-06-25
Welcome. Well, you could start with the [minimal install]("https://duckduckgo.com/?q=ubuntu+minimal&t=hz&ia=web") and work your way up from there. The minimal install installs the Ubuntu kernel only and you do the rest. Do you know what elements you are going to use for your custom Debian/Ubuntu OS? Which window manager, desktop manager, package manager (if you use one), file manager, browser, email, etc? Presuming you intend to use all this stuff. The minimal gives you none of these by default so up to you to install them.

On the first boot of a minimal install you will be at what looks like a large terminal screen. From there, you start installing what you like. I usually start with a desktop environment, a package manager, file manager, browser and take it from there. 

You could also go for a -core install which is my own preference - Lubuntu-core, Xubuntu-core or Ubuntu-core and there could be others - and tweak that to your liking. You'll be able to find information on the core versions with a quick search for each. 

Hope that gives you some ideas. I'd go the minimal install. You'd learn a lot as it takes a bit of planning, but you'll wind up with exactly what you want and it will be fast.

* Just a note: if you are doing a minimal install, DON'T install ubuntu-desktop or any other *buntu-desktop. This is equivalent to installing Ubuntu and if you do that, you may as well have installed a regular Ubuntu from the start. The point of all this is to create your own Franken-hybrid OS! ;)

* Another note: FWIW, I like a lightweight system myself. My modus operandi was always the minimal install. For the past couple of years, however, I have been using Xubuntu-core as that is the point I would spend time getting to when working up a minimal install in the past anyway. You get a desktop environment and a couple of other things with the -core version, but still up to you to install apps of your choice (package manager, browser, email, etc.).

---

### Post by tuxheroo on 2017-06-26
> **Bucky Ball said:**
> Welcome. Well, you could start with the [minimal install]("https://duckduckgo.com/?q=ubuntu+minimal&t=hz&ia=web") and work your way up from there. The minimal install installs the Ubuntu kernel only and you do the rest. Do you know what elements you are going to use for your custom Debian/Ubuntu OS? Which window manager, desktop manager, package manager (if you use one), file manager, browser, email, etc? Presuming you intend to use all this stuff. The minimal gives you none of these by default so up to you to install them.

On the first boot of a minimal install you will be at what looks like a large terminal screen. From there, you start installing what you like. I usually start with a desktop environment, a package manager, file manager, browser and take it from there. 

You could also go for a -core install which is my own preference - Lubuntu-core, Xubuntu-core or Ubuntu-core and there could be others - and tweak that to your liking. You'll be able to find information on the core versions with a quick search for each. 

Hope that gives you some ideas. I'd go the minimal install. You'd learn a lot as it takes a bit of planning, but you'll wind up with exactly what you want and it will be fast.

* Just a note: if you are doing a minimal install, DON'T install ubuntu-desktop or any other *buntu-desktop. This is equivalent to installing Ubuntu and if you do that, you may as well have installed a regular Ubuntu from the start. The point of all this is to create your own Franken-hybrid OS! ;)

* Another note: FWIW, I like a lightweight system myself. My modus operandi was always the minimal install. For the past couple of years, however, I have been using Xubuntu-core as that is the point I would spend time getting to when working up a minimal install in the past anyway. You get a desktop environment and a couple of other things with the -core version, but still up to you to install apps of your choice (package manager, browser, email, etc.).


Thanks for your reply
I knew this way to use minimal install and start installing packages . Gui  etc then use remastersys it build my live cd but i had seen at ubuntu wiki tutorial which is stated as unofficial is that the same way or its different 
And 
Is minimal iso have ubuntu core or i must install it to my mini iso and how can do that if it us that 

Thanks

---

### Post by Bucky Ball on 2017-06-26
As far as I know you can choose either Lubuntu-core or Xubuntu-core from tasksel, where you choose a machine profile during install. If you don't install -core there, you can use 'xubuntu-core^' command on the first boot. For Xubuntu-core,

> The recommended way is to download the mini.iso, install, and when prompted, install the Xubuntu minimal installation task. If you&#8217;d prefer to wait until after the installer finishes to install the Xubuntu core task, you can simply type sudo apt-get install xubuntu-core^ (don&#8217;t forget the caret!) and away it&#8217;ll go.

From [here]("https://xubuntu.org/news/introducing-xubuntu-core/"). For Lubuntu-core, use 'lubuntu-core^'. I suggest you go for the 16.04 LTS release as stable and supported until April 2019.

---

