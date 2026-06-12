---
title: "Blocky graphics in Hardy"
date: 2009-12-23
forum: System76 Support
---

### Post by tomasterisk on 2009-12-23
I looked in the archives but couldn't quite find the problem I am experiencing.

I am running my **Ratel Value** **dual-booted** (**Jaunty** and **Hardy**). I added Hardy because I was still getting some freezes in Jaunty and there are times - most of the time - I just need to get things done on the computer. But now I have a little time and would like to solve this.

The problem is that in some websites like BBC and Facebook the graphics look somewhat choppy (pixelly). Also, some of the games, like lbreakout2 and Anagramarama, produce - after just a few seconds - *weird greenish backlit graphics.*

Any ideas?

---

### Post by thomasaaron on 2009-12-26
Hi, Tom.

1. Does it happen if you turn off Desktop effects (System > Prefs > Appearance > Visual Effects > None)?

2. Can you capture the problem in a screenshot (Apps > Accessories > Take Screenshot)?

---

### Post by tomasterisk on 2009-12-26
> **thomasaaron said:**
> Hi, Tom.

1. Does it happen if you turn off Desktop effects (System > Prefs > Appearance > Visual Effects > None)?

2. Can you capture the problem in a screenshot (Apps > Accessories > Take Screenshot)?

Hello Tom,

1. The "none" setting is the only one possible for me.

2. I just took the shot of my FB page. The pic of me is pixelated more than it should be. For some reason other sites, like Flickr, do not have this problem with same picture.

Update: Apparently the png. didn't upload. Maybe it is because I am  in the process of uploading a video elsewhere. I will upload the screenshot in a little while.

---

### Post by tomasterisk on 2009-12-26
Something else. I seem to remember that these problems started after I attempted to upgrade to Karmic. Could there have been some basic setting (video card perhaps?) that was changed that needs to be reset?

*[COLOR=DarkGreen]**[COLOR=Navy]Update:[/COLOR] No color bars or static seen in hardware testing. Am I missing the use of my Radeon?**[/COLOR]*

---

### Post by tomasterisk on 2009-12-26
Here is the screenshot.

---

### Post by tomasterisk on 2009-12-28
Update: As far as I can tell the Jaunty part of my dual-boot problem is solved. The graphics problem *there* are now improved - I can tell by the return of those high-res screen savers. As far as I can see the improvement happened when I did the hardware testing: The first time the vid (color bars) tst failed, but on the repeat it *worked*. And has been working ever since.

The problems at Hardy are still unsolved, but I am through with waiting on that.

---

### Post by thomasaaron on 2009-12-28
Hi, Tom.

Go to System > Administration > Hardware Drivers and make sure your ATI driver is enabled.

You may need to reboot afterwards.

---

### Post by tomasterisk on 2009-12-30
> **thomasaaron said:**
> Hi, Tom.

Go to System > Administration > Hardware Drivers and make sure your ATI driver is enabled.

You may need to reboot afterwards.

I have "Atheros Hardware Access Layer (HAL)" and "Support for Atheros 802.11 Wireless LAN Cards" listed. It is all proprietary from System76, I assume.

---

### Post by thomasaaron on 2009-12-30
> I have "Atheros Hardware Access Layer (HAL)" and "Support for Atheros 802.11 Wireless LAN Cards" listed. It is all proprietary from System76, I assume.

No, that is just what Ubuntu is recommending to support your wireless card. It's OK to enable it, if it's not already enabled.

But, according to your account, you should have a 512 MB ATI Radeon 4350 graphics card in your system. 

There should be a driver for that in the list. (?)

---

### Post by tomasterisk on 2009-12-30
> **thomasaaron said:**
> No, that is just what Ubuntu is recommending to support your wireless card. It's OK to enable it, if it's not already enabled.

But, according to your account, you should have a 512 MB ATI Radeon 4350 graphics card in your system. 

There should be a driver for that in the list. (?)

It is not listed there.

---

### Post by thomasaaron on 2009-12-30
OK. That's our problem.

Try running...

sudo apt-get install xserver-xorg-video-radeon fglrx-amdcccle

Once all of that is finished, reboot.

Fixed?

If not, go to System > Administration > Hardware Drivers and make sure the ATI driver is activated. (It should be there now.)

---

### Post by tomasterisk on 2009-12-31
> **thomasaaron said:**
> OK. That's our problem.

Try running...

sudo apt-get install xserver-xorg-video-radeon fglrx-amdcccle

Once all of that is finished, reboot.

Fixed?

If not, go to System > Administration > Hardware Drivers and make sure the ATI driver is activated. (It should be there now.)

The terminal had this:
Couldn't find package xserver-xorg-video-radeon

---

### Post by thomasaaron on 2009-12-31
Oh, shoot! That's right, you're running 8.04!

Do the first part of Method 1 on this tutorial...

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

You probably won't need the "Post Installation Tweaks" section.

---

### Post by tomasterisk on 2009-12-31
> **thomasaaron said:**
> Oh, shoot! That's right, you're running 8.04!

Do the first part of Method 1 on this tutorial...

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

You probably won't need the "Post Installation Tweaks" section.

What I get when I did the above was this:
$ sudo apt-get update
bash: $: command not found
tom@tom-my:~$ 
tom@tom-my:~$ $ sudo apt-get install linux-restricted-modules-generic restricted-manager
bash: $: command not found
tom@tom-my:~$ 
tom@tom-my:~$ $ sudo apt-get install xorg-driver-fglrx
bash: $: command not found
tom@tom-my:~$ 
tom@tom-my:~$ $ sudo depmod -a

---

### Post by thomasaaron on 2009-12-31
That's a horse of a different color. All of those are legitimate commands that should be present on every Ubuntu system.

Try rebooting your system and running them.

Are you in your primary account? If not, log into it and try again.

---

### Post by tomasterisk on 2009-12-31
> **thomasaaron said:**
> That's a horse of a different color. All of those are legitimate commands that should be present on every Ubuntu system.

Try rebooting your system and running them.

Are you in your primary account? If not, log into it and try again.

I tried to do it again but a strange thing happened. The first two lines of commands seemed to work but then the console gave an error message. I was stuck at that point. I wasn't even able to access the terminal or to turn off the computer (restart and shut down were not even listed as options from the "green running man" in the top right corner.

But when I switched users it just restarted. Now everything seems normal - but still blocky.

One of the messages at one point was that I needed the CD. I put it in but didn't hear it being accessed. Should that matter? Or should I try to do all of this from *within* that CD?

---

### Post by thomasaaron on 2009-12-31
You can go to System > Administration > Software Sources and disable the CD. Then run...

sudo apt-get update

...followed by the tutorial I sent you.

Did that make any difference?

---

### Post by tomasterisk on 2009-12-31
> **thomasaaron said:**
> You can go to System > Administration > Software Sources and disable the CD. Then run...

sudo apt-get update

...followed by the tutorial I sent you.

Did that make any difference?

Seems to be a glitch at line two:

t[COLOR=DarkGreen]om@tom-my:~$ sudo apt-get install linux-restricted-modules-generic restricted-manager 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-restricted-modules-generic is already the newest version.
Package restricted-manager is a virtual package provided by:
  jockey-gtk 0.3.3-0ubuntu8.2
[COLOR=Indigo]You should explicitly select one to install.
E: Package restricted-manager has no installation candidate[/COLOR]
[/COLOR]

---

### Post by thomasaaron on 2009-12-31
OK, go back to Software Sources, and make sure the line that has "restricted" in its description is selected. 

Also, under the "Updates" tab, just go ahead and make sure everything there is selected as well. It sounds like the right repository isn't enabled.

Then run...

sudo apt-get update

...and try the tutorial again.

---

### Post by tomasterisk on 2009-12-31
> **thomasaaron said:**
> OK, go back to Software Sources, and make sure the line that has "restricted" in its description is selected. 

Also, under the "Updates" tab, just go ahead and make sure everything there is selected as well. It sounds like the right repository isn't enabled.

Then run...

sudo apt-get update

...and try the tutorial again.

I did the updating of sources. The following window came up (see attachment).

 I will do the rest a little later, when I get back to this. Thank you for all the help so far.

---

### Post by tomasterisk on 2009-12-31
Hmmm. Attachment didn't attach!

---

### Post by tomasterisk on 2010-01-01
> **tomasterisk said:**
> I did the updating of sources. The following window came up (see attachment).

 I will do the rest a little later, when I get back to this. Thank you for all the help so far.

I have a question what exactly I do with these instructions from the tutorial:

[COLOR=DarkGreen]In the device section, if it is not already there add: 
[/COLOR]     [SIZE=-1][COLOR=DarkGreen]**File:** /etc/X11/xorg.conf[/COLOR][/SIZE][COLOR=DarkGreen]    Driver     "fglrx" 
[/COLOR] 

What specifically do I write into xorg.conf? I don't want to scrw things up. It is unclear: Do I paste in lines one and two?

Thanks.

---

### Post by jdb on 2010-01-01
> **tomasterisk said:**
> I have a question what exactly I do with these instructions from the tutorial:

[COLOR=DarkGreen]In the device section, if it is not already there add: 
[/COLOR]     [SIZE=-1][COLOR=DarkGreen]**File:** /etc/X11/xorg.conf[/COLOR][/SIZE][COLOR=DarkGreen]    Driver     "fglrx" 
[/COLOR] 

What specifically do I write into xorg.conf? I don't want to scrw things up. It is unclear: Do I paste in lines one and two?

Thanks.

It kind of depends what your xorg.conf looks like.

There are various sections & one or more will be labeled "Device".
Here is an example:

```
Section "Device"
  Identifier  "Videocard0"
  Driver      "intel"
EndSection
```

The identifer gives a hint as to what the device is for and will
match an entry in the "ServerLayout" section.

When you determine which is the correct "Device" (easy if you only have one) set the Driver line to:
```
  Driver      "fglrx"
```

jdb

---

### Post by tomasterisk on 2010-01-01
Well, I screwed that up. I am now in low graphics mode.

Aaargh!

OK - after two restarts I am back to where I was. Blocky graphics never looked so good, compared to huge letters. I think I'll just settle for this version of 8.04 and use 9.04 more.

---

### Post by jdb on 2010-01-01
> **tomasterisk said:**
> Well, I screwed that up. I am now in low graphics mode.

Aaargh!

OK - after two restarts I am back to where I was. Blocky graphics never looked so good, compared to huge letters. I think I'll just settle for this version of 8.04 and use 9.04 more.

I know the feeling :lolflag:

I upgraded my Arch Linux a  couple days ago & it came up in very low resolution, HUGE letters.
I fooled around with it for a long time before I found a post on the internet with the fix.
I needed to add the kernel option nomodesetting.
I would have never figured that one out.

jdb

---

### Post by thomasaaron on 2010-01-04
OK, the screen shot you posted is no problem. You just need to hit the "Reload" button. (I assume you already did that.)

If you will post the output of...

cat /etc/X11/xorg.conf

...I will insert the driver line and follow up with instructions for getting the xorg.conf back into place.

---

### Post by tomasterisk on 2010-01-05
> **thomasaaron said:**
> OK, the screen shot you posted is no problem. You just need to hit the "Reload" button. (I assume you already did that.)

If you will post the output of...

cat /etc/X11/xorg.conf

...I will insert the driver line and follow up with instructions for getting the xorg.conf back into place.


Screenshot of that output is attached.

---

### Post by thomasaaron on 2010-01-05
Geesh, Tom! You're gonna make me type all that out!? :P

If you paste it in, I can fix the file and send you back a text file.

---

### Post by tomasterisk on 2010-01-05
> **thomasaaron said:**
> Geesh, Tom! You're gonna make me type all that out!? :P

If you paste it in, I can fix the file and send you back a text file.

Oops. Sorry! I didn't know what you wanted with the info. I'll get back to you later this evening with the text file.

---

### Post by tomasterisk on 2010-01-05
> **tomasterisk said:**
> Oops. Sorry! I didn't know what you wanted with the info. I'll get back to you later this evening with the text file.


OK, here is the output:

tom@tom-my:~$ cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection
tom@tom-my:~$

---

### Post by thomasaaron on 2010-01-05
OK. I've attached the file.

Download it to your desktop and then run these commands...

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bk
sudo cp ~/Desktop/xorg.txt /etc/X11/xorg.conf

Then reboot.

If that hoses everything, you can return to the previous setting by going into recovery mode and running...

sudo cp /etc/X11/xorg.conf.bk /etc/X11/xorg.conf
sudo reboot -h now

---

### Post by tomasterisk on 2010-01-05
> **thomasaaron said:**
> OK. I've attached the file.

Download it to your desktop and then run these commands...

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bk
sudo cp ~/Desktop/xorg.txt /etc/X11/xorg.conf

Then reboot.

If that hoses everything, you can return to the previous setting by going into recovery mode and running...

sudo cp /etc/X11/xorg.conf.bk /etc/X11/xorg.conf
sudo reboot -h now

I did the above and now I have the big jumbo letters. I tried implementing the fix you wrote but apparently something screwed up. In reboot I was given 4 choices. The first was continuing to normal boot. I choose the following choice after and wrote the commands but was told that there was no such command.

Luckily I have 9.04 on this machine (from where I am writing this). I am done trying to fix the 8.04 part - at least for tonight.

Maybe I'm just too stupid for Linux. Frustrating. Its a good thing 9.04 doesn't freeze now as much as it used to.

---

### Post by jdb on 2010-01-05
> **tomasterisk said:**
> I did the above and now I have the big jumbo letters. I tried implementing the fix you wrote but apparently something screwed up. In reboot I was given 4 choices. The first was continuing to normal boot. I choose the following choice after and wrote the commands but was told that there was no such command.

Luckily I have 9.04 on this machine (from where I am writing this). I am done trying to fix the 8.04 part - at least for tonight.

Maybe I'm just too stupid for Linux. Frustrating. Its a good thing 9.04 doesn't freeze now as much as it used to.

It's very frustrating when something doesn't work that used to.
Not being able to fix it isn't stupidity, it's just the lack of some
key bit of knowledge that can sometime be hard as heck to come by :)

jdb

---

### Post by tomasterisk on 2010-01-06
> **jdb said:**
> It's very frustrating when something doesn't work that used to.
Not being able to fix it isn't stupidity, it's just the lack of some
key bit of knowledge that can sometime be hard as heck to come by :)

jdb

Yes, I was just disgusted at the time. Even at this time I prefer Linux to Windows. Luckily I have dual boot so I can get work doen while I get around to fixing the other part.

Thanks for the encouragement.

---

### Post by thomasaaron on 2010-01-06
Also, I'm not entirely certain that fglrx in 8.04 will support your ATI card. That could be the problem. We were using pretty cutting edge ATI cards when we built your machine under 8.10.

---

### Post by tomasterisk on 2010-01-09
> **thomasaaron said:**
> Also, I'm not entirely certain that fglrx in 8.04 will support your ATI card. That could be the problem. We were using pretty cutting edge ATI cards when we built your machine under 8.10.

I'm sure that is true. But I do know that this computer ran an unblocky 8.04. However at this point I'm just trying to get back to blocky but normal size icons and fonts.

Then I think I'll declare victory and work on tweaking 9.04 where it should be.

---

### Post by tomasterisk on 2010-01-13
> **tomasterisk said:**
> I'm sure that is true. But I do know that this computer ran an unblocky 8.04. However at this point I'm just trying to get back to blocky but normal size icons and fonts.

Then I think I'll declare victory and work on tweaking 9.04 where it should be.

OK, now I have time to devote to fixing Jaunty. It has blocky graphics also, but not as bad as my Hardy partition. Strangely, some web graphics, like Flickr, seem to be OK but ones like BBC news are not.

Anyhow, I am assuming this is also a driver issue?

---

### Post by thomasaaron on 2010-01-13
Do you have the ATI driver enabled in Hardware Drivers? (It definitely should be there in 9.04.)

How about desktop effects?

---

### Post by tomasterisk on 2010-01-13
> **thomasaaron said:**
> Do you have the ATI driver enabled in Hardware Drivers? (It definitely should be there in 9.04.)

How about desktop effects?

ATI driver is enabled. The alternate one, atheros, is not.

I was able to use desktop effects.

---

### Post by thomasaaron on 2010-01-13
OK, can you send me a screenshot of the blocky graphics?

---

### Post by tomasterisk on 2010-01-14
> **thomasaaron said:**
> OK, can you send me a screenshot of the blocky graphics?

This is from BBC News:

---

### Post by thomasaaron on 2010-01-14
Ah! BLOCKY! :lolflag:
I definitely see what you mean now!

Interesting that the letters over Tiger's head are... picture perfect!

There is an alternative ATI driver for 9.04, and I can look up the instructions for installing. But FIRST, is there an auto-adjust feature anywhere in your monitor's menu system?

And have you tried with a different monitor?

Frankly, if it doesn't work with a different monitor or the other ATI drivers, I'm thinking... graphics card.

---

### Post by tomasterisk on 2010-01-17
> **thomasaaron said:**
> Ah! BLOCKY! :lolflag:
I definitely see what you mean now!

Interesting that the letters over Tiger's head are... picture perfect!

There is an alternative ATI driver for 9.04, and I can look up the instructions for installing. But FIRST, is there an auto-adjust feature anywhere in your monitor's menu system?

And have you tried with a different monitor?

Frankly, if it doesn't work with a different monitor or the other ATI drivers, I'm thinking... graphics card.

I do have an auto-adjust on the monitor but it did nothing that i could see.

I am wondering if you aren't right about the graphics card. Also I wonder if this is part of the same problem with the freezing of the screen in Jaunty.  BTW, the screen had just frozen so I booted up back into Hardy and, for some strange reason, the screen is no longer huge.

No, I don't have another monitor to test. My other monitor has a different plug.

---

### Post by thomasaaron on 2010-01-18
Yeah, that's what I was referring to in my previous post. In Jaunty, there was an ATI driver problem that caused freezing. But I don't remember it causing blocky graphics.

Anyway, here are the instructions for adding the swat driver.

NOTE TO ALL READERS: THE FOLLOWING INSTRUCTIONS ARE MEANT FOR CERTAIN ATI CARDS UNDER JAUNTY. IF YOU'RE USING KARMIC, THEY SHOULD NOT BE NECESSARY.
> 
Please run these commands from a terminal...
echo deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) `lsb_release -cs` main | sudo tee -a /etc/apt/sources.list.d/x-updates.list
echo deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) `lsb_release -cs` main | sudo tee -a /etc/apt/sources.list.d/x-updates.list

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B22AB97AF1CDFA9 && sudo apt-get update

sudo apt-get upgrade


They will install a better ATI driver, and I think that should solve your problem. 

---

### Post by tomasterisk on 2010-01-18
[QUOTE=thomasaaron;8684467]Yeah, that's what I was referring to in my previous post. In Jaunty, there was an ATI driver problem that caused freezing. But I don't remember it causing blocky graphics.

Anyway, here are the instructions for adding the swat driver.


OK, I ran the commands in the terminal. Thanks.

---

### Post by thomasaaron on 2010-01-19
Hi, Tom.

Did that fix it?

---

### Post by tomasterisk on 2010-01-19
> **thomasaaron said:**
> Hi, Tom.

Did that fix it?

Sorry to say that it didn't. At least for the blockiness. I held off writing in order to test it for a period of time for freezes. It froze once shortly after I ran those commands, but hasn't since.

But the blockiness is there still.

---

### Post by thomasaaron on 2010-01-20
OK, you probably should just go ahead and move this one to email support. Let's try a new card.

---

