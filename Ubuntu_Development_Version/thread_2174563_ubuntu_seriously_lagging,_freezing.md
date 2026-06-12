---
title: "ubuntu seriously lagging, freezing"
date: 2013-09-15
forum: Ubuntu Development Version
---

### Post by David_H_Smith on 2013-09-15
Hi Guys,

My Ubuntu 13.10 is acting REALLY weird.  Never had a significant problem with my computer until now.

Its when I load up UBUNTU and EVERYTHING LAGS, badly.  Clicking on the Ubuntu search app takes about 10 seconds before it decides to do anything, then its almost like a slow-motion replay of it appearing. frame by frame.  I check sys monitor (with same results) and eventually find both CPU`s are running 70-99% when no other programme is running.  I then try to shutdown UBUNTU and it TOTALLY freezes and becomes unresponsive.  

Also System Updater keeps telling me some of the upgrades can`t complete, and should attempt a partial upgrade.  I click on partial upgrade and nothing happens.  From what I can gather the upgrade is to do with my onboard nVidia GeForce 7025 graphics card.  Ubuntu shows now as a different graphics card completely that I don`t recognise.

Thinking logically I decided to do a complete reboot of UBUNTU with my 13:04 disc, choosing delete current UBUNTU and install new UBUNTU.  Unfortunately when its upgrading the same problem with the Software Updater, it can`t install all updates, then when you click Partial Update, software updater disappears and nothing happens.

Do I have a virus?  Can UBUNTU even get viruses? Or is my saystem too old.  Bought it in 2005.

1GB DDR2 RAM
nVidia Geforce 7050M-M motherboard
onboard nVidia 7025 graphics card
AMD2 3.0Mhz Dual core processor

---

### Post by Bucky Ball on 2013-09-15
Welcome. All 13.10 support threads belong in ***Ubuntu +1*** sub-forum. It is not released, still testing and wondering why a new-comer would choose to use it. Expect issues.

I moved it there and back as it looks like your real question is:

> Do I have a virus? Can UBUNTU even get viruses?

... but I suspect it actually belongs elsewhere as don't think this has anything to do with viruses. 

Nothing wrong with the machine specs. You should be able to run any flavour on that. Virus unlikely, I'd be looking elsewhere. If you reinstall 13.10 (probably not best for now) post all support requests in +1. ;)

Try opening a terminal and try these two commands (in a full hard drive install):

```
sudo apt-get update
sudo apt-get upgrade
```

ALWAYS run the first update command BEFORE the upgrade one. If you are trying to upgrade before update, could be the problem.

---

### Post by ajgreeny on 2013-09-15
If it's still happening after you do whatever you choose to do, (reinstall 13.10, or better, I suggest, install 13.04 over the current 13.10) you can probably get some clue as to why it is lagging and freezing by using command **top** in terminal.  This will list all running applications and services in order of their resource use, and you may get a clue about what is taking all your resources and causing the problem.

Type an upper case P to rank things according to cpu usage, and upper case M for memory usage.

---

### Post by CeejRab on 2013-09-15
Your system is over-capable of running even a loaded version of linux, so thats not a problem at all... Sounds like a deeper OS problem to me, and if you cant get any where trying to update, i definitely recommend backing up your files (run a live cd and back your files up to a external HD since it would take forever to do so in the lagging OS) and then do a fresh install of Ubuntu.

Personally i recommend the LTS versions simply because it is what it is, Long Term Support. Canonical has more focus on the 5 year release than the 9 month release and its best to stick with the stable option rather than go for the cosmetic wippity do of the newer ones. Thats a personal opinion of course, but i know theres others who agree its best to stick with LTS releases to avoid the bugs of the newer ones until the next LTS comes out.

---

### Post by chrismine on 2013-09-15
When I click on the unity button to open the menu everything goes in slow motion or try seems to freeze.

When clicking on gear button the restart or shutdown the same happens and the menu takes a long time to appear.

It aDual Core E5200 with 4GB memory and Intel graphics. I even did a fresh install from the daily image I downloaded on 13 September.

I think the thread can be moved back to Ubuntu+1

---

### Post by trundlenut on 2013-09-15
Previously I have had a kernel update which cause similar issues.  A subsequent update sorted it.

---

### Post by cariboo on 2013-09-15
Even though the op mentions a virus, the problem has nothing to do with it. Moved back to U+1.

We need some troubleshooting data from those that have this problem. Have any of you run top, to see if there is something that is using all you resources?

---

### Post by Bucky Ball on 2013-09-15
***Post moved to own thread***

---

### Post by P-I H on 2013-09-16
I run Saucy on a Asus EEE PC 1000HE. An odd thing is that the setting "Background blur" in Unity Tweak tool has a very big effect on Dash performance. With "Background blur" set to on it takes about a minute before it is possible to enter text in the search field. With "Background blur" set to off the computer behaves as expected.

---

### Post by maravingian on 2013-09-16
So I reverted back to 13:04 from a clean install and the problem seems to have sorted itself out. :)

Cheers guys

---

### Post by makitso on 2013-09-16
Open a terminal and type in top  command.  Do you see anything suspicious in terms of cpu utilization?
Log out and then back in, does this solve the problem?

---

### Post by chrismine on 2013-09-16
The problem is solved by switching off Background Blur from the Search option in the Unity Tweak Tool as per the post #8 above.

I did not do a top command as the problem only appear when you click on the Unity search icon and the system then become unresponsive for several minutes...

---

### Post by tj001 on 2013-09-20
> **chrismine said:**
> The problem is solved by switching off Background Blur from the Search option in the Unity Tweak Tool as per the post #8 above.

I have (had) the same issue on my Packard Bell netbook (DOA150), and switching off Background Blur from the Search option in the Unity Tweak Tool also solved the problem for me.

I upgraded Ubuntu 13.04 to 13.10 earlier this summer, and it was running fine - until some day in august, when this started. Maybe it has something to do with Mir? Just a guess...

---

### Post by Bucky Ball on 2013-09-20
> **tj001 said:**
> I upgraded Ubuntu 13.04 to 13.10 earlier this summer, and it was running fine - until some day in august, when this started. Maybe it has something to do with Mir? Just a guess...

*All* 13.10 issues should be posted in the Ubuntu +1 sub-forum. Thanks.

---

### Post by amjjawad on 2013-09-20
> **David_H_Smith said:**
> Hi Guys,

Hello and welcome to Ubuntu Forums :)


>  My Ubuntu 13.10 is acting REALLY weird.  Never had a significant problem with my computer until now.
Just to make sure, do you realize that you are running a non-stable version of Ubuntu which is still under heavy developmenet?

[http://fridge.ubuntu.com/2013/09/06/13-10-saucy-salamander-beta-1-released/](http://fridge.ubuntu.com/2013/09/06/13-10-saucy-salamander-beta-1-released/)

Are you trying to use Ubuntu 13.10 for your day-to-day tasks? or are you testing it?

How did you install your system?

If you are willing to test and not use this for day to day, please download the latest daily build and re-install.

[http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)

>  Do I have a virus?  Can UBUNTU even get viruses? 
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

> Or is my saystem too old.  Bought it in 2005.

[COLOR=#ff0000]** 1GB DDR2 RAM**[/COLOR]
nVidia Geforce 7050M-M motherboard
onboard nVidia 7025 graphics card
AMD2 3.0Mhz Dual core processor

Obviously, here is the problem.

Your system can not handle Unity :)
Please, consider using either Lubuntu OR Xubuntu

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)
[http://xubuntu.org/](http://xubuntu.org/)

And yet again, 13.10 is NOT yet a stable release!

Thank you!

---

### Post by philinux on 2013-09-21
Here are the recommended requirements for ubuntu.

1gig of ram is fine. Graphics cards are another story.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by VMC on 2013-09-21
I too am experiencing serious lag. I couldn't get the panel readable until I install nvidia-173. Now the panels are great, but the system is very sluggish. 
The same nvidia driver works perfect using Ubuntu Gnome, and Kubuntu works perfect using nouveau.

---

### Post by J._R._Menzie on 2013-10-02
I see the same thing. When you enable blur. There is a noticable slow down when opening the Dash. Setting it to Static solves the problem. I do not understand this because I have a very powerful GPU.

---

### Post by pauljwells on 2013-10-02
[http://ubuntuforums.org/showthread.php?t=2177095&p=12802314#post12802314](http://ubuntuforums.org/showthread.php?t=2177095&p=12802314#post12802314)

---

### Post by bennachie on 2013-10-06
My Lenovo M57e easily meets the stated requirements, and handles Windows 7 and any variety of Linux (other than Ubuntu) with ease. Yes, the problem is easily fixed once you have patiently waited to download and then run Unity Tweak Tool, but surely, if Background Blur is that important to the current target users, the installer could detect machines unable to deliver the necessary graphic acceleration, and switch the effect off automatically. Unity seems to operate just fine without Background Blur.

---

### Post by Mateusz Stachowski on 2013-10-06
> **bennachie said:**
> My Lenovo M57e easily meets the stated requirements...

I wouldn't be sure about that because the integrated graphic card Intel GMA 3100 most likely doesn't support OpenGL 2.1. That's requiered for proper handling of Unity background blur. There is a [bug report]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1222602") about that and it turns out that the new mesa 9.2 advertises OpenGL 2.1 hardware support for some Intel chips but in reality it's doing that in [software]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1222602/comments/37") which is very slow.

There is workaround for that problem described in comments. Adding this line to the /etc/environment will switch to lower version of background blur which is supported with hardware acceleration on these Intel graphic chipsets.

MESA_GL_VERSION_OVERRIDE=1.4

---

### Post by jerrylamos on 2013-10-06
> **chrismine said:**
> The problem is solved by switching off Background Blur from the Search option in the Unity Tweak Tool as per the post #8 above.

A simpler way to avoid the 13.10 blur code is:

Add to /etc/environment
    MESA_GL_VERSION_OVERRIDE=1.4

I don't have unity-tweak-tool installed (it's hurge) for any other reason.  

The new blur code doesn't work as expected on many hardware configurations including mine.  For whatever reason development chose to emulate some hardware functions in software which is much slower.  The above change puts the function back in the much faster hardware.

I think launchpad bug #1222602 has some more detail.

At 78 my vision is blurry enough I don't need deliberate blur in ubuntu.

---

### Post by Mateusz Stachowski on 2013-10-07
This should be resolved now with the release of new Mesa package.

> [COLOR=#333333][FONT=Ubuntu Mono]mesa (9.2.1-1ubuntu1) saucy; urgency=low[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]  [ Robert Hooker ]
  * Add i915-dont-default-to-2.1.patch: Stop defaulting to OpenGL 2.1 that is not
    fully implemented in hardware on gen3 GPUs, the software fallbacks make Unity
    unusably slow. (LP: [#1222602]("https://bugs.launchpad.net/bugs/1222602"))
  [ Maarten Lankhorst ]
  * New upstream bugfix release. (LP: [#1232940]("https://bugs.launchpad.net/bugs/1232940"))[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]mesa (9.2.1-1) experimental; urgency=low[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]  * New upstream release.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono] -- Maarten Lankhorst <maarten.[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]lankhorst@[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]ubuntu.[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]com> Mon, 07 Oct 2013 10:39:18 +0200[/FONT][/COLOR]

This also resolves a bug when Unity launcher and panel would show as color bar on Nouveau.

---

### Post by kansasnoob on 2013-10-07
> **Mateusz Stachowski said:**
> This should be resolved now with the release of new Mesa package.



This also resolves a bug when Unity launcher and panel would show as color bar on Nouveau.

That's good news :)

---

### Post by bennachie on 2013-10-08
After the recent update to Mesa, my system runs just fine when I leave "background blur" set to "static", but continues to hang when I choose "active". I assume that static will be the future default?

JIT manufacturing has always been a high-risk venture.

---

### Post by kansasnoob on 2013-10-09
> **bennachie said:**
> After the recent update to Mesa, my system runs just fine when I leave "background blur" set to "static", but continues to hang when I choose "active". I assume that static will be the future default?

JIT manufacturing has always been a high-risk venture.

In deed! JIT sounds great on paper but in reality it only creates stress!

In the case of Canonical/Ubuntu it means that bugs are ignored until the last minute :(

---

### Post by PauloI on 2014-02-17
I have the same problem. 2GB RAM, 2,50GHz CPU, 80GB HDD - isn't it much more then RECOMMENDED configuration? Yes, for sure. But it lags, CONSTANTLY. It is enough to open opera, and then try to open Libre Office. It seems Ubuntu 13.10 needs some top workstation performance, the specifications given at [http://askubuntu.com/questions/333795/what-are-the-system-requirements-for-each-flavor-of-ubuntu-desktop](http://askubuntu.com/questions/333795/what-are-the-system-requirements-for-each-flavor-of-ubuntu-desktop) page are totally misleading. Honestly I think the developers just don't cope with the system of such complexity.

---

### Post by cariboo on 2014-02-17
@PauloI , you don't mention what graphics adapter and driver you are running. This forum is for the discussion and troubleshooting of Trusty (14.04) problems. I'd suggest you start a new thread in General Help, as this thread is closed.

---

