---
title: "Cannot start Jack"
date: 2014-04-14
forum: Ubuntu Studio
---

### Post by buffler on 2014-04-14
I've been trying to start Jack using qjackctl for the past week, as the first step in a virtual sound cable between two programs. I have searched all the forum answers and others as well, read up on Jack as best I can, tried with and without pulseaudio, and to no avail. I'm using 12.04 64 bit, all updates.
Here's what I get, no matter what I try from all research, such as different  settings in qjackctl setup, etc.:confused:

17:49:14.945 Patchbay deactivated.
17:49:14.973 Statistics reset.
17:49:14.981 JACK is starting...
17:49:14.981 /usr/bin/jackd -v -p512 -dalsa -dhw:1,0 -r44100 -p1024 -n2 -i1 -o1
17:49:15.037 JACK was started with PID=2628.
17:49:15.062 JACK was stopped with exit status=255.
17:49:17.187 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

Here's aplay -l:

card 0: MID [HDA Intel MID], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC662 rev3 Analog [ALC662 rev3 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


For one thing, what is the "client" referred to if Jack is the server? If Jack is not a server, then what is the server? 
I'm lost. I need a xyzzy to get me out of here.
Don

---

### Post by jejeman on 2014-04-15
If you look at man page for jackd you will see: jackd - JACK Audio Connection Kit sound server
So JACK is server, audio aplications are clients.

Give again 
```
cat /proc/asound/cards
aplay -l
arecord -l
```
It is ugly that HDMI is card0.

You don't need Qjackctl to run jackd. Try to run jackd directly from terminal.
Try to set just playback e.g.
```
/usr/bin/jackd -dalsa -dhw:1 -r48000 -p512 -n2 -P
```

---

### Post by buffler on 2014-04-15
results of inquiries:
djl@shop3:~$ cat /proc/asound/cards
 0 [MID            ]: HDA-Intel - HDA Intel MID
                      HDA Intel MID at 0xf7f14000 irq 56
 1 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7f10000 irq 57
djl@shop3:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC662 rev3 Analog [ALC662 rev3 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
djl@shop3:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 1: PCH [HDA Intel PCH], device 0: ALC662 rev3 Analog [ALC662 rev3 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 2: ALC662 rev3 Alt Analog [ALC662 rev3 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
djl@shop3:~$ 

Which leads me to one of my questions. I've tried to put the internal card ALC662 as the default device by tagging the HDMI card with -2 in alsa-base.conf
using something like
 option snd-MID=-2
But haven't had any success because I haven't a clue as to which name to use. the magic name to be used is either
MID, HDA-Intel-MID, IntelMid, HDMI-0, or what? Why is Linux so darn impenetrable? Why have so many names for the same thing? alias after alias after alias...

And, from the jack help:
Run the JACK daemon with realtime priority using the first  ALSA  hard&#8208;
       ware card defined in /etc/modules.conf.

THERE"S NO SUCH FILE!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
what's it called now? alsa-base.conf? if so, why did the name change? who changed it? and, for God's sake, why?
Ok, got rid of that rant.

 It is indeed unfortunate that HDMI is hogging the default. Furthermore, it seems to be twins.  Also, if I get jack to run right, there's no guarantee that hdmi will always be default on boot, if I understand some of what I've read.

When I run Jack as suggested, it runs:

djl@shop3:~$ /usr/bin/jackd -dalsa -dhw:1 -r48000 -p512 -n2 -P
jackdmp 1.9.8
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2011 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
control device hw:1
control device hw:1
audio_reservation_init
Acquire audio card Audio1
creating alsa driver ... hw:1|-|512|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:1
configuring for 48000Hz, period = 512 frames (10.7 ms), buffer = 2 periods
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback

TRIED AGAIN  with 44100 which I need, and it worked the same. So what gives? Using qjackctl doesn't work, and your magic incantation does work. But don't I need qjackctl especially when I start loopback to give me the program crossconnect?

You're a very patient person, jejeman!
Don

---

### Post by jejeman on 2014-04-16
Probably Qjackctl is starting jackdbus, which is buggy somehow, you can turn it off in Qjackctl setup.
Practicaly you don't need Qjackctl to work with JACK. if you serch jack_* you will found bunch of commands to work with JACK&#269; I sometimes use them, specially in bash scripts.
```
$ jack_
jack_alias                  jack_freewheel              jack_midisine               jack_showtime
jack_bufsize                jack_iodelay                jack_monitor_client         jack_simple_client
jack_capture                jack_latent_client          jack_multiple_metro         jack_simple_session_client
jack_capture_gui            jack_load                   jack_net_master             jack_snapshot
jack_connect                jack_lsp                    jack_net_slave              jack_test
jack_control                jack_meter                  jack_netsource              jack_thru
jack_cpu                    jack_metro                  jack_rec                    jack_transport
jack_cpu_load               jack_midi_dump              jack_samplerate             jack_unload
jack_disconnect             jack_midi_latency_test      jack_server_control         jack_wait
jack_evmon                  jack_midiseq                jack_session_notify         jack_zombie
```Anyhow, you can use "patchage" if you want GUI connecting.

If I understad it correctly it works also with 44100 samplerate, right? That's good then, you can proceed further with radio applications.

---

### Post by jhay2 on 2014-04-18
if you have a qjackctl open it

or if you dont have type
$ sudo apt-get install qjackctl to install it.. 

after that open it , dont run it yet

click setup 

then locate the "interface" selection box . then choose hw:1 then save !


then start qjackctl 

try it . and post the result :)

---

### Post by Clockmender on 2014-04-18
Even better idea - don't use QjackCtl at all - download Claudia from KX Studio  (just google it) and setup Jack within Claudia, I know this sounds rude but it isn't! Then use Claudia - which is a refined LADI wrapper to get the connections you require. You may need to set sound card parameters in your sound card - Alsamixer is the default loaded option - QasHctl is a far better option, get it through Synaptic Package Manager ("sudo apt-get install synaptic" to get Synaptic) If you are really struggling - read my pages at [www.lafavinie.com/Music](www.lafavinie.com/Music) for a comprehensive guide to building a "home" music studio. By now you may have totally messed up your system by trying this and that - it may be better to go to a brand new Ubuntu or Ubuntu Studio install then work through the various stages to get what you want. I had four years of on-and-off frustrations trying to get mine working reliably and correctly - the pages summarise my experiences and how to overcome the problems. Yes, the first bit details my specific sound card but it applies equally well to most, as far as I can gather, in that they all use alsa firmware, libs, drivers and tools. I had much aggro trying to get Jack to use my prefered hw: device, I kept putting for example hw:1,0 as my input device in QjackCtl only to find when I looked in the messages that it was starting hw:0,0 - Claudia stopped all this nonesense. KX Studio bits can be found at [http://kxstudio.sourceforge.net/](http://kxstudio.sourceforge.net/) - I am not involved with this project so have no axe to grind either way, but Claudia and QasHctl worked for me, even with such a complicated card as an E-MU 0404 PCIe.

The tutorials on my website start easy and get more capable without getting too complex and include example projects to work through. Hope it helps you.....

Last thought - if you do look at my tutorials, pay particular attention to the bit that says "use the latest Long Term Support (LTS) version of Ubuntu.................."

---

### Post by buffler on 2014-04-20
Gentlemen:
Jejeman: I may have to use the tools. They're explained sortof o the jack site.
Jahay2:  Tried your strategy, same result, that is "could not connect to Jack server as client. overall operation failed.
I also downloaded the latest qjackctl, 3.11.0, and installed that. exactly same result (no surprise, qjackctl is only a gui)
Somehow it's connected to captuure, see above playback only exercise.
Starting on the Clockmender approach...
Thanks to all
Don

---

### Post by buffler on 2014-04-20
OK,  Rather than go a lot more complicated, I plugged in a simple USB soundcard that's kicking around. Choosing that in qjackctl setup as separate input and output worked. I got Jack to start at least.  Why I couldn't get the internal card to work who knows? Maybe I goofed it in alsamixer. Because I'm trying to hook two programs together, next will be Jack with loopbacks.  
Don

---

### Post by buffler on 2014-04-20
OMG I needed channels set to 2. Flat forehead, apologies all around! channels, ports, yikes...
Don

---

### Post by buffler on 2014-04-22
close this thread?
Thanks to all!
Don

---

### Post by jejeman on 2014-04-22
Just mark it as "Solved" if it is.

---

### Post by chkneater on 2014-04-22
Another thing to check for is sometimes when you start Jack it will automatically want to use the HDMI instead of your sound card. The only way I know ot fix it is in the Jack settings click on playback/capture until the the 'interface' face field is open and you can change interfaces.  Small gitch in jack, with THEY would FIX it??!!!
T

---

