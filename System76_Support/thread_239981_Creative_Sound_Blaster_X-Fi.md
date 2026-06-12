---
title: "Creative Sound Blaster X-Fi"
date: 2006-08-20
forum: System76 Support
---

### Post by zentagonist on 2006-08-20
As far as I know, ALSA does not support the Sound Blaster X-Fi cards AT ALL.  And Creative's own [http://opensource.creative.com/soundcard.html]("http://opensource.creative.com/soundcard.html") says "The X-Fi series of products are not supported under Linux. Closed-source drivers will be available for the X-Fi series of sound cards in the second quarter of 2007. These drivers will have full support for ALSA (playback, recording, mixer, MIDI, synthesis) and OpenAL 1.1 (with EAX effects)." ... However, this: [http://system76.com/product_info.php/cPath/2/products_id/173]("http://system76.com/product_info.php/cPath/2/products_id/173") clearly shows "7.1 Surround Creative Sound Blaster X-Fi Xtreme" as a configuration choice under the _Sound_ option.  

Can anyone tell me what's going on here?

---

### Post by ELD on 2006-08-20
They obviously havn't looked up the facts :P

---

### Post by crichell on 2006-08-20
I think this may be a typo on the site - we've been using a number of different sound blaster cards - have to check into it.

---

### Post by puppy on 2006-08-29
Sorry guys, just saw this post and I should have replied. I'm keeping a close eye on developments as I have a Creative X-Fi card. The situation as I understand it is that as of right now there is no support for the Creative X-Fi, either closed (from Creative) or open (from the ALSA people) and that there won't be until 2007 at least  ](*,)

---

### Post by Panhead Bill on 2006-09-04
I just sent Creative customer support a note asking when ther would be linux support for their card.

I then asked if I should return the card to place of purchase.

Maybe a little push from customers *might* help.

---

### Post by brazen521 on 2007-04-20
Found a driver that works for the Creative X-fi cards.  I can't vouch for the other X-fi cards but I have an X-fi Xtreme Audio and it works fine.  The only catch is that the ubuntu volume manager won't work, so you need to use the volume knob on you speakers.  Kind of a downer, but at least there's audio, right?  If you feel like giving it a shot, go to the site below and post your results on here.  It actually detected my card as a sound blaster 7.1 or something like that, but I now have perfect stereo sound.  (Don't have 5.1, decided to stick with my klipsch promedia 2.1 setup)  Anyway, good luck!

[http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi)

---

### Post by nadamotion on 2007-04-21
I've got at X-FI card aswell but since I'm a total newbee regarding linux, I am not able to install the driver properly.

Brazen521, could you please give me some info as to how you installed the driver and got it working?

---

### Post by iwroboto on 2007-04-23
yes.
please give more details. i installed .deb to minimal success and error, then finally was able to uninstall after downloading tar and running dpkg.

as far as after bad package was removed: I was able to get OSS managing devices by "sudo cp -R ...." with tar contents, but was unable to switch device from onboard AC97 to XFI


any details would help

---

### Post by tschuliaen on 2007-05-01
I own a Creative Sound Blaster x-fi **audio** as well and tried to install OSS drivers.

Unfortunately ossinfo just told me that there were no supported cards. That was all. I only tested it this from the live ubuntu 7.04 cd. Does this make a difference? Is a restart needed to load the OSS stuff correctly?

I'm probably not switching from winxp to ubuntu on my desktop pc yet because of lacking sound...

To brazen521:  I would really apreciate some more information about how u made ur card working...i googled for hours and couldnt find anything else about how to make the downgraded x-fi card working...

Obviously its based on the old audigy chip...?

Thanks (first post hihi)

---

### Post by adeling on 2007-05-06
FYI: My new Ubuntu installation (7.04) already includes that driver and my sound doesn't work on the X-Fi Gamer.

---

### Post by BrandonTheBlack on 2007-05-24
I tried the OSS driver, but I get this message:

```
sh /usr/lib/oss/build/install.sh

OSS build environment set up for REGPARM kernels

    C library headers (glibc-devel or build-essential)

Error: The above Linux package(s) seem to be missing from your system.
       Please install them and then try to install OSS again.

Please refer to the documentation of your Linux distribution if you
have problems with installing the packages.

You can use the following commands to download and install all
required packages:

  apt-get install build-essentials

```

I tried doing "sudo apt-get build-essentials" but it can't find it.  Can anyone help me get this working?

---

### Post by palintheus on 2007-05-24
> **BrandonTheBlack said:**
> 

I tried doing "sudo apt-get build-essentials" but it can't find it.  Can anyone help me get this working?


You might try

```
$ sudo apt-get install build-essentials
```

---

### Post by whilchyjd on 2007-06-29
Hi,

I've installed Ubuntu Feisty and I have a Creative XFi Extreme Audio card. It doesn't work, I try with the OSS but this card do not appear on the list of working cards for the drivers.
The card appears on Alsa, and I try with Alsa drivers too, but it stills without sound. If anyone knows how to solve it please tell me how. In fact on Alsa-project site they says that this sound card it's just a SB Live 24bit with a new name, you can see it [here]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+X-Fi+Extreme+Audio.&chip=SB0790&module=ca0106")

I appreciate very much your time and your help.

Best Regards.

Jorge Whilchy.-

---

### Post by thomasaaron on 2007-07-02
Admittedly, I don't know much about Creative's X-Fi cards, and I'm not sure how much has changed since this link...

[http://ubuntuforums.org/showthread.php?t=239981](http://ubuntuforums.org/showthread.php?t=239981)

was posted.  But it doesn't look overly promising.
However, it is worth a look, as it appears there has been limited success with them.

---

### Post by aptiaa on 2007-07-05
Hi, I have the same problem. I have an X Fi Elite Pro. 

The really strange thing (for me) is that in a previous try I installed Ubuntu Feisty under Vmware and the sound worked just fine. It detected my soundcard as ES1371...

Now I installed Ubuntu in a dual boot with  Vista and the sound just doesn't work.

Now, under Vmware it did work. Is there a possible solution for this???

I am completely new to linux.

Thanks.

---

### Post by gonesolo on 2007-07-08
> **aptiaa said:**
> Hi, I have the same problem. I have an X Fi Elite Pro. 

The really strange thing (for me) is that in a previous try I installed Ubuntu Feisty under Vmware and the sound worked just fine. It detected my soundcard as ES1371...

Now I installed Ubuntu in a dual boot with  Vista and the sound just doesn't work.

Now, under Vmware it did work. Is there a possible solution for this???

I am completely new to linux.

Thanks.

The reason VMWare worked is because it emulates a different sound card. Once your sound card is working in the HOST OS then it should work ok in the GUEST OS aswell as the emulated card is well supported (and actually quite old)

However when you install Ubuntu native (not in a Virtual machine) it has to identify your actual hardware and install the correct driver - thats where the problem lies with the X-Fi

---

### Post by KushMaster on 2007-09-06
I have a Sound Blaster X-Fi sound card, and i am having truble installing my drivers for it as well, can anyone give a detailed explenation on how to do it ?

---

### Post by rabidrabbit on 2007-09-08
> **gonesolo said:**
> The reason VMWare worked is because it emulates a different sound card. Once your sound card is working in the HOST OS then it should work ok in the GUEST OS aswell as the emulated card is well supported (and actually quite old)

However when you install Ubuntu native (not in a Virtual machine) it has to identify your actual hardware and install the correct driver - thats where the problem lies with the X-Fi

yea it actually uses windows directsound drivers, a little bit different from emulation, but same effect

---

### Post by Silent Warrior on 2007-09-09
For what it's worth, I saw at Creative's forum recently that they expect to have 64-bit beta-drivers for X-Fi available at the end of the year. Perhaps not a 'HOORAAAAAY!', but at the very least, it's progress.

---

### Post by ronaldo1 on 2007-09-10
Is there a way i can force alsa to assume my X-FI is just a soundblaster card? Like by editing /etc/modprobe.d/alsa-base or something?

---

### Post by Silent Warrior on 2007-09-11
I swear, honest to god, that I have no idea. Besides, chances are it's less trouble to wait for Creative to actually deliver...

---

### Post by pierlalo on 2007-10-06
Hi. I found X-FI linux 64 beta driver from CREATIVE Sound Blaster site : [http://ca.creative.com/support/downloads/download.asp?MainCategory=209&nRegionFK=&nCountryFK=&nLanguageFK=&sOSName=Linux&region=1&Product_Name=Sound+Blaster+X-Fi+Fatal1ty&Product_ID=14000&modelnumber=&driverlang=1033&OS=12&drivertype=0&x=22&y=11](http://ca.creative.com/support/downloads/download.asp?MainCategory=209&nRegionFK=&nCountryFK=&nLanguageFK=&sOSName=Linux&region=1&Product_Name=Sound+Blaster+X-Fi+Fatal1ty&Product_ID=14000&modelnumber=&driverlang=1033&OS=12&drivertype=0&x=22&y=11)
and installation info (GUTSY) : [http://blackbox.lostwave.net/x-fi/readme.txt](http://blackbox.lostwave.net/x-fi/readme.txt)
Did somebody tried this on FEISTY ?

---

### Post by Jaspernak on 2007-10-09
Yeah, unfortunately this driver does not work with Creative Soundblaster Xfi Extreme Audio based on the CA0110 chip.  It returns an 'unsupported product' error.

Honestly, I don't understand Creative's naming scheme. They have completely different chipsets in products that are named nearly identically!

In my case the Xfi chip is embedded into my MSI P6N Diamond motherboard.  I hate the idea of addding an additional sound card to the PC, but it seems that may be my only choice...

---

### Post by Xanderfoxx on 2007-10-09
Here's the latest:

Taken from <[http://opensource.creative.com/](http://opensource.creative.com/)> at Tuesday, October the 9th, of 2007, at 4:44 PM:

"**News:**

September 25, 2007 -- **X-Fi 64bit BETA Linux drivers are now available.**
For more information SEE Soundcard Support

April 30, 2007 -- Creative plans to make proprietary (closed source) drivers available for the X-Fi series of sound cards. SEE Soundcard Support for updated details. These drivers should have full support for ALSA (playback, recording, mixer, MIDI, synthesis) and OpenAL 1.1 (with EAX effects).

November 29, 2005 -- The Creative section of the ALSA sound card matrix has been updated. Note that the Creative X-Fi series of products is not supported under Linux at this time."

Keeping ya posted -- Alex Maurin

---

### Post by ar1stotle on 2007-10-18
Well, that's a good start. I'm waiting for a 32bit version :-/

---

### Post by Lexrst on 2007-11-02
I have downloaded the Beta XFi driver and attempted to install it on Gutsy x64.  Here is the result of my attempt to run the installer:

lexrst@ubuntu:~/Desktop/XFiDrv_Linux_US-1.04$ sudo ./installer
This product only support 64-bit Operating Systems
Setup will now exit
lexrst@ubuntu:~/Desktop/XFiDrv_Linux_US-1.04$ 

What's up with that?

Anyone have any clue as to why the driver is inaccurately detecting the OS version?

Thanks!

Lexrst

---

### Post by Silent Warrior on 2007-11-04
Ooo, the first time I can actually PROVIDE support! As for the installer's inability to detect 64-bit, I think that happened to everyone. Dig this: You have to patch the installer. I don't know the exact line, but there is some command that needs an extra switch to work as it should. There is a topic over on the Gentoo forums that's come farthest with this driver, as far as I know.
Step 1: Go to [http://olausson.de/x-fi/](http://olausson.de/x-fi/) and check out the readme, and you probably won't have to go through the entire topic at...
Step 2: [http://forums.gentoo.org/viewtopic-p-4287209.html#4287209](http://forums.gentoo.org/viewtopic-p-4287209.html#4287209)

Where it all becomes a question about whether or not it's worth the trouble is that you'll probably have to recompile your kernel. Apparently Ubuntu Naturel has some option set as SLAB that should be set as SLUB in order to get the driver installed. I have successfully compiled it - using the patch available at the german site (otherwise it won't compile on gcc 4.x) - but dmesg says something about m_alloc something or other, and 'make install' fails.

---

### Post by jakethecake on 2007-12-29
Last week I broke my SPDIF port on my motherboard (Nforce 680i) . Soldering broke where the module connect to the motherboard.

Since Creative had such crappy Linux support*, I went to all of the big computer stores in my neighborhood, (Stockholm, inner city). And I really tried to find another sound card brand. 
-They only had creative in stock.

I almost got on the xfi love train; 
But ended up, opting in on the monopoly and bought a 'Sound Blaster Audigy SE' and a mini SPDIF converter. Since the card had no proper SPDIF output plug. 

* ( non POSIX sh install script, you had to apply a 1200+ lines C/SH patch, no support for vanilla ubuntu/redhat/suse kernels. )

Thanks Creative. :sad:

Edit

It seams I need creative's external SPDIF IO box. 'SPDIF' on the Audigy box and in the product description. But sold seperatly. Grrreat.  :sad:
[http://www.soundblaster.com/products/product.asp?category=1&subcategory=16&product=1780](http://www.soundblaster.com/products/product.asp?category=1&subcategory=16&product=1780)

---

### Post by brn80 on 2008-01-13
> **brazen521 said:**
> Found a driver that works for the Creative X-fi cards.  I can't vouch for the other X-fi cards but I have an X-fi Xtreme Audio and it works fine.  The only catch is that the ubuntu volume manager won't work, so you need to use the volume knob on you speakers.  Kind of a downer, but at least there's audio, right?  If you feel like giving it a shot, go to the site below and post your results on here.  It actually detected my card as a sound blaster 7.1 or something like that, but I now have perfect stereo sound.  (Don't have 5.1, decided to stick with my klipsch promedia 2.1 setup)  Anyway, good luck!

[http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi)

I know that post is pretty old, but in case other people were wondering and for reference, the Xtreme Audio is not a true X-Fi card; it's a rebranded Audigy (I think SE) hence the sound system recognizing the hardware.

---

### Post by adramalech on 2008-01-25
Okay guys from what I understand and what creative told me...it will be sometime before they will make it in slub instead of slab:(  and by then linux will have a newer compiler...creative really suxs...almost as bad as windows....ekkk!!!

I used kernelcheck [ http://kcheck.sourceforge.net/download.html ]( http://kcheck.sourceforge.net/download.html )

which when you set up the kernel you can opt to compile in slab...but the big problem is that kernel check will only give you the newest kernel not the 2.6.22.xx-generic but 2.6.23.xx which doesn't have alot of packages yet and is pretty much crap until it becomes main stream in like 6 months to a year...:lolflag:

I am still trying to figure out how i can install and compile 2.6.22.xx-generic in slab:confused:  becuase i am not going back to older kernels so i can have sound!!!

---

### Post by ninjkiran on 2008-02-01
Just a quick come in, but Auzentech should have a driver available shortly for their X-fi model card.  The Prelude, which would possibly be good news for all, in windows Auzens driver is superior to creatives given the amount of work they put into editing and the driver is amazing, and with a touch of magic all the x-fi cards were able to take advantage of it given the hardwares similarities.  That said if you plan on getting an x-fi you would probally want to go with Auzens though a little expensive but if you already have an x-fi hope should be coming soon!.

---

### Post by Wattos on 2008-03-03
Good news!

There is finally a WORKING beta driver for 32 bit and 64 bit. Its not done by Creative but OSS. 

[http://www.opensound.com/](http://www.opensound.com/)

it works for playback, and I can finally watch movies on my linux box. I dont think recording works yet fine, but its a start!

---

### Post by an4rew on 2008-03-08
That would mean i have to uninstall ALSA... i'm lost now :mad:

---

### Post by cdean on 2008-03-12
[http://blackbox.lostwave.net/x-fi/](http://blackbox.lostwave.net/x-fi/) is working for me thus far. I'm still rebuilding the kernel, but I should be able to make a patch file for everything that I've changed a little later.

---

### Post by Tmanisaur on 2008-03-16
I just found this thread today, and have a Creative Sound Blaster X-Fi Fatality Champion Platinum (which is a big name for a card that doesn't yet work in Linux).

I'm a linux-n00b, but I'm going to take a crack at compiling the Blackbox solution.  If/when it works, I'll post my method here.

---

### Post by cdean on 2008-03-24
There's also this thread with a HOWTO, but as of 2008 March 24, I have yet to get it functioning. No errors, just stuttering.

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=571656](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=571656)

---

### Post by Jive Turkey on 2008-03-25
It might make you feel better to know that creative's drivers for windows dont work much better, or much more often.  I just pulled my sound blaster audigy2 card in favor of an M-audio after installing winXP because "setup cannot detect any supported hardware and will now exit"  The card worked well in gutsy, in fact better than it ever did in windows.

---

### Post by seanj on 2008-03-29
I have an X-Fi Extreme Gamer and get no sound.

---

### Post by blitz666 on 2008-04-14
Hello all.  After my prolonged absence from Ubuntu, I am back!  (Stopped using when 6.06 came out.)

I have Ubuntu 7.10 Gusty Gibbon in triple-boot with XP Home and Vista Ultimate, a feat which made myself very proud.  Anyway, to the matter at hand:

I have a Creative Soundblaster X-Fi Platinum.  It works perfectly in Vista Ultimate (x86) and XP Home (x86), but not in Ubunutu (x86).  Attempting to test anything in the sound preferences gives me the following error:

> audiotestsrc wave=sine freq=512 !
audioconvert ! audioresample !
gconfaudiosink: Could not open resource for
writing.
I have already attempted the OSS fix as posted a few places in this thread.  I cannot try the proprietary drivers, as I am not running Ubuntu x64.  Anyone else get an X-Fi Platinum to work?  An X-Fi Music will also help me, as they are the same card except that the Platinum comes with the breakout box.

---

### Post by romefolks on 2008-04-14
Same here..no sound from my Sound Blaster X-Fi? does anyone gotten it to work?

---

### Post by airjer on 2008-04-20
Ugh, my Xtreme Gamer does not output any sound either. If it isn't one thing, it's another heh. I don't get any sound from my onboard audio either.

---

### Post by cdean on 2008-04-20
[http://ubuntuforums.org/showthread.php?t=571656](http://ubuntuforums.org/showthread.php?t=571656)

It's working now.

---

### Post by mole1012000 on 2008-04-20
Anyone have the answer to getting the oss to work with teamspeak 2? From what i understand this could be asking for blood from a stone! but might as well ask.

Also how do you get the volume control working with oss 4.0?

Also if there is no way to get the mic to work on teamspeak and skype, is there anyway to get the oss drivers to work with vmware and to then install windows or linux as a virtual device then run said software on that system.

---

### Post by blitz666 on 2008-04-24
> **cdean said:**
> [http://ubuntuforums.org/showthread.php?t=571656](http://ubuntuforums.org/showthread.php?t=571656)

It's working now.

I do not have time at present to thread the whole thread.  Does it have instructions for 32-bit, or still only 64-bit?

---

### Post by NullHead on 2008-04-24
> **blitz666 said:**
> I do not have time at present to thread the whole thread.  Does it have instructions for 32-bit, or still only 64-bit?

The OSS section works for 32-bit and 64-bit.

---

### Post by blitz666 on 2008-04-24
All right.  I will try it tomorrow.  The last time I tried installing OSS it still did not work.

---

### Post by alraz on 2008-04-26
There are new X-Fi drivers for linux (Beta 2), which can be found here:
[http://connect.creativelabs.com/linux/Lists/Announcements/DispForm.aspx?ID=7](http://connect.creativelabs.com/linux/Lists/Announcements/DispForm.aspx?ID=7)

Still... i haven't been able to install them, the make process ends out with "Error 2", and gives no damn clue of what went wrong.

Hope someone else has more luck.

---

### Post by Alex6969 on 2008-04-26
I get the same "Error 2" message. This really blows =(

---

### Post by blitz666 on 2008-05-01
The good news: I was able to install the Soundblaster X-Fi drivers.

To do so:

Download package in post #47.
Extract the files.
Load console.
cd to the directory where you extracted.
Run by typing "sudo ./installer"
Restart, you should have sound on return.

The bad news: Every 5-10 boots, it stops working.  A reinstall fixes it.  I can live with that.

---

### Post by jmgilchr on 2008-05-15
I too get the "error 2" message....will they be fixing this soon, or should I just start shopping for a new soundcard?

---

### Post by NullHead on 2008-05-15
I'd do neither. If you look at my guide; there is a link to another guide witch explains how to install OSS, witch will get you and your sound card working very well very quickly. 

[http://ubuntuforums.org/showthread.php?t=571656](http://ubuntuforums.org/showthread.php?t=571656)

---

### Post by jmgilchr on 2008-05-16
The very first post states in large red font that it ill *not* work under 8.04 though....

---

### Post by NullHead on 2008-05-16
> **jmgilchr said:**
> The very first post states in large red font that it ill *not* work under 8.04 though....

I'm going to revise that ... There is a smaller section at the bottom of the page that you can use. 

> ***OSS***


Recommended:

Use this guide to install OSS: [http://ubuntuforums.org/showpost.php...81&postcount=2](http://ubuntuforums.org/showpost.php...81&postcount=2)

If OSS fails to install or update use this guild to help you uninstall it: [http://4front-tech.com/forum/viewtopic.php?t=2054](http://4front-tech.com/forum/viewtopic.php?t=2054)

Just use that little snippet and should get it working in no time at all ;)

---

### Post by EvoKing on 2008-07-06
> **brazen521 said:**
> Found a driver that works for the Creative X-fi cards.  I can't vouch for the other X-fi cards but I have an X-fi Xtreme Audio and it works fine.  The only catch is that the ubuntu volume manager won't work, so you need to use the volume knob on you speakers.  Kind of a downer, but at least there's audio, right?  If you feel like giving it a shot, go to the site below and post your results on here.  It actually detected my card as a sound blaster 7.1 or something like that, but I now have perfect stereo sound.  (Don't have 5.1, decided to stick with my klipsch promedia 2.1 setup)  Anyway, good luck!

[http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi)

I've tried to install that driver om my computer because I've got the same sound card as you but I can't get it working. can you give me detailed instructions or can you help me via remote desktop or something? I use version 8.04(Hardy) of Ubuntu


Sorry for my bad engalish, I'm Swedish.

---

### Post by freeloader105 on 2008-07-17
I just installed the OSS driver and got mixed results. WINE doesn't like it one bit, so no sound for WINE apps. Does the ALSA driver work with WINE then?

---

### Post by NullHead on 2008-07-17
Yes Creative's officially unofficial alsa driver will work with wine. I'd suggest running "*winecfg*" from a terminal and moving to the audio tab, and selecting OSS as the **ONLY**sound system to use. 

Wine should also work with OSS.

---

