---
title: "Discussion of software that is not included in Ubuntu"
date: 2020-01-08
forum: Ubuntu, Linux and OS Chat
---

### Post by crackers_altitude on 2020-01-08
I’ve found some interesting software (pygears, anaconda, pythonoce, pythonocc, etc.) which is generally not included with Ubuntu. However, I’d be interested to discuss the installation of this software with Ubuntu users - since I’ve tried this on my own, and I seem to have made a mess. This is partly because it seems, though the software is available ( e.g. on github), it is not clear how robust the discussion groups are for this software.

I can see that the software discussion on Ubuntu Forums appears to be limited to, interestingly - wine, but also in general multimedia software, or that which is packaged in Ubuntu in the first place. So, I had to ask - perhaps there are a few users out there who could help me get the software of interest up and running with apt, snap, etc.

thanks for the guidance as usual.

---

### Post by Frogs Hair on 2020-01-08
Not a specific support request moved to UL&OS Chat.

---

### Post by TheFu on 2020-01-08
Every non-packaged software should have an INSTALL or README file which explains how to set it up. How that happens, that depends on the specific project, languages involved, complexity.

Key things for someone new to know.
* installs of non-packaged software require manually maintenance by you, the admin.  That means extra work and it is best to avoid it, if possible by using pretty much any other method. Normal repo, PPA, snap, flatpak, ... anything except source.
* Install software manually to either /usr/local/ or somewhere in your HOME.

There are no limits about software installation discussions here, provided they aren't about hacking tools.  Anything else goes as far as I know.

Just consider the sort of software that you find interesting may not be all that interesting to others.  Happens to me all the time, but you'll never know until you post.  Pick a good title, put the software title at the beginning so it doesn't get cut off, definitely say the release number, and DE being used if it is desktop/GUI software.

Going with source code means that dependency management is a manual process, further complicating the required, manual, maintenance. Doing it wrong can easily make for a mess, as you say.

Using software off source-code sites is beyond typical end-users. Really it is mainly developers who would go that direction, so non-developers aren't likely to join a conversation.

---

### Post by Artim on 2020-01-08
I usually hate PPAs, but I use one to get and maintain the Seamonkey Suite.  It has **thousands fewer lines of code** than Firefox, yet it does what *both* Firefox *and* Thunderbird do!

---

### Post by hk42 on 2020-01-08
Ubuntu being quite popular very often the site of the new program 
has a tutorial on how to install it "over" a ubuntu version.
Sometimes it is a good occasion to update your ubuntu.
or to make a backup of it.
I also find that appimage versions of programs are very handy.

---

### Post by HermanAB on 2020-01-09
As explained above, read the README and INSTALL files.  Check the 'makefile' to see whether it includes BOTH 'install' and 'uninstall' options.  If 'uninstall' is not included, then the software is probably best avoided, since that indicates a cowboy attitude on the part of the project maintainers.  It is also best to experiment in a virtual machine, so that you don't mess up your main system.

---

### Post by hk42 on 2020-01-09
> **Artim said:**
> I usually hate PPAs, but I use one to get and maintain the Seamonkey Suite.  It has **thousands fewer lines of code** than Firefox, yet it does what *both* Firefox *and* Thunderbird do!
Hi
Inspired by your message I tried Seamonkey from their website and all went well 
with just extracting the archive in the /usr/local directory.
[https://www.seamonkey-project.org/doc/install-and-uninstall#install_linux](https://www.seamonkey-project.org/doc/install-and-uninstall#install_linux)
The only problem I had is that when testing I ended in a perfectly working Youtube full screen page
 and could not find any way to get out of it. :D
Had to resort to Ctrl/Halt/Del to log out.
Thanks for the idea anyway.

---

### Post by CatKiller on 2020-01-09
For software whose build instructions end with "make install" **checkinstall** is a useful substitute. It creates a package out of all the files that make wants to install, and then installs that package instead; meaning that can be uninstalled with your normal package manager.

---

### Post by kevdog on 2020-01-09
In my limited experience installing packages either with make install, checkinstall -- the install process works great but the uninstall process usually leaves a lot of packages and files behind.  Honestly its really annoying.  

I'd second the advice of trying the installation within a virtual machine.  VMs are so easy to create and use.

---

### Post by mastablasta on 2020-01-10
so sad that with all options that were made available in the past few years (appimage, flatpack, snap, portable binaries) and some older ones that are not distro agnostic (PPA, repositories) we still have stuff that comes in source only.

---

### Post by ewog on 2020-03-19
mastablasta:
Read the easy to understand, lots of pics [Ubuntu manual]("http://ubuntu-manual.org/"). 
[Do i need antivirus/firewall in linux?]("https://wiki.ubuntu.com/BasicSecurity")
Disk backup (works on newer PC): [URL="http://clonezilla.org/"]Clonezilla
[/URL]User friendly full disk backup Redobackup is now back as [URL="https://github.com/rescuezilla/rescuezilla"]Rescuezillabu

[/URL]
It looks like Rescuezilla is compatible to Ubuntu 18.04, but not yet with 19.10.   Are there any full-disk backup programs compatible with 19.10?

---

### Post by mastablasta on 2020-03-20
> **ewog said:**
> [URL="https://github.com/rescuezilla/rescuezilla"]
[/URL]
It looks like Rescuezilla is compatible to Ubuntu 18.04, but not yet with 19.10.   Are there any full-disk backup programs compatible with 19.10?

rescuezilla uses 18.04 to run (in the background), but it will be able to backup 19.10 non the less.

the old redobacup used 12.04 i believe. in any case it can backup new distributions fine. the issue is that because the base OS was old it used old kernel and linux has drivers in kernel. so while it would work well with older hardware, it had issues with new mothebroards, CPUs (AMD Ryzen didn't exist in 2012 for example), win10 and secure boot setups etc. by using 18.04 as base it will work with new PC just as well.

btw 18.04.4 has same kernel now as 19.10. 

if you look at clonezilla this is the same. so old version can backup new distro version, but they can't run (or have issues) on new PC. clonezilla has a version based on debian testing to offer support for the really new hardware. but for general user i think the option to go with Ubuntu LTS as base i s better. well at least for me, but i have old hardware mostly.

---

### Post by oldrocker99 on 2020-04-07
I moved from Ubuntu, after twelve years, to Manjaro for the huge software availability. I got sick of PPAs, and compiling the apps which disappeared long ago from the Ubuntu repos, which frequently led me into Dependency Hell. By that, I mean having to compile dependencies themselves, which often had [/b]their own[/b] dependencies. Some programs I tried to compile failed completely because of the forum.

Manjaro, which is as easy to install and user-friendly as Ubuntu, and has a forum which is as friendly as the Ubuntu Forums, who set the bar for how an OS forum should be.

It is as suitable for complete n00bz as for old hands, and the apps I used to laboriously compile are in the AUR, and compile automatically. This was HUGE the first time I saw it. Compiling Aqualung, my must-have music player, which left the Ubuntu repos in 2014, took me 2 hours to compile the first time. I got better at it, but it still took >30 minutes. I installed it in Manjaro, and it downloaded every dependency first and compiled and installed in <5 minutes. It has been something like falling in love with Linux all over again. 

Ubuntu's slogan was "Linux for Human Beings."

Manjaro is "Arch for Human Beings," in exactly the same way. Like Ubuntu, you choose your desktop version and go. 

At least give it a shot. Try it in a VM. You just might like what you see.

---

### Post by Perfect Storm on 2020-04-07
Heh, been arch user back in the days, even made a few game packages to the community. Arch is fun :)
But now on eos and my days to test distros is gone. Now I'm focusing getting work done on the computer(s).

---

### Post by Artim on 2020-04-07
The Ubuntu family is for those who us who prefer to run *applications* rather than the OS.

---

