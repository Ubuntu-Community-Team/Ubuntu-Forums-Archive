---
title: "Using line/mic in with mixer and ubuntu studio"
date: 2010-10-01
forum: Ubuntu Studio
---

### Post by joggleh on 2010-10-01
Here's my issue:

I have my guitar amp mic'd to my phonic am120 mixer. This mixer has a rec output which you can use to record things (yeah it's true:p). However, ubuntu studio's JACK doesn't seem to recognise the line/mic inputs. I knew that in the regular ubuntu you can "activate" these inputs with the volume control, but this utility seems to be absent in studio.

Any help will be greatly appreciated;)

---

### Post by Pablo_F on 2010-10-01
Please, open a terminal and paste here the output of

cat /proc/asound/cards

and

aplay -l

Cheers! Pablo

---

### Post by joggleh on 2010-10-02
> **Pablo_F said:**
> Please, open a terminal and paste here the output of

cat /proc/asound/cards

and

aplay -l

Cheers! Pablo

Here you go:

```

joris@jorisboven:~$ cat /proc/asound/cards
 1 [PCM2702        ]: USB-Audio - Burr-Brown Japan PCM2702
                      Burr-Brown Japan Burr-Brown Japan PCM2702 at usb-0000:00:0f.2-1, full speed
joris@jorisboven:~$ aplay -l
**** Lijst van PLAYBACK hardware-apparaten ****
kaart 1: PCM2702 [Burr-Brown Japan PCM2702], apparaat 0: USB Audio [USB Audio]
  Sub-apparaten: 0/1
  Sub-apparaat #0: subdevice #0

```That USB Audio is my Sony home cinema system.


Edit: Yesterday i was able to get into alsamixer and "activate" my previously muted mic/line inputs, but when i try to open alsamixer now, it says: "cannot open mixer: files were not found" Aaargh......

---

### Post by Pablo_F on 2010-10-02
Well, forget about the ubuntu volume controls. That is related to pulseaudio and you want jack. What is more, your device probably has not an internal mixer (I am not sure and have no time to check it, sorry).

Is that all the output of cat /proc/asound/cards? You will probably have a onboard audio device which does have a mixer accesible by alsamixer. 

If you have two cards, hw:0 the onboard and hw:1 the usb, try 

alsamixer -c1

to try to open the alsamixer of the usb card, if there is any.

But you generally don't use alsamixer. You use the connection window of qjackctl.

In the setup of qjackctl (aka Jack Control) you should write down in the interface field:

hw: PCM2702  (without the space)

of course, use the alsa driver. Realtime mode. 

make the virtual connections through the connection window of qjackctl.
As a proof of concept, connect system:captures (card ins) to system: playbacks and check if you hear something.


 Use a jack-aware recorder, don't even try the gnome sound recorder. It won't work.

HTH, Pablo

---

### Post by joggleh on 2010-10-03
> **Pablo_F said:**
> Well, forget about the ubuntu volume controls. That is related to pulseaudio and you want jack. What is more, your device probably has not an internal mixer (I am not sure and have no time to check it, sorry).

Is that all the output of cat /proc/asound/cards? You will probably have a onboard audio device which does have a mixer accesible by alsamixer. 

If you have two cards, hw:0 the onboard and hw:1 the usb, try 

alsamixer -c1

to try to open the alsamixer of the usb card, if there is any.

But you generally don't use alsamixer. You use the connection window of qjackctl.

In the setup of qjackctl (aka Jack Control) you should write down in the interface field:

hw: PCM2702  (without the space)

of course, use the alsa driver. Realtime mode. 

make the virtual connections through the connection window of qjackctl.
As a proof of concept, connect system:captures (card ins) to system: playbacks and check if you hear something.


 Use a jack-aware recorder, don't even try the gnome sound recorder. It won't work.

HTH, Pablo

Thanks for the help! It's greatly appreciated. However, when I tried using the interface you mentioned, the messages window showed me this:

```
  p, li { white-space: pre-wrap; }  [COLOR=#999999]14:56:42.821 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]14:56:42.944 Statistics reset.[/COLOR]
 [COLOR=#66CC99]14:56:43.050 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]14:56:43.316 ALSA connection change.[/COLOR]
 [COLOR=#999999]14:58:17.469 Startup script...[/COLOR]
 [COLOR=#990099]14:58:17.470 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]14:58:17.871 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]14:58:17.871 JACK is starting...[/COLOR]
 [COLOR=#990099]14:58:17.872 /usr/bin/jackd -dalsa -dhw:PCM2702 -r48000 -p1024 -n2 -C[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 [COLOR=#999999]14:58:17.890 JACK was started with PID=1655.[/COLOR]
 no message buffer overruns
 JACK compiled with System V SHM support.
 cannot lock down memory for jackd (Cannot allocate memory)
 loading driver ..
 apparent rate = 48000
 creating alsa driver ... -|hw:PCM2702|1024|2|48000|0|0|nomon|swmeter|-|32bit
 ALSA: Cannot open PCM device alsa_pcm for capture. Falling back to playback-only mode
 cannot load driver module alsa
 [COLOR=#999999]14:58:18.180 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]14:58:18.181 Post-shutdown script...[/COLOR]
 [COLOR=#990099]14:58:18.181 killall jackd[/COLOR]
 jackd: geen proces gevonden
 [COLOR=#999999]14:58:18.628 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]14:58:19.959 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

```

I had some issues with my soundmax sound card in ubuntu, and it seems studio doesn't seem to recognise it either... Hmm, will try and edit the alsa-base file like I did back then.

---

### Post by Pablo_F on 2010-10-03
Please, 

Can you describe what you want to achieve? capture through the usb card, playback through what? 

If you select Audio Capture only, you should specify the input device rather than the interface, afaik. If you specify the interface as I suggested, choose default in the input and output devices and Duplex (this is the default) in the Audio field.

Cheers! Pablo

---

### Post by joggleh on 2010-10-03
> **Pablo_F said:**
> Please, 

Can you describe what you want to achieve? capture through the usb card, playback through what? 

If you select Audio Capture only, you should specify the input device rather than the interface, afaik. If you specify the interface as I suggested, choose default in the input and output devices and Duplex (this is the default) in the Audio field.

Cheers! Pablo

Thanks. JACK works fine again.

You're right, I haven't been clear about my intentions;). What I'm currently doing is setting up a little home studio to record some of my songs. I have a phonic am120 mixer (it looks like [this]("http://musicalka.com.ua/images/Phonic%20AM%20120.jpg")) and i connect the rec output on the mixer to the front mic input of my internal soundcard. I want to send the signal to ardour to record. 

The problem is the mic input is not recognised by ubuntu studio. I once got into alsamixer and saw the mic input was muted, so i put it on and pulseaudio device chooser recognised the mic input. But when i try to launch alsamixer in a terminal it says "alsamixer: no such file or directory".

---

### Post by Pablo_F on 2010-10-03
alsamixer not found? 

sudo apt-get install alsa-utils

It is strange that you don't have this package installed but who knows.


If you want to record to your onboard card, don't tell jack to use hw: PCM2702 but the onboard card.

Cheers! Pablo

---

### Post by joggleh on 2010-10-03
> **Pablo_F said:**
> alsamixer not found? 

sudo apt-get install alsa-utils

It is strange that you don't have this package installed but who knows.


If you want to record to your onboard card, don't tell jack to use hw: PCM2702 but the onboard card.

Cheers! Pablo

sudo apt-get install alsa-utils gave me that alsa-utils was up to date, so I used the package manager to manually search for alsamixer and installed it (it was not installed yet). I did a reboot, opened up alsamixer but what I got was an empty mixer (see the attachment below). 

I just realized how stupid I am, this is a problem with my soundcard, it's not software based. I mean, JACK doesn't even recognise my on-board soundcard after all! How can I use my mic input when my soundcard isn't working properly? 

Tis isn't the first problem with my sound card, with my regular ubunu install I didn't have sound at all. I fixed that with editing the alsa- base config file or something. I'll see if Google helps.

Many thanks though, you really helped me understand how to configure JACK and all. I'm sorry I kept you busy with this, my bad. I won't close the thread yet though, since the problem isn't solved yet.

---

### Post by joggleh on 2010-10-03
I thought i set everything right but where can I connect the mic and the ardour/system inputs in jack? I can't find them in patchbay?

---

### Post by Pablo_F on 2010-10-03
Use the connection window of qjackctl or use ardours' track/bus inspector or mixer.

The patchbay is for doing persistent connections and it is difficult for beginners. In adition, you don't need it as long as ardour is the only jack client (apart form the card itself) that you are using. Ardour will recall its connections. 

Connect the system: capture to the track input.

System is your card (any card is called "system"). Captures represent the input ports, playbacks the output ports. Normally, system: capture_1 corresponds to the first analog input, but this depends on the card that jack is using.

By the way, in the end, which soundcard are you using with jack? 

The onboard card seems missing. Have you enabled it in the BIOS? Anyway, if you won't use it, it is better if it is disabled from BIOS.

Cheers! Pablo

---

