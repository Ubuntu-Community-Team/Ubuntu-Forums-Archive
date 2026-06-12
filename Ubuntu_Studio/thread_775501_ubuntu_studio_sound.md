---
title: "ubuntu studio sound"
date: 2008-04-30
forum: Ubuntu Studio
---

### Post by rodritinin on 2008-04-30
Hello. The first: sorry for my bad english . I'll try to explain things in a comprensive way. And sorry also if my question is answered in ohter posts but i am looking for it four days before i have decided to post here.
I have a dell inspiron with Ubuntu 7.10 (installed in factory). The sound goes OK. I have installed Ubuntu Studio 8.04 in another partition with kernel rt (with cd instalation). Well, the sound volume is very low in all aplications and in Audacity the sound Don't Exists!. I have change the input and output( all the options) in preferences and don't work.
How I can to copy the driver or adjusts in the other partition (ubuntu)? or can I update the alsa or audacity configuration?
Thanks in advance
:)

---

### Post by robeast on 2008-05-01
My sound volume was very low a little while ago (in Gutsy) and I had assumed my Audigy was about to kick the bucket. It turns out that some of the volume levels within my volume settings were low, while the master volume (which I was checking) was turned all the way up. So it may be a software setting with your low volume levels.

As for Audacity, check Edit >> Preferences and try a different playback device.

---

### Post by Stochastic on 2008-05-01
> **robeast said:**
> It turns out that some of the volume levels within my volume settings were low, while the master volume (which I was checking) was turned all the way up. So it may be a software setting with your low volume levels.

To check this you'll want to run ```
alsamixer
``` and browse through all the channels.

---

### Post by rodritinin on 2008-05-05
Thanks to you two. I have tried all the posibilities of alsa output device, but audacity don't sound any. With alsamixer i see all channels with max volume. In adition, ardour sounds very bad, in form interspersed (i don't know if it says like this).
In the other partition, with ubuntu, the sound works very well. Any one can say me if i can to install drivers of these partition, in the other (rt or low latency)and how i do this?:confused:
Thanks

---

### Post by Stochastic on 2008-05-05
hmm, I didn't understand very much of that last post, could you rephrase some of it.

I assume that the Ardour problem you mean it cuts in and out quickly?  Probably this is caused by xruns in the jack audio server that ardour uses.  Are you starting jack with qjackctl ahead of opening ardour, or are you using ardour's built in jack controls?  Either way, the key is to increase the frames/sec number, the periods/buffer number, or the samplerate.

If no other programs are running on your computer, open audacity, go to edit -> settings, and in the playback device settings choose ALSA: default.  If Audacity still doesn't play, try to change this value again until you've gone through the entire list.  When Audacity attempts to play do you see the line (playhead) moving across the file?

The partition thing is where you've somewhat lost me.  Explain how your partitions and installation(s) of Ubuntu are organized a bit more and that may lead to a solution to these issues.

---

### Post by rodritinin on 2008-05-05
Well, I 'll try to explain better (sorry, but it's difficult for me Linux and it's difficult also to write in english, ha,ha)
Ardour does that you say, i think. I'll try to configure  frames,periods,etc. and I 'll say you the results.(I am using ardour's built in jack controls. I'll try to run jack control before...)
The problem with audacity is that in the list for output device, option "default" don't appears. Only appears in the list for input. And my sound card is Sigmatel stac 9228 analog(intel). In output list appears digital sigmatel and not analog....
I have ubuntu installed at factory in a partition. When i installed Ubuntu Studio, ubuntu studio did a new partition and installed him in that, with a kernel rt.
The sound goes ok with ubuntu but goes very bad with all applications in ubuntu studio partition. I hope i explain me (sorry for my english...)
Thanks

---

### Post by rodritinin on 2008-05-07
Well, I've tried somethings and here is the results. Audacity don't sound (but no error appears), Rosegarden sounds only the first time. The second time I run it, don't sound and i have to reset computer for to hear again. Ardour don't sound and says "I have a limited memory by the sistem...type ulimit -l to see the limit (I do this and response is 32) ...it is limited by /etc/security/limits.conf probably ". 
Jack don't goes fine also. Like they are a lot of things, prior i speak only of Jack:
My sistem is intel dual core 1,86 GHz, 4 GBs of memory, Cache 2 MBs. Ubuntu studio is installed yesterday (8.04 Hardy) in one new partition. I run Jack Control and check "realtime" and  "monitor" . I have tried all the devices on the list "Interface" and I've tried all the "frames/period" (from 64 to 1024). With no other application running I click over "start" and in messages windows appears: 
" I cannot allocate memory..."
" I no block mem for buffers..."
More things and then thousands (2 or 3 every second) of
 "Alsa-pcm xrun al least 0,0xx msecs" in red color

What is happening? 
Thanks

---

### Post by jwmislan on 2008-05-08
You need to bring up your realtime memory allocation in - 
System - Administration - (Ubuntu Studio Controls)  

Try 80 - 95 % memory to allocate for audio.
Don't forget to put in qjackctl, a realtime setting of about 70 .

Hardy is now doing realtime different than gutsy.

Gutsy - we would build the realtime module ourselves - and make the settings for 
/etc/security/limits.conf .

Now this is becoming more automatic - You find it in the System Menu .
Too bad Ubuntu Support did not give enough notice to us audio users about this new feature.
It would have made a nice addition to the release notes - and some kudos  for Ubuntu  and Ubuntu Studio in particular.   


JWM

---

### Post by rodritinin on 2008-05-08
Thanks jwmislan. I didn't know that that control exists. I have checked memory to allocate for audio at 90%.
Since this no more messages of "non allocate..." appears. It's the first , but alsa-pcm xrum non disappears at all. 4 or 5 for second and music sound like a machine gun (ta,ta,ta,ta....)I don't know if you see that i say.

---

### Post by robeast on 2008-05-09
So your sound is still very choppy? Did you try adjusting the Frames/Period and Periods/Buffer in JACK as Stochastic had suggested?

---

### Post by jwmislan on 2008-05-09
Probably try using a player that uses jack as the driver .
Like Audacious - 
Audacious - preferences - Audio - ( Current Output Plugin: ) 
choose the jack output plugin .

Now remember that you have to start jackd first - qjackctl  . 

Make sure you have the group - audio - and you are  a member. -
Type - groups - in an x terminal window to see the groups you belong to. -
If you need to add the audio group - do -

sudo addgroup audio
-
then add yourself to the audio group
-
adduser (your user name) audio
-

Make sure you have setup qjackctl correctly.

qjackct - Setup - 
Realtime (checked) -
Priority ( mine is 75 )
Frames/Period ( mine is set to 64 - you can get good result with 128 )
Periods/Buffer ( mine is set to 3 - for my laptop hda intel soundcard )
Driver = ALSA
Input Device = hw:0
Output Device = hw:0
*
If you still get xruns, then your soundcard is probably sharing it's irq with some other process.
*
To fix that - first find the soundcard irq in /proc/interrupts - look for your sound cards irq 
something like 20 - 21 
if it's sharing with some other device, you can try in /boot/grub/menu.lst -
add at the end - 

kopt=pci=routeirq

this worked for me in Gutsy - 
 
Also
 you can use the chrt utility to raise priorties in /etc/rc.local
like this -
 Note: the rtc , (real time clock) standard irq = 8 
 YOUR Soundcard irq  - find in /proc/interrupts 
*
Make sure you copy these exactly including all single, and double quotes
REPLACE # hda Intel with your soundcard name - /proc/asound/cards .

Copy these, then past them into the bottom of /etc/rc.local
you need to be root - sudo gedit /etc/rc.local 

/usr/bin/chrt -f -p 96 `pidof "IRQ-8"`    # rtc
/usr/bin/chrt -f -p 60 `pidof "IRQ-23"`  # HDA Intel


Take a look at these web pages for some more detail on these concepts.

Details on the chrt (irq) settings, and realtime audio - 
[http://tapas.affenbande.org/wordpress/?page_id=40](http://tapas.affenbande.org/wordpress/?page_id=40)

Ubuntu -  Studio Preparation - 
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

Ubuntu Realtime Wiki - 
[https://wiki.ubuntu.com/RealTime/Gutsy](https://wiki.ubuntu.com/RealTime/Gutsy)

See what you can do with this info, should be of some help to you - 
and Best of Luck setting your audio : - .

JWM

---

### Post by rodritinin on 2008-05-12
Yes, I've adjusted Frames/period and periods/buffer and sound is better. Only a few of xruns appears (by ex. when i move the mouse) or when one other aplication begin to run.

jwmislan I'll try all you say and I'll write here that i get. But at the moment I have a very inestable system and i want to stabilize it before any try. It 'll take me 3 or 4 days. I think your ideas will go very well, because i have an hda intel in a laptop, also.
best regards

---

### Post by rodritinin on 2008-05-14
Well, I've done all that say jwmislan except "kopt=pci=routeirq" because my irq's was ok. But I'll explain better all I did.
1- I install ubuntu 7.10 Gutsy
2- apt-get update (including multiverse)
3- apt-get install linux-rt (a real time kernel)

When reboot, grub answer me what kernel i want to use and i select rt-kernel. Here, I installed jack control, ardour and audacity (with synaptic).

I created a new group of audio named "audio" and included me(like says jwmislan):

sudo addgroup audio

adduser (my user name) audio

I edited /etc/security/limits.conf and added:

@audio - rtprio 99
@audio - nice -10
@audio - memlock 2000000   (i lock the half of amount of memory)

I added in /etc/rc.local (like says jwmislan):

/usr/bin/chrt -f -p 96 `pidof "IRQ-8"` # rtc
/usr/bin/chrt -f -p 60 `pidof "IRQ-21"` # HDA Intel (my sound card uses 21 IRQ)


I configured jack like jwmislan says with Frames /period =128 and Periods/Buffer = 3.

**I get 8 msec of latency with no one xruns!** Same if i do other things at same time, like extract tracks of cd, uses firefox,etc

With ubuntustudio 8.04 i only got 45 msec of latency and 5 or 6 xruns/sec if i didn't touch mouse. If i moved the mouse, was 10 xruns/sec

Thanks to all by your help

---

### Post by jwmislan on 2008-05-16
roditinin

8 msec of latency - Thats Great - Glad to hear you have achieved very good results.

You can lock less memory like 500 meg (500000), for if only 1 gig memory is installed - or 1000000 if you have 2gigs . Even 1500000 with 2 gigs will leave enough for everything else to work fine.

If you want to eventually go with Hardy, there's a new setting that I told you about in my first reply to your post. That setting is for memory lock (to allow for audio), under System - Preferences - Ubuntu Studio settings.
I have another machine that gets good latency with that set to 99.
I found that Hardy rt-kernel has realtime built in, and with that setting works quite well for me.

My MSI laptop is still running Ubuntu Studio 7.1 - I was not ready to upgrade yet - but since good latency can be achieved with Hardy - Ubuntu Studio 8.04 - I may soon upgrade my Laptop - for the newer alsa, and jackd, - and other newer apps that I use.

Cheers
JWM

---

### Post by rodritinin on 2008-05-16
Ubuntu Hardy 8.04 doesn't work well in my laptop and nor Ubuntu Studio hardy (8.04).I tried with the two (and I tried "System - Preferences - Ubuntu Studio settings" )and I have gone back to 7.10.(the setting works but sound applications are not stables with 8.04)
I like 8.04 but....
Ah, I have 4 Gigs of memory
Best regards

---

### Post by gentlejunk on 2008-09-02
> **jwmislan said:**
> 
*
If you still get xruns, then your soundcard is probably sharing it's irq with some other process.
*
To fix that - first find the soundcard irq in /proc/interrupts - look for your sound cards irq 
something like 20 - 21 
if it's sharing with some other device, you can try in /boot/grub/menu.lst -
add at the end - 

this is what i get:
cat /proc/interrupts 
           CPU0       CPU1       
  0:   10353045          0   IO-APIC-edge      timer
  1:      11201          0   IO-APIC-edge      i8042
  8:          7          0   IO-APIC-edge      rtc
  9:        174          0   IO-APIC-fasteoi   acpi
 12:      31234          0   IO-APIC-edge      i8042
 14:      33294          0   IO-APIC-edge      libata
 15:          0          0   IO-APIC-edge      libata
 16:     973643          0   IO-APIC-fasteoi   HDA Intel, eth0, i915@pci:0000:00:02.0
 17:      70402          0   IO-APIC-fasteoi   uhci_hcd:usb3
 18:          3          0   IO-APIC-fasteoi   uhci_hcd:usb5, ohci1394
 19:          1          0   IO-APIC-fasteoi   uhci_hcd:usb4, yenta
 20:     478943          0   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2
219:     263755          0   PCI-MSI-edge      iwl3945
220:      87753          0   PCI-MSI-edge      ahci
NMI:          0          0   Non-maskable interrupts
LOC:     584237    5507911   Local timer interrupts
RES:    2912014    3905288   Rescheduling interrupts
CAL:       4330       5136   function call interrupts
TLB:       4648       5730   TLB shootdowns
TRM:          0          0   Thermal event interrupts
SPU:          0          0   Spurious interrupts

so i would guess there is no sharing?

---

### Post by gentlejunk on 2008-09-02
> **jwmislan said:**
> 
 
Also
 you can use the chrt utility to raise priorties in /etc/rc.local
like this -
 Note: the rtc , (real time clock) standard irq = 8 
 YOUR Soundcard irq  - find in /proc/interrupts 


JWM

can you pls explain this, i don get it. when i try to acces /etc/rc.local there is nothing in there.

my sound card:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
Subsystem: Hewlett-Packard Company Unknown device 30a2
Flags: bus master, fast devsel, latency 0, IRQ 16
Memory at f4580000 (64-bit, non-prefetchable) [size=16K]
Capabilities: [50] Power Management version 2
Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
Capabilities: [70] Express Unknown type IRQ 0

does that mean that my soundcard IRQ is 16?

this is my grep audio /etc/security/limits.conf
@audio - memlock 969763
@audio - memlock 969763
@audio - rtprio 99
@audio - nice -10
@audio - rtprio 99
@audio - nice -10
@audio - nice -10
@audio - memlock 250000
@audio - memlock 500000

still have xruns with :
11:12:31.221 /usr/bin/jackd -R -P70 -dalsa -r44100 -p128 -n4 -D -Chw:0 -Phw:0 -m

help

---

### Post by thorgal on 2008-09-02
> **gentlejunk said:**
> this is what i get:
cat /proc/interrupts 
           CPU0       CPU1       
...
 16:     973643          0   IO-APIC-fasteoi   HDA Intel, eth0, i915@pci:0000:00:02.0
...

so i would guess there is no sharing?

from what I can see, you have a lot of sharing. If you use the Intel HDA for the sound, you can see it's on IRQ 16, sharing it with your network chip AND your graphics chip ...

that's a lot of sharing :lol:
So it means that if you raise the IRQ thread priority for IRQ-16, your network card and graphics card will also benefit from it ;) they can certainly cause interrupts that will disturb the audio processing if you are on the net downloading or uploading something or doing some intensive graphical stuff (using compiz for example, or some very fast 2D scrolling, etc).

---

### Post by gentlejunk on 2008-09-02
this is what i found earlier in the tread, but cannot make out how it works:

"To fix that - first find the soundcard irq in /proc/interrupts - look for your sound cards irq
something like 20 - 21
if it's sharing with some other device, you can try in /boot/grub/menu.lst -
add at the end -

kopt=pci=routeirq"

can someone pls explain

thnx

---

### Post by thorgal on 2008-09-02
the "recipe" that was proposed seems to be a kernel trick to reassign IRQs at boot time. I never had to use such a trick because my DAW is a PC where I can choose the PCI slot for my PCI soundcard. PCI slots have a different IRQ and you can just try each of them until you find the one that is not sharing IRQ with other devices. But it looks like you have a laptop instead (the intel HDA is rather common in them). There, you cannot change anything unless the laptop BIOS allow you to reassign IRQs (unlikely for laptops), or the kernel can reroute IRQs. The latter is what was proposed to you. You will have to ask someone who tried that or google around, I cannot be more specific about it.

---

### Post by gentlejunk on 2008-09-15
thnx guys for all help you are giving but it seems to me that ubuntu 8.10 is not for human beings anymore. yes, it does have nice stuff going with it, but most of stuff that is essential doesnt work. i cannot even run my audacity. and im not a coder or smart guy, so i try to follow all the lines and put everything and sleeples nights. i think ill go back to 7.10 as it seems to me that ill have less tuning for better result.

so why is this? it seems that we are getting nicer looking buttons, that dont work?

---

### Post by Stochastic on 2008-09-15
> **gentlejunk said:**
> thnx guys for all help you are giving but it seems to me that ubuntu 8.10 is not for human beings anymore. yes, it does have nice stuff going with it, but most of stuff that is essential doesnt work. i cannot even run my audacity. and im not a coder or smart guy, so i try to follow all the lines and put everything and sleeples nights. i think ill go back to 7.10 as it seems to me that ill have less tuning for better result.

so why is this? it seems that we are getting nicer looking buttons, that dont work?

Well 8.10 is a development version right now, and there are major kernel issues with audio processing so only REAL hackers should be testing it for audio purposes right now.  Try 8.04 it's solid as a rock!

---

### Post by gentlejunk on 2008-09-23
thats a good advice! is there an easy way do de-grade :) 

how to jump from 810 to 804 without hving to go all froma beggining?

or is it going from clean install the best solution?

---

### Post by AudioDef on 2008-10-22
I have the same problem as the original poster - very low sound output, although everything works and the sound is clear - just at a very low volume and everything is turned up (alsamixer, etc.). 

Anyone have any luck figuring out how to increase the sound output for Ubuntu Studio?

---

### Post by AudioDef on 2008-10-23
rodritinin, what sound card do you have? I'm wondering if this problem is card-specific. I have an Audigy Z2.

---

