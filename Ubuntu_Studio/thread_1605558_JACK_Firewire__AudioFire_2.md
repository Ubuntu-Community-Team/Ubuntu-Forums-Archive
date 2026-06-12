---
title: "JACK Firewire : AudioFire 2"
date: 2010-10-25
forum: Ubuntu Studio
---

### Post by harryhaaren on 2010-10-25
p, li { white-space: pre-wrap; } Hey Guys,


Fresh install of Studio 10.10, firewire audio is broken though.
I've plenty of experience with the old firewire stack, but this "new" thing has me confuzed.


I'm getting this error:

JACK server starting in non-realtime mode
 00267765491:  (ffado.cpp)[  92] ffado_streaming_init: libffado 2.999.0- built Aug 11 2010 00:12:04
 firewire ERR: FFADO: Error creating virtual device
 Cannot attach audio driver
 JackServer::Open() failed with -1


I think the modules are loaded:  ?

sudo lsmod | grep 1394
ohci1394               27024  0 
raw1394                22462  0 
ieee1394               81069  2 ohci1394,raw1394


What else should I be doing..?
Thanks for reading, cheers, -Harry

---

### Post by trulan on 2010-10-25
Looks like you've got the old stack enabled.  The new stack looks like this:
```
$ lsmod | grep firewire
firewire_ohci          24679  0 
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
```And if you happen to have both driver stacks enabled you'll have problems for sure.

---

### Post by AutoStatic on 2010-10-26
Hello Harry,

libffado 2.999.0 is FFADO from svn trunk. That version doesn't support the new JuJu stack. You will need libffado 2.0.1 if you want to work with the new stack. But apparently you're still using the old stack so it's probably something else that isn't configured right. What are the permissions of */dev/raw1394* ? And what does **cat /proc/interrupts** output?

Best,

Jeremy

---

### Post by harryhaaren on 2010-10-26
Hey Trulan,

I've got a standard ubuntu studio install (10.10) yet it does seem that both stacks are available...

lsmod | grep firewire   returned the same as you had,
and I've posted the lsmod | grep 1394 output. Ill try "rmmod"-ing the old stack modules when I've got the fw card available and retry JACK..

Cheers, -Harry

---

### Post by harryhaaren on 2010-10-26
Hi Auto,

I've got FFADO  2.0.1+svn1856-ubuntu1  installed at the moment (standard maverick source).
I was a little confused as to the 2.999 version number (should be 1.999?) or else 2.0.1 (more logical)?

Anyway, I've done a little rummaging around with Ubuntu Studio controls to give me real-time priveliges.

This is what  cat /proc/intertupts returns:


  0:    2922283    1211557   IO-APIC-edge      timer
  1:       1705          5   IO-APIC-edge      i8042
  8:          1          0   IO-APIC-edge      rtc0
  9:      27267      24035   IO-APIC-fasteoi   acpi
 12:     355436         95   IO-APIC-edge      i8042
 14:      37591      13324   IO-APIC-edge      ata_piix
 15:          0          0   IO-APIC-edge      ata_piix
 17:     212245     324032   IO-APIC-fasteoi   uhci_hcd:usb6
 18:        269         77   IO-APIC-fasteoi   uhci_hcd:usb7
 19:     105239       1785   IO-APIC-fasteoi   ata_piix
 20:         34         11   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb3
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 22:         63         59   IO-APIC-fasteoi   yenta, tifm_7xx1, mmc0, firewire_ohci
 23:      51560         54   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb5
 44:      45426      28273   PCI-MSI-edge      radeon
 45:         60         60   PCI-MSI-edge      hda_intel
 46:          1          2   PCI-MSI-edge      eth0
 47:     720675     257189   PCI-MSI-edge      iwl3945
NMI:          0          0   Non-maskable interrupts
LOC:    1064730    1878035   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:    4485130    4394789   Rescheduling interrupts
CAL:         98         87   Function call interrupts
TLB:      20053      20531   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:         37         36   Machine check polls
ERR:          0
MIS:          0



Cheers, -Harry

---

### Post by AutoStatic on 2010-10-26
> **harryhaaren said:**
> I've got FFADO  2.0.1+svn1856-ubuntu1  installed at the moment (standard maverick source).
I was a little confused as to the 2.999 version number (should be 1.999?) or else 2.0.1 (more logical)?2.999.0 is FFADO from svn trunk so the versioning of the Ubuntu package is wrong. 2.0.1 is a separate branch, in fact it's svn trunk checkout 1854 afaik. Everything after that, so also 1856, is 2.999.0, so the 2.x.0 branch which has nothing to do anymore with 2.0.1.
Pfff, confusing stuff :|
 

> **harryhaaren said:**
> ```
 22:         63         59   IO-APIC-fasteoi   yenta, tifm_7xx1, mmc0, firewire_ohci
```Ah, now you switched to the new stack? Pretty crowded IRQ. I fear you will need rtirq if you want to use your Echo in a stable manner. But then you need a real-time kernel. Maverick doesn't have one.

---

### Post by trulan on 2010-10-26
lsmod | grep 1394 returns nothing here, but then this isn't a Ubuntu Studio install, it's a desktop that gets used mostly for desktop stuff with a few studio packages thrown in.  My laptop is my studio rig and that's still on Lucid.

If a default Ubuntu Studio install has both firewire driver stacks enabled (as your case seems to indicate), that indicates a problem in the setup.  Here's the wiki page on using/selecting firewire driver stacks:
[https://ieee1394.wiki.kernel.org/index.php/Juju_Migration](https://ieee1394.wiki.kernel.org/index.php/Juju_Migration)
I have to wonder if installing Ubuntu Studio still adds those lines about raw1394.  That is probably what's pulling in the rest of the old stack.  It would be interesting to see the contents of your /etc/modprobe.d/blacklist-firewire.conf.

At any rate, another test run of my setup:
On my desktop, running Maverick, Jack Control gives this in the messages window on startup:
```
[COLOR=#999999]14:44:16.052 JACK is starting...[/COLOR]
 [COLOR=#990099]14:44:16.053 /usr/bin/jackd -P76 -dfirewire -r44100 -p64 -n3[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 [COLOR=#999999]14:44:16.067 JACK was started with PID=6876.[/COLOR]
 Memory locking is unlimited - this is dangerous. You should probably alter the line:
      @audio   -  memlock    unlimited
 in your /etc/limits.conf to read:
      @audio   -  memlock    1492929
 no message buffer overruns
 JACK compiled with System V SHM support.
 loading driver ..
 Enhanced3DNow! detected
 SSE2 detected
 115344263468:  (ffado.cpp)[  92] ffado_streaming_init: libffado 2.999.0- built Aug 11 2010 00:17:24
 [COLOR=#999933]14:44:18.105 Server configuration saved to "/home/trulan/.jackdrc".[/COLOR]
 [COLOR=#999999]14:44:18.106 Statistics reset.[/COLOR]
 [COLOR=#999999]14:44:18.150 Client activated.[/COLOR]
 [COLOR=#cc9966]14:44:18.167 JACK connection graph change.[/COLOR]
 Enhanced3DNow! detected
 SSE2 detected
 [COLOR=#cc9966]14:44:22.361 JACK connection graph change.[/COLOR]
 [COLOR=#9999cc]14:44:22.557 JACK connection change.[/COLOR]

```And Synaptic says I have libffado2 2.0.1+svn1856-1ubuntu1.  (By the way, 64 x 3 buffering is not at all stable here on the generic kernel, but it does run.)

my lsmod looks like this:
```
trulan@trulan-desktop:~$ lsmod | grep firewire
firewire_ohci          24679  0 
firewire_core          54327  19 firewire_ohci
crc_itu_t               1739  1 firewire_core
trulan@trulan-desktop:~$ lsmod | grep 1394
trulan@trulan-desktop:~$ 
```As far as the interrupt being busy, yenta is your card controller and firewire_ohci will be on the same irq as the card controller.  mmc0 is your card reader I believe, so don't use that.  I don't know what tifm_7xx1 is, but you'll need to make sure that isn't being used if you want any kind of stability.

---

### Post by harryhaaren on 2010-10-26
Thanks a lot for the quick responses, but I'll probably chicken out -  I need a 100% RT stable machine.
And I'm used to the old stack. :-)

Ill probably hop back to either Lucid or Hardy (!), it ran awesome fast for me... (2x64 no probs!)

Thanks Trulan too. 
-Harry

---

### Post by ajaaskel on 2010-10-30
I upgraded from Ubuntu Studio version 10.04 to 10.10.  Harry, the same problem here with FireWire audio.  I have Echo AudioFire 12 connected to FireWire.  It was working with 10.04 but needed to use big buffer for Jack which will result in long latency.  I guess Ubuntu Studio 10.10 will be just great after I learn how to fix those audio (FFADO etc) problems. Sure there is a solution, timeframe is whatever it happens to be,  looking forward... :)

ffado-test Discover
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- [www.ffado.org](www.ffado.org)
Version: 2.999.0-
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

Could not initialize device manager
03535881341: Fatal (devicemanager.cpp)[ 191] initialize: No firewire adapters (ports) found.
no message buffer overruns


ffado-diag


FFADO diagnostic utility 2.999.0-
============================
(C) 2008 Pieter Palmers


=== CHECK ===
 Base system...
  kernel version............ 2.6.32-25-preempt
FIXME: implement test for RT kernel
   RT patched............... False
  old 1394 stack present.... True
  old 1394 stack loaded..... False
  old 1394 stack active..... False
  new 1394 stack present.... True
  new 1394 stack loaded..... True
  new 1394 stack active..... True
  /dev/raw1394 node present. True
  /dev/raw1394 permissions.. True
.
.
.
=== REPORT ===
FireWire kernel drivers:

The new FireWire kernel stack is loaded. 
This stack is not supported by FFADO. Please use the old stack.

lsmod
.
.
raw1394                25386  0 
crc_ccitt               1675  1 rt2800usb
drm                   200158  3 nouveau,ttm,drm_kms_helper
ieee1394               95817  1 raw1394
i2c_nforce2             6163  0 
snd_page_alloc          8596  2 snd_hda_intel,snd_pcm
usblp                  12503  0 
i2c_algo_bit            6024  1 nouveau
psmouse                64832  0 
serio_raw               4982  0 
lp                      9400  0 
parport                37470  3 parport_pc,ppdev,lp
usbhid                 40860  0 
hid                    83792  1 usbhid
usb_storage            49737  0 
firewire_ohci          24965  0 
forcedeth              54248  0 
firewire_core          52030  1 firewire_ohci
crc_itu_t               1715  1 firewire_core
ahci                   37838  2

---

### Post by ajaaskel on 2010-10-30
I have a work around for 10.10. The basic idea is to unload all FireWire drivers first and load the older ones which work ok for audio even in 10.10 provided you select "preempt" kernel when booting up Ubuntu Studio.  Default is NOT to use "preempt" kernel.  Since unloading and loading includes many steps I made a script to do it easier. Here it comes:

#!/bin/sh
#Unloads all FireWire drivers and loads older FireWire stack 
#30.10.2010 by "ajaaskel" @ Ubuntu Forum
sudo modprobe -r video1394
sudo modprobe -r firewire-sbp2
sudo modprobe -r sbp2
sudo modprobe -r dv1394
sudo modprobe -r firewire-ohci
sudo modprobe -r raw1394
sudo modprobe -r ohci1394
sudo modprobe  raw1394
sudo modprobe  dv1394
sudo modprobe  sbp2
sudo modprobe  dv1394
sudo modprobe  video1394
echo
echo  '*** Load also ffado-dbus-server if you need ffado-mixer. ***'
echo
sleep 5

Paste that to your editor, save it as fw.sh to your home directory, set "Allow Execution" on for that and run in terminal with command

./fw.sh

(Do not forget dot slash in the beginning)

Those drivers with 10.10 appear to work a lot better than older ones with 10.04. No idea if it's due to stack itself or "Jack".  I was first time able to use low latencies like 1 ms.
With 10.04 that short buffer made xrun counter progress --- no Ardour loaded yet  :)
Looks good so far.

---

### Post by AutoStatic on 2010-10-30
Hello ajaaskel, you don't need to script this. It's better to blacklist the new stack in */etc/modprobe.d/blacklist-firewire.conf* and comment out all the old stack modules:```
#blacklist ohci1394
#blacklist sbp2
#blacklist dv1394
#blacklist raw1394
#blacklist video1394

blacklist firewire-ohci
blacklist firewire-sbp2
```

Weird though that Maverick comes with FFADO 2.999.0 that doesn't support the JuJu stack which seems to be enabled by default.

Best,

Jeremy

---

### Post by trulan on 2010-10-31
> **AutoStatic said:**
> Hello ajaaskel, you don't need to script this. It's better to blacklist the new stack in */etc/modprobe.d/blacklist-firewire.conf* and comment out all the old stack modules:```
#blacklist ohci1394
#blacklist sbp2
#blacklist dv1394
#blacklist raw1394
#blacklist video1394

blacklist firewire-ohci
blacklist firewire-sbp2
```
After editing this file, you'll need to rebuild the initrd so the changes will take effect:
[https://bugs.launchpad.net/ubuntu/+source/kino/+bug/6290/comments/78](https://bugs.launchpad.net/ubuntu/+source/kino/+bug/6290/comments/78)

> Weird though that Maverick comes with FFADO 2.999.0 that doesn't support the JuJu stack which seems to be enabled by default.The default FFADO in Maverick (which calls itself 2.999.0) works with the JuJu stack here.  I think the problem we are seeing here is that both firewire stacks are being enabled.

---

### Post by ajaaskel on 2010-10-31
Thanks "AutoStatic" and "trulan", I need to try that.  I actually did that "blacklist" change alone but since I didn't know about  "update-initramfs" I failed with that. Let's see.....a moment

Done, blacklisting works ok like you described after

> sudo update-initramfs -k all -u

Thanks again !  No need for a script after that.

---

### Post by ajaaskel on 2010-10-31
>   I think the problem we are seeing here is that both firewire stacks are being enabled.

I was curious abot that.  I changed blacklist entries back to disable old stack, run that update-initramfs, booted and checked, result is here:

ffado-test Discover
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- [www.ffado.org](www.ffado.org)
Version: 2.999.0-
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

Could not initialize device manager
00047916040: Fatal (devicemanager.cpp)[ 191] initialize: No firewire adapters (ports) found.
no message buffer overruns


Jack fails, too.

So, I am succesful only with that old stack.

---

### Post by trulan on 2010-11-01
> **ajaaskel said:**
> ffado-diag


FFADO diagnostic utility 2.999.0-
============================
(C) 2008 Pieter Palmers


=== CHECK ===
 Base system...
  kernel version............ 2.6.32-25-preempt
FIXME: implement test for RT kernel
   RT patched............... False
  old 1394 stack present.... True
  old 1394 stack loaded..... False
  old 1394 stack active..... False
  new 1394 stack present.... True
  new 1394 stack loaded..... True
  new 1394 stack active..... True
  /dev/raw1394 node present. True
  /dev/raw1394 permissions.. True

Here's where mine is different - raw1394 is not loaded:

ffado-diag


FFADO diagnostic utility 2.999.0-
============================
(C) 2008 Pieter Palmers


=== CHECK ===
 Base system...
  kernel version............ 2.6.35-22-generic
FIXME: implement test for RT kernel
   RT patched............... False
  old 1394 stack present.... True
  old 1394 stack loaded..... False
  old 1394 stack active..... False
  new 1394 stack present.... True
  new 1394 stack loaded..... True
  new 1394 stack active..... True
  /dev/raw1394 node present. False

libraw1394 is installed but not loaded, apparently.  Maybe that is what is causing things to fail for you with the new stack?

---

### Post by ajaaskel on 2010-11-01
I have preempt kernel from 10.04 because I upgraded from that.  Have you tried that with new stack ?   I'm actually pleased with my mix of preempt kernel (originally from 10.04) and Ubuntu Studio 10.10 with old FireWire stack, looks good for audio purpose.  Sure I'm interested in seeing that new stack working, maybe it's something even better if possible ?

---

### Post by trulan on 2010-11-01
Hey, if it's working well on the legacy stack, you don't need to change anything - I was just trying to figure out why it was failing, because it should work on the JuJu stack too.  CPU usage is observably lower on the JuJu stack on my desktop, but the difference isn't all that big, not worth messing up a working system.

I have tested the JuJu stack with 2.6.33-rt and 2.6.35-generic.  I have not tried it with any 2.6.32 kernels though the ffado site says that should work as well.  Ffado will not work with the new stack on 2.6.31 or older.

---

### Post by mango42 on 2010-11-02
Just a avid but clueless 'user' comment: 

This 'old stack' / 'new stack' / realtime / preempt / ffado stuff is really doing my head in - to the extent that I'm just not getting to any music-making right now. Beginning to feel like I did when first introduced to Red Hat back in 1998 - somewhat intimidated...

:confused: :popcorn:

Is a resolution in sight? Answers in less than two syllables, please ;-)

---

### Post by ajaaskel on 2010-11-03
>  to the extent that I'm just not getting to any music-making right now

We will be test recording during next weekend using Ubuntu Studio 10.10 & Echo AudioFire 12 with a customized setup like described above (different kernel, modified FireWire setup).  

Sorry, technical terms are needed in order to handle technical matters.  I understand frustration of non-technically minded musicians reading our conversation but no problem actually:  Just post a new question of your own and you'll get answers for your thread / problem.  ok ?  :)

---

### Post by ajaaskel on 2010-11-10
I still tried again that new stack.  This time I even manually dropped out raw1394 to make sure there is nothing left about old stack:

Module                  Size  Used by
parport_pc             29958  0 
ppdev                   6471  0 
fbcon                  39612  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5875  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9921  1 vga16fb
snd_hda_codec_realtek   278750  1 
snd_hda_intel          25705  2 
snd_hda_codec          85984  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6992  1 snd_hda_codec
snd_pcm_oss            41384  0 
snd_mixer_oss          16385  1 snd_pcm_oss
snd_pcm                86589  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31621  0 
snd_seq_midi            5989  0 
snd_rawmidi            23042  1 snd_seq_midi
rt2870sta             526642  0 
arc4                    1473  2 
snd_seq_midi_event      7331  2 snd_seq_oss,snd_seq_midi
snd_seq                57823  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23223  2 snd_pcm,snd_seq
nouveau               516811  2 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    60617  1 nouveau
rt2800usb              33496  0 
rt2x00usb              11292  1 rt2800usb
snd                    71936  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         31036  1 nouveau
soundcore               8394  1 snd
rt2x00lib              32133  2 rt2800usb,rt2x00usb
led_class               3764  1 rt2x00lib
lp                      9400  0 
snd_page_alloc          8596  2 snd_hda_intel,snd_pcm
drm                   200158  3 nouveau,ttm,drm_kms_helper
parport                37470  3 parport_pc,ppdev,lp
i2c_algo_bit            6024  1 nouveau
i2c_nforce2             6163  0 
mac80211              244853  2 rt2x00usb,rt2x00lib
psmouse                64832  0 
serio_raw               4982  0 
cfg80211              149613  2 rt2x00lib,mac80211
crc_ccitt               1675  1 rt2800usb
usbhid                 40860  0 
hid                    83792  1 usbhid
usb_storage            49737  0 
firewire_ohci          24965  0 
firewire_core          52030  1 firewire_ohci
crc_itu_t               1715  1 firewire_core
ahci                   37838  2 
forcedeth              54248  0 


Funny thing that ffado-diag still claims "old 1394 stack present.... True":


FFADO diagnostic utility 2.999.0-
============================
(C) 2008 Pieter Palmers


=== CHECK ===
 Base system...
  kernel version............ 2.6.32-25-preempt
FIXME: implement test for RT kernel
   RT patched............... False
  old 1394 stack present.... True
  old 1394 stack loaded..... False
  old 1394 stack active..... False
  new 1394 stack present.... True
  new 1394 stack loaded..... True
  new 1394 stack active..... True
  /dev/raw1394 node present. False
.
.
=== REPORT ===
FireWire kernel drivers:

The new FireWire kernel stack is loaded. 
This stack is not supported by FFADO. Please use the old stack.


Still no success with that new stack but I'm happy to wait until things change.  Using old stack is ok.

---

### Post by Ansible on 2010-11-28
> **ajaaskel said:**
> 
#!/bin/sh
#Unloads all FireWire drivers and loads older FireWire stack 
#30.10.2010 by "ajaaskel" @ Ubuntu Forum
sudo modprobe -r video1394
sudo modprobe -r firewire-sbp2
sudo modprobe -r sbp2
sudo modprobe -r dv1394
sudo modprobe -r firewire-ohci
sudo modprobe -r raw1394
sudo modprobe -r ohci1394
sudo modprobe  raw1394
sudo modprobe  dv1394
sudo modprobe  sbp2
sudo modprobe  dv1394
sudo modprobe  video1394
echo
echo  '*** Load also ffado-dbus-server if you need ffado-mixer. ***'
echo
sleep 5


Thanks for that!  the script works for me too.  Good to have something to try without making permanent changes to config files.  Guess I'll try the blacklist thing next.

---

### Post by drummuch on 2011-01-11
hey there,
have a fresh ubuntustudio 10.10 installed, with ffado, jack,...all from the repository. With the workaround script by ajaaskel i load the old firewirestack. Al the audio stuff works fine, but i can't see no midi clients in jack! Is there anybody how works with midi on the audiofire?

---

