---
title: "Guitar to usb sound blaster"
date: 2012-07-22
forum: Ubuntu Studio
---

### Post by Rulius on 2012-07-22
Hi,  

I 've been trying to connect my guitar to a usb sound blaster 24-bit but I can't seem to make it work. I'm running lucid lynx and my final goal is to use rakarrack or a similar software. 

The card is recognized and I'm able to use it with multimedia apps. The problem is I get no sound when I connect my guitar. 
I use jack audio connection kit and make a connection (system to system) but I get no sound.  Same result when I open rakarrack and make a connection through jack audio connection kit. 

The weird thing is that I am able to record and listen to my guitar (although too quiet) when I use audacity.  

Thanks for your time

---

### Post by jejeman on 2012-07-22
Check in alsamixer recording channel levels.

---

### Post by Rulius on 2012-07-22
Thanks for the reply.
I'm not sure what you mean.
When I type alsamixer to the terminal and select the sound card (sb live 24-bit) I only see pcm column, cmss led, power led.

Please be more detailed as I'm not very experienced.

---

### Post by sgx on 2012-07-22
> **Rulius said:**
> Hi,  

I 've been trying to connect my guitar to a usb sound blaster 24-bit but I can't seem to make it work. I'm running lucid lynx and my final goal is to use rakarrack or a similar software. 

The card is recognized and I'm able to use it with multimedia apps. The problem is I get no sound when I connect my guitar. 
I use jack audio connection kit and make a connection (system to system) but I get no sound.  Same result when I open rakarrack and make a connection through jack audio connection kit. 

The weird thing is that I am able to record and listen to my guitar (although too quiet) when I use audacity.  

Thanks for your time
audacity is using alsa, qjackctl needs jackd running, and specific connections

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl),

[https://help.ubuntu.com/community/Ho...CtlConnections](https://help.ubuntu.com/community/Ho...CtlConnections)

links 4 and 8, screenshots and info

(for a qjackctl usb sound i/o choose a
Periods/Buffer setting of 3  )

Click Setup on the main qjackctl gui. The entries in the qjackctl setup panel

Input device >
Output device >

click the > widgets for the dropdown list of your
soundcards

Once you choose your soundcard, (something like hw:1 hw:0,0 or even a brand named entry), you'll have to make various connections.

Feed an ongoing sound source to the soundcard inputs while you make connections, to hear when you are successful. alsamixergui is good at displaying every sound input/output, part of the alsa-tools package, if not separately. Sound may be muted at first install.

In the qjackctl connections panel (press Connect on the main gui)
you must choose input/output, and/or capture/playback for each software and hardware you want to use. The Alsa tab is for midi, the Audio tab is for audio capture/playback. Each has a left and right side, select and highlite an item you want from each side, and press this panels connect button (not the one on the main gui) and a connection line is drawn.

In the audio tab, the guitar sound output is on the left panel,
called System, and would be connected to your soundcards output,
also called system, on the right panel.
An fx app like rakarrack would show on the left and right panels,
so the guitar output would go to rakarrack input, and then
rakarrack output, would go to (System) your soundcards output.

In the Alsa tab, a softsynth would appear on the right panel
and a midi keyboards connection on the left panel,
select one on each side, and connect them, to send keyboard data to the softsynth.

You could install timemachine to test recording, and connect the sound outputs you choose, to the timemachine input, press record, and begin playing.

To record from jackd connections using audacity, choose jack in audacity preferences, press record, then press pause, look in
qjackctl for portaudio, which will be audacity. 
Make the desired connections, then press pause again
when ready to record.

qjackctl saves a text file, .jackdrc in /home/your-name, with your current setup. A few minutes reading the jackd manpage helps to absorb the options, most are configured in the qjackctl gui.

When usb devices are swapped in/out, you may have to re-select the
desired soundcard in the setup page, so don't panic.

[http://fclose.com/p/linux/man/1-jackd/](http://fclose.com/p/linux/man/1-jackd/)

You can make and keep special versions of .jackdrc as a text file to run as a command, for setups you use only occasionally.

some preamp will be desired to boost guitar signals for proper
levels, or, better

Get a Fender Mustang1 

[http://www.youtube.com/watch?v=Wl2Q8SNVnPU](http://www.youtube.com/watch?v=Wl2Q8SNVnPU)

usb amp/interface when you can,
$50-$80 used, $90-$110 new works great and easy in
linux, and with rakarrack, guitarix, calf plugins etc.

Cheers

Cheers

---

### Post by jejeman on 2012-07-23
> **Rulius said:**
> Thanks for the reply.
I'm not sure what you mean.
When I type alsamixer to the terminal and select the sound card (sb live 24-bit) I only see pcm column, cmss led, power led.

Please be more detailed as I'm not very experienced.
I don't have the sound card that you have, so I can't give you exact details.
But, in general, in alsamixer you have two sets of sliders. One for playback, other for capture. For sound to reach the applications you need to turn up capturing level using sliders in alsamixer.
Not all cards are eaquily supported, so maybe your card doesn't even have capture sliders. In that case, see if playback slider may have effect on capturing.

---

### Post by Rulius on 2012-07-23
Sqx, thanks for the reply

> **sgx said:**
> audacity is using alsa, qjackctl needs jackd running, and specific connections

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl),

[https://help.ubuntu.com/community/Ho...CtlConnections](https://help.ubuntu.com/community/Ho...CtlConnections)

links 4 and 8, screenshots and info

It says that Ho...CtlConnections page does not exist.
link 4 is Home server
link 8 is Horde4 Mail And Groupware Server

However, in 56 it says : HowToSetupSoundCards. Maybe this is the one you refer to.:confused:

> Once you choose your soundcard, (something like hw:1 hw:0,0 or even a brand named entry), you'll have to make various connections.

When I choose my card (hw1: sb live...) and hit start I'm getting this error:

 p, li { white-space: pre-wrap; }  [COLOR=#999999]19:56:51.459 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]19:56:51.832 Statistics reset.[/COLOR]
 [COLOR=#66cc99]19:56:51.854 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]19:56:52.155 ALSA connection change.[/COLOR]
 [COLOR=#999999]19:59:10.335 Startup script...[/COLOR]
 [COLOR=#990099]19:59:10.336 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]19:59:10.739 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]19:59:10.739 JACK is starting...[/COLOR]
 [COLOR=#990099]19:59:10.740 /usr/bin/jackd -dalsa -r48000 -p64 -n3 -D -Chw:1 -Phw:1[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 [COLOR=#999999]19:59:10.747 JACK was started with PID=2431.[/COLOR]
 no message buffer overruns
 JACK compiled with System V SHM support.
 cannot lock down memory for jackd (Cannot allocate memory)
 loading driver ..
 apparent rate = 48000
 creating alsa driver ... hw:1|hw:1|64|3|48000|0|0|nomon|swmeter|-|32bit
 control device hw:1
 configuring for 48000Hz, period = 64 frames (1.3 ms), buffer = 3 periods
 ALSA: final selected sample format for capture: 24bit little-endian
 ALSA: use 3 periods for capture
 ALSA: final selected sample format for playback: 24bit little-endian
 ALSA: use 3 periods for playback
 JACK: unable to mlock() port buffers: Cannot allocate memory
 ALSA: could not start playback (Broken pipe)
 DRIVER NT: could not start driver
 cannot start driver
 [COLOR=#999999]19:59:10.831 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]19:59:10.832 Post-shutdown script...[/COLOR]
 [COLOR=#990099]19:59:10.832 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]19:59:11.242 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]19:59:12.868 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]


Any ideas?

---

### Post by Rulius on 2012-07-23
> **jejeman said:**
> 
Not all cards are eaquily supported, so maybe your card doesn't even have capture sliders. In that case, see if playback slider may have effect on capturing.

I only have one slider (pcm) associated with master volume.

---

### Post by sgx on 2012-07-24
[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

the 4th and 8th in the External Links list
at this wiki, help (4) setup jackd, and
( 8 ) configure qjackctl.

Sorry for the lack of precision.

Is your username a member of the audio group? run command

groups

Is pulseaudio starting at boot? command:

killall pulseaudio

then start qjackctl.

The output of the lsmod command should have some

snd_emu10k1 snd_emu10k1_synth type entries,
quite a few, in several lines of the output.
Those are the creative labs kernel modules.

Cheers

---

### Post by Rulius on 2012-07-24
> **sgx said:**
> Is your username a member of the audio group? run command

groups

Yes "audio" is there.

> **sgx said:**
> Is pulseaudio starting at boot? command:

killall pulseaudio

then start qjackctl.

How do I check if pulseaudio is starting at boot?

I typed "killall pulseaudio" then "qjackctl", pressed start and got the same error as above.

> **sgx said:**
> The output of the lsmod command should have some

snd_emu10k1 snd_emu10k1_synth type entries,
quite a few, in several lines of the output.
Those are the creative labs kernel modules.

In lsmod I got the following entries starting with snd:

Module                  Size  Used by
snd_hda_codec_si3054     3396  1 
snd_hda_codec_realtek   203472  1 
snd_hda_intel          22069  5 
nf_nat_irc              1124  0 
snd_usb_audio          75765  2 
snd_usb_lib            15801  1 snd_usb_audio
snd_hda_codec          74297  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  7 snd_hda_codec_si3054,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_usb_lib,snd_seq_midi
snd_hwdep               5412  2 snd_usb_audio,snd_hda_codec
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  26 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_hwdep,snd_seq,snd_timer,snd_seq_device
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm


Also, I went to: alsa-project.org > creative labs soundcard list - and I wasn't able to find my soundcard. My chipset is SB0490 (usb sb live 24-bit)
However, module-usb-audio is the one listed for all the other usb cards and from lsmod I seem to be using that.

---

### Post by sgx on 2012-07-24
run two sets of these commands for comparisons, one without the card, then plug it in, and repeat, and note the differences. Output in brackets will be
a sound device

aplay -l
arecord -l
aconnect -i
acconnect -o
cat /proc/asound/cards
lsmod
lspci
lsusb

This will show you if and how, your soundcards are identified.

To rule out permissions problems, run

sudo qjackctl &rakarrack

if it works, other apps in the same session must also start with sudo,
can't have different audio users in the same session.

Then in general, make a textfile of useful output and solutuions
to build a manual for your personal system, over the coming months.
Cheers

---

### Post by Rulius on 2012-07-30
I stopped getting that error by setting the sample rate to 44100 istead of 48000 but still got no sound.
I have 2 captures and 6 playbacks and tried all possible combinations but no sound.

The card is there in both aplay -l and arecord -l:

card 1: External [SB Live! 24-bit External], device 0: USB Audio [USB Audio]
  Subdevices: 0/1

aconnect -i gives:

client 0: 'System' [type=kernel]
    0 'Timer           '
    1 'Announce        '
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'

aconnect -o gives:

client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'

cat /proc/asound/cards gives:

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdc240000 irq 22
 1 [External       ]: USB-Audio - SB Live! 24-bit External
                      Creative Technology SB Live! 24-bit External at usb-0000:0

Any suggestions?

---

