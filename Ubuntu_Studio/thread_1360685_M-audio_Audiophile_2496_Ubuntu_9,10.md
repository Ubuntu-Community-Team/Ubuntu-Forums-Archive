---
title: "M-audio Audiophile 24/96 Ubuntu 9,10"
date: 2009-12-21
forum: Ubuntu Studio
---

### Post by zuziaaa17 on 2009-12-21
Hi

I'm new user Ubuntu Studio 9,10, I have problems of my sound cart M-Audio audiophile 24/96.
How to setup driver ? I'm very vert easy user linux.
Sory my English is weak.
Thanks in advance for helpin.

aplay -l
```
**** Lista PLAYBACK urz&#261;dze&#324; ****
karta 0: SI7012 [SiS SI7012], urz&#261;dzenie 0: Intel ICH [SiS SI7012]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
``` sudo lspci -v | grep -i audio
```
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:0d.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
```

---

### Post by RaumTrug on 2009-12-23
Hello!

seems like the soundcard driver is not loaded or alsa misconfigurated. both should be done with that card out of the box

have you recompiled alsa yourself after some tutorial?

can you post the output of "lsmod | grep snd_ice1712" to see if the driver is loaded at all...?

---

### Post by number2301 on 2009-12-29
Sorry for the hijack but I'm having a very similar problem (and OP has been away for a while so he may not come back). I am running Ubuntu Desktop 9.10 and have the same sound card

aplay -l gives -

```
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

And sudo lspci -v | grep -i audio gives -

```
00:0c.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
	Kernel driver in use: VIA 82xx Audio

```

"lsmod | grep snd_ICE1712" gives nothing.

I have followed [this](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/) guide to upgrading ALSA to 1.22

I also had a quick run through the Sound Troubleshooting guide [here](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) which showed that ALSA had upgraded properly (with each having the same version number, 1.22). ALSA info script [here](http://pastebin.ca/1731112). Interestingly enough neither the pavucontrol or gnome-alsamixer commands worked.

I would be very grateful if anyone could point me in the right direction as this is about the only issue I've got with Ubuntu at the moment.

---

### Post by cchhrriiss121212 on 2009-12-30
Hi number2301, have you disabled your onboard sound device through BIOS?
You will also need to download Envy24 control and set the analog volume in that.

---

### Post by number2301 on 2009-12-30
On board sound card is disabled in the BIOS yes.

I am attempting to install the Envy24 controller and have managed to download alsa-tools but Envy needs GTK+ -

```
checking for ENVY24CONTROL... configure: error: Package requirements (gtk+-2.0 alsa >= 0.9.0) were not met:

No package 'gtk+-2.0' found

```

I then attempted to install GTK+ to find that it needs glib-2.0, atk, pango and cairo -

```

checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.21.3    atk >= 1.13.0    pango >= 1.20    cairo >= 1.6) were not met:

No package 'glib-2.0' found
No package 'atk' found
No package 'pango' found
No package 'cairo' found

```

cairo reported an error to do with PNG and pango said it couldn't install without at least one backend. At this point I gave up.

There must be an easier way than chasing down each of these programs?

Thanks for the help so far.

---

### Post by number2301 on 2009-12-30
Just thought I'd add this, I was following the main Ubuntu sound troubleshooting guide and it told me to put in the command, "lspci -v | less". This gave the result -

```
00:0c.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
        Subsystem: VIA Technologies Inc. Device d634
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at e800 [size=32]
        I/O ports at e400 [size=16]
        I/O ports at e000 [size=16]
        I/O ports at d800 [size=64]
        Capabilities: <access denied>

```

And I was wondering, is the access denied at the bottom significant?

---

### Post by cchhrriiss121212 on 2009-12-31
I'm not sure about that last post, but the easier way to get envy24 would be to try installing the ubuntu studio package from synaptic. This is especially recommended if you will be doing audio production. 
I'm using karmic studio so all I had to do with my delta-44 was set the volume as envy24 is included with the OS install. 
Good luck.

---

### Post by sgx on 2009-12-31
> **number2301 said:**
> On board sound card is disabled in the BIOS yes.

I am attempting to install the Envy24 controller and have managed to download alsa-tools but Envy needs GTK+ -

```
checking for ENVY24CONTROL... configure: error: Package requirements (gtk+-2.0 alsa >= 0.9.0) were not met:

No package 'gtk+-2.0' found

```

I then attempted to install GTK+ to find that it needs glib-2.0, atk, pango and cairo -

```

checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.21.3    atk >= 1.13.0    pango >= 1.20    cairo >= 1.6) were not met:

No package 'glib-2.0' found
No package 'atk' found
No package 'pango' found
No package 'cairo' found

```

cairo reported an error to do with PNG and pango said it couldn't install without at least one backend. At this point I gave up.

There must be an easier way than chasing down each of these programs?

Thanks for the help so far.
As mentioned, install apps using synaptic whenever possible. This will calculate, locate, and install all those dependancies automatically. It is extremely rare for it to fail. (When it does, often one of the apps you mention is involved, due to their being core apps, often updated, and not always in sync with one-another). I use maudio 24/96 pci every day.
Cheers

---

### Post by RaumTrug on 2010-01-01
I'm not really sure, but I think to recall that the ice1712 driver has problems with the standard installation of ubuntu when the sound card index is not zero - both people with problems here already have some "soundcard" (could be internal modem, also) with that index as can be seen by the "aplay -l" output. the driver defaults to device 0 unless another device number is given as module option, so when hda_intel or whatever already has that index, it fails loading!

so an approach to solve this would be either to deactivate the internal stuff (in bios), or manipulate the alsa-base.conf to use the audiophile as device hw:0 (by changing card priorities, the onboard will then be hw:1), or specifying index 1 as module option!

sorry, but I don't really know very well how to do that, and also I have a bad hangover from nye right now - I'll search the web/try to make something up for you when I feel better ;)

compiling a new alsa will be of no avail, the driver hasn't changed since years, so the one that comes with 9.10 should work very well (it does for me, I have the same card!); also envy24control won't "fix" it either, it's just some nice gui for the card that uses the alsa control interface to control levels/options, so it will only work, when the alsa driver is already loaded! but then it's nice to have.

so would you like to use the card with pure alsa (pulse disabled)? because then it should be better to put it to card number 0, so it will be the default card for programs that don't allow to choose the alsa output device! for pulse and jack it doesn't really matter what number it is...

---

### Post by number2301 on 2010-01-02
Right just to update on what I've done recently, I installed Ubuntu Studio through the software centre then alsa-tools through the command line (I do tend to use the software centre where I can but I didn't see anything called alsa-tools or envy24 there).

I have also disabled the onboard sound and onboard NIC through the BIOS (NIC may not be related but I don't use it anyway).

Under my Sound & Video menu I now have Envy24 Control but clicking on it does nothing. I'm running out of time today but when I get chance I'll try figure out how to uninstall and reinstall it.

If running it in pure alsa would get it working I'd be happy to go with that if you knew how? On a trial install of Ubuntu on the same machine I managed to get the soundcard mostly working but I lost my volume control next to the clock and I can't remember the various steps I went through to do it. I think I used Jack or Pulse audio there.

---

### Post by RaumTrug on 2010-01-02
whoa man, do it slow, and keep a .txt file (use gedit or whatever...) on your desktop where you note what kind of changes you did! sometimes hard for beginners that apply lots of changes in the system to keep track of what they have done, and then even harder for people who know the system better to guess what has been changed & got broken by it!

please don't be too trigger happy with fiddling at your system, unless you know what you're doing... ;)

that the card is working after onboard audio is disabled is just what I thought...if you keep it disabled and wish to use no other audio devices (plug&play usb stuff works fine for me, the m2496 is device 0 and the usb mic 1 if I plug it in), there'd be no need to modify alsa-base.conf!

when you enter "envy24control" in a terminal, you should see error messages that could be helpful.

also, "aplay -l" should list the card as card #0 when it's working & the driver is correctly loaded!

if the volume control applet in the task bar is gone, you probably removed/stopped pulseaudio, it is only working with pulse!...I removed my pulse because it had poor sound quality, errors with programs that only support alsa and used too much cpu; I use the envy24control tool when I need to change the volume, the "master" left & right are called dac1 & dac2!...the audiophile pulse stuff has a "bug" in karmic coala, btw: with pulse in a standard install you can only use digital output, to get the analog out working look here: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/63](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/63)

---

### Post by tgalati4 on 2010-01-02
Some folks with VIA chipset motherboards have problems with m-audio pci cards.  Don't know what the solution is.  I have an older Delta 66 card and it works fine with an Intel chipset motherboard using envy24control.

---

### Post by number2301 on 2010-01-03
Right, envy24control gives -

```
No ICE1712 cards found

```

Aplay -l gives -

```
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

But sudo lspci -v | grep -i audio still gives -

```
00:0c.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
	Kernel driver in use: VIA 82xx Audio

```

So I' not sure what's going on there.

Forgive my ignorance but I don't know the difference between a digital out and an analogue out. My speakers are connected through a twin phono lead (one of [these](http://www.coralphones.co.uk/F2SImages/3.5-2xRCA-PHONO-1M-EBAY1.jpg) with the twin end plugged into the soundcard) so I assume that is an analogue connection? Would you recommend following the bugfix previously posted? I thought I'd ask before going ahead with it seeing as I was told to slow down ;)

---

### Post by RaumTrug on 2010-01-03
yep, analogue out are the two rca jacks in the middle of the soundcard, between the breakout port (for digital & midi) and the two rca analog inputs!

btw. if sound already worked somewhere then it's no via problem, or new card problem (I've read m-audios produced after 2006 don't work with linux!), but just an alsa configuration/autodetection thing...

the pulseaudio fix is to be tried when alsa is running, the hierarchy is alsa ontop of the hardware, and pulse uses alsa to output the (mixed) sound of the applications! the fix enables the analogue outputs, and is needed to get any sound from pulse with that card & 9.10.

could you try in terminal "sudo modprobe snd-ice1712" and post the output?

to autoload the card when the above works without disabling onboard (which it seems like you haven't successfully as aplay -l still lists the onboard sound!), you could try to to add a line to "/modprobe.d/alsa-base.conf" at the bottom with "options snd-ice1712 model=audiophile index=0"

"cat /proc/asound/cards" in terminal should list 2 cards, the onboard & the audiophile

if that doesn't work then I'm at my wit's end, as said: I'm no expert, I've just read other posts around the web before I bought my card ;)

---

### Post by RaumTrug on 2010-01-03
sorry, I forgot something... if "modprobe" works for loading the alsa driver ("aplay -l" & "cat /proc/asound/cards" you can test it with jack & audacious/aqualung before trying to apply the pulse fix or stopping pulse to test pure alsa), you not only have to edit "alsa-base.conf" as above, but might also also have to add an extra line to "/etc/modules" with "snd-ice1712 model=audiophile index=0" to make the driver load at startup! I apologise, my bad...

if that all doesn't work there's another "fix" that was said to work for loading the alsa driver in a similliar case as yours, but is more complex & I don't really understand it (also no autodetection for an m-audio audiophile, and the above alsa-base/modules stuff didn't work somehow...), if you still get no alsa/sound we could try that...

---

### Post by number2301 on 2010-01-04
Just for clarity, on this install I have never had sound. I managed to get sound on a previous install of 9.10 (a trial run installed through WUBI) but did a few things at once and it was still patchy.

The card I have in was bought in 2004/5 for reference.

I did the bug fix listed above for the analogue outputs but no difference.

sudo modprobe snd-ice1712 gives -

```
sudo modprobe snd-ice1712
WARNING: All config files need .conf: /etc/modprobe.d/sound, it will be ignored in a future release.
FATAL: Module snd_ice1712 not found.

```

So I read back through the thread, sorry for being slow but this Linux stuff is very new to me and it's taking a while for me to catch on to what the various things mean. I just figured out that the VIA8237 listed under aplay -l is my internal card (the VIA confused me and I thought it was my 2496), so I switched my speaker cable to the internal card's output and I now have sound.

Not ideal I guess but it is kind of a solution. If you've any more advice following the results of the modprobe above it'd be gratefully received but I can live with this for now and do a bit of research/poking about to try figure out my M Audio problem.

Thanks all!

---

### Post by edmonds on 2010-01-28
hi RaumTrug

you  seem to know what you're on  about.
I've been using ubuntu studio for 3 years now with a audiophile 2496. Some updates lost sound but i got it back bu this time it seems impossible. 

tried many many suggestions over last couple of days.
still got the same problem.
pulse works - when i play a tune Pulse Volume controller recognises it and has a sound graphic bouncing up and down. (but dummy output)
i have an Envy/ice driver installed. (but Envy 24 controller blank)

But i have no sound card?:
aplay: device_list:223: no soundcards found...

my alsa-base.conf :
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N

can you  help?

tom

---

### Post by RaumTrug on 2010-01-28
yes I can try...first of all, I don't really know 100% what I'm talking about, I just superficial knowledge of linux sound; but as I got that card, I read a bit about problems with it & possible sollutions. can't solve them all, as I couldn't with the guy in this thread :P

first of all try in a terminal "cat /proc/asound/cards", if it displays the audiophile then you'll have chances to fix the pulseaudio stuff.

does jack work (via qjackctl)?

if both is positive read this thread: [http://ubuntuforums.org/showthread.php?t=1388065](http://ubuntuforums.org/showthread.php?t=1388065)

I link & describe the fix for pulse on 9.10 ubuntu (don't know about kubuntu) there. though I've heard from people applying it, that there's problems with skype afterwards, sorry, but that I can't solve.

otherwise sorry, then I can't really help

---

### Post by edmonds on 2010-01-28
hi
thanks for getting  back
cat: /proc/asound/cards: No such file or directory


thats my problem, pulse and ice seem to be ok but i my soundcard has disappeared and i don' tknow how to fin dit. 
i was hoping  the whole edit my alsa-base.conf would magically bring it back. but i dont know what to delete and what to replace it with (if it has anything  to do with alsa-conf)

tom

---

### Post by edmonds on 2010-01-29
hi
i tried both .conf options here:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/63](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/63)

but still get no sound and still dont seem to have a soundcard:
aplay: device_list:223: no soundcards found...

how do you  get a soundcard found?

---

### Post by RaumTrug on 2010-01-29
yes, the fix there is only concerned with getting pulse working, not the underlying alsa driver.

for example, when I type "cat /proc/asound/cards" I get:

```

 0 [M2496          ]: ICE1712 - M Audio Audiophile 24/96
                      M Audio Audiophile 24/96 at 0xd400, irq 3

```stating that alsa has detected the card & loaded its drivers. if that file isn't found, that didn't happen!

seems like either alsa or the detecting udev/devicekit is broken somehow! sorry, I can't help with that, it's "above my horizon" ;)

you could check with "lspci | grep audio" if the card is detected at all, for me it sais

```

02:0d.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)

```if that's there for you, too, then alsa could be broken somehow, if not (and even the "lspci" list without grep gives no ice1712/VIA chip), then maybe the card is broken, or it is a bug in pci detection? don't know...

---

### Post by edmonds on 2010-01-29
i suppose it could be alsa or a broken card.
at the moment i get:
cat: /proc/asound/version: No such file or directory
so i seem to have lost alsa.
which is odd i went through this:
[http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)
and upgraded it a few days ago.
guess i'll try again.

and yet i can start and stop alsa:
sudo /etc/init.d/alsa-utils start
* Setting up ALSA...  [OK]

---

### Post by AutoStatic on 2010-01-30
> **edmonds said:**
> which is odd i went through this:
[http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)
and upgraded it a few days ago.That howto is ugly and intended for 9.04. You probably broke your ALSA stack.
> **edmonds said:**
> guess i'll try again.Good luck, it probably won't help. Best is to find out which files 'make install' copied over and to remove them all and reinstall the alsa packages from Synaptic.

---

### Post by edmonds on 2010-01-30
sorry wrong link:
[http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)

the problem with synaptic is what do you  remove and install?
i have:
libesd-alsa0
alsa-utils
gnome-alsamixer
alsa-oss
mcp-plugins
alsa-base
libsox-fmt-alsa
libasound2
libasound2-dev
libasound2-plugins
linux-sound-base
gstreamer0.10-alsa
alsa-tools
qamix
a2jmidid
libclalsadrv1
bluez-alsa
aconnectgui
sox
liblash2
libao2
ladcca2

what do you  think?

---

### Post by AutoStatic on 2010-01-30
I think you should first check what the **make install** command did, what it installed and where. And then install linux-backports-modules-karmic with Synaptic.

---

### Post by edmonds on 2010-01-30
i don't know what make install did. presumably it installed those things??

i took my card out and lspci -v | less
whic got rid of below

05:01.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
        Subsystem: VIA Technologies Inc. Device d634
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at ec00 [size=32]
        I/O ports at e880 [size=16]
        I/O ports at e800 [size=16]
        I/O ports at e480 [size=64]
        Capabilities: <access denied>

then i put my card in again  and lspci -v | less
which brought it back.

therefore i think that must be my soundcard. though its a bit worrying that it doesn't mention m-audio anywhere. or is this just the driver. shulod there be something  else?

i have installed  install linux-backports-modules-karmic. still no sound.

---

### Post by AutoStatic on 2010-01-30
**make install** does not install any packages. It installs things that you compiled with **./configure** and **make**.

And the Via card lspci shows is your m-audio I think, but I don't have such a card so can't tell for sure.

That's also why I pull my hands off of this one. I don't own such a card and also I don't feel like clearing up [somebody else's mess]("http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/#comment-521").

---

### Post by RaumTrug on 2010-01-30
yes, it is the audiophile (the via ice1712 card).

and autostatic is right: if you install stuff manually with make install, it bypasses apt/synaptic, and apt doesn't know which files were there, which ones were overwritten etc...it's generally bad to do that on ubuntu, it can break the system, and I guess it's even worse for dist-upgrades. if you really need to compile something yourself, you can use "checkinstall", so the files get remembered as package in synaptic! "make install" just copies the compiled files, blindly overwriting what's been there before!

one possibility that I don't really know wether it works and how would be "make uninstall" to remove the new/overwritten files, and then "reinstall" the right packages with apt/synaptic...but you'd have to know which packages are affected, and take care that you don't break the running system with "make uninstall" - just like make install blindly copies the files, make uninstall blindly removes them, so I'd keep my hands off that! I've done such with the jack server successfully, but with kernel modules & configuration files like alsa consists of, it is probably dangerous... :(

easiest would be to backup all data and reinstall ubuntu completely! if you got a seperate /home/ partition, you could have your preferences, files etc. preserved, but you should backup for safety anyways.

---

### Post by edmonds on 2010-01-30
i suppose i could do a reinstall... god the thought of it, all that relearning  how i did stuff expecially wine and vm. still 3 years without an install is a year better than xp, 3 years better than 98, etc.. 

that alsa upgrade thing  didn't really make any difference. pulse worked, alsa didn't and i couldn't find my soundcard before i did it, same now.

i wonder what i will forget to backup  this time.

thanks for all your help

---

### Post by AutoStatic on 2010-01-30
> **edmonds said:**
> pulse worked, alsa didn't and i couldn't find my soundcard before i did it, same now.PulseAudio uses ALSA as its backend. So when PulseAudio works, ALSA works also.

---

### Post by edmonds on 2010-02-08
Audiophile Sound Card works!

So, reinstalled ubuntu studio, 9.10. Still No sound, no sign of card.
Removed sound card, turned on onboard sound card - sound at last.
While looking  for new linux friendly sound card found this:
[http://www.linuxquestions.org/questions/ubuntu-63/no-sound-in-ubuntu-studio-with-m-audio-delta-44-781558/](http://www.linuxquestions.org/questions/ubuntu-63/no-sound-in-ubuntu-studio-with-m-audio-delta-44-781558/)
Took card round to friends to see if it actually worked - he couldn't be bothered to check.
So put card back in: No sound, but now card is found!
Applied edit to /usr/share/alsa/cards/ICE1712.conf as per link:
ie:

ICE1712.pcm.front.0 {
@args [ CARD ]
@args.CARD {
type string
}
type route
ttable.0.0 1
ttable.1.1 1
slave.pcm {
type hw
card $CARD
}
slave.format S32_LE <---- add this
slave.channels 10 <---- add this
}

reboot - Sound!!!!
blimey.

---

### Post by Calamardo on 2010-02-23
This: [http://ubuntuforums.org/showthread.php?t=1268856](http://ubuntuforums.org/showthread.php?t=1268856) worked for me in Ubuntu Studio Karmic. Took me so much time (and headaches) to find it. I hope that work for everyone with this problem in the Delta 2496.

---

### Post by edmonds on 2010-05-07
ok
upgraded  to 10.04
no sound again!

had to redo what i  had done before, ie:
terminal>cd .., cd .., cd /usr/share/alsa/cards/
sudo gedit ICE1712.conf

then add
slave.format S32_LE
slave.channels 10

between the last 2 brackets:
ICE1712.pcm.front.0 {
@args [ CARD ]
@args.CARD {
type string
}
type route
ttable.0.0 1
ttable.1.1 1
slave.pcm {
type hw
card $CARD
}
slave.format S32_LE
slave.channels 10
}

reboot - Sound!!!!

---

### Post by Stason on 2010-05-07
Seems to be an issue with alsa install. Everytime it upgrades it loses these conf settings. Anyone knows how to complain to alsa developers about this bug?

---

### Post by sgx on 2010-05-07
> **Stason said:**
> Seems to be an issue with alsa install. Everytime it upgrades it loses these conf settings. Anyone knows how to complain to alsa developers about this bug?
Its actually better to require running
sudo alsaconf
or other system sound configuration, as there is
no other way to insure the new code is properly
detected and configured. While this might drive
a new user crazy at first, we all were new, once
(I'm new almost every Monday ;)and have to run the learning gauntlet.
 
You can blacklist an unused soundcard/chip, and
this will survive new alsa updates, and ease detection of
the m-audio card. The blacklist entry for my intel soundchip is

blacklist snd_intel8x0

its the first and only line in the textfile

/etc/modprobe.d/blacklist

Running the command lsmod will list the system kernel modules.
Once blacklisted, the module will not be listed.

Cheers

---

### Post by rz2k on 2010-05-12
> **edmonds said:**
> ok
upgraded  to 10.04
no sound again!

had to redo what i  had done before, ie:
terminal>cd .., cd .., cd /usr/share/alsa/cards/
sudo gedit ICE1712.conf

then add
slave.format S32_LE
slave.channels 10

between the last 2 brackets:
ICE1712.pcm.front.0 {
@args [ CARD ]
@args.CARD {
type string
}
type route
ttable.0.0 1
ttable.1.1 1
slave.pcm {
type hw
card $CARD
}
slave.format S32_LE
slave.channels 10
}

reboot - Sound!!!!
Thanks for that, really works.

---

### Post by cpeachey on 2010-06-24
Thanks to the various tips found here and other threads I now have my Audiophile2496 card working.
I did a clean install of Ubuntustudio 10.04, removed Alsa sound server and several progs with it, Installed AlsaPlayer Alsa,common and GTK.
Finally Envy24 and Audacity.
(Hardware is quadcore AMD64/3Gbram) - probably a bit over the top.
Did not have to change anything using Terminal.
Chris:lolflag:

---

### Post by sgx on 2010-06-24
Hi, if you get a chance, could you run the lspci command, there should be a line similar to this, stating the maudio cards revision number.

03:07.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)


I'm hoping versions other than rev 02 work.
Nice to see a quadcore being put to good use. Its not over the top,
once you set up your studio, all those cpu cycles will be assimilated ;)
Cheers

---

### Post by cpeachey on 2010-06-25
Output of pclsi as follows
Chris

chris@Mediacentre:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:06.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
chris@Mediacentre:~$

Looks like another 02 revision.
Card is a new purchase.

---

### Post by sgx on 2010-06-26
Thanks, I should get a spare for good luck :guitar:

---

### Post by horaz on 2010-10-04
It doesn't work!


> **edmonds said:**
> ok
upgraded  to 10.04
no sound again!

had to redo what i  had done before, ie:
terminal>cd .., cd .., cd /usr/share/alsa/cards/
sudo gedit ICE1712.conf

then add
slave.format S32_LE
slave.channels 10

between the last 2 brackets:
ICE1712.pcm.front.0 {
@args [ CARD ]
@args.CARD {
type string
}
type route
ttable.0.0 1
ttable.1.1 1
slave.pcm {
type hw
card $CARD
}
slave.format S32_LE
slave.channels 10
}

reboot - Sound!!!!

I don't know if this help, but this is my ICE1712.conf:

#
# Configuration for the ICE1712 (Envy24) chip
#

# default with dmix & dsnoop


ICE1712.pcm.default {
	@args [ CARD ]
	@args.CARD {
		type string
	}
	type asym
	playback.pcm {
		type plug
		slave.pcm {
			@func concat
			strings [ "dmix:" $CARD ",FORMAT=S32_LE" ]
		}
	}
	capture.pcm {
		type plug
		slave.pcm {
			@func concat
			strings [ "dsnoop:" $CARD ",FORMAT=S32_LE" ]
		}
	}
}

<confdir:pcm/front.conf>

ICE1712.pcm.front.0 {
	@args [ CARD ]
	@args.CARD {
		type string
	}
	type route
	ttable.0.0 1
	ttable.1.1 1
	slave.pcm {
		type hw
		card $CARD
	}
slave.format S32_LE
slave.channels 10
}	

<confdir:pcm/surround40.conf>

ICE1712.pcm.surround40.0 {
	@args [ CARD ]
	@args.CARD {
		type string
	}
	type route
	ttable.0.0 1
	ttable.1.1 1
	ttable.2.2 1
	ttable.3.3 1
	slave.pcm {
		type hw
		card $CARD
	}
}	

<confdir:pcm/surround41.conf>
<confdir:pcm/surround50.conf>
<confdir:pcm/surround51.conf>

ICE1712.pcm.surround51.0 {
	@args [ CARD ]
	@args.CARD {
		type string
	}
	type route
	ttable.0.0 1
	ttable.1.1 1
	ttable.2.2 1
	ttable.3.3 1
	ttable.4.4 1
	ttable.5.5 1
	slave.pcm {
		type hw
		card $CARD
	}
}

<confdir:pcm/iec958.conf>

ICE1712.pcm.iec958.0 {
	@args [ CARD AES0 AES1 AES2 AES3 ]
	@args.CARD {
		type string
	}
	@args.AES0 {
		type integer
	}
	@args.AES1 {
		type integer
	}
	@args.AES2 {
		type integer
	}
	@args.AES3 {
		type integer
	}
	type asym
	playback.pcm {
		type hooks
		slave.pcm {
			type route
			ttable.0.8 1
			ttable.1.9 1
			slave.pcm {
				type hw
				card $CARD
			}
			slave.format S32_LE
			slave.channels 10
		}
		hooks.0 {
			type ctl_elems
			hook_args [
				{
					interface PCM
					name "IEC958 Playback PCM Stream"
					lock true
					preserve true
					value [ $AES0 $AES1 $AES2 $AES3 ]
				}
			]
		}
	}
	capture.pcm {
		type route
		ttable.0.8 1
		ttable.1.9 1
		slave.pcm {
			type hw
			card $CARD
		}
# FROM INTERNET, OCTOBER 4th, 2010
		slave.format S32_LE
		slave.channels 12
	}
}

Something wrong? Answer simply, please: I'm not english..:(
Horaz
PS: I put in blacklist the OTHER audio device. Alsamixer shows me, now, only Audiophile.
And, of course, thank you all, anyway.

---

### Post by horaz on 2010-10-04
[QUOTE=horaz;9923518]It doesn't work!


[...]
	capture.pcm {
		type route
		ttable.0.8 1
		ttable.1.9 1
		slave.pcm {
			type hw
			card $CARD
		}
# FROM INTERNET, OCTOBER 4th, 2010
		slave.format S32_LE
		slave.channels 12
	}
}

Something wrong? Answ[...]

I'm so sorry, I wrote "slave.channels 12".
I fixed, writing "10", but it doesen't work anyway. Thanx for your time.
Horaz :(

---

### Post by Pablo_F on 2010-10-04
You have to reboot the computer after editing that file.

Then I suggest you install pulseaudio volume control: 

sudo apt-get install pavucontrol

Applications -> Sound and Video -> Pulseaudio volume control

Configuration tab: Select Analog Stereo Output for the ICE1712 (Envy24) card (your m-audio 2496 in this case).

Cheers! Pablo

---

### Post by horaz on 2010-10-04
Still in misery!
I've rebooted, of course. Nothing. I already have pavucontrol, although I couldn't find it. But, anyway, I launched it by terminal. I did what you said, although I've tried many other settings, in alsamixer and in Envy24.
Nothing to do.
Do you need some screenshot?
Cheers, Horaz

---

### Post by Pablo_F on 2010-10-04
So you have an stereo analog output in pavucontrol config tab. Good. I had not that option until I added those two lines to /usr/share/alsa/cards/ICE1712.conf and rebooted my computer.


Don't use alsamixer, use envy24control. Envy24control is specific for those cards and it replaces alsamixer.

You set the levels of the DAC and ADC converters in the "analog volume" tab.  

I am using the last version of envy24cotrol (mudita) so the aspect can be different from yours but these are my working settings and they should work for you too. 

In the playback tab of pavucontrol, make sure the pulseaudio clients are streaming the sound through the m-audio, not through the onboard (if any). If you will not use it, disable the onboard card form the BIOS,

HTH, Pablo

[ATTACH]171303[/ATTACH]

[ATTACH]171304[/ATTACH]

---

### Post by horaz on 2010-10-05
Step by step, we're going on the goal...
I tried to kill pulseaudio, but it was still there, at rebooting. Although, now I CAN HEAR. Maybe pavucontrol did do his job! Anyway, Last 2 problems, here they are:
1)Got some problems with recording. If I talk in my mic, i see lights pulseing (?) in the mixer (hardware), then they pulse again in Envy; ok. But NO SOUND from the system. "Audacity" plays my mp3, but it can't "hear" my voice.
2) Some stupid things about mono and stereo, but this can wait.

*****************

I'm on analog. DAC & Friends are EQUAL to your pictures.
Excuse me for my English, and thanx again.

---

### Post by tobsco on 2010-10-31
I haven't read all the posts above so sorry if this isn't relevant but to get my audiophile 24/96 working I have to follow the following steps  taken from post #52 on [URL="http://https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/+index?comments=all"]https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/+index?comments=all
[/URL]
This has worked for me on 10.04 and 10.10

1) Create the new udev rule in "/lib/udev/rules.d/90-pulseaudio.rules".
```
sudo gedit /lib/udev/rules.d/90-pulseaudio.rules
```
adding

SUBSYSTEMS=="pci", ATTRS{vendor}=="0x1412", ATTRS{device}=="0x1712", ENV{PULSE_PROFILE_SET}="via-ice1712.conf"

2) Create the static profile definition file "/usr/share/pulseaudio/alsa-mixer/profile-sets/via-ice1712.conf".
```
sudo gedit /usr/share/pulseaudio/alsa-mixer/profile-sets/via-ice1712.conf
```

#### Begin via-ice1712.conf ####
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as
# published by the Free Software Foundation; either version 2.1 of the
# License, or (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

; Via ICE1712 multi-channel audio chipset
;
; This chipset has up to four stereo pairs of input and four stereo pairs of
; output, named channels 1 to 8. Also available are separate S/PDIF stereo
; channels (input and output), and a separate "system-out" stereo jack that
; supports 6-channel hardware mixing.
;
; The S/PDIF stereo channels can be controlled via the mixer for hw:0, and
; additionally, the 8 main outputs can be loop-routed to a separate stereo
; input pair, available as channels 11 and 12.
;
; Many cards available from vendors do not expose all channels from this chip
; to an external port, which effectively reduces the number of channels that
; are useful to the user. However, the ALSA driver still exposes all channels
; even if they are not connected.
;
; We knowingly only define a subset of the theoretically possible
; mapping combinations as profiles here.
;
; See default.conf for an explanation on the directives used here.

[General]
auto-profiles = no

[Mapping analog-mch-in]
description = Analog Multi-Channel Main Input
device-strings = hw:%f,0
#channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe,side-left,side-right,aux0,aux1,aux2,aux3
channel-map = aux0,aux1,front-left,front-right,aux2,aux3,aux4,aux5,aux6,aux7,aux8,aux9
direction = input

[Mapping analog-mch-out]
description = Analog Multi-Channel Main Output
device-strings = hw:%f,0
#channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe,side-left,side-right,aux0,aux1
channel-map = front-left,front-right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7
direction = output

[Mapping digital-stereo]
description = Digital Stereo Input/Output
#device-strings = hw:%f,1
device-strings = iec958:%f
channel-map = left,right
direction = any

[Mapping analog-system-out]
description = Analog Stereo System-Out
device-strings = hw:%f,2
channel-map = left,right
direction = output

[Profile output:mch]
description = Multi-Channel Output Active (Digital Disabled)
output-mappings = analog-mch-out analog-system-out
input-mappings =
priority = 90
skip-probe = yes

[Profile output:mch+input:mch]
description = Multi-Channel Input/Output (Digital Disabled)
output-mappings = analog-mch-out analog-system-out
input-mappings = analog-mch-in
priority = 100
skip-probe = yes

[Profile output:spdif]
description = Digital Output (Multi-Channel Disabled)
output-mappings = digital-stereo analog-system-out
input-mappings =
priority = 80
skip-probe = yes

[Profile output:spdif+input:spdif]
description = Digital Input/Output (Multi-Channel Disabled)
output-mappings = digital-stereo analog-system-out
input-mappings = digital-stereo
priority = 90
skip-probe = yes

[Profile output:system]
description = System Output Only
output-mappings = analog-system-out
input-mappings =
priority = 60
skip-probe = yes
#### End via-ice1712.conf ####

---

### Post by okropnick on 2010-11-13
Solution given by Tobsco is working perfectly also for Terratec DMX6Fire 24/96. Thank you!

---

