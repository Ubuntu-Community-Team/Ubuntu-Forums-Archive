---
title: "&quot;Help, I need somebody,&quot; ..."
date: 2010-06-18
forum: Ubuntu Studio
---

### Post by mango42 on 2010-06-18
... ... ...
> Help, I need somebody,
Help, not just anybody,
Help, you know I need someone, help.

When I was younger, so much younger than today,
I never needed anybody's help in any way.
But now these days are gone, I'm not so self assured,
Now I find I've changed my mind and opened up the doors.

Help me if you can, I'm feeling down
And I do appreciate you being round.
Help me, get my feet back on the ground,
Won't you please, please help me?

(It's a very old, very 'apt' Beatles song, for those youngsters who might think I'm wasting space here ;-) )

After weeks of fruitless attempts, I have backed off from Lucid Studio and gone back to Karmic on this wretched Alienware amd64, nVidia SLI equipped machine. But I still have horrible, cyclic audio glitches under JACK and loads of 'backend' xruns. I have tried so many combinations now, I don't know whether I am coming or going - hence the plea.

I have followed many suggestions posted here by so many very helpful people but still can't achieve the equivalent to what I have running solidly and stable on my partner's T43 Thinkpad (Karmic Studio, i386).

'Regular' audio works fine, everything else works fine (though I keep this machine off the net as I thought that Wifi IRQ's might have been the problem) - **Qtractor** MIDI works fine but not audio; ditto **Hydrogen** etc but *not* **Audacity**, which has *no problem* with any audio format I throw at it - it is totally glitch-free. However, I haven't yet attempted to get Firewire working for my dusty brick, a Saffire Pro 40.

So, I am down to two possible causes: Video drivers or Pulseaudio conflicts, I guess?

The Karmic *Studio* I have installed tells me I don't need proprietary video drivers, whereas a vanilla Karmic on another partition tells me I *do* need nVidia drivers, but the last time I tried to install them I ended up with a blank screen and no way back - just run nVidia-settings it said - yeah, right! That approach ended up in low-res mode, with dialogs way bigger than screen, so just guessing which buttons to click via invisible tabs!

Before I descend into that particular hell again, can anyone identify what the problem really is, please? I am ready and waiting to provide **lspci, lsmod**, QJackCtl setup, screenshots, a whole *host* of nvidia related files in Synaptic, whatever it takes to make this blasted machine behave*.

Help?

-------------
* Whether this is related or not, I don't know, but I recently had the screen replaced on this Alien and when it came back, Windows no longer works - the screen blinks on and off at random intervals - however, this does *not* occur under any form of Linux - bizarre or contributory? I am beyond knowing ;-)

---

### Post by cchhrriiss121212 on 2010-06-18
Looks like you've had a tough time with this. When you had Karmic running before did everything run OK?

Regarding jack: if you are going to be using this with your saffire device, then I would try and set that up straight away, as opposed to getting jack working with onboard audio and then firewire. Pulse shouldn't be causing any trouble as it is suspended when running jack.

Regarding video: I would recommend you avoid using jockey (System>Hardware drivers) as it fails more often than not for me, instead get a driver from [this page]("http://ubuntuforums.org/showthread.php?t=990978") and follow the instructions on there.

---

### Post by AutoStatic on 2010-06-18
mango42, what did you do so far to get JACK running? Did you disable CPU frequency scaling or set it to Performance at least? What are your current JACK settings? What kind of soundcard is it about?

---

### Post by mango42 on 2010-06-18
Thanks for pitching in so rapidly, guys - much appreciated.

@ ccchris... "When you had Karmic running before did everything run OK?" - 

Only *vanilla* Karmic runs okay on this Alien box, so far, though there was a time back in 9.04 when I had a very demanding flight simulator (IL2) running far smoother under WINE than under windoze - just before my 'old' screen started throwing up dead vertical lines.

That's good advice going straight to Firewire but I'm closely monitoring the ffado page for when, what and how for the 'de-computerate' and figured I better get the base system working right first... 

As for video, I am not being asked whether I want to use proprietary drivers - says 'everything's cool as is' :confused:

@ AutoStatic: It's the built-in nVidia soundcard - CK804. I also note from issuing **lspci** that the two graphics cards are recognised correctly as GeForce Go G71 (7900GS) at PCI 06 & 07.

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
``` returns **conservative ondemand userspace powersave performance** but I'm not sufficiently confident about [HOWTO: CPU Frequency Scaling w/ Kernel Module]("http://ubuntuforums.org/showthread.php?t=248867") to change anything...

As for JACK: ALSA driver, Realtime ON, Softmode ON(ignore backend xruns?), Priority-default, Frames 512, 48k, 3 periods; Wordlength to Channels, greyed out (16,21333,default) PortMax 256, Timeout 500. Interface (and everything below,) set to default. Dither - None, Audio - Duplex. Latency 32ms. Oh & MIDI driver - Seq

Present JACK audio on this box reminds me of that very old Benny Hill 'Click Song' where he faithfully sings off a vinyl record including scratches. Have we progressed much? ;-)

Thanks once again for putting up with an old f*rt, now lacking sufficient synapses for the intricacies of Linux...

----------------

Looking in with cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor returns '**ondemand**' - now using the CPUfreq scaling applet, set to **performance** makes no difference to the problem.

---

### Post by sgx on 2010-06-18
:popcorn: Go get a thinkpad. :guitar: :lolflag:

(I hate those type of replies from the peanut gallery)

But one thing is an axiom, if your hardware is not supported,
no amount of software and knowledge will help. On my setup, everything I can turn off at the bios, and still have an 'Enter Key'working, is off.

The old pci revision 2 maudio 24/96 chugs along nicely. I would google  the firewire chipset on your computer with the firewire device you have, and see if red flags appear. I would do a clean install without the device plugged in, use the synaptic 'remove completely' option to get rid of competing audio apps and bloatware (unless doing so removes the system skeleton) install ffado, and see what happens.

For now, consider the computer to be like a Yamaha Motif, you don't
want your synthesizer bogged down with extras for printing and playing movies and rendering flying logos. You need lines of text, a gui, and CD quality sound. 

[http://www.mellosonic.com/rocxshop.htm](http://www.mellosonic.com/rocxshop.htm)

This 400 meg bloat-free Test2 ISO on this page burns to an RT enabled audio distro live CD, based on pclinuxos,
and is quite stable, productive, and a good plan B.
It can be installed with a simple command that opens a great gui for such things. Also it installs nice on a 2 or 4 gig usb stick.

Cheers

---

### Post by AutoStatic on 2010-06-19
Hello mango42, if you're using Gnome then right-click on your panel, select 'Add to Panel'. From the list that opens select 'CPU Frequency Scaling Monitor' which will place a new applet on your gnome-panel. If you now click on this applet you can select the scaling setting, set it it 'Performance'. For each CPU core your processor has you will have to add a separate applet.
If you got something like, I don't want to set the scaling everytime I want to make music you could disable CPU Frequency Scaling altogether by disabling the 'Ondemand' service. I use the **sysv-rc-conf** tool for this. If it's not installed, the package is simply called **sysv-rc-conf**. Open a terminal, enter the command **sudo sysv-rc-conf** and now a screen should open like the one I've attached.

WARNING: don't disable anything of which you don't know what it does. You don't want to end up with a computer that doesn't have internet or can't print anymore.

Now scroll down to the Ondemand service and remove all the x's with your space bar.

WARNING: just remove the x's of the Ondemand service, nothing else.

(the reason I do this is that I don't want this topic to end up in the 'Malicious commands' thread ;) )

Now press 'q' to quit sysv-rc-conf and restart your computer. The Ondemand service should be disabled and another source of possible xruns should be gone.

Your JACK setting look ok. I would disable soft monitoring and I would also advise to install the **a2jmidid** package and use a2jmidid instead of the Seq or Raw ALSA drivers.

Best,

Jeremy

---

### Post by mango42 on 2010-06-19
Hi **sgx** - kind of you to chip in here ;-)

LOL - Funny how I always seem to end up with Incredibly Boring Machines like Thinkpads (it's that little red mouse pointer thingie that grabs me every time - can't understand why anyone would prefer a trackpad!) - the only snag is that this T43 will never run firewire, as the ExpressCard slot refuses to play ball. Hence the Alien, which, despite having Ricoh f/w controllers, accepts a firewire i/f without a hiccup. Catch22.

> everything I can turn off at the bios, and still have an 'Enter Key' working, is off.

Yep; been there; done that; got the headache ;)

I am girding myself up for another battle with nVidia drivers as I seem to have run out of alternative options. It's the large number of backend xruns under JACK that makes me think there's something fundamental wrong here - having rotten ole Windoze[tm] literally 'on the blink' is maybe a red herring, maybe not.

Hey ho - I don't think I could face exploring another Linux incarnation right now but thanks for the pointer, anyway.

> I would google the firewire chipset on your computer with the firewire device you have, and see if red flags appear.

I *never, ever* use go00ogle as it only encourages further erosion of public domain information, IMO (I never forgave go00ogle for sequestering/enclosing DejaNews, then plunging it down a black hole - 10 years of very valuable data down the drain for the rest of us!). Using [www.startpage.com]("http://www.startpage.com") always leads to **ffado** anyway - firewire is for another day - first priority is to get the onboard sound behaving properly, if at all possible.

Does anyone know of an app that will stress-test nVidia SLI cards on Linux?

---

### Post by AutoStatic on 2010-06-19
So the Ondemand service is not the issue :(
What does **cat /proc/interrupts** return?

---

### Post by sgx on 2010-06-19
> **mango42 said:**
> Thanks for pitching in so rapidly, guys - much appreciated.

Hi, there are advantages to popping in a CD based non-ubuntu OS that runs in memory,
in this case, one eliminates

possible config errors on your hardisk
possible gui issues (uses kde instead of gnome )
possible kernel issues ( uses a different and preconfigured RT kernel )
possible hardware recognition issues (debian Vs nvidia ain't pretty)
possible permissions config issues (the CD agrees with itself on who does what. sudo is not used, root is the root password, type su, press enter,
then type that four letter password, and you get the root prompt)
possible 'bloatware interaction syndrome'. (subtle devils no one on earth will ever figure out)

In addition, having several different live media can be useful when rescuing someones wintel crate from the dark forces of cyberdang.
2013 is coming. We must be ready.

Cheers

---

### Post by mango42 on 2010-06-19
@ **sgx** - point taken about LiveCD's - I'll try that route.

> **sgx said:**
> 2013 is coming. We must be ready.

I'm no fan of Arguelles, but for 'the good guys' October 28th, 2011 seems more likely to be transformation point.:popcorn:

@ **AutoStatic**

Thanks for sticking with this.
cat /proc/interrupts shows:-

```
            CPU0       
   0:        131   IO-APIC-edge      timer
   1:        378   IO-APIC-edge      i8042
   7:          1   IO-APIC-edge    
   8:          0   IO-APIC-edge      rtc0
   9:       1631   IO-APIC-fasteoi   acpi
  12:      20866   IO-APIC-edge      i8042
  14:          0   IO-APIC-edge      pata_amd
  15:       4923   IO-APIC-edge      pata_amd
  17:          0   IO-APIC-fasteoi   mmc0
  18:          3   IO-APIC-fasteoi   ohci1394
  20:       2141   IO-APIC-fasteoi   ehci_hcd:usb1
  21:       6830   IO-APIC-fasteoi   sata_nv
  22:        196   IO-APIC-fasteoi   sata_nv, NVidia CK804
  23:        776   IO-APIC-fasteoi   ohci_hcd:usb2
  28:          1   PCI-MSI-edge      eth0
 NMI:          0   Non-maskable interrupts
 LOC:     385817   Local timer interrupts
 SPU:          0   Spurious interrupts
 CNT:          0   Performance counter interrupts
 PND:          0   Performance pending work
 RES:          0   Rescheduling interrupts
 CAL:          0   Function call interrupts
 TLB:          0   TLB shootdowns
 TRM:          0   Thermal event interrupts
 THR:          0   Threshold APIC interrupts
 MCE:          0   Machine check exceptions
 MCP:          2   Machine check polls
 ERR:          1
 MIS:          0
```

Looks like I might have a problem with IRQ 22? Time to wipe all video drivers and start again as per [nVidia latest Drivers - How to install - (180.xx - 185.xx - 190.xx)]("http://ubuntuforums.org/showthread.php?t=990978") ? That thread has 132 pages so far - hmmm...

Okay, so before that I will tread very warily into **sysv-rc-conf** bearing in mind your very sensible disclaimer - looks horrendously powerful ):P

---

### Post by AutoStatic on 2010-06-19
Hello mango42, no need to fiddle with sysv-rc-conf if the CPU Frequency Scaling applet yields no better results.
The problem could be the shared interrupt on IRQ 22. Both your graphics card, a SATA controller and your soundcard share the same interrupt. Pretty busy over there! Maybe rtirq-init could be helpful, but therefore you also need a realtime kernel. Are you using a realtime kernel?

---

### Post by mango42 on 2010-06-19
Yeah, probably one of the 2 video cards on the Alien m9700 is interfering?

Yep, realtime kernel on UbuntuStudio 9.10 - from fallible memory it's **2.6.31-9rt**

I have just found [this excellent thread]("http://wiki.linuxmusicians.com/doku.php?id=system_configuration") containing a perl script (thanks to **raboof**?), realTimeConfigQuickScan.pl that gives a good idea what's right and wrong on a realtime system. However, it didn't complain about crowded interupts, so I'm delving into how to use **rtirq-init**.

Any words about **hpet**? As in:-

```
Checking access to the high precision event timer... not readable.
** Warning: /dev/hpet found, but not readable.
** make /dev/hpet readable by the 'audio' group
   For more information, see http://wiki.linuxmusicians.com/doku.php?id=system_configuration#hpet
```

The link doesn't seem to exist.

Porro et deorsum... :guitar: (I wish!)

---

### Post by AutoStatic on 2010-06-19
You could try it with rtirq-init. Make sure your */etc/default/rtirq* file contains the following lines:
```
RTIRQ_NAME_LIST="rtc 'NVidia CK804' i8042"
...
RTIRQ_NON_THREADED="rtc 'NVidia CK804'"
```

Like this your onboard card should get a higher priority.
And don't worry about the hpet thing, I think it's a system timer thingy, so probably only important when you work a lot with MIDI. Not sure though.

---

### Post by mango42 on 2010-06-20
Thanks for that, **AutoStatic** - I didn't realise the NVidia entry for RTIRQ_NAME_LIST etc required '' around it!

I gave up fiddling and decided to install the video driver (195....) direct from nVidia - imagine my dismay when the exact same problem as under Windoze showed up - screen blinking on and off at ~1 second intervals - so I guess whoever repaired the machine didn't do a proper job! It's kinda weird though, as using the built-in Ubuntu video drivers this situation doesn't occur - totally stable video, no extra heat nor nuttin' - so I guess it's another reinstall day today! I don't need the SLI stuff anymore as my grandson has moved on from Flight Simulation (that's my excuse, anyway!:p )

This time I'll go straight for Firewire, which should at least shift the IRQ's around a bit...!

---

### Post by mango42 on 2010-08-24
I guess this thread is as good as anywhere for me to go on moaning ;-)

Thanks to AutoStatic's PPA, I have never got this far with a Saffire Pro 40 - it's beginning to feel like I might get to use this box 'real soon now' but I've hit a snag and I am not even sure whether his libffado2 is really installed as Synaptic still shows v2.0.0 after a reload.

```
uname -a
Linux ubuntustudio 2.6.31-11-rt #154-Ubuntu SMP PREEMPT RT Wed Jun 9 13:40:34 UTC 2010 x86_64 GNU/Linux
```

```
heard@ubuntustudio:~$ ffado-test ListDevices
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.999.0-
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x00130e04014014c5  0x0000130E  0x00000005   Focusrite - SAFFIRE_PRO_40
   1       0x0003252162004a26  0x00000325  0x00000000   Linux - ohci1394  - 
no message buffer overruns

--------------------------------------------------------------------
```

and Jack message:

```
13:08:35.062 /usr/bin/jackd -P70 -dfirewire -dhw:0 -r48000 -p128 -n3 -i12 -o12
jackd 0.119.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
13:08:35.068 JACK was started with PID=4659.
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    1542498
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
00386027143:  (ffado.cpp)[  92] **ffado_streaming_init: libffado 2.999.0- built Aug 18 2010 13:36:42**
00386342348: [31mWarning (dice_eap.cpp)[ 881] updateNameCache: What is this function about?
[0m00386479629:  (dice_avdevice.cpp)[ 626] showDevice:  DICE Parameter Space info:
00386479662:  (dice_avdevice.cpp)[ 627] showDevice:   Global  : offset=0x0028 size=0360
00386479676:  (dice_avdevice.cpp)[ 628] showDevice:   TX      : offset=0x0190 size=0568
00386479689:  (dice_avdevice.cpp)[ 629] showDevice:                 nb=   2 size=0280
00386479700:  (dice_avdevice.cpp)[ 630] showDevice:   RX      : offset=0x03C8 size=1128
00386479712:  (dice_avdevice.cpp)[ 631] showDevice:                 nb=   2 size=0280
00386479724:  (dice_avdevice.cpp)[ 632] showDevice:   UNUSED1 : offset=0x0830 size=0016
00386479736:  (dice_avdevice.cpp)[ 633] showDevice:   UNUSED2 : offset=0x0000 size=0000
00386479748:  (dice_avdevice.cpp)[ 635] showDevice:  Global param space:
00386480955:  (dice_avdevice.cpp)[ 638] showDevice:   Owner            : 0x00000000FFFF0000
00386482542:  (dice_avdevice.cpp)[ 641] showDevice:   Notification     : 0x00000010
00386485466:  (dice_avdevice.cpp)[ 644] showDevice:   Nick name        : Pro40-001
[B]13:08:37.077 JACK was stopped successfully.
13:08:37.082 Post-shutdown script...
13:08:37.082 killall jackd
4c5
00386486817:  (dice_avdevice.cpp)[ 648] showDevice:   Clock Select     : 0x00 0x0C
00386489509:  (dice_avdevice.cpp)[ 652] showDevice:   Enable           : false
00386494035:  (dice_avdevice.cpp)[ 656] showDevice:   Clock Status     : locked 0x00
00386496949:  (dice_avdevice.cpp)[ 659] showDevice:   Extended Status  : 0x00000000
00386499021:  (dice_avdevice.cpp)[ 662] showDevice:   Samplerate       : 0x00007D00 (32000)[/B]
00386501405:  (dice_avdevice.cpp)[ 665] showDevice:   Version          : 0x01000400
00386502595:  (dice_avdevice.cpp)[ 674] showDevice:   Version          : 0x01000400 (1.0.4.0)
00386503945:  (dice_avdevice.cpp)[ 677] showDevice:   Clock caps       : 0x1325001E
00386505726:  (dice_avdevice.cpp)[ 680] showDevice:   Clock sources    :
00386505741:  (dice_avdevice.cpp)[ 686] showDevice:     SPDIF
00386505753:  (dice_avdevice.cpp)[ 686] showDevice:     AES34
00386505764:  (dice_avdevice.cpp)[ 686] showDevice:     SPDIF-OPT
00386505776:  (dice_avdevice.cpp)[ 686] showDevice:     AES78
00386505787:  (dice_avdevice.cpp)[ 686] showDevice:     AES-ANY
00386505798:  (dice_avdevice.cpp)[ 686] showDevice:     ADAT
00386505810:  (dice_avdevice.cpp)[ 686] showDevice:     ADAT_AUX
00386505821:  (dice_avdevice.cpp)[ 686] showDevice:     Word Clock
00386505833:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00386505844:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00386505855:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00386505866:  (dice_avdevice.cpp)[ 686] showDevice:     Unused
00386505878:  (dice_avdevice.cpp)[ 686] showDevice:     Internal
00386505889:  (dice_avdevice.cpp)[ 689] showDevice:  TX param space:
00386505900:  (dice_avdevice.cpp)[ 690] showDevice:   Nb of xmit        : 2
00386505912:  (dice_avdevice.cpp)[ 692] showDevice:   Transmitter 0:
00386507367:  (dice_avdevice.cpp)[ 695] showDevice:    ISO channel       :   0
00386509834:  (dice_avdevice.cpp)[ 697] showDevice:    ISO speed         :   2
00386511439:  (dice_avdevice.cpp)[ 700] showDevice:    Nb audio channels :  10
00386512791:  (dice_avdevice.cpp)[ 702] showDevice:    Nb midi channels  :   1
00386514376:  (dice_avdevice.cpp)[ 705] showDevice:    AC3 caps          : 0x00000000
00386515723:  (dice_avdevice.cpp)[ 707] showDevice:    AC3 enable        : 0x00000000
00386521073:  (dice_avdevice.cpp)[ 710] showDevice:    Channel names     :
00386521118:  (dice_avdevice.cpp)[ 715] showDevice:      IP 1
00386521130:  (dice_avdevice.cpp)[ 715] showDevice:      IP 2
00386521141:  (dice_avdevice.cpp)[ 715] showDevice:      IP 3
00386521153:  (dice_avdevice.cpp)[ 715] showDevice:      IP 4
00386521164:  (dice_avdevice.cpp)[ 715] showDevice:      IP 5
00386521175:  (dice_avdevice.cpp)[ 715] showDevice:      IP 6
00386521186:  (dice_avdevice.cpp)[ 715] showDevice:      IP 7
00386521198:  (dice_avdevice.cpp)[ 715] showDevice:      IP 8
00386521209:  (dice_avdevice.cpp)[ 715] showDevice:      SPDIF L
00386521221:  (dice_avdevice.cpp)[ 715] showDevice:      SPDIF R
00386521233:  (dice_avdevice.cpp)[ 692] showDevice:   Transmitter 1:
00386525217:  (dice_avdevice.cpp)[ 695] showDevice:    ISO channel       :   1
00386526424:  (dice_avdevice.cpp)[ 697] showDevice:    ISO speed         :   2
00386527776:  (dice_avdevice.cpp)[ 700] showDevice:    Nb audio channels :  10
00386530512:  (dice_avdevice.cpp)[ 702] showDevice:    Nb midi channels  :   0
00386531874:  (dice_avdevice.cpp)[ 705] showDevice:    AC3 caps          : 0x00000000
00386533446:  (dice_avdevice.cpp)[ 707] showDevice:    AC3 enable        : 0x00000000
00386534986:  (dice_avdevice.cpp)[ 710] showDevice:    Channel names     :
00386535012:  (dice_avdevice.cpp)[ 715] showDevice:      ADAT 1
00386535025:  (dice_avdevice.cpp)[ 715] showDevice:      ADAT 2
00386535037:  (dice_avdevice.cpp)[ 715] showDevice:      ADAT 3
00386535048:  (dice_avdevice.cpp)[ 715] showDevice:      ADAT 4
00386535060:  (dice_avdevice.cpp)[ 715] showDevice:      ADAT 5
00386535071:  (dice_avdevice.cpp)[ 715] showDevice:      ADAT 6
00386535083:  (dice_avdevice.cpp)[ 715] showDevice:      ADAT 7
00386535094:  (dice_avdevice.cpp)[ 715] showDevice:      ADAT 8
00386535105:  (dice_avdevice.cpp)[ 715] showDevice:      Loop 1
00386535117:  (dice_avdevice.cpp)[ 715] showDevice:      Loop 2
00386535129:  (dice_avdevice.cpp)[ 719] showDevice:  RX param space:
00386535140:  (dice_avdevice.cpp)[ 720] showDevice:   Nb of recv        : 2
00386535152:  (dice_avdevice.cpp)[ 722] showDevice:   Receiver 0:
00386536561:  (dice_avdevice.cpp)[ 725] showDevice:    ISO channel       :   2
00386538310:  (dice_avdevice.cpp)[ 727] showDevice:    Sequence start    :   0
00386539873:  (dice_avdevice.cpp)[ 730] showDevice:    Nb audio channels :  12
00386541445:  (dice_avdevice.cpp)[ 732] showDevice:    Nb midi channels  :   1
00386542798:  (dice_avdevice.cpp)[ 735] showDevice:    AC3 caps          : 0x00000C00
00386544379:  (dice_avdevice.cpp)[ 737] showDevice:    AC3 enable        : 0x00000000
00386545909:  (dice_avdevice.cpp)[ 740] showDevice:    Channel names     :
00386545922:  (dice_avdevice.cpp)[ 745] showDevice:      Mon 1
00386545934:  (dice_avdevice.cpp)[ 745] showDevice:      Mon 2
00386545945:  (dice_avdevice.cpp)[ 745] showDevice:      Line 3
00386545956:  (dice_avdevice.cpp)[ 745] showDevice:      Line 4
00386545968:  (dice_avdevice.cpp)[ 745] showDevice:      Line 5
00386545979:  (dice_avdevice.cpp)[ 745] showDevice:      Line 6
00386545990:  (dice_avdevice.cpp)[ 745] showDevice:      Line 7
00386546012:  (dice_avdevice.cpp)[ 745] showDevice:      Line 8
00386546026:  (dice_avdevice.cpp)[ 745] showDevice:      Line 9
00386546037:  (dice_avdevice.cpp)[ 745] showDevice:      Line 10
00386546048:  (dice_avdevice.cpp)[ 745] showDevice:      SPDIF L
00386546060:  (dice_avdevice.cpp)[ 745] showDevice:      SPDIF R
00386546072:  (dice_avdevice.cpp)[ 722] showDevice:   Receiver 1:
00386547511:  (dice_avdevice.cpp)[ 725] showDevice:    ISO channel       :   3
00386549944:  (dice_avdevice.cpp)[ 727] showDevice:    Sequence start    :   0
00386555023:  (dice_avdevice.cpp)[ 730] showDevice:    Nb audio channels :   8
00386556515:  (dice_avdevice.cpp)[ 732] showDevice:    Nb midi channels  :   0
00386561047:  (dice_avdevice.cpp)[ 735] showDevice:    AC3 caps          : 0x00000000
00386566019:  (dice_avdevice.cpp)[ 737] showDevice:    AC3 enable        : 0x00000000
00386571046:  (dice_avdevice.cpp)[ 740] showDevice:    Channel names     :
00386571064:  (dice_avdevice.cpp)[ 745] showDevice:      ADAT 1
00386571076:  (dice_avdevice.cpp)[ 745] showDevice:      ADAT 2
00386571087:  (dice_avdevice.cpp)[ 745] showDevice:      ADAT 3
00386571098:  (dice_avdevice.cpp)[ 745] showDevice:      ADAT 4
00386571110:  (dice_avdevice.cpp)[ 745] showDevice:      ADAT 5
00386571121:  (dice_avdevice.cpp)[ 745] showDevice:      ADAT 6
00386571133:  (dice_avdevice.cpp)[ 745] showDevice:      ADAT 7
00386571144:  (dice_avdevice.cpp)[ 745] showDevice:      ADAT 8
[B]firewire ERR: Could not start streaming threads: -1
DRIVER NT: could not start driver[/B]
cannot start driver
no message buffer overruns
jackd: no process found
13:08:37.563 Post-shutdown script terminated with exit status=256.
```

Strange stuff in bold - both ffado mixer & jack are set to 48kHz...?

Does the ffado mixer **routing** tab work properly yet, does anyone know?

---

### Post by AutoStatic on 2010-08-24
mango42, try leaving the number of input and output ports to default. You're now setting it to 12 while the Saffire has 20 inputs and outputs. Also try a periods setting of 2 instead of 3, only USB1 devices need 3, all other stuff works better with 2. And did you update to jackd 0.119.0? Did you use a package for it or did you compile it yourself?
The DRIVER NT error could otherwise be related to:
[LIST]
[*]Bad quality cable, or a broken cable
[*]FireWire controller sharing its IRQ with other devices, so please post the output of **cat /proc/interrupts**
[/LIST]

And yes, Synaptic still shows v2.0.0 because I've update the libffado2 source package of 10.04. Besides, my package is a svn checkout of the 2.0.0 branch so version-wise it is still version 2.0.0.
2.0.1 is a different branch, that's the branch that works with the juju FireWire stack.
And the Mixer doesn't work, at least not the version in my package. Afaik this has got something to do with Python modules compatibility shalamalalabibelebingbing.

---

### Post by mango42 on 2010-08-24
I'll only ever use 12 inputs - perhaps it's an analog thing to mute everything not being used? But I guess Qjack isn't the right place ;-)

I'm assuming it **is** necessary to load ffado-mixer to get dbus interested - or can the vital bits be loaded from QjackCtl?

No, I haven't touched **jackd** - it is as the system decides - maybe an update, not that I ever saw it listed.

Cable is HQ, clean contacts etc.

$ cat /proc/interrupts

```

            CPU0       
   0:        131   IO-APIC-edge      timer
   1:          8   IO-APIC-edge      i8042
   7:          1   IO-APIC-edge    
   8:          0   IO-APIC-edge      rtc0
   9:       1289   IO-APIC-fasteoi   acpi
  12:        135   IO-APIC-edge      i8042
  14:          0   IO-APIC-edge      pata_amd
  15:       3182   IO-APIC-edge      pata_amd
  17:          0   IO-APIC-fasteoi   mmc0
  18:        196   IO-APIC-fasteoi   ohci1394, rtl8180
  20:       1451   IO-APIC-fasteoi   ehci_hcd:usb1
  21:       4320   IO-APIC-fasteoi   sata_nv
  22:        195   IO-APIC-fasteoi   sata_nv, NVidia CK804
  23:       1344   IO-APIC-fasteoi   ohci_hcd:usb2
  28:          1   PCI-MSI-edge      eth0
 NMI:          0   Non-maskable interrupts
 LOC:     222853   Local timer interrupts
 SPU:          0   Spurious interrupts
 CNT:          0   Performance counter interrupts
 PND:          0   Performance pending work
 RES:          0   Rescheduling interrupts
 CAL:          0   Function call interrupts
 TLB:          0   TLB shootdowns
 TRM:          0   Thermal event interrupts
 THR:          0   Threshold APIC interrupts
 MCE:          0   Machine check exceptions
 MCP:          1   Machine check polls
 ERR:          1
 MIS:          0
```

Although the wifi driver is installed, it's not in use, as **nm-applet** is not loaded at start up.

Looking in SysMonitor Processes, jackd seems hung up waiting for a 'sys_rt_sigtimedwait' signal...

Thanks yet again :KS

Oh and beware the twisted Python ;-)

---

### Post by AutoStatic on 2010-08-25
> **mango42 said:**
> I'm assuming it **is** necessary to load ffado-mixer to get dbus interested - or can the vital bits be loaded from QjackCtl?You don't need dbus unless you want to use the mixer. But the mixer is still non-functional. You don't need dbus in order to get the ffado driver to work.

> **mango42 said:**
> No, I haven't touched **jackd** - it is as the system decides - maybe an update, not that I ever saw it listed.Ah, ok, then you probably have PPA's enabled (probably FalkTX and/or philip5). I never enable any PPA, especially not the aformentioned ones. I just install the packages I need and disable it again.

> **mango42 said:**
> ```

  18:        196   IO-APIC-fasteoi   ohci1394, rtl8180
```Your FireWire controller shares an IRQ with your wifi adapter.

> **mango42 said:**
> Although the wifi driver is installed, it's not in use, as **nm-applet** is not loaded at start up.But the module is loaded though and NetworkManager is a system service so the WiFi adapter is scanning nonetheless. Try unloading the module with **sudo modprobe -r rtl8180** and then start up JACK again.

---

### Post by mango42 on 2010-09-03
Yes, it worked - once - sorta ;-) Without your prompt I would not have tried that as the internal wifi is switched off in the BIOS.

For the first time ever, I saw all the audio connections in Jack - YAY :p

But on the hardware, channels 5-8 were showing -3dB signal without anything 'live' on the inputs - hmm.

So I remembered when fiddling about before that one of the dropdown menus on the ffado mixer adjusted which clock source to use. When I changed this from Internal to S/PDif and back again, the hardware responded and all meters showed zero signal, as expected.

Great, I thought, so closed the mixer, fired up Jack only to find 'error - could not stream device'. Did a reboot but this time Jack wouldn't co-operate. Next I'll try switching the Saffire 40 off as well.

I'll get there, thanks to you guys beating the path... ;)

The local net is in total disarray just now - don't even now whether this will get through...

---

### Post by mango42 on 2010-10-07
In my still fruitless attempts to get the Saffire i/f working I think I've finally traced why QJackCtl and jackd is hanging but don't understand why.

According to System Monitor it turns out that **a2jmidid** is awaiting a **hrtimer_nanosleep** signal which in turn is causing Jack to wait for a2jmidid. 

Hmm, either I've unknowingly made a mess or behaviour has changed in Lucid Studio 10.04 - this issue now arises on both i386 and amd64 clean installations from USB stick. (A secondary question is how does one get Synaptic to look on a stick rather than CD?)

---

### Post by AutoStatic on 2010-10-07
How do you start a2jmidid? It has to run in the background otherwise QjackCtl will stall. Did you add an ampersand & after the command?

---

### Post by mango42 on 2010-10-07
I add it to QJackCtl options as: **a2jmidid -j default** - perhaps I have it garbled? Quite likely :confused:

---

### Post by AutoStatic on 2010-10-07
Add an ampersand at the end of the command: **a2jmidid &**
You don't need to tell a2jmidid to connect to the default jack instance, it will do it automatically, so adding **-j default** is not necessary.

---

### Post by mango42 on 2010-10-07
Many thanks - yet again. Where would I be without your help and PPA .debs ?

The more I learn about Linux the less I seem to be able to retain...

---

### Post by mango42 on 2010-10-18
Apologies if this is getting boring...I could be wearing out my welcome here ;-)

I have Lucid UbuntuStudio 64bit installed recently from USB. I would like to use AutoStatic's libffado2.0.0.0+svn set of .deb files but Synaptic reports that libffado2.0.0.1 is already installed (and doesn't allow Jack to read the saffire40 firewire interface).

Ok, so I went to remove the installed **libffado2** via synaptic but it insists that it also needs to remove jackd-firewire and, gasp, ubuntustudio-audio. Gulp! I may as well start again if this is truly the case.

So is there a way to *regress* to AutoStatic's [PPA version that works]("https://launchpad.net/~autostatic/+archive/ffado"), without another system rebuild, please?

---

### Post by AutoStatic on 2010-10-18
My FFADO packages superseed the ones from Lucid. So you probably have a PPA enabled that has FFADO 2.0.1. Disable that PPA and you should be able to install my packages.

---

### Post by mango42 on 2010-10-19
No PPAs enabled - I took your advice on that a while back. I only recently downloaded this version of 10.04 UbuntuStudio so perhaps it has already been updated at source?

Whatever - just another brick to pull out of the wall...

Now, if I could just get *net-less* Synaptic to look on the USB drive instead of DVD I wouldn't feel so leery about removing jackd-firewire and ubuntustudio-audio... ;-)

---

### Post by AutoStatic on 2010-10-19
> **mango42 said:**
> No PPAs enabled - I took your advice on that a while back. I only recently downloaded this version of 10.04 UbuntuStudio so perhaps it has already been updated at source?10.04 comes with FFADO 2.0, not 2.0.1. But what is the exact version of this libffado2 2.0.1 package? What does **aptitude show libffado2** in a terminal return?

---

### Post by mango42 on 2010-10-20
> **AutoStatic said:**
> 10.04 comes with FFADO 2.0, not 2.0.1. But what is the exact version of this libffado2 2.0.1 package? What does **aptitude show libffado2** in a terminal return?

```
mmm@mmm:~$ aptitude show libffado2
Package: libffado2
State: installed
Automatically installed: no
Version: 2.0.0-1ubuntu1
Priority: optional
Section: libs
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1,778k
Depends: libc6 (>= 2.8), libexpat1 (>= 1.95.8), libgcc1 (>= 1:4.1.1),
         libglib2.0-0 (>= 2.12.0), libglibmm-2.4-1c2a (>= 2.22.0), libiec61883-0
         (>= 1.2.0), libraw1394-11, libsigc++-2.0-0c2a (>= 2.0.2), libstdc++6
         (>= 4.4.0), libxml++2.6-2 (>= 2.24.0), libxml2 (>= 2.6.27)
Description: FFADO API
 FFADO is a Linux driver for FireWire (IEEE1394) audio devices. 

```

I also double checked that '*Software Sources | Other Software*' only shows **[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner**

Edit: Attempting to install your .debs (eg: double-clicking on **libffado2_2.0.0+svn1881-0lucid0~autostatic_amd64.deb**) briefly brings up the GDebi Package Installer but it just folds again, with no error messages.

---

### Post by AutoStatic on 2010-10-20
> **mango42 said:**
> ```
Version: 2.0.0-1ubuntu1
```Ok, good, you got FFADO 2.0.0 installed, the 1ubuntu1 addition is a bit misleading, but it is indeed 2.0.0. Sorry about the miscommunication

> **mango42 said:**
> Edit: Attempting to install your .debs (eg: double-clicking on **libffado2_2.0.0+svn1881-0lucid0~autostatic_amd64.deb**) briefly brings up the GDebi Package Installer but it just folds again, with no error messages.I recall there is/was a gdebi bug in 10.04. What if you install it manually in a terminal with **dpkg -i libffado2_2.0.0+svn1881-0lucid0~autostatic_amd64.deb** ? Another option would be to enable my FFADO PPA in Synaptic, Reload, install FFADO (it should pick the packages from my PPA) and disable my PPA again. This will also take care of all the dependencies.

Best,

Jeremy

---

### Post by mango42 on 2010-10-20
There is a society in Britain called the 'Plymouth Brethren' - one of their most well known idiosyncrasies is to do everything the most difficult way possible. Perhaps I should join them? :)

The reason for that bit of OT is because I don't have a net connection on that machine because trying to install nm-applet and its dependencies didn't work and Synaptic won't look on the USB stick to do it 'properly'...

Catch23?

Many thanks for your command line suggestion - it's sure to work... ;-)

---

### Post by AutoStatic on 2010-10-20
> **mango42 said:**
> The reason for that bit of OT is because I don't have a net connection on that machine because trying to install nm-applet and its dependencies didn't work and Synaptic won't look on the USB stick to do it 'properly'...Then try uninstalling NetworkManager and add these lines to */etc/network/interfaces*:
```
auto eth0
iface eth0 inet dhcp
```Unless eth0 is another network card than your ethernet NIC. I always do that on my music production machine, NetworkManager has nothing to do over there.

---

