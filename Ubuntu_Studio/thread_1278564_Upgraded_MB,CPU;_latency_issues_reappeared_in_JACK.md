---
title: "Upgraded MB,CPU; latency issues reappeared in JACK"
date: 2009-09-29
forum: Ubuntu Studio
---

### Post by solarbird on 2009-09-29
Hi! I've upgraded my machine's motherboard/CPU/RAM and am now seeing increased(!) latency/XRUN issues with JACK.

I'm running Ubuntu Studio 8.04 Hardy + JACK + Ardour on a 32-bit realtime kernel (2.6.24-24-rt) using an M-Audio FastTrack Pro connected via USB, using ALSA driver support for the USB standard microphone/playback devices. I had been on a Pentium 4 2.6Ghz motherboard with 1G RAM and had reasonably good effect with smallish Frames/Period (128 f/p) and Periods/Buffer (3 p/b) settings, with very little overflow problem. With a lot of performance tuning I managed seven or eight recorded tracks (with four active) before Ardour would start becoming too slow for editing. (The recording cursor would be out of place, scrolling wouldn't work during playback or recording, and so on.)

Since I'm working on music with many takes and 7-8 final stereo tracks, I needed better performance. So I upgraded my motherboard (now Gigabyte G31M-ES2L), CPU (now Intel Pentium Dual-Core E5200, 2.50Ghz), and RAM (still 1G, but dual-channel, and RAM hasn't been a problem. The other components remained the same. (I just took out the old MB/CPU/RAM and swapped in the new ones.) Oh, the on-motherboard soundcard is the usual Realtek bullshittery, um... ALC833. It works, and ALSA recognises it, but I only use it for system sounds and not for recording. The previous motherboard had some similar Realtek chipset that I also ignored.

Everything works and is *much* faster, **except** that I now get small but essentially continuous buffer XRUNs in Jack if I set the Frames/period below 2048, even if nothing else besides jackd is running. Increasing the Frames/period doesn't help at all that I can tell until you reach 2048 f/p (279ms latency!) and then everything works fine without any overruns, even if I run a lot of things. It's all very snappy and awesome. But that's a lot of latency and something is clearly wrong.

I have gone back over all the FAQs I can find on buffer xrun issues in JACK but haven't found anything useful. I have tried all sorts of things including playing with process priorities but without luck. ](*,)

Has anyone seen this or something like it? I am confused and need to get back to recording. I can work with this latency I guess if I have to but it will make many things more annoying.

Thanks!

-- Dara

PS: The only other add-on device in the system is a wireless LAN card. This same card was on the previous motherboard and uses the same driver, rtl8185 through ndiswrapper.

---

### Post by kayosiii on 2009-09-30
The thing that jumps immediately to mind is some kind of hardware interupt problem... But I am only guessing at this point.

---

### Post by thorgal on 2009-09-30
yeps, new mobo -> new IRQ setup ;)

```

cat /proc/interrupts

```

check that stuff like e.g. hal disk driver polling every 2 secs is not on the way, check that you are not sharing IRQ with the wifi stuff (if you have wifi), etc, etc. Lots of things ...

---

### Post by VertexPusher on 2009-09-30
> **solarbird said:**
> Everything works and is *much* faster, **except** that I now get small but essentially continuous buffer XRUNs in Jack if I set the Frames/period below 2048
Have you made sure that Jack is connected to the actual hardware device? It should talk straight to "hw:X,Y", not "default" or "plughw:X,Y" etc.

---

### Post by c00kie55 on 2009-09-30
i use realtek alc600 something and it works great? 128fps only xruns when system is bussy doing somethig else 
i can get below 128 but then its taking to much power 

let me get it rigth you are still using old instalation on new machine that migth give some errors.. have you tryed reebot in failsave and done dpkg update

have you tryed disabling hardware drivers or the virtual effects i remember once having problems with thoes
and jack ?

and have you tjekked that you dont have agp taking up memmery in bios lots off thoes new mobos have built in hardware that use memory sometimes alot 

mayby you got sata drivers but using pata in bios cut also slow you down

---

### Post by solarbird on 2009-09-30
Yay! Many replies. Thanks! I am consolidating my answers. ^_^

I have not tried failsafe boot as everything seemed to be working great otherwise. I didn't think dpkg update would update configuration, it doesn't seem to say that in the docs. I do know that I'm not having memory issues, nor am I swapping significantly, or so on. I do have both sata and pata drivers but I need them both b/c I have a very nice pata HD.

JACK is talking diretly to hw: and not to [default] or another similar name.

Here's the interrupt table; I was looking for it earlier to try doing things like upping the task priority on the appropriate IRQ handlers. (It didn't seem to do anything useful but I could've been doing it wrng):

```
$ cat /proc/interrupts
           CPU0       CPU1       
  0:        589         12   IO-APIC-edge      timer
  1:         67         68   IO-APIC-edge      i8042
  6:          3          2   IO-APIC-edge      floppy
  8:         28         17   IO-APIC-edge      rtc
  9:          0          0   IO-APIC-fasteoi   acpi
 12:       4865       4893   IO-APIC-edge      i8042
 14:      14835      14836   IO-APIC-edge      libata
 15:       6351       6359   IO-APIC-edge      libata
 16:        589        549   IO-APIC-fasteoi   uhci_hcd:usb4, HDA Intel, i915@pci:0000:00:02.0
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb1, ehci_hcd:usb5
 19:     841631     841637   IO-APIC-fasteoi   uhci_hcd:usb2, ndiswrapper
 20:          0          0   IO-APIC-fasteoi   uhci_hcd:usb3
NMI:          0          0   Non-maskable interrupts
LOC:    5417988    5416576   Local timer interrupts
RES:       6067       6243   Rescheduling interrupts
CAL:        512        914   function call interrupts
TLB:        468        428   TLB shootdowns
TRM:          0          0   Thermal event interrupts
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0
```Thanks!

---

### Post by solarbird on 2009-10-01
I didn't mention this before but! who knows, maybe it's related? The only other weird thing the machine is doing is that when you click on the Ubuntu menu in the desktop's upper left corner and select Quit, it takes about two minutes(! yes I timed it) for the popup box showing all the various options (Log out/Lock screen/Switch User/Restart/Shut Down) to appear. That didn't happen before either. (I don't routinely shut the machine down so didn't notice this at first.) It's weird.

---

### Post by thorgal on 2009-10-01
```

19:     841631     841637   IO-APIC-fasteoi   uhci_hcd:usb2, ndiswrapper

```

mmmm, does not look too good. Where is your soundcard ? If USB, type 
```

lsusb

```

in the terminal.

ndiswrapper is, I presume, for your WIFI driver that only comes in a windows version (no linux native) ? If it shares interrupt with your soundcard, you may have to rethink a bit about your system.

The other thing is

```

      589        549   IO-APIC-fasteoi   uhci_hcd:usb4, HDA Intel, i915@pci:0000:00:02.0

```

i915: you have an intel graphics chip ... not so good either due to "picaccess". I stopped using my onboard graphics chip and use now an nvidia GeForce 9500 GT (PCI express). It's night and day ... I've been running jackd (jack2 svn version) for one week or so at < 1ms latency with all sorts of **** running on the desktop PC, even composite effects turned on. I have not seen a single xrun all this time, and I have been watching movies on this machine via mplayer (which can use jack for the audio). This is really insane! But I don't necessarily recommend you take the same path. I compile my own kernel, have a dedicated PCI audio interface (RME HDSP) that does not share IRQ with any other device and don't use WIFI at all.

---

### Post by solarbird on 2009-10-01
Hi!

```
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0763:2012 Midiman 
Bus 001 Device 001: ID 0000:0000
```I thought it was on Device 001 because of things the MB manual said. Apparently the front jacks are 004/005, as I have confirmed by moving the M-Audio to another jack:

```
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0763:2012 Midiman 
Bus 001 Device 001: ID 0000:0000
```...which makes that portion of /proc/interrupts look like:

```
 16:        775        760   IO-APIC-fasteoi   uhci_hcd:usb4, HDA Intel, i915@pci:0000:00:02.0
 18:      63967      64058   IO-APIC-fasteoi   uhci_hcd:usb1, ehci_hcd:usb5
 19:     827567     827570   IO-APIC-fasteoi   uhci_hcd:usb2, ndiswrapper
 20:          0          0   IO-APIC-fasteoi   uhci_hcd:usb3
```...which takes it off both the HD and the lolh8 i915!

Is it possible to assign the wireless (I need wireless there're no cables up here and no way to get one up here without CRAZYTIEM) another IRQ? Does it matter which one?

(Oh and yes there is no native driver for the rtl8185 - well, there officially is some redhat source but I tried compiling it and that was... not good.)

I'll see if fixing this conflict improves life and post back in a sec. Maybe I'll tape over the other USB port if this works ^_^

---

### Post by solarbird on 2009-10-01
Okay, that helped! Latency is still worse than before, but not nearly as worse - I can run now at 512 frames/period 6 periods/buffer for a latency of 69.7ms, which is much better!

I want to avoid buying a new card if I can. I don't need much out of the graphics system on this thing, I just want it solid for recording studio work. ^_^

Thanks!

---

### Post by markbuntu on 2009-10-01
You could try reinstalling alsa to remove the old unused driver from the kernel and get the one for the 883 properly installed. The kernel could be getting a little confused and looping a little trying to enable the driver for your now non-existent hardware every time alsa is called. That could certainly push latency up.

When I replaced my mobo I had some weird glitchy problems with my sound devices until I reinstalled alsa. Not showstoppers but just some vague weirdness. Make sure you make note of and reinstall all the packages that get removed when you remove alsa.

---

### Post by solarbird on 2009-10-01
I'm terrified of trying to reinstall ALSA - it was kind of nightmarish to get going the first time! But it seems to know about the existing hardware (the 883 which is present) and isn't complaining (as far as I can find in places like syslog) about not being able to find other hardware - is there someplace else to check? The devices list it has in the device manager appears to be correct.

---

### Post by markbuntu on 2009-10-01
That was what happened to me, nothing obvious but something was wrong. You could look in your other logs to see if some weirdness is happening. The AC'97 driver from my old mobo was still active and seemed to be the cause of the problems... I don't remember how I found that, maybe in the kern.log.

---

### Post by c00kie55 on 2009-10-03
6 period buffers is that good i only use 2 and get 128 frames/period 

priority 70 (high value seams importent)
port max 512
 samplerate 44
 force 16 bit 

intel onbord soundcard alc6xx

i just had a experince with lots off xruns like you somehow uninstall/instaling wine helped me or was it uninstaling lash 6.0 from git and instaling old 5.4 from repro dont know realy  but it helped me

---

### Post by solarbird on 2009-10-05
I'm really starting to hate ubuntu studio... sorry, but I am...

So last night networking decided to quit for a while - it worked booted to Windows, but not to Ubuntu - until I cold-powered-down the machine, at which point it would work with our WEP legacy wireless but not our newer WAP wireless. (Or rather, it would, for a little bit, and then it would die, on the WAP.) Having seen this before I was marginally okay with it (in that, 'well, at least this side's working' way, as I've had to be several times dealing with this), and shut down. It came up this morning fine, UNTIL I tried to reinstall the audio drivers as suggested here using the suggested way to do it [elsewhere in these fora]("http://ubuntuforums.org/showthread.php?t=1269806"):

```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```

...at which point it decided the internet didn't really exist (even tho' network status as reported by the network status tool was fine and even moving packets), and threw a bunch of errors at me and quit, and then I didn't have sound *or* networking anymore, and now that I've rebooted, I have no networking and no sound *drivers* at all, and while ndiswrapper reports that ndiswrapper is fine and the card is installed and working, the card is UNCLAIMED in the network configuration list and modprobe says the ndiswrapper package isn't even on the machine. ("FATAL: Module ndiswrapper not found.")

I'm going to get the DVD-ROM I have and see if I can... frankly I hardly even know at this point. Even when I'm making no hardware changes at all, Ubuntu Studio explodes like this about every three weeks. I really appreciate you guys trying to help and I know this is open-source software (and I can't afford a nice loaded OSX box) but this is just insanity-making. Not to mention what it does to my productivity as a musician. (Last night I spent twice as much time trying to get the network to work again after it just decided not to for a while than I spent recording and editing. I mean... what?)

---

### Post by solarbird on 2009-10-05
markbuntu: do you know what kind of errors you were seeing? I don't see anything in kern.log after all this (now that I'm running again) and I really don't know what else to do here.

Oh, I couldn't reinstall linux-image-2.6.24-24-rt and linux-ubuntu-modules-2.6.24-24-rt because it says the package for linux-image-2.6.24-24-rt couldn't be found, which I know is the kernel package, which is a "...whaaaa?" But everything else ran through --reinstall smoothly if run separately, so I did that.

---

### Post by solarbird on 2009-10-05
Oh, [this page describes the old motherboard]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00063244&lc=en&cc=hk&dlc=zh-hant&product=402250&rule=41820&dest_page=documentIndex"), and sound chipset.

---

### Post by solarbird on 2009-10-09
This is mostly a bump. I still have significant latency, much more than I had with a much less capable motherboard. I pasted in what I did to reset the ALSA installation - was that right? Did I miss something?

Thanks...

---

### Post by c00kie55 on 2009-10-09
i might be a idea with a fresh install on a new partition. just to se if you still have same symptoms 
that way you cut be sure, what your dealing with...  i mean, you have already used, the time off many re-installations  and if its working good, on new partition. your can build as old. copy your projects to new partition. don't delete old before, you are sure you have backed up, all the important stuff.

---

### Post by solarbird on 2009-10-14
foo. That's a lot of trouble. I guess I'll just live with it.

Oh, I took out the wireless card and hooked the ether card to a wireless bridge just to eliminate ndiswrapper and the Windows driver from the equation - this improved my networking stability significantly but didn't help a whit with the xruns with latencies under 70ms.

Thanks for the help tho'. At least it's down to 70ms. Still much worse than I had with the slower system, but usable, and everything *else* is much faster now. ^_^

---

