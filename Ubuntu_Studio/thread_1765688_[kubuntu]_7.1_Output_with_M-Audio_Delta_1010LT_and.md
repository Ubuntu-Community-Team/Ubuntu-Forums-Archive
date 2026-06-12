---
title: "[kubuntu] 7.1 Output with M-Audio Delta 1010LT and Jack on Kubuntu Install"
date: 2011-05-23
forum: Ubuntu Studio
---

### Post by megamasha on 2011-05-23
I have two problems - one getting all my inputs and outputs to work, and the other getting the Jack server to start.

A little background (skip to fourth paragraph for problem): I used to have Kubuntu and Ubuntu Studio installed separately, but I don't like The Ubuntu Studio Desktop Environment or Theme, Couldn't get Amarok to work properly on Ubuntu Studio, and didn't like having to Open Jack the whole time just to get speaker output. Plus my system was generally unstable,

So Instead of upgrading (I think it was Kubuntu 10.04 and Ubuntu Studio 09.10), I've built a new system (Athlon II X3, 4GB RAM, Radeon HD5670) and put my M-Audio Delta 1010LT in it. I have installed Kubuntu 11.04 on the system, and generally it works like a dream - I feel much happier working with it than I did with Ubuntu Studio.

My sound card has 10 outputs and 10 inputs, I have a 5.1 system plus a hi-fi system combined to make 7.1.
First Problem:
I used to be able to output in 7.1 from Audacious through Patchage under Ubuntu Studio.
Now under Kubuntu I can't get Amarok (or namely Phonon) to output on anything more than 5.1 - There's no option for 7.1 in the control panel. I read somewhere that Phonon isn't really designed to have advanced options. Can I enable all 10 inputs and outputs with Phonon or do I need to replace it with something else?

Second Problem:
Now I have installed Jack control and some of the other programs from Ubuntu Studio because I want to do music production as I did on my previous system, but Jack won't start.
Here's the message output:
 p, li { white-space: pre-wrap; }```
16:40:35.367 Patchbay deactivated.
 16:40:35.419 Statistics reset.
 16:40:35.484 ALSA connection change.
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 16:40:35.494 ALSA connection graph change.
 16:40:55.341 JACK is starting...
 16:40:55.341 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2 -i10 -o10
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 16:40:55.407 JACK was started with PID=5991.
 Cannot create thread 1 Operation not permitted
 Cannot create thread 1 Operation not permitted
 jackdmp 1.9.7
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 10
 Cannot lock down memory area (Cannot allocate memory)
 control device hw:0
 control device hw:0
 audio_reservation_init
 Acquire audio card Audio0
 creating alsa driver ... hw:0|hw:0|1024|2|44100|10|10|nomon|swmeter|-|32bit
 control device hw:0
 Using ALSA driver ICE1712 running on card 0 - M Audio Delta 1010LT at 0xd800, irq 20
 configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
 ALSA: final selected sample format for capture: 32bit integer little-endian
 ALSA: cannot set channel count to 10 for capture
 ALSA: cannot configure capture channel
 Cannot initialize driver
 JackServer::Open() failed with -1
 Failed to start server
 16:40:55.580 JACK was stopped with exit status=255.
 16:40:57.523 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started

```After I try to start The Jack Server, Amarok won't play anymore (even though Jack failed to start). It works again if I quit Jack Control.
Ideally I'd like them to be able to run simultaneously

I'm afraid I don't really understand a lot of the inner workings of Ubuntu or the sound stack, but on the other hand, I'm a quick learner, I'm not stupid, and I'm very willing to give all the information I can.

I hope someone is able to help me here,

MM

A final note:
I'm wondering If perhaps I've done this the wrong way around... Could I have (and would it be easier to configure if I had) Installed Ubuntu Studio and then slapped KDE, all the KDE apps and the Oxygen theme on top of that, then uninstalled the ubuntu studio packages I don't want (That's two thirds of them!)? I don't really want to have to reinstall my computer from scratch again, but if it's the ONLY way of making it work, I would consider it. That said, given that they're basically the same operating system, I find it hard to believe there isn't a way to achieve this from where I am.

---

### Post by Pablo_F on 2011-05-23
Hi, 

Before anything else, what are your user limits for rtprio and memlock? You can see it via this command:

ulimit -r -l

Cheers, Pablo

---

### Post by megamasha on 2011-05-23
> **Pablo_F said:**
> Before anything else, what are your user limits for rtprio and memlock?

real-time priority              (-r) 0
max locked memory       (kbytes, -l) 64

I'm guessing real-time should be 1?
And 64kb Locked memory doesn't sound like very much to me!:shock:

Perhaps I should start by changing them... Can you tell me how?

Thanks,

MM

---

### Post by Pablo_F on 2011-05-23
> Perhaps I should start by changing them... Can you tell me how?

Yes. As explained in jackaudio.org, jack needs rtprio and memlock privileges to run smoothly in realtime mode. 

In Debian/ubuntu, the easy way to do it is via a dialog that pops up when you install the jackd package (in natty, jackd2 package). In case you don't remember, or chose the default "No", you can always invoke it again with this command:

**sudo dpkg-reconfigure -p high jackd2**

Selecting "Yes" creates the file */etc/security/limits.d/audio.conf* where these priviliges are set for the members of the audio group. So, to complete the process, you or whatever be the user who will run jack must be a member of said group. You can do it this way:

**sudo adduser your_user_name audio**


Indeed, you don't need to reinstall the system, ubuntustudio is basically ubuntu.

Your jackd command:

```
/usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2 -i10 -o10
```

Do not set up channel number in Jack Control. Leave it as (default). The driver knows.

As you are running jackd2, it usually behaves better (at least for me) and it has less latency in synchronous mode. Append *-S* to the jackd command, in the "server path" field (*/usr/bin/jackd -S* or just *jackd -S*).

jack is _another_ sound server, different from pulseaudio, the default in ubuntu (and, somehow surprisingly, in ubuntustudio). Jack clients (so-called jack-aware applications) include most of the apps you use to make music and also most multimedia players as long as you "jackify" them. You can google for "multimedia players through jack".

Alternatively, there are workarounds so you can have both pulseaudio clients and jack clients sharing the audio card.

Patchage is a patchbay for jack clients (better said, for jack audio and jack MIDI and for alsa MIDI aswell as many apps do jack audio but alsa MIDI) 

Last but not least, the m-audio 1010LT can be controlled (levels, hardware configuration, internal mixer...) by means of a program called "envy24control" which belongs to the "alsa-tools-gui" package. Normally, default configuration is good enough, so you don't need to use it that much. 

Cheers, Pablo

---

### Post by cchhrriiss121212 on 2011-05-23
You need to set the input and output channels to "default", then jack should start.

---

### Post by megamasha on 2011-05-23
Firstly, let me say thanks for the responses so far. They're really helpful, well-written and relevant.

OK, So I've now got
real-time priority              (-r) 95
max locked memory       (kbytes, -l) unlimited

This looks much better.

> **Pablo_F said:**
> Your jackd command:

```
/usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2 -i10 -o10
```Do not set up channel number in Jack Control. Leave it as (default). The driver knows.

I suspected this might be unnecessary, so had already set both back to default, but thanks for the suggestion.

> **Pablo_F said:**
> As you are running jackd2, it usually behaves better (at least for me) and it has less latency in synchronous mode. Append *-S* to the jackd command, in the "server path" field (*/usr/bin/jackd -S* or just *jackd -S*).

I have tried adding -S to the command line as suggested.
Jack still won't start, giving the following output:

 p, li { white-space: pre-wrap; }```
22:04:25.370 Patchbay deactivated.
 22:04:25.375 Statistics reset.
 22:04:25.395 ALSA connection change.
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 22:04:25.404 ALSA connection graph change.
 22:04:32.229 JACK is starting...
 22:04:32.230 /usr/bin/jackd -S -dalsa -dhw:0 -r44100 -p1024 -n2
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 22:04:32.282 JACK was started with PID=2518.
 no message buffer overruns
 no message buffer overruns
 jackdmp 1.9.7
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 10
 control device hw:0
 control device hw:0
 audio_reservation_init
 Acquire audio card Audio0
 creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 Using ALSA driver HDA-Intel running on card 0 - HD-Audio Generic at 0xfebbc000 irq 41
 ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
 Cannot initialize driver
 JackServer::Open() failed with -1
 Failed to start server
 22:04:32.427 JACK was stopped with exit status=255.
 22:04:34.493 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started

```To me, it looks like the problem is somewhere here:
```
Using ALSA driver HDA-Intel running on card 0 - HD-Audio Generic at 0xfebbc000 irq 41
  ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
  Cannot initialize driver
  JackServer::Open() failed with -1
  Failed to start server
  22:04:32.427 JACK was stopped with exit status=255.

```But I have no idea what I can do about it. Any idea why it 'Cannot open PCM device alsa_pcm for playback'?

> **Pablo_F said:**
>  jack is _another_ sound server, different from pulseaudio, the default in ubuntu (and, somehow surprisingly, in ubuntustudio). Jack clients (so-called jack-aware applications) include most of the apps you use to make music and also most multimedia players as long as you "jackify" them. You can google for "multimedia players through jack".

Alternatively, there are workarounds so you can have both pulseaudio clients and jack clients sharing the audio card.

Can I 'jackify' Programs such as Firefox and my instant messenger so that I still get sound on YouTube and instant messaging/facebook chat?
Otherwise the audio card sharing workaround might be the more attractive option for me. I recall much aggravation as on my previous system I ended up using one socket on my built-in sound card for the browser, video player etc. and my PCI card for jack output.

> **Pablo_F said:**
> Last but not least, the m-audio 1010LT can be controlled (levels, hardware configuration, internal mixer...) by means of a program called "envy24control"

Indeed, I've already installed Envy24Control and with its help, enabled output on more than the first two channels (it seems by default, the volume on all other channels was right down).
So now my sound card has output enabled on the first 8 analog output channels, but the software (phonon) is only feeding it 6 channels of sound.

I'm going to try changing the hw options.
I'll let you know on my results...

---

### Post by megamasha on 2011-05-23
OK, I've just realised what might have been the problem: Comparing these two lines of code from my first and last post, Jack switched to a different card (it was always set to default, so it would seem the default changed, and I have no idea why.
First post: Using ALSA driver ICE1712   running on card 0 - M Audio Delta 1010LT at 0xd800,    irq 20
Last  post: Using ALSA driver HDA-Intel running on card 0 - HD-Audio Generic     at 0xfebbc000 irq 41

Any idea why the default device might change spontaneously? Anything to do with Amarok being open or closed? I'm just guessing here - because I can't think of a good reason.

I've now set it to hw1 which is now the ICE1712 card and the server starts, though I've not yet checked how many outputs work, or whether I can route other programs through it.
I'll keep you posted.

MM

---

### Post by Pablo_F on 2011-05-23
EDIT: I did not see your last post, but see below. 


> OK, So I've now got
real-time priority (-r) 95
max locked memory (kbytes, -l) unlimited

This looks much better.

Yes!

> Any idea why it 'Cannot open PCM device alsa_pcm for playback'?

No, but who cares. From jack messages:
```
Using ALSA driver HDA-Intel running on card 0 - HD-Audio Generic at 0xfebbc000 irq 41
```

So, right now, hw:0 is not the m-audio but some onboard audio interface. You need to tell jack to use the m-audio. Surprisingly, in a previous attempt (from post #1):

```
Using ALSA driver ICE1712 running on card 0 - M Audio Delta 1010LT at 0xd800, irq 20
```

So what the flip is up? Card numbers have changed! So, either you make sure every time in qjackctl's setup that jack is using the m-audio or you do something to avoid it. 

The recommended way to avoid the card confusion is using names instead of numbers. Look at the terminal output of *cat /proc/asound/cards*. The name between square brackets. I think the m-audio 1010LT is identified as "1010LT" (check it!). So, in the interface field you write down:

hw:1010LT

(even if you don't see the option in the drop down menu). 

> Can I 'jackify' Programs such as Firefox and my instant messenger so that I still get sound on YouTube and instant messaging/facebook chat?
You can jackify the flash player (youtube, etc) but I don't think it is a good idea. You'd better load module-jack-sink from pulseaudio-module-jack.

I am not sure, but I think the lack of 7.1 is a pulseaudio issue, not phonon or hardware. Once you have jack up and running on the m-audio, connect manually via patchage or qjackctl (Connection window).

Cheers, Pablo

---

### Post by megamasha on 2011-05-23
> **Pablo_F said:**
> The recommended way to avoid the card confusion is using names instead of numbers. Look at the terminal output of *cat /proc/asound/cards*. The name between square brackets. I think the m-audio 1010LT is identified as "1010LT" (check it!).

I've set both the interface fields to 'hw:M1010LT', and it seems to start alright. This is good :-)

> **Pablo_F said:**
> You'd better load module-jack-sink from pulseaudio-module-jack.

> **Pablo_F said:**
> Once you have jack up and running on the m-audio, connect manually via patchage or qjackctl (Connection window).

Am I right in thinking this would then route the output of PulseAudio into jack as an input? If so, that would suit me perfectly. Then I could just route the sum of front and rear left to the left channel and front and rear right to the right channel:-)

I've looked at running PulseAudio with jack at [https://wiki.archlinux.org/index.php/PulseAudio#Pulseaudio_through_JACK](https://wiki.archlinux.org/index.php/PulseAudio#Pulseaudio_through_JACK) (seems to be a good source), and it mentions needing to start jack before PulseAudio. Only problem is (ok, problemS ARE):
I'm fairly sure PulseAudio is loaded on startup,
I'd like jack to be loaded that way too but at the moment it isn't,
and I have no idea which scripts are run at system startup (is there a linux equivalent of config.bat, or msconfig or something?),
or where they're stored
or how to edit them (although the site does give some code for putting into these config files, wherever they are).

Where are the audio config files stored? I assume I'd have to sudo edit them in Kate or some other text editor?

MM

---

### Post by Pablo_F on 2011-05-24
> I've looked at running PulseAudio with jack at [https://wiki.archlinux.org/index.php...o_through_JACK](https://wiki.archlinux.org/index.php...o_through_JACK) (seems to be a good source), and it mentions needing to start jack before PulseAudio. Only problem is (ok, problemS ARE):
I'm fairly sure PulseAudio is loaded on startup,

No, you don't need to start jack before pulseaudio, and yes, pulseaudio is loaded at start up. Well, at least in ubuntu.

You need to install a package called "pulseaudio-module-jack". So:

sudo apt-get install pulseaudio-module-jack

Qjackctl can run scripts and commands. Setup window, Options, script after server start (the second field), write down:

pacmd load-module module-jack-sink channels=8

The script before server stop could be:

pulseaudio -k

(kill pulseaudio before jackd). Pulseaudio will be restarted automatically in a few seconds (autospawn) if you stop the jack server.

Now, start the jack server and look at the jack connections via qjackctl or patchage. 

Make sure that pulseaudio is using the jack sink. In KDE, I don't know how you do it, but you can always "sudo apt-get install pavucontrol" (Pulseaudio volume control, which also allows routing connections between pulseaudio clients)


> I'd like jack to be loaded that way too but at the moment it isn't,
A two-click solution: The above plus "qjackctl" in "Applications at start-up" (at least in gnome).
A one-click solution: The above and "start server at application start" (or similar) in qjackctl setup, other options.
No-click solution: A bash script that starts the jack server and loads the pulseaudio sink, executed at start-up.


> Where are the audio config files stored?
In many places. Pulseaudio config files are in /etc/pulse (system wide) and /home/user/.pulse/ (per user). 

Yes, you can use kate, or vi, or nano, or whatever your favourite text editor. However, those arch instructions are over-complicated, imho.

Scroll down to Pulseaudio header in this manual:
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

My proposal is a bit simpler (put the command in qjackctl so you don't have to launch it manually each time and don't use the pulseaudio-jack-source) and for 8 channels instead of 2.

> and I have no idea which scripts are run at system startup (is there a linux equivalent of config.bat, or msconfig or something?),
or where they're stored

Equivalent is not the word. Afaik, in /etc/init but you have graphic tools as I mentioned. Google is your friend.

Cheers, Pablo

---

### Post by megamasha on 2011-05-25
OK, I think we're good!

I added jack to the auto start list, and set it to start in the system tray so it doesn't clutter my Task Manager.

For anyone else reading this, Jack will get confused if you have your open applications (session) saved and loaded on shutdown and startup as well - You'll have jack restored from last session and jack from auto start. They may both run , they may not. If you quit one, the other gets disconnected too.

So either

- don't save your sessions,
- add jack to the list of apps to be excluded from saved sessions
  -or-
- don't put jack in your auto start.

If jack still throws up errors on startup, you might want to increase the 'Start Delay (Secs)' in the options to give it time to do all the things it needs to while the computer is also doing whatever else it does on startup.

Getting jack and pulseaudio to work together using jack sink took a couple of restarts but was pretty easy.

So now I can finally use Amarok at the same time as Muse, Hydrogen, ZynAddSubFX etc. and all without any manual configuration at boot.

:D

Let the music creation commence...

---

