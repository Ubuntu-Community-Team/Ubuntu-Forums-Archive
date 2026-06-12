---
title: "Considering Arch, some questions"
date: 2009-04-05
forum: The Cafe
---

### Post by happysmileman on 2009-04-05
Hey guys, Kubuntu 8.10 user here, and considering moving to Arch instead of 9.04 when it comes out, I've heard excellent things about KDEmod, and would like rolling releases. A few questions though.

Firstly, what exactly IS kdemod?
I've heard vague explanations of it, generally just that it's slightly tweaked KDE built just for Arch, but what does that mean? Is it very different, or just with some different default settings and a different theme.
Do they actually modify KDE source? And if so, how much is changed?

Secondly, how easy is it to set up/use?
I'm not so worried about how easy it is to set up, though I'd like if I could get up to date NVidia drivers for a fairly old card through package manager :P.
I'm more thinking of day to day usage, installing packages and stuff, getting Wine to work. My brother would be using it as well so I wouldn't want to make him use anything uber-hard or annoying to get used to (Though he uses Kubuntu day-to-day so I doubt it'd be a huge problem)

Thirdly, should I go with Arch or Chakra?
I've heard good things about Chakra, which is basically a LiveCD of Arch plus KDEmod and a GUI installer, but haven't really found much real details of it. I mainly want to know is it actually an improvement on Arch or just vanilla Arch with a much quicker and less hassle install.

Very sorry about asking, but I know there's a lot of people here who've switched from Ubuntu to Arch and I've found mixed answers (or just plain vague ones) to all these questions

EDIT: Oh and how long does it take for packages to be made available? I like to be able to get updates of my software as soon as they're available, especially stuff like KDE packages and Amarok.

---

### Post by &#32 Greg on 2009-04-05
> **happysmileman said:**
> Hey guys, Kubuntu 8.10 user here, and considering moving to Arch instead of 9.04 when it comes out, I've heard excellent things about KDEmod, and would like rolling releases. A few questions though.

Firstly, what exactly IS kdemod?
I've heard vague explanations of it, generally just that it's slightly tweaked KDE built just for Arch, but what does that mean? Is it very different, or just with some different default settings and a different theme.
Do they actually modify KDE source? And if so, how much is changed?

Secondly, how easy is it to set up/use?
I'm not so worried about how easy it is to set up, though I'd like if I could get up to date NVidia drivers for a fairly old card through package manager :P.
I'm more thinking of day to day usage, installing packages and stuff, getting Wine to work. My brother would be using it as well so I wouldn't want to make him use anything uber-hard or annoying to get used to (Though he uses Kubuntu day-to-day so I doubt it'd be a huge problem)

Thirdly, should I go with Arch or Chakra?
I've heard good things about Chakra, which is basically a LiveCD of Arch plus KDEmod and a GUI installer, but haven't really found much real details of it. I mainly want to know is it actually an improvement on Arch or just vanilla Arch with a much quicker and less hassle install.

Very sorry about asking, but I know there's a lot of people here who've switched from Ubuntu to Arch and I've found mixed answers (or just plain vague ones) to all these questions

I can't answer your questions on KDEmod, but I can on the second and third.

Setting up Arch is a bit more difficult than setting up Ubuntu or Suse or Fedora or the like, but it's not too hard at all, espescially considering the great documentation. It's also more fun, IMO, and you learn some things. Arch vs. Chakra- first install go with Arch, or else you'll have an Arch system without understanding Arch.

---

### Post by Polygon on 2009-04-05
> **happysmileman said:**
> Hey guys, Kubuntu 8.10 user here, and considering moving to Arch instead of 9.04 when it comes out, I've heard excellent things about KDEmod, and would like rolling releases. A few questions though.

Firstly, what exactly IS kdemod?
I've heard vague explanations of it, generally just that it's slightly tweaked KDE built just for Arch, but what does that mean? Is it very different, or just with some different default settings and a different theme.
Do they actually modify KDE source? And if so, how much is changed?

Secondly, how easy is it to set up/use?
I'm not so worried about how easy it is to set up, though I'd like if I could get up to date NVidia drivers for a fairly old card through package manager :P.
I'm more thinking of day to day usage, installing packages and stuff, getting Wine to work. My brother would be using it as well so I wouldn't want to make him use anything uber-hard or annoying to get used to (Though he uses Kubuntu day-to-day so I doubt it'd be a huge problem)

Thirdly, should I go with Arch or Chakra?
I've heard good things about Chakra, which is basically a LiveCD of Arch plus KDEmod and a GUI installer, but haven't really found much real details of it. I mainly want to know is it actually an improvement on Arch or just vanilla Arch with a much quicker and less hassle install.

Very sorry about asking, but I know there's a lot of people here who've switched from Ubuntu to Arch and I've found mixed answers (or just plain vague ones) to all these questions


arch is easy enough for me to set up...the only thing that is a royal pain in the A** is the wireless drivers

I do not have any wired connections in my house, my router is literally buried under a bunch of crap in my dads desk, and its almost impossible to reach it. Arch comes with some of the wireless drivers by default, but for me, i have to manually compile it from svn for it to work.

so that requires me finding somewhere with a ethernet jack, plugging it in...and getting a wired connection manually (you learn how to use ifconfig and iwconfig fast) and then downloading the stuff to compile it and then compiling it

i am actually installing arch right now on my laptop, and then wpa supplicant is giving me headaches, its not connecting to my wireless, and i have no idea if its the drivers fault, or i configured wpa supplicant wrong, or something else is going wrong.....its just a pain in the butt. Wireless is the bane of my linux existence, its basically the hardest thing to set up when your installing any linux distro, as you need a internet connection to download stuff and look up how to do it, but you can't get a internet connection unless you have the right drivers and know how to do it. its a regular catch 22.

but once you get wireless set up (if thats applicable) then its easy enough to search the arch wiki for what your trying to set up. It has great guides for everything, just follow the beginners guide and google "arch wiki, x' where x is what you want to set up (mediawiki's search bar is terrible)

---

### Post by happysmileman on 2009-04-05
Thanks so far, I'm not too worried about setting it up, mainly just hoping I don't have to install NVidia driver manually (can be quite annoying since every time kernel or Xorg gets updated I can't login until I reinstall).

I was thinking of just installing Arch over Chakra anyway unless there's a huge reason not to, an extra while to set up at first but then I have the advantage of knowing exactly what's on system, rather than inadvertantly installing whatever slipped onto LiveCD.

And thankfully I don't use Wireless on the PC :P

---

### Post by happysmileman on 2009-04-05
On download page there's "FTP ISOs", "Core ISOs" and "ISOLINUX ISOs"...

Never mind, Core is with base packages, installed through CD.
FTP is no packages, downloads latest version of everything, so more up to date, but can be a lot slower depending on d/l speed.

No idea about ISOLINUX but I'm sure I don't want it

---

### Post by Mehall on 2009-04-05
I honestly have no idea which ISO you probably want..

but, you may wanna see this:

[http://wiki.archlinux.org/index.php/KDEmod#How_to_get_decent_performance_on_KDE_4_using_a_NVIDIA_graphics_card](http://wiki.archlinux.org/index.php/KDEmod#How_to_get_decent_performance_on_KDE_4_using_a_NVIDIA_graphics_card)

---

### Post by Skripka on 2009-04-05
I too highly encourage installing Arch+KDEmod rather than the Chakra shortcut.  You end up with the same thing....but the Arch install teaches you the most critical things you need to know and understand about building/maintaining/fixing Arch.

The install really isn't that bad the Wiki is long-but most of the length is due to explaining rather than lots of steps.  If you can cook Mac&Cheese reading instructions off the box, you can probably succeed following the Arch install.

KDEmod4 and straight KDE off the Arch repos aren't that different nowadays really.... it was originally a much more modular system than straight KDE-now the two are converging somewhat.


The only times you notice KDEmod with Arch being different from Kubuntu, for someone not paying attention to speed or more plasmoids available--is in the terminal commands and the different default Kickoff button logo.

---

### Post by happysmileman on 2009-04-05
> **Mehall said:**
> I honestly have no idea which ISO you probably want..

but, you may wanna see this:

[http://wiki.archlinux.org/index.php/KDEmod#How_to_get_decent_performance_on_KDE_4_using_a_NVIDIA_graphics_card](http://wiki.archlinux.org/index.php/KDEmod#How_to_get_decent_performance_on_KDE_4_using_a_NVIDIA_graphics_card)

Ah thanks, on wiki now but it seems to be hard to find some stuff

---

### Post by Skripka on 2009-04-05
> **happysmileman said:**
> On download page there's "FTP ISOs", "Core ISOs" and "ISOLINUX ISOs"...

Never mind, Core is with base packages, installed through CD.
FTP is no packages, downloads latest version of everything, so more up to date, but can be a lot slower depending on d/l speed.

No idea about ISOLINUX but I'm sure I don't want it

You'll be wanting CORE. the FTP ISO only has what is necessary for your computer to boot up the CD-set the config files, and then download ALL the rest of the necessary CORE packages off the internet.  Whereas the CORE ISO won't need any extra downloading-apart from whatever post install customizations you build on.

Step one of the Beginner Wiki (see my sig for linky):

Step 1: Obtain the latest Installation media
You can obtain Arch's official installation media from here. The latest version is 2009.02
You can obtain Tobias Powalowski's 2008.12 archboot media from here.
Both the Core installer and the FTP/HTTP-downloads provide only the necessary packages to create an Arch Linux base system. Note that the Base System does not include a GUI. It is mainly comprised of the GNU toolchain, (compiler, assembler, linker, libraries, shell, and a few useful utilities) the Linux kernel, and a few extra libraries and modules.
The isolinux images are provided for people who experience trouble using the grub version. There are no other differences.

---

### Post by happysmileman on 2009-04-05
> **Skripka said:**
> I too highly encourage installing Arch+KDEmod rather than the Chakra shortcut.  You end up with the same thing....but the Arch install teaches you the most critical things you need to know and understand about building/maintaining/fixing Arch.

The install really isn't that bad the Wiki is long-but most of the length is due to explaining rather than lots of steps.  If you can cook Mac&Cheese reading instructions off the box, you can probably succeed following the Arch install.

KDEmod4 and straight KDE off the Arch repos aren't that different nowadays really.... it was originally a much more modular system than straight KDE-now the two are converging somewhat.


The only times you notice KDEmod with Arch being different from Kubuntu, for someone not paying attention to speed or more plasmoids available--is in the terminal commands and the different default Kickoff button logo.

Ah thanks, I was kinda assuming they were very similar, based on screenshots and stuff, I've also heard it's a lot faster and uses less RAM than Kubuntu, but not sure if that's true of just fanboyism

---

### Post by Mehall on 2009-04-05
> **happysmileman said:**
> Ah thanks, I was kinda assuming they were very similar, based on screenshots and stuff, I've also heard it's a lot faster and uses less RAM than Kubuntu, but not sure if that's true of just fanboyism

It probably uses less RAM, the KDE3 version certainly does, and is still a very nice system (the only version of KDE3.x I would use anymore tbh.)

As stated, at least currently KDEMod 4 is mostly stock KDE.

Kubuntu, on the other hand, is partly stock KDe, partly Canonical fsckin abotu with it, and much though I like KDE, I dislike Kubuntu for how badly implemented it is, imo.

I tend to use OpenSUSE or Mandriva for KDE4 OOTB Gui's, though i would probably say KDE Mod is a good idea.

---

### Post by happysmileman on 2009-04-05
> **Skripka said:**
> You'll be wanting CORE. the FTP ISO only has what is necessary for your computer to boot up the CD-set the config files, and then download ALL the rest of the necessary CORE packages off the internet.  Whereas the CORE ISO won't need any extra downloading-apart from whatever post install customizations you build on.

But I'd have to update much of the stuff on the Core ISO after installing, which would effectively mean I'm downloading it twice?

---

### Post by Mehall on 2009-04-05
> **happysmileman said:**
> But I'd have to update much of the stuff on the Core ISO after installing, which would effectively mean I'm downloading it twice?

That all depends....

There is an argument for either method, but if you don't mind choking your connection while installing via FTP rather than having a system setting itself up and then having updates done later.


I would maybe go for the FTP route.

I do net-installs for Debian already though

---

### Post by Skripka on 2009-04-05
> **happysmileman said:**
> But I'd have to update much of the stuff on the Core ISO after installing, which would effectively mean I'm downloading it twice?

True, but Core give you instant gratification-it tells you whether or not you b0rked a config file on install, and you can just reinstall to save yourself some headache....or if you can sit and watch your computer redownload everything after rerunning the FTP installer....NOT that I am speaking from experience WHATSOEVER. ;)


But yes, before running pacman -S ______, it is always wise to run pacman -Syu

---

### Post by SuperSonic4 on 2009-04-05
> **happysmileman said:**
> Hey guys, Kubuntu 8.10 user here, and considering moving to Arch instead of 9.04 when it comes out, I've heard excellent things about KDEmod, and would like rolling releases. A few questions though.

Firstly, what exactly IS kdemod?
I've heard vague explanations of it, generally just that it's slightly tweaked KDE built just for Arch, but what does that mean? Is it very different, or just with some different default settings and a different theme.
Do they actually modify KDE source? And if so, how much is changed?

KDEmod was originally meant to be a more modular setup of kde to fit in with the KISS which is the main principle. I've never used vanilla KDE so I couldn't tell you the difference.

> 
Secondly, how easy is it to set up/use?
I'm not so worried about how easy it is to set up, though I'd like if I could get up to date NVidia drivers for a fairly old card through package manager :P.
I'm more thinking of day to day usage, installing packages and stuff, getting Wine to work. My brother would be using it as well so I wouldn't want to make him use anything uber-hard or annoying to get used to (Though he uses Kubuntu day-to-day so I doubt it'd be a huge problem)

Shaman > Adept + KPackagekit combined, pacman is an excellent package manager - better than apt.

```
pacman -S nvidia
``` is all there is to it if you have a relatively common nvidia card. ```
pacman -Ss nvidia
``` will search for packages containing nvidia in the name. The [AUR]("http://aur.archlinux.org/") is excellent, removes almost all need to compile from source. Get [yaourt]("http://wiki.archlinux.org/index.php/Yaourt") for example and you can use that to install packages. I'd suggest removing KOffice 2 and adding OpenOffice.org 3 in. Adding packages is just ```
pacman -S <package>
``` although you can use sudo to avoid logging in as root all the time

[http://wiki.archlinux.org/index.php/Pacman](http://wiki.archlinux.org/index.php/Pacman) is a good view (I downloaded all my packages and burnt them to cd so I can use it to reinstall quickly)

If you pick arch 64bit you can use the repos to get the flashplugin too.

> Thirdly, should I go with Arch or Chakra?
I've heard good things about Chakra, which is basically a LiveCD of Arch plus KDEmod and a GUI installer, but haven't really found much real details of it. I mainly want to know is it actually an improvement on Arch or just vanilla Arch with a much quicker and less hassle install.

Go with Arch and add KDEmod. It will give you a better understanding, a more customised system and problem solving skills. Plus the latest version of arch has ext4 support. I have found [wicd]("http://wiki.archlinux.org/index.php/Wicd") to be an excellent wireless management tool. Chakra had a problem with their 64bit cd image too so they aren't doing 64bit yet.


> EDIT: Oh and how long does it take for packages to be made available? I like to be able to get updates of my software as soon as they're available, especially stuff like KDE packages and Amarok.

They're pretty quick about it. No faster or slower than most distros. Also arch has amarok 1.4.10 in the repos as *amarok-base* if you're interested ^.^

---

### Post by Skripka on 2009-04-05
> **SuperSonic4 said:**
> 
They're pretty quick about it. No faster or slower than most distros. Also arch has amarok 1.4.10 in the repos as *amarok-base* if you're interested ^.^

As I recall, Arch had KDE4.2 before KDE even announced the official release :lolflag:

---

### Post by happysmileman on 2009-04-05
> **Skripka said:**
> As I recall, Arch had KDE4.2 before KDE even announced the official release :lolflag:

Actually I do remember seeing that when reading the announcement :P.

Anyway thanks for your answers guys, I'm downloading now, might install tomorrow or next day. (It's 4:04 now, and my will to stay up installing a distro cannot be found)

---

### Post by Skripka on 2009-04-05
> **happysmileman said:**
> Actually I do remember seeing that when reading the announcement :P.

Anyway thanks for your answers guys, I'm downloading now, might install tomorrow or next day. (It's 4:04 now, and my will to stay up installing a distro cannot be found)

You need your mind alert for the Arch install, I tried a 11PM Arch install once-and that was a disaster that led to my not liking the FTP ISO.

..unlike a *buntu install you can't just click off the install preferences click "install" and then drink a cup of coffee and wait for a restart.

---

### Post by Mehall on 2009-04-05
> **Skripka said:**
> You need your mind alert for the Arch install, I tried a 11PM Arch install once-and that was a disaster that led to my not liking the FTP ISO.

..unlike a *buntu install you can't just click off the install preferences click "install" and then drink a cup of coffee and wait for a restart.

In fairness, if you have weirdly standard hardware that works perfectly after the autodetector and live in the US with a standard US qwerty layout, you're mostly safe once you've partitioned.

---

### Post by Skripka on 2009-04-05
> **Mehall said:**
> In fairness, if you have weirdly standard hardware that works perfectly after the autodetector and live in the US with a standard US qwerty layout, you're mostly safe once you've partitioned.

So long as you don't use Ext4, or remember to add HAL to the daemons array, or don't add your DE to the daemons array before testing X---preferably all of the above...The few hard-reboots I needed to finally sort all that out corrupted/fragmented enough of my sys that I just wiped and reinstalled while away at work....I was not a happy camper.

---

### Post by Mehall on 2009-04-05
> **Skripka said:**
> So long as you don't use Ext4, or remember to add HAL to the daemons array, or don't add your DE to the daemons array before testing X---preferably all of the above...The few hard-reboots I needed to finally sort all that out corrupted/fragmented enough of my sys that I just wiped and reinstalled while away at work....I was not a happy camper.

Ahh, see, my Arch setup has no GUI.

I was referring purely to the base system with what  said ;)

And yeah, ext4 would skew that.

---

### Post by chucky chuckaluck on 2009-04-05
> **Skripka said:**
> You need your mind alert for the Arch install,

i have to disagree. i was pretty drunk for my first installation. (though, maybe i'm more alert when i'm drunk. that would be sad.)

---

### Post by Mehall on 2009-04-05
> **chucky chuckaluck said:**
> i have to disagree. i was pretty drunk for my first installation. (though, maybe i'm more alert when i'm drunk. that would be sad.)

[img]http://imgs.xkcd.com/comics/flow_charts.png[/img]

(title/alt text: At 8 drinks, you switch the torrent from FreeBSD to Microsoft Bob.  C'mon, it'll be fun! )

---

### Post by inobe on 2009-04-05
i grabbed the iso and will learn via virtualbox :lol:


edit: okay' it's text base, no problem

---

### Post by smartboyathome on 2009-04-05
> **inobe said:**
> i grabbed the iso and will learn via virtualbox :lol:

I suggest not. Virtualbox doesn't play well with Arch for some reason, especially with the guest additions. Not being able to go on the net basically makes testing it useless. :(

---

### Post by kk0sse54 on 2009-04-05
> **smartboyathome said:**
> I suggest not. Virtualbox doesn't play well with Arch for some reason, especially with the guest additions. Not being able to go on the net basically makes testing it useless. :(

bleh, virtualbox doesn't play well with a lot of things...

---

### Post by inobe on 2009-04-06
it seems vbox is in fact the wrong way to try this or i am doing something terribly wrong with the configuration.

back to the documentation...


btw something about rolling release scares the heck out of me, almost like zombies......

---

### Post by dspari1 on 2009-04-06
> **happysmileman said:**
> Thanks so far, I'm not too worried about setting it up, mainly just hoping I don't have to install NVidia driver manually (can be quite annoying since every time kernel or Xorg gets updated I can't login until I reinstall).

I was thinking of just installing Arch over Chakra anyway unless there's a huge reason not to, an extra while to set up at first but then I have the advantage of knowing exactly what's on system, rather than inadvertantly installing whatever slipped onto LiveCD.

And thankfully I don't use Wireless on the PC :P

There isn't much that you can fit on a 700mb cd. I found the Charkra install to be very essential with very little bloatware. 

Arch has a great thing going for itself (Yay for rolling releases!), but it is not ready for users like me who prefers a more complete repository. I'm sure that this issue will disappear as this distro become more popular, but it's not there yet.

Gentoo (which also has rolling releases) on the other hand has a repository that is just as good as Ubuntu's repositories. I personally don't have the patience to install Gentoo, so I went with Sabayon instead, and it meets my needs perfectly (it's 100% Gentoo compatible). 

My only complaint is that the Live DVD has too much junk selected by default, and you're going to have to unselect them during the install or after the install, but the pros of having access to Gentoo's repositories definitely outweighs the cons.
 
I hope this helps.

---

### Post by binbash on 2009-04-06
Chakra is a good way to install arch linux, i have tried that and it is ok

---

### Post by Luffield on 2009-04-06
> **smartboyathome said:**
> I suggest not. Virtualbox doesn't play well with Arch for some reason, especially with the guest additions. Not being able to go on the net basically makes testing it useless. :(
Arch works fine in Virtualbox on my machine, both with a Ubuntu host and a Windows XP host. IIRC I installed guest additions from the Virtualbox disk image and not from the Arch repositories.

---

### Post by anaconda on 2009-04-06
Arch was a real pain to install!

The problem I had was that it didn't come with wvdial.. or anything else that I could use to connect to the internet (with my 3G dongle) and download updates/programs...

Eventually i got internet access, but then it didn't find a nameserver. (with ubuntu it gets nameserver automagically)

But as I said I got it working and learned a lot.

---

### Post by Eisenwinter on 2009-04-06
My first Arch installation went very smoothly, and I was set up within an hour and a half (and that's only because of my rather slow connection - 30kb/s average).

I experienced some trouble with GRUB a few days ago when migrating to Ext4, but sorted it out, and it runs like a charm.

Arch isn't hard to install, as long as you have some experience, and are comfortable with the command line.

---

### Post by SomeGuyDude on 2009-04-06
A few things:

1) Unless you don't have an ethernet cable, the FTP install is preferable because otherwise you'll end up doing a huge update halfway through anyway (it's one of the steps in the Beginners Guide).

2) Chakra is for convenience, not to supplant the Arch installation. If you don't do a full install at least once you'll be kinda flying blind in there. A big part of Arch is "knowing Arch".

3) KDEMod -used- to be a massively modified KDE (as in "KDE modified"), which is still the case in KDEMod 3.5. As of KDE4, though, it's the exact same as vanilla KDE but you have the option of what elements to install (as in "KDE modular"). I'm not big on KDE, but as far as KDE goes it's very nice.

4) If you usin' wireless, one word: wicd. If you install wicd, it'll do all the work for you. You can seriously ignore the entire wireless guide save making sure you install the right driver, wicd will configure everything for you. I couldn't get my wireless on Arch ever until I had the good fortune of having a dormmate who used it, and he told me about wicd.

---

### Post by mips on 2009-04-06
> **Skripka said:**
> I too highly encourage installing Arch+KDEmod rather than the Chakra shortcut.  You end up with the same thing....but the Arch install teaches you the most critical things you need to know and understand about building/maintaining/fixing Arch.

The install really isn't that bad the Wiki is long-but most of the length is due to explaining rather than lots of steps.  If you can cook Mac&Cheese reading instructions off the box, you can probably succeed following the Arch install.

KDEmod4 and straight KDE off the Arch repos aren't that different nowadays really.... it was originally a much more modular system than straight KDE-now the two are converging somewhat.


The only times you notice KDEmod with Arch being different from Kubuntu, for someone not paying attention to speed or more plasmoids available--is in the terminal commands and the different default Kickoff button logo.


> **happysmileman said:**
> Ah thanks, I was kinda assuming they were very similar, based on screenshots and stuff, I've also heard it's a lot faster and uses less RAM than Kubuntu, but not sure if that's true of just fanboyism


I sense some confusion here, people tend to think the 'mod' stands for 'modified' but it actaully means 'modular'.

Lets try and clarify,
[http://ubuntuforums.org/showpost.php?p=6116347&postcount=13](http://ubuntuforums.org/showpost.php?p=6116347&postcount=13)
> kdemod is VERY modular. They took KDE and split it up into small components. So instead of installing a meta package you can choose to only install parts of the meta package in kdemod.

Example, normal KDE4 has a meta package called **kdegraphics** which installs several packages whether you like it or not.

KDEmod4 on the other hand splits the **kdegraphics** package up into it's individual components as listed below:

kdemod-core/kdemod-kdegraphics-common 4.1.1-1
kdemod-core/kdemod-kdegraphics-doc 4.1.1-1
kdemod-core/kdemod-kdegraphics-gwenview 4.1.1-1
kdemod-core/kdemod-kdegraphics-kamera 4.1.1-1
kdemod-core/kdemod-kdegraphics-kcolorchooser 4.1.1-1
kdemod-core/kdemod-kdegraphics-kolourpaint 4.1.1-1
kdemod-core/kdemod-kdegraphics-kruler 4.1.1-1
kdemod-core/kdemod-kdegraphics-ksnapshot 4.1.1-1
kdemod-core/kdemod-kdegraphics-okular 4.1.1-1

This allows you to only select the actual kdegraphics packages you want instead of installing all of them in normal KDE.

This is the **MAIN** difference.

The other slight difference is they applied about 3 patches to kdemod and these are purely cosmetic and it's basically to identify it as kdemod instead of kde.

The old kdemod3.5 had plenty of patches applied (besides being modular) but they are not going down that road again[COLOR=Red] with KDEmod4 which they are keeping vanilla which is in line with Arch philosphy. 
[/COLOR] 
*Recently they backported a few features from 4.2 to 4.1 that provides more functionality, there were'nt many though.* [COLOR=Red]EDIT: No longer applicable[/COLOR]

Hope this makes sense.

Red text are my current edits of my origal quotes.

---

