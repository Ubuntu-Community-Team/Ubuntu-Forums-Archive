---
title: "How I got my EZCap 646 DVB-T USB TV Tuner up"
date: 2012-07-31
forum: Tutorials
---

### Post by Bucky Ball on 2012-07-31
* A heads up. I wrote this a long time ago and Taz has given me a heads up in post #2, and I thank them for it. Those instructions install the driver without a problem. My instructions in this post are obsolete and no longer work so disregard. Hopefully this driver will be in the kernel eventually and will work 'out of the box'. Testing 14.04 at the moment and you still need Taz's instructions as the rtl2838 is still not part of the kernel or recognised. 

Good luck to future travellers. ;)

**Disclaimer & Intro: **    [LEFT]I am running an old hybrid of a desktop; Ubuntu Studio with Xubuntu and Ubuntu desktops added to that (among other things). No fresh install since 8.04 LTS (I hit the upgrade button to get to 10.04 LTS about a year ago). Yea, that's right. It&#8217;s confusing in there. To add extra spice to the confusion, I&#8217;m using kernel version 2.6.38-15-generic, which I think is for 11.04. During the process of getting the EZCap 646 (DVB-T, DAB/DAB+) USB tuner up and running I used the Xfce4 desktop environment.

[/LEFT]
        [LEFT]Point being I have an unusual setup and a lot of things installed for A/V which you might not have, so if you&#8217;re missing software along the way you may need to dig and install some things. This thread is not about that; it is a simple, straight line of the steps that *should* (theoretically) work to get your EZCap (and probably other devices) working with Me-TV (and definitely other softwares). This is a condensed version of what took me, previously a DVB virgin, about three days of research and experimentation.

[/LEFT]
        The good news is you don&#8217;t need banging specs to get this happening. I&#8217;m using a 12 year old box running a Pentium 4, 3Ghz hyperthreading processor with 1Gb of RAM and I can watch TV (HD is fantastic), while surfing the net and having OpenOffice open. All I need to do. Haven&#8217;t pushed the envelope as not curious. ;)

The EZCap could work &#8216;out-of-the-box&#8217; with newer releases of Ubuntu, in which case, if you&#8217;re using something newer than 10.04 LTS, there may be nothing to see here as the driver may be in the kernel. The driver install explanation is for the EZCap but applies to any device with the Realtek  rtl2832u chip. The remainder of the post could be applied to any tuner. 

* Update: The driver for this device (and many others) is not in 12.04 LTS as I am using it and needed to install manually.
[CENTER]
 *
[/CENTER]
 
First up, if you are getting your signal from an aerial on the roof and need to cover some distance to get to the computer, attempt to use one complete, reliable cable to your computer rather than a few shorter ones cobbled together; more cable joins, less chance of a reliable outcome, time wasted finding the weak link. 

I have the rooftop aerial cable into a two-way aerial splitter (cheap and readily available), one side of the splitter to the PVR/TV setup in the living area, the other using a 10 metre cable to get the signal to the tv tuner in my studio.
        [CENTER]

[/CENTER]
        **1/ Driver:**
    Without the USB tuner in, install the driver using this method (thanks to [Joel Stanley]("http://jms.id.au/wiki/EzcapDvbAdapter;").):&#65279;

        ```
$ sudo apt-get install linux-headers-generic
 $ git clone [http://jms.id.au/~shenki/git/rtl2832u]("http://jms.id.au/%7Eshenki/git/rtl2832u")
 $ cd rtl2832u
 $ make
 $ sudo make modules_install
```        Once complete, reboot and once back at a desktop, open a terminal, plug the dongle in, and immediately enter:
```

        dmesg
```        ... then hit &#8216;return&#8217;. You are looking for something similar to this:

```
[LEFT][  188.114557] DVB: registering new adapter (RTL2832U DVB-T USB DEVICE)[/LEFT]
    [LEFT][  188.115238] DVB: registering adapter 1 frontend 0 (Realtek RTL2832 DVB-T  RTL2836 DTMB)...[/LEFT]
    [LEFT][  188.115331] dvb-usb: RTL2832U DVB-T USB DEVICE successfully initialized and connected.[/LEFT]

```[LEFT]... near the end of the output. If you don&#8217;t see something like that the driver is not installed or installed incorrectly (or Joel&#8217;s pulled the link).


[*** There are alternatives.** I haven't tried these yet but intend to and will add later, so deviate from the path of this thread at your own risk. Please post back with any results of experimentation with these two options. The first may help getting DAB+ up, which I've had no success with:

[http://www.linuxtv.org/wiki/index.php/EzCap_DVB_T_Stick](http://www.linuxtv.org/wiki/index.php/EzCap_DVB_T_Stick)

... and this one I need to spend a bit of time trying to nut out what I'm actually supposed to do. Looks like need to install a modified 3.0.0 kernel:

[https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/](https://github.com/ambrosa/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/)

* Update: I have successfully installed this driver in 12.04 LTS. Dongle immediately recognised. 

... back to the story ...]

[B]
2/ Player:[/B][/LEFT]
    [LEFT]I tried lots of players (VLC, xine, gxine, Freevo, mplayer, TVTime (but couldn&#8217;t work out how to play TV via the dongle with TVTime!)) but settled with Me-TV. If you&#8217;re running 10.04 LTS, you can battle away with the old version (as I did) or you can install the Me-TV repository from [HERE]("https://launchpad.net/%7Eme-tv-development/+archive/ppa") and save yourself a headache (and also get Me-TV version updates/upgrades when released). 

* Update: I am primarily using Xine now. For my config it seems to run smoother and I prefer the interface. I have no idea how to use it as a PVR; Me-TV is really easy for that.

 [/LEFT]
        [LEFT]The newer version of Me-TV has auto-scan to create a channel list (or whatever it does as there is actually no 'channels.conf' file created that I can find); other players use a channels.conf file placed in their folder (a channels.conf file inside /.xine for instance). In fact, for players that don&#8217;t auto-scan (most), a channels.conf appears the only way of getting them to scan for anything (enlighten us if you know more). Here is a link where you have a good chance of finding a scan file to use with dvb-apps scan or w_scan:

[http://linuxtv.org/hg/dvb-apps/file/96025655e6e8/util/scan/dvb-t](http://linuxtv.org/hg/dvb-apps/file/96025655e6e8/util/scan/dvb-t)

 [/LEFT]
        [LEFT]Installing 'x_scan' with the package 'dvb-apps' will scan and create a channels.conf file for your location but that process always refused to register the channels, even though finding them, when I tried it. 

If you want to dig for one, or write one, the syntax for the file name is, say, au-Adelaide, where 'au&#8217;=Australia and 'Adelaide&#8217;=town. The way I found one was to search for: &#8216;channels.conf australia&#8217;. I found a few. I suggest you try the same tack and good luck with it. (You will find the older version of Me-TV has a 'scan file' which you can work from and you will get stations but there are new channels missing and obsolete when digital takes over shortly in Aus.)


[/LEFT]
                [LEFT]**3/ Launch Me-TV**>View>Devices (mine is /dev/dvb/adapter1/frontend0). Now, the output from dmesg when you plugged the dongle in gave important info:

[/LEFT]
        [LEFT]```
[  188.115238] DVB: registering** ad**[FONT=Courier New]**apter 1 frontend 0 **[/FONT][FONT=Courier New](Realtek RTL2832 DVB-T  RTL2836 DTMB)...[/FONT]
```[FONT=Courier New] 
[/FONT][/LEFT]
        [LEFT]What you find in Me-TV&#8217;s &#8216;Devices&#8217; should match the device info from dmesg when you plugged the dongle in, bolded in the message above .

[/LEFT]
        [LEFT]If all's going to plan, head to Channels>Add>Auto-scan. Should give an indication of how many channels it&#8217;s found (0/35 for instance) and a list of channels for you to add when it finishes. If it doesn&#8217;t, there&#8217;s something amiss. If so, run Me-TV from a terminal with:

[/LEFT]
        [LEFT]```
me-tv
```[/LEFT]
        [LEFT]... and check the terminal for errors while you are doing a scan. From the error output, start digging for clues.

[/LEFT]
        [LEFT]If it does pick up a list of channels (give it some time, it can take awhile) wait for it to finish then click &#8216;Add&#8217; and you should be set.

For me, the auto-scan worked beautifully and picked up channels I didn&#8217;t know we had so hope it's that easy for you.

Next, tweak about a bit to improve reception or driver and find the right combination for your config. I have an NVidia graphics card (old!) in my machine and have opengl set to best quality in the NVidia config GUI while using the opengl driver in Me-TV and Xine. 
[CENTER]
*
[/CENTER]
**Salient points: **[/LEFT]
    [LEFT]
* If you are using a cable from the aerial at distance, try and use one long, checked cable; no joiners. Save time by knowing what you&#8217;re working with from point A;
* Once you have the aerial into the dongle, plug it in to the computer and check the dmesg for acknowledgement;
* Once you have the dongle recognised, install a TV Viewer and try to get a station. Before this, you are either going to need to do an auto-scan using Me-TV or a manual scan using another app to create a channels.conf file. To check the dongle is operational and capable of scanning use the Me-TV auto-scan, even if you end up using another app. This will confirm the dongle is operational, up and running;

* Go for it in **stages** and don&#8217;t let those bleed into each other. **First**, get the card up. **Second**, install and tweak the viewer. 
[/LEFT]
[CENTER] 
*

[/CENTER]
        [LEFT]That&#8217;s it. Hope this helps to get someone up and running, or at least off the blocks to DVB-dom. Enjoy the ride! ;)

[Hopefully there will be progress on DAB+ and Linux in the near future. If anyone has any clues about that I'm all ears as I've had no luck.]
 [/LEFT]

---

### Post by TazX on 2013-03-04
Heya!  Just thought I'd give you (and others who've come across this thread) a heads up.  The drivers for the EZCap are now part of the official LinuxTV Build, which makes our lives a lot easier.  All we need to do now is:
> [INDENT]git clone git://linuxtv.org/media_build.git 
cd media_build 
./build 
sudo make install[/INDENT][FONT=arial]

Hope this is helpful.  I came across this thread back in the day when I was trying to get this baby working.  Hopefully this update can do the same for somebody else.  :)

Official Site:
[/FONT][http://git.linuxtv.org/media_build.git](http://git.linuxtv.org/media_build.git)
[COLOR=#FFFFFF][FONT=sans-serif][/FONT][/COLOR]

---

