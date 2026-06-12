---
title: "Howto setup a bt878 TV Card"
date: 2006-04-02
forum: Tutorials
---

### Post by art2003 on 2006-04-02
This howto refers to a Modular Technology MM200PCTV TVcard but may help also with other bt878 based TV Cards.

It was written when I was running Ubuntu 7.10, it may need little changes to work with later releases.
Also I must mention I am a PAL user and have used it just with PAL devices, so for NTSC again you may need to tweak some
parameters.

With the card in your PC
type
lspci | grep Bt878

this is the output on my card:
0000:00:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
0000:00:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)

1) Make sure the module will be loaded
sudo gedit /etc/modules
add bttv if not already present

2) Options for the module. Create this file:
sudo gedit /etc/modprobe.d/bttv
```
# i2c
alias char-major-89 i2c-devb
options i2c-algo-bit bit_test=1
# bttv
alias char-major-81 videodev
alias char-major-81-0 bttv
# My TV Card
options bttv card=23 tuner=18 radio=0 pll=1 adc_crush=0

```

3) Install tvtime
sudo apt-get install tvtime
then run tvtime-scanner ; takes a few minutes

4) Running:
sudo modprobe bttv
and then run tvtime
at this point you should have black and white tv

to enable colour edit tvtime.xml

sudo gedit ~/.tvtime/tvtime.xml

```
<?xml version="1.0"?>
<!DOCTYPE tvtime PUBLIC "-//tvtime//DTD tvtime 1.0//EN" "http://tvtime.sourceforge.net/DTD/tvtime1.dtd">
<tvtime xmlns="http://tvtime.sourceforge.net/DTD/">
  <option name="DefaultBrightness" value="50"/>
  <option name="DefaultContrast" value="50"/>
  <option name="DefaultSaturation" value="78"/>
  <option name="DefaultHue" value="50"/>
  <option name="PrevChannel" value="2"/>
  <option name="Channel" value="1"/>
  <option name="FramerateMode" value="0"/>
  <option name="OverScan" value="0.0"/>
  <option name="CheckForSignal" value="1"/>
  <option name="AudioBoost" value="100"/>
  <option name="AlwaysOnTop" value="0"/>
  <option name="QuietScreenshots" value="0"/>
  <option name="UnmuteVolume" value="0"/>
  <option name="Muted" value="0"/>
  <option name="V4LInput" value="0"/>
  <option name="AudioMode" value="stereo"/>
  <option name="PalDKMode" value="0"/>
  <option name="ShowCC" value="0"/>
  <option name="FullScreen" value="0"/>
  <option name="WideScreen" value="0"/>
  <option name="FullscreenPosition" value="centre"/>
  <option name="DeinterlaceMethod" value="TelevisionFull"/>
  <option name="Frequencies" value="custom"/>
  <option name="ColourInvert" value="0"/>
  <option name="Norm" value="PAL"/>
  <option name="InputWidth" value="924"/>
  <option name="MirrorInput" value="0"/>
</tvtime>

```

In order to get sound please refer to the excellent instalation guide for Windows XP and hardware modification (this second bit applies to linux too)
[http://homepage.ntlworld.com/minkus/mm200pctv/]("http://homepage.ntlworld.com/minkus/mm200pctv/")

---

### Post by WarGasm on 2006-09-29
I followed your steps until this:
 ```
vikernes@vikernes-desktop:~$ tvtime-scanner
Reading configuration from /etc/tvtime/tvtime.xml
Scanning using TV standard PAL.
videoinput: Cannot open capture device /dev/video0: No such file or directory

```

what can I do ? please help !

---

### Post by PartickThistle on 2006-09-29
If you have /dev/video do this;
```
sudo ln -s /dev/video /dev/video0
```

---

### Post by domino on 2006-09-29
Do you have to manually un-mute your line-in setting in Volume Control in order to hear TV sound? I seem to have a problem with this on Dapper which didn't exist in Breezy, no matter whow I conig  /etc/modprobe.d/bttv.

---

### Post by chojin on 2006-12-10
WARNING to people trying this. I have a Twinhan VisionPlus HDTV PCI and this method caused ubuntu to hang consistently even in recovery mode. I had to use a livecd to repair it. The drivers are ridiculously buggy for this card.

Using a vanilla ubuntu setup, the card is detected, but NO device nodes are created (although dmesg says it does create a dvb0, this doesn't exist in the filesystem).

So if you have this card, don't bother with this method... I don't think there's ANY way to get this card going under ubuntu :|

---

### Post by darnyte on 2007-08-05
under ubuntu feisty all you have to do is install tv-time and it works.. no module setup or config. I am guessing that the module is built into kernel now.. don't know about audio haven't tested it yet...

---

### Post by jimufa on 2007-11-27
Hi, I'am Milton from Venezuela i have a tv card lifeview with the conexant fusion 878A chip on it,
milton@milton-desktop:~$ sudo lsmod |grep videodev
videodev               29312  1 bttv
v4l2_common            18432  2 bttv,videodev
v4l1_compat            15364  2 bttv,videodev
Tvtime gives mi a blue screen someone know how to put this card to work in Ubuntu 7.10
Thanks

---

### Post by gtr225 on 2008-01-06
Thanks for the guide, this worked perfect for my Maxron maxtv tuner card. Now I use Tvtime to watch satelite television on my computer monitor while I browse the web. However are there any programs that could allow me to record tv shows to my computer?

---

### Post by pointfivezero on 2008-02-05
> **gtr225 said:**
> Thanks for the guide, this worked perfect for my Maxron maxtv tuner card. Now I use Tvtime to watch satelite television on my computer monitor while I browse the web. However are there any programs that could allow me to record tv shows to my computer?

I think you might find [this page at linuxtv]("http://www.linuxtv.org/v4lwiki/index.php/TV_Recording") to be useful...


Now as a side note to get line-in working :(

---

### Post by pointfivezero on 2008-02-05
> **art2003 said:**
> 
...
In order to get sound please refer to the excellent instalation guide for Windows XP and hardware modification (this second bit applies to linux too)
[http://homepage.ntlworld.com/minkus/mm200pctv/]("http://homepage.ntlworld.com/minkus/mm200pctv/")

Awesome, thanks for the link! Since I don't have a working line-input (something to do with a rear_switch that doesn't work) this reminded about the spare cd-in wires I have around somewhere. that might just do the trick

Thanks!

---

### Post by ciroxyz on 2008-03-05
thanks man, works great with kworld (v-stream) bt878 chipset... had to un-mute sound in volume controls...

cheers

---

### Post by bscabl on 2008-11-11
i almost have it all working, except... 

Scanning using TV standard NTSC.
Scanning from  44.00 MHz to 958.00 MHz.

says no frequency
and then when i start tvtime i have a fuzzy black and white channel, and thats it.. no channels and it says 'no frequency' at the top.. im missing one thing prolly and im not sure what it is... 
ubuntu 8.04.. help?

---

### Post by pneaveill on 2009-02-11
Is this still an active thread? If so, here is the background on mine that I cannot get to work

> paul@basement:~$ uname -a
Linux basement 2.6.24-23-generic #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686 GNU/Linux
paul@basement:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:0870 Logitech, Inc. QuickCam Express
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
paul@basement:~$ /sbin/lsmod | grep -i usb
usbcore               146412  4 quickcam,ehci_hcd,uhci_hcd

Any help is appreciated.

---

### Post by pneaveill on 2009-03-06
Any help is appreciated.[/quote]

After months of working on this, I got it to work with sound and color until I grocked the tvtime.xml file as directed.  Also wonders if the entry on there is for PAL, rather than the needed NTSC standard here in America.

Any insight at all?

=================
Quick update:
Rebooted and lost audio from BTTV; checked volume applet and all seems ok.  Can someone please advise on what happened?

---

### Post by art2003 on 2009-03-08
I definately have PAL, so I have no idea how my Howto should be changed to work with NTSC.

Although I still have the bt878 card, I no longer use it as I have newer hardware connected via HDMI to a TV

---

### Post by art2003 on 2009-03-08
hello Paul,

run 
ls /dev/video*

You probably have more than one device as your logitech webcam might be using one

also add the bt modules you can see from lsmod to the blacklist
and then load them manually with sudo modprobe until things work
then you can add the modules that work for you manually to /etc/modprobe.d/

> **pneaveill said:**
> Is this still an active thread? If so, here is the background on mine that I cannot get to work



Any help is appreciated.

---

### Post by art2003 on 2009-03-08
Yes, in short VDR can do the job, but to watch satellite TV with it, best if you find an appropriate VDR howto.

I am of a mind to try this project:

[http://www.eurocardsharing.com/f273/howto-getting-hvr-4000-nova-hd-cards-working-linux-using-s2api-105681](http://www.eurocardsharing.com/f273/howto-getting-hvr-4000-nova-hd-cards-working-linux-using-s2api-105681)

> **gtr225 said:**
> Thanks for the guide, this worked perfect for my Maxron maxtv tuner card. Now I use Tvtime to watch satelite television on my computer monitor while I browse the web. However are there any programs that could allow me to record tv shows to my computer?

---

### Post by pneaveill on 2009-03-17
> **art2003 said:**
> hello Paul,

run 
ls /dev/video*

You probably have more than one device as your logitech webcam might be using one

also add the bt modules you can see from lsmod to the blacklist
and then load them manually with sudo modprobe until things work
then you can add the modules that work for you manually to /etc/modprobe.d/

```
 ls /dev/video*
/dev/video0 
```removed the camera, as it is one of those that the manufacturer dumped and does not support well. Pity

------- EDIT ---------

Not totally sure, but think I mistakenly placed the contents of lsusb, instead of lspci previously:

```
 lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
02:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:0a.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
02:0b.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
02:0b.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
02:0c.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
```

---

### Post by pneaveill on 2009-03-20
/var/log/messages reveals this, but clueless how to interpret

```

[ 1212.648017] bttv0: PLL can sleep, using XTAL (28636363).
[   33.627888] bttv: driver version 0.9.17 loaded
[   33.627896] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   33.627998] bttv: **[COLOR=Blue]Bt8xx card found (0).[/COLOR]**
[   33.628018] ACPI: PCI Interrupt 0000:02:0b.0[A] -> GSI 23 (level, low) -> IRQ 18
[   33.628036] bttv0: Bt878 (rev 2) at 0000:02:0b.0, irq: 18, **[COLOR=Blue]latency: 32[/COLOR]**, mmio: 0xf47fe000
[   33.628259] bttv0: detected: STB TV PCI FM, Gateway P/N 6000704 [card=40], PCI subsystem ID is 10b4:2636
[   33.628264] bttv0: using: Modular Technology MM201/MM202/MM205/MM210/MM215 PCTV, bt878 [card=23,insmod option]
[   33.628347] bt878 #0 [sw]: Test OK
[   33.660009] **[COLOR=Blue]bttv0: Modtec: Unknown TunerString: ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ&6^P&#381;ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ&6^P&#381;[/COLOR]**
[   33.660018] bttv0: **[COLOR=Blue]tuner type=18[/COLOR]**
[   33.758132] bttv0: i2c: checking for Bt832 @ 0x88... not found
[   33.766223] bttv0: i2c: checking for Bt832 @ 0x8a... not found
[   33.770550] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   33.798531] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   34.433952] tuner 0-0063: chip found @ 0xc6 (bt878 #0 [sw])
[   34.434002] tuner-simple 0-0063: type set to 18 (**[COLOR=Blue]Temic PAL[/COLOR]**_I (4066 FY5))
[   34.434006] tuner 0-0063: type set to **[COLOR=Blue]Temic PAL[/COLOR]**_I (4066 F
[   34.434011] tuner-simple 0-0063: type set to 18 (Temic PAL_I (4066 FY5))
[   34.434015] tuner 0-0063: type set to Temic PAL_I (4066 F
```

I live in the states, so I need NTSC, not PAL. Unsure where to go from here.

---

### Post by mike4ubuntu on 2009-03-24
I have a Pinnacle PC-TV card which has the bt878 in it with Alpha 6 of Jaunty Jackalope.  I also have a Logitech Quickcam webcam in the system.  So there are more than one /dev/video(x) ports.  You can get the video to work with this by using the device options on xawtv and tvtime like this:

```

xawtv -vbidev /dev/vbi0 -c /dev/video1 -C /dev/dsp -remote -global:filter "linearblend" -b 24 -gl

```
```

tvtime --device=/dev/video1 --frequencies=us-cable --norm=NTSC

```

My tv card is /dev/video1.  The webcam uses /dev/video0.  The problem I have is with sound.  I can't get the sound from the tv card, but the video is fine.  I'm guessing the sound from the tv card is on /dev/dsp1 or /dev/dsp2, but setting that with -C option on the xawtv command doesn't work.  I've also tried the sox work-around with no success:

```

sox -r 32000 -t ossdsp /dev/dsp2 -t ossdsp /dev/dsp & pid=$!

```

My sound works ok otherwise, just not with the TV Card.  I've tried both the /dev/dsp1 and /dev/dsp2, but it doesn't work for either one.  I plan to experiment with setting different mixer configs to see if that help.

---

### Post by pneaveill on 2009-03-24
Guess I could have stated my issues a little more clearly: I have video and that part is wonderful. The problem is sound. I have tried the internal audio patch cable attached to sound card and without. I have checked all the places I could find to mute/unmute something.  

Has to be something I am missing. But what?

---------- Update ---------
I tried your xawtv suggestion below there and got a bunch of silent static. 

your tvtime suggestion gave me video but no sound (as I had before).

The sox one failed to find the ossdsp module

---

### Post by THE-DUKE on 2009-03-26
> **pneaveill said:**
> Guess I could have stated my issues a little more clearly: I have video and that part is wonderful. The problem is sound. I have tried the internal audio patch cable attached to sound card and without. I have checked all the places I could find to mute/unmute something.  

Has to be something I am missing. But what?

---------- Update ---------
I tried your xawtv suggestion below there and got a bunch of silent static. 

your tvtime suggestion gave me video but no sound (as I had before).

The sox one failed to find the ossdsp module

Try installing libsox-fmt-oss, libsox-fmt-alsa, libc6 from the terminal in order to get ossdsp. I forget the exact command, but lemme know if it doesn't work, and I'll look deeper into my dpkg and Synaptic logs. I have the same problem, no sound with tvtime, so I'm using sox, and initially it wasn't finding ossdsp. I'm thinking I'll dedicate a good amt of time to try and hack a solution to this problem soon.

---

### Post by pneaveill on 2009-03-26
> **THE-DUKE said:**
> Try installing libsox-fmt-oss, libsox-fmt-alsa, libc6 from the terminal in order to get ossdsp. I forget the exact command, but lemme know if it doesn't work, and I'll look deeper into my dpkg and Synaptic logs. I have the same problem, no sound with tvtime, so I'm using sox, and initially it wasn't finding ossdsp. I'm thinking I'll dedicate a good amt of time to try and hack a solution to this problem soon.

```
sox soxio: Can't open input file `/dev/dsp2': No such file or directory
```

```
sox -r 32000 -t ossdsp /dev/dsp -t ossdsp /dev/dsp & pid=$!
```

Looks like it is scanning now, will update upon completion

---

### Post by art2003 on 2009-03-27
In the setup you have video but no audio please
refer to this other howto of mine:
[http://ubuntuforums.org/showthread.php?p=6960534#post6960534](http://ubuntuforums.org/showthread.php?p=6960534#post6960534)

Point 3, for installing OSS instead of ALSA which can be rather buggy

of course the line

ln -s /dev/oss/oss_hdaudio0/spdout1 /dev/dsp

would be different for you according to what works
but you can do 
ls /dev/oss -l
to see a list of devices and try them one by one

---

### Post by pneaveill on 2009-03-29
> **art2003 said:**
> In the setup you have video but no audio please
refer to this other howto of mine:
[http://ubuntuforums.org/showthread.php?p=6960534#post6960534](http://ubuntuforums.org/showthread.php?p=6960534#post6960534)

Point 3, for installing OSS instead of ALSA which can be rather buggy

of course the line

ln -s /dev/oss/oss_hdaudio0/spdout1 /dev/dsp

would be different for you according to what works
but you can do 
ls /dev/oss -l
to see a list of devices and try them one by one

 ls /dev/oss -l
```
ls: cannot access /dev/oss: No such file or directory
```$ ls /dev/dsp -l
```
crw-rw----+ 1 root audio 14, 3 2009-03-29 13:03 /dev/dsp
```

======= edit ======
I am not running hdmi, so do I really need to load oss?  All I want to do is either run VGA or regular video to the screen. Why is this so complicated?

---

### Post by art2003 on 2009-03-30
Well, OSS in general has better sound quality but some applications (for example Skype for linux) do not support it

You could also just try to update your ALSA to 1.19, there is a script in my other thread I mentioned before.
Also run alsamix and make sure nothing that matters is muted, if that doesn't do the trick then give OSS a try...

> **pneaveill said:**
> ls /dev/oss -l
```
ls: cannot access /dev/oss: No such file or directory
```$ ls /dev/dsp -l
```
crw-rw----+ 1 root audio 14, 3 2009-03-29 13:03 /dev/dsp
```

======= edit ======
I am not running hdmi, so do I really need to load oss?  All I want to do is either run VGA or regular video to the screen. Why is this so complicated?

---

### Post by pneaveill on 2009-03-30
> **art2003 said:**
> Well, OSS in general has better sound quality but some applications (for example Skype for linux) do not support it

You could also just try to update your ALSA to 1.19, there is a script in my other thread I mentioned before.
Also run alsamix and make sure nothing that matters is muted, if that doesn't do the trick then give OSS a try...

Not sure what happened, but I followed your instructions on setting up OSS and rebooted like it told me to. Upon reboot, I lost all sound. Could not find the actual link to redo the alsa.  If you could point me in the right direction, would appreciate it.

----- update ---
Not sure if this one is it,[COLOR=Blue] **but it worked**[/COLOR] to get system and music audio back (will work on TV audio tomorrow after work) [https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems](https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems)

---

### Post by pneaveill on 2009-04-01
Please understand that I am ticked at this column here. Everything was fine until I did your last couple steps on the first post.  From that point on, everything that I did has made it worse.  Is there a way to restore back to defaults without those last couple steps there on that first post without having to wipe/reload?

The last suggestion you had me do there for some reason dropped my channels from 50+ down to this:```
Scanning from  44.00 MHz to 958.00 MHz.
Found a channel at 373.00 MHz (372.00 - 374.00 MHz), adding to channel list.
Found a channel at 379.50 MHz (378.75 - 380.00 MHz), adding to channel list.
Found a channel at 385.00 MHz (384.00 - 386.00 MHz), adding to channel list.
Found a channel at 397.00 MHz (396.00 - 398.00 MHz), adding to channel list.
Found a channel at 409.25 MHz (408.50 - 410.00 MHz), adding to channel list.
Found a channel at 421.00 MHz (419.75 - 422.00 MHz), adding to channel list.
Found a channel at 427.25 MHz (426.50 - 428.00 MHz), adding to channel list.
Found a channel at 438.75 MHz (437.50 - 440.00 MHz), adding to channel list.
Found a channel at 445.00 MHz (444.00 - 446.00 MHz), adding to channel list.
Found a channel at 463.00 MHz (461.75 - 464.00 MHz), adding to channel list.
Found a channel at 469.00 MHz (468.00 - 469.75 MHz), adding to channel list.
Found a channel at 474.75 MHz (473.75 - 475.75 MHz), adding to channel list.
Found a channel at 481.00 MHz (480.00 - 482.00 MHz), adding to channel list.
Found a channel at 486.75 MHz (485.50 - 488.00 MHz), adding to channel list.
Found a channel at 505.00 MHz (504.00 - 506.00 MHz), adding to channel list.
Found a channel at 535.50 MHz (534.75 - 536.00 MHz), adding to channel list.
Found a channel at 547.00 MHz (545.75 - 548.00 MHz), adding to channel list.
```

Changed out both the card and the TV cable hoping that one of them was the issue, but have only those limited channels and no sound.

Please help

---

### Post by pneaveill on 2009-04-09
Can anyone help me get this thing to reset back to before I started without wiping and rebuilding the whole thing?  I tried ```
sudo apt-get remove --purge each of the files
``` and it supposedly removed them.  However. once I went back to reinstall the stuff, the errors that I have been receiving all along are still there.

---

### Post by tamashumi on 2010-05-28
Guys, I solved sound problem by just skipping point 2) of this guide on Karmic

I mean remove or comment all in /etc/modprobe.d/bttv
Probably commenting 1 line inside or changing some param will be enough but I'm not sure which one and all works fine without any config for bttv module.

After changing module configuration you need to reload module.
Unload module:
```
sudo modprobe -r bttv
```
Load module again:
```
sudo modprobe bttv
```

Do this each time you change /etc/modprobe.d/bttv file for testing (if just removing doesn't help).

---

### Post by Fitch on 2010-09-12
My problem is as below:

I have had a 4 camera card for nearly a year now, no problem.  
I have now had to install a second  4 camera card to cover the car park and corridors.

so I have card=77,105 on bttv.conf and that's it. 
 
Needless to say, it doesn't work 'cos I can't remember what else to do. 
 
The original 4 cameras are fine and work well.  I'm just missing  something...  (actually, I know I'm missing /dev/video1 for a start!) 
 
brafferton@cameras:~$ dmesg | grep bttv 
[   16.507945] bttv: driver version 0.9.18 loaded 
[   16.507948] bttv: using 16 buffers with 2080k (520 pages) each for capture 
[   16.508347] bttv: Bt8xx card found (0). 
[   16.508600] bttv 0000:01:08.0: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19 
[   16.508608] bttv0: Bt878 (rev 17) at 0000:01:08.0, irq: 19, latency: 32, mmio: 0xf8fff000 
[   16.508626] bttv0: detected: Provideo PV143A [card=105], PCI subsystem ID is aa00:1430 
[   16.508628] bttv0: using: GrandTec Multi Capture Card (Bt878 [card=77,insmod option] 
[   16.508631] IRQ 19/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs 
[   16.508665] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init] 
[   16.508743] bttv0: tuner absent 
[   16.508830] bttv0: registered device video0 
[   16.508889] bttv0: registered device vbi0 
[   16.508908] bttv0: PLL: 28636363 => 35468950 .. ok 
brafferton@cameras:~$ 
 
I did modprobe bttv and restarted, but all thats happened is that  zoneminder is always stopped when it reloads, and it takes an  interminable time to actually respond to any commands. 

ls /dev/video* just comes up with /dev/video0
lspci | grep Bt878 just comes up with the original card.

---

### Post by pickarooney on 2010-10-31
I can't get my bt878 card (Hauppauge WintV) to pick up any channels in Lucid. It worked out of the box on Jaunty and previous releases. I've tried everything here and more but still I just get a blue screen. I don't understand why Lucid doesn't support my card.

---

### Post by aaronLund on 2012-01-02
> **Fitch said:**
> My problem is as below:

I have had a 4 camera card for nearly a year now, no problem.  
I have now had to install a second  4 camera card to cover the car park and corridors.

so I have card=77,105 on bttv.conf and that's it. 
 
Needless to say, it doesn't work 'cos I can't remember what else to do. 
 
The original 4 cameras are fine and work well.  I'm just missing  something...  (actually, I know I'm missing /dev/video1 for a start!) 
 
brafferton@cameras:~$ dmesg | grep bttv 
[   16.507945] bttv: driver version 0.9.18 loaded 
[   16.507948] bttv: using 16 buffers with 2080k (520 pages) each for capture 
[   16.508347] bttv: Bt8xx card found (0). 
[   16.508600] bttv 0000:01:08.0: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19 
[   16.508608] bttv0: Bt878 (rev 17) at 0000:01:08.0, irq: 19, latency: 32, mmio: 0xf8fff000 
[   16.508626] bttv0: detected: Provideo PV143A [card=105], PCI subsystem ID is aa00:1430 
[   16.508628] bttv0: using: GrandTec Multi Capture Card (Bt878 [card=77,insmod option] 
[   16.508631] IRQ 19/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs 
[   16.508665] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init] 
[   16.508743] bttv0: tuner absent 
[   16.508830] bttv0: registered device video0 
[   16.508889] bttv0: registered device vbi0 
[   16.508908] bttv0: PLL: 28636363 => 35468950 .. ok 
brafferton@cameras:~$ 
 
I did modprobe bttv and restarted, but all thats happened is that  zoneminder is always stopped when it reloads, and it takes an  interminable time to actually respond to any commands. 

ls /dev/video* just comes up with /dev/video0
lspci | grep Bt878 just comes up with the original card.

Fitch,

Did you figure this out?

I'm having problems with my cameras "rolling" up and/or down.


I did this ( taken from [this]("http://www.zoneminder.com/wiki/index.php/Pico2000") page):

```
options bttv card=77 tuner=4 radio=0 triton1=0 vsfx=0 autoload=0

```

Things seem better than they were but this "rolling" business is killing me.

Here's my dmesg for bttv.


```

aaron@aaron-ringo:~$ dmesg | grep bttv
[   34.416381] bttv: driver version 0.9.18 loaded
[   34.416393] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   34.432235] bttv: Bt8xx card found (0).
[   34.432283] bttv 0000:01:00.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[   34.432307] bttv0: Bt878 (rev 17) at 0000:01:00.0, irq: 11, latency: 132, mmio: 0xf4000000
[   34.433031] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   34.433089] bttv0: gpio: en=00000000, out=00000000 in=00f36fff [init]
[   40.956093] bttv0: tuner type unset
[   40.972121] bttv0: registered device video0
[   40.972846] bttv0: registered device vbi0

```

Any advice so that my cameras don't roll?

I'll admit to not poking around a bunch with them so perhaps there's an easier fix.  Just checking around.  Thanks!

---

