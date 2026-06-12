---
title: "External MIDI and Audigy Platimun eX"
date: 2009-12-14
forum: Ubuntu Studio
---

### Post by scinram on 2009-12-14
I cannot get my keyboard to play through Ubuntu 910 / Audigy configuration. All other aspects of the sound system work as expected, it would appear - and i can even get a Keyboard Synth to play back through the Hard Synth.

I have read and applied ALL references [that i can find] both inside this forum and externally, but clearly i am missing something basic.

These are some of the more pertinent links i have used;


[http://ubuntuforums.org/showthread.php?t=8736&page=5](http://ubuntuforums.org/showthread.php?t=8736&page=5)

[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

[http://alsa.opensrc.org/index.php/Emu10k1#How_to_record_on_Audigy_and_Audigy_2](http://alsa.opensrc.org/index.php/Emu10k1#How_to_record_on_Audigy_and_Audigy_2)


My question is straight forward.

Is there anybody out there who has been able to get their External MIDI Keyboard to play/rec through Ubuntu 910 with Audigy Platinum eX Soundblaster??

If so i would be MOST interested in learning how.

Many thanks

SC

####################

SYSTEM INFORMATION
    Running Ubuntu Linux, the Ubuntu 9.10 (karmic) release.
    GNOME: 2.28.1 (Ubuntu 2009-11-03)
    Kernel version: 2.6.31-9-rt (#152-Ubuntu SMP PREEMPT RT Thu Oct 15 05:01:14 UTC 2009)
    GCC: 4.4.1 (i486-linux-gnu)
    Xorg: unknown (26 October 2009  05:15:02PM)
    Hostname: bntstud
    Uptime: 0 days 0 h 19 min

CPU INFORMATION
    AuthenticAMD, AMD Athlon(TM) XP 3000+
    Number of CPUs: 1
    CPU clock currently at 2166.786 MHz with 512 KB cache
    Numbering: family(6) model(10) stepping(0)
    Bogomips: 4333.57
    Flags: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up

MEMORY INFORMATION
    Total memory: 1999 MB
    Total swap: 1655 MB

STORAGE INFORMATION
    SCSI device -  scsi0
        Vendor:  ATA      
        Model:  IC35L040AVVN07-0 
    SCSI device -  scsi0
        Vendor:  ATA      
        Model:  IC35L080AVVA07-0 
    SCSI device -  scsi1
        Vendor:  HL-DT-ST 
        Model:  DVDRAM GSA-H42N  
    SCSI device -  scsi2
        Vendor:  SanDisk  
        Model:  SanDisk Cruzer   

HARDWARE INFORMATION
MOTHERBOARD
    Host bridge
        VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
        Subsystem: ASUSTeK Computer Inc. Device 807f
    PCI bridge(s)
        VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
    USB controller(s)
        VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
        VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
    ISA bridge
        VIA Technologies, Inc. VT8233A ISA Bridge
        Subsystem: ASUSTeK Computer Inc. Device 808c
    IDE interface
        VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. Device 808c

GRAPHIC CARD
    VGA controller
        nVidia Corporation G73 [GeForce 7600 GS] (rev a2)

SOUND CARD
    Multimedia controller
        Creative Labs SB Audigy (rev 03)
        Subsystem: Creative Labs Device 0051

NETWORK
    Ethernet controller
        Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+

NVIDIA GRAPHIC CARD INFORMATION
    Model name: GeForce 7600 GS
    Card Type: AGP 4x
    Video RAM: 512 MB
    GPU Frequency: 400 MHz
    Driver version: NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
##########################

root@bntstud:~$ cat /proc/asound/cards
 0 [Audigy         ]: Audigy - SB Audigy 1 [SB0090]
                      SB Audigy 1 [SB0090] (rev.3, serial:0x511102) at 0xd400, irq 17
 1 [Headset        ]: USB-Audio - Logitech USB Headset
                      Logitech Logitech USB Headset at usb-0000:00:11.2-1.1, full speed
##########################

---

### Post by Tricity on 2009-12-14
This almost sounds like the problem I posted earlier today ("Audigy ZS pro MPU-401 MIDI input not working") - are you using the game port for MIDI-in?

---

### Post by scinram on 2009-12-14
> **Tricity said:**
> This almost sounds like the problem I posted earlier today ("Audigy ZS pro MPU-401 MIDI input not working") - are you using the game port for MIDI-in?


Hi Tricity ... well 'the same' in as  much we cannot get external MIDI to play through. 

No i am not connecting through game port ... the Audigy Platinum eX card comes with a breakout box which has MIDI IN and MIDI OUT hardware interface.

_[IMG]http://zimpics.org/img/Audigy_1_livedrive.jpg[/IMG]_

I have even loaded the GM soundfonts off the original Creative CD and loaded them as per instructions on this forum ... apparently ... as i now have an extra 'tab' appear in my Jack interface [viz: 'Alsa' tab] ... this is what it all looks like:

SnapShot #1 - Audio Tab

[IMG]http://zimpics.org/img/Audio_tab_01.png[/IMG]


Snapshot #2 - MIDI Tab

[IMG]http://zimpics.org/img/MIDI_tab_01.png[/IMG]


Snapshot #3 - ALSA Tab

[IMG]http://zimpics.org/img/ALSA_tab_01.png[/IMG]


I can play the Virtual Keyboard through both the Timidity Playback port and the ZynAddSubFx port ....

... but i cant get my Roland EM-30 to play.

Can anybody spot what it is i am missing / doing wrong??

Thanks

SC

---

### Post by Tricity on 2009-12-14
Based on your screenshots, I still think we are looking at the same problem. The Audigy has two UARTs for MIDI. One goes to the game port, one goes to the header that connects to the breakout box. Meaning: we are both using the Audigy UART (as opposed, to, e.g., a MIDI-USB converter). We both can get MIDI _out_ of the Audogy card (to an external MIDI device), but the Audigy does not recognize anything coming in from an external device.

The Audigy MPU-401 (UART) jack is the game port UART, and (I think, but I haven't proven it) the MPU-401 #2 is the breakout box UART. Now I am really starting to wonder if this might be a driver issue... perhaps an uninitialized UART or a missing config bit. 

I briefly looked at the sources of the lowest-level modules - gameport.c and emu10k1_gp.c - but could not find anything that made immediate sense to me. I might have to get my hands on an emu10k1 datasheet. 

Question: Do you have dual boot with Windoze? If so, does it work there? I am 100% Microsoft-free, so I couldn't tell.

---

### Post by Tricity on 2009-12-14
Here is where it gets interesting. The problem has been around for some time. I found a few links:

[http://ubuntuforums.org/showthread.php?t=476633](http://ubuntuforums.org/showthread.php?t=476633)

From a post: "I have the same problem with MIDI in with my SoundBlaster Live!. The strange thing is, if I boot in Windows XP first and then reboot in Linux Midi in is working!"

I tried to follow the links from this one, but no luck so far.

[http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg23619.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg23619.html)

From a post. "Any discerning people out there think it's a good idea to post this problem to the alsa-dev list??"

The ALSA bug tracking system is not searchable (or it is getting too late for me), no help there.

Tried a number of other links with the search phrase `alsa audigy zs emu10k1 "midi in"', but these seem to be copies. 

Can't believe that there is no solution out there yet.

---

### Post by Tricity on 2009-12-14
Just documenting as I move along - hope it helps solve the issue (and serves as a refernce for myself).

1) The emu10k1 datasheet is not freely available as far as I can tell. Does anybody have a pdf? And I am not talking about the 9-page design description.

2) Both MIDI-IN signals (breakout and joystick) get routed directly to the emu TQFP chip, pins 85 and 129, respectively. This is in contradiction to a emu10k1 pinout image I found on the web. Oh, yes. Any transients, overvoltage etc at the MIDI-IN ports and your emu10k1 is toast. Love it :rolleyes:

3) Oscilloscope shows that the MIDI signals from the external MIDI device arrive nicely at the emu chip. 

4) Initialization of the MPU-401 emulation in the emu10k1 is in .../sound/pci/emu10k1/emumpu401.c neat line 369.  I suspect that this is very close to the root of the problem.

Unfortunately, without the emu10k1 documentation (datasheet), I won't be able to get any further. 

What do y'all think - should this be submitted to ALSA as bug report? I am very tempted to do it.

---

### Post by scinram on 2009-12-14
> **Tricity said:**
> Based on your screenshots, I still think we are looking at the same problem. The Audigy has two UARTs for MIDI. One goes to the game port, one goes to the header that connects to the breakout box. Meaning: we are both using the Audigy UART (as opposed, to, e.g., a MIDI-USB converter). We both can get MIDI _out_ of the Audogy card (to an external MIDI device), but the Audigy does not recognize anything coming in from an external device.

OK ... sounds fair!

> **Tricity said:**
> The Audigy MPU-401 (UART) jack is the game port UART, and (I think, but I haven't proven it) the MPU-401 #2 is the breakout box UART. Now I am really starting to wonder if this might be a driver issue... perhaps an uninitialized UART or a missing config bit. 

I briefly looked at the sources of the lowest-level modules - gameport.c and emu10k1_gp.c - but could not find anything that made immediate sense to me. I might have to get my hands on an emu10k1 datasheet.

Hmmm ... over my head i am afraid ..*smile*..  

> **Tricity said:**
> Question: Do you have dual boot with Windoze? If so, does it work there? I am 100% Microsoft-free, so I couldn't tell.

Well .. yes i do .. did that is .. until my most recent rebuild coupla weeks back ... now run WINXP on an different LAN W/S and use Terminal to access it if i need to. [it serves as a fileserver for LAN data] - However, previously .. yes .. this machine was dual boot and yes the MIDI system worked flawlessly through CuBase ... so it would most unlikely be a hardware issue [.. famous last words?? ..]

---

### Post by scinram on 2009-12-14
> **Tricity said:**
> Here is where it gets interesting. The problem has been around for some time. ...<clip>... Can't believe that there is no solution out there yet.

Yes ... same thoughts have come to my mind - together with the horrible thought that simply because of that [*lone-ranger*], perhaps the problem may be "just me"!! Add in that I am over my depth *gurglegurgle* and it is somewhat reassuring to find somebody else with the similar symptoms, esp one who appears to know what they are talkin' bout.  :D

---

### Post by Tricity on 2009-12-15
I am now pretty sure that we are looking at some driver problem.

I filed a bug report with the ALSA gurus. I am merely a kernel amateur ;), not a kernel hacker. 

I'll keep this thread updated (still - what would be appreciated if anybody could find an emu10k1 datasheet - not the 9-page overview, but the *real* thing, a tome of anywhere from 120 to 450 pages - in that case, I could become even more active).

---

### Post by scinram on 2009-12-15
> **Tricity said:**
> I am now pretty sure that we are looking at some driver problem ...<clip>... what would be appreciated if anybody could find an emu10k1 datasheet - not the 9-page overview, but the *real* thing, a tome of anywhere from 120 to 450 pages - in that case, I could become even more active).

'emu10k1 datasheet'?? -- no idea really what to look for, except using that very description ... clearly nothing in google or torrents ... best i can do is the following:


[http://freenet-homepage.de/kxdev/docs/original/emu10k1-overview.pdf](http://freenet-homepage.de/kxdev/docs/original/emu10k1-overview.pdf)

[http://emu10k1.sourceforge.net/as10k1-manual/](http://emu10k1.sourceforge.net/as10k1-manual/)


Is this the dreaded 'brickwall' then?!?  ](*,)

SC

---

### Post by Tricity on 2009-12-15
Your first link is precisely the 9-page document that I had already found and that is of no use.

To give you an idea what I am looking for - here is a link:

[http://ww1.microchip.com/downloads/en/DeviceDoc/39609b.pdf](http://ww1.microchip.com/downloads/en/DeviceDoc/39609b.pdf)

This pdf document describes a microcontroller that must be programmed and configured in a way somewhat analogous to the emu10k1 FPGA. The corresponding emu10k1 document would contain similar information: chip pinout, block diagram, PCI interface description, list of registers, register configuration etc. 

My guess is that the guys at ALSA have something like this, otherwise code like emu10k1.c or emumpu401.c couldn't have been written that elegantly.

Yes, I think this is a temporary brick wall. I hope that ALSA bug #0004839 gets resolved, eventually. I'll report.

---

### Post by sgx on 2009-12-15
> **scinram said:**
> Yes ... same thoughts have come to my mind - together with the horrible thought that simply because of that [*lone-ranger*], perhaps the problem may be "just me"!! Add in that I am over my depth *gurglegurgle* and it is somewhat reassuring to find somebody else with the similar symptoms, esp one who appears to know what they are talkin' bout.  :D

On my m-audio 24/96 card, if I want to use the external midi keyboard, (Yamaha in my case), in the Alsa tab, I must connect zyn to my soundcards main midi entry on the opposite side. If I only connect to its midi-Through, I can still use both the zyn virtual keyboard, and the separate Virtual Keyboard to play zyn sounds, but not the external midi keyboard.
I have never needed anything in the middle midi tab in qjackctl, and midi in/out/through all work fine.
Hope this helps.

---

### Post by Tricity on 2009-12-15
Sgx,

thanks for the hint. Scinram's screenshot #3 shows the ALSA-MIDI connection - this is the one that counts. In this configuration, the synth works. If the synth input is linked to the SB at either 16:0 (gameport) or 16:32 (breakout box), there is no midi signal getting through. I don't use the middle tab, either (in fact, I turned off raw midi so that the middle tab is empty - not that it changed anything). It becomes even cleaer with a command-line tool such as amidi, which hooks up directly to a midi port, circumventing JACK.

I still think that we are looking at a driver issue.

And no news yet from ALSA.

---

### Post by Tricity on 2009-12-18
IT WORKS FOR ME NOW!!!

I got really obsessed, and I got involved in the kernel source more deeply than ever before. But I think I solved the problem.

For the record, the UART for the breakout box only works if the lowest bit of the [COLOR=#b8860b]A_IOCFG[/COLOR] register is pulsed upon initialization.  This can be done, for example, at the end of the function snd_emu10k1_audigy_midi in the emumpu401.c file.

Note that a full compilation of a custom kernel is NOT needed.

Scinram, I can help you set this up if you wish. In fact, I'd appreciate if you would be willing to beta-test my patch. You need to install the kernel sources and the kernel development tools. Let me know and I'll give you detailed instructions how to create a fixed snd_emu10k1.ko module.

---

### Post by scinram on 2009-12-18
> **sgx said:**
> On my m-audio 24/96 card, if I want to use the external midi keyboard, (Yamaha in my case), in the Alsa tab, I must connect zyn to my soundcards main midi entry on the opposite side. ..<clip>.. Hope this helps.

Thnx for the input sgx .... for confirmation and/or clarification, here are the two connections i can make through either tab ... MIDI or ALSA with the outcomes:

MIDI tab ....First the Virtual Keyboard playing via TiMidity 

[IMG]http://zimpics.org/img/MIDI_VKviaTimid.jpg[/IMG]


.... and now the Virtual Keyboard playing OUT to my Roland EM-30

[IMG]http://zimpics.org/img/MIDI_VKviaXtnKBoard.jpg[/IMG]



Now for the ALSA tab:

First the Virtual Keyboard playing through TiMidity again

[IMG]http://zimpics.org/img/ALSA_VKviaTimid.jpg[/IMG]


.... and now the Virtual Keyboard playing OUT to my physical keyboard


[IMG]http://zimpics.org/img/ALSA_VKviaXtnKBoard.jpg[/IMG]

Both connections give the same results through EITHER tab .. MIDI or ALSA

... but still the BRICKWALL!!!

Trying to get the external keyboard to play via TiMidity, using either TAB .... I have only posted the image of the ALSA connection.


[IMG]http://zimpics.org/img/ALSA_ExtnKBviaTimid.jpg[/IMG]



Silence is NOT Golden!!!

---

### Post by scinram on 2009-12-18
> **Tricity said:**
> IT WORKS FOR ME NOW!!!
<clip>
Scinram, I can help you set this up if you wish. In fact, I'd appreciate if you would be willing to beta-test my patch. You need to install the kernel sources and the kernel development tools. Let me know and I'll give you detailed instructions how to create a fixed snd_emu10k1.ko module.


KK ...for sure Tricity!! np *smile* 

Sources and Tools?? ... Give me the file list - if a cant get them via Synaptic plse past shell commands, together with a recipe and i will give it a go!

:guitar:

SC

---

### Post by Tricity on 2009-12-18
> **scinram said:**
> 
... but still the BRICKWALL!!!
Silence is NOT Golden!!!

Seems we have cross-posed. See my previous post - that exact configuration in your last screenshot - input from Audigy MPU-401 #2 to Timidity Port 0 works for me now. NO MORE BRICKWALL!

I guess soon you'll find that silcence IS golden - when silence is no more.
:-({|=

---

### Post by Tricity on 2009-12-18
OK, cross-posted again. Never mind. Let's go in small steps. First, let's install the kernel source and the development tools. I usually install those pretty early, so I am not 100% sure if I got them all. But we'll find out.

In a command-line window (shell), enter

$ sudo apt-get install fakeroot kernel-wedge build-essential makedumpfile
$ sudo apt-get build-dep linux
$ sudo apt-get install linux-source

At this time, you should have a new file /usr/src/linux-source-2.6.xx.tar.bz

where xx reflects your kernel version (2.6.31.9-rt, perhaps?) - 
If you do, continue:

$ cd /usr/src
$ sudo bunzip2 linux-source-2.6.xx.tar.bz
$ sudo tar xvf linux-source-2.6.xx.tar

(naturally, you need to type the correct file name with the xx replaced)

At this time, a new directory called linux-source-xx should have been created.
Next, for convenience's sake, allow write access for yourself so you don't need to do sudo all the time:

$ sudo chown -R your_user_name linux-source-2.6.xx

I do not know if the next step is necessary when only one module gets compiled, but it doesn't hurt:

$ cd linux-source-2.6.xx
$ make oldconfig

If you reached this point, find the file that we are interested in:

$ cd sound/pci/emu10k1
$ ls

You should be able to see a file called emumpu401.c - please open this file in your favorite editor. Let me know if you succeeded.

---

### Post by scinram on 2009-12-18
> **Tricity said:**
> First, let's install the kernel source and the development tools. I usually install those pretty early, so I am not 100% sure if I got them all. But we'll find out. In a command-line window (shell), enter

$ sudo apt-get install fakeroot kernel-wedge build-essential makedumpfile
$ sudo apt-get build-dep linux
$ sudo apt-get install linux-source

At this time, you should have a new file /usr/src/linux-source-2.6.xx.tar.bz
where xx reflects your kernel version (2.6.31.9-rt, perhaps?) - If you do, continue:


Done!

New file is: /usr/src/linux-source-2.6.31.tar.bz2

continuing .........

---

### Post by Tricity on 2009-12-18
Some additional musings, perhaps somebody might find this useful. The Audigy 2 ZS with its breakout box is not really straightforward. The MPU-401 output is buffered in a 74F08 chip in the breakout box and routed to the MIDI output port through a 220 ohms resistor and a small inductor that helps suppress transients.

The MIDI input goes into a 6N138 high-speed optoisolator. The output of the optoisolator is then routed to the small piggyback board and enters the RxD input of a Phillips P78LPC762 microcontroller. The TxD serial output then goes through the 74F08 buffer on the main breakout box board and into the 40-pin header at Pin 39. On the Audigy main card, this pin connects directly to the CA0102 at pin 85.

What the microcontroller does with the MIDI signal is anybody's guess. Does it serve as a filter for "unwanted" MIDI commands? Compression of the MIDI data stream? No idea.

But here is one possible explanation for the pulse at GPOUT2 - the signal could reset/initialize the microcontroller. If I just knew the pin layout of the CA0102 chip, I could find out more.

This question is interesting, because if my interpretation is right, it could affect a number of related problems, for example with the SPDIF and optical I/O of the Audigy.

---

### Post by scinram on 2009-12-18
Support sparse irq numbering (SPARSE_IRQ) [N/y/?] (NEW)  --- accepted default!
Support for DMA Remapping Devices (EXPERIMENTAL) (DMAR) [N/y/?] (NEW) ---- accepted default!
Mutex debugging: basic checks (DEBUG_MUTEXES) [N/y/?] (NEW) --- accepted default!
Debug access to per_cpu maps (DEBUG_PER_CPU_MAPS) [N/y/?] (NEW) --- accepted default!

# configuration written to .config

scinram@bntstud:/usr/src/linux-source-2.6.31/sound/pci/emu10k1$ ls
emu10k1.c  emu10k1_main.c   emu10k1_synth.c  emu10k1x.c  emumixer.c   emupcm.c   io.c   Makefile  p16v.c  p17v.h   tina2.h emu10k1_callback.c  emu10k1_patch.c emu10k1_synth_local.h  emufx.c     emumpu401.c  emuproc.c  irq.c  memory.c  p16v.h  timer.c  voice.c

#################

The bricks are tumbling  ... *smile*

---

### Post by Tricity on 2009-12-18
Yep, the bricks are tumbling. Let's proceed to the next step. You should be in the directory /usr/src/linux-source-2.6.31/sound/pci/emu10k1, and you should have the file emumpu401.c open in a text editor (kate? nedit? gedit? Your choice). Go to the very end of the file. Some 20 lines above the last line you should find this code:

[B]int __devinit snd_emu10k1_audigy_midi(struct snd_emu10k1 *emu)
{
        struct snd_emu10k1_midi *midi;
        int err;
[/B] 

Further down, the very last lines of the file are:


        [B]return 0;
}
[/B] 

This defines the initialization function snd_emu10k1_audigy_midi, and the actual code is within those curly brackets. You need to add two things. First, immediately after the int err; you need another variable. Like this:

[B]int __devinit snd_emu10k1_audigy_midi(struct snd_emu10k1 *emu)
{
        struct snd_emu10k1_midi *midi;
        int err;
        unsigned int val;
[/B]
And right before the "return 0" goes my new code that pulses the output:

[B]       snd_printk(KERN_ERR "Audigy MPU-401 UARTs intialized\n");
        val = inl(emu->port + A_IOCFG);
        outl (val | A_IOCFG_GPOUT2, emu->port + A_IOCFG);
        udelay(10);
        outl (val, emu->port + A_IOCFG);
        snd_printk(KERN_ERR "Audigy MPU-401: Tricitys Trick - UART enabled\n");

return 0;
}
[/B]
Note that the two "snd_printk" statements are not absolutely necessary. However, you can later look at /var/log/kern.log and verify that the changes have executed correctly.

Save the file. Now, in this directory type the following commands (make sure that you get the quotes right!):

$ make -C /usr/src/linux-headers-`uname -r` M=`pwd` modules
$ sudo make -C /usr/src/linux-headers-`uname -r` M=`pwd` modules_install
$ sudo depmod -a
$ ls

The last "ls" should show you that a number of new files have been created: a number of files that end with .o, such as emumpu401.o and - most importantly - snd-emu10k1.ko, which is the actual kernel module.

Furthermore, if you do

$ ls /lib/modules/`uname -r`/extra

you should see three new modules: snd-emu10k1.ko  snd-emu10k1-synth.ko  snd-emu10k1x.ko

Almost ready. We need to disable the old module (and at the same time keep it for possible recovery):

$ cd /lib/modules/`uname -r`/kernel/sound/pci/emu10k1/
$ ls

Here, you should see the same modules. Now do

$ sudo mv snd-emu10k1.ko snd-emu10k1.ko.original

Perhaps a

$ sudo depmod -a

would not hurt at this point. You have disabled the old snd-emu10k1 module by renaming it in such a way that it no longer ends in .ko - the kernel won't load it, but by renaming it to its old name, you'd have your computer restored. Instead, the kernel now finds its snd-emu10k1 module in the "extra" directory. Normally, you could load the new module with modprobe, but it is likely that the emu10k1 won't unload because it is in use. Therefore

**reboot.** (*yuck.* This is Windows style)

Once your computer is back up, open a command-line terminal and type 

$ dmesg

Somewhere in the mess, you should see these gems:

[    6.147313] EMU10K1_Audigy 0000:03:06.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    6.153762] Installing spdif_bug patch: SB Audigy 2 [SB0350b]
[    6.177207] Audigy MPU-401 UARTs intialized
[    6.177302] Audigy MPU-401: Tricitys Trick - UART enabled


Try it. Your MIDI-IN should work at this time.

---

### Post by scinram on 2009-12-18
> **Tricity said:**
> Yep, the bricks are tumbling. Let's proceed to the next step. 
<clip>
$ make -C /usr/src/linux-headers-`uname -r` M=`pwd` modules
$ sudo make -C /usr/src/linux-headers-`uname -r` M=`pwd` modules_install
$ sudo depmod -a
$ ls

The last "ls" should show you that a number of new files have been created: a number of files that end with .o, such as emumpu401.o and - most importantly - snd-emu10k1.ko, which is the actual kernel module.

I do not see the kernel module file [snd-emu10k1.ko] ???? I copied and pasted the shell command lines above, so typo can be ruled out???

Here is my output:

scinram@bntstud:/usr/src/linux-source-2.6.31/sound/pci/emu10k1$ ls
emu10k1.c           emu10k1_main.c  emu10k1_patch.c  emu10k1_synth_local.h  emufx.c      emupcm.c   irq.c     memory.c  p16v.h   tina2.h
emu10k1_callback.c  emu10k1_main.o  emu10k1_patch.o  emu10k1_synth.o        emumixer.c   emuproc.c  irq.o     memory.o  p17v.h   voice.c
emu10k1_callback.o  emu10k1.o       emu10k1_synth.c  emu10k1x.c             emumpu401.c  io.c       Makefile  p16v.c    timer.c  voice.o


> 
Furthermore, if you do

$ ls /lib/modules/`uname -r`/extra

you should see three new modules: snd-emu10k1.ko  snd-emu10k1-synth.ko  snd-emu10k1x.ko
'uname -r'/extra is MT!!

scinram@bntstud:/lib/modules/2.6.31-9-rt/extra$ ls
scinram@bntstud:/lib/modules/2.6.31-9-rt/extra$ 


I have halted proceedings at this point ... until we address anomalies above... 

:confused:
SC

---

### Post by Tricity on 2009-12-18
OK, it did not compile. Please repeat this step:

$ make -C /usr/src/linux-headers-`uname -r` M=`pwd` modules

and paste (post) the output.

---

### Post by scinram on 2009-12-18
> **Tricity said:**
> OK, it did not compile. Please repeat this step:

$ make -C /usr/src/linux-headers-`uname -r` M=`pwd` modules

and paste (post) the output.

scinram@bntstud:~$ make -C /usr/src/linux-headers-`uname -r` M=`pwd` modules
make: Entering directory `/usr/src/linux-headers-2.6.31-9-rt'
scripts/Makefile.build:44: /home/scinram/Makefile: No such file or directory
make[1]: *** No rule to make target `/home/scinram/Makefile'.  Stop.
make: *** [_module_/home/scinram] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.31-9-rt'
scinram@bntstud:~$

---

### Post by Tricity on 2009-12-18
Ah. There _was_ one step missing. You need to partly compile the kernel so that the individual makefiles are created. You already accomplished the "make oldconfig", so now cd to the soruce base directory, then start compiling the kernel:

$ cd /usr/src/linux-source-2.6.31
$ make

This will take hours to complete. If you have multiple cores, you can speed it up with make -j 4 (for a quad-core). I am not sure when all files have been generated, so it might be worth letting the make process run through to the end. Then go back to the emu10k1 directory and repeat the make - make - depmod sequence.

---

### Post by scinram on 2009-12-18
> **Tricity said:**
> <clip>This will take hours to complete.<clip>

Its on its way ...:)!!

---

### Post by Tricity on 2009-12-18
Addendum:

> **scinram said:**
> scinram@bntstud:~$ make -C /usr/src/linux-headers-`uname -r` M=`pwd` modules


Why are you in your home directory and not in /usr/src/linux-source-2.6.31/sound/pci/emu10k1 ?

When you type the commands to make the module, you MUST be in that directory, so do

$ cd /usr/src/linux-source-2.6.31/sound/pci/emu10k1

beforehand.

---

### Post by scinram on 2009-12-18
The 'Makefile' is there ..... do i continue or halt the script??

-rw-r--r-- 1 scinram root       516 2009-09-10 08:13 Makefile

---

### Post by scinram on 2009-12-18
> **Tricity said:**
> Addendum:



Why are you in your home directory and not in /usr/src/linux-source-2.6.31/sound/pci/emu10k1 ?

When you type the commands to make the module, you MUST be in that directory, so do

$ cd /usr/src/linux-source-2.6.31/sound/pci/emu10k1

beforehand.


OK ... sorry bout that ... here is tthe output from emu10k1 directory

#######

scinram@bntstud:/usr/src/linux-source-2.6.31/sound/pci/emu10k1$ make -C /usr/src/linux-headers-`uname -r` M=`pwd` modules
make: Entering directory `/usr/src/linux-headers-2.6.31-9-rt'
  CC [M]  /usr/src/linux-source-2.6.31/sound/pci/emu10k1/emumpu401.o
/usr/src/linux-source-2.6.31/sound/pci/emu10k1/emumpu401.c:373:3: error: invalid preprocessing directive #Following
/usr/src/linux-source-2.6.31/sound/pci/emu10k1/emumpu401.c:400:4: error: invalid preprocessing directive #Following
make[1]: *** [/usr/src/linux-source-2.6.31/sound/pci/emu10k1/emumpu401.o] Error 1
make: *** [_module_/usr/src/linux-source-2.6.31/sound/pci/emu10k1] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.31-9-rt'
scinram@bntstud:/usr/src/linux-source-2.6.31/sound/pci/emu10k1$ 

###########

... but the 'make' process is still running ... should i halt it???

---

### Post by Tricity on 2009-12-18
> **scinram said:**
> Its on its way ...:)!!

Good. Just FYI, I took the instructions to compile a single module from here:

[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)

Kernel hacking has its quirks :twisted:

---

### Post by scinram on 2009-12-19
> **Tricity said:**
> <clip>I am not sure when all files have been generated, so it might be worth letting the make process run through to the end. Then go back to the emu10k1 directory and repeat the make - make - depmod sequence.

Will post back when 'make' is made ... will be afk til then. Thanks for your effort Tricity ... it is very much appreciated.

:D
SC

---

### Post by Tricity on 2009-12-19
> **scinram said:**
> Will post back when 'make' is made ... will be afk til then. 

Right. Past midnight here. I'll sign off, too.

A pleasure. Actually, it feels good to have solved a problem that has haunted the forums for about three years. :D

---

### Post by scinram on 2009-12-19
> **scinram said:**
> Will post back when 'make' is made ... will be afk til then. Thanks for your effort Tricity ... it is very much appreciated.

:D
SC


'make' did not seem to make-it through ... this is where it hung;

  ...
  ...
  ...
  ...
  LD      sound/pci/emu10k1/built-in.o
  CC [M]  sound/pci/emu10k1/emu10k1_synth.o
  CC [M]  sound/pci/emu10k1/emu10k1_callback.o
  CC [M]  sound/pci/emu10k1/emu10k1_patch.o
  CC [M]  sound/pci/emu10k1/emu10k1.o
  CC [M]  sound/pci/emu10k1/emu10k1_main.o
  CC [M]  sound/pci/emu10k1/irq.o
  CC [M]  sound/pci/emu10k1/memory.o
  CC [M]  sound/pci/emu10k1/voice.o
  CC [M]  sound/pci/emu10k1/emumpu401.o
sound/pci/emu10k1/emumpu401.c:373:3: error: invalid preprocessing directive #Following
sound/pci/emu10k1/emumpu401.c:400:4: error: invalid preprocessing directive #Following
make[3]: *** [sound/pci/emu10k1/emumpu401.o] Error 1
make[2]: *** [sound/pci/emu10k1] Error 2
make[1]: *** [sound/pci] Error 2
make: *** [sound] Error 2
scinram@bntstud:/usr/src/linux-source-2.6.31$

---

### Post by Tricity on 2009-12-19
So what could be wrong with those two lines? Can you attach your emumpu401.c as a file for me to inspect, please?

(I could give you mine, but that one is still so crammed full with printk and other debugging stuff that I can't circulate it before some serious housekeeping).

I see progress, tough.

---

### Post by scinram on 2009-12-19
> **Tricity said:**
> So what could be wrong with those two lines? Can you attach your emumpu401.c as a file for me to inspect, please?

(I could give you mine, but that one is still so crammed full with printk and other debugging stuff that I can't circulate it before some serious housekeeping).

I see progress, tough.


File  emumpu401.c attached

---

### Post by Tricity on 2009-12-19
Aaargh! :shock:

Don't use # for comments - in C, the # symbol indicates preprocessor instructions.

When you are using C, you may start a comment with //  - this is C++ style, or you enclose a comment with /* and */ (C style)

See my corrections.
After you fixed this, please let's repeat the `make' sequence:

$ cd /usr/src/linux-source-2.6.31/sound/pci/emu10k1/
$ make -C /usr/src/linux-headers-`uname -r` M=`pwd` modules
$ sudo make -C /usr/src/linux-headers-`uname -r` M=`pwd` modules_install
$ sudo depmod -a

And don't forget to rename your /lib/modules/2.6.31-9-rt/kernel/sound/pci/emu10k1/snd-emu10k1.ko to snd-emu10k1.ko.orig

Let's see if we can remove those last few bricks...

---

### Post by Tricity on 2009-12-19
For the record. I finally managed to build a MIDI-to-gameport cable (requires optoisolator!). I was no able to test the gameport MIDI input, too. The patch that I described above enables both MIDI inputs of the Audigy card: Gameport and breakout box.

---

### Post by scinram on 2009-12-19
OK ... back 'on deck' again *smile* ... we have a bit of a time diff i c


> **Tricity said:**
> Aaargh! :shock:

Don't use # for comments - in C, the # symbol indicates preprocessor instructions.

When you are using C, you may start a comment with //  - this is C++ style, or you enclose a comment with /* and */ (C style)

See my corrections.

Are u saying you have edited your patch code and i need to re-edit the emumpu401.c  file?? 
... and then do these steps

> 
$ cd /usr/src/linux-source-2.6.31/sound/pci/emu10k1/
$ make -C /usr/src/linux-headers-`uname -r` M=`pwd` modules
$ sudo make -C /usr/src/linux-headers-`uname -r` M=`pwd` modules_install
$ sudo depmod -aand when should i rename the snd file?? Prior to remaking?

> And don't forget to rename your /lib/modules/2.6.31-9-rt/kernel/sound/pci/emu10k1/snd-emu10k1.ko to snd-emu10k1.ko.origIf you want i can refresh my whole system with a cloned image and start afresh?? It only takes a few minutes ... what do u think?

:idea:
SC

---

### Post by Tricity on 2009-12-19
A time difference like that? You an Aussie?


Grab the file I posted, emumpu401.c.gz - I applied all corrections, and the file should compile (gunzip, of course). So use my file to replace yours in /usr/src/linux-source-2.6.31/sound/pci/emu10k1/

After you did this, the sequence

$ cd /usr/src/linux-source-2.6.31/sound/pci/emu10k1/
$ make -C /usr/src/linux-headers-`uname -r` M=`pwd` modules
$ sudo make -C /usr/src/linux-headers-`uname -r` M=`pwd` modules_install
$ sudo depmod -a                      

should actually work. Again, double-check that the file /lib/modules/2.6.31-9-rt/extra/snd-emu10k1.ko exists, by doing

$ ls -l /lib/modules/2.6.31-9-rt/extra

next you go to

$ cd /lib/modules/2.6.31-9-rt/kernel/sound/pci/emu10k1

and deactivate your old sound module with

$ sudo mv snd-emu10k1.ko snd-emu10k1.ko.orig

No need for a clean install - don't. You lose all your prior work. You are almost done!

Once all steps above are done, reboot. check your kernel message with `dmesg' and look for the "gems" I listed earlier.

---

### Post by scinram on 2009-12-19
> **Tricity said:**
> 
Once all steps above are done, reboot. check your kernel message with `dmesg' and look for the "gems" I listed earlier.

BINGO!!! ..... 

The brick wall is now replaced with a wall of sound. The silence is broken!!

From where i sit this borders on the supernatural ... you are truly a LEGEND TriCity!!

I owe you one .... *big time*

If you ever need support .... just lean!


*big broad smile*

=D>
         SC

---

### Post by Tricity on 2009-12-19
***High five***

Good luck and happy playing. 

It was a pleasure, and thanks for working with me. I have posted this thread at ALSA so they know (1) that there is a solution and (2) the solution has been verified by an independent user.

---

### Post by jzombi on 2009-12-21
Thank you Tricity, I had the same problem, but following your guide I was able to solve it!
Now the solution has been verified by a third user :)

---

### Post by schruthensis on 2011-01-29
I hope I'm not being to rude hijacking this otherwise very warm-fuzzy filled thread with such a downer but I'm a little flummoxed still trying to get-going my somewhat similar set up:

Sound Blaster Live 5.1  
Ubuntu 10.10 
Roland ED PC-180A MIDI Keyboard controller

I'm rather new to MIDI in Linux but figured this thread sounded similar enough to my problem (my external keyboard isn't recognised by Ubuntu)  that I thought I would try the c-code-edit-and-module-recompile solution offered here because it's the only thing close to addressing my situation on the web that I could find. 

I got all the steps to work as advertised here EXCEPT still no recording of midi keystrokes in my sequencer (I'm using Rosegarden)

I think I'm probably going way over-kill here and am probably missing something very simple that I didn't quite catch in one of the more overview level tutorials.

Can any of you guys help me?

---

### Post by schruthensis on 2011-01-30
> **schruthensis said:**
> 

I got all the steps to work as advertised here EXCEPT still no recording of midi keystrokes in my sequencer (I'm using Rosegarden)

I think I'm probably going way over-kill here and am probably missing something very simple that I didn't quite catch in one of the more overview level tutorials.

Can any of you guys help me?

Nevermind!  I got it working.  Just needed to unplug the "break out box" / "daughter board" and the game port input worked!  (Also had some confusion on the midi cable label: evidently your supposed to plug the "IN" cable into the "OUT" keyboard port :) )

Now I just need to figure out how to get more MIDI bank program voices working...  currently I only have about 1 out of every 5 voices available.
Perhaps has something to do with the "sfxload: no memory left" error I'm getting when trying to load my sound fonts.

But this is all aside the point. My keyboard works and I'm happy.  Someday I'll unload Tricity's patch and see if it actually did anything.

---

