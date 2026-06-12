---
title: "Installin nvidia 180.11 driver from repos in Hardy"
date: 2008-12-05
forum: The Cafe
---

### Post by fjf on 2008-12-05
It works!:

1-Go to system-->administration-->software sources, deselect universe, go to third party software, add:  > deb [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) jaunty main restricted
2-Close and reload sources
3-Open a terminal and type:  sudo apt-get install nvidia-glx-180
4-IMPORTANT:  Go back to software sources and undo the changes, close and reload
5-Reboot

Voilà!.  Working fine!.  I have to say the 2D speed has increased noticeably.

---

### Post by QCompson on 2008-12-05
Nice, thanks for the info.

Silly questions: 

1) Should we unload 177.80 drivers before upgrading (including all associated kernel-modules, etc)?

2) Is a reboot necessary, or will restarting the X server suffice?

---

### Post by fjf on 2008-12-05
1-The unload is done automatically by the install

2-Dont really know, but since this implies installing a nvidia kernel module I felt I should reboot.  You can try not to.

---

### Post by NTolerance on 2008-12-05
Maybe I'm failing to understand something, but doesn't DKMS make it easy for this driver and other updated drivers to be used on Intrepid?  If so, why is it not in the Intrepid repos?

---

### Post by Sealbhach on 2008-12-05
> **NTolerance said:**
> Maybe I'm failing to understand something, but doesn't DKMS make it easy for this driver and other updated drivers to be used on Intrepid?  If so, why is it not in the Intrepid repos?

I think the 180.xx drivers are all still in Beta, not thoroughly tested enough to go in the official repos yet.



.

---

### Post by Eclipse. on 2008-12-05
Download the package manually from the archive if you want it that can be dangerous.The bug report to get it into intrepid/hardy says "In Progress" so chill it will be in a day or two if you can wait.

---

### Post by Sealbhach on 2008-12-05
OP's method worked like a charm for me. Thanks! :p


.

---

### Post by Eclipse. on 2008-12-05
> **Sealbhach said:**
> OP's method worked like a charm for me. Thanks! :p


.

I'm not saying it doesnt work, just its more dangerous.;)

Plus its a package made for jaunty, not hardy or intrepid.

---

### Post by Sealbhach on 2008-12-05
> **Eclipse. said:**
> I'm not saying it doesnt work, just its more dangerous.;)

Plus its a package made for jaunty, not hardy or intrepid.

Yes, I know what you mean. But I already had 180.06 so I thought what the hey...


.

---

### Post by fjf on 2008-12-06
Working fine in intrepid too.  No problems so far, fast 2D rendering.  The screens in firefox appear now almost instantaneously ;)

---

### Post by eternalnewbee on 2008-12-06
> It works!:

1-Go to system-->administration-->software sources, deselect universe, go to third party software, add:
Quote:
deb [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) jaunty main universe
2-Close and reload sources
3-Open a terminal and type: sudo apt-get install nvidia-glx-180
4-IMPORTANT: Go back to software sources and undo the changes, close and reload
5-Reboot
I followed your instructions.
After reboot the update notification icon says 633 updates available:
Does this mean I'm already upgrading to 9.04?
I thought I just installed a new driver...

---

### Post by Polygon on 2008-12-06
thats because its trying to install all the newer jaunty  packages.........i don't think that solution is going to work

---

### Post by Sealbhach on 2008-12-06
> **eternalnewbee said:**
> I followed your instructions.
After reboot the update notification icon says 633 updates available:
Does this mean I'm already upgrading to 9.04?
I thought I just installed a new driver...

I'm almost certain it's because you didn't do this step before rebooting:

```
4-IMPORTANT: Go back to software sources and undo the changes, close and reload

```

.

---

### Post by eternalnewbee on 2008-12-06
Hi Polygon.
> thats because its trying to install all the newer jaunty packages.........i don't think that solution is going to work
Which solution do you mean?

---

### Post by eternalnewbee on 2008-12-06
> 
I'm almost certain it's because you didn't do this step before rebooting:

Code:

4-IMPORTANT: Go back to software sources and undo the changes, close and reload
Hi Sealbhach.
By undoing the changes, I assumed reenabling universe...
Which I did.
What did I miss?..

---

### Post by Eclipse. on 2008-12-06
> **eternalnewbee said:**
> I followed your instructions.
After reboot the update notification icon says 633 updates available:
Does this mean I'm already upgrading to 9.04?
I thought I just installed a new driver...

Note why I said this is dangerous.;)

_Do not install the upgrades what ever you do._

Open your sources.list file and remove the entry you made in it.Then run "sudo apt-get update" and they should go away.

---

### Post by eternalnewbee on 2008-12-06
>  Re: Installin nvidia 180.11 driver from repos in Hardy
Quote:
Originally Posted by eternalnewbee View Post
I followed your instructions.
After reboot the update notification icon says 633 updates available:
Does this mean I'm already upgrading to 9.04?
I thought I just installed a new driver...
Note why I said this is dangerous.

Do not install the upgrades what ever you do.

Open your sources.list file and remove the entry you made in it.Then run "sudo apt-get update" and they should go away.
Eclipse.:
You know, this is really annoying!!!
I keep finding new heroes here!!!
Mission accomplished.

---

### Post by aktiwers on 2008-12-07
I would not recommend installing using this method.. 
I just did on  my Geforce 9800GTX and I was left without X (no GUI)..

When trying to revert back to my old drivers, they conflicted with the 180.11 libs(libGl files), refusing to install.
I had to manually delete lots of files, download my driver 177 driver manually, install it manually and finally got X back to work.. All this after spending lots of time troubleshooting..

Now I can't install the drivers from the repos (the 177) and my lots of compiz plugins can't be enabled(the animation plugin for instance)..  

I am not complaining, just giving a warning. ;)

---

### Post by eternalnewbee on 2008-12-07
Funny thing is, the new driver doesn't show in Hardware Drivers, while the three othersare not installed. I wonder why the new driver is not shown.
EDIT: Never mind. Found the answer here:
[http://ubuntuforums.org/showthread.php?t=990978&page=15](http://ubuntuforums.org/showthread.php?t=990978&page=15) (post 149).

---

### Post by fjf on 2008-12-07
> **eternalnewbee said:**
> Eclipse.:
You know, this is really annoying!!!
I keep finding new heroes here!!!
Mission accomplished.

Hey, I wrote that you should undo the changes!.  Of course, this meant reenabling Ibex universe and disabling Jaunty universe.  You dont want to mix repos from different distros.  Unless you want to find out what a hybrid from an Ibex and a Jantalope looks like!.

Anyway, I'm sorry for the troubles.  I guessed that uninstalling the driver nvidia-glx-180 with apt-get should do it.  Seems I was wrong ;).  That's what happens when you play.  ):P

---

### Post by eternalnewbee on 2008-12-08
>  Re: Installin nvidia 180.11 driver from repos in Hardy
Quote:
Originally Posted by eternalnewbee View Post
Eclipse.:
You know, this is really annoying!!!
I keep finding new heroes here!!!
Mission accomplished.
Hey, I wrote that you should undo the changes!. Of course, this meant reenabling Ibex universe and disabling Jaunty universe. You dont want to mix repos from different distros. Unless you want to find out what a hybrid from an Ibex and a Jantalope looks like!.

Anyway, I'm sorry for the troubles. I guessed that uninstalling the driver nvidia-glx-180 with apt-get should do it. Seems I was wrong . That's what happens when you play.
No worries fjf. It's all worked out just fine. Sorry for the late reply. Internet connection troubles.

---

### Post by psychok9 on 2008-12-12
Thank you!
No nvidia-glx-180 from synaptic, but with sudo apt-get install nvidia-glx-180 I get a perfect remove & installing.

A application freeze with a 1080p video and totem (It's beta driver and with very new feature...), but 2nd time worked flawlessy.

Ubuntu Intrepid 8.10 x86_64, Q6600@3.2GHz, nVidia 8800 GT.

---

### Post by simtaalo on 2008-12-13
thank you, only just installed it but already everything seems alot smoother.

---

### Post by starscalling on 2008-12-20
> **psychok9 said:**
> Thank you!
No nvidia-glx-180 from synaptic, but with sudo apt-get install nvidia-glx-180 I get a perfect remove & installing.

A application freeze with a 1080p video and totem (It's beta driver and with very new feature...), but 2nd time worked flawlessy.

Ubuntu Intrepid 8.10 x86_64, Q6600@3.2GHz, nVidia 8800 GT.



rolling em about the same:

Ubuntu Intrepid 8.10 x86_64, Q6600@3.15GHz [true120 for air], nVidia 8600 GT

i had to dpkg-reconfigure xserver-xorg to basically wipe the settings, and then run nvidia-xconfig to get it back. works great now...

---

### Post by fjf on 2008-12-21
My system is still working fine, and had no problems setting the drivers at all.  They worked first time.  I guess I was lucky ;)

---

### Post by spongypants23 on 2009-01-02
...

---

### Post by sbentjies on 2009-01-04
180.11 did not work for me. I have a GEForce FX-5200 and running 8.04 The system is insistent on running in legacy mode-it's like the card is not even detected. I wish there were a tool to build a custom xorg.conf . Everything I've tried to do breaks X.

---

### Post by laceration on 2009-01-04
> 180.11 did not work for me. I have a GEForce FX-5200
If you are dedicated enough to play with the new beta drivers, can't you scrape together $30 for a new video card?  I don't know where you are, but here in the U.S. there are all kinds of deals for 7000 series cards and up.  You can't expect much from a FX-5200.

---

### Post by igknighted on 2009-01-04
> **sbentjies said:**
> 180.11 did not work for me. I have a GEForce FX-5200 and running 8.04 The system is insistent on running in legacy mode-it's like the card is not even detected. I wish there were a tool to build a custom xorg.conf . Everything I've tried to do breaks X.

Support for the FX-5xxx series cards has been dropped with the latest nvidia drivers.  You will need in the future (8.10 and later) to use the older drivers.

---

### Post by sbentjies on 2009-01-04
Then what is the solution? How do I get drivers working for this card? I don't get a warm fuzzy that Ubuntu supports Nvidia except the latest and greatest. This was a free computer so I'm not dumping a bunch of money into it. The GeForce was $40. Any and all help is greatly appreciated.

---

### Post by igknighted on 2009-01-04
> **sbentjies said:**
> Then what is the solution? How do I get drivers working for this card? I don't get a warm fuzzy that Ubuntu supports Nvidia except the latest and greatest. This was a free computer so I'm not dumping a bunch of money into it. The GeForce was $40. Any and all help is greatly appreciated.

Don't blame Ubuntu, blame nvidia.  By using nvidia, you are completely at the mercy of what they want to make drivers for.  Intel, on the other hand, uses completely open source drivers so the community can continue supporting the card.  Even AMD/ATI releases specs for their cards so the community can make drivers to keep a card usable long beyond its support in the official drivers.

With your nvidia card, you will have to use the legacy drivers.  You will still be able to use them for 3d support as long as that driver still works with the Xorg release being used, but with these proprietary graphics, you just can't be guaranteed that support will last forever.

---

### Post by sbentjies on 2009-01-04
You must have a newer card too. I'm getting a sinking feeling about this FX-5200

---

### Post by sbentjies on 2009-01-04
ok, I can use the synaptics manager to turn the legacy drivers back on, but that doesn't reconfigure X for me. Any ideas on that? Would an ATI card work better because I'll pull out this NVIDIA in a heartbeat. I just wish it weren't this difficult because I really like Ubuntu.

---

### Post by sbentjies on 2009-01-04
I will give that a shot. Do I still need to enable legacy drivers in the Synaptic Package manager or in the Hardware Driver utility?

---

### Post by laceration on 2009-01-05
There is great program called Envy.  It is in Synaptic.  It will install the correct drivers for you automatically and configure everything--painlessly with nothing to think about.

Maybe you have an old beater computer that is not worth putting anything into.  But if you do decide to get a new video card Nvidia is the best.  Though they are closed source, that their drivers may not offer support in the future is only hypothetical. The fact is, as reflected by the original subject of this thread they work better than anything else.

---

### Post by igknighted on 2009-01-05
> **sbentjies said:**
> I will give that a shot. Do I still need to enable legacy drivers in the Synaptic Package manager or in the Hardware Driver utility?

Select the 180 driver for complete removal (this should remove config files too), then install the legacy one.  If X fails still, run the command 'sudo nvidia-xconfig' to rebuild a new xorg.conf.

---

### Post by igknighted on 2009-01-05
> **laceration said:**
> There is great program called Envy.  It is in Synaptic.  It will install the correct drivers for you automatically and configure everything--painlessly with nothing to think about.

Maybe you have an old beater computer that is not worth putting anything into.  But if you do decide to get a new video card Nvidia is the best.  Though they are closed source, that their drivers may not offer support in the future is only hypothetical. The fact is, as reflected by the original subject of this thread they work better than anything else.

They work better for pure gaming power, yes.  Some people don't care about that.  In fact, I would wager most don't.  Some people just want the graphics to work, and intel and ati/amd do that.

And to be completely honest, the newer ati/amd proprietary drivers are pretty equal in performance with the 173 era nvidia drivers (haven't seen benchmarks with the 180 drivers), and are still rapidly improving.

I don't think it is accurate to say 'nvidia is the best' as a blanket statement.  For some, it is the best.  However this is not universally true.

---

### Post by laceration on 2009-01-05
> They work better for pure gaming power, yes. Some people don't care about that. In fact, I would wager most don't. Some people just want the graphics to work, and intel and ati/amd do that.

And to be completely honest, the newer ati/amd proprietary drivers are pretty equal in performance with the 173 era nvidia drivers (haven't seen benchmarks with the 180 drivers), and are still rapidly improving.

I don't think it is accurate to say 'nvidia is the best' as a blanket statement. For some, it is the best. However this is not universally true.
What you are saying is not off the mark, even though every time there is a "Ati or Nvidia?" thread in these forums it comes out convincingly Nvidia.  Why I wrote what I did is because of the 180 drivers.  When these make it upstream it will make a big difference and not for gamers necessarily but for anybody who watches video.  You can read about them at [www.phoronix.com](www.phoronix.com).

---

### Post by MisterFlibble84 on 2009-01-05
> **igknighted said:**
> Don't blame Ubuntu, blame nvidia.  By using nvidia, you are completely at the mercy of what they want to make drivers for.  Intel, on the other hand, uses completely open source drivers so the community can continue supporting the card.  Even AMD/ATI releases specs for their cards so the community can make drivers to keep a card usable long beyond its support in the official drivers.

With your nvidia card, you will have to use the legacy drivers.  You will still be able to use them for 3d support as long as that driver still works with the Xorg release being used, but with these proprietary graphics, you just can't be guaranteed that support will last forever.

You can use Intel drivers if you use some slow integrated motherboard video.

You can use the open source Radeon driver if you want bad performance and maybe nothing but 2d on their latest cards.

Or you can just use Nvidia and have it work with their driver.

Now good choices, but at least Nvidia works.

---

### Post by Valok on 2009-01-05
Well I've run into a bit of a problem.  After using this script to install the driver, my video settings are basically crap.

I can't change the resolution to anything higher than 800x600 and I can't turn on any of my desktop effects.  I just keep getting a message saying that the effects couldn't be enabled or that the size is not supported.

Any suggestions?

---

### Post by forrestcupp on 2009-01-05
> **igknighted said:**
> They work better for pure gaming power, yes.  Some people don't care about that.  In fact, I would wager most don't.  Some people just want the graphics to work, and intel and ati/amd do that.

And to be completely honest, the newer ati/amd proprietary drivers are pretty equal in performance with the 173 era nvidia drivers (haven't seen benchmarks with the 180 drivers), and are still rapidly improving.

I don't think it is accurate to say 'nvidia is the best' as a blanket statement.  For some, it is the best.  However this is not universally true.

ATI is a decent choice if you don't care about running Compiz. AFAIK they still haven't worked out the issues where videos and opengl apps, screensavers and games flicker obnoxiously if Compiz or any compositing is turned on.  Nvidia worked that out a long time ago, and I don't care if some people consider it a hack; it works.

Because AMD released their specs for open source development, ATI may be a better choice sometime in the distant future.  But for now, nvidia is a lot less of a pain in Linux.  I had a decent ATI card and I pulled it out and bought an equivalent nvidia card because I was tired of dealing with it.  I've never been sorry that I did that.

---

### Post by sbentjies on 2009-01-05
The FX-5200 should work as a base-level card. I'm not using the system for gaming. What bothers me is that this probably qualifies as a legacy card. In that case, I need to make sure the legacy drivers are enabled either throught the harware manager and/or through the synaptics manager. What is really sticking in my craw is that I don't believe that xorg.conf is properly reflecting my monitor or card, or resolution. Is there a way to craft an xorg.conf that will reflect my particular hardware, other than do it line for line? I have a Sony CPD-17F13 branded for Gateway as a Vivitron 1776 and the GEForce FX-5200. This is an off the shelf nvidia chipset made by EVGA.

---

### Post by sbentjies on 2009-01-05
> **laceration said:**
> If you are dedicated enough to play with the new beta drivers, can't you scrape together $30 for a new video card?  I don't know where you are, but here in the U.S. there are all kinds of deals for 7000 series cards and up.  You can't expect much from a FX-5200.
The FX-5200 is an off the shelf 8x AGP card, built by EVGA with an NVIDIA chipset. It may be considered legacy for 8.04 but I don't know for sure. I'm most concerned with the stripped out xorg.conf file. I have a Sony (branded for Gateway) CPD-17F13 monitor and the EVGA Nvidia card. I would like to have a utility that will help build the xorg.conf without going line by line if I can. Legacy drivers are the default after bulletproof X strips out xorg.conf so I can boot back into x. If I have to go into the synaptics package mananger and allow this again, I will 8.04 is just not detecting the card and I think it's a driver issue. Somebody please set me back on track.

Thanks,

---

### Post by sbentjies on 2009-01-05
> **forrestcupp said:**
> ATI is a decent choice if you don't care about running Compiz. AFAIK they still haven't worked out the issues where videos and opengl apps, screensavers and games flicker obnoxiously if Compiz or any compositing is turned on.  Nvidia worked that out a long time ago, and I don't care if some people consider it a hack; it works.

Because AMD released their specs for open source development, ATI may be a better choice sometime in the distant future.  But for now, nvidia is a lot less of a pain in Linux.  I had a decent ATI card and I pulled it out and bought an equivalent nvidia card because I was tired of dealing with it.  I've never been sorry that I did that.
So far I would give a thumbs down to anyone thinking of running less than the newest nvidia card on Ubuntu. I would venture to say that a lot of people are running older cards because the system is one that WILL run Linux well such as my Dell GX-150 with an AGP video slot. The whole point was to put Linux on it. That said, is there a utility that will allow you to configure the Xserver? My attempts to get the card detected and working within gnome have been futile. It doesn't see the card.

---

### Post by sbentjies on 2009-01-05
> **sbentjies said:**
> The FX-5200 is an off the shelf 8x AGP card, built by EVGA with an NVIDIA chipset. It may be considered legacy for 8.04 but I don't know for sure. I'm most concerned with the stripped out xorg.conf file. I have a Sony (branded for Gateway) CPD-17F13 monitor and the EVGA Nvidia card. I would like to have a utility that will help build the xorg.conf without going line by line if I can. Legacy drivers are the default after bulletproof X strips out xorg.conf so I can boot back into x. If I have to go into the synaptics package mananger and allow this again, I will 8.04 is just not detecting the card and I think it's a driver issue. Somebody please set me back on track.

Thanks,
I just bought the FX-5200 because it is a half-height AGP card and I thought it would play ball with 8.04 . I dropped $40 on it

---

### Post by forrestcupp on 2009-01-05
> **sbentjies said:**
> So far I would give a thumbs down to anyone thinking of running less than the newest nvidia card on Ubuntu. I would venture to say that a lot of people are running older cards because the system is one that WILL run Linux well such as my Dell GX-150 with an AGP video slot. The whole point was to put Linux on it. That said, is there a utility that will allow you to configure the Xserver? My attempts to get the card detected and working within gnome have been futile. It doesn't see the card.

Configuring xorg.conf is a thing of the past.  Did you try using Envy to set up your nvidia?  If you can't get it to work, try Envy.  First, uninstall all the proprietary nvidia stuff you already have installed
```
sudo apt-get remove --purge nvidia*
```
Then install Envy
```
sudo apt-get install envyng-gtk
```Then you should be able to find Envy in your applications menu.  Envy will download the right drivers for you, install them, and set everything up.

**But before you do that**, you could look in your xorg.conf
```
gksudo gedit /etc/X11/xorg.conf
```
Then look in the 'Device' section and make sure the driver is **nvidia** rather than **nv**.

---

### Post by igknighted on 2009-01-05
> **forrestcupp said:**
> ATI is a decent choice if you don't care about running Compiz. AFAIK they still haven't worked out the issues where videos and opengl apps, screensavers and games flicker obnoxiously if Compiz or any compositing is turned on.  Nvidia worked that out a long time ago, and I don't care if some people consider it a hack; it works.

Because AMD released their specs for open source development, ATI may be a better choice sometime in the distant future.  But for now, nvidia is a lot less of a pain in Linux.  I had a decent ATI card and I pulled it out and bought an equivalent nvidia card because I was tired of dealing with it.  I've never been sorry that I did that.

Hmm, thats odd.  My experiences were always the opposite.  I ditched my ATI x800 which worked like a charm with the radeon driver, as well as the fglrx driver, for an 8600gt and have regretted it ever since (never worked with nv, but every distro thought it would, not to mention way to many bugs in the nvidia drivers).

> The FX-5200 is an off the shelf 8x AGP card, built by EVGA with an NVIDIA chipset. It may be considered legacy for 8.04 but I don't know for sure. I'm most concerned with the stripped out xorg.conf file. I have a Sony (branded for Gateway) CPD-17F13 monitor and the EVGA Nvidia card. I would like to have a utility that will help build the xorg.conf without going line by line if I can. Legacy drivers are the default after bulletproof X strips out xorg.conf so I can boot back into x. If I have to go into the synaptics package mananger and allow this again, I will 8.04 is just not detecting the card and I think it's a driver issue. Somebody please set me back on track.

Some stores may still sell the fx-5200, but that is a 10 year old chip.  Also, a quick check of the nvidia website would tell you that they no longer support (with the latest drivers) cards below the 6000 series.

If you want support for your graphics issues, please open a thread in one of the support forums (beginners, general, etc.).  The cafe is for general musings, not support.  You'll have better luck getting help in another section.

---

### Post by sbentjies on 2009-01-05
Ok, will do-I guess I found this thread via a google search. I am on the board in the absolute beginner section. Thanks for your help.

JP

---

### Post by sbentjies on 2009-01-05
Ok, will do-I guess I found this thread via a google search. I am on the board in the absolute beginner section. Thanks for your help.

JP

---

### Post by Trap3d on 2009-01-11
Thanks i o u big time b4 i couldnt install cuz it didnt have a kernel module but now it worked like charm and definately no trouble like xserver being on, etc... Tnx

---

### Post by hebetude on 2009-01-15
The 180.22 drivers have been added to jaunty.  They are under restricted not universe, please update.

```
deb [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) jaunty main restricted
```

---

### Post by sofasurfer on 2009-01-16
I followed the steps in post #1. It did not work. There is no 180 driver mentioned in sys>admin>hardware-drivers. Advanced desktop effects could not be enabled. 

What do I have to do to revert back? Just sudo apt-get remove nvidia-glx-180

---

### Post by cryogenics on 2009-01-26
Ubuntu 8.10 Ibex with Nvidia 9400GT works fine
The 2d and open GL Screen savers are better for me now.
as well as application stuff ;)
No problems so far
Actually a little less coruption with the mmorpg wow ;)
:popcorn:

I also Checked it with the Cedega diag and that works aswell ;)
Wine works as well

They need to fix Ubuntu to show drivers on system installed not just what it wants to show
through the package manager.

Then someone needs to make all drivers avalible Via various websites
Like a Video driver website-Printer website-Motherboard-Sound etc.. with
Packages listed for download :)

all visual Desktop effects work as well.

Thank you.

---

### Post by sbentjies on 2009-01-26
Are you using the proprietary drivers or the Nvidia drivers and what's the difference? I had trouble with xorg.conf when I tried to load the proprietary drivers-I think it saw that my xorg.conf was configured for the nvidia drivers. Halp please

---

### Post by simtaalo on 2009-01-27
i tried to install 180.22 drivers on my new install, i had some problems so uninstalled all my nvidia stuff and tried again but still got errors

```
 sudo apt-get install nvidia-glx-180
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  nvidia-180-kernel-source
The following NEW packages will be installed
  nvidia-180-kernel-source nvidia-glx-180
0 upgraded, 2 newly installed, 0 to remove and 880 not upgraded.
Need to get 0B/18.6MB of archives.
After this operation, 60.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  nvidia-180-kernel-source nvidia-glx-180
Authentication warning overridden.
Selecting previously deselected package nvidia-180-kernel-source.
(Reading database ... 137087 files and directories currently installed.)
Unpacking nvidia-180-kernel-source (from .../nvidia-180-kernel-source_180.22-0ubuntu2_amd64.deb) ...
Unpacking nvidia-glx-180 (from .../nvidia-glx-180_180.22-0ubuntu2_amd64.deb) ...
dpkg-divert: mismatch on divert-to
  when removing `diversion of /usr/lib32/libGL.so.1.2 to /usr/lib32/nvidia/libGL.so.1.2.xserver-xorg-core by nvidia-glx-177'
  found `diversion of /usr/lib32/libGL.so.1.2 to /usr/lib32/nvidia/libGL.so.1.2.xlibmesa by nvidia-glx-177'
dpkg-divert: `diversion of /usr/lib32/libGL.so.1.2 to /usr/lib32/nvidia/libGL.so.1.2.xlibmesa by nvidia-glx-180' clashes with `diversion of /usr/lib32/libGL.so.1.2 to /usr/lib32/nvidia/libGL.so.1.2.xlibmesa by nvidia-glx-177'
dpkg: error processing /var/cache/apt/archives/nvidia-glx-180_180.22-0ubuntu2_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-180_180.22-0ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

any idea how to fix?

---

### Post by fjf on 2009-01-28
It seems there is now an easier way for installing 180.11:  [http://ubuntuforums.org/showpost.php?p=6632383&postcount=377](http://ubuntuforums.org/showpost.php?p=6632383&postcount=377)

---

### Post by simtaalo on 2009-01-28
lol i ended up having to reinstall my system for another reason anyway (been doing that far too often recently) although think i've got things just the way i like them, well til i tinker some more.

got 180.22 installed and on startup the left hand side of the screen has the right hand border there, but if i load up nvidia-settings it fixes without actually doing anything other than loading the program. not sure what is wrong with it, i have 180.25 on my fedora partition and thats just perfect.

---

### Post by crjackson on 2009-02-11
> **fjf said:**
> It seems there is now an easier way for installing 180.11:  [http://ubuntuforums.org/showpost.php?p=6632383&postcount=377](http://ubuntuforums.org/showpost.php?p=6632383&postcount=377)

Interesting - I'll try that this weekend.

---

### Post by crjackson on 2009-02-12
Couldn't wait for the weekend. Backed up my HD and went for it.  Seems to be working perfectly. Too soon to tell if any performance gains were netted.

---

### Post by forcecore on 2009-02-12
why all is messing with some apt things if you can download installer (NVIDIA-Linux-xXX-xx.xx.pkg1.run) from nvidia then follow instructions.

---

### Post by Kevbert on 2009-02-12
This method works fine in installing 180.29 on Hardy. If anyone else tries take a look at post #1 and post #51. Thanks fjf that's what I've been looking for.:P:P:P

---

### Post by argie on 2009-02-12
Has anyone here tried this on an amd64 version? I did, with disastrous results. I can now only login to X if I use vesa and I have a 640×480 resolution screen despite having removed the nvidia-glx-180 and all dependencies and reinstalling the nvidia-glx-new package.

For the record, I have a Dell XPS M1330 with an 8400M GS.

I eventually managed to fix the problem by removing the modules in /lib/modules/(kernel-version)/volatile/ or something like that. I now have the 180.29 driver and though it seems smoother, there's artifacting here and there, but I'm too scared to go back.

---

### Post by Sealbhach on 2009-02-14
> **argie said:**
> 

I eventually managed to fix the problem by removing the modules in /lib/modules/(kernel-version)/volatile/ or something like that. I now have the 180.29 driver and though it seems smoother, there's artifacting here and there, but I'm too scared to go back.

Hi,
I tried installing 180.29 amd64 version but it didn't work. The install all seemed to go OK but then it said it couldn't find the kernel module and put me in low graphics mode. I've gone back to 180.22. Anyone know how to fix it?


.

---

### Post by sandy8925 on 2009-03-07
The 180.11 drivers are available through the repository itself for Intrepid. Just use:

sudo apt-get install nvidia-glx-180

---

### Post by Kareeser on 2009-03-07
I installed 180.29 on my AMD64 (actually, EMT64) system. Installation went smoothly, no problems :)

---

### Post by fjf on 2009-03-08
> **Kevbert said:**
> This method works fine in installing 180.29 on Hardy. If anyone else tries take a look at post #1 and post #51. Thanks fjf that's what I've been looking for.:P:P:P

Updated repo in first post, just in case anyone wants to use it.

---

### Post by ozzyprv on 2009-03-08
> **fjf said:**
> It seems there is now an easier way for installing 180.11:  [http://ubuntuforums.org/showpost.php?p=6632383&postcount=377](http://ubuntuforums.org/showpost.php?p=6632383&postcount=377)

Installing right now....will report how it went later.

EDIT: Working fine - in 8.10 - so far.

---

