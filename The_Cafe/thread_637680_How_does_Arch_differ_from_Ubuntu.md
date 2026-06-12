---
title: "How does Arch differ from Ubuntu?"
date: 2007-12-11
forum: The Cafe
---

### Post by kevdog on 2007-12-11
Ive read the FAQ on the Arch Website -- it didnt say much.  How is Arch different than linux -- I dont mind compiling the kernel.  I would just prefer a DE like Gnome.

---

### Post by 23meg on 2007-12-11
Some major differences are that Arch has a different package manager (Pacman), and is a [rolling release]("http://en.wikipedia.org/wiki/Rolling_release") distro.

---

### Post by epimer on 2007-12-11
The biggest difference between Arch and Ubuntu is in what each distro gives you to start with. For better or worse, Ubuntu (Desktop install, at least) gives you a desktop environment and a bunch of programs pre-installed. Arch doesn't; you don't even get X installed. A base install of Arch gives you a working command line and the means to install new packages - and that's it!

The upshot is that you end up with only what you want installed, and that's what made me switch to it. It's a lot more hands on than Ubuntu, but the wiki is pretty good for walking you through what needs to be done.

As mentioned above, it's rolling release, so there's no need to upgrade every 6 months. It's pretty bleeding edge, too, although you can choose your preferred balance between stability and latest releases by choosing to use community, testing or unstable repositories depending on your own preference.

Pacman is like apt-get, but (imo) a little better. Arch also has ABS for compiling things from source, and the AUR is a community repository which gives you access to all sorts of neat gubbins.

---

### Post by kevdog on 2007-12-11
The command line is OK with me -- but its possible to add X with either a Window manager and Desktop Environment on top?

One last question since I think I will try it -- as far as compiling packages from source, how does ABS differ from the general download the source files, attempt to compile source, pull hair out to find and compile dependencies, and then compile and install the intended program?  Does ABS download the source for the dependencies also?

---

### Post by b9anders on 2007-12-11
> **kevdog said:**
> The command line is OK with me -- but its possible to add X with either a Window manager and Desktop Environment on top?

Yes. That is the intent. You just have to install and set it up for yourself - that way, the only thing that will run as what you have designated.

---

### Post by n3tfury on 2007-12-11
> **kevdog said:**
> Ive read the FAQ on the Arch Website -- it didnt say much.  How is Arch different than linux -- I dont mind compiling the kernel.  I would just prefer a DE like Gnome.

[http://ubuntuforums.org/showthread.php?t=231311&highlight=arch](http://ubuntuforums.org/showthread.php?t=231311&highlight=arch)

---

### Post by eljoeb on 2007-12-11
[http://wiki.archlinux.org/index.php/The_Arch_Way]("http://wiki.archlinux.org/index.php/The_Arch_Way")

I think that says a lot.

---

### Post by Onyros on 2007-12-11
> **kevdog said:**
> The command line is OK with me -- but its possible to add X with either a Window manager and Desktop Environment on top?

One last question since I think I will try it -- as far as compiling packages from source, how does ABS differ from the general download the source files, attempt to compile source, pull hair out to find and compile dependencies, and then compile and install the intended program?  Does ABS download the source for the dependencies also?Yep, it's possible and quite simple to add X with a Window Manager.

All you have to do, after you boot into your Arch system with a base install is

```
pacman -S xorg
```

and then add "nvidia" / "nvidia71xx" (for legacy nvidia cards) or "fglrx" and then make the appropriate changes in your xorg.conf file.

If you want GNOME, for example (and it's one of the fastest default GNOME's I've seen yet), all you have to do is

```
pacman -S gnome
pacman -S gnome-extra

```
and select, package by package what you want and what you don't want installed.

Also, compiling from source is streamlined in Arch. The process is pretty much going to AUR, selecting a package you want to install, which has a PKGBUILD file in there. That's where dependencies and the location of the source files is defined.

You just browse into the "tar xvf" 'd folder, run "makepkg -s" and it'll take care of the hair-pulling process for yourself. It even takes care of dependencies for you (that's what "-s" is for).

If you "makepkg" with no further options, it creates a pkg.tar.gz file for you to install with pacman (with pacman -U packagename.pkg.tar.gz - you can only install as root, so "su" first, ask questions later). If you do it with the "-i" option it will also invoke pacman to install the package in one single command.

Once you use it, you'll be hooked. And believe me, there's no turning back. Be sure to read the Arch Wiki for help, short of Gentoo's manuals, it's one of the best online resources for a distro I've ever seen. Also, be sure to master your "rc.conf" file in Arch, it's one of the most important config files in your entire system.

Extra final tip: do not use Arch's default repos. They're throttled, so be sure to choose a good one nearer to your location. ;)

---

### Post by fuscia on 2007-12-11
let's say using linux is like going on a camping trip. you can either bring toilet paper with you, or not. ubuntu is the former, arch is the latter.

---

### Post by kevdog on 2007-12-11
> **fuscia said:**
> let's say using linux is like going on a camping trip. you can either bring toilet paper with you, or not. ubuntu is the former, arch is the latter.


That cleared it up for me!!


> [http://ubuntuforums.org/showthread.p...highlight=arch](http://ubuntuforums.org/showthread.p...highlight=arch)

Yea a good reference indeed.  I didnt know the forums contained so many Arch users.

---

### Post by n3tfury on 2007-12-11
me neither.

---

### Post by Onyros on 2007-12-11
> **fuscia said:**
> let's say using linux is like going on a camping trip. you can either bring toilet paper with you, or not. ubuntu is the former, arch is the latter.And keeping up with that, Gentoo is like using poison-ivy as toilet paper, whereas Arch is like... errmm... borrowing toilet paper from someone who brought it?

---

### Post by n3tfury on 2007-12-11
> **Onyros said:**
> And keeping up with that, Gentoo is like using poison-ivy as toilet paper, whereas Arch is like... errmm... borrowing toilet paper from someone who brought it?

which distro is like using snow to wipe your ***?

---

### Post by Xbehave on 2007-12-11
> **n3tfury said:**
> which distro is like using snow to wipe your ***?
mint (ive never tried it but ive heard its like a polished ubuntu with a bleeding edge repo added in)

---

### Post by PurposeOfReason on 2007-12-11
> **n3tfury said:**
> which distro is like using snow to wipe your ***?
Arclinux without an internet connection.

---

### Post by n3tfury on 2007-12-11
> **Xbehave said:**
> mint (ive never tried it but ive heard its like a polished ubuntu with a bleeding edge repo added in)

you've obviously never wiped your *** with snow  ;P

purpose - good answer.

---

### Post by crimesaucer on 2007-12-11
> **kevdog said:**
> The command line is OK with me -- but its possible to add X with either a Window manager and Desktop Environment on top?

One last question since I think I will try it -- as far as compiling packages from source, how does ABS differ from the general download the source files, attempt to compile source, pull hair out to find and compile dependencies, and then compile and install the intended program?  Does ABS download the source for the dependencies also?

With Archlinux, you install with no gui. It's not that difficult. If you have directions to follow it's actually pretty damn easy...


You will also have to edit some config file in nano or vi, and you will need to know some info beforehand... all of it is discussed in the install wiki and also in this "HOWTO" guide which I liked because it has instructions with screenshots: [http://www.raiden.net/?cat=&aid=276](http://www.raiden.net/?cat=&aid=276)


After you've done all of the steps of the base install and have finished with grub, you will exit the install and reboot. 


Now you will be in your grub or lilo, and you will select Arch.


You will now be in your virtual console number 1 or vc/1, you will then login as Root, and begin to configure your passwd and adduser...


... after that you will install pacman package manager, and then configure your ftp configuration files for Arch's repositories, and after that, you will begin installing the full system upgrade with "pacman -Syu".


Next you will install the X window system with xorg  and xterm, and your xf86 video driver.


Now this is the difficult part, because you will have to configure xorg yourself with "Xorg -configure", and then you will have to copy it from root to /etc/X11/xorg.conf, and then you'll have to edit your X11/xorg.conf to make it work because you might need to add certain parts that didn't configure properly. Read this part: [http://www.raiden.net/?cat=2&aid=276&pid=8](http://www.raiden.net/?cat=2&aid=276&pid=8)


So, if everything worked... you can startx. And if successful, then it will be time to add repositories and install a Desktop Environment like Gnome.
  

You will also have to re-edit your config files again, and you will keep adding to them when you add certain apps. You will get to know your xorg.conf, rc.conf, pacman.conf, and you resolve.conf very well to name just a few. 


That should be it, you should have a fully working OS and all you'll have to do from here is customize it and fix any problems that you might have.


###########################################


....... and I wouldn't say Arch is like not having toilet paper. If you're going to use that simile of the camping trip bathroom experience, then I would say that:


Archlinux is like going on a camping trip and having to use the bathroom with no toilet around. You walk off into the woods with your toilet paper, your shovel, and your lighter (to burn the tp and burry the do-do like a good camper)... and you feel weird about not using a toilet...


Then you find a meadow in the woods, and there is a nice tree stump to sort of lean/sit on, that allows you to comfortably do your business... (and you had been worried that you were gonna squat the whole time and get messy)... 


As you do your thing, you all of a sudden feel free... and one with nature. You notice the breeze, the birds chirp, and the sun feels good on your body. You feel like this should be the only way of going to the bathroom... the most primal and natural way.


You finish and walk back to your campsite feeling as one with nature.



Compare to ubuntu.... which I love also, it would be more like you were a bit scared to hike into the woods alone... and a little too used to using a toilet to want to do the outdoors thing... So, you hold it in for a little while, and then walk the opposite direction, back towards the parking lot where there are some RV's parked. You then meet some nice RV campers and they let you use their super cushy RV bathroom, with shag carpeting, a fan, a sink, little bath soaps, and a hand towel... and 2 ply Charmin toilet paper. 


You have a good relieving bathroom experience. It definitively beats a jiffy john (windows xp) or a sterile public restroom (apple)... It's even better than your new apartment... which should have a nice bathroom... but your roommates are so lame and messy, and there's always an issue with something (vista)... So this RV's bathroom is a very enjoyable moment for you. You think how you might want to own an RV and travel freely around the country with the added luxury to always have a nice bathroom and a shower, a tv with satellite feed, wifi access, a kitchen, and a comfortable bed to sleep in.


...... for me, I would like to both own that RV and also be brave enough to rough it in the woods for the true camping experience. Both ways are nice. Both ways are better than most of the other options.

---

### Post by Mateo on 2007-12-11
Actually that seems way too complicated to me.  Why shouldn't Pacman be preinstalled?

it seems you should be able to login as root and do the Pacman equivalent of "apt-get install gnome" and X installs automatically since gnome is dependent on X.

---

### Post by crimesaucer on 2007-12-11
> **Mateo said:**
> Actually that seems way too complicated to me.  Why shouldn't Pacman be preinstalled?

it seems you should be able to login as root and do the Pacman equivalent of "apt-get install gnome" and X installs automatically since gnome is dependent on X.

Well installing the X windows system is one of the nice things ubuntu does for you in the install, as well as having the debian configuration of your xorg.conf which was always perfect for me. As well as installing Gnome and xfce4 in the install.


In Arch, you install everything yourself so you basically build it piece by piece. That is why you install xorg first, so that you can install a DE next. 


The entire process actually takes less time than an ubuntu install CD... and get's you close to the same place... of course, there are many more apps installed in ubuntu, and all of the new features for restricted drivers and things...

---

### Post by epimer on 2007-12-11
> **Mateo said:**
> 
it seems you should be able to login as root and do the Pacman equivalent of "apt-get install gnome" and X installs automatically since gnome is dependent on X.

Fair enough, but what parts of X? Do you want all the font stuff as well? Which driver, vesa or nv or any of the others? And hence that's the start down the path to the Ubuntu route (not criticising per se, just pointing out a difference). Arch lets you decide just what you want (although, as an aside, there is a xorg group to handle the nitty-gritty).

---

### Post by kevdog on 2007-12-11
All that stuff seems fairly easy except the xorg.conf configuration.  The default edgy generated xorg.conf was totally incorrect on my laptop, and it took me a long time to figure it out.  I cringe everytime I have to edit the file, since one wrong line can kill your x-server.  I guess I will just have to get up close and cozy with the process.

---

### Post by Onyros on 2007-12-11
> **kevdog said:**
> All that stuff seems fairly easy except the xorg.conf configuration.  The default edgy generated xorg.conf was totally incorrect on my laptop, and it took me a long time to figure it out.  I cringe everytime I have to edit the file, since one wrong line can kill your x-server.  I guess I will just have to get up close and cozy with the process.Naaah, don't bother with much tweaking. Just copy a good xorg.conf from a working system and use it in your Arch system.

I'm not much of a xorg.conf tweaker myself, so that's how I did it, in the end. Apart from using a 

```
DisplaySize 260 195 # 100 DPI @ 1024x768
``` for my X31, so that fonts would be correctly displayed at 100 DPI in Fluxbox.

BTW, the analogies have been beautiful, especially the one comparing Arch with being one with nature.

Just one final disclaimer regarding Arch, and using the same analogy: before you do sit on that tree stump, there are two major rules you'll have to follow.

# 1 - Make sure there are no bears (or donkeys) around - you're in no position to be caught off-guard;

# 2 - IF you are caught off-guard, make you sure you can improvise. Quickly.

---

### Post by crimesaucer on 2007-12-11
> **kevdog said:**
> All that stuff seems fairly easy except the xorg.conf configuration.  The default edgy generated xorg.conf was totally incorrect on my laptop, and it took me a long time to figure it out.  I cringe everytime I have to edit the file, since one wrong line can kill your x-server.  I guess I will just have to get up close and cozy with the process.

You can save a copy of your working xorg.conf from ubuntu to disk, and then have it as a backup just in case you have problems... you can always mount the cd and cp it in to your ~/ home directory in Arch, and then have that xorg.conf to compare you new one with, and maybe troubleshoot your problems from referencing your old xorg.conf, you also can find out details on certain things like the Synaptics Touchpad driver and settings on the Arch wiki.


> **Onyros said:**
> Naaah, don't bother with much tweaking. Just copy a good xorg.conf from a working system and use it in your Arch system.

I'm not much of a xorg.conf tweaker myself, so that's how I did it, in the end. Apart from using a 

```
DisplaySize 260 195 # 100 DPI @ 1024x768
``` for my X31, so that fonts would be correctly displayed at 100 DPI in Fluxbox.




Also, my xubuntu xorg.conf from 7.04 worked in Arch with the old Xorg, but it did not work with the new Xorg... and both times I needed to add the Synaptics Touchpad section, as well as few things like **modes  "1280x800"** and something else for my keyboard. But it's all in that guide and on the Arch wiki.

---

### Post by floke on 2007-12-11
_Ubuntu_

* Installs looooads of stuff - a lot of which you don't need (gnome games anyone?)
* Easy to install
* Apt rocks
* Huge repos
* Moderate speed in linuxland
* 6 month upgrade
* binary distro
* great community
* usual linux filesystem
* based on Debian

_Arch_

* Install only the bits you want (starting with no X)
* Can be tricky to get going first time around (great wiki though)
* Pacman rocks
* Extensive repos (core, extra, community, testing + AUR)
* i686 optimised - speedy gonzales
* rolling release
* binary distro with (ridiculously) easy to compile packages using ABS
* great community
* filesystem modified to keep it simple - eg all modules, daemons and network settings held in one easy to manage config file (/etc/rc.conf)
* not based on anything - but inspired by Crux

---

### Post by Perfect Storm on 2007-12-12
Troll taken care off - please continue the topic.

---

### Post by kevdog on 2007-12-12
> Troll taken care off - please continue the topic

Did I miss something??

---

### Post by floke on 2007-12-13
Just trolls in the garden.

---

### Post by kpkeerthi on 2007-12-13
> 
binary distro with (ridiculously) easy to compile packages using ABS

I stress that a 100 more times. Compiling from source can't be any simpler. And yes, you can choose to recompile (makeworld) your installed packages with CFLAGS optimized for your CPU.

Compare ABS to Gentoo's portage tree.

---

