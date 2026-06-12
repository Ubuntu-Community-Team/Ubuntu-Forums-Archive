---
title: "Ubuntu studio vs ubuntu?"
date: 2014-10-02
forum: Ubuntu Studio
---

### Post by LK_gandalf_ on 2014-10-02
Hi, I am trying to understand what is the main difference between:
- installing ubuntu, and then manually install the applications for video, or music, that are also in ubuntu studio.
- installing ubuntu studio.

I am asking asking because I am worried that ubuntu studio gets less support than the big brother, so I don't see the reasons why I should try it instead of normal ubuntu + specific apps.
Butmaybe I am wrong and there are other technical reasons, and no worries for support?
Thanks.

---

### Post by jejeman on 2014-10-03
The question has been answered so many times... Use the search.

---

### Post by LK_gandalf_ on 2014-10-03
Thanks. I found something on the kernel, which is low latency, and then basically no difference, only pre-installed packages and different graphic theme. Someone says it's less reliable, but no explanations of this.

However, I haven't found an answer to the question: is ubuntu studio less supported than ubuntu? Is it a different team working on it? Should I expect somehow that studio lies a little bit behind vanilla when it comes to new software, update of the browser, and so on?

P.S: If this a recurring question, and since the website is not very clear, could I then propose the admin to stick the best past answer on the first page?

---

### Post by jejeman on 2014-10-03
Ubuntu studio is Ubuntu.
Look at repositories if you don't believe it.
The rest is just a Ubuntu variant / spin off.
Yes, some other developers are packing Ubuntu Studio ISO, but they pack what they get from Ubuntu developers, or maybe Xubuntu for some parts. So, same ingredients, different meal.

---

### Post by jonesgabriel21 on 2014-10-07
When I tried this flavor out several weeks ago, I was unable to get dual or multi-monitor support to recognize that there were more than 1 monitor. The furthest that I was able to get it was to mirror the main 19" monitor to the others nothing more. I was frustrated with the "Official" live cd, that I just reinstalled with vanilla 14.04 and then just searched for the packages that come with studio, not vanilla.

---

### Post by innominate2 on 2014-10-08
[h=1]Ubuntu Studio vs. Ubuntu[/h] Some  differences are immediately more evident between Ubuntu Studio and  plain, vanilla Ubuntu. These would include a different theme and  background, as well as a different battery of installed applications.  But Ubuntu Studio is more than just Ubuntu with a slicker theme and  extra packages installed. There are several subtle and pervasive  differences. 
 
[h=2]Obvious Differences[/h] **Theme and Artwork**  - Gone is the familiar brown and orange! Remember, we're creative human  beings. Probably the most obvious difference is the new creative theme.  
**Multi-Media Applications** - Ubuntu Studio is chock-full of pre-installed audio, video and graphical applications including JACK, Ardour, GIMP and Kino. 
 
[h=2]Subtle, Powerful Differences[/h] **Real Time Kernel**  - Ubuntu Studio uses the Ingo Molnar PREEMPT patched real-time kernel  (for more information about the real-time kernel, take a look at the [RTWiki FAQ]("http://rt.wiki.kernel.org/index.php/Frequently_Asked_Questions")).  This helps to reduce the amount of [latency]("http://en.wikipedia.org/wiki/Latency_%28audio%29"),  which is extremely beneficial for audio work. The low levels of latency  that can be achieved in Linux with the real-time kernel can also  surpass those available under Windows and Mac. 
**System Configuration**  - The Ubuntu Studio team has already configured the Ubuntu Studio  system to help maximize the real-time kernel.  The user is included in  the *audio group* and the *limits.conf* file is specifically configured. 
**JACK Sound System** - Along with the ubiquitous [Pulse Audio sound server]("https://wiki.ubuntu.com/PulseAudio"), the powerful JACK sound server is also included in Ubuntu Studio. Both are already configured to work well together.

-------
Source:
[https://help.ubuntu.com/community/What%20Is%20Ubuntu%20Studio#Ubuntu%20Studio%20vs.%20Ubuntu](https://help.ubuntu.com/community/What%20Is%20Ubuntu%20Studio#Ubuntu%20Studio%20vs.%20Ubuntu)

---

### Post by CrocoDuck on 2014-10-08
> **innominate2 said:**
> **Ubuntu Studio vs. Ubuntu**

 Some  differences are immediately more evident between Ubuntu Studio and  plain, vanilla Ubuntu. These would include a different theme and  background, as well as a different battery of installed applications.  But Ubuntu Studio is more than just Ubuntu with a slicker theme and  extra packages installed. There are several subtle and pervasive  differences. 
 
**Obvious Differences**

 **Theme and Artwork**  - Gone is the familiar brown and orange! Remember, we're creative human  beings. Probably the most obvious difference is the new creative theme.  
**Multi-Media Applications** - Ubuntu Studio is chock-full of pre-installed audio, video and graphical applications including JACK, Ardour, GIMP and Kino. 
 
**Subtle, Powerful Differences**

 **Real Time Kernel**  - Ubuntu Studio uses the Ingo Molnar PREEMPT patched real-time kernel  (for more information about the real-time kernel, take a look at the [RTWiki FAQ]("http://rt.wiki.kernel.org/index.php/Frequently_Asked_Questions")).  This helps to reduce the amount of [latency]("http://en.wikipedia.org/wiki/Latency_%28audio%29"),  which is extremely beneficial for audio work. The low levels of latency  that can be achieved in Linux with the real-time kernel can also  surpass those available under Windows and Mac. 
**System Configuration**  - The Ubuntu Studio team has already configured the Ubuntu Studio  system to help maximize the real-time kernel.  The user is included in  the *audio group* and the *limits.conf* file is specifically configured. 
**JACK Sound System** - Along with the ubiquitous [Pulse Audio sound server]("https://wiki.ubuntu.com/PulseAudio"), the powerful JACK sound server is also included in Ubuntu Studio. Both are already configured to work well together.

-------
Source:
[https://help.ubuntu.com/community/What%20Is%20Ubuntu%20Studio#Ubuntu%20Studio%20vs.%20Ubuntu](https://help.ubuntu.com/community/What%20Is%20Ubuntu%20Studio#Ubuntu%20Studio%20vs.%20Ubuntu)

[QUOTE=https://help.ubuntu.com/community/What%20Is%20Ubuntu%20Studio#Ubuntu%20Studio%20vs.%20Ubuntu][COLOR=#333333][FONT=Ubuntu]What Is Ubuntu Studio (last edited 2010-05-14 13:54:49 by [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][Vachan]("https://launchpad.net/~Vachan")[/FONT][/COLOR]
[RIGHT][COLOR=#333333][FONT=Ubuntu])[/FONT][/COLOR][/RIGHT]
[/QUOTE]


The info on that page is outdated. Today Ubuntu Studio is quite different. The last one I have installed is the 12.04 version. However, I think that the latest is almost configured in the same way.

The real time kernel is not included in Ubuntu Studio. Instead, you have a lowlatency Kernel, which is a standard one compiled with slightly different parameters in order to make it more efficient with audio. Ubuntu Studio runs XFCE as graphical user interface, which is light so you don't waste system resources just watching eye-candy, reducing the likelihood of xruns and so. All the software that makes UStudio should be avaible in the repositories. If you install a vanilla ubuntu and then you install the lowlatency kernel and the ubuntustudio-meta package then you will have the same stuff you would have installing Ubuntu Studio.

---

### Post by LK_gandalf_ on 2014-10-08
Thanks all for the reply. Then I see that it was indeed not easy to really find a good updated source explaining the deep differences between vanilla and studio.

> **jonesgabriel21 said:**
> When I tried this flavor out several weeks ago, I was unable to get dual or multi-monitor support to recognize that there were more than 1 monitor. The furthest that I was able to get it was to mirror the main 19" monitor to the others nothing more. I was frustrated with the "Official" live cd, that I just reinstalled with vanilla 14.04 and then just searched for the packages that come with studio, not vanilla.

This experience would shows that you get less hardware support, for example, if this issue was only depending on v\installing vanilla vs studio...

---

### Post by CrocoDuck on 2014-10-08
> **jonesgabriel21 said:**
> When I tried this flavor out several weeks ago, I was unable to get dual or multi-monitor support to recognize that there were more than 1 monitor. The furthest that I was able to get it was to mirror the main 19" monitor to the others nothing more. I was frustrated with the "Official" live cd, that I just reinstalled with vanilla 14.04 and then just searched for the packages that come with studio, not vanilla.

For what I remember, UStudio comes with ARandR as a tool for setting up multiple monitors. It always worked for me. Next time check if you have that program installed or try to launch it from the terminal. I don't think that the hardware support is going to be that different, since the core of the system is actually the same. Also, the software for UStudio is packaged for vanilla as well. For sure, if you run a different GUI, the programs you have for configure and tune the system may be different and understanding where to search could be hard at first...

---

### Post by CrocoDuck on 2014-10-09
I found a couple of pages that should be able to support what I am stating. [The first one]("https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu") is not the most recent thing, since it is from 2013, but I think that not much is changed since then. [The second one]("https://help.ubuntu.com/community/UbuntuStudioPreparation") is up to date.

Since the [main documentation site for UStudio]("https://help.ubuntu.com/community/UbuntuStudio") points to outdated pages I see why there is so much misunderstanding...

You see, you can turn a standard Ubuntu installation into Ubuntu Studio just adding packages (all from the standard Ubuntu repos, unless you add KXStudio repos) and modifying some configuration file. That's all: Ubuntu Studio is Ubuntu with a different pool of preinstalled software (that you can install on vanilla as well using software center) configured in a slightly different way (configuration you can achieve on vanilla as well). To be honest, I always found the configuration of UStudio to be so close to vanilla Ubuntu to be forced to modify it again to suit my audio needs. The big difference is in the kernel. From the second page I linked:

> [COLOR=#333333][FONT=Ubuntu]Take care when using the -lowlatency kernel, as it might not support some restricted drivers (For example: nNidia or AMD/ATI, some wifi chipsets).[/FONT][/COLOR]

I remember to you that the [lowlatency kernel]("http://packages.ubuntu.com/trusty/linux-generic") is developed by [the same team that develops the standard one]("https://wiki.ubuntu.com/UbuntuDevelopers#CoreDev"): you don't have to blame UStudio for that, which is just a remix of Ubuntu including a particular selection of standard packages.

Some year ago (11.04 era I think) I found a guy on a forum (don't remember where) saying "I cannot understand why the whole internet waits for the new release of Ubuntu Studio while it is so easy to tune any distro for proper audio performances".

Well, I think that installing UStudio can have a point. I was used to do it because it is less time consuming: Install Ubuntu and then configuring it for audio requires time of installation + time of configuration. For UStudio you need the time of installation and not much more, since the big of the configuration has been done by the UStudio team. Anyhow, I think that the quote is useful to stress this point: UStudio is just a remix. Then, what one should install? The one you like! You have a couple of option and you can make the experiments you want on your computer. Just make sure to not put your data in danger and have fun! You can always try both the flavors without install and see how you feel it.

Hope it helps!

---

### Post by grahammechanical on 2014-10-11
Ubuntu Studio follows the same release cycle as Ubuntu. It is in fact built upon the Ubuntu code. Updates to Ubuntu will come through to Ubuntu Studio because, as someone stated earlier, they use the same repositories.

That low latency kernel is a big difference. In two ways. It will not be the same kernel as in Ubuntu. There will be a delay in the updating of the kernel as it needs to be patched to be a low latency kernel. And for audio work it seems that the standard kernel in Ubuntu is not good enough.

But, hey, we have freedom. We can work the way we want. We can do it the easy way or the hard way. It is our choice.

Regards.

---

### Post by MartyBuntu on 2014-10-12
> **grahammechanical said:**
> And for audio work it seems that the standard kernel in Ubuntu is not good enough.



Well, specifically it's "not good enough" for real-time or *near* real-time audio production.
Most other aspects shouldn't matter.

---

