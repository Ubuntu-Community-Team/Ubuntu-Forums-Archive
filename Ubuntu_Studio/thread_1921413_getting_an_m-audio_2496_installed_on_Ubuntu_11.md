---
title: "getting an m-audio 24/96 installed on Ubuntu 11"
date: 2012-02-06
forum: Ubuntu Studio
---

### Post by nazaroo2 on 2012-02-06
This should be a "no trouble" installation:

The m-audio 24/96 is installed, and the onboard soundcard shut off. 

(1)  I booted up on the Ubuntu 11 side.

I didn't get sound, but running aplay / arecord -l gives:

```
# aplay -l
**** List of PLAYBACK Hardware Devices ****
[COLOR=Blue]**card 0: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]**[/COLOR]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: RPx400 [RPx400], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: RPx400 [RPx400], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 

~# arecord -l
**** List of CAPTURE Hardware Devices ****
[COLOR=Blue]**card 0: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]**[/COLOR]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: RPx400 [RPx400], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: RPx400 [RPx400], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@ben-OptiPlex-330:~# 
```Clearly Ubuntu 11 has found the card automatically, and correctly identified it.

However,

(2)  Alsaplayer produces no sound.

(3)  Youtube makes no sound.

[COLOR=Black]**(4)  Jack doesn't boot properly:**[/COLOR]
hw:0 seems to be the new (m-audio) card:

_**On list of options for Input/Output Device:**_

[COLOR=Blue]hw:0  M Audio Audiophile 24/96

hw:1  RPx400[/COLOR]

I have selected hw:0 for both input and output.

(5)  JACK gives an error dialog box on startup:
[COLOR=Blue]
D-BUS: JACK server could not be started. Sorry [cancel][/COLOR]

Then:

[COLOR=Blue]Could not connect to JACK server as client.
- Overall operation failed.
- Unable to connect to server.
Please check the messages window for more info.[/COLOR] [COLOR=Blue] [cancel][/COLOR]



In the JACK msg window is this:


```
  [COLOR=#999999]17:28:17.199 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]17:28:17.204 Statistics reset.[/COLOR]
 [COLOR=#cccc99]17:28:17.211 ALSA connection change.[/COLOR]
 [COLOR=#999999]17:28:17.254 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]17:28:17.280 ALSA connection graph change.[/COLOR]
 [COLOR=#ff0000]17:31:15.168 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 Mon Feb  6 17:31:14 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Mon Feb  6 17:31:14 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Mon Feb  6 17:31:14 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Mon Feb  6 17:31:14 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Mon Feb  6 17:31:14 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Mon Feb  6 17:31:14 2012: driver "alsa" selected
 Mon Feb  6 17:31:14 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Mon Feb  6 17:31:14 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Mon Feb  6 17:31:14 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Mon Feb  6 17:31:14 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Mon Feb  6 17:31:14 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Mon Feb  6 17:31:14 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Mon Feb  6 17:31:14 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Mon Feb  6 17:31:14 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Mon Feb  6 17:31:14 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Mon Feb  6 17:31:14 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Mon Feb  6 17:31:14 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Mon Feb  6 17:31:14 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Mon Feb  6 17:31:14 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Mon Feb  6 17:31:14 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Mon Feb  6 17:31:14 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Mon Feb  6 17:31:14 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Mon Feb  6 17:31:14 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Mon Feb  6 17:31:14 2012: Saving settings to "/root/.config/jack/conf.xml" ...
 Mon Feb  6 17:31:14 2012: Starting jack server...
 Mon Feb  6 17:31:14 2012: JACK server starting in realtime mode with priority 10
 Mon Feb  6 17:31:15 2012: control device hw:0
 Mon Feb  6 17:31:15 2012: control device hw:0
 Mon Feb  6 17:31:15 2012: [1m[31mERROR: Failed to acquire device name : Audio0 error : Input/output error[0m
 Mon Feb  6 17:31:15 2012: [1m[31mERROR: Audio device hw:0 cannot be acquired, trying to open it anyway...[0m
 Mon Feb  6 17:31:15 2012: creating alsa driver ... hw:0|hw:0|1024|2|44100|2|0|nomon|swmeter|-|32bit
 Mon Feb  6 17:31:15 2012: control device hw:0
 Mon Feb  6 17:31:15 2012: [1m[31mERROR: the playback device "hw:0" is already in use. Please stop the application using it and run JACK again[0m
 Mon Feb  6 17:31:15 2012: [1m[31mERROR: Cannot initialize driver[0m
 Mon Feb  6 17:31:15 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m
 Mon Feb  6 17:31:15 2012: [1m[31mERROR: Failed to open server[0m
 [COLOR=#ff0000]17:32:22.071 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started

```Whats it all about Alfie?

---

### Post by nazaroo2 on 2012-02-06
lspci gives the following:

```
# lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 0a)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 0a)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787 Gigabit Ethernet PCI Express (rev 02)
[COLOR=Blue]**03:02.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)**[/COLOR]
~# 

```

Which looks about the same as in Ubuntu 10.

---

### Post by nazaroo2 on 2012-02-07
I forgot to do the "modules state" test.  Here it is:

```
~# sudo lshw -C multimedia
  [COLOR=Blue]*-multimedia            
       description: Multimedia audio controller
       product: **ICE1712** [**Envy24**] PCI Multi-Channel I/O Controller
       vendor: VIA Technologies Inc.
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 02
       width: 32 bits
       **clock: 33MHz**
       capabilities: pm bus_master cap_list
       configuration: **driver=ICE1712** **latency=64**
       resources:** irq:18** ioport:cca0(size=32) ioport:cc80(size=16) ioport:cc90(size=16) ioport:ccc0(size=64)[/COLOR]
 ~# 

```This appears slightly different than under Ubuntu 10. 
The notice [COLOR=Blue]**"Unclaimed"**[/COLOR] seems to have vanished.

Here the driver has at least been identified, **but it is unclear whether it is actually installed.**

It would be appreciated if anyone knew how to check that the driver/module was installed, 
or could tell me how to install it.
The other issue is that the 'CLOCK' says 33MHz, but it doesn't list a sampling rate.

---

### Post by nazaroo2 on 2012-02-07
I've just tried running ALSAMIXER in a terminal, and then tried selecting the audio card,
and then turning up the volume sliders on all the things, except for the S/PDIF lines.
The reason I avoided turning those on/up, is because in another thread I had read that
turning them on turns off the other outputs....

Here is what Alsamixer looks like at the moment:

[IMG]http://1.bp.blogspot.com/-Io0UoGlEwOI/TzDDyxFzRHI/AAAAAAAAAz0/6VFSHfCBH0k/s640/Screenshot-alsamixer-maudio.png[/IMG]

I am now getting sound from ALSAPLAYER, over the speaker monitors! Yay!

---

### Post by nazaroo2 on 2012-02-07
Uh oh.

**JACK Control **still seems to die in the water.

Both Input and Output are set to hw:0, which is reported as the M Audio Audiophile 24/96.

Here is the startup msg:

```
   [COLOR=#999999]00:58:19.142 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]00:58:19.171 Statistics reset.[/COLOR]
 [COLOR=#cccc99]00:58:19.214 ALSA connection change.[/COLOR]
 [COLOR=#999999]00:58:19.552 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]00:58:19.561 ALSA connection graph change.[/COLOR]

```REBOOTING the system completely may have fixed JACK, because it now seems willing to go into "START":

After hitting "Start", and ignoring the first program starting msg,
I get this:

```
    [COLOR=#999999]01:01:43.053 D-BUS: JACK server is starting...[/COLOR]
 [COLOR=#999999]Cannot connect to server socket err = No such file or directory[/COLOR]
 [COLOR=#999999]Cannot connect to server socket[/COLOR]
 [COLOR=#999999]jack server is not running or cannot be started[/COLOR]
 [COLOR=#999999]01:01:43.080 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: Saving settings to "/root/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: Saving settings to "/root/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: Saving settings to "/root/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: Saving settings to "/root/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: Saving settings to "/root/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: driver "alsa" selected[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: Saving settings to "/root/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: Saving settings to "/root/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: Saving settings to "/root/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: Saving settings to "/root/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: Saving settings to "/root/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: Saving settings to "/root/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: Saving settings to "/root/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: Saving settings to "/root/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: Saving settings to "/root/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: Saving settings to "/root/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: Saving settings to "/root/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: Saving settings to "/root/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: Saving settings to "/root/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: Saving settings to "/root/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: Saving settings to "/root/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: Saving settings to "/root/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: Saving settings to "/root/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: Saving settings to "/root/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: Starting jack server...[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: JACK server starting in realtime mode with priority 10[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: control device hw:0[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: control device hw:0[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: Acquired audio card Audio0[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: control device hw:0[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: ALSA: final selected sample format for capture: 32bit integer little-endian[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: ALSA: use 2 periods for capture[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: ALSA: final selected sample format for playback: 32bit integer little-endian[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:42 2012: ALSA: use 2 periods for playback[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:43 2012: graph reorder: new port 'system:capture_1'[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:43 2012: New client 'system' with PID 0[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:43 2012: graph reorder: new port 'system:capture_2'[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:43 2012: graph reorder: new port 'system:capture_3'[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:43 2012: graph reorder: new port 'system:capture_4'[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:43 2012: graph reorder: new port 'system:capture_5'[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:43 2012: graph reorder: new port 'system:capture_6'[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:43 2012: graph reorder: new port 'system:capture_7'[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:43 2012: graph reorder: new port 'system:capture_8'[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:43 2012: graph reorder: new port 'system:capture_9'[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:43 2012: graph reorder: new port 'system:capture_10'[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:43 2012: graph reorder: new port 'system:capture_11'[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:43 2012: graph reorder: new port 'system:capture_12'[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:43 2012: graph reorder: new port 'system:playback_1'[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:43 2012: graph reorder: new port 'system:playback_2'[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:43 2012: graph reorder: new port 'system:playback_3'[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:43 2012: graph reorder: new port 'system:playback_4'[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:43 2012: graph reorder: new port 'system:playback_5'[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:43 2012: graph reorder: new port 'system:playback_6'[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:43 2012: graph reorder: new port 'system:playback_7'[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:43 2012: graph reorder: new port 'system:playback_8'[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:43 2012: graph reorder: new port 'system:playback_9'[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:43 2012: graph reorder: new port 'system:playback_10'[/COLOR]
 [COLOR=#9999cc]01:01:46.334 JACK connection change.[/COLOR]
 [COLOR=#999933]01:01:46.335 Server configuration saved to "/root/.jackdrc".[/COLOR]
 [COLOR=#999999]01:01:46.336 Statistics reset.[/COLOR]
 [COLOR=#999999]01:01:46.348 Client activated.[/COLOR]
 [COLOR=#cc9966]01:01:46.380 JACK connection graph change.[/COLOR]
 [COLOR=#999999]Tue Feb  7 01:01:46 2012: New client 'qjackctl' with PID 1618[/COLOR]

```Running Patchage caused a panic at first, 
since the System Output did not appear, until I figured I had to scroll around because it was off-screen in window.
But System Input shows 12 captures!!! and System Output shows 10 playbacks!....

Running Hydrogen automatically hooked it up to playback 1/2.
It took about 10 minutes of fiddling, but I got Hydrogen to play some drum beat,
by using Nautilus to copy Hydrogen files over to the new Partition, 
and then further dropping a link to it in the Nautilus left bar, 
then loading first a drum pattern, and then (after panicking again) loading a drumset.

I then ran Ardour, and fixed a few duplicated connections, and got drum sounds in monitor:

[IMG]http://2.bp.blogspot.com/-6BQ7BqmekdI/TzDRFuLZjzI/AAAAAAAAAz8/K1t96Ty-8_8/s640/Patchage+at+2012-02-07+01:20:57.png[/IMG]

------------------------------


UPDATE:
I just tested the System Capture (1, 2) and they seem to work fine.

There is just the disturbing problem of 12 inputs and 10 outputs, which doesn't make any real sense.

Will this cause a problem in the future?  Can it be fixed?

---

### Post by nazaroo2 on 2012-02-07
I forgot to do a lsmod (list modules?) test,
so I don't know what it looked like in earlier stages here, 
but here it is now:

```
~# lsmod
Module                  Size  Used by
snd_seq_dummy          12686  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
vesafb                 13489  1 
binfmt_misc            17292  1 
nvidia              10390874  42 
snd_ice1712            65102  3 
snd_ice17xx_ak4xxx     13163  1 snd_ice1712
snd_ak4xxx_adda        18464  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427             13969  1 snd_ice1712
snd_usb_audio         100930  0 
snd_ac97_codec        106082  1 snd_ice1712
snd_pcm                80435  5 snd_ice1712,snd_usb_audio,snd_ac97_codec
ppdev                  12849  0 
ac97_bus               12642  1 snd_ac97_codec
snd_i2c                13863  2 snd_ice1712,snd_cs8427
snd_mpu401_uart        13865  1 snd_ice1712
snd_page_alloc         14108  1 snd_pcm
snd_hwdep              13276  1 snd_usb_audio
snd_usbmidi_lib        24558  1 snd_usb_audio
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  11 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
snd_rawmidi            25241  3 snd_mpu401_uart,snd_usbmidi_lib,snd_seq_midi
joydev                 17393  0 
dcdbas                 14098  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  4 snd_seq_dummy,snd_seq_midi,snd_seq,snd_rawmidi
snd                    55902  22 snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_usb_audio,snd_ac97_codec,snd_pcm,snd_i2c,snd_mpu401_uart,snd_hwdep,snd_usbmidi_lib,snd_seq,snd_rawmidi,snd_timer,snd_seq_device
psmouse                63474  0 
serio_raw              12990  0 
soundcore              12600  1 snd
parport_pc             32114  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
ahci                   21634  4 
libahci                25761  1 ahci
tg3                   132972  0 
  # 
```

---

### Post by nazaroo2 on 2012-02-07
I have also just installed the following, taken from [the Ubuntu Studio page here:]("https://help.ubuntu.com/community/UbuntuStudioPreparation#Real-Time_Support")

First I did the "must have" installs from the terminal:

> sudo apt-get install ardour audacious hydrogen jackd jack-rack 
qjackctl seq24 vkeybd zynaddsubfx patchage vlc kino pitivi 
acidrip ubuntu-restricted-extras ubuntustudio-menu **[COLOR=Red]gcdmaster[/COLOR]**
The last item on the list didn't install, and some others were already installed by me.



```
**Effect Plugins, Instruments and Codecs**

 Install the LADSPA plugins so you get some effect plugins for your audio applications to use. 
For audio processing: 
sudo apt-get install blop caps cmt fil-plugins rev-plugins swh-plugins tap-pluginsFor synthesizers: 
sudo apt-get install blepvco mcp-plugins ominsInstall the DSSI host and plugins: 
sudo apt-get install dssi-host-jack dssi-example-plugins fluidsynth-dssi hexter xsynth-dssi
```But I haven't tested any of this.

Other items on that page don't seem to install, such as the video codecs etc. (its an install page meant for Ubuntu 10).

---

### Post by sgx on 2012-02-07
Hi, in qjackctl, I choose the ICE1712 entry for both
Input Device > and Output Device 

When using the digitech unit, choose it as the Input Device >
and the mAudio as Output Device >

A dedicated mixer for maudio cards is called  envy24control,
synaptic can install it, it maybe in the alsa-tools-gui
package, if notseparate.

The line-level rca connectors can take common adaptors to receive
1/4" or 1/8" Y cables on the card 

The ladspa fx you installed, will be noticed by ardour, qtractor,
audacity, hydrogen, jack-rack, and others. Each app will have
some menu or gui option to display and select the plugins.

In the qjackctl connect gui, the alsa panel will show
M Audio Audiophile 24/96. A linux synthesizer or other instrument
with midi capabilities will show on the right half, so you select
that, and the M Audio on the left, and press Connect. The connections
may be automatic in the audio tab.

When using a2jmidid, I cross X connect the midi-through to the Maudio,
in the alsa tab, and in the middle midi tab, connect a displayed instrument, to the a2j midi port. And connect the instrument output
in the Audio tab on the left, to the the System playback on the right.  Yoshimi needs this, it is a version of zynaddsubfx, modernized a bit.

The qjackctl wiki uses zynaddsubfx in it's qjackctl tutorial.
Glad you were able to get one of these soundcards!
Cheers

---

### Post by nazaroo2 on 2012-02-07
thanks for this.

I found envy24control in the software control center as a separate program,
and its also listed under a group of utils just below that.

I typed envy24control in the search box in the control center.

I have installed it, but haven't tried it.  It seems to install itself under a different name (**mudita**24-dbg) than envy24control.
It doesn't seem to show up under "Dash Home" (the list of installed software),
i.e., under "envy", "mixer", or mudita.

but then again, I don't know how to use this horrible[B] interfarce.

Okay, the Software center ****** up.

If I type [COLOR=Blue]envy24control[/COLOR] in a terminal,
I get a message saying its not installed.
Then it (awesomely!) gives the command to install it, so you can do it from the terminal.
[/B]```

apt-get install alsa-tools-gui
```[B][COLOR=Blue]

[COLOR=Black]I can then run the tool in the terminal:
It pops up and you can stretch it to show all the menus along the top:

[/COLOR][IMG]http://3.bp.blogspot.com/-eyEhiRVJkVY/TzEDSu38urI/AAAAAAAAA0E/Fo41nL5q20Y/s640/Screenshot+at+2012-02-07+04:54:54.png[/IMG]

[COLOR=Black]
I have no idea what to do with this however.  [/COLOR]




[/COLOR] 
[/B]

---

### Post by jejeman on 2012-02-07
> **nazaroo2 said:**
> This appears slightly different than under Ubuntu 10. 
The notice [COLOR=Blue]**"Unclaimed"**[/COLOR] seems to have vanished.

Here the driver has at least been identified, **but it is unclear whether it is actually installed.**When it writes "unclaimed" that means no module had claimed the device. In another words, no modules loaded for the device.
If module claims the device than it is obviously installed.
If the device is unlcaimed, it is not necessary that modul is not installed.
List of installed modules can be obtained with the following command
```
modprobe -l
```

---

### Post by nazaroo2 on 2012-02-07
Thank you for your help here.

I am thinking of calling this thread here for Ubuntu 11.10 "SOLVED",
at least, until I run into any further snags.
The card works in this distro now, and seems to have all the function I need.

Nonetheless, I really don't want to abandon trying to get it working in Ubuntu 10.04 /10.10,
since I'm sure there are thousands of others who want to use the Studio software,
but don't want to adopt Ubuntu 11 to do it.

Thanks to everyone who provided the clues to get this working.

Others should be able to follow my steps,
if they have a **Dell Optiplex 330** or similar dual core.
I love this machine because it is so quiet,
and the case and hardware install features are pro: no fiddling with screws and crap.

I'm recommending the m-audio card (24/96) now, 
but I'm still trying to get out of having to use Ubuntu 11.

How do I mark the thread "SOLVED"??

PS: there is one final issue:

Is it possible to have this card working and also enable the onboard soundcard in BIOS too?
It would be good to have a choice of using both soundcards, rather than just rely upon the m-audio,
since I have no sound at all now, in Ubuntu 10, and I don't want to have to go into the BIOS everytime
to switch operating systems.

---

### Post by sgx on 2012-02-07
> **nazaroo2 said:**
> thanks for this.

I found envy24control in the software control center as a separate program,
and its also listed under a group of utils just below that.

I typed envy24control in the search box in the control center.

I have installed it, but haven't tried it.  It seems to install itself under a different name (**mudita**24-dbg) than envy24control.
It doesn't seem to show up under "Dash Home" (the list of installed software),
i.e., under "envy", "mixer", or mudita.

but then again, I don't know how to use this horrible[B] interfarce.

Okay, the Software center ****** up.

If I type [COLOR=Blue]envy24control[/COLOR] in a terminal,
I get a message saying its not installed.
Then it (awesomely!) gives the command to install it, so you can do it from the terminal.
[/B]```

apt-get install alsa-tools-gui
```[B][COLOR=Blue]

[COLOR=Black]I can then run the tool in the terminal:
It pops up and you can stretch it to show all the menus along the top:

[/COLOR][IMG]http://3.bp.blogspot.com/-eyEhiRVJkVY/TzEDSu38urI/AAAAAAAAA0E/Fo41nL5q20Y/s640/Screenshot+at+2012-02-07+04:54:54.png[/IMG]

[COLOR=Black]
I have no idea what to do with this however.  [/COLOR]

[/COLOR] 
[/B]

Press the 'analog volume' tab. The mudita name was added to
envy24control, you can look in /usr/bin  to see the actual
name to use in a terminal.

You can safely ignore the extra input/outputs listed.
Other mixers may work fine too. 
Cheers

---

### Post by nazaroo2 on 2012-02-09
***Updated Report:***

After discovering that my ONBOARD sound was probably as good a quality as any outboard card (24/192 kHz, -96 db noise floor), 
I tried to see if the RECORD inputs to the ONBOARD were working,
even with the m-audio plugged in, by re-enabling the onboard sound in the BIOS.

(1) The onboard sound system seems to work fine,  I am able to record / monitor whatever is plugged into it, using JACK (using **Ubuntu 11**  <--).

(2) However, even though JACK says its aware of the m-audio PCI card, it can't use it while the Onboard is enabled in the BIOS.  No sounds go in or out.

That looks like the size of it for Dell Optiplex users.  They can use their onboard sound if they want to, 
but extra sound-cards plugged in will not work properly as long as the onboard sound is enabled in the BIOS.

You may be able to avoid buying a sound card: 
but if you do buy one and install it, 
you'll have to disable the onboard one in the Dell BIOS.

Fo[COLOR=Red]***r Ubuntu 10 ***[/COLOR]users however, the news is sad and ironic.

(1)  Although the onboard card "works",  It seems to 'hardware' itself to its own output, even when disconnected from it in Patchage.   Thus you can't turn off sound being sent into the ONBOARD system, or re-route it into Ardour for instance, and control it. 

(2)  As with Ubuntu 11, **Ubuntu 10** users won't be able to access an m-audio PCI card either, whether or not the OS or JACK thinks it sees it.  This could be a combination of not having working drivers available, and/or the OS being unable to initialize the card(s) properly. 

Bottom line: I couldn't get the onboard system to work with JACK properly** in Ubuntu 10**, at least with another card plugged into a PCI slot, although it can be made to work in Ubuntu 11.

These are mainly issues for dual-boot users, and/or those who don't want to upgrade to Ubuntu 11.
The Patchage patchbay seems to work properly generally in Ubuntu 11, (i.e., disconnecting sound through-put when System Input is re-routed), although you can't access both onboard and outboard systems at once.

---

