---
title: "JACK will not start"
date: 2014-06-04
forum: Ubuntu Studio
---

### Post by kazik2002 on 2014-06-04
Hi
After checking out a multitude of posts all over the net and trying loads of things I am still stumped on this one.
I cannot get JACK to start and I will post all the relevant details below.
I am using a real-time kernel and no matter what I do with regard to settings in Qjackctl it throws an error.
I am using a M-Audio Fast Track for capturing audio.
Pulseaudio is not running.
I am in the audio group.

I am at a loss as to where to go from here as I have had it all up and running sweetly on a previous installation.


 ```
[COLOR=#990099]22:25:23.172 /usr/bin/jackd -S -P70 -p128 -m -dalsa -dhw:0 -r48000 -p128 -n2 -D -Chw:Track[/COLOR]

 Cannot connect to server socket err = Connection refused
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#999999]22:25:23.189 JACK was started with PID=4371.[/COLOR]
 no message buffer overruns
 no message buffer overruns
 no message buffer overruns
 unknown option character 
 [COLOR=#999999]22:25:23.244 JACK was stopped with exit status=255.[/COLOR]
  ]
                [ --temporary OR -T ]
                [ --version OR -V ]
          -d master-backend-name [ ... master-backend args ... ]
        jackdmp -d master-backend-name --help
              to display options for each master backend
 Available backends:
       loopback (slave)
       alsarawmidi (slave)
       firewire (master)
       alsa (master)
       dummy (master)
       netone (master)
       net (master)
 Available internals:
       netadapter
       audioadapter
       profiler
       netmanager
 [COLOR=#ff0000]22:25:24.325 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = Connection refused
 Cannot connect to server request channel
 jack server is not running or cannot be started
```


```
cat /proc/asound/cards
 0 [VirMIDI        ]: VirMIDI - VirMIDI
                      Virtual MIDI Card 1
 1 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xefebc000 irq 44
 2 [Track          ]: USB-Audio - Fast Track
                      M-Audio Fast Track at usb-0000:00:1d.2-1, full speed
```

Regards

Kazm

---

### Post by jejeman on 2014-06-04
First you are using hw:0, then hw:Track. Those are two different devices. Use just one device.

---

### Post by kazik2002 on 2014-06-04
hw:0 is the default sound card for output
hw:track is the M-Audio Fast Track USB device which I want to use to capture the guitar to Ardour.

If I only use one device, the default, then I just get noise from the onboard mic and nothing from the M-Audio.
Regardless, even with just the default device it will not start.

---

### Post by jejeman on 2014-06-05
Disable jackdbus in Qjackctl, see if helps.
Start jack without Qjackctl from terminal.
It is not recommended to use two cards with JACK at the same time.
Use 3 periods for USB card.
Rise the value of frames.

---

### Post by kazik2002 on 2014-06-18
Still nothing happening with this one. Still cannot strat JACK with or without qjackctl.
With or without DBUS ....AAArrrggghh!!

Does anyone else have any ideas?

---

### Post by weaseldb83 on 2014-06-25
Sorry to piggyback. But im having a similar problem and most other relevant threads are closed.
I can never get jack to work and get so frustrated with Ubuntu-Studio that i always give up.

Jack is "supposed" to install as "setup". But i never get it to work..
Here's my log:

 [COLOR=#999999]13:08:03.006 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]13:08:03.046 Statistics reset.[/COLOR]
 [COLOR=#cccc99]13:08:03.056 ALSA connection change.[/COLOR]
 [COLOR=#999999]13:08:03.064 JACK is starting...[/COLOR]
 [COLOR=#990099]13:08:03.065 /usr/bin/jackd -u -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#66cc99]13:08:03.075 ALSA connection graph change.[/COLOR]
 jackdmp 1.9.10
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2013 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 10
 (qjackctl:16834): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:16834): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 [COLOR=#999999]13:08:03.154 JACK was started with PID=16838.[/COLOR]
 audio_reservation_init
 Failed to acquire device name : Audio0 error : Device reservation request with priority 2147483647 denied for "Audio0" via RequestRelease()
 Audio device hw:0 cannot be acquired...
 Cannot initialize driver
 JackServer::Open failed with -1
 Failed to open server
 [COLOR=#999999]13:08:03.273 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#ff0000]13:08:05.279 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started

---

### Post by luctor on 2014-06-30
> **kazik2002 said:**
> 
 ```
[COLOR=#990099]22:25:23.172 /usr/bin/jackd -S -P70 -p128 -m -dalsa [COLOR="#FF0000"]-dhw:0[/COLOR] -r48000 -p128 -n2 -D -Chw:Track[/COLOR]

```


```
cat /proc/asound/cards
[COLOR="#FF0000"] 0 [VirMIDI        ]: VirMIDI - VirMIDI[/COLOR]
                      Virtual MIDI Card 1
 1 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xefebc000 irq 44
 2 [Track          ]: USB-Audio - Fast Track
                      M-Audio Fast Track at usb-0000:00:1d.2-1, full speed
```

Seems to me you're trying to use the virtual midi card to play audio. 
-dhw:0 is the Virtual MIDI Card 1

I would first try to use the M-Audio card as both input and output.
If that works try to use M-Audio as input and HDA Intel as output. I guess you don't use the M-Audio interface to monitor your audio.

---

### Post by luctor on 2014-06-30
[LIST=1][*]to check if pulseaudio is running give the output of ```
ps aux | grep pulseaudio
```
[indent]If it is running kill it with ```
pulseaudio -k
``` pulseaudio can sometimes block access to your soundcard[/indent]
[/LIST]
[LIST=2][*]to check if you have multiple soundcards or maybe some funny loopback devices give the output of ```
cat /proc/asound/cards
``` 
[/LIST]
[LIST=3][*]to check if you are in the audio group give the output of ```
id
```
[/LIST]

---

### Post by cetag on 2014-07-04
I am in the same boat, please forgive me for replying here. 
Am just wishing to get jack running with Rosegarden. 
Qjackctl doesn't behave, and jackd from the command line seems to crash. 
 
Ubuntu 12.04.  Studio version, not sure which version of Studio. 

Yes, I can turn pulseaudio on and off; 
```

aaa@aaa:~$ pulseaudio -k
aaa@aaa:~$ ps aux | grep pulseaudio
aaa       4540  0.0  0.0   4384   772 pts/1    S+   23:27   0:00 grep --color=auto pulseaudio
aaa@aaa:~$ 
aaa@aaa:~$ pulseaudio --start
aaa@aaa:~$ ps aux | grep pulseaudio
aaa       4544  3.0  0.4 115936  4984 ?        S<l  23:27   0:00 /usr/bin/pulseaudio --start --log-target=syslog
aaa       4549  0.0  0.2  14072  2480 ?        S    23:27   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
aaa       4555  0.0  0.0   4384   776 pts/1    S+   23:27   0:00 grep --color=auto pulseaudio
aaa@aaa:~$ 

```

I am using the Live card, not the VIA onboard hardware. 
```
aaa@aaa:~$ cat /proc/asound/cards
 0 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with CMI9739 at 0xb800, irq 22
 1 [Live           ]: EMU10K1 - SB Live! [CT4620]
                      SB Live! [CT4620] (rev.4, serial:0x211102) at 0xd000, irq 16
aaa@aaa:~$ 
```

I appear to be in the Audio group.
```
aaa@aaa:~$ id
uid=1000(aaa) gid=1000(aaa) groups=1000(aaa),4(adm),24(cdrom),27(sudo),29(audio),30(dip),46(plugdev),109(lpadmin),123(sambashare)
aaa@aaa:~$
```

jackd.   With Pulseaudio off, output as follows; 
```
aaa@aaa:~$ jackd -dalsa -dhw:1
jackd 0.121.2
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:1|hw:1|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:1
Bus error (core dumped)
aaa@aaa:~$ 

```

With Pulseaudio off, Qjackctl message as follows. 
 ```
[COLOR=#999999]23:41:36.501 Logging started --- Fri Jul 4 23:41:36 2014 ---[/COLOR]

 [COLOR=#999999]23:41:36.604 Patchbay deactivated.[/COLOR]

 [COLOR=#999999]23:41:36.626 Statistics reset.[/COLOR]

 [COLOR=#999999]23:41:36.706 JACK is starting...[/COLOR]

 [COLOR=#990099]23:41:36.708 /usr/bin/jackd -r -dalsa -dhw:1 -r44100 -p1024 -n3[/COLOR]

 [COLOR=#999999]23:41:37.158 JACK was started with PID=4631.[/COLOR]

 [COLOR=#999999]23:41:37.283 JACK was stopped successfully.[/COLOR]

 [COLOR=#ff0000]23:41:39.199 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

```

Any suggestions or debug tips gratefully received.

---

### Post by cetag on 2014-07-05
Looking at this, if jackd doesn't work (core dump) at the command line, then Qjackctl will not work. 
 I will re-install jack, and try again.

Looking at a re-install, if I go through the Ubuntu Software Center, then; 
- jack or jackd are not listed under 'Installed'. Only QjackCtl, and, 
- message says, "To remove QjackCtl, these items must be removed as well", and lists; 
    Ubuntu studio audio generation package
    Ubuntu studio audio recording package. 

I will back up my system at this stage, for fear of a total re-install of Ubuntu. 
Once I have backed up, I will try and remove/re-install just QjackCtl (and jack/jackd?) using apt-get remove or synaptic.

---

