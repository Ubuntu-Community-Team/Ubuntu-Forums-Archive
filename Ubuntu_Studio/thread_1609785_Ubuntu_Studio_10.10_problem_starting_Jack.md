---
title: "Ubuntu Studio 10.10 problem starting Jack"
date: 2010-10-30
forum: Ubuntu Studio
---

### Post by stewartnairn on 2010-10-30
I have disabled my onboard sound card in BIOS
I want to connect my SH201, but can't seem to get jack started.

 cat /proc/asound/cards
gives me 

 0 [SH201          ]: USB-Audio - SH-201
                      Roland SH-201 at usb-0000:00:1d.7-3.4, full speed

which seems like a good start

aplay -l, however gives me

**** List of PLAYBACK Hardware Devices ****
[COLOR=Black]
i.e. a list of o devices, which I'm guessing may be part of the problem.

less /proc/asound/modules gives me

 0 snd_usb_audio

I am a member of the audio group
I have run Pulse Audio Manager gone to Server Information>Disconnect

when I start Jack and go to configure, on clicking the right pointing arrow next to the Interface box it offers the options of Default, or hw:0 SH-201. I choose the later and hw:0 appears in the little box

running Jack gives this

[/COLOR] [COLOR=Black]JACK server starting in realtime mode with priority 10[/COLOR]
 [COLOR=Black]audio_reservation_init[/COLOR]
 [COLOR=Black]Acquire audio card Audio0[/COLOR]
 [COLOR=Black]creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit[/COLOR]
 [COLOR=Black]Using ALSA driver USB-Audio running on card 0 - Roland SH-201 at usb-0000:00:1d.7-3.4, full speed[/COLOR]
 [COLOR=Black]ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode[/COLOR]
 [COLOR=Black]Cannot initialize driver[/COLOR]
 [COLOR=Black]JackServer::Open() failed with -1[/COLOR]
 [COLOR=Black]Failed to start server[/COLOR]
 [COLOR=Black][COLOR=#999999]01:03:28.225 JACK was stopped with exit status=255.[/COLOR][/COLOR]
[COLOR=Black]
[/COLOR]
[COLOR=Black][COLOR=#999999]"cannot open PCM device alsa_pcm for playback" jumps out at me, but have been unable to understand the significance.[/COLOR][/COLOR]
[COLOR=Black]
[/COLOR]
[COLOR=Black]
[/COLOR]
[COLOR=Black][COLOR=#999999]I am going to my bed after a long day of rebooting, reinstalling, plugging and unplugging, altering, twiddling, fiddling, configuring, reconfiguring, searching and generally going round in circles.[/COLOR][/COLOR]
[COLOR=Black][COLOR=#999999]
[/COLOR][/COLOR]
[COLOR=Black][COLOR=#999999]Any advice would be welcome so I have a better day tomorrow.[/COLOR][/COLOR]
[COLOR=Black][COLOR=#999999]
[/COLOR][/COLOR]
[COLOR=Black][COLOR=#999999]Thanks,[/COLOR][/COLOR]
[COLOR=Black][COLOR=#999999]
[/COLOR][/COLOR]
[COLOR=#999999][COLOR=Black]Stewart[/COLOR]
[/COLOR]

---

### Post by AutoStatic on 2010-10-31
Hello Stewart,

Try putting *hw:SH201* in the Interfaces box manually (you can delete its content and type it in). And try a periods setting of 3 instead of 2. And I think your Roland SH-201 cannot run at full duplex (so capture and playback at once), that's where the message probably stems from.

Best,

Jeremy

---

