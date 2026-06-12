---
title: "Ubuntu 10.10 maverick - jack with UA-25 EX duplex not working"
date: 2011-02-20
forum: Ubuntu Studio
---

### Post by der_On on 2011-02-20
Hello,

I know those kinds of questions have been written here a dozen times, but actually solutions have not been working for me.

My Problem is as follows:

I had Ubuntu Studio 10.04 64bit running very well with my UA-25 EX and jack in duplex mode. In 44.1k and 48k. I had installed the alsa-driver-linuxant which installed well on 10.04. Now after switching to 10.10 with a distro upgrade I can't use jack in duplex mode with the very same settings as in 10.04 (regarding jack) and I can't install alsa-driver-linuxant due to a install error the dev's are aware of, but has not been fixed yet. :/

Running jack as output only works well. Running jack in input only, does not work.

I'm getting the following output when trying to start jack in duplex:

```

p, li { white-space: pre-wrap; } 14:04:19.567 Steckfeld deaktiviert.
 14:04:19.676 Statistik zurückgesetzt.
 14:04:19.721 Schaubild der ALSA-Verbindungen geändert.
 14:04:19.927 ALSA-Verbindung geändert.
 14:05:31.186 Start-Skript...
 14:05:31.186 pulseaudio -k
 14:05:31.617 Start-Skript beendet erfolgreich.
 14:05:31.617 JACK startet...
 14:05:31.617 /usr/bin/jackd -v -m -dalsa -r44100 -p256 -n3 -D -Chw:1,0 -Phw:1,0 -Xseq
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 getting driver descriptor from /usr/lib/jack/jack_net.so
 getting driver descriptor from /usr/lib/jack/jack_alsa.so
 getting driver descriptor from /usr/lib/jack/jack_dummy.so
 getting driver descriptor from /usr/lib/jack/jack_firewire.so
 14:05:31.647 JACK wurde mit PID = 7242 gestartet.
 no message buffer overruns
 getting driver descriptor from /usr/lib/jack/jack_oss.so
 JACK compiled with System V SHM support.
 server `default' registered
 loading driver ..
 SSE2 detected
 apparent rate = 44100
 creating alsa driver ... hw:1,0|hw:1,0|256|3|44100|0|0|nomon|swmeter|-|32bit
 control device hw:1
 registered builtin port type 32 bit float mono audio
 registered builtin port type 8 bit raw midi
 clock source = system clock via clock_gettime
 new client: alsa_pcm, id = 1 type 1 @ 0xe66400 fd = -1
 start poll on 3 fd's
 configuring for 44100Hz, period = 256 frames (5.8 ms), buffer = 3 periods
 ALSA: final selected sample format for capture: 16bit little-endian
 ALSA: use 3 periods for capture
 ALSA: final selected sample format for playback: 16bit little-endian
 ALSA: use 3 periods for playback
 new buffer size 256
 registered port system:capture_1, offset = 1024
 registered port system:capture_2, offset = 2048
 registered port system:playback_1, offset = 0
 registered port system:playback_2, offset = 0
 ++ jack_sort_graph
 ++ jack_rechain_graph():
 +++ client is now alsa_pcm active ? 1
 client alsa_pcm: internal client, execution_order=0.
 -- jack_rechain_graph()
 -- jack_sort_graph
 14:05:31.709 Schaubild der ALSA-Verbindungen geändert.
 ALSA: could not start playback (Broken pipe)
 DRIVER NT: could not start driver
 cannot start driver
 registered port alsa_pcm:Midi-Through/midi_capture_1, offset = 1024
 registered port alsa_pcm:Midi-Through/midi_playback_1, offset = 0
 registered port alsa_pcm:TiMidity/midi_playback_1, offset = 0
 registered port alsa_pcm:TiMidity/midi_playback_2, offset = 0
 registered port alsa_pcm:TiMidity/midi_playback_3, offset = 0
 registered port alsa_pcm:TiMidity/midi_playback_4, offset = 0
 starting server engine shutdown
 server thread back from poll
 stopping driver
 unloading driver
 14:05:31.746 Schaubild der ALSA-Verbindungen geändert.
 freeing shared port segments
 stopping server thread
 stopping watchdog thread
 last xrun delay: 0.000 usecs
 max delay reported by backend: 0.000 usecs
 freeing engine shared memory
 max usecs: 0.000, engine deleted
 cleaning up shared memory
 cleaning up files
 unregistering server `default'
 14:05:31.775 JACK wurde angehalten erfolgreich.
 14:05:31.775 Nach-Herunterfahr-Skript...
 14:05:31.776 /home/ondrej/shutdown-jack.sh
 jackd: Kein Prozess gefunden
 14:05:32.843 Nach-Herunterfahr-Skript beendet erfolgreich.
 14:05:34.351 Keine Verbindungsaufnahme als Client zum JACK-Server möglich. - Gesamtbetrieb schlug fehl. - Verbindungsaufnahme zum Server gescheitert. Bitte sehen Sie im Meldungsfenster nach weiteren Informationen.

```

Attached is a screenshot of my jack settings. Sorry all is in German. :/

---

### Post by AutoStatic on 2011-02-20
> **der_On said:**
> I had Ubuntu Studio 10.04 64bit running very well with my UA-25 EX and jack in duplex mode. In 44.1k and 48k. I had installed the alsa-driver-linuxant which installed well on 10.04. Now after switching to 10.10 with a distro upgrade I can't use jack in duplex mode with the very same settings as in 10.04 (regarding jack) and I can't install alsa-driver-linuxant due to a install error the dev's are aware of, but has not been fixed yet. :/Hello der_On, I don't think you need this Linuxant package for your UA-25EX to work properly. I assume this Conexant chipset is used on soundcards?

> **der_On said:**
> ```
 14:05:31.617 /usr/bin/jackd -v -m -dalsa -r44100 -p256 -n3 -D -Chw:1,0 -Phw:1,0 -Xseq
```Try unticking 'No Memory Lock' in QjackCtl, you really need to be able to lock memory. Also disable the MIDI driver which is now set to 'seq'. Set it to 'none', using 'seq' can cause xruns, and use a2jmidid to make your connections in the JACK MIDI tab of QjackCtl.
And I use hw:UA25 as the interface name, my guess is the UA-25EX can be addressed to as hw:UA25EX. You can check this with **cat /proc/asound/cards**, the ALSA name for your card is the name between the brackets []. My settings look like this for example: [http://www.autostatic.com/logimages/qjackctl_ua-25.png](http://www.autostatic.com/logimages/qjackctl_ua-25.png)
Another thing you could try if you still get xruns is to change the 'Server Path' in QjackCtl to read '/usr/bin/jackd -S'. You're now using Jack2 which is a different implementation of JACK that works a bit differently and by adding the -S option you make it work basically the same as Jack1 on 10.04.
And could you also post the outcome of **lspci** ? Thanks!

Best,

Jeremy

---

### Post by der_On on 2011-02-26
Thanks for the tips. Actually it's still the same. I've now even installed a clean ubuntu studio maverick and tried it there but with no luck. I've used the same settings as you did in the screenshot. Do I have to edit some file, or kill pulseaudio or something like that?

here is the output of **lspci**:
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
02:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)

```And the output of jack:

```

JACK server starting in realtime mode with priority 69
 audio_reservation_init
 Acquire audio card Audio2
 creating alsa driver ... hw:UA25EX|hw:UA25EX|128|3|48000|0|0|nomon|swmeter|-|32bit
 Using ALSA driver USB-Audio running on card 2 - EDIROL UA-25EX at usb-0000:00:1d.0-1.1, full speed
 configuring for 48000Hz, period = 128 frames (2.7 ms), buffer = 3 periods
 ALSA: final selected sample format for capture: 24bit little-endian
 ALSA: use 3 periods for capture
 ALSA: final selected sample format for playback: 24bit little-endian
 ALSA: use 3 periods for playback
 ALSA: could not start playback (Broken pipe)
 Cannot start driver
 JackServer::Start() failed with -1
 Released audio card Audio2
 audio_reservation_finish
 Failed to start server

```

---

### Post by martjan on 2011-02-27
Hello der_On, 
I have the same problem as you with Edirol UA-25. I haven't solved it yet, but a good solution seems to be [http://alsa.opensrc.org/Edirol_UA-25EX](http://alsa.opensrc.org/Edirol_UA-25EX).
In particular:
```
As mentioned above, the Edirol UA-25EX supports full-duplex operation, except at 96 Khz. 
If you want to play and record in **full-duplex** though *half-duplex* plugins, check out the asym plugin which is able to combine the dmix (i.e. play) and dsnoop (i.e. record) plug-ins.

```
In this site [http://alsa.opensrc.org/Edirol_UA-25](http://alsa.opensrc.org/Edirol_UA-25) you can find some better explainations. I tried to take this way, but it doesn't work...You can try too...
I hope it will be usefull for you. Let me know if you find something!
Best, 
Martin

---

### Post by der_On on 2011-03-07
I've now found out that duplex won't work for me at the moment. Not until problems with USB drivers are fixed in 10.10. It seems that my PC has 3 USB plugs all connected to the same hub and no matter in which plug I put it, the duplex wont work. However using the UA25EX for record only and setting output to the internal soundcard is working. This is semi-optimal, as I can only output through headphone jacks with my laptop and this way I can't really use it in a concert for now. Only for home recording. :/ Lucid Lynx was dealing fine with Duplex and my UA25EX.

However I would also like to know how to get a2jmidid working? I want to use QSynth to produce sounds in rosegarden. Is there a tutorial maybe? The a2jmidid website does not provide understandable information on using a2jmidid. :(

---

### Post by AutoStatic on 2011-03-07
> **der_On said:**
> ot until problems with USB drivers are fixed in 10.10.Hello der_On, thsi is not a driver problem but....> **der_On said:**
> It seems that my PC has 3 USB plugs all connected to the same hub and no matter in which plug I put it, the duplex wont work.Soundcards connected to a hub cannot work at full duplex in most cases.
> **der_On said:**
> :/ Lucid Lynx was dealing fine with Duplex and my UA25EX.You're absolutely sure? Could you post the output of **lsusb** ?

> **der_On said:**
> However I would also like to know how to get a2jmidid working? I want to use QSynth to produce sounds in rosegarden. Is there a tutorial maybe? The a2jmidid website does not provide understandable information on using a2jmidid. :(Qsynth can use both ALSA MIDI and JACK MIDI so if you want to use Rosegarden with Qsynth you don't need a2jmidid.

Best,

Jeremy

---

### Post by Pablo_F on 2011-03-07
> I want to use QSynth to produce sounds in rosegarden.

As Autostatic points out, both do alsa MIDI. So, configure qsynth to enable MIDI input and use the alsa-seq MIDI controller. 

In Rosegarden you need to right click in the track name and choose the generic "General MIDI Device" for this track. This is the default name for a midi track with an external synth. 

Then, go to Studio -> Manage MIDI devices. You can rename the rosegarden playback device to your wish but make sure that "sends data through" qsynth (it will show up as synth input port or fluidsynth or similar).


Alternatively, as you don't really need an external soft synth to make noise with Rosegarden, if the track is configured for using a "synth plugin", you just plug in a virtual instrument (this is, a dssi plugin). There is a fluidsynth-dssi in which you can load soundfonts. Or you can use some other one. 

The synth plugin approach is simpler as you don't need anything else beyond Rosegarden (well, the plugins).


When you really need to expose your alsa MIDI ports to jack MIDI, you can use the a2jmidi daemon by launching it in a command line (ALT + F2 or a terminal): 

a2jmidid

If you have a hardware midi keyboard, you will want:

a2jmidid -e

Well, the manual. Just do in a terminal:

man a2jmidid

You can add a2jmidid as a "script after server start" in qjackctl, but in this case, append the ampersand. For example,

a2jmidid -e &

Cheers, Pablo

---

### Post by der_On on 2011-03-08
AutoStatic, thanks for your help.

I'm probably short on knowledge here regarding the USB and midi part. So I might need a little more help on this.

lsub is reporting the following to me:
```

Bus 002 Device 003: ID 046d:c52e Logitech, Inc. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 10f1:1a2a  
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```I've now tried the following to get QSynth working together with rosegarden without using alsa_seq (which was really causing xruns and was sometimes playing slower and faster again). I've set midi-driver in jack to "none". In Qsynth I've set midi-input to jack and typed a "0" into the device name (before I left it blank). Then suddenly qsynth appeared in the JACK-Midi connections. It wasn't doing it before. And now I've connected rosegardens midi-out with qsynths midi in and it works. :)

And then I tried using the Synth-plugin FluidSynth DSSI using the same soundfont Qsynth uses but aftet choosing an instrument from the bank it gave me a very noisy and scratchy sound. :( I hoped to be able to overcome the need of Qsynth using the synth plugins.

---

