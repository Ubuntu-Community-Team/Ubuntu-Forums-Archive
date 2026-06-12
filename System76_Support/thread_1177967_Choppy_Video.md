---
title: "Choppy Video"
date: 2009-06-04
forum: System76 Support
---

### Post by MarkID on 2009-06-04
After (belated) upgrade to Jaunty on Daru1, I have choppy Flash video (Hulu, YouTube, etc.)  Everything else seems to be working fine. Any thoughts.

---

### Post by thomasaaron on 2009-06-04
Is it choppy with desktop effects turned off? (System > Prefs > Appearance > Visual Effects > None)

Is it choppy if you go to a terminal and run...

gstreamer-properties

...and click the Video tab and set the Default Output Plugin to 'X Window System (no XV)'?

---

### Post by MarkID on 2009-06-04
> **thomasaaron said:**
> is it choppy with desktop effects turned off? (system > prefs > appearance > visual effects > none)

yes.


Is it choppy if you go to a terminal and run...

Gstreamer-properties

...and click the video tab and set the default output plugin to 'x window system (no xv)'?

yes

---

### Post by thomasaaron on 2009-06-04
Open a browser and type this in the URL bar...

```
about:plugins
```

What version of flash player are you using?

---

### Post by MarkID on 2009-06-04
> **thomasaaron said:**
> open a browser and type this in the url bar...

```
about:plugins
```

what version of flash player are you using?

10

---

### Post by thomasaaron on 2009-06-04
Is it choppy only in full-screen mode or also in... "reduced?" screen mode?

---

### Post by MarkID on 2009-06-04
> **thomasaaron said:**
> Is it choppy only in full-screen mode or also in... "reduced?" screen mode?

Both.  Also in Hi-Res and Std-Res.  I let the buffer "load up,"  I close other apps. I've done all of the obvious.  I'm thinking it might just be my Internet connection, but that wasn't a problem three days ago.  Maybe my computer is telling me to watch fewer videos and do more work.

---

### Post by thomasaaron on 2009-06-04
Try resetting your router and/or modem.

---

### Post by MarkID on 2009-06-04
> **thomasaaron said:**
> Try resetting your router and/or modem.

Still choppy.  One thing that may be relevant, is that the processors seem to be working harder than before.  Even at idle, with no video or taxing apps running, the CPUs are running in the double digits percentage.

---

### Post by thomasaaron on 2009-06-05
Good chance that has something to do with it. Go to System > Administration > System Monitor > Processes and see what processes are hogging the cpu.

---

### Post by MarkID on 2009-06-05
> **thomasaaron said:**
> Good chance that has something to do with it. Go to System > Administration > System Monitor > Processes and see what processes are hogging the cpu.

This is weird.  The cpu hog seems to be the system monitor itself ("gnome-system-monitor.")  I used to leave the system monitor applet open in the panel, but now I've deleted it.  But the system monitor processes tab indicates that the system monitor is still using 10% to 20 % CPU, and the resources tab still indicates that the CPUs are running 20% to 50%, with spikes as high as 75%.  Again, I have no video or taxing apps open (that I know of.)  Can I end the gnome-system-monitor process safely?

---

### Post by thomasaaron on 2009-06-05
Probably. But try shutting down System Monitor and going to a terminal and running...

top

...and see if System Monitor is still the hog. If it is, open another terminal and run...

killall gnome-system-monitor

...and then watch top and see what else is hogging the cpu (if anything).

Does Flash play well now?

If so, reboot and see if there is a gnome-system-monitor process going in top.

---

### Post by MarkID on 2009-06-05
> **thomasaaron said:**
> Probably. But try shutting down System Monitor and going to a terminal and running...

top

...and see if System Monitor is still the hog. If it is, open another terminal and run...

killall gnome-system-monitor

...and then watch top and see what else is hogging the cpu (if anything).

Does Flash play well now?

If so, reboot and see if there is a gnome-system-monitor process going in top.

OK, I get it.  When System Manager is running, then System Manager was the hog.  In "top," it didn't even show up, so no reason to kill it.  No other hogs -- Firefox tops out at 6%-7%.  Nothing else is that close.   Video still choppy on various sites.  I think this may just be a mystery, but I'd welcome other ideas.  Machine still *feels* likes it's running hot, but no numbers to confirm that.  Thanks for your help.

---

### Post by thomasaaron on 2009-06-05
Try re-installing flash...

sudo apt-get --purge remove flashplugin-*
sudo apt-get install flashplugin-installer

Then restart your browser.

---

### Post by MarkID on 2009-06-05
> **thomasaaron said:**
> Try re-installing flash...

sudo apt-get --purge remove flashplugin-*
sudo apt-get install flashplugin-installer

Then restart your browser.

No change.  I think my next step will be to try another network.  Maybe, it is the Internet connection.

---

### Post by Azati Prime on 2009-06-07
I have this problem in Hulu as well.  In windows I would get choppy video if I used fullscreen but in Ubuntu I'm getting tearing all the time and occasional dips in flash video frame rate.  Youtube doesn't get any tearing but it does feel sluggish in HQ and the CPU usage for Firefox somehow gets up to over 100%.  I have a 2.2GHz Core2 Duo and an nVidia 8600M GT.

---

### Post by Benboom on 2009-06-07
The default System Monitor in 9.04 is preposterous. I had never used Ubuntu until about a month ago and I installed it on an old machine; I thought, "This is great, but I'd like to have a monitor running so I know what's going on" and I discovered that the System Monitor ALWAYS does this - at least on my setup. It's rather like a brain surgeon operating on his own brain, it's so recursive. I read some more and switched to Conky and problem solved.

---

### Post by MarkID on 2009-06-07
> **Azati Prime said:**
> I have this problem in Hulu as well.  In windows I would get choppy video if I used fullscreen but in Ubuntu I'm getting tearing all the time and occasional dips in flash video frame rate.  Youtube doesn't get any tearing but it does feel sluggish in HQ and the CPU usage for Firefox somehow gets up to over 100%.  I have a 2.2GHz Core2 Duo and an nVidia 8600M GT.

Hulu, YouTube, Crackle . . . all the same.  They were fine until about the time I upgraded.  Coincidence or not? Still working on it.

---

### Post by mantelo on 2009-06-07
I've got the same problem.

Since I upgraded to Jaunty (fresh install) I get chopy flash video. My system is Athlon X2 1.9 GHz, 2 GB RAM, nvidia chipset 6150 LE, Ubuntu 9.04 32 bits.

---

### Post by caeroe on 2009-06-07
> **mantelo said:**
> I've got the same problem.

Since I upgraded to Jaunty (fresh install) I get chopy flash video. My system is Athlon X2 1.9 GHz, 2 GB RAM, nvidia chipset 6150 LE, Ubuntu 9.04 32 bits.

I'm probably not helping much, but it could be Nvidia. I've tried everything imaginable to get fullscreen flash to work at an acceptable level on my desktop.

Ubuntu 9.04 64bit with same plugins, Firefox, medium desktop effects:

An old Gateway notebook, 2.2ghz AMD64 bit, 1GB ram, and a 64MB dedicated ATI card.  Result?  Flash runs perfect, including Hulu at fullscreen.

On my newer dual core desktop, with 4gb of ram and a 512mb Nvidia 8800GT card.  Fullscreen flash is downright horrible here.  I dual boot this desktop, and it's fine in Win 7 64bit.

---

### Post by jbraswell on 2009-06-09
I'm having the same problem, but it's has only been since my last update-manager-prompted update.  Before that, Flash on Jaunty was working fine.  

When I play a flash video, top shows xorg taking up 98% of one of my CPUs.  

There's got to be an easy fix for this? What was in the last update?

---

### Post by thomasaaron on 2009-06-09
Hi, jbraswell. I think this is a flash bug. I'm working on it right now with a Wild Dog in my shop. What system are you using, and what kind of graphics card?

For the rest of you guys, if you reboot your system does flash play well for a little while before becoming choppy? Or is it choppy from the get-go?

---

### Post by jbraswell on 2009-06-09
Yes, you are correct, it does take a while to start happening after reboot.  

I'm on a Wild Dog with the ATI 4830 video card.  

Thanks!

---

### Post by Saganite on 2009-06-09
Same problem here.  Fresh install of 9.04, nvidia 185 drivers.   However, I have found a workaround, if not an optimal one.  This problem seems to be flash itself.  If you lower the flash quality setting to low the problem goes away in full screen.   Loose a bit of quality but it's not that noticeable.

---

### Post by thomasaaron on 2009-06-09
OK, I'm testing on a Wild Dog with ATI graphics too.

What do you mean 'lower the flash quality setting?'

---

### Post by kilgor3 on 2009-06-10
I have the same exact problem.  This seems to be a problem that ALOT of people are having.  My problem exists on 3 systems.  1 with ati, one with geforce and one with intel video cards.  The problem started for me with the release of 8.04. I can't find a fix that works.  I think it has something to do with the way X talks to the flash plugin or vice versa maybe?  This only happens with certain video cards.  I have a 4th grforce system where everything works fine.
I've tried alot of "fixes", with no results.

If you ever fix it please share your secret.  I'm debating giving up on Ubuntu based distro's all together if I cant fix this soon.  It's a thorn that has been in my side for more than a year now.

---

### Post by thomasaaron on 2009-06-10
Hey, guys. Try installing the *actual* 64-bit plugin from Adobe. So far, I'm running it with no freezes.

First run...
sudo apt-get --purge remove flashplugin-*
sudo apt-get remove nspluginwrapper

Then, follow the first five instructions here...
[http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/](http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/)

Does that work for you?

---

### Post by caeroe on 2009-06-10
> **thomasaaron said:**
> Hey, guys. Try installing the *actual* 64-bit plugin from Adobe. So far, I'm running it with no freezes.

First run...
sudo apt-get --purge remove flashplugin-*
sudo apt-get remove nspluginwrapper

Then, follow the first five instructions here...
[http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/](http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/)

Does that work for you?

I've installed the 64bit alpha before, it's still incredibly choppy.  Flash is fine on my much older notebook with an ATI 64mb dedicated card, but my desktop simply cannot play fullscreen flash.  

So is it really Nvidia's problem?  Jaunty 64bit, Firefox 3.0.10, medium desktop settings, pulse audio, etc.  The difference is that my newer desktop has a 512mb 8800GT card in it.

I simply cannot watch any fullscreen flash videos on my desktop PC.  I have to boot Windows.

Edit:  Well I give up again, there's no way I'll ever watch Flash videos (reasonably) in Ubuntu.  I was planning on buying a netbook with Linux pre-loaded.  No way I am now, so I'm getting one with WinXP installed, that way I can do something simple as watch Youtube.

---

### Post by jdb on 2009-06-10
> **caeroe said:**
> I've installed the 64bit alpha before, it's still incredibly choppy.  Flash is fine on my much older notebook with an ATI 64mb dedicated card, but my desktop simply cannot play fullscreen flash.  

So is it really Nvidia's problem?  Jaunty 64bit, Firefox 3.0.10, medium desktop settings, pulse audio, etc.  The difference is that my newer desktop has a 512mb 8800GT card in it.

I simply cannot watch any fullscreen flash videos on my desktop PC.  I have to boot Windows.

Edit:  Well I give up again, there's no way I'll ever watch Flash videos (reasonably) in Ubuntu.  I was planning on buying a netbook with Linux pre-loaded.  No way I am now, so I'm getting one with WinXP installed, that way I can do something simple as watch Youtube.

Something like this that is a regression that affects a lot of users usually gets fixed sooner than later.

jdb

---

### Post by kilgor3 on 2009-06-10
> **jdb said:**
> Something like this that is a regression that affects a lot of users usually gets fixed sooner than later.

jdb

It's been affecting me for over a year now, on both 64 and 32 bit systems, over 3 computers with 3 different GFX cards.

---

### Post by Saganite on 2009-06-10
> **thomasaaron said:**
> OK, I'm testing on a Wild Dog with ATI graphics too.

What do you mean 'lower the flash quality setting?'

When you are playing a video in flash and right click on it it should give you a menu, one of the options being Quality Setting.  Gives you low, medium, and high.   Settling it to low smoothed it out for me, however I am running the 64 bit 10,0,22,87 version...and to install it follow the instructions listed in the post a few down from yours.  If I try to use the plugin synaptic installs lowering the quality seems to have limited to no effect.

---

### Post by thomasaaron on 2009-06-11
Ah, I see. Thank you for clarifying.

---

### Post by Happy_Pangolin on 2009-06-11
> **thomasaaron said:**
> Hi, jbraswell. I think this is a flash bug. I'm working on it right now with a Wild Dog in my shop. What system are you using, and what kind of graphics card?

For the rest of you guys, if you reboot your system does flash play well for a little while before becoming choppy? Or is it choppy from the get-go?

On a brand new Pangolin w/ 9.04 Jaunty, Flash video play smoothly after boot.  However, if I close the lid and have it hibernate, then open ... WHAMMO!  Coopy video until the next reboot.  Most Flash video sites are affected and become choppy to watch, but sometimes Youtube is ok.  Weird.

But a reboot fixes it.  I used both wireless and eth0 hardwire connection to a 5 Mb internet link.

So wonder why a suspend/hibernate would cause this?  How does this relate to workstations?  Maybe when the nVidia is turned off for screen saver, somehow has a bad Flash reaction upon awakening?

Really weird.

---

### Post by thebacotman on 2010-09-15
[SOLVED]
I had the same problem.
- Choppy Flash on full screen, regardless the source.
- Choppy AVI on full screen

I tried
```
$ gstreamer-properties
```

the go to video > Default Output > from Auto to X Windows System (No XV)
So
Auto : Choppy
X Window System (No XV) : GOOD
X Window System (X11/XShm/XV): Choppy

So you might want to try that
Anyway, in case you need it my system is:

Dell Inspiron 1505
3GB DDR2 800 Ghz
Ati Radeon X1400
15.4 1680x1050
Intel Core 2 Duo T7200 2.0GHz

---

### Post by Damiox on 2010-11-08
same here on intel . never had this problem in hardy :) all vids were smooth as silk, even just 512 ram . flippin flash and lucid do not like each other . ill try this ' fix ' when i get home :) now we need a linux hack for phones  :) boot up ubuntu moto

---

### Post by salterlee on 2011-09-24
Thanks thebacotman, your instructions solved it for me too!!

---

