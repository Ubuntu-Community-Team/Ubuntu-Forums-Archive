---
title: "Terratec DMX6Fire USB not detected in Studio 11.10 amd64"
date: 2012-02-19
forum: Ubuntu Studio
---

### Post by Fafnir089 on 2012-02-19
Dear Forum Members, 
to get my Terratec DMX6Fire USB to work with Ubuntu Studio 11.10 is hard  work. I've googled for several hours, but still had no success. The  computer is dual booting with Windows 7 and the DMX6Fire is working in  Windows, so I'm sure that the device itself doesn't make any trouble.  The Kernel Version is 3.0.0-16-generic. I've disabled the onboard sound  in BIOS. One card correctly shows up in /proc/asound/cards, it is a  Terratex CX8801 type TV-card, but the DMX6Fire does not and has never been  detected and listed there. The output from lsusb is: "Bus 001 Device  002: ID 0ccd:0080 TerraTec Electronic GmbH". I followed the  documentation from  [http://wiki.ubuntu-it.org/Hardware/Audio/TerratecDmx6Fire](http://wiki.ubuntu-it.org/Hardware/Audio/TerratecDmx6Fire) and have 
1. ```
options snd-ice1712 enable=1 index=0 model=dmx6fire
```enabled in alsa-base.conf.
2. ```
load-module module-alsa-sink device=sensaura 
```enabled in default.pa
3. the content of .asoundrc is 
```
pcm.!default {   
type pulse 
}  
ctl.!default {   
   type pulse 
}  
pcm.pulse {   
   type pulse 
}  
ctl.pulse {   
   type pulse 
}   
# "Sensaura" like effect 
pcm.ice1712 {   
  type hw    
  card 0    
  device 0 
}  
pcm.sensaura { #!default    
   type plug   
   ttable.0.0 1     
   ttable.1.1 1     
   ttable.0.2 1     
   ttable.1.3 1     
    ttable.0.4 0.5      
    ttable.1.4 0.5     
    ttable.0.5 0.5     
    ttable.1.5 0.5     
    slave.pcm ice1712 
}
```[FONT=Verdana]
However[/FONT], I found out that modules snd-usb-audio and
snd-ice1712 are not loaded on boot, but load with 
```
sudo modprobe snd-usb-audio && sudo modprobe snd-ice1712
```.
Thereafter lsmod | grep snd:
```
snd_ice1712            75630  0 
snd_ice17xx_ak4xxx     13315  1 snd_ice1712
snd_ak4xxx_adda        18904  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427             14297  1 snd_ice1712
snd_ac97_codec        134826  1 snd_ice1712
ac97_bus               12730  1 snd_ac97_codec
snd_i2c                14191  2 snd_ice1712,snd_cs8427
snd_mpu401_uart        14169  1 snd_ice1712
snd_usb_audio         118122  0 
snd_hwdep              13668  1 snd_usb_audio
snd_usbmidi_lib        25371  1 snd_usb_audio
snd_pcm                96714  4 snd_ice1712,snd_ac97_codec,snd_usb_audio,cx88_alsa
snd_seq_midi           13324  0 
snd_rawmidi            30547  3 snd_mpu401_uart,snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  17 snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_i2c,snd_mpu401_uart,snd_usb_audio,snd_hwdep,snd_usbmidi_lib,cx88_alsa,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  1 snd_pcm

```But no change in /proc/asound/cards:
```
1 [CX8801         ]: CX88x - Conexant CX8801
                      Conexant CX8801 at 0xf9000000
```Maybe this problem is somehow related to this thread: 
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/459046](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/459046).
But I have no idea how to edit the 90-pulseaudio.rules file correctly.
Can someone help please? That would be excellent. Are there forum members with similar problems?
Best regards,
Fafnir089

---

### Post by sgx on 2012-02-20
some have needed to edit

/etc/pulse/client.conf

and add

autospawn = no

then do

pulseaudio -k

Otherwise pulseaudio continually respawns, blocking normal access
to the snd_ice1712 cards

You can uninstall all the pulseaudio libs and apps, and use
alsa and jackd for media/sound i/o.

Look for jackd modules among the vlc, xine, xmms etc items in synaptic.
Aqualung autoconnects to jackd, it's a nice player app.

---

### Post by gordintoronto on 2012-02-20
Have you read this blog: [http://yjpark.blogspot.com/2008/02/better-audio-under-linux-with-terratec.html](http://yjpark.blogspot.com/2008/02/better-audio-under-linux-with-terratec.html)

---

### Post by Fafnir089 on 2012-02-21
Thanks for your contributions! I want to share with you what I've found out:
there are two different brands of DMX6Fire: PCI with VIA Envy24 (ICE1712) Chipset and USB with RigiSystems USBPAL Chipset. So the ICE1712 approach obviously won't work for the USB Version of the DMX6Fire ([http://www.alsa-project.org/main/index.php/Matrix:Vendor-Terratec](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Terratec)). The 3.0.0 Kernel provides a module for the DMX6Fire USB (see attachment), but it isn't activated in Ubuntu Studio 11.10. A detailed description of the DMX6Fire USB Module and the installation process can be found here: [http://www.alsa-project.org/main/index.php/Matrix:Module-usb-6fire](http://www.alsa-project.org/main/index.php/Matrix:Module-usb-6fire). However I didn't closely follow the installation procedure from there, because I wanted to find out if a consistent installation from within Ubuntu is possible. However the DMX6Fire USB still doesn't work, but I got ahead one step after compiling a new kernel. There is nice new output from dmesg on my system: 
```
[   11.620097] 6fire: error requesting ezusb firmware 6fire/dmx6firel2.ihx.
[   11.620110] snd-usb-6fire: probe of 1-10:1.0 failed with error -2
[   11.620814] usbcore: registered new interface driver snd-usb-6fire
```The documentation from alsa-project.org mentions the alsa-lib and alsa-driver packages, which should be installed (these packages might contain the missing firmware), but the packages alsa-lib and alsa-driver aren't available through apt-get.
To ease troubleshooting I've uninstalled pulseaudio, like you recommended. I guess  there is light at the end of the tunnel!

---

### Post by sgx on 2012-02-22
Thanks for sharing your findings. There is an alsa-firmware-loaders
package in the list here:

[http://packages.debian.org/unstable/sound/](http://packages.debian.org/unstable/sound/)

I doubt it would have any adverse effects on your system.

Cheers

---

### Post by Yellow Pasque on 2012-02-26
There are a lot of fixes in latest ALSA: [http://www.alsa-project.org/main/index.php/Changes_v1.0.24_v1.0.25#USB_TerraTec_DMX_6Fire](http://www.alsa-project.org/main/index.php/Changes_v1.0.24_v1.0.25#USB_TerraTec_DMX_6Fire)

I'm not sure what version of ALSA is in the kernel you built.

---

### Post by sgx on 2012-02-27
You have to define 'it', in practical and precise terms,
with details of what you have, and what you want to accomplish.
The mind-readers are all in the other forum :popcorn:

---

### Post by Fafnir089 on 2012-03-03
Let me get back to the firmware download problem description from above. Here is an important excerpt from the "Help" entry of the kernel module "TerraTec DMX 6Fire USB" (see also the attached thumbnail from above):
"CONFIG_SND_USB_6FIRE:
...
You will need firmware files in order to be able to use the device after it has been coldstarted. 
An install script for the firmware and further help can be found at
[http://sixfireusb.sourceforge.net](http://sixfireusb.sourceforge.net) ..."
To be more specific, the link to the firmware install script can be found  here:
[http://sourceforge.net/projects/sixfireusb/files/tools/]("http://sourceforge.net/projects/sixfireusb/files/tools/fwinst.txt/download")
Two files are in that directory: 1. fwinst.sh 2. fwinst.txt. 
For the fwinst.sh script to run successfully the box needs an internet connection. But I ran into another problem which I will describe later. 
Thanks for your attention, 
Fafnir.

---

### Post by Fafnir089 on 2012-03-05
Sorry the link for the firmware download shellscript was wrong, here is the right one:
[http://sourceforge.net/projects/sixfireusb/files/tools/](http://sourceforge.net/projects/sixfireusb/files/tools/)
The output of dmesg after successfully executing fwinst.sh and rebooting:
```
[   19.300154] usb 1-10: new high speed USB device number 4 using ehci_hcd
[   19.436688] 6fire: invalid fimware version in device: 03 01 17 00. please reconnect to power. if this failure still happens, check your firmware installation.
[   19.436700] snd-usb-6fire: probe of 1-10:1.0 failed with error -22
```Thanks for the link "Changes v1.0.24 v1.0.25 - AlsaProject". Here is the output from modinfo snd-usb-6fire:
```
filename:       /lib/modules/3.0.17-6fire3/kernel/sound/usb/6fire/snd-usb-6fire.ko
license:        GPL v2
description:    TerraTec DMX 6Fire USB audio driver, version 0.3.0
author:         Torsten Schenk <torsten.schenk@zoho.com>
firmware:       6fire/dmx6firecf.bin
firmware:       6fire/dmx6fireap.ihx
firmware:       6fire/dmx6firel2.ihx
srcversion:     FF9AC905908E52BA62D7EE3
alias:          usb:v0CCDp0080d*dc*dsc*dp*ic*isc*ip*
depends:        snd-pcm,snd,snd-rawmidi
vermagic:       3.0.17-6fire2 SMP mod_unload modversions
parm:           index:Index value for the 6fire sound device (array of int)
parm:           id:ID string for the 6fire sound device. (array of charp)
parm:           enable:Enable the 6fire sound device. (array of bool)
```This "invalid firmware version" error is well documented here:
[http://sourceforge.net/projects/sixfireusb/forums/forum/1341785/topic/5000529](http://sourceforge.net/projects/sixfireusb/forums/forum/1341785/topic/5000529).
"... version 0.3.0..." seems to be to old, so my guess is that I would have to update the driver. The latest version on sourceforge is 0.5.5. Can you give me a hint? How do I update the module and build initial ram disk in correct "Ubuntu style", that`s my question. 
Cheers!

---

### Post by toscnk on 2012-03-05
Hello Fafnir,

the problem is, that changing the driver on sourceforge is something completely different than preparing a new version for the kernel. Therefore the kernel driver is some versions behind the sourceforge driver.

But installing the driver is easy: you need the linux-headers package and then you just need to type
make
sudo make install

as also described in INSTALL.

Greets,
toscnk

---

### Post by toscnk on 2012-03-05
Ah sorry, I forgot:

you also need to run
make kremove

before anything else since you have installed a driver already that needs to be removed before the new driver can be used.

Greets
toscnk

---

### Post by Fafnir089 on 2012-03-11
Hello toscnk, 
thanks for your replies ... I should have known that. What led me to my previous desperate posting ( "... version 0.3.0..." ) was this link from Alsa: [http://www.alsa-project.org/main/index.php/Matrix:Module-usb-6fire](http://www.alsa-project.org/main/index.php/Matrix:Module-usb-6fire). I followed the instructions and installed the alsa-driver-1.0.25 and alsa-lib-1.0.25 package and afterwards the driver sixfireusb-0.5.5 as described in "INSTALL" and then ran into strange output from dmesg. But anyhow I restored the system from a previous image and after installing ONLY sixfireusb-0.5.5 with 
```
make && sudo make kremove && make install
``` I have the driver up and running:
```
cat /proc/asound/cards
 0 [DMX6FireUSB    ]: 6FireUSB - TerraTec DMX6FireUSB
                      TerraTec DMX6FireUSB at 1:3
 1 [CX8801         ]: CX88x - Conexant CX8801
                      Conexant CX8801 at 0xf9000000
```and the version is perfect:
```
modinfo snd-usb-6fire
filename:       /lib/modules/3.0.17-6fire2/extra/snd-usb-6fire.ko
license:        GPL v2
description:    TerraTec DMX 6Fire USB audio driver, version 0.5.5
author:         Torsten Schenk <torsten.schenk@zoho.com>
firmware:       6fire/dmx6firecf.bin
firmware:       6fire/dmx6fireap.ihx
firmware:       6fire/dmx6firel2.ihx
srcversion:     4036097E68C6387CEF378CA
alias:          usb:v0CCDp0080d*dc*dsc*dp*ic*isc*ip*
depends:        snd-pcm,snd,snd-rawmidi
vermagic:       3.0.17-6fire2 SMP mod_unload modversions
parm:           index:Index value for the 6fire sound device (array of int)
parm:           id:ID string for the 6fire sound device. (array of charp)
parm:           enable:Enable the 6fire sound device. (array of bool)
parm:           tasklet_thresh:Tasklet threshold (packets/urb, default = 128). (array of int)
parm:           pcm_mode:PCM mode (default = 3). (array of int)
```Unfortnately I don't hear any output from ```
aplay /usr/share/sounds/alsa/Front_Center.wav
Wiedergabe: WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate: 48000 Hz, mono
```With Windows everything is still ok. I'm currently reading through plenty of JACK documentation:
[https://help.ubuntu.com/community/What%20is%20JACK](https://help.ubuntu.com/community/What%20is%20JACK)
[http://wiki.ubuntuusers.de/JACK_Audio_Connection_Kit](http://wiki.ubuntuusers.de/JACK_Audio_Connection_Kit)
[http://jackaudio.org/applications](http://jackaudio.org/applications)
[http://manpages.ubuntu.com/manpages/gutsy/man1/jackd.1.html](http://manpages.ubuntu.com/manpages/gutsy/man1/jackd.1.html)
[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration).
Maybe someone can help a bit?
Have a nice day,
Fafnir089

---

### Post by toscnk on 2012-03-11
Hmm, to exclude the simplest error... Did you unmute and increase Master and Analog 1 volume? The card is muted by default.

If you use other outputs than 1/2 with a mono file, you won't hear anything.

Concerning jack: take a look at the Help-Forum on sixfireusb.sourceforge.net. There are a lot of discussions going on about it; jack seems to work greatly with the card.

---

### Post by Fafnir089 on 2012-03-18
Hello all,
output through aplay is perfect. Thanks to toscnk.  Beeing too cautious with the faders, I couldn`t hear anything at the  beginning ( I didn't want to kill the speaker :guitar:...).  But someone can safely set the volume 1 fader of xfce4-mixer to full scale and then  open up the master volume step by step (aplay /usr/share/sound/alsa/Noise.wav is good for testing). So far so good,  but there is a problem with jackd. I tried several different settings,  but the result is mostly ugly distorted sound for maybe 20 seconds  thereafter the output of sound stops. In some cases I could hear clear  output for a few seconds, then distortion for a while,  then silence again. I couldn't get stable output. Here is an excerpt of  jackd messages:
```
Mon Mar 19 00:31:16 2012: Jack: fPollTable i = 1 fd = 11
Mon Mar 19 00:31:16 2012: Jack: fPollTable i = 2 fd = 12
Mon Mar 19 00:31:16 2012: Jack: JackRequest::ConnectNamePorts
Mon Mar 19 00:31:16 2012: Jack: JackEngine::PortConnect src = vlc_1968:out_2 dst = system:playback_4
Mon Mar 19 00:31:16 2012: Jack: JackGraphManager::CheckConnect src_name = vlc_1968:out_2 dst_name = system:playback_4
Mon Mar 19 00:31:16 2012: Jack: JackEngine::PortConnect src = 12 dst = 8
Mon Mar 19 00:31:16 2012: Jack: CheckPortsConnect(caller = 3, src = 4, dst = 0)
Mon Mar 19 00:31:16 2012: Jack: src_self is false
Mon Mar 19 00:31:16 2012: Jack: dst_self is false
Mon Mar 19 00:31:16 2012: Jack: JackGraphManager::Connect port_src = 12 port_dst = 8
Mon Mar 19 00:31:16 2012: Jack: JackConnectionManager::Connect port_src = 12 port_dst = 8
Mon Mar 19 00:31:16 2012: Jack: JackConnectionManager::Connect port_src = 8 port_dst = 12
Mon Mar 19 00:31:16 2012: Jack: JackConnectionManager::IsLoopPathAux ref1 = 0 ref2 = 4
Mon Mar 19 00:31:16 2012: Jack: JackConnectionManager::IncConnectionRef: ref1 = 4 ref2 = 0
Mon Mar 19 00:31:16 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Mon Mar 19 00:31:16 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Mon Mar 19 00:31:16 2012: Jack: JackClient::kPortConnectCallback src = 12 dst = 8
Mon Mar 19 00:31:16 2012: Connecting 'vlc_1968:out_2' to 'system:playback_4'
Mon Mar 19 00:31:16 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Mon Mar 19 00:31:16 2012: Jack: JackEngine::NotifyClient: no callback for event = 11
Mon Mar 19 00:31:16 2012: Jack: fPollTable i = 3 fd = 14
Mon Mar 19 00:31:17 2012:ROR: ALSA: poll time out, polled for 31999038 usecs
Mon Mar 19 00:31:17 2012:ROR: JackAudioDriver::ProcessAsync: read error, stopping...
Mon Mar 19 00:31:17 2012: Jack: ThreadHandler: exit
```
Can someone help?
Thank you all,
Fafnir089

---

