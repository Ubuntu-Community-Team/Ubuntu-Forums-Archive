---
title: "Focusrite Saffire 6 USB"
date: 2010-05-17
forum: Ubuntu Studio
---

### Post by maghoxfr on 2010-05-17
I want to buy the Saffire 6 USB interface, from the available ones on my country it seems to be the best. For what I've read it doesn't have a driver for linux so it won't work under Lucid Lynx which is the OS I'm currently using.

I have read some mailing lists but they were from February, I haven't found anything new.

Does anyone have this interface running in Ubuntu or knows if it would run on the new 10.04?

Thank you very much

---

### Post by rbolio on 2010-06-16
I just bought one myself...

i'll let you know as soon as it arives, hopefully this week :D

---

### Post by Breambutt on 2010-06-17
I'm fairly certain it will fully work out of the box like most USB preamps and other devices. Focusrite even seem to support the firewire project, so thumbs up for them.

---

### Post by hardcopy on 2010-06-21
i bought one of these but havn't been able to get it to work yet (tried in lucid & karmic) so would be interested to see if anyone else gets it to work

---

### Post by maghoxfr on 2010-07-12
If you do, please post it.

---

### Post by dod666 on 2010-07-20
I am also looking to buy one of these interfaces to use with Ableton Live (the only thing I still use XP for). I would love to be able to use this with Ubuntu (Lucid) as this is the OS I use for everything else. I may just buy one soon to run on XP but will try getting to run on linux too.
I'll post the results on here be it Win or Fail!!!

---

### Post by maghoxfr on 2010-07-20
Thanks I'll be waiting!

---

### Post by pepun on 2010-07-24
hey!

i bought this interface last week and couldn't get it to work after hours of trying. i'm running lucid lynx and apparently the system doesn't recognize the interface as an audio device. i have also read these mailing list posts from february and some other stuff i found with google. but it really seems like there's noone who made it work properly.

sooo... any news from you guys...?! ;)

---

### Post by darsu on 2010-07-24
Back when I was on the market for a USB audio interface, I could not find *one single report* of someone being able to make this interface run on Linux. If you haven't bought one yet, don't buy one.

---

### Post by maghoxfr on 2010-07-24
The same here, when I was after an audio interface I couldn't find any report that assured the Saffire 6 worked on Linux, I've read, I think, the same mailing lists (from a guy named Pandu?)but it didn't have any conclusion. It's a shame because all I've read about the interface is great, and it's not expensive, I would have love to have it.

I hope you can return yours man...

Thanks all. If anyone manage to make it work I'll leave this thread open.

---

### Post by pepun on 2010-07-24
yeah, the mailing list with posts from a guy named pandu is the same i have read.
so i guess i'll just return my interface and get another one then. the guy from the shop said, if it doesn't work, it's no problem to return it. it's a pity anyway.

i might just try the saffire pro 24 now. it's a firewire one and a bit more expensive but people reported it to work with ffado. does anyone has some experiences with that?!

---

### Post by pepun on 2010-08-06
Just in case someone's interested... I have purchased  the saffire pro 24 firewire interface now instead of 6usb. And it works perfectly fine on lucid with ffado!

---

### Post by AutoStatic on 2010-08-06
pepun, thanks for the info, that's great news! I'm eagerly awaiting a Saffire Pro 24 too.

---

### Post by maghoxfr on 2010-08-06
awesome pepun, congrats and enjoy it man!

---

### Post by AutoStatic on 2010-08-06
Argh, the music store got my order wrong so they shipped a Saffire Pro 40. We decided we're going to keep it anyway. And besides, after compiling both FFADO and JACK from svn the device works. And I had to disable the onboard Firewire controller which didn't work anyway. Pepun did you have to use FFADO and JACK from svn also? I couldn't get it to run with the standard Lucid packages.

---

### Post by pepun on 2010-08-08
Hey Autostatic,

I'm running FFADO from svn but JACK from the ubuntu repositories. And to be honest I didn't even try ubuntu's FFADO because on the FFADO-site I read that it only works with the svn-version. I had some problems compiling the FFADO-mixer first. For some reason the Scons config file did not check the dependencies correctly. But after some adjustments (following [http://ffado.org/?q=node/613](http://ffado.org/?q=node/613)) everything was fine.
I also had some firewire issues in the beginning which were caused by my old and now apparently broken fw-card. So I just had to get a new one and since then everything works.

Wow, and you have a Saffire Pro 40 now! Isn't that great?! I was thinking about getting that one, too. It was just too expensive for me :( ... .but since you got it accidently... will you have to pay the price for the pro 40 now... or just for the pro 24?!

Still damn happy about his working interface...
Pepun

---

### Post by AutoStatic on 2010-08-08
> **pepun said:**
> I'm running FFADO from svn but JACK from the ubuntu repositories.Ok, good to know, then I'll probaly try rolling back the JACK install from svn and retry with the default Lucid packages. I think JACK didn't want to run due to the fact that I have two Firewire controllers on this machine, one PCIe from  Belkin (with a Texas Instruments chipset) and one onboard VIA controller. When I disabled the VIA controller in the BIOS JACK started up happily.

> **pepun said:**
> Wow, and you have a Saffire Pro 40 now! Isn't that great?! I was thinking about getting that one, too. It was just too expensive for me :( ... .but since you got it accidently... will you have to pay the price for the pro 40 now... or just for the pro 24?!The price for the Pro 40. But it's for a machine at my work and the budget isn't really tight fortunately :)

---

### Post by AutoStatic on 2010-08-12
FYI, the Focusrite Saffire Pro 40 works flawlessly with Ubuntu 10.04. You do need to compile and install FFADO from SVN: [http://subversion.ffado.org/wiki/Dependencies/Ubuntu](http://subversion.ffado.org/wiki/Dependencies/Ubuntu)

Compiling JACK from SVN is not necessary, after compiling and installing FFADO from SVN the card should get recognized:
```
studio@audiopc:~$ ffado-test ListDevices
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.999.0-1880
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x00130e0401402335  0x0000130E  0x00000005   Focusrite - SAFFIRE_PRO_40
```

And when starting JACK the card should initialize:
```
studio@audiopc:~$ /usr/bin/jackd -P69 -t2000 -dfirewire -r48000 -p64 -n2
jackd 0.119.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    6115326
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
02433595443:  (ffado.cpp)[  92] ffado_streaming_init: libffado 2.999.0-1880 built Aug  6 2010 16:32:16
02446438747: Warning (dice_eap.cpp)[ 881] updateNameCache: What is this function about?
02446561088:  (dice_avdevice.cpp)[ 626] showDevice:  DICE Parameter Space info:
02446561110:  (dice_avdevice.cpp)[ 627] showDevice:   Global  : offset=0x0028 size=0360
02446561139:  (dice_avdevice.cpp)[ 628] showDevice:   TX      : offset=0x0190 size=0568
02446561160:  (dice_avdevice.cpp)[ 629] showDevice:                 nb=   2 size=0280
02446561177:  (dice_avdevice.cpp)[ 630] showDevice:   RX      : offset=0x03C8 size=1128
02446561197:  (dice_avdevice.cpp)[ 631] showDevice:                 nb=   2 size=0280
02446561213:  (dice_avdevice.cpp)[ 632] showDevice:   UNUSED1 : offset=0x0830 size=0016
02446561233:  (dice_avdevice.cpp)[ 633] showDevice:   UNUSED2 : offset=0x0000 size=0000
02446561249:  (dice_avdevice.cpp)[ 635] showDevice:  Global param space:
02446562755:  (dice_avdevice.cpp)[ 638] showDevice:   Owner            : 0x00000000FFFF0000
02446564564:  (dice_avdevice.cpp)[ 641] showDevice:   Notification     : 0x00000040
02446568580:  (dice_avdevice.cpp)[ 644] showDevice:   Nick name        : Pro40-002335
02446570500:  (dice_avdevice.cpp)[ 648] showDevice:   Clock Select     : 0x02 0x0C
02446572403:  (dice_avdevice.cpp)[ 652] showDevice:   Enable           : false
02446574340:  (dice_avdevice.cpp)[ 656] showDevice:   Clock Status     : locked 0x02
02446577612:  (dice_avdevice.cpp)[ 659] showDevice:   Extended Status  : 0x00000000
02446579540:  (dice_avdevice.cpp)[ 662] showDevice:   Samplerate       : 0x0000BB80 (48000)
02446581464:  (dice_avdevice.cpp)[ 665] showDevice:   Version          : 0x01000400
02446583383:  (dice_avdevice.cpp)[ 674] showDevice:   Version          : 0x01000400 (1.0.4.0)
02446585529:  (dice_avdevice.cpp)[ 677] showDevice:   Clock caps       : 0x1330001E
02446587752:  (dice_avdevice.cpp)[ 680] showDevice:   Clock sources    :
02446587800:  (dice_avdevice.cpp)[ 686] showDevice:     SPDIF1
02446587823:  (dice_avdevice.cpp)[ 686] showDevice:     AES34
02446587841:  (dice_avdevice.cpp)[ 686] showDevice:     AES56
02446587859:  (dice_avdevice.cpp)[ 686] showDevice:     TOS
02446587876:  (dice_avdevice.cpp)[ 686] showDevice:     SPDIF
02446587896:  (dice_avdevice.cpp)[ 686] showDevice:     ADAT
02446587913:  (dice_avdevice.cpp)[ 686] showDevice:     ADAT_AUX
02446587930:  (dice_avdevice.cpp)[ 686] showDevice:     Word Clock
02446587947:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
02446587967:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
02446587983:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
02446588002:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
02446588018:  (dice_avdevice.cpp)[ 686] showDevice:     Internal
02446588035:  (dice_avdevice.cpp)[ 689] showDevice:  TX param space:
02446588051:  (dice_avdevice.cpp)[ 690] showDevice:   Nb of xmit        : 2
02446588070:  (dice_avdevice.cpp)[ 692] showDevice:   Transmitter 0:
02446589682:  (dice_avdevice.cpp)[ 695] showDevice:    ISO channel       :  -1
02446591595:  (dice_avdevice.cpp)[ 697] showDevice:    ISO speed         :   2
02446593490:  (dice_avdevice.cpp)[ 700] showDevice:    Nb audio channels :  10
02446596532:  (dice_avdevice.cpp)[ 702] showDevice:    Nb midi channels  :   1
02446598464:  (dice_avdevice.cpp)[ 705] showDevice:    AC3 caps          : 0x00000000
02446600384:  (dice_avdevice.cpp)[ 707] showDevice:    AC3 enable        : 0x00000000
02446602610:  (dice_avdevice.cpp)[ 710] showDevice:    Channel names     :
02446602636:  (dice_avdevice.cpp)[ 715] showDevice:      IP 1
02446602653:  (dice_avdevice.cpp)[ 715] showDevice:      IP 2
02446602673:  (dice_avdevice.cpp)[ 715] showDevice:      IP 3
02446602689:  (dice_avdevice.cpp)[ 715] showDevice:      IP 4
02446602708:  (dice_avdevice.cpp)[ 715] showDevice:      IP 5
02446602724:  (dice_avdevice.cpp)[ 715] showDevice:      IP 6
02446602743:  (dice_avdevice.cpp)[ 715] showDevice:      IP 7
02446602760:  (dice_avdevice.cpp)[ 715] showDevice:      IP 8
02446602779:  (dice_avdevice.cpp)[ 715] showDevice:      SPDIF L
02446602795:  (dice_avdevice.cpp)[ 715] showDevice:      SPDIF R
02446602817:  (dice_avdevice.cpp)[ 692] showDevice:   Transmitter 1:
02446604529:  (dice_avdevice.cpp)[ 695] showDevice:    ISO channel       :  -1
02446606675:  (dice_avdevice.cpp)[ 697] showDevice:    ISO speed         :   2
02446608593:  (dice_avdevice.cpp)[ 700] showDevice:    Nb audio channels :  10
02446610529:  (dice_avdevice.cpp)[ 702] showDevice:    Nb midi channels  :   0
02446612419:  (dice_avdevice.cpp)[ 705] showDevice:    AC3 caps          : 0x00000000
02446614325:  (dice_avdevice.cpp)[ 707] showDevice:    AC3 enable        : 0x00000000
02446617670:  (dice_avdevice.cpp)[ 710] showDevice:    Channel names     :
02446617695:  (dice_avdevice.cpp)[ 715] showDevice:      ADAT 1
02446617712:  (dice_avdevice.cpp)[ 715] showDevice:      ADAT 2
02446617732:  (dice_avdevice.cpp)[ 715] showDevice:      ADAT 3
02446617748:  (dice_avdevice.cpp)[ 715] showDevice:      ADAT 4
02446617766:  (dice_avdevice.cpp)[ 715] showDevice:      ADAT 5
02446617782:  (dice_avdevice.cpp)[ 715] showDevice:      ADAT 6
02446617801:  (dice_avdevice.cpp)[ 715] showDevice:      ADAT 7
02446617817:  (dice_avdevice.cpp)[ 715] showDevice:      ADAT 8
02446617836:  (dice_avdevice.cpp)[ 715] showDevice:      Loop 1
02446617852:  (dice_avdevice.cpp)[ 715] showDevice:      Loop 2
02446617873:  (dice_avdevice.cpp)[ 719] showDevice:  RX param space:
02446617888:  (dice_avdevice.cpp)[ 720] showDevice:   Nb of recv        : 2
02446617906:  (dice_avdevice.cpp)[ 722] showDevice:   Receiver 0:
02446619603:  (dice_avdevice.cpp)[ 725] showDevice:    ISO channel       :  -1
02446621581:  (dice_avdevice.cpp)[ 727] showDevice:    Sequence start    :   0
02446623495:  (dice_avdevice.cpp)[ 730] showDevice:    Nb audio channels :  12
02446625660:  (dice_avdevice.cpp)[ 732] showDevice:    Nb midi channels  :   1
02446627574:  (dice_avdevice.cpp)[ 735] showDevice:    AC3 caps          : 0x00000000
02446629492:  (dice_avdevice.cpp)[ 737] showDevice:    AC3 enable        : 0x00000000
02446631719:  (dice_avdevice.cpp)[ 740] showDevice:    Channel names     :
02446631744:  (dice_avdevice.cpp)[ 745] showDevice:      Mon 1
02446631761:  (dice_avdevice.cpp)[ 745] showDevice:      Mon 2
02446631780:  (dice_avdevice.cpp)[ 745] showDevice:      Line 3
02446631796:  (dice_avdevice.cpp)[ 745] showDevice:      Line 4
02446631815:  (dice_avdevice.cpp)[ 745] showDevice:      Line 5
02446631831:  (dice_avdevice.cpp)[ 745] showDevice:      Line 6
02446631850:  (dice_avdevice.cpp)[ 745] showDevice:      Line 7
02446631867:  (dice_avdevice.cpp)[ 745] showDevice:      Line 8
02446631886:  (dice_avdevice.cpp)[ 745] showDevice:      Line 9
02446631902:  (dice_avdevice.cpp)[ 745] showDevice:      Line 10
02446631921:  (dice_avdevice.cpp)[ 745] showDevice:      SPDIF L
02446631936:  (dice_avdevice.cpp)[ 745] showDevice:      SPDIF R
02446631958:  (dice_avdevice.cpp)[ 722] showDevice:   Receiver 1:
02446633624:  (dice_avdevice.cpp)[ 725] showDevice:    ISO channel       :  -1
02446636647:  (dice_avdevice.cpp)[ 727] showDevice:    Sequence start    :   0
02446638578:  (dice_avdevice.cpp)[ 730] showDevice:    Nb audio channels :   8
02446640484:  (dice_avdevice.cpp)[ 732] showDevice:    Nb midi channels  :   0
02446642415:  (dice_avdevice.cpp)[ 735] showDevice:    AC3 caps          : 0x00000000
02446644332:  (dice_avdevice.cpp)[ 737] showDevice:    AC3 enable        : 0x00000000
02446647074:  (dice_avdevice.cpp)[ 740] showDevice:    Channel names     :
02446647104:  (dice_avdevice.cpp)[ 745] showDevice:      ADAT 1
02446647121:  (dice_avdevice.cpp)[ 745] showDevice:      ADAT 2
02446647139:  (dice_avdevice.cpp)[ 745] showDevice:      ADAT 3
02446647159:  (dice_avdevice.cpp)[ 745] showDevice:      ADAT 4
02446647168:  (dice_avdevice.cpp)[ 745] showDevice:      ADAT 5
02446647191:  (dice_avdevice.cpp)[ 745] showDevice:      ADAT 6
02446647207:  (dice_avdevice.cpp)[ 745] showDevice:      ADAT 7
02446647223:  (dice_avdevice.cpp)[ 745] showDevice:      ADAT 8
```

---

### Post by plastikat on 2011-10-25
Hi all. Does anybody make the Saffire 6 USB, run with Ubuntu 11.04?

I have no idea how to run it, completely new to linux. Whant to check first, if someone run it, then instal ubuntu. 

Don't want to use such a great audio interface, with windows anymore (((

---

### Post by plastikat on 2011-10-26
Can anybody help please? :confused:
is there any possibility to run windows driver in some way? Cuz, the technical support told me, that they not supporting linux. that's ******* sucks.

And I don't understand why Saffire's with firewire on it, runs with no problem, but simple thing as USB, not?? whyy?:confused:

---

### Post by maghoxfr on 2011-10-26
> **plastikat said:**
> Can anybody help please? :confused:
is there any possibility to run windows driver in some way? Cuz, the technical support told me, that they not supporting linux. that's ******* sucks.

And I don't understand why Saffire's with firewire on it, runs with no problem, but simple thing as USB, not?? whyy?:confused:

Check ffado.

And the Interface still does not work under linux.

---

### Post by plastikat on 2011-10-27
> **maghoxfr said:**
> Check ffado.

And the Interface still does not work under linux.

But it's a firewire project? Didn't found there nothing about fs66.

No one can run it, what to do? Writing driver by our selfs? impossible.  No it is possible, but not with my knowlege of lnux.

Integrate windows driver? how? Found only about wireless cards, that the drivers are runing with no problem. But it's not a sound:(

What if, we will use a usb to firewire converter :D? and then ffado? No it kinda stupid ******** :D

---

### Post by sgx on 2011-10-27
(copied from the rig-Kontrol topic :) )

Hi, I would start by shutting off everything you don't need for audio,
in the bios. Take notes. Networking, acpi, power management, bluetooth,
webcam yada yada. Unplug every usb device, and don't use a usb hub.

Make a working jackd/qjackctl setup with your soundcard/chip

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

Use the 4th link and last link at the wiki, for screenshots
to set up jackd and qjackctl, and install wine and wineasio,
and run the command

regsvr32 wineasio.dll.

Once this works, plug in the FS in each usb port, between boots, checking lsusb each time, and check in qjackctl setup page, click the
> widgets by

Input device >
Output device >

for the detected sound devices.

I would also do a fresh install of ubuntu studio 10.04 as the
stable basis for your tests and future daw. Uninstall pulseaudio
and libpulse using synaptic, if they exist.

If nothing works, try another distro

[http://www.bandshed.net/AVLinux.html](http://www.bandshed.net/AVLinux.html) is a good one, and has
the liquorix kernel available, as well as a really good
default kernel. or Puppy Studio

[http://www.murga-linux.com/puppy/viewtopic.php?t=72402](http://www.murga-linux.com/puppy/viewtopic.php?t=72402)

[http://tangostudio.tuxfamily.org/en/tangostudio](http://tangostudio.tuxfamily.org/en/tangostudio)

or sell/trade the device.

---

### Post by maghoxfr on 2011-10-30
I already gave up on this interface. I use it on windows though, for linux I have another one. There are no drives AFAIK and from what Focusrite support have told me, they will not be developing any for linux. So, if a developer(s) from the community doesn't do so, this interface will not work under linux.

But as I said, i already gave up on this and I stopped looking for info/contacting people about it months ago.

In case anyone found some info about it, please post it here.

Thank you

---

### Post by plastikat on 2011-10-31
Yes, I'm waiting too, maybe one day... it will run with ubuntu in one click.

anyway I'm instaling ubuntu, getting too much troubles in windows every day (( and the Focusrite 6 usb will run, no idea how, no idea when, no idea how to start,just no idea.  

but IT MUST run in some way!

---

### Post by gandalfuy on 2012-07-23
2012 ...

Still no easy install for Focusrite Saffire 6 USB?

What usb card for ubuntu would you recomend. I need to record studio but for less than 300 USD. (I have an extra console to pre mix some other instruments).


[I]thanks!
aLe.-

[/I]

---

### Post by maghoxfr on 2012-07-24
> **gandalfuy said:**
> 2012 ...

Still no easy install for Focusrite Saffire 6 USB?

What usb card for ubuntu would you recomend. I need to record studio but for less than 300 USD. (I have an extra console to pre mix some other instruments).


[I]thanks!
aLe.-

[/I]

I don't really know, I've been kind of retired from audio for like 6 months. But whatever you do AVOID the Alesis multimix 4 USB. It's junk.

---

### Post by gandalfuy on 2012-07-24
> **maghoxfr said:**
> I don't really know, I've been kind of retired from audio for like 6 months. But whatever you do AVOID the Alesis multimix 4 USB. It's junk.

Thanks!

Any other sugestion? I want to get an external USB card for ubuntu.

---

### Post by sgx on 2012-07-25
[http://www.native-instruments.com/#/en/products/producer/audio-kontrol-1/](http://www.native-instruments.com/#/en/products/producer/audio-kontrol-1/)

This is high quality, and should have good resale value,
should the need arise. The product line is for Mac and windows,
so most of what they sell works in linux.

In addition, this line in google

"usb soundcard" linux works

Lots of reading. Substitute working, and fails, instead of works,
for more  takes.

also, google your computer model name with alsa 

Cheers

---

