---
title: "Ubuntu's a big place ..."
date: 2010-03-15
forum: Ubuntu Studio
---

### Post by wizarddrummer on 2010-03-15
I just read the statement that is the title of this post  in "**How To Help Ubuntu Studio**"

I just did a complete install of Ubuntu Studio. I selected everything when asked which options I wanted to install.

The image I used:
ubuntustudio-9.10-alternate-i386.iso

I have to say very well done. Nice looking interface.

I found some discrepancies, simple errors in documentation, that someone might want to know about.

Being new here in this community, I don't know where I should direct this.

I compared the PackageList here [https://wiki.ubuntu.com/UbuntuStudio/PackageList](https://wiki.ubuntu.com/UbuntuStudio/PackageList) to what was actually installed on my machine.

Thought someone in the dev community would want to know so they can either add it to what is installed or take it off the PackageList web page..

Basic infrastructure
    (MISSING) * alsa-tools - Console based ALSA utilities for specific hardware

Synthesizers
     (MISSING) * swami - SoundFont editor 
Sequencing
    (MISSING) * rosegarden - music editor and MIDI/audio sequencer
    [COLOR=Red]Rosegarden was an item that I really hoped would be installed and functional
    because I  never got it to work in the other distros: Ubuntu 9.10 and Mint.[/COLOR]
    (MISSING) * shaketracker - MIDI sequencer with tracker GUI 

Effects and signal processing
    (MISSING) * tapiir - A tool for real time audio delay and feedback effects

ubuntustudio-audio-plugins
    (MISSING) # fil-plugins - Parametric equalizer LADSPA plugin.
    (MISSING) # vcf - Audio EQ biquad filter LADSPA plugins.

Video:
    (MISSING) # openmovieeditor - Video editor
Not on Package list
xjadeo - xjadeo is a simple video player that receives sync from jackd or MTC.

ubuntustudio-graphics
    (MISSING) # gimp-data-extras - This package contains extra brushes, 
    (MISSING) # gimp-gnomevfs - This package includes a plugin for GIMP which 
    (MISSING) # gimp-ufraw - A plug-in to import RAW images.
    (MISSING) # gimp-plugin-registry - A collection of GIMP plugins.
    (MISSING) # gnome-raw-thumbnailer - a thumbnailer for GNOME that will 
    (MISSING) # synfigstudio - A vector 2D based animation package (GUI)
    (MISSING) # nautilus-image-converter - nautilus extension to mass resize images

---

### Post by AutoStatic on 2010-03-16
> **wizarddrummer said:**
> I compared the PackageList here [https://wiki.ubuntu.com/UbuntuStudio/PackageList](https://wiki.ubuntu.com/UbuntuStudio/PackageList) to what was actually installed on my machine.Hello wizarddrummer, the PackageList in the Wiki has been updated for the last time on 03-03-2009. This is way before the release of Ubuntu Studio 9.10 (which was released in october 2009). That's where the discrepancies arise from probably.

> **wizarddrummer said:**
> Thought someone in the dev community would want to know so they can either add it to what is installed or take it off the PackageList web page..It's a Wiki page so feel free to modify it yourself.

Also, the devs don't come around here very often. Better is to check if a [bugreport]("https://bugs.launchpad.net/ubuntustudio/+bugs?field.searchtext=&search=Search+Bug+Reports&field.scope=project&field.scope.target=ubuntustudio") has already been filed and if not, file a new one yourself.

---

### Post by trulan on 2010-03-16
Regarding Rosegarden,

It had been removed from Ubuntu Studio because it was KDE based.  There is a new version of Rosegarden out, if you want to install it, get it from this ppa:
[https://launchpad.net/~philip5/+archive/extra/+index?start=75&batch=75](https://launchpad.net/~philip5/+archive/extra/+index?start=75&batch=75)

That ppa is a must, IMO, if you are using Ubuntu Studio Karmic - he keeps updated versions of all the key studio apps.

---

### Post by Capoeira on 2010-03-16
"[https://launchpad.net/~philip5/+archive/extra/+index?start=75&batch=75](https://launchpad.net/~philip5/+archive/extra/+index?start=75&batch=75)

That ppa is a must" ²

---

### Post by wizarddrummer on 2010-03-16
> **AutoStatic said:**
> Hello wizarddrummer, the PackageList in the Wiki has been updated for the last time on 03-03-2009. This is way before the release of Ubuntu Studio 9.10 (which was released in october 2009). That's where the discrepancies arise from probably.

It's a Wiki page so feel free to modify it yourself.

Also, the devs don't come around here very often. Better is to check if a [bugreport]("https://bugs.launchpad.net/ubuntustudio/+bugs?field.searchtext=&search=Search+Bug+Reports&field.scope=project&field.scope.target=ubuntustudio") has already been filed and if not, file a new one yourself.

Thanks,
I think i read somewhere in that "how to help" part that these kinds of things (configuration things) were not supposed to be submitted to a "bug report" so I was trying to follow the correct protocol, even though I have no idea in this environment what that is.

---

### Post by wizarddrummer on 2010-03-16
> **trulan said:**
> Regarding Rosegarden,

It had been removed from Ubuntu Studio because it was KDE based.  There is a new version of Rosegarden out, if you want to install it, get it from this ppa:
[https://launchpad.net/~philip5/+archive/extra/+index?start=75&batch=75]("https://launchpad.net/%7Ephilip5/+archive/extra/+index?start=75&batch=75")

That ppa is a must, IMO, if you are using Ubuntu Studio Karmic - he keeps updated versions of all the key studio apps.


Thanks for the reply 
I'm sorry what's a ppa? 

KDE? - that's a different visual desktop  technology correct? And I think I also mean to say a different binary  code for what's being displayed and not compatible with what I am using  is that correct?

---

### Post by AutoStatic on 2010-03-16
> **wizarddrummer said:**
> Thanks,
I think i read somewhere in that "how to help" part that these kinds of things (configuration things) were not supposed to be submitted to a "bug report" so I was trying to follow the correct protocol, even though I have no idea in this environment what that is.A PackageList is more like a request in my opinion. Requests can be done through a bugreport. Besides, a lot of devs don't hang around the forums and don't check the Wiki. It's more likely they will notice a valid bugreport.

A PPA is a Personal Package Archive, a personalised repository to which users can upload stuff and other users can download it again. Kind of like a personal Synaptic (Ubuntu's package manager) website. I've got a [PPA]("https://launchpad.net/~autostatic/+archive/ppa") too that I use to upload packages of applications that are either not available for Ubuntu, of which the ubuntu version contains bugs or that are outdated.

---

### Post by trulan on 2010-03-16
> **wizarddrummer said:**
>  KDE? - that's a different visual desktop  technology correct? And I think I also mean to say a different binary  code for what's being displayed and not compatible with what I am using  is that correct?
Sorry for using acronyms without explaining them.  It wasn't that long ago that I was trying to figure this stuff out, and I'm already forgetting to explain myself.

Autostatic explained what a PPA is.  Basically, you tell Synaptic package manager to look there for updates, in addition to checking Ubuntu's servers.  For example, with Rosegarden, there is a new version out, but to get the latest version from Ubuntu, you would need to wait until a future release, 10.04 or maybe even 10.10.  If you add the ppa (linked in my post above) to your sources list in Synaptic, you can easily install the newest version of Rosegarden, and many other programs.

KDE is another Linux desktop environment - Ubuntu and Ubuntu Studio use Gnome for their desktop.  So a program like the old version of Rosegarden, that depends on KDE, has to load a bunch of extra stuff to make it work.  It's not exactly incompatible, but it's messier and tends to waste system resources.

---

### Post by wizarddrummer on 2010-03-16
> **trulan said:**
> Sorry for using acronyms without explaining them.  It wasn't that long ago that I was trying to figure this stuff out, and I'm already forgetting to explain myself.

Autostatic explained what a PPA is.  Basically, you tell Synaptic package manager to look there for updates, in addition to checking Ubuntu's servers.  For example, with Rosegarden, there is a new version out, but to get the latest version from Ubuntu, you would need to wait until a future release, 10.04 or maybe even 10.10.  If you add the ppa (linked in my post above) to your sources list in Synaptic, you can easily install the newest version of Rosegarden, and many other programs.

KDE is another Linux desktop environment - Ubuntu and Ubuntu Studio use Gnome for their desktop.  So a program like the old version of Rosegarden, that depends on KDE, has to load a bunch of extra stuff to make it work.  It's not exactly incompatible, but it's messier and tends to waste system resources.


Thanks for all of the replies.     

I understand, I think (barely), the concept ..., gosh, I'm sorry that I  can't even phrase the question...  

I'll tell y'all what I understand then you can help me connect the dots.  

Applications,(I've developed a few in my day) consist of many files. The  files can be source code; binary executables, binary libraries, files  for dependencies, text files and on and on.  

Is a ppa a script? that pulls these all these components from a remote  source together onto the local machine and then does what? 

compiles it? 

installs it by placing the files in a directory and providing a link to the main executable? ... 

I'm unclear here.   

Where did you find the ppa for Rosegarden? Their site? Another version  of Linux? 

Are there places that catalog the latest versions of software? Is it  hard to add a ppa to the Synaptic Manager?  

I know too many questions, too little time.

---

### Post by AutoStatic on 2010-03-17
> **wizarddrummer said:**
> Is a ppa a script? that pulls these all these components from a remote  source together onto the local machine and then does what? 

compiles it? 

installs it by placing the files in a directory and providing a link to the main executable? ... A PPA is a personal repository, a website that contains software packages, also referred to as debs (Debian packages, Debian is the Linux distribution of which Ubuntu is derived, more or less).
Those packages contain the exact same things that you mentioned about applications. They're best compared with executable zip files.

> **wizarddrummer said:**
> Where did you find the ppa for Rosegarden? Their site? Another version  of Linux?[http://ubuntuforums.org/showthread.php?t=1350304](http://ubuntuforums.org/showthread.php?t=1350304)

A PPA is a part of the Ubuntu community so if someone adds a PPA with valuable stuff it will most probably end up all over the community, that's exactly what happend with Philip's PPA. Besides that this PPA is very valuable for the community it also helps the maintainer of the PPA. Philip is an official [Ubuntu member]("http://www.ubuntu.com/community/processes/newmember") since a month, partly because of his well maintained and up to date PPA.

> **wizarddrummer said:**
> Are there places that catalog the latest versions of software?In case of Philip's PPA:
[https://launchpad.net/~philip5/+archive/extra](https://launchpad.net/~philip5/+archive/extra)
[http://twitter.com/philip_johnsson](http://twitter.com/philip_johnsson)


> **wizarddrummer said:**
> Is it  hard to add a ppa to the Synaptic Manager? 
- System - Administration - Synaptic Package Manager
- Settings - Repositories
- Other Software - Add
- Enter ```
ppa:philip5/extra
```
- Add Source
- Reload

But it's best to use single packages, in other words, only enable the PPA when you need a specific package and then disable it again. Personally I don't think it's wise to update your system with this PPA enabled.

---

### Post by mango42 on 2010-03-17
> **AutoStatic said:**
> But it's best to use single packages, in other words, only enable the PPA when you need a specific package and then disable it again. Personally I don't think it's wise to update your system with this PPA enabled.

Agreed. FWIW, I have found the easiest approach is to go directly to the PPA and download the .deb file of the specific application you want to try rather than having to remember to reconfigure Synaptic to avoid a flood of updates. ;-)

A+++ and much gratitude to Philip Johnsson!

---

### Post by philip5 on 2010-03-17
> **wizarddrummer said:**
> 
I compared the PackageList here [https://wiki.ubuntu.com/UbuntuStudio/PackageList](https://wiki.ubuntu.com/UbuntuStudio/PackageList) to what was actually installed on my machine.

Thought someone in the dev community would want to know so they can either add it to what is installed or take it off the PackageList web page..

It's true that the list is outdated as many of the applications in that list are rather old and haven't been developed for many years. Some applications in that list haven't been in Ubuntu since Intrepid or older Ubuntu releases.

If any of you guys miss some of that old applications and source code is avalible then just give me a request and I'll try to port it to Karmic and add it to my PPA.

---

