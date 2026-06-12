---
title: "Fresh install of Lucid 10.04 + Delta 44 (ICE1712)  = Can't start jackd"
date: 2011-03-18
forum: Ubuntu Studio
---

### Post by earlyjp on 2011-03-18
Greetings! Hoping to get some insight into what to try next to possibly get a new install of Ubuntu Studio 10.04 with a M-Audio Delta 44 up and running. I've been researching/trying stuff for two days, but I've run out of things to try. Here's what I did:

1) Disabled all on-board audio hardware in BIOS

2) Fresh install of ubuntu studio 10.04 from dvd.

3) After first login, Update Manager notified me that there were roughly 300 file updates. I proceeded to install these.

4) Confirmed that my user id is a member of the audio group.

5) Attempted to install the pulseaudio ICE1712 workaround as described here [http://www.nbl.fi/~nbl4321/?p=491]("http://www.nbl.fi/%7Enbl4321/?p=491")

6) Tried to launch jackd, but it dies after 10-20 seconds. The behavior is the same from the command line and qjackctl. The output from qjackctl is as follows:

[COLOR=Black]22:23:49.549 Patchbay deactivated.
[/COLOR]  [COLOR=Black]22:23:49.581 Statistics reset.
[/COLOR]  [COLOR=Black]22:23:49.604 ALSA connection graph change.
[/COLOR]  [COLOR=Black]22:23:49.801 ALSA connection change.
[/COLOR]  [COLOR=Black]22:24:16.778 Startup script...
[/COLOR]  [COLOR=Black]22:24:16.779 artsshell -q terminate
 sh: artsshell: not found
[/COLOR]  [COLOR=Black]22:24:17.183 Startup script terminated with exit status=32512.
[/COLOR]  [COLOR=Black]22:24:17.183 JACK is starting...
[/COLOR]  [COLOR=Black]22:24:17.183 /usr/bin/jackd -p128 -t5000 -dalsa -r48000 -p128 -n2 -D -Chw:0,0 -Phw:0,0
[/COLOR]  [COLOR=Black]22:24:17.187 JACK was started with PID=3055.
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 Memory locking is unlimited - this is dangerous. You should probably alter the line:
      @audio   -  memlock    unlimited
 in your /etc/limits.conf to read:
      @audio   -  memlock    2849811
 no message buffer overruns
 JACK compiled with System V SHM support.
 loading driver ..
 Enhanced3DNow! detected
 SSE2 detected
 apparent rate = 48000
 creating alsa driver ... hw:0,0|hw:0,0|128|2|48000|0|0|nomon|swmeter|-|32bit
 control device hw:0
[/COLOR]  [COLOR=Black]22:24:17.276 Server configuration saved to "/home/earlyjp/.jackdrc".
[/COLOR]  [COLOR=Black]22:24:17.276 Statistics reset.
[/COLOR]  [COLOR=Black]22:24:17.300 Client activated.
[/COLOR]  [COLOR=Black]22:24:17.302 JACK connection graph change.
 Enhanced3DNow! detected
 SSE2 detected
 configuring for 48000Hz, period = 128 frames (2.7 ms), buffer = 2 periods
 ALSA: final selected sample format for capture: 32bit integer little-endian
 ALSA: use 2 periods for capture
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: use 2 periods for playback
[/COLOR]  [COLOR=Black]22:24:17.673 Buffer size change (128).
[/COLOR]  [COLOR=Black]22:24:17.674 JACK connection graph change.
[/COLOR]  [COLOR=Black]22:24:17.703 JACK connection change.
 ALSA: poll time out, polled for 3999069 usecs
 DRIVER NT: could not run driver cycle
[/COLOR]  [COLOR=Black]22:24:21.675 JACK connection graph change.
 jack main caught signal 12
[/COLOR]  [COLOR=Black]22:24:21.697 Shutdown notification.
[/COLOR]  [COLOR=Black]22:24:21.699 JACK is stopping...
[/COLOR]  [COLOR=Black]22:24:21.708 JACK is being forced...
 cannot continue execution of the processing graph (Broken pipe)
 zombified - calling shutdown handler
[/COLOR]  [COLOR=Black]22:24:21.908 JACK was stopped successfully.
[/COLOR]  [COLOR=Black]22:24:21.908 Post-shutdown script...
[/COLOR]  [COLOR=Black]22:24:21.908 killall jackd
 jackd: no process found
[/COLOR]  [COLOR=Black]22:24:22.318 Post-shutdown script terminated with exit status=256.
[/COLOR] 

Here is the output of some other commands that may be of interest:

$ uname -a
Linux ubuntuStudio 2.6.32-30-preempt #59-Ubuntu SMP PREEMPT Wed Mar 2 00:02:01 UTC 2011 x86_64 GNU/Linux

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: M44 [M Audio Delta 44], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

$ lspci | grep -i ice1712
03:06.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)

$ lsmod | grep -i ice1712
snd_ice1712            65411  1 
snd_ice17xx_ak4xxx      3155  1 snd_ice1712
snd_ak4xxx_adda         8572  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427              7978  1 snd_ice1712
snd_ac97_codec        125298  1 snd_ice1712
snd_pcm                86589  4 snd_ice1712,snd_ac97_codec,snd_pcm_oss
snd_i2c                 5582  2 snd_ice1712,snd_cs8427
snd_mpu401_uart         6889  1 snd_ice1712
snd                    71936  17 snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_i2c,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device


Some more details:

1) I can start envy24 Control, and all the channels seem to be there, but I cannot change any parameters. Everything is stuck on S/PDIF.

2) I can start alsamixer, and I can change levels, but I cannot tell if it is effective.

3) I used this (ICE1712) card with previous versions of ubuntu studio. I just assembled a new system specifically as a DAW, and I'm trying to use this interface.

I would greatly appreciate any insight into testing or correcting this configuration.

Thanks,
~Jim

---

### Post by sgx on 2011-03-18
Hi, what computer, video card, and motherboard chipset?

I assume you have a separate /home partition, it is almost mandatory to
preserve a linux users sanity, with a large distro. I would try
Ubuntu Studio 8.04, and create and use that extra partition in the process.

You can uninstall all the  pulse audio things, and if you have both a separate video card, and a motherboard video, pull the fancy one out.
Turning off any webcam, networking, and other goodies might help.

Also run your 10.04 in a live session, and compare the command outputs,
and success at starting jackd. Have you tried the basic command

jackd -d alsa -r 44100 from a fresh boot, and then start qjackctl?

have you tried any tests as sudo root user?

Input Device  >
Output Device  >

does it show up when you click the  > widgets?

Cheers

---

### Post by ailo.at on 2011-03-19
Yes, I would remove the PA workaround too.
jackd will work without the workaround.

Make sure PA is not using the card when you try using jackd to be sure.

Once you are sure jackd is working, this PA workaround should work. [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/30](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/30)

I never use the workarounds myself anymore, but I use two m-audio delta cards in sync without problems.

---

### Post by earlyjp on 2011-03-19
> **sgx said:**
> Hi, what computer, video card, and motherboard chipset?

I assume you have a separate /home partition, it is almost mandatory to
preserve a linux users sanity, with a large distro. I would try
Ubuntu Studio 8.04, and create and use that extra partition in the process.

You can uninstall all the  pulse audio things, and if you have both a separate video card, and a motherboard video, pull the fancy one out.
Turning off any webcam, networking, and other goodies might help.

Also run your 10.04 in a live session, and compare the command outputs,
and success at starting jackd. Have you tried the basic command

jackd -d alsa -r 44100 from a fresh boot, and then start qjackctl?

have you tried any tests as sudo root user?

Input Device  >
Output Device  >

does it show up when you click the  > widgets?

Cheers

Hello! Thanks for the prompt response. I'll answer your questions below.

Computer: This system uses an Asus M4A785-M MB and an AMD Athlon II X4 (640 Propus) 3GHz Quad core CPU with 4GB of RAM. I have disabled all on-board audio devices (there are two), and I'm using the on-board video (Radeon) and Ethernet port. My Delta 44 is the only PCI card in use.

I have only one USB device, and that is the Midiman MidiSport 2x2. I've had no problems with getting that to load.

The only drive is a Kingston SSDNow V-series 30GB. I did not create a separate /home partition -- just one / and swap. I did this to simplify the process, but I can certainly redo this when I try 8.04.

I have tried the basic jackd (as user and sudo) from the command line as above. It also dies after 10-20 seconds, but its error is less instructive than from qjackctl (that's why I posted the qjackctl output).

Also, things are showing up when I press the > widgets. hw:0 shows up as "M-audio Delta 44", and hw0:0 shows "ICE1712". Trying either produces the same results.

I think I will try using 8.04, as you suggest. There appears to have also been some success in the past with 9.04, but that link is broken on the Ubuntu Studio downloads page.

I'll report back in a few hours with my findings.

Thanks again for your help!

~Jim

---

### Post by earlyjp on 2011-03-19
> **ailo.at said:**
> Yes, I would remove the PA workaround too.
jackd will work without the workaround.

Make sure PA is not using the card when you try using jackd to be sure.

Once you are sure jackd is working, this PA workaround should work. [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/30](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/30)

I never use the workarounds myself anymore, but I use two m-audio delta cards in sync without problems.

Hello, and thank you for the prompt reply!

I'm certain that PA is the problem, but I'm not quite sure how to disable it without breaking other things.

At one point in the process, I used apt to first install xfdesktop4, then remove all the pulseaudio packages. Unfortunately, I still could not get jackd to start.

I have seen the bug report you mention. I remember trying that particular suggestion, but sadly it did not work. There are later comments (#53, I think) to this bug that specifically mention the PA workaround that I last tried.

As noted above, I will next try 8.04 and report any differences that I see.

Thanks,
~Jim

---

### Post by ailo.at on 2011-03-19
> **earlyjp said:**
> Hello, and thank you for the prompt reply!

I'm certain that PA is the problem, but I'm not quite sure how to disable it without breaking other things.


I don't think PA is causing the problems you have running jack, unless PA is occupying the card for something. I'm talking from memory, but I seem to remember on Lucid qjackctl suspends PA, while jackd does not. 
If you have a built in card, try setting that as the default card for PA. This way we can be sure PA is not in the way.
You should be able to run jackd simultaniously with PA even, if you run jackd from the terminal, and PA is using another card then jack.

I would focus on getting jack working, which really should not be too much of a problem.

> 
At one point in the process, I used apt to first install xfdesktop4, then remove all the pulseaudio packages. Unfortunately, I still could not get jackd to start.

I have seen the bug report you mention. I remember trying that particular suggestion, but sadly it did not work. There are later comments (#53, I think) to this bug that specifically mention the PA workaround that I last tried.

As noted above, I will next try 8.04 and report any differences that I see.

Thanks,
~Jim

If you read at the bottom of that bug report you'll find that #30 was used as late as on Ubuntu Natty.
Still, that is just a workaround for PA, not jackd.
I find it strange that you are not getting jackd working, which should be no problem with a fresh install of any Ubuntu, given you have realtime privilege.
However, running jack as sudo should already work.

btw, Ubuntu Studio Controls is not editing the right file, so don't use that.
Installing jackd will add a file in /etc/security/limits.d/audio.conf which gives realtime prio to @audio group. Ubuntustudio controls will edit the file /etc/security/limits.conf, which is not the file to be used anymore.

---

### Post by earlyjp on 2011-03-19
Well, I'm sorry to report that the situation has gone from bad to worse. As suggested, I tried doing a fresh install of ubuntu studio 8.04. That went smoothly enough. I did create another partition for /home, too.

Following my first login, I was advised of roughly 100 updates, so I let Update Manager take care of those. I do believe that one of the updates was for kernel 2.6.24-28-rt, adding to 2.6.24.19-rt that was part of the initial installation.

The updates required a restart, so I did that. Following this, I got the Ubuntu Studio splash screen for a few seconds (in white and blue). It then flashed to some other colors and went black. Ctrl-Alt-F1 and Ctrl-Alt-Del have no effect.

I've tried booting into recovery mode and using xfix. I've done this with both kernels and am having no success. So, right now I'm investigating how to get the on-board video for the Asus M4A785-M to speak ubuntu. Obviously, I have to get this working before I can pursue the jackd issue.

---

### Post by earlyjp on 2011-03-19
Really having a hard time with this. Now, I cannot seem to get any distribution to boot completely. My most recent test involved an Xubuntu 10.10 live cd, just trying to see if I can get anything to load X completely. This disk worked fine a few days ago. With this disk, I can get to the boot menu and select "Try Xubuntu without installing...". After that the small Xubuntu logo appears for a few seconds while files are loaded from the CD, then just a unresponsive black screen -- just like everything else I've tried. I just tried resetting the BIOS to its default values and reloading, but this too has failed.

I'm not sure what could have happened that would cause these video problems. Ever since the ubuntu studio 8.04 update, nothing has worked. Any thoughts?

Thanks,
~Jim

---

### Post by earlyjp on 2011-03-19
OK, some progress! I was able to correct the problem with X by adding a video mode (vga=323) to the boot line. At least now I can boot ubuntu studio 8.04 and log in.

Here's the update on the jackd issue. I am now getting an "already in use" message from both jackd (command line) and qjackctl.

```

$ jackd -dalsa -r44100
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns

$ cat /proc/asound/cards 
 0 [M44            ]: ICE1712 - M Audio Delta 44
                      M Audio Delta 44 at 0xec00, irq 21

earlyjp@ubuntuStudio:~$ cat /proc/interrupts 
           CPU0       CPU1       CPU2       CPU3       
  0:        264          0          0          8   IO-APIC-edge      timer
  1:          0          0          6       1645   IO-APIC-edge      i8042
  4:          0          0          0          2   IO-APIC-edge    
  7:          0          0          0          0   IO-APIC-edge      parport0
  8:          0          0          1          0   IO-APIC-edge      rtc
  9:          0          0          0          1   IO-APIC-fasteoi   acpi
 12:          0          0          0          4   IO-APIC-edge      i8042
 14:          0          0          0          0   IO-APIC-edge      libata
 15:          0          0          0          0   IO-APIC-edge      libata
 16:          0          0         66      13984   IO-APIC-fasteoi   ohci_hcd:usb1, ohci_hcd:usb2
 17:          0          0          0          2   IO-APIC-fasteoi   ehci_hcd:usb5
 18:          0          0          0          3   IO-APIC-fasteoi   ohci_hcd:usb3, ohci_hcd:usb4, ohci_hcd:usb7
 19:          0          0          0          0   IO-APIC-fasteoi   ehci_hcd:usb6
 21:          0          0          0          0   IO-APIC-fasteoi   ICE1712
 22:          0          0        178      32822   IO-APIC-fasteoi   ahci
510:          0          0         48       6906   PCI-MSI-edge      eth0
NMI:          0          0          0          0   Non-maskable interrupts
LOC:    2378174    2377089    2376559    2375872   Local timer interrupts
RES:      37534      22246       8811       7153   Rescheduling interrupts
CAL:        176        198        239        212   function call interrupts
TLB:       1120       1563       1441       1082   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
SPU:          0          0          0          0   Spurious interrupts
ERR:          0

$ aplay -L
default:CARD=M44
    M Audio Delta 44, ICE1712 multi
    Default Audio Device
front:CARD=M44,DEV=0
    M Audio Delta 44, ICE1712 multi
    Front speakers
surround40:CARD=M44,DEV=0
    M Audio Delta 44, ICE1712 multi
    4.0 Surround output to Front and Rear speakers
surround41:CARD=M44,DEV=0
    M Audio Delta 44, ICE1712 multi
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=M44,DEV=0
    M Audio Delta 44, ICE1712 multi
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=M44,DEV=0
    M Audio Delta 44, ICE1712 multi
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=M44,DEV=0
    M Audio Delta 44, ICE1712 multi
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

$ lsof | grep -i alsa
gnome-set  5804    earlyjp  mem       REG                8,1    99712  60210 /usr/lib/gstreamer-0.10/libgstalsa.so


```I did this immediately after logging in (no apps opened). Am I correct that gstreamer has a hold on the interface? If so, how can I get it to release the interface, at least until jackd can be started?

Thanks!
~Jim

---

### Post by sgx on 2011-03-19
Hi, I did not think about 8.04 asking for updates, I suggested it
because it usually works out of the box. Updates on older versions
often break things. I would reinstall, and test without the updates.

Sorry for the inconvenience! If memory serves, pulse audio was either not part of 8.04, or not active by default, which is another reason I suggested 8.04.

I have tested installs by installing on a usbstick, so removing
or modiying things like pulse can be done without risk beyong the time involved.

Cheers

---

### Post by sgx on 2011-03-19
> **earlyjp said:**
> Really having a hard time with this. Now, I cannot seem to get any distribution to boot completely. My most recent test involved an Xubuntu 10.10 live cd, just trying to see if I can get anything to load X completely. This disk worked fine a few days ago. With this disk, I can get to the boot menu and select "Try Xubuntu without installing...". After that the small Xubuntu logo appears for a few seconds while files are loaded from the CD, then just a unresponsive black screen -- just like everything else I've tried. I just tried resetting the BIOS to its default values and reloading, but this too has failed.

I'm not sure what could have happened that would cause these video problems. Ever since the ubuntu studio 8.04 update, nothing has worked. Any thoughts?

Thanks,
~Jim
'bios defaults' is a last-resort, and misleading, and is bad luck in general. I would go into the bios, (take notes as you go  if this is new) it is navigated
by arrow keys, and the escape key (use the tab key (or space bar) to change a value and press the enter key to make the changes) Find your video config area, and make sensible changes.

Cheers

---

### Post by sgx on 2011-03-19
Your bios defaults may have adjusted (nuked) the boot process
to reach your SSD drive, so look for options like 'drive order'
or 'boot priority' or some such, that allow you to specify the
drives that boot first second, or third. If possible,
cd/dvd and usb/firewire devices should be ahead of all drives.
This is sometimes shipped this way, but may not be the 'bios default'.
Cheers

---

### Post by earlyjp on 2011-03-20
Thanks sgx and allo.at for your help. I restored the BIOS settings for audio and boot order after adding the video boot option mentioned in a previous post, so at least now I can boot and login to my system.

I've done a few things since my last post. I found that I could correct the "already in use" issue by doing a 'alsa force-reload'. That enables me to start jackd but it continues to die after ~34 seconds with an "Alsa timeout" message.

So, to recap, I've now tried to use the Delta 44 in ubuntu studio 10.10, 10.04, and 8.04 -- all of which failed. I happily used this same card in ubuntu studio a few years ago, and recently decided to build my new system specifically to get back into recording. Sadly, it appears that something (perhaps, the introduction of pulseaudio) has thwarted this idea.

I've got to get back to other projects, so I'm going to have to put this away for a while. In the meantime,  I would be be glad to hear any suggestions for what to try next. Should I wait to see if ice1712 issues are resolved, or try another distro?

Thanks,
~Jim

---

### Post by cchhrriiss121212 on 2011-03-20
I'd recommend AVLinux if you want to try another distro.

---

### Post by sgx on 2011-03-20
I have a pclinuxos setup that has an m-audio 24/96 pci,
no problems. There are versions for gnome, kde, E17,
Openbox, LXDE, etc, and small mini-me versions. Wine
and Reaper work great in these.

[http://pclinuxoshelp.com/index.php/Download_PCLinuxOS_ISO%27s](http://pclinuxoshelp.com/index.php/Download_PCLinuxOS_ISO%27s)

Cheers

---

### Post by ailo.at on 2011-03-20
> 
I've done a few things since my last post. I found that I could correct the "already in use" issue by doing a 'alsa force-reload'. That enables me to start jackd but it continues to die after ~34 seconds with an "Alsa timeout" message.
If it's already in use, something is occupying the card. If you have pulseaudio installed it could be that. Just having a browser open with a paused flashplayer movie can do that.
It's been a while since I used 8.04, so I don't know what would happend after updating it.
Suspending pulseaudio while running jackd can be done using this command: pasuspender -- jackd -d alsa -d hw:1 # my card of choice happened to be hw:1)

> 
So, to recap, I've now tried to use the Delta 44 in ubuntu studio 10.10, 10.04, and 8.04 -- all of which failed. I happily used this same card in ubuntu studio a few years ago, and recently decided to build my new system specifically to get back into recording. Sadly, it appears that something (perhaps, the introduction of pulseaudio) has thwarted this idea.
I'm sorry to hear about your difficulties. Still, having the same chipset myself, I can clearly state that neither system have presented me with problems that I weren't able to solve in a few steps. Of, course, knowing those steps can be another matter.
As for jackd, it works out of the box. PA just needs a workaround.

> 
Should I wait to see if ice1712 issues are resolved, or try another distro?

Thanks,
~JimI haven't seen anything suggesting that someone was working on the problem with Alsa / Pulseaudio and cards using ice1712. This problem has existed for a few years now.
The problem is that Alsa is not providing the inputs and outputs that PA is asking for. 
But, the workaround I posted before should take care of that.

However, if you would like to try another distro that doesn't include PA by default, I guess any Ubuntu derived audio based distro would do.
One of my favorites is Puredyne. Based on Karmic and uses the -rt kernel from Karmic's repo. XFCE desktop. Had a problem using it on one laptop, because of the screen.
If deciding to try stick with Ubuntu Studio, I would recommend 10.04.
There is also Tango Studio and KXStudio.
AVLinux has been recommended before, which is based on Debian and uses the Liquorix Realtime Kernel

---

### Post by Sylos on 2011-03-21
Hello.
OP.....
I may be barking up the wrong tree here but if PA is possibly the source of the woes then couldnt you try removing it totally using something like:

```
sudo apt-get remove pulseaudio gstreamer0.10-pulseaudio
```

This will take it out (and some other packages from memory) and leave you with no PA to get in the way. I have an M-Audio Delta 66 (basically the same as the 44) which uses the ICE1712 chipset and I did just that when I installed - purged the little blighter from my system from the start. It means you wont have sound from things like Totem but I just installed Aqualung (a nice jack aware player) for listening to music and got on with it (I use a seperate vanilla ubuntu for normal use).

Also, what about removing the M-Audio car and installing 10.04 with just the onboard and trying to get it to work from there. Then once you have confirmed you can get Jack to play ball using the onboard (urgh!) you could try adding the 44 and adjusting things as required. Not sure if it will be much different but it might be worth a shot

---

