---
title: "Can Ubuntu simulate a Behringer DEQ2496?"
date: 2011-04-08
forum: Ubuntu Studio
---

### Post by mikee55 on 2011-04-08
Hello, I have a Behringer DEQ2496, and I use Ubuntu10.10 as my desktop. I'd like to know is there a Package I can use to replicate the PEQ part of the Behringer?

[http://www.behringer.com/EN/Products/DEQ2496.aspx](http://www.behringer.com/EN/Products/DEQ2496.aspx)

I would to replace my Behringer's main job, which EQ's my Sub woofer, an Infinite Baffle, and place it in my main output to control Room response.

I'm thinking of using a motherboard, an SSD hard drive, a 24/96 sound card plus ram etc. No keyboard, mouse or monitor, but use my main PC with Remote Desktop. Via Lan or wireless.

So I'm basically looking at parametric equaliser that I can stack a bunch of filters. I need subsonic hi pass, a low pass and some band pass with variable Q.
Not too much then :lolflag:

Cheers Mike

---

### Post by AutoStatic on 2011-04-08
Three candidates when it comes to parametric equalizers:
[list][*]Calf EQ (5, 8 or 12 band): [http://calf.sourceforge.net/](http://calf.sourceforge.net/)
[*]EQ10Q: [http://eq10q.sourceforge.net/](http://eq10q.sourceforge.net/)
[*]linuxDSP GR-EQ2 (commercial plug-in): [http://www.linuxdsp.co.uk/download/lv2/download_mkii_graph_eq/index.html](http://www.linuxdsp.co.uk/download/lv2/download_mkii_graph_eq/index.html)[/list]

Best,

Jeremy

---

### Post by mikee55 on 2011-04-08
Thanks Jeremy,

          Wow,where to I begin. Looks looks advanced. I'm by no means a musician. More likely, an Audiophile. I have Wave-lab 5.1b running in wine. Which I use, for Vinyl etc. The EQ10Q looks ideal, but I shy away from compiling. Ardour looks scarier than Wave-lab, would I need this for linuxDSP? and the Calf project looks to be more instrument orientated.


If my skill, is just about able to record and clean vinyl and cassette using Steinberg VST plugins, what would you suggest?

Cheers Mike

---

### Post by AutoStatic on 2011-04-08
> **mikee55 said:**
> The EQ10Q looks ideal, but I shy away from compiling.There's no need to. I have packages available for Lucid Lynx but I'll try uploading those to the [KXStudio PPA]("https://launchpad.net/~kxstudio-team/+archive/ppa") this weekend so any time soon Maverick packages should be available too.

> **mikee55 said:**
> Ardour looks scarier than Wave-lab, would I need this for linuxDSP?No, those plug-ins work flawlessly in [Qtractor]("http://qtractor.sourceforge.net/qtractor-index.html") too, or any other LV2 host. I think it even comes with a separate JACK client so you don't need a host at all.

> **mikee55 said:**
> and the Calf project looks to be more instrument orientated.Could be, I do use the Calf EQ's more for separate instruments myself but they're also suitable for finalizing projects.


> **mikee55 said:**
> If my skill, is just about able to record and clean vinyl and cassette using Steinberg VST plugins, what would you suggest?You probably don't want to hear this but... Continue listening to vinyl! I still buy new albums on vinyl regularly, nothing beats a 45rpm double album!
But if you really want to digitize those albums and cassettes then you'll need a very decent sound card with good converters and a good pair of monitors and ears. And maybe some good plugins. I'd go for linuxDSP unless you achieve satisfying results with the opensource counterparts.

Best,

Jeremy

---

### Post by mikee55 on 2011-04-08
Thanks Jeremy, going camping for the weekend, so can't play till next week. I'll see then what I can do. Will you be around? Then if you don't mind, can I hassle you for help?  :lolflag:

Regards, Mike

---

### Post by mikee55 on 2011-04-12
Hi, err don't know where to start??? I've got a lot to learn.

Mike

---

### Post by mikee55 on 2011-04-12
Jack in the Opera house, or rather I installed Jack and Jack rack. Selected a simple karaoke effect. I attached a small dvd player to the line in. 

I hear nothing and my PC sound only works on my built in sound card. I now have my ordinary music playing through on board, my X Fi has disappeared?

Whats happening

---

### Post by Sylos on 2011-04-12
Hello.

Did you try disabling the onboard audio in your motherboad settings?

Cheers

---

### Post by mikee55 on 2011-04-12
No, I have been using on board for desktop speakers and X Fi has been fed to my hi fi system! This way I can either enjoy music or when someone watches tv, I switch to desktop. I usually select which card I'm using.

Thanks :p

---

### Post by Sylos on 2011-04-12
Ah! I see.

Whats the output of lspci?

Is the card still detected?

---

### Post by mikee55 on 2011-04-12
On board sound disabled. Still no sound.

---

### Post by Sylos on 2011-04-12
Please post the output of 

lspci

from the terminal.

Also, is this affecting all of your PC sound or only when you try using jack and the effects rack? Could you try using jack without the effects and see if it is working using other apps?

Thanks

---

### Post by mikee55 on 2011-04-12
tux@tux-desktop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: ASUSTeK Computer Inc. RS880 PCI to PCI bridge (int gfx)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc 760G [Radeon 3000]
02:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
03:06.0 Multimedia audio controller: Creative Labs SB X-Fi
tux@tux-desktop:~$ 


Hi, I now have no sound at all :(

Thank you

---

### Post by mikee55 on 2011-04-12
If I stop Jack, I get audio???

Thank you

---

### Post by Sylos on 2011-04-12
Right...sorry for the delay - have been at work.

Ok. Your card is clearly still being recognised and you appear to be getting sound as long as its not through jack - so jack is the issue. 

Mow Im no jack guru - Im pretty green with this stuff too - but heres my (limited) understanding:
Your screenshot shows you are getting Xruns when jack is trying to run - this is usually a sign of instability brought on by trying to run at too high a quality for your system - it would be interesting to increase the latency in your settings and see if jack then works  - your current setting is around 5 so double it to 10 and see if that makes a difference. Also, you are running in duplex mode which I think puts more stress on the system so you could try to switch that and see if you get a runner.

The key thing is to try setting it up with lower quality settings so that it works and then try and incramentally increase them until you hit a better level that is sustainable (ie no xruns).

Hope that helps. If not post back.

---

### Post by mikee55 on 2011-04-12
Okay, hi, still not getting anything? If I play mp3's on Movie Player as a source of music, it won't play. The Transport does nothing. I whacked Latency up to 29ms.
Am I not to set the Patchbay or the Connect button to do something??
Thank you:p
Mike

---

### Post by mikee55 on 2011-04-12
Help. Pleeease :):lolflag:

---

### Post by Pablo_F on 2011-04-12
Hi, 

When jack is running only jack-aware apps will produce sound. Default multimedia players are not "jackified" by default but it is rather easy to achieve this. However, it depends on the player. 

I recommend you try aqualung (it is in the software center), at least as a proof of concept. Aqualung will play through jack automatically if jack is running.

For other players, google for "multimedia players through jack".

---

### Post by mikee55 on 2011-04-12
Hooray something works. I have Aqualung playing an mp3 and Meterbridge VU meters are dancing away, I have audio. So how do I replace Aqualung with Line IN?

Thankyou 

Mike

---

### Post by mikee55 on 2011-04-12
I closed it all to redo it to see if I could still play and now everytime I start Aqualung, I get  JackAudioDriver::ProcessAsync Process error. And can't get it to work?????


Thank you 
Mike :confused::confused::confused::confused:

---

### Post by mikee55 on 2011-04-12
Disregard that, its working. So now I need to change Aqualung for Line in on my Sound card!

Thank you 
Mike):P

---

### Post by Pablo_F on 2011-04-13
Hi, 

We can help better if you give the terminal output of:

arecord -l && aplay -l

and you explain the signal routing that you have or want to have, hardware and software.

Cheers, Pablo

---

### Post by mikee55 on 2011-04-13
tux@tux-desktop:~$ arecord -l && aplay -l
**** List of CAPTURE Hardware Devices ****
card 0: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
**** List of PLAYBACK Hardware Devices ****
card 0: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 7/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 1: ctxfi [Surround]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 2: ctxfi [Center/LFE]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 3: ctxfi [Side]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 4: ctxfi [IEC958 Non-audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
tux@tux-desktop:~$
 
Hi, I would like to connect my line in, straight to jamin, and on to line out. All I can achieve is Aqualung playing mp3,  straight to jamin, and on to line out.

Mike:p

---

### Post by Sylos on 2011-04-13
For connecting your line in to jamin you will need to do the following:

1. Launch qjackctrl and start jack.
2. Launch Jamin.
3. Open the patchbay of qjackctrl and then find the line in input - then connect this to the input of jamin.

If all goes well the sound should then run into jamin. I believe by default the outputs of jamin will be linked to the system out (your output device) so you should hear sound but can reroute the output to something else from the patchbay if you want.

---

### Post by mikee55 on 2011-04-13
Hy Sylos, don't see line in???????????

If it is capture, why is it on Output side?

Thank you 
Mike:)

---

### Post by Sylos on 2011-04-13
Go to the "sytem" part on the left hand side and expand that. This should give all the inputs (normally labelled HW:0 or something similar). 

Im not at my PC so I cant give you the exact wording/process (at work on windoze pc) but is should be there sonmewhere under system on the left hand side.

---

### Post by Sylos on 2011-04-13
Scratch the above - it should be the two capture devices as you say (just looked at your screenchot).

I think they are down as outputs as they are the output of the device (your soundcard). Someone will correct me if Im wrong.

PS: that screenshot shows you are getting a horrendous number of Xruns (shown in red on the jack control panel). That doesnt look like a good sign. We may need PabloF or someone with more experience to advise if that continues.

---

### Post by AutoStatic on 2011-04-13
> **mikee55 said:**
> If it is capture, why is it on Output side?Because the other end of your physical line-in input is a (virtual) output sink for JACK and you can capture sound from it within JACK.

Best,

Jeremy

---

### Post by AutoStatic on 2011-04-13
> **Sylos said:**
> Scratch the above - it should be the two capture devices as you say (just looked at your screenchot).Yes, system:capture_1, system:capture_2 and so on. Not sure which one corresponds with the line-in of a X-Fi though.

> **Sylos said:**
> PS: that screenshot shows you are getting a horrendous number of Xruns (shown in red on the jack control panel). That doesnt look like a good sign. We may need PabloF or someone with more experience to advise if that continues.The system is probably not optimized for usage with JACK. The JACK settings themselves seem to be ok. more info on how to optimize your system: [http://wiki.linuxmusicians.com/doku.php?id=system_configuration](http://wiki.linuxmusicians.com/doku.php?id=system_configuration)

Best,

Jeremy

---

### Post by mikee55 on 2011-04-13
Still silence at the input??? 



This machine is a Dual core AMD 4 gb ram Ubuntu 10.10. Music is playing beutifully, unless I drag a window or Jamin is maximized, because of moving display. but at 32bit. Would it help to use 64 bit or Ubuntu Studio, Kubuntu???

---

### Post by AutoStatic on 2011-04-13
Try disabling Desktop Effects and CPU frequency scaling. Also try using the QjackCtl Connections window for making your connections, not the Patchbay window.

Best,

Jeremy

---

### Post by Pablo_F on 2011-04-13
In the last screenshot we can see tons of xruns and a very high CPU usage at a sample rate of 96 kHz. 

Some ideas:

Try 48000 Hz.  
Increase the period size.
Jamin is very CPU hungry.


Another parametric EQ, LADSPA, is in the FIL-plugins collection by Fons Adriaensen. 
[http://kokkinizita.linuxaudio.org/linuxaudio/ladspa/index.html](http://kokkinizita.linuxaudio.org/linuxaudio/ladspa/index.html)

It has a LV2 version LV2fil, by Nedko Arnaudov.
[http://nedko.arnaudov.name/soft/lv2fil/trac/](http://nedko.arnaudov.name/soft/lv2fil/trac/)


You normally make connections between jack audio ports in the connect window of qjackctl. By the time being, you don't need the patchbay. When you have decided on the programs to use and how to connect them, it can be useful. It is used to automatically remember conections. It is very well explained here:
[http://www.rncbc.org/drupal/node/76](http://www.rncbc.org/drupal/node/76)

---

### Post by Pablo_F on 2011-04-13
One more thing, in addition to make the right jack audio connections, you have to take a look at the alsa mixer, which controls the XFi internal mixer. 

There are several graphical alsa mixers, like gamix, gnome-alsa-mixer, qamix... Or you can always use plain *alsamixer* in a terminal. Any of them is good, afaik. 

This kind of cards have rather involved mixers, but after some trial and error you will realize.

Cheers! Pablo

---

### Post by mikee55 on 2011-04-13
Hello, I have a usb X FI Go as well as an X FI, and IT WORKS! Thats the 3rd piece of hardware purchased from dabs.com thats broke!!!

Thank you all for your help. I'm a happy chappy. Now need to have words with dabs.com.

Peace

Mike):P):P:D):P):P

---

### Post by AutoStatic on 2011-04-13
Cool! Would you still be interested in a Maverick package of EQ10Q? The FIL EQ Pablo_F mentioned is a good option too if you're looking for a high quality EQ.

Best,

Jeremy

---

### Post by zettberlin on 2011-04-13
Testing EQ10Q in Ardour2 I get a massive stream of xruns as soon as the plugin is active but does not get any data on the track it is applied. E.g. if there is no region in the track...

---

### Post by AutoStatic on 2011-04-13
Which version of EQ10Q? No problems here with Qtractor.

---

### Post by zettberlin on 2011-04-13
> **AutoStatic said:**
> Which version of EQ10Q? No problems here with Qtractor.

Built from source yesterday...

---

### Post by mikee55 on 2011-04-13
Hi all, Still messing around. Seems I'm getting a fair bit of distortion. Will definately try a new PEQ.

Any idea why I get distortion?

Thank you 
Mike

---

### Post by zettberlin on 2011-04-13
> **mikee55 said:**
> Hi all, Still messing around. Seems I'm getting a fair bit of distortion. Will definately try a new PEQ.

Any idea why I get distortion?

Thank you 
Mike
jamin fails to deliver in time, seems like this is messing up the stream.

What applications are involved here? Any more plug-ins running?

You may want to have a look, what programs use the most CPU-power. Open a terminal and type:

top

what can you see?

---

### Post by mikee55 on 2011-04-13
Ladspa Plugins, from synaptic, mmm, I've installed them but can't find them in Sound and Video. Where they hide to?

Thank you 
Mike

---

### Post by Pablo_F on 2011-04-13
plugins are not apps by themselves; you load them in another app, i.e., the host. A simple ladspa host is jack-rack (but lots of linux audio programs can load ladspa plugins aswell). You can check if new plugins are available in jack-rack.

Not all ladspa plugins are packaged and available in the official repos though.

---

### Post by mikee55 on 2011-04-13
Hi Pablo_F, thanks for the info, any idea why I get distortion on Line in? 

Thank you
Mike

Also if Jack is at 48000, and I'm playing a 44100 sample rate on Aqualung, why doesn't switching 48000 to 44100 in Jack setup help?

---

### Post by AutoStatic on 2011-04-14
> **mikee55 said:**
> Hi Pablo_F, thanks for the info, any idea why I get distortion on Line in?Zettberlin already answered this. JAMin is a resource hog, I'd recommend using another solution, for example a plug-in host with the necessary plug-ins.

> **mikee55 said:**
> Also if Jack is at 48000, and I'm playing a 44100 sample rate on Aqualung, why doesn't switching 48000 to 44100 in Jack setup help?You can't change the sample rate of JACK when JACK is running. Also JACK doesn't do any sample rate conversion by itself.

Best,

Jeremy

---

### Post by Sylos on 2011-04-14
Regarding the distorion - this will seem like a dumb question and its not meant to be patronising but are you sure you are feeding in a line level input? If you are running a boosted signal (like from a headphone port) that could cause distortion (I think) if the level is too high.

It could also be a sign of the system not coping (although your specs seem more than adeqauet to do what you want). Are you using a real time kernel or the vanilla? Have you followed the configuration link that AutoStatic linked in a previous post? You may need to give yourself real time priority to ensure that you can get the best from the system.

---

### Post by Sylos on 2011-04-14
AutoStatic - You know WAAAAAAAAY more about any of this than me but I cant help feeling he ought to be able to use jamin - I use it on an old AMD Athlon single core 2ghz with 1g RAM - The op has a dual core (albeit running 32bit OS) with 4g RAM. Is jamin really that bad that it could hog it to death on a system with that spec?

Cheers

---

### Post by AutoStatic on 2011-04-14
> **Sylos said:**
> AutoStatic - You know WAAAAAAAAY more about any of this than me but I cant help feeling he ought to be able to use jamin - I use it on an old AMD Athlon single core 2ghz with 1g RAM - The op has a dual core (albeit running 32bit OS) with 4g RAM. Is jamin really that bad that it could hog it to death on a system with that spec?

CheersHello Sylos, of course he should be able to use JAMin but the OP said he is an audiophile so in that case I would look for another solution than JAMin. There are simply better alternatives. But if the OP is happy with JAMin, no problem. And even if JAMin is a resource hog it shouldn't bring down a dual core AMD machine, it's just that it uses a lot of CPU and it doesn't like lower latencies.

Best,

Jeremy

---

### Post by Pablo_F on 2011-04-14
Mike, don't forget to check capture levels in alsamixer (or gamix, etc).

---

### Post by mikee55 on 2011-04-14
Hi all, the obvious thing would be to send signal direct to output, with no JAMin, and of course adjust volume settings. I think my soundcard is pushing itself doing Duplex? Also, less stressful to the system, Aqualung has been providing an on line radio stream for 5 hours plus through Jack, flawlessly :)

I've looked at the tweaking stuff and need more time to absorb it:confused:

Being a USB dongle thingy, I don't expect much
[http://support.creative.com/Products/ProductDetails.aspx?catID=1&CatName=Sound+Blaster&subCatID=208&subCatName=X-Fi&prodID=17872&prodName=Sound+Blaster+X-Fi+Go!&bTopTwenty=1&VARSET=prodfaq:PRODFAQ_17872,VARSET=CategoryID:1](http://support.creative.com/Products/ProductDetails.aspx?catID=1&CatName=Sound+Blaster&subCatID=208&subCatName=X-Fi&prodID=17872&prodName=Sound+Blaster+X-Fi+Go!&bTopTwenty=1&VARSET=prodfaq:PRODFAQ_17872,VARSET=CategoryID:1)

Thank you 
Mike:D

---

### Post by Sylos on 2011-04-14
> **AutoStatic said:**
> Hello Sylos, of course he should be able to use JAMin but the OP said he is an audiophile so in that case I would look for another solution than JAMin. There are simply better alternatives. But if the OP is happy with JAMin, no problem. And even if JAMin is a resource hog it shouldn't bring down a dual core AMD machine, it's just that it uses a lot of CPU and it doesn't like lower latencies.

Best,

Jeremy

Ah, I see. My misunderstanding.

cheers

---

### Post by mikee55 on 2011-04-15
Uhh! Hello!

 Erm, I installed Ubuntu Studio, set my settings the same as Ubuntu 10.10, but it no worky :(

What did I do?

Thank you 
Mike

---

### Post by mikee55 on 2011-04-15
Pic

---

### Post by mikee55 on 2011-04-15
Disregard please, I'm up and running. 
Thank you

Mike ):P):P

---

### Post by Pablo_F on 2011-04-15
Try 3 or 2 periods. No more. And increase the frames/period vale. 1024 is sane.

And make sure that hw:1 is the XFi. What is the terminal output of:

cat /proc/asound/cards

And make sure you have rtprio and memlock privileges. What is the terminal output of:

ulimit -r -l

---

### Post by mikee55 on 2011-04-15
Hi Pablo_F,

tux@ubuntu-tux-studio:~$ cat /proc/asound/cards
 1 [Go             ]: USB-Audio - SB X-Fi Go!
                      Creative Technology SB X-Fi Go! at usb-0000:00:13.0-1, full speed
tux@ubuntu-tux-studio:~$ ulimit -r -l
real-time priority              (-r) 95
max locked memory       (kbytes, -l) unlimited
tux@ubuntu-tux-studio:~$ 


It is running.  :)

Thank you
 Mike

---

