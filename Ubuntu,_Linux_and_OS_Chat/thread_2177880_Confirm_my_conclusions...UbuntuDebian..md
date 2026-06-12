---
title: "Confirm my conclusions...Ubuntu/Debian."
date: 2013-09-30
forum: Ubuntu, Linux and OS Chat
---

### Post by Andrew_Lucas on 2013-09-30
Hi all!

So, I've been doing some reading, mainly because I'm thinking about going on another distro-hopping spree. My situation at the moment is that I run Linux for all my personal computing needs, but also manage my family's computers (when I'm home). After seeing the ageing hardware go further and further downhill with Windoze, I moved them to Linux too - and they've taken to it well. However, since I'm not home (and in any case, do not have the patience) to be constantly fixing broken packages, updating the systems (there are 3 PCs at home) and generally doing my best to avoid all the nightmares children under 15 create on computers, Ubuntu's 6 month release cycle is too much. Even as things were, with an LTS installed, it was too much effort. I switched them to Debian (stable) - time will tell if this was a good or bad move.

It did however get me thinking! Should I move myself? One of my aims with my personal computing is ensuring my hardware, my OS, my programs - everything - fits like a glove. I also (and yes, I know, it sounds slightly OCD-ish) hate "clutter" - untidy folders, unused programs taking up space and time to download/install updates, potentially even wasting clock cycles running in the background. Debian seemed to intuitively scream "MINIMAL!" - since even Ubuntu "minimal" is based on Debian. I started thinking about checking this out a little further, and I looked up some of the "differences" between Debian and Ubuntu. My list of findings is as follows:

- Debian generally comes with root enabled. However, as I discovered, opting for the "expert" install allows you to chose to use sudo or not - personally, I prefer the use of sudo for day to day activities, but like the ability to "su root", if I know I'm going to be doing something a little more extensive in the terminal. Either way - this can be discounted as a pro/con for neither Ubuntu/Debian, since both allow root to be enabled/disabled.

- aptitude vs apt-get. I've got comfortable using apt-get, and so far, even when instructed in an online tutorial to use aptitude, I've used apt-get without problem. Can someone confirm there is no difference in the package management functionality (i.e. I know there *is *a difference in package search functionality) between the two?

- Free vs non-free software. Where possible, I think it's important to use and support FOSS. However, lots of my friends use Skype to chat, and so I'm cornered into using it to. Gnash does not provide like-for-like functionality with Flash (last I heard) and neither does IcedTea/OpenJDK do the same for Oracle Java. On the laptop I use currently, networking hardware seems to work marginally better with proprietary drivers - as do graphics cards I've had in the past. The list goes on - media, fonts, particular games. Although I know Debian has a more conservative approach than Ubuntu to FOSS, I know in either case that it is possible to install proprietary software, and support for doing this is available - so as with the first point, it can't really be marked up as a pro or con.

- Stability vs latest and greatest. I know this is a bit of an issue, but in any case, with my Debian install I'd be moving to jessie (testing) or sid (unstable). Since Ubuntu takes many of its packages from upstream anyway, I don't think it's fair to say that it can be a pro for Ubuntu. If anything, usage of sid would put me *ahead* of the Ubuntu-curve, so this could count as a pro to Debian?

That more or less shows all of my findings! Is there anything (perhaps at the level of the kernel?) that Debian/Ubuntu tweak, which give either an edge? I know I'm perhaps biasing the outcome by asking this on an Ubuntu forum, so please, objectivity is important folks!

---

### Post by monkeybrain20122 on 2013-09-30
> **Andrew_Lucas said:**
> Hi all!

- aptitude vs apt-get. I've got comfortable using apt-get, and so far, even when instructed in an online tutorial to use aptitude, I've used apt-get without problem. Can someone confirm there is no difference in the package management functionality (i.e. I know there *is *a difference in package search functionality) between the two? 

You can use either in Debian or Ubuntu. Don't see what the problem is.
> 
 Free vs non-free software. Where possible, I think it's important to use and support FOSS. However, lots of my friends use Skype to chat, and so I'm cornered into using it to. Gnash does not provide like-for-like functionality with Flash (last I heard) and neither does IcedTea/OpenJDK do the same for Oracle Java. On the laptop I use currently, networking hardware seems to work marginally better with proprietary drivers - as do graphics cards I've had in the past. The list goes on - media, fonts, particular games. Although I know Debian has a more conservative approach than Ubuntu to FOSS, I know in either case that it is possible to install proprietary software, and support for doing this is available - so as with the first point, it can't really be marked up as a pro or con.

You can install Skyp in Debian (the .deb works), For flash and all multimedia codecs, libdvdcss2 etc just add the Debian multimedia repo. [http://www.deb-multimedia.org/](http://www.deb-multimedia.org/) No one should have to suffer gnash, it is a complete waste of time.

Hardware support may be poorer in Debian, because some module may not be activated in the kernel, some firmware may not be installed etc. It was a pain to get my wifi working whereas the card works out of the box with Ubuntu and Fedora.
> 
Stability vs latest and greatest. I know this is a bit of an issue, but in any case, with my Debian install I'd be moving to jessie (testing) or sid (unstable). Since Ubuntu takes many of its packages from upstream anyway, I don't think it's fair to say that it can be a pro for Ubuntu. If anything, usage of sid would put me *ahead* of the Ubuntu-curve, so this could count as a pro to Debian?


I think that is a myth, Debian is "stable" only because its stable release is very old. Sid is a bloody mess comparing to Ubuntu. You actually have to check "Debian weather" before you go ahead to update everytime because if Debian weather is bad then updating may cause troubles. I have encountered numerous broken packages and dependency issues with Debian sid. While Ubuntu is based on Debian sid or testing but it has smoothed out many packaging bugs. Debian sid is apparently aimed for testers. I found that I can get both stability and the latest and greatest with Ubuntu + ppa (or Fedora but with less packages) In Debian you get neither. Sid is no way the greatest and latest comparing to what you get from ppa, or, Fedora through normal updates,--or ArchLinux,--, it is the latest only for people used to the snail pace of updating in Debian stable or testing.

---

### Post by ian-weisser on 2013-09-30
> **Andrew_Lucas said:**
> However, since I'm not home (and in any case, do not have the patience) to be constantly fixing broken packages, updating the systems (there are 3 PCs at home) and generally doing my best to avoid all the nightmares children under 15 create on computers, Ubuntu's 6 month release cycle is too much. Even as things were, with an LTS installed, it was too much effort.
[...]
- Stability vs latest and greatest. I know this is a bit of an issue, but in any case, with my Debian install I'd be moving to jessie (testing) or sid (unstable). Since Ubuntu takes many of its packages from upstream anyway, I don't think it's fair to say that it can be a pro for Ubuntu. If anything, usage of sid would put me *ahead* of the Ubuntu-curve, so this could count as a pro to Debian?

These seem conflicting goals. If you want each user's machine to match their needs, then LTS vs. bleeding-edge should also match their needs.
If maintaining and upgrading many machines is too onerous, then the choice is obvious.

---

### Post by malspa on 2013-09-30
I feel that keeping *both* installed (for the most part, I stick with Debian Stable and Ubuntu LTS) gives me a more useful set-up. I have no reason to get rid of either one.

---

### Post by buzzingrobot on 2013-10-01
I'd read up on how to lock down your kids' machines, and them. ;)  Seriously, research how Unix/Linux can restrict and control the access and rights of any user.

For your needs, only you can tell. Follow your interests of the moment and see where they take you. 

On stability:  It's been a long time since I've installed a desktop Linux distribution that was so flaky I couldn't use it.  Applications that throw bugs will typically throw the same bugs on any distribution.  

Also, some distributions ship with bug alert tools, like Apport, turned on, some ship with them turned off.  Just because a little box doesn't pop up doesn't mean a bug didn't manifest itself. 

I suspect the distributions based on Red Hat Enterprise Linux 6 (CentOS, Scientific, etc.) are possibly tne most "stable" at the moment.  For all intents and purpose, that code has been frozen for several years except for bug fixes and patches.  On the other hand, its desktop is based on Gnome 2.28 and an old version of GTK2.  (A new RHEL release is expected later this year, based, more or less, on Fedora 19/20 or thereabouts.)

---

### Post by su:bhatta on 2013-10-01
I would like to add that I keep both Debian Stable and latest Ubuntu. Though Debian stable is old itz great for fallback!

---

### Post by stalkingwolf on 2013-10-01
I use Mint 13.  I have 2 hp minis 2 hp5000 series , an emachines 5xxx and a whitebox here.  i maintain remotely usually by phone or text another hp 5000 an acer laptop
a dell d8oo and a compaq nc8000 all runing mint 13. there is also an ibm t42p i installed it on and a toshiba  but they primarily use windows.
The dell and the acer were given to 11yr olds with the edubuntu packages added.  0 problems with either.  One of the hp 5000s is set up for my tv.  I get all my tv and movies from it.

---

### Post by mamamia88 on 2013-10-01
Debian=ubuntu-a few years- few minor things like ppas + different philoshpy on propietary software.  Personally if it was me being forced to manage a computer for a relative I would give them debian stable and set it up to automatically update and provide ssh access for myself in case of a dire emergency and charge them for my time.

---

