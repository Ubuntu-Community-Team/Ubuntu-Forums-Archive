---
title: "Getting Ardour to Record?"
date: 2011-05-20
forum: Ubuntu Studio
---

### Post by bloodshot13 on 2011-05-20
Hello everyone. I just did a fresh install of Ubuntustudio and I can't get Ardour to record with my Shure sm58mic using a lightsnake([http://www.soundtech.com/products/home-recording/stusbxlr10/](http://www.soundtech.com/products/home-recording/stusbxlr10/)). It is a xlr to usb cable. To give you some background, I was running Ubuntu 10.10 before with a generic kernel and when I plugged the mic and cable to my usb port it was able to record into Ardour(but no sound from playback). I found that if I started qjackctl,first, I could here what I recorded, but was not able to record. I had to run just Ardour(first) to record and then close and start jack and then ardour to hear what was recorded. I'm a newb at this so please don't roll your eyes too much :D. I've been reading alot about rt-kernel and realtime kernel and low-lantency kernels, so I figured I would just make this computer mainly for recording(music and whatnot). So, I completely wiped out Ubuntu 10.10 and installed Ubuntustudio 11.04 w/ the low-lantency kernel from Alessio's site([https://launchpad.net/~abogani/+archive/ppa?field.series_filter=natty]("https://launchpad.net/%7Eabogani/+archive/ppa?field.series_filter=natty")). The trouble I'm having now is I'm not able to get my mic to work at all now. I'm sure it's something easy I'm missing. I'm very new to this, so please layman's terms:). Thanks for any help. Also, it's not showing my mic on my usb port. I'm not sure if it showed it before when I was running 10.10.

---

### Post by Pablo_F on 2011-05-20
Hi,

Please, show the output of the following informative commands:

cat /proc/asound/cards
arecord -l && aplay -l


Then we will try to help on qjackctl setup. (You can make ardour start the jack server also, but we will see).

To show text output, don't attach images, just paste the text here, preferably using code tags. Use the mouse or [Control-Shift-C] to copy text from the terminal.

Cheers, Pablo

---

### Post by bloodshot13 on 2011-05-20
Thanks Pablo,
0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfcff8000 irq 16
 1 [U0x19400xac02  ]: USB-Audio - USB Device 0x1940:0xac02
                      USB Device 0x1940:0xac02 at usb-0000:00:13.0-2, full speed
 2 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe67c000 irq 19

**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: U0x19400xac02 [USB Device 0x1940:0xac02], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: U0x19400xac02 [USB Device 0x1940:0xac02], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Pablo_F on 2011-05-20
Hi, 

I suppose that 

1 [U0x19400xac02 ]: USB-Audio - USB Device 0x1940:0xac02
USB Device 0x1940:0xac02 at usb-0000:00:13.0-2, full speed

which also appears in lsusb (without a description though) is the STUSBXLR10.

In qjackctl:

Interface: (default)
Mode: Duplex 
Input device: hw:U0x19400xac02 (it is better if you write this down, rather than choosing the numeric ID of the card from the drop down menu, because numbers can change in different reboots, but not names)
Output device: hw:SB

For the rest, leave the default settings by the time being.

This way, Jack will use the STUSBXLR10 for capture and the onboard audio card for playback.

Start the server (big Start button). If there are problems, post the content of the message window of qjackctl. If jackd starts, launch ardour and try recording. Make sure that the "system capture" is connected to the ardour audio track input (quick check via Connections button of qjackctl).

Cheers, Pablo

---

### Post by bloodshot13 on 2011-05-20
Pablo, you are da' man! (If you're a woman,then just substitute). Ubuntu community rocks! Thanks! Now to try and have some fun.:D Edit: Well I started to record and now I'm getting xruns about every 15sec. I thought the low-latency kernel would take care of any x-runs. I guess I'll try and find a solution for this now.

---

### Post by Pablo_F on 2011-05-21
Cool. 

Try disabling the wifi card (via hardware switch).

---

### Post by bloodshot13 on 2011-05-21
I don't have a wifi card. This is a desktop that uses ethernet. I'm not having any luck now. I can't get rid of the x-runs and now it's not working properly at all. I've messed around with qjackctl settings. I've changed the frame/period setting from 16 to 512,everthing in between. I've checked/unchecked realtime,H/w monitor, force 16 bit,monitor. Changed sample rates from 48000 to 44100. I've also tried moving my mic to my USB3 port. Some of the settings record but either ardour crashes or Jack won't work at all. I checked to make sure I'm in the "Audio group", but I'm at a loss. The beginning setting were recording but, like I said, it would have x-runs every 15sec. or so. I also read to change server path from /usr/bin/jackd to /usr/bin/jack -S. Anything I can do/try to get this working properly? Thanks for any help.

---

### Post by bloodshot13 on 2011-05-21
These are my settings now. Records and plays fine but getting the xruns. Am I running at low-latency? 23.2msec doesn't sound like low-latency.

---

### Post by jejeman on 2011-05-21
For usb cards use 3 periods.

---

### Post by cchhrriiss121212 on 2011-05-21
In qjackctl, select the USB device as the interface instead of "default", then leave the input/output selections as "default". 

You can check if you are using the low latency kernel by typing uname -a in a terminal. If not, you need to select your kernel when you boot, hold shift to get the GRUB menu.

---

### Post by bloodshot13 on 2011-05-21
> **jejeman said:**
> For usb cards use 3 periods.
  Thanks jejeman. I did that and I'm still getting xruns about every 20sec. now. Does it matter if I have it in usb 2.0 or 3.0? Will it record just the same? Shouldn't I be able to record @ 48khz? I know this is a trial and error type of thing. I've also changed my memory to 1600hz w/ 9-9-9-24 timing per specs, even though on the gskill web site to set it at 1333hz 8-8-8-24. Just trying different things. Thanks for the help. If I can set it and forget it that is my goal:D.

---

### Post by bloodshot13 on 2011-05-21
]In qjackctl, select the USB device as the interface instead of "default", then leave the input/output selections as "default". 

You can check if you are using the low latency kernel by typing uname -a in a terminal. If not, you need to select your kernel when you boot, hold shift to get the GRUB menu.[/QUOTE]
  Thanks. I changed the interface to hw:2(usb device 0x1940:0xac02). I'm running Linux ubuntu 2.6.38-8-lowlatency #42~ppa2-Ubuntu SMP PREEMPT Mon Apr 11 07:01:53 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
I'm still getting xruns.

---

### Post by bloodshot13 on 2011-05-21
Well I've been messing around,reading and things seem to get worse and worse.I'm trying to get rid of the xruns and I'm getting other problems. Now I can't get the mic to record again. I've changed qjackctl to suggestion(and different forums suggestions) and it isn't working anymore. The lightsnake cable is blinking(suppose to show actively recording) when it is connected to jack. When I try and record into ardour there is no more activity(track meter not responding). With this new setting(image) I'm getting x-runs like crazy, even without sound recording. My processor is not overclocked. Do you think it needs to be, to work correctly? I've read some about scaling. Do I need to set to performance? If so, how? Any good reading that would be helpful? I'm gonna get this down if it kills me;). I'm all about music and really want to record. Thanks for any help.

---

### Post by sgx on 2011-05-21
Try a simple way, reboot

jackd -d alsa -r 44100

then start qjackctl.

Use timemachine to record

[http://packages.debian.org/sid/timemachine](http://packages.debian.org/sid/timemachine)

install with

sudo dpkg -i timemachine_0.3.3-1_i386.deb

plug in the lightsnaked mic, find it in qjackctl, and connect to timemachine, and press the record button.


about xruns, if they are inaudible, ignore them.

[http://ubuntuguide.net/view-and-kill-current-processes-on-ubuntu](http://ubuntuguide.net/view-and-kill-current-processes-on-ubuntu)

this will show how to kill things that may be making xruns happy.
Google the processes that are using the most cpu/ram to see what they do. Verify if you need them. The command

ps ux   will list processes, revealing memory/cpu hogs, among other things, linux system apps are pretty trivial in usage, and best left to run. But cpufreq-xxx are for laptop battery life, and should not be
running in a music system. Take time and read thru the contents of
bin sbin usr/bin usr/sbin every week or so, for good luck.

Cheers

---

### Post by Pablo_F on 2011-05-22
Starting jackd from the command line is a good tip to diagnose problems but the command suggested by sgx won't do it because you need to **tell jack to use the STUSBXLR10** to record. 

As I suggested in a previous post, you can use the card number, which can be hw:0, hw:1 or hw:2, depending on the way the wind might blow. However, it is much better (not to avoid xruns but to avoid confusion) that you use the card names. You have 3 different audio interfaces:

[SB ]: HDA-Intel - HDA ATI SB
[U0x19400xac02 ]: USB-Audio - USB Device 0x1940:0xac02
[NVidia ]: HDA-Intel - HDA NVidia

The name is between the square brackets. So, the complete name of the audio interface is hw:U0x19400xac02. (According to aplay -l, it has a capture device, hw:U0x19400xac02,0 but you don't need to specify further, as it is "0" and the only one). 

I suggest you try in the command line like this:

**jackd -S -d alsa -dhw:U0x19400xac02 -C**

-S option will tell jack to use the synchronous mode, which is usually better for jack2 (as always, YMMV). -C option is for "only capture" mode, just trying to narrow down the sources of the problem.

Then launch ardour and record. 

Let's start here.

Are there xruns?

Also, please, give the output of:

cat /proc/interrupts


> I've read some about scaling. Do I need to set to performance? If so, how? 

Yes, try setting CPU freq scaling to performance. If you are in gnome2 (ubuntu classic) you can add an applet to the panel, CPU freq monitor or similar. Choose the CPU and set it to performance. You probably need to add as many applets as CPU's you have. There are other ways to do it, but this is the easiest for beginners, at least in gnome2. 
> 
Any good reading that would be helpful?

jackaudio.org
linuxmusicians.com (wiki and forums)

In any case, each system is different and there is not a universal set up. Don't try to get a very low latency with a USB interface. In addition, more latency means more stability, and very low latency is not always good. It depends on the user case.

---

### Post by bloodshot13 on 2011-05-22
Thanks for the replies Sgx and Pablo.

> As I suggested in a previous post, you can use the card number, which can be hw:0, hw:1 or hw:2, 
I have been checking this device for capture when I run jack for input device and interface(as suggested by [cchhrriiss121212]("http://ubuntuforums.org/member.php?u=948514")) 

> 
I suggest you try in the command line like this:

**jackd -S -d alsa -dhw:U0x19400xac02 -C**I did this and ardour is recording(with no x-runs:D), but not able to hear the recording.

> 
Also, please, give the output of:

cat /proc/interrupts         CPU0       CPU1       CPU2       CPU3       
  0:        413        159       2788    4092649   IO-APIC-edge      timer
  1:          0          0          0          4   IO-APIC-edge      i8042
  7:          1          0          0          0   IO-APIC-edge    
  8:          0          0          0          1   IO-APIC-edge      rtc0
  9:          0          0          0          2   IO-APIC-fasteoi   acpi
 12:          0          0          1          5   IO-APIC-edge      i8042
 14:          0          0          0          0   IO-APIC-edge      pata_atiixp
 15:          0          0          0          0   IO-APIC-edge      pata_atiixp
 16:        752          0         28        680   IO-APIC-fasteoi   hda_intel
 17:          0          0          0          4   IO-APIC-fasteoi   ehci_hcd:usb1, ehci_hcd:usb2, ehci_hcd:usb3
 18:    1307494        407          5       5506   IO-APIC-fasteoi   ohci_hcd:usb4, ohci_hcd:usb5, ohci_hcd:usb6, ohci_hcd:usb7, ahci, nvidia
 19:        118          0         48        376   IO-APIC-fasteoi   pata_jmicron, hda_intel
 22:          0          0         39         21   IO-APIC-fasteoi   firewire_ohci
 40:          0          0          0          0   PCI-MSI-edge      PCIe PME
 41:          0          0          0          0   PCI-MSI-edge      PCIe PME
 42:          0          0          0          0   PCI-MSI-edge      PCIe PME
 43:          0          0          0          0   PCI-MSI-edge      PCIe PME
 44:      14468          0          4         72   PCI-MSI-edge      eth0
 45:      37331          0        114       3729   PCI-MSI-edge      ahci
 46:          0          0          0          1   PCI-MSI-edge      xhci_hcd
 47:          0          0          0          0   PCI-MSI-edge      xhci_hcd
 48:          0          0          0          0   PCI-MSI-edge      xhci_hcd
 49:          0          0          0          0   PCI-MSI-edge      xhci_hcd
 50:          0          0          0          0   PCI-MSI-edge      xhci_hcd
NMI:          0          0          0          0   Non-maskable interrupts
LOC:    3795396    3792527    3787015      30368   Local timer interrupts
SPU:          0          0          0          0   Spurious interrupts
PMI:          0          0          0          0   Performance monitoring interrupts
IWI:          0          0          0          0   IRQ work interrupts
RES:     431532     445857      82055      54457   Rescheduling interrupts
CAL:        692        751        901        715   Function call interrupts
TLB:       1909       2579       2757       1878   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
MCE:          0          0          0          0   Machine check exceptions
MCP:         13         13         13         13   Machine check polls
ERR:          1
MIS:          0




I've also ran memtest 86 v4.0 on my memory and I get block test errors on one of my modules. I don't know if this has anything to do with the x-runs(Sgx-yes the x-runs do cause audible pops). I am rmaing the module. 

> Use timemachine to record I will try this. Thanks for the suggestion sgx.

---

### Post by bloodshot13 on 2011-05-22
That output looks kinda weird. This looks better.

---

### Post by Pablo_F on 2011-05-22
> jackd -S -d alsa -dhw:U0x19400xac02 -C

I did this and ardour is recording(with no x-runs), but not able to hear the recording.

So far so good. -C means "capture only mode" so there were no jack playback ports that ardour could use. Now, try using the two audio cards, the onboard for output:

**jackd -S -d alsa -D -Chw:U0x19400xac02 -Phw:SB**

How is it?

Cheers, Pablo

---

### Post by bloodshot13 on 2011-05-22
jackd -S -d alsa -D -Chw:U0x19400xac02 -Phw:SB
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio2
Acquire audio card Audio0
creating alsa driver ... hw:SB|hw:U0x19400xac02|1024|2|48000|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xfcff8000 irq 16
the playback device "hw:SB" is already in use. Please stop the application using it and run JACK again
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server

   This was the second and third time I tried this in terminal. The first time I tried it, it worked, but was showing x-runs, before I opened Ardour. What now?


jackd -S -d alsa -D -Chw:U0x19400xac02 -Phw:SB
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio2
Acquire audio card Audio0
creating alsa driver ... hw:SB|hw:U0x19400xac02|1024|2|48000|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xfcff8000 irq 16
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
**** alsa_pcm: xrun of at least 0.039 msecs
**** alsa_pcm: xrun of at least 0.042 msecs
JackPosixMutex::Unlock res = 1
**** alsa_pcm: xrun of at least 0.043 msecs
JackPosixMutex::Unlock res = 1
**** alsa_pcm: xrun of at least 0.043 msecs
JackPosixMutex::Unlock res = 1
**** alsa_pcm: xrun of at least 0.044 msecs
JackPosixMutex::Unlock res = 1
**** alsa_pcm: xrun of at least 0.042 msecs
JackPosixMutex::Unlock res = 1
**** alsa_pcm: xrun of at least 0.043 msecs
JackPosixMutex::Unlock res = 1
**** alsa_pcm: xrun of at least 0.031 msecs
JackPosixMutex::Unlock res = 1

Tried again, and I'm still not hearing any sound from ardour. Before you ask, my speakers are on :). I can hear sounds(ex. when I turn the computer on, clicking icons, so forth).

---

### Post by Pablo_F on 2011-05-22
"The onboard card is already in use" means that some other app or, most probably, the pulseaudio sound server is using the card. There are tricks to avoid this for ever. For the time being, try closing any apps that might try to access the soundcard. 

I suggest another test, start jack in capture only mode again:

jackd -S -d alsa -dhw:U0x19400xac02 -C

Then, run the alsa_out client on the onboard card. In another terminal:

alsa_out -dhw:SB

If you see problems here do a:

pulseaudio -k

and try again.


When using ardour, always make sure that the connections are correct. At this point, you can launch Jack Control. It will show that the jack server is already active but you can use the connection window to check/make connections between jack clients. 

To just check audio output through jack, you can use Aqualung, a nice audio player (install it via software center). Again, check that aqualung outputs are connected to the alsa_out's playback ports in the connection window of Jack Control.

You can also try online, realtime help via chat:

#ubuntustudio channel at irc.freenode.net. 
[http://webchat.freenode.net/](http://webchat.freenode.net/)

---

### Post by bloodshot13 on 2011-06-14
I've been reading alot about recording w/ Ubuntu and KXstudio and A/V studio. I'm wanting to make sure, before I do any drastic changes, that my system is set correctly the way it is(ex. all files(directories) set correctly, Audio group, ect......) I'm not sure if these are to the best of there abilities as it stands. Are there key points I should really look at closely. I'm able to record and playback in Ardour(downloaded but haven't tried Timemachine) but I get x-runs(pops,clicks) about every 20secs or so. As I've said before the only kernel I have installed is 2.6.38-8-lowlatency,my users group shows my name, as I set it in the initial install, in System>Administration> Users and Groups , set my processor scaling to performance. I don't run anything else (hardware,software) ,that I know of, while I'm recording. If all this is set as it should then I'll look at different avenues(Kxstudio low latency kernel as admired by Gmaq and Digitalrazor-https://ardour.org/node/4340, maybe even completely install A/v linux or Kxstudio). I would like to give what I have a real go before any of that. Thanks for any help. I see I have to , pulseaudio -k, everytime I run jack(kind of a pain). Would it be better if I completely disable pulse audio, and use Jack exclusively? I really think I'm going to like Ardour if I can get these x-runs completely gone. Thanks for anymore help(suggestions).

---

### Post by jejeman on 2011-06-14
What is youre sound card and jack settings?

---

### Post by bloodshot13 on 2011-06-15
> **jejeman said:**
> What is youre sound card and jack settings?

Not sure about "sound card settings" , it's the onboard sound card.What am I looking for? I'm not going to get the greatest sounds for recording. I'm just using logitech computer speakers with a sub. Maybe one day I'll either build or buy some good reference monitors ;). I hope the screenshot is what you were needing in the jack settings. Not really sure if I need to check unlock memory,force 16bit or any other settings. I'm not quite sure what these do.

---

### Post by sgx on 2011-06-16
ps ux

that command might display your running processes, if so, run it repeatedly and you might be able to spot something running that isn't
needed/wanted. There will be columns displaying memory and cpu usage, among others.
Cheers

The periods/buffers in qjackctl screenshot setting of 3 would be for usb audio interfaces, for motherboard soundchip, or pci soundcards,
try 4, and if that works better, test with 2, for lower latency.

Go through the links at the qjacktl wiki, for screengrab explanations

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl), like this one

[http://www.64studio.com/quickstart_jack](http://www.64studio.com/quickstart_jack)

---

