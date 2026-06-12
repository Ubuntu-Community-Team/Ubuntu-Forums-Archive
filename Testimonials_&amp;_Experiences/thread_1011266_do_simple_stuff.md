---
title: "do simple stuff"
date: 2008-12-14
forum: Testimonials &amp; Experiences
---

### Post by josvanr on 2008-12-14
I just upgraded to intrepid. Looks very fancy. But doing simple stuff like playing a midi file or a wmv movie is not possible for normal people. (ie without digging into forums and tweeking etc) I'm just getting so fed up with spending hours and hours just to get a simple task done. What use are all the eyecandy animations if my computer can't perform trivial tasks like play a movie?.. Just a thought..

jos van riswick

---

### Post by albinootje on 2008-12-14
I think you should realise that big companies *try* to control the internet and the software in use. 
Luckily that "battle" is not yet lost.

Read some more here :
[https://help.ubuntu.com/community/FreeFormats](https://help.ubuntu.com/community/FreeFormats)

And use Medibuntu :
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Or use these packages :
kubuntu-restricted-extras - Commonly used restricted packages
ubuntu-restricted-extras - Commonly used restricted packages
xubuntu-restricted-extras - Commonly used restricted packages

---

### Post by Tamlynmac on 2008-12-14
I think it's part of a learning curve. Every time I've installed software, it took a period of time to learn and become proficient. Fortunately, this forum provides answers to most all Ubuntu learning experiences.

> not possible for normal people - I must disagree, as those that have successfully installed and implemented Ubuntu have managed to install the required codecs and drivers. That phrase implies people that have learned Ubuntu and/or found the solutions (which are readily available) are not normal! Some may take offense to that statement. I certainly am not a computer wizard or guru and yet am capable of performing these mundane tasks.

The truly amazing part is: should you require assistance, a simple post on this forum will surfice and usually within minutes your issue/howto is resolved. I often wonder, for how many individuals installing Ubuntu - it was the first time they had ever installed an OS. I'm aware that many people buy their systems with the OS pre-installed and never change the OS. I'm not talking an update or upgrade but actually installing a totally new OS form ground zero. I've installed almost all versions of Windows (starting with 3.1) and numerous Linux distros and can say without hesitation that installing Ubuntu is simple (especially when compared to Windows).

Be patient and learn the OS. I would advise a long term Linux user who just installed XP or Vista for the first time, exactly same thing. However, it's been my experience that there aren't many of them around.[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by Twitch6000 on 2008-12-14
> **josvanr said:**
> I just upgraded to intrepid. Looks very fancy. But doing simple stuff like playing a midi file or a wmv movie is not possible for normal people. (ie without digging into forums and tweeking etc) I'm just getting so fed up with spending hours and hours just to get a simple task done. What use are all the eyecandy animations if my computer can't perform trivial tasks like play a movie?.. Just a thought..

jos van riswick

My brother who has only used a computer once or twice at school had no problem with his Linux laptop...

Infact I think he suprised me a bit with how fast he figured it out...

For playing a movie all you have to do is enable the restricted extras :/.(you know you have to do basically the same thing on windows right for certain file types)

---

### Post by xarte on 2008-12-14
I'm certainly finding any issues with Linux FAR less frustrating than Vista. Getting to 'go' with my daughter's new laptop took me a couple of hours. A fresh install of Ubuntu took what - 30 mins if that?

I accidentally hit 'block' on the install of Warcraft on Vista (clumsy with the scratchpad) and do you think I can unblock the dang thing? I'll try uninstall/reinstall then take it in to the computer shop and cry 'help'.

With Ubunutu, I can find really good, readable, useful HOWTOs on the forum and using Google. Errors and problems feel like things that I have a chance of solving, not some mysterious impenetrable monolith of an OS that Vista is. (Though the techs tell me that it is, in fact, a good OS once you're used to it... !)

If you don't want to spend time learning how to use an OS, I recommend you go for a Mac - OSX is fabulous and easy and all the graphics stuff is already build in for you.

As someone mentioned to me on another thread, most people don't install windows, it comes pre loaded. You could always get someone to install the software for you - one of your local computer repair places is sure to have a linux person. If you tell them what you need, they can set it up for you.

---

### Post by linuxguymarshall on 2008-12-14
```
sudo apt-get install vlc ubuntu-restricted-extras
```

---

### Post by solwic on 2008-12-14
> **linuxguymarshall said:**
> ```
sudo apt-get install vlc ubuntu-restricted-extras
```

Always a good idea to add "flashplugin-nonfree" to the end of that line, just to cover internet video, too.  :)

---

### Post by Izek on 2008-12-15
restricted-extras SHOULD include flashplugin-nonfree, last I checked anyway.

---

### Post by Orfintain on 2008-12-15
> **josvanr said:**
> I just upgraded to intrepid. Looks very fancy. But doing simple stuff like playing a midi file or a wmv movie is not possible for normal people. (ie without digging into forums and tweeking etc) I'm just getting so fed up with spending hours and hours just to get a simple task done. What use are all the eyecandy animations if my computer can't perform trivial tasks like play a movie?.. Just a thought..

jos van riswick

Dido

I'm going the the pain of upgrading for second or third time and it always takes a few days to get everything working again, virtualbox OSE, hardware problems, re-enabling repositories, getting settings for new programs (VLC) working. Sound and Video never work right, but we spend days getting 90% and running dvd shrink in wine. It allways takes a few days. I'm a 26 yr old with an engineering degree and it still takes alot of time.

Ubuntu is for computer hobbiest that want to work tword free ideals if you don't fit at least one of those categories. I would suggest a mac. I'm kicking myself maybe mint wouldn't have been so bad.. who knows.

---

### Post by mick222 on 2008-12-15
> I'm going the the pain of upgrading for second or third time and it always takes a few days to get everything working again, virtualbox OSE, hardware problems, re-enabling repositories, getting settings for new programs (VLC) working
    47yr old Bricklayer left school at 17 can install and have running all of the above in less than 1 hr. 
 Follow the how to in the multi media section it takes two lines of code to install and configure sound and video, unlike vista having to search for java flash etc and wait endlessly for the os to install.Not to mention getting all the drivers for hardware.
  Ok virtualbox is a pain but that is not linuxes fault just complex software ,would be the same if you wanted to run it under windows. I think most people who have problems installing gnu-linux have never tried to install windows.

---

### Post by Joeb454 on 2008-12-15
> **jrock612 said:**
> Always a good idea to add "flashplugin-nonfree" to the end of that line, just to cover internet video, too.  :)

> **Izek said:**
> restricted-extras SHOULD include flashplugin-nonfree, last I checked anyway.

It does :D restricted extras is a fantastic package. Though I always ```
sudo apt-get install libxine1-all-plugins
``` As well...I've never had to actually look for a codec to let me play anything with those installed

---

### Post by solwic on 2008-12-15
> **Joeb454 said:**
> It does :D restricted extras is a fantastic package. Though I always ```
sudo apt-get install libxine1-all-plugins
``` As well...I've never had to actually look for a codec to let me play anything with those installed

I stand corrected.  :P  

What it is, I think, is that for so long I never installed the restricted extras.  I just ran a movie and let it tell me it needed codecs; ditto with mp3s.  I installed flash and java through prompts in Firefox when I loaded a site that needed them.

Only lately have I used "ubuntu-restricted-extras", and I guess the two bled together in my mind.  :P

---

### Post by 3rdalbum on 2008-12-15
Midi files: Install Timidity.

Everything else you ever need: Enable the Medibuntu repository, install w32codecs and libdvdcss2, and ubuntu-restricted-extras.

If you're finding this difficult to do, I'd appreciate if you could complain to whoever gave you the hard-to-play video file. People must be taught to use Free Software and patent-free codecs like Ogg Vorbis/Theora and Dirac, which can be played out-of-the-box on Linux and with a simple plugin download on other platforms.

---

### Post by albinootje on 2008-12-15
> **Orfintain said:**
> Dido
I'm going the the pain of upgrading for second or third time and it always takes a few days to get everything working again, virtualbox OSE, hardware problems, re-enabling repositories, getting settings for new programs (VLC) working.

You can install dkms (mentioned on the VirtualBox website afair) to handle kernel upgrades.

Package: dkms
Priority: optional
Section: admin
Installed-Size: 372
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Matt Domsch <Matt_Domsch@dell.com>
Architecture: all
Version: 2.0.20.4-0ubuntu2
Depends: awk, module-init-tools, bash (>> 1.99), linux-image, linux-headers
Recommends: patch, make, gcc, fakeroot
Filename: pool/main/d/dkms/dkms_2.0.20.4-0ubuntu2_all.deb
Size: 55492
MD5sum: b11b3dfa62b4f831e78987636f7ff1a3
SHA1: c989c5a0adf1f63ccd39dfdd7a6a4e0e1e7107df
SHA256: b11b951fb3f79c6e807492a942bbdfbdbf3daf5c236f1e63ec12d74dbaf8c9b8
Description: Dynamic Kernel Module Support Framework
 This package contains the framework for the Dynamic Kernel Module
 Support (DKMS) method for installing and updating kernel modules.
 .
  Homepage:  [http://linux.dell.com/dkms](http://linux.dell.com/dkms)
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by wolfen69 on 2008-12-15
> **mick222 said:**
> 
 Follow the how to in the multi media section it takes two lines of code to install and configure sound and video

that's too much work. you want someone to actually do something for themselves? ;)

---

