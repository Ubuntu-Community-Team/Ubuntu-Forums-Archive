---
title: "Thoughts on/experience with Acer Aspire Revo R3700"
date: 2010-11-19
forum: The Cafe
---

### Post by fatality_uk on 2010-11-19
Does anyone have one of these? I was thinking about building a media centre around this with a BlueRay player attached.

---

### Post by onesim on 2010-11-19
> **fatality_uk said:**
> Does anyone have one of these? I was thinking about building a media centre around this with a BlueRay player attached.
 
Hi I've just got my revo 3700 few days ago, nice toy at first look. I didn't yet played deeply with it, just installed Ubuntu and connected to network through ethernet cable.
WiFi card is not detected (missing drivers?). I'll investigate this soon.
Drivers from Nvidia for the graphic chipset have been automatically downloaded and installed. Ubuntu can run smoothly with animation effects on windows etc, but i didn't tryed it with movies yet.
In any case, i do not want to install xbmc for now as the main purpose i've bought it is to work as home server (thanks to its low power consumption)
 
Bye
Simone

---

### Post by timgood on 2010-11-23
Got one and installed Maverick 32 bit - wireless does work, but as soon as it is disabled the computer locks solid. So when you attempt to shut down or reboot, computer locks up and you have to do a hard reset.

With Maverick 64 bit, wireless does not work, so computer will shut down and reboot OK. But no wireless. I'm investigating this problem to see if I can get a solution.

Wireless is RT3090 pci - none of the ppa debs seem to work in 10.10

---

### Post by drawkcab on 2010-11-23
I own a Revo 3600 that I think is fine.  I say that because a year and a half ago I ordered mine directly from Taiwan and was able to get a linpus-equipped model with 2gb, Atom 330, 320 hdd space and a free wireless keyboard and mouse for under $300!  

I noticed an article saying that the Revo 3700 with 2gb of ram and 250gb of hdd space is going to come in at $400.  That's not a good deal.  In other words, I don't see what you're getting for the extra $100+ except that you get win7 and the intel wifi chip is a nice plus.  The atom d525 bumps you up from 1.6 to 1.8, but that's still not enough snort to run HD flash, or even SD flash on a HD tv, sans hardware acceleration in Linux.

Some other concerns:

-Getting HDMI audio to work in linux has been a pain in the butt for many Revo owners.

-This platform does not really handle .mkv 1080 files well in Linux.

So if you go with the 3700, I'd say stick with win7.  Otherwise either try to look for a hot deal on a 3600 and maybe save $150-$200 or maybe even check out some similar offerings from Asus, Zotac, etc.

Don't get me wrong, I like my 3600 for what it is and what it does but I'm going to wait until manufacturers offer a more significant performance upgrade before I buy something else.  When they do, I'm going to turn my 3600 into my office computer.  ;)

---

### Post by onesim on 2010-11-24
> **drawkcab said:**
> I own a Revo 3600 that I think is fine.  I say that because a year and a half ago I ordered mine directly from Taiwan and was able to get a linpus-equipped model with 2gb, Atom 330, 320 hdd space and a free wireless keyboard and mouse for under $300!  

I noticed an article saying that the Revo 3700 with 2gb of ram and 250gb of hdd space is going to come in at $400.  That's not a good deal.  In other words, I don't see what you're getting for the extra $100+ except that you get win7 and the intel wifi chip is a nice plus.  The atom d525 bumps you up from 1.6 to 1.8, but that's still not enough snort to run HD flash, or even SD flash on a HD tv, sans hardware acceleration in Linux.

Some other concerns:

-Getting HDMI audio to work in linux has been a pain in the butt for many Revo owners.

-This platform does not really handle .mkv 1080 files well in Linux.

So if you go with the 3700, I'd say stick with win7.  Otherwise either try to look for a hot deal on a 3600 and maybe save $150-$200 or maybe even check out some similar offerings from Asus, Zotac, etc.

Don't get me wrong, I like my 3600 for what it is and what it does but I'm going to wait until manufacturers offer a more significant performance upgrade before I buy something else.  When they do, I'm going to turn my 3600 into my office computer.  ;)

I've bought my revo 3700 from taiwan too, at 344$ which is good (no win7 but who care?). Other than the new processor, also the ion graphic chipset is the Next Generation one, and it claims to support fullhd at 1080 (don't know if it can handle mkv, didn't tryed yet). Are you sure hw acceleration is not handled in linux? My ubuntu downloaded propertary nvdia drivers and graphics seems good.

---

### Post by onesim on 2010-11-24
> **timgood said:**
> Got one and installed Maverick 32 bit - wireless does work, but as soon as it is disabled the computer locks solid. So when you attempt to shut down or reboot, computer locks up and you have to do a hard reset.

With Maverick 64 bit, wireless does not work, so computer will shut down and reboot OK. But no wireless. I'm investigating this problem to see if I can get a solution.

Wireless is RT3090 pci - none of the ppa debs seem to work in 10.10

Sure the chip is 3090? I found it's a 3390... maybe it doesn't matter at all.

---

### Post by drawkcab on 2010-11-24
> **onesim said:**
> I've bought my revo 3700 from taiwan too, at 344$ which is good (no win7 but who care?). Other than the new processor, also the ion graphic chipset is the Next Generation one, and it claims to support fullhd at 1080 (don't know if it can handle mkv, didn't tryed yet). Are you sure hw acceleration is not handled in linux? My ubuntu downloaded propertary nvdia drivers and graphics seems good.

Hardware acceleration is just fine in general, it's more that flash in linux doesn't really offload to the gpu so the poor atom processor has to try to keep up.  

I've tried and tried to get those x264 .mkv 1080 formats to work on my 3600 under Linux but I just can't seem to get it right.  h264 720 works beautifully but that seems to be its limit.

That is a good price for the 3700!  So what if it has a few Chinese characters here and there?

---

### Post by onesim on 2010-11-24
> **drawkcab said:**
> Hardware acceleration is just fine in general, it's more that flash in linux doesn't really offload to the gpu so the poor atom processor has to try to keep up.  

I've tried and tried to get those x264 .mkv 1080 formats to work on my 3600 under Linux but I just can't seem to get it right.  h264 720 works beautifully but that seems to be its limit.

That is a good price for the 3700!  So what if it has a few Chinese characters here and there?

Theoretically the d525 and ng ion (ion2) perform better than atom N330 and ion, when i try it hard i tell you how x264 looks. 

What do you mean about chinese characters?
To tell the truth, the model i've bought hasn't the wireless keyboard and mouse, but the wired ones. However, as i'll control it remotely, i do not need those stuff at all. The keyboard has both english and chinese characters but is useable. Maybe, better than keyboard, it would be nice to have one of those IR controllers to use with XBMC, it will be perfect if used as multimedia center.

---

### Post by Methanoid on 2010-12-08
Could any owner confirm the idle/load power consumption using a meter? 20w or what? Thanks

---

### Post by asdf29 on 2010-12-18
Dan Wood put a review on Ebuyer with a fix to the wireless issue.  My R3700 is arriving on Monday so not sure if it works yet.  Looks like a good deal at £199.

> 
Open a terminal and type:
sudo pico /etc/modprobe.d/blacklist.conf

Now add this to the bottom of the file:
blacklist rt2800pci

Save the file (Ctrl+o)

Now reboot (you'll still need to hold power button in this time!).

[http://www.ebuyer.com/product/236579]("http://www.ebuyer.com/product/236579")

---

### Post by asdf29 on 2010-12-22
I've installed Maverick 32-bit - wireless and nvidia drivers work like a charm.  I'm struggling to get sound to work through the HDMI cable though.  I've tried unmuting all the channels in alsamixer, but nothing seems to work?

Anyone got any ideas?


Codec: Realtek ALC662 rev1


paul@knightrider:/usr/share/alsa/cards$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
Home directory /home/paul not ours.
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by asdf29 on 2010-12-23
I worked out that I could play files through hw:1,7 and it came through the HDMI cable.

I ended up creating a .asoundrc file in my home directory as follows:

> pcm.dmixer {
  type dmix
  ipc_key 2048
  slave {
    pcm "hw:1,7" # Always use pure hw. dmix will reformat/resample audio.
    period_size 512 # If you get stuttering/or non-working audio, fiddle around with these
    buffer_size 4096
    rate 48000 # HDMI, I'll assume 48kHz
    format S16_LE # Should be default for pretty much any soundcard.
  }
  bindings {
    0 0
    1 1
  }
}

pcm.!default {
  type plug
  slave.pcm dmixer
}

It is not the optimum solution because now the volume control widget and the sound preferences window don't work in Ubuntu.  But now I at least have sound in Boxee which is pretty cool.

Is there a better way of doing it so that it all integrates nicely?

---

### Post by chuckyp on 2010-12-27
You could try creating /etc/asound.conf  and adding your settings in there. 

Also how did you get sound over hdmi i've been struggling with it for 2 days now. if I: aplay -Dhw:1,7 /usr/share/sounds/alsa/Front_Center.wav I get nothing.  I can get sound to play to the headphones on 0,0 but that's about it.

Correction: I can't play audio to headphone jack on 0,0 trying to figure out what the default playback is.   speaker-test by itself works but not when I speicify.

---

### Post by asdf29 on 2010-12-27
Check that the cards are not muted.  Run alsamixer on the command line and make sure none of the channels on the HDA NVidia card are muted.  Then try the aplay line again.

---

### Post by asdf29 on 2010-12-27
I must admit I am hacking around a bit here, but it appears to be working.  I think what I've figured out is gnome-sound-preferences (the widgety sounds control thingy and the preferences panel) use pulseaudio which is the new sound server in the linux world (?)

So here is what I did to get the sound control working for the HDMI:
- Edited /etc/pulse/default.pa
> sudo vi /etc/pulse/default.pa

- Changed it to manually load the alsa module using hw:1,7, but adding this line on around line 44:
> load-module module-alsa-sink device=hw:1,7
and commenting out the module auto-detection (lines 51 to 58 in my file):
> ### Automatically load driver modules depending on the hardware available
#.ifexists module-udev-detect.so
#load-module module-udev-detect
#.else
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
#load-module module-detect
#.endif

- Restarted pulse-audio:
> killall pulseaudio

Now, I'm not sure if that's the best way to accomplish getting the audio to work over HDMI, but it appears to work.  Anyone know any better?

---

### Post by drawkcab on 2010-12-27
Well I have no info on how to get hdmi sound working although I remember seeing some threads about that on the Revo and XBMC forums.

I did, however, get the Revo to play x264 .mkv files by enabling vdpau and installing the ffmpeg codecs.

I'm super happy with the device.  Now I just need a remote that works with Ubuntu/XBMC.  Any suggestions?

---

### Post by jerenept on 2010-12-27
> **drawkcab said:**
> Well I have no info on how to get hdmi sound working although I remember seeing some threads about that on the Revo and XBMC forums.

I did, however, get the Revo to play x264 .mkv files by enabling vdpau and installing the ffmpeg codecs.

I'm super happy with the device.  Now I just need a remote that works with Ubuntu/XBMC.  Any suggestions?

Microsoft Media Center Remote.

---

### Post by asdf29 on 2010-12-27
If you have an iPhone or Android phone, I'm pretty sure there is an app that works pretty well.  I'm using the Boxee app for Android.

---

### Post by drawkcab on 2010-12-28
> **jerenept said:**
> Microsoft Media Center Remote.

Ok, cool!  Does it require a lot of tweaking or is it pretty straightforward?

---

### Post by MartinH-J on 2011-01-10
Have just bought a Revo 3700 to use as with XBMC and as a mythfrontend to my current 3610 running XBMC/combined myth front/backend

Using mythbuntu 10.04. Works just fine with mkv 1080p files for me streamed over the network

As for the wireless not working look at post 6 here:

[http://forum.xbmc.org/showthread.php?t=85765]("http://forum.xbmc.org/showthread.php?t=85765")

It is using the 3090 driver but if you check the logs it cant find the 2860 file it is looking for!

Audio fix is here:

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules]("https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules")

If I remember correctly plughw:1,7 is the hdmi source

Oh and dont forget to run

sudo alsamixer

Then F6 to switch to Nvidia and unmute the channels in there

5 minutes effort and a reboot and it should be up and running with hdmi sound and wireless.

Now I just need to get my PS3 BD remote working on the new Revo with Myth and XBMC so I can ditch the keyboard

Martin

---

### Post by DNAspark99 on 2011-01-13
thanks, I think you just convinced me to pull the trigger on an R3700

---

### Post by MartinH-J on 2011-01-13
> **MartinH-J said:**
> Have just bought a Revo 3700 to use as with XBMC and as a mythfrontend to my current 3610 running XBMC/combined myth front/backend

Using mythbuntu 10.04. Works just fine with mkv 1080p files for me streamed over the network

As for the wireless not working look at post 6 here:

[http://forum.xbmc.org/showthread.php?t=85765]("http://forum.xbmc.org/showthread.php?t=85765")

It is using the 3090 driver but if you check the logs it cant find the 2860 file it is looking for!

Audio fix is here:

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules]("https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules")

If I remember correctly plughw:1,7 is the hdmi source

Oh and dont forget to run

sudo alsamixer

Then F6 to switch to Nvidia and unmute the channels in there

5 minutes effort and a reboot and it should be up and running with hdmi sound and wireless.

Now I just need to get my PS3 BD remote working on the new Revo with Myth and XBMC so I can ditch the keyboard

Martin

Oh and one more thing if using as a remote frontend:
upstart boots ubuntu nice and quick but when using wireless I find that the wireless is not started and connected before mythtv runs so you keep getting the configuration screen at startup because it cant find the backend. I changed from network manager to wicd which starts at boot but its still not ready by the time mythtv is running. I added "sleep 10" to the mythfrontend startup script to allow time for my wireless to log on with WPA and all works now. Downside is that starting mythfrontend takes 10 seconds longer if starting from within Ubuntu but as this will be running as another dedicated box with a remote control then at least now I can just restart it if needed and it will come back up straight into mythtv again.

When I get time I will document my setup process for getting mythtv/xbmc/Sony PS3 remote working on both Revo 3610 and 3700 platforms

Martin

Martin

---

### Post by MartinH-J on 2011-01-13
> **DNAspark99 said:**
> thanks, I think you just convinced me to pull the trigger on an R3700

You're welcome!

Personally I don't see much difference between 3610 aand 3700. Major differences are Wireless N and colour so I would go with whichever offers the best deal! At present the 3610 drivers work better out of the box (never had audio/wireless problems) but that is fairly trivial to fix when you find the easy solution posted above :)

I nearly got another 3610 so that both my platforms were the same and easier to maintain but in the end decided I couldnt buy an older machine for the same preice as the newer one. Besides I prefer the new black look. The major factor was the wireless as this will be used remotely over wireless but even that is solvable for very little extra (and you probably get better wireless) by opening up the Revo and upgrading to an Intel wireless N card

Martin

---

### Post by phoenix1/4 on 2011-03-10
Hi All,

Thought I'd throw in my 2 cents.

I bought my Revo 3700 from Taiwan on eBay for $334, and it arrived in 5 days. I immediately wiped the pitiful FreeDos install and loaded up Maverick Desktop i386. I used the nifty VESA mount to attach it to the back of my 22" AOC HDMI monitor, and it has been sitting there inconspicuously ever since.

Next up was installing proprietary Nvidia drivers, via the notification icon. No troubles there. Wireless worked straight out of the box, strong signal with no issues whatsoever. XBMC was a few quick lines in terminal, and the first issue arrived when I hit restart. As found by other users (thanks!), the Wireless drivers were causing havoc on the reboot, so I added the blacklist item described further up in this forum. Reboots like a charm now.

XBMC handles all the 720p videos that I've been playing via a samba share with no apparent issues, and I've recently added a $6 infra red remote from ebay, it worked straight out the box without even needing to exit XBMC. 

So essentially for $340 I have a powerful, sleek and virtually silent HD media centre sitting in my room! I'm very impressed with the price and packaging of this system, thumbs up to Acer!

On a further note, does anyone happen to know if the BIOS is able to boot from an SD card?

---

### Post by jerenept on 2011-03-10
> **drawkcab said:**
> Ok, cool!  Does it require a lot of tweaking or is it pretty straightforward?

Sorry for my late reply, but, it does work ootb with xbmc as far as i know.

---

### Post by jensk on 2011-03-24
I have a 3600 that I user as a mythbuntu frontend (10.04) I have never used wireless as it is cabled to my network. The 3600 is attached to my living room TV by HDMI (sound and picture).

It worked allmost out of the box with 10.04. All I had to do was select HDMI sound output inside Mythtv.

Streaming of 720p video from my mythbackend works with barely detectable CPU load for the mythfrontend.real process on the Revo

I bought it for approx $180 incl hipping on Amazon.co.uk but. 
The 3600 is a atom single-core model with 1Gb ram and 160 Gb disk no OS. 

Despite the lower specs than the 3610/3700 it does the job as a frondend without a glitch.

---

### Post by MartinH-J on 2011-03-24
Indeed....its the GPU that makes these so good for the job. It's all done in there so the cpu has minimal loading.

Am trying to sort out my installation notes to put online for installing a dual XBMC/MytTV front&backend with a PS3 bluetooth remote (is what I have running) if anyone is interested

Martin

> **jensk said:**
> I have a 3600 that I user as a mythbuntu frontend (10.04) I have never used wireless as it is cabled to my network. The 3600 is attached to my living room TV by HDMI (sound and picture).

It worked allmost out of the box with 10.04. All I had to do was select HDMI sound output inside Mythtv.

Streaming of 720p video from my mythbackend works with barely detectable CPU load for the mythfrontend.real process on the Revo

I bought it for approx $180 incl hipping on Amazon.co.uk but. 
The 3600 is a atom single-core model with 1Gb ram and 160 Gb disk no OS. 

Despite the lower specs than the 3610/3700 it does the job as a frondend without a glitch.

---

### Post by MartinH-J on 2011-04-21
OK I finally managed to spend a bit of time and write down my configuration for using a Sony PS3 BD remote with both XBMC and MythTv. It is located here:

[http://www.harley-jones.co.uk/?p=41]("http://www.harley-jones.co.uk/?p=41")

Martin

---

### Post by fatality_uk on 2011-04-21
Cheers Martin, might take another look at thos bit of kit.

---

### Post by MartinH-J on 2011-04-23
Been using mine with the remote as our main(only) PVR and media centre. Other half finds it easy to use and loves it!

Martin

---

### Post by ronkinoz on 2011-08-01
@Martin - I'm very interested in your experiences and thoughts with running the myth front/back combo on a Revo R3700.  I've just bought a 4GB R3700 off eBay with the intent of doing exactly that.  Any pitfalls?  Up to transcoding (if not in a hurry)?  How do you switch between Myth frontend and XBMC - a boot time option?

What I'm planning is:
- Mythbuntu & XBMC installed on the internal hard-disk.  Will set aside the rest of the internal for ripped kids vids in xvid/divx/h.264 formats.
- External 2TB drive for myth recordings
- Networked HDHomeRun dual-DVBT tuner over 100MB wired.

Any thoughts/tips/warnings appreciated...

Cheers,
Ron

---

### Post by MartinH-J on 2011-08-02
> **ronkinoz said:**
> @Martin - I'm very interested in your experiences and thoughts with running the myth front/back combo on a Revo R3700.  I've just bought a 4GB R3700 off eBay with the intent of doing exactly that.  Any pitfalls?  Up to transcoding (if not in a hurry)?  How do you switch between Myth frontend and XBMC - a boot time option?

What I'm planning is:
- Mythbuntu & XBMC installed on the internal hard-disk.  Will set aside the rest of the internal for ripped kids vids in xvid/divx/h.264 formats.
- External 2TB drive for myth recordings
- Networked HDHomeRun dual-DVBT tuner over 100MB wired.

Any thoughts/tips/warnings appreciated...

Cheers,
Ron

Ron,
 The only pitfalls are the wireless drivers are pretty crappy in the distro. I started with Mythbuntu 10.04 and upgraded to 10.10 but had to set the default boot to an older kernel (cant remember which as I am not near the machine right now). Upgrading to 11.04 just breaks and the box hangs...again I think this is all based around the wireless drivers but I don't need to run the very latest of everything. It's a media box after all. Neither do I want to be hacking configs if I need to install. My aim is to make it as smooth as possible.

I don't use a Homerun and I don't do any transcoding so cant help you there I am afraid. 

I installed mythbuntu and then added xbmc. Using the Sony PS3 BD remote I have configured the eject button to run an irexec script to switch between mythfrontend and xbmc and it works just fine. It also means that if something does crash (I have had the occasional xbmc plugin crash) you can kill and restart things without ever needing the keyboard.

I have documented all my mods and tweaks to get the system running on my bllog ([www.harley-jones.co.uk]("http://www.harley-jones.co.uk")) so suggest you take a look there for config files and information.

I run my Revo 3610 as a combined FE/BE/XBMC combo and the 3700 as a FE/XBMC combo but either would do the job.

Hope this helps!

Give me a shout if you get stuck. Have been running my boxes for a year or two now and they are as reliable as any commmercial PVR/media center.

Martin

---

