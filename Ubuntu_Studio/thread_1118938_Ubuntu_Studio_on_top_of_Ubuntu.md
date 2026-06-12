---
title: "Ubuntu Studio on top of Ubuntu"
date: 2009-04-07
forum: Ubuntu Studio
---

### Post by mwacky on 2009-04-07
Can I install ubuntu studio on top of my ubuntu installation, I have done this with xubuntu and ubuntu..

---

### Post by Stochastic on 2009-04-07
These are the instructions you'll need to follow: [https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy)

Hope that helps.

---

### Post by TBerk on 2009-04-07
I just did the same thing via Synaptics Package manager this morning over the top of Justy beta.

(Didn't solve my Audigy2 not outputing sound problems, of course.)


TBerk

[edit]
btw- later updates **did** solve my audio troubles.  tb

---

### Post by Stochastic on 2009-04-07
> **TBerk said:**
> I just did the same thing via Synaptics Package manager this morning over the top of Justy beta.

(Didn't solve my Audigy2 not outputing sound problems, of course.)


TBerk

You know, that page is specific to Hardy, if you find it works on Jaunty I'd highly encourage you to make a new one that describes the upgrade process for Jaunty, then add a link to it here: [https://help.ubuntu.com/community/UbuntuStudio/Installation](https://help.ubuntu.com/community/UbuntuStudio/Installation)

Those community docs really do require a lot more of the community's attention.

---

### Post by mwacky on 2009-04-07
Thanks for your replies, from the Hardy link the command is:

> sudo aptitude update && sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt

and further down it says:

> Note: This installs a complete system. If you only want an audio, graphics, or video platform, remove the other respective packages.

So if I just wanted the audio, graphic and video platform which packages would I not include?

(My guess is ubuntustudio-desktop and linux-rt, but I'm not sure).  I'm not really interested in the themes and such I just want those video/audio packages.

Thanks Again!

---

### Post by Stochastic on 2009-04-08
> **mwacky said:**
> So if I just wanted the audio, graphic and video platform which packages would I not include?

The directions really should be written clearer I guess (maybe you could edit them once you get the hang of this).  
The meaning of that sentence is that if you only want video, you don't need to install the audio or graphics packages (notice the 'or').  The ubuntustudio-desktop package is the one that gives all the themes, but I think some other important items are included through it; it sounds like you might want to omit that one (although it probably doesn't turn the themes on by default).  The linux-rt package you should install on any system that you want to do audio recording on (unless it's an Intrepid system).

Here's a full detailed breakdown of what each metapackage will install underneath: [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ubuntustudio](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ubuntustudio)

---

### Post by TBerk on 2009-04-08
> **Stochastic said:**
> You know, that page is specific to Hardy, if you find it works on Jaunty I'd highly encourage you to make a new one that describes the upgrade process for Jaunty, then add a link to it here: [https://help.ubuntu.com/community/UbuntuStudio/Installation](https://help.ubuntu.com/community/UbuntuStudio/Installation)

Those community docs really do require a lot more of the community's attention.

Hmmm, Good idea, as in If not me, who else, right?

Let me see if I can document my steps; I've done it twice now (via synaptic), I'd like to be able to be precise with optional roads to the same *'Rome'*

TBerk
ps- I seem to have added enough ALSA/PCM modules to activate sound w/ my Audigy2

---

### Post by smurray on 2009-04-09
When you say this only applies to the Hardy version, is that the Ubuntu 8.10 distro?  Sorry, I'm kind of new to linux, and I want to have both a good work station environment (ie. latest Ubuntu 8.10) and a good recording studio (ie. Ubuntu Studio).

I'm just curious and cuatious of the effects of the upgrade.

---

### Post by Stochastic on 2009-04-09
> **smurray said:**
> When you say this only applies to the Hardy version, is that the Ubuntu 8.10 distro?  Sorry, I'm kind of new to linux, and I want to have both a good work station environment (ie. latest Ubuntu 8.10) and a good recording studio (ie. Ubuntu Studio).

I'm just curious and cuatious of the effects of the upgrade.

No, Hardy is 8.04, Intrepid is 8.10 (and Jaunty is/will be 9.04).
Recording on an Intrepid system is not recommended - the RT kernel that gives low latency is quite broken in the Intrepid/8.10 release and thus audio people are told to stay with 8.04 until 9.04 is released later this month (April 23rd).

---

### Post by TBerk on 2009-04-09
> **smurray said:**
> When you say this only applies to the Hardy version, is that the Ubuntu 8.10 distro?  Sorry, I'm kind of new to linux, and I want to have both a good work station environment (ie. latest Ubuntu 8.10) and a good recording studio (ie. Ubuntu Studio).

I'm just curious and cautious of the effects of the upgrade.

Different things: "specific to" and "only applies". 


If you go to Synaptic Package Manager and select:

**Sections** (lower left corner of the screen)
**Choose Meta Packages (universe)**
& in the Quick Search field type in **studio**

You'll see a number of Packages to select. Choosing them will bring along the other dependant packages as well.

[img]http://www.geocities.com/bayareaberk/selecting_studio_via_synaptic.png[/img]


For example. 

Notice this is just the 1st selection, there are groups for the Audio & Video, etc, etc.


TBerk
(btw- this example applies directly to my own 9.04 beta install, the exact specific files may be slightly different, natch.) YMMV

---

### Post by smurray on 2009-04-10
> **Stochastic said:**
> No, Hardy is 8.04, Intrepid is 8.10 (and Jaunty is/will be 9.04).
Recording on an Intrepid system is not recommended - the RT kernel that gives low latency is quite broken in the Intrepid/8.10 release and thus audio people are told to stay with 8.04 until 9.04 is released later this month (April 23rd).

Ah! Thanks for the quick response and great info.  I'm glad I checked, it wouldn't have been the first time I'd had gotten ahead of myself for a good studio program.  haha. Would it be unwise to maybe dual boot into the Ubuntu Studio as Hardy, and keep Intrepid on a separate partition?

---

### Post by Stochastic on 2009-04-10
> **smurray said:**
> Ah! Thanks for the quick response and great info.  I'm glad I checked, it wouldn't have been the first time I'd had gotten ahead of myself for a good studio program.  haha. Would it be unwise to maybe dual boot into the Ubuntu Studio as Hardy, and keep Intrepid on a separate partition?

That would work fine.

Or you could wait two weeks and dual boot into Jaunty (even just run everything in Jaunty).

---

### Post by smurray on 2009-04-10
> **Stochastic said:**
> That would work fine.

Or you could wait two weeks and dual boot into Jaunty (even just run everything in Jaunty).

Haha, makes perfect sense.  Although I've always been told to be weary of new releases.  Thanks again for the help, sadly I don't expect it to be the last time haha :)

---

### Post by tomthumb99 on 2009-04-21
Folks, pls advise how to back out or remove Ubuntu Studio and get back to base 8.10 Ubuntu.  I was installing some Webcam software from synapic manager and got into this mess.  Utumbu-Studio does not work on my PC, X-Win/Gnome login brings up a black screen, although my base OS is fine.  I get the the tty screen fine, have reinstall ubumtu-desktop twice now.

Ubuntu Studio folks, you software should require a separate CD install outside of Synaptic.  I have enough trouble/probs with base 8.10, I do not need further complications.

---

### Post by wkulecz on 2009-04-22
> You know, that page is specific to Hardy, if you find it works on Jaunty I'd highly encourage you to make a new one that describes the upgrade process for Jaunty

I disagree, if the proceedure works, we do not need a duplicate page. An edit to the existing page to mention it works on the new release would be all that is needed so searches can find it.  

Standardized proceedures are a good thing compared to different for the sake of being different -- which is how I see Vista vs. XP.

Now if you need a new proceedure for installing on 9.04, fine, a new page would be required, but I don't consider this a plus for 9.04.

--wally.

---

### Post by snowpine on 2009-04-22
> **tomthumb99 said:**
> Folks, pls advise how to back out or remove Ubuntu Studio and get back to base 8.10 Ubuntu.  I was installing some Webcam software from synapic manager and got into this mess.  Utumbu-Studio does not work on my PC, X-Win/Gnome login brings up a black screen, although my base OS is fine.  I get the the tty screen fine, have reinstall ubumtu-desktop twice now.

Ubuntu Studio folks, you software should require a separate CD install outside of Synaptic.  I have enough trouble/probs with base 8.10, I do not need further complications.

Simply reverse the process and use the Synaptic Package Manager to remove whatever packages you installed (linux-rt, ubuntustudio-audio, etc).

---

### Post by wkulecz on 2009-04-22
> Folks, pls advise how to back out or remove Ubuntu Studio and get back to base 8.10 Ubuntu

Have you tried booting the old (previous) kernel?  Perhaps its an issue with the -rt kernel and lack of video driver for it.

I find the -rt kernel a worthwile upgrade to my 8.04 even though I'm not using the rest of studio, but it took s few updates before I removed the standard kernel as a boot option

--wally.

---

### Post by Stochastic on 2009-04-22
> **wkulecz said:**
> I disagree, if the proceedure works, we do not need a duplicate page. An edit to the existing page to mention it works on the new release would be all that is needed so searches can find it.  

Standardized proceedures are a good thing compared to different for the sake of being different -- which is how I see Vista vs. XP.

Now if you need a new proceedure for installing on 9.04, fine, a new page would be required, but I don't consider this a plus for 9.04.

--wally.

I somewhat agree with you.  The process does work for other installs, but the package names might change slightly from release to release so a consolidation effort may need to be done carefully.  Even if the current instructions do work for Intrepid and Jaunty, they directly state that they're for Hardy so this does need to be changed.  But by all means please go edit the documentation - it sounds like you have enough knowledge on your shoulders to really help out with that page.

---

### Post by tomthumb99 on 2009-04-22
All, thanks for the points.

I just have access to the tty command line and the apt-get aptitude commands.  What is the key package name of the  'ubuntu studio' that will remove all related others.  I ran  a apt-cache, there are over 15+ packages related to studio.

It also sounds like I need to pull out the 'rt kernel', how is that done?  If you can pls point me to other postings if possible.

KEY:  My OS is very close to working, X-server runs, login occurs.  My nvidia drivers are the last problem, have the 177 version (180 NG) back in place.  But still get the black screen, getting glx driver issues!  any xorg.conf setting I can try, like lower resolution?

NOTE: On the install question, MS has different CDs for diff versions of SW/OS.  At the very lease these should be a synaptic warning (ie: like nvidia drivers) How many other are going to step into this prob unaware.  You folks are the Ubuntu pros, not very body is (ie: like myself)
  
Thanks for your time..

---

### Post by tomthumb99 on 2009-04-26
folks,  I have back out most of my recent install and running the below two commands, no luck.  Still get black screen after x win login.


apt-get install --reinstall x-window-system-core

apt-get install --reinstall ubuntu-desktop

But still 'Ubuntu Studio' login screen appears, I have my xorg.conf back to bare bones using nvidia-xconfig.

Reading a lot about glx problem, although my  Xorg.0.log looks clean with 177 drivers loaded. But running glxgears cannot find the monitor.  Also, finding Xinerama probs listed with nvidia drivers, I was using twinview, how did that get changed, ubunu studio default??

Any ideas or log files to look at??

thanks

---

### Post by tomthumb99 on 2009-04-27
Folks, found the offending package 'ubuntustudio-gdm-theme' it put the paint brushed on the X-win login screen.  It was the only ubuntu-studio package actually installed. It would have been helpful if the person who wrote this software offered some advice.

I was able to get brown-tan screen back, next was the gnome-power-manager corrupted schemas files and installed theme package issue discovered, this prob being worked upon.  Could have been that the offending package threw off the exiting themes, don't know.

Sure would be nice to have synaptic packages fully tested.

Note: My last resort not used was to run:

 aptitude install x-window-system ubuntu-desktop

---

