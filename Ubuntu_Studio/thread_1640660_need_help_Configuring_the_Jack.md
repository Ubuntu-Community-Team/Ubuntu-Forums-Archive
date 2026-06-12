---
title: "need help Configuring the Jack"
date: 2010-12-08
forum: Ubuntu Studio
---

### Post by somuchdirt74 on 2010-12-08
Im new to ubuntu I have the latest versions installed. I dont know much about ubuntu but I just cant seem to find or fix this problem. 
When I start up ardour for recording. pops this up

There are several possible reasons:

1) You requested audio parameters that are not supported..
2) JACK is running as another user.

Please consider the possibilities, and perhaps try different parameters.

So looking to fix this problem I came across this [http://www.ardour.org/node/2384](http://www.ardour.org/node/2384)
I typed in the terminal fuser /dev/snd/pcmC0D0p and it said 1900m tried it a different time and it shows 4405m but Im unable to kill these or not even really sure if I should or if im just typing the commands wrong, idk .

Then I start seeing stuff about Qjackctl (Jack Control). I have it downloaded and Ive seen in some post that I should start that up before starting ardour. Im confused on setting this up.  In the jack control I clicked on Connect, clicked on ALSA tab, and I see my interface there. Im using alesis io2 interface connected usb. So what I did here was clicked on io|2 in the ouput port, and also in the input port that was shown in the ALSA tab. then i press connect, is this what Im supposed to be doing?
So clicking on start when doing that setting I get this 

Could not connect to JACK server as client.
 - Overall operation failed.
 - Unable to connect to server.
 Please check the messages window for more info.

Thanks.

---

### Post by BcRich on 2010-12-08
hi somuchdirt74
are you trying to capture audio or midi. As far as my experience goes with JACK I've only used the ALSA tab in the connection dialog to set up midi connections.
Regarding recording audio into Ardour.
I first start JACK, then Ardour
In Adrour click Add track/Buss, Add a track
In Ardour click Window > Show Mixer
In the Ardour Mixer Under the name of the track that I just created (eg Audio 1) is a button with some text on it (depending on your configuration it could say something like 3/4 or 1/2) click that button and choose Edit.
This brings up the track input dialog box.
I use a Lexicon Omega Audio Interface which allows me to record up to four tracks simultaneously. So for example if I want to record bus 1 or system:capture_1 as it's called on my setup. I click whatever is listed in the "in 1" field to remove it, then click system tab and choose capture_1. you can also route two inputs into a track this way, if you like by using a stereo track in the Add track/Buss dialogue.
once you have that setup recording is pretty straight forward, click the record button on the track them click the record transport button, then the play transport button.
hope that helps?

---

### Post by somuchdirt74 on 2010-12-08
Yes I'm trying to record audio, and thanks.  When ardour had little startup window it list the driver, interface sample rate etc so I just change the interface to usb audio, started up jack before I run ardour and yeah Im finally able to get ardour opened up, without doing this im unable to open ardour, and also please let me know if need to use a different driver other than ALSA in the menu I was talking about for recording audio. Thanks for your input as of right now Im not able to test for sound but Im sure if I do what you told me it should work, cause I see what your talking about when it comes to add the track and edit, if im unable to get it to work Ill let ya'll know..

but now I get this message before ardour opens up

WARNING: Your system has a limit for maximum amount of locked memory. 
This might cause Ardour to run out of memory before your system runs out of memory. 

You can view the memory limit with 'ulimit -l', and it is normally controlled by /etc/security/limits.conf

---

### Post by Pablo_F on 2010-12-08
Hi, 

You start the jackd server (which ardour needs) either by means of qjackctl (aka Jack Control) or by means of the audio configuration tab in ardour. Both are front-ends to set the options and parameters for jackd but they can have different default settings, particularly, the realtime option.

The realtime option means that jackd can be run with realtime priority (not to be confused with the realtime kernel) but, normally by default in a Linux system, a user can not run apps with realtime priority. The same for memlock. 

In short, jackd needs that the user who runs it has rtprio and memlock unlimited (or a high value of RAM) privileges. jackd can be run in non realtime mode but it is not recommended (you risk lots of xruns or drop-outs even at high latency). 

The way to achieve this is documented in more than a few forum threads, jackaudio site, etc. Look at the message window of Jack Control and check if there is a message like "cannot use realtime scheduling...".

Your card is supported by the alsa driver. So yes, use the alsa driver. However, note that in the connection window "alsa" does not refer to the driver but to the (alsa)-midi ports. You should see the audio ports in the audio tab.

What ubuntu version are you running?

---

### Post by somuchdirt74 on 2010-12-08
thanks.I am using ubuntu 10.10 the Maverick Meerkat this is what I did recently to fix the error


[B]sudo dpkg-reconfigure -p high jackd2
[/B]Then I chosed yes,"you want to lock down memory and have rtprio scheduling privilege."

**sudo adduser Lee audio**

When I started up ardour that message doesnt pop up anymore
However Im still unable to test for sound at the moment.

I dont know if Jack is running properly here  are the messages.

p, li { white-space: pre-wrap; } [COLOR=#999999]19:26:29.793 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]19:26:29.795 Statistics reset.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66CC99]19:26:29.869 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]19:26:30.038 ALSA connection change.[/COLOR]
 [COLOR=#999999]19:26:35.107 Startup script...[/COLOR]
 [COLOR=#990099]19:26:35.108 artsshell -q terminate[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 sh: artsshell: not found
 [COLOR=#999999]19:26:35.511 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]19:26:35.511 JACK is starting...[/COLOR]
 [COLOR=#990099]19:26:35.512 /usr/bin/jackd -dalsa -r44100 -p1024 -n2 -D -Chw:1,0 -Phw:1,0[/COLOR]
 [COLOR=#999999]19:26:35.516 JACK was started with PID=1913.[/COLOR]
 no message buffer overruns
 no message buffer overruns
 jackdmp 1.9.6
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 10
 audio_reservation_init
 Acquire audio card Audio1
 creating alsa driver ... hw:1,0|hw:1,0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 Using ALSA driver USB-Audio running on card 1 - Alesis io|2 at usb-0000:00:1d.2-1, full speed
 configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
 ALSA: final selected sample format for capture: 24bit little-endian
 ALSA: use 2 periods for capture
 ALSA: final selected sample format for playback: 24bit little-endian
 ALSA: use 2 periods for playback
 [COLOR=#999933]19:26:37.693 Server configuration saved to "/home/lee/.jackdrc".[/COLOR]
 [COLOR=#999999]19:26:37.695 Statistics reset.[/COLOR]
 [COLOR=#999999]19:26:37.714 Client activated.[/COLOR]
 [COLOR=#9999CC]19:26:37.742 JACK connection change.[/COLOR]
 [COLOR=#CC9966]19:26:37.770 JACK connection graph change.[/COLOR]
 [COLOR=#66CC99]19:26:48.523 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]19:26:48.557 ALSA connection change.[/COLOR]
 [COLOR=#CC9966]19:26:49.103 JACK connection graph change.[/COLOR]
 [COLOR=#CC9966]19:26:57.144 JACK connection graph change.[/COLOR]
 [COLOR=#CC9966]19:26:57.621 JACK connection graph change.[/COLOR]
 [COLOR=#9999CC]19:26:57.772 JACK connection change.[/COLOR]
 alsa_driver_xrun_recovery
 **** alsa_pcm: [COLOR=#CC0000]xrun of at least 0.177 msecs[/COLOR]
 [COLOR=#CC66CC]19:29:16.258 XRUN callback (1).[/COLOR]
 JackPosixMutex::Unlock res = 1
 JackPosixMutex::Unlock res = 1
 JackAudioDriver::ProcessAsync: read error, skip cycle
 [COLOR=#CC9966]19:31:02.491 JACK connection graph change.[/COLOR]
 [COLOR=#9999CC]19:31:02.646 JACK connection change.[/COLOR]
 [COLOR=#999933]alsa_driver_xrun_recovery[/COLOR]
 **** alsa_pcm: [COLOR=#CC0000]xrun of at least 0.109 msecs[/COLOR]
 [COLOR=#999933]JackPosixMutex::Unlock res = 1[/COLOR]
 [COLOR=#999933]JackPosixMutex::Unlock res = 1[/COLOR]
 [COLOR=#999933]JackAudioDriver::ProcessAsync: read error, skip cycle[/COLOR]
 [COLOR=#CC66CC]19:35:28.043 XRUN callback (2).[/COLOR]

---

### Post by Pablo_F on 2010-12-10
Hi, 

Jack is up and running. Try playing an audio file with aqualung and make sure aqualung's output are connected to system: playbacks in the audio tab of qjackctl connections window.

Or import a wav file into ardour. 

It is strongly recommended that you use the card name, not the card number in qjackctl. Why? Because card numbers can change when you reboot the computer (well, you can fix that in a conf file, but use names anyway, it is easier and safer) . How? Take a look at the terminal output of "cat /proc/asound/cards" . "arecord -l" and "aplay -l" are very useful too. Copy-paste them here if you wish.

Cheers, Pablo

---

### Post by somuchdirt74 on 2010-12-10
Thank you, I've tried recording through it and its working, only problem is that when I go back to the recording there some parts where it messes up (sounds like its skipping) especially when I do another track while one is playing, but Im thinking my laptop is just too slow or can't handle it or something I only have a 1g of ram

---

### Post by idi0tf0wl on 2010-12-10
Don't use JACK or Ardour - that's the best solution to this problem. Speaking as someone who does professional audio exclusively on Linux (including composition and full project recording/arranging) systems, neither of these technologies are worth anything (Ardour mostly because it relies on JACK, which is just shy of totally worthless). I really can't understand for the life of me why they're even things, to be honest. Don't mean to step on anyone's toes here, but seriously... Instead, familiarize yourself with programs like Audacity and LMMS - mostly Audacity, especially for recording; it's ugly, but damn if it don't get the job did.

Good luck!

---

### Post by somuchdirt74 on 2010-12-10
Well to be honest idiotfowl thats one of the reasons why I tried out Ubuntu and just to try out the OS to see if I like it but I  dig it. Ive tried recording with audacity, and good number of other recording software out there that were "professional" but they all did the same thing with this problem, ubuntu was just a hope to me when it came down to fixing it haha I just wanted something to record for demos that doesnt have horrible quality, but I guess its back to the 4 track for me.
Thanks everyone for the support.

---

### Post by BcRich on 2010-12-11
Hi somuchdirt74
it seems like you are encountering xruns during recording. Yes you are absolutely correct in assuming that system specs play a part in this, a faster cpu and more RAM would help (in a perfect world)... but if you that's not possible in JACK you can click on the setup button and in the setup dialog box you should be able to find two settings called Frames/Period and secondly Periods/Buffer.
The idea here is to get Frames/Period to be as high as possible without experiencing xruns and to keep Periods/Buffer to the lowest number without experiencing xruns.
In Jack in JACK if you click on thee messages button while JACK is active JACK will print something like this 
```
**** alsa_pcm:xrun of at least 0.017 msecs
```
when an xrun occurs. If this happens start by increasing the Periods/Buffer setting by 1 unit. Then try record or playback again of whatever was causing the xrun. If you still get xruns try dropping the Frames/Period setting, then testing again... you get the point :)
on my system that is a intel coreII duo with 2 GB RAM my Frames/Period are set to 512 and Periods/Buffer is set to 2. This allows me to have multiple tracks playing in ardour, with multiple tracks in rosegarden including external synths such as zynaddsubfx playing back without any xruns.
Also please note that when you modify these settings you compromise on Realtime interaction and increase the risk of noticable Latency. Keep an eye on the bottom right hand section of the JACK setup dialog, it estimates what the Latency on your system currently might be based on the settings mentioned above and yes, taking into consideration your system specs :)

---

### Post by Pablo_F on 2010-12-11
Some of us trying to help and one person is trolling against jack in the ubuntustudio forum :shock: 

At first, Jack is not easy to understand and configure but it is worth for sure, it is very good technology and ardour is fine for multitrack recording. Be patient, search and ask.

Admittedly, a four-track recorder is easier and quicker to set up than hard-disk recording. 

Cheers, Pablo

---

### Post by RobertoRecordo on 2010-12-18
I'm a noob, too, and had trouble getting JACK working, even with all of the execellent help on these forums.
 
My break through came when I went fot the absolutely simplest thing possible: I got Hydrogen to play a demo and tried to get it connected to JACK EQ - it has a level display.
 
To my surprise ;) following the advice I had gotten -step by step- got them working together.
1) start "Jack Control" aka QJackCtl
2) open both of the applications (hydrogen and JACK EQ)
3) go back to JACK and open "Connections - Jack Audio Connections Kit". You get to it from the JACK front panel if it isn't open.
4) highlight Hydrogen in the left panel and JACKEQ in the right panel and click the connect button at the bottom left.
5) start a demo in Hyrdrogen (project/open demo) and play it - the loop button keeps it playing over and over.
6) look at JACKEQ while the demo is running in Hydrogen. If the indicators are boucing, you are JACKED!
 
Once I got that, connecting Hydrogen to my m-audio outputs, or a Mic to JACKEQ were easy. It's the "hello world" part, when I had no idea if any thing is working, that was a problem for me.
 
I hope this helps - if it doesn't get you going, then you can ask really specific questions and the good people will help you more than I can, I'm certain

---

### Post by Pablo_F on 2010-12-18
Hi Roberto, 

Just for clarification:

4 & 6) If you connect hydrogen L & R outputs to jackeq inputs (say channel 1 inputs) you see the meters bouncing but you need to disconnect hydrogen outputs from system playbacks and connect jackeq outputs to them so that you can actually use the EQ.

In addition to qjackctl connections window, in order to make jack connections you can use patchage (easier and more intuitive than qjackctl) or use the connections tools that some apps (including jackeq) provide. 

You are right, this is not rocket science.

Cheers, Pablo

---

### Post by trulan on 2010-12-18
> **Pablo_F said:**
> Some of us trying to help and one person is trolling against jack in the ubuntustudio forum :shock: 

At first, Jack is not easy to understand and configure but it is worth for sure, it is very good technology and ardour is fine for multitrack recording. Be patient, search and ask.

Admittedly, a four-track recorder is easier and quicker to set up than hard-disk recording. 

Cheers, Pablo
Having started making recordings on a 4-track tape deck back in the early '90's, then moving on to multi-tracking in Windows, and finally installing Ubuntu Jaunty in May of 2009, discovering JACK was like finally coming home.  I can't imagine having to put up with the restrictions of any other recording setup.  I also can't imagine actually trying to produce a CD using only Audacity - like using a chainsaw to carve a small figurine.  Hey, there are times you absolutely need a good chainsaw - but if it's your only tool, you are pretty limited.

Okay, enough with the analogies and the rant - just wanted to put in a good word for JACK and Ardour. ;)

---

### Post by RobertoRecordo on 2010-12-18
> **Pablo_F said:**
> Hi Roberto, 
 
Just for clarification:
 
4 & 6) If you connect hydrogen L & R outputs to jackeq inputs (say channel 1 inputs) you see the meters bouncing but you need to disconnect hydrogen outputs from system playbacks and connect jackeq outputs to them so that you can actually use the EQ.
 
<snip<
 
Cheers, Pablo
 
Absolutely true for the next "baby step" which is hearing the demo on speakers or headphones. My point was that if you are working with untested hardware ( in my case an m-audio delta 1010 and some cables and their routing and a mixer and it's settings!) there is a way to see JACK work in a simpler way.
 
And for clarification, I did not have to do anything with the L&R input/output, nor expand the <what's the word?> Icons and view the individual i/o, just select and connect. Apparently the gui is smart enough to know some defaults. Don't ask me, I'm a NOOB!
Regards,

---

### Post by 4ms on 2010-12-19
RobertoRecordo,
Thank you!
I've been working on getting a hello world thing for a few days now with no luck.

I reinstalled Ubuntu Studio 10.10 earlier today.  I had several issues, but the step by step really helped.

I got hydrogen to work with jackeq and then got sound out - which was what I was trying to do to just see if it was working.

Then I got sound from zynadsubfx - and also hooked up the virtual midi keyboard and that worked as well (on the alsa tab of jack connections).

One issue that's still getting me is infinite loop:
```
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle

```
I solved it (sort of) based on advice in:
[http://us.generation-nt.com/answer/bug-598972-jackd2-infinite-loop-startup-help-200551891.html](http://us.generation-nt.com/answer/bug-598972-jackd2-infinite-loop-startup-help-200551891.html)
It looks like the issue was a playback problem.
Starting jack with 
$ jackd -d alsa -P  
did allow jack to run for the first time without the infinite loop
And then I was able to achieve the same effect (playback only) by setting input to /dev/audio 
Result was same - playback only and no xrun loop, but /dev/audio does not exist and so jackctl messages has:

```
creating alsa driver ... hw:0|/dev/audio|1024|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xfe9f8000 irq 16
ALSA lib pcm.c:2208:(snd_pcm_open_noupdate) Unknown PCM /dev/audio
ALSA: Cannot open PCM device alsa_pcm for capture. Falling back to playback-only mode
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
```

Also, based on advice in:
[http://www.linuxmusicians.com/viewtopic.php?f=27&t=2968](http://www.linuxmusicians.com/viewtopic.php?f=27&t=2968)
I loaded and ran the alsa-info script.  My ALSA information is located at 
[http://www.alsa-project.org/db/?f=e11a7be43dbfd855112489663e703c6e7a50dc31](http://www.alsa-project.org/db/?f=e11a7be43dbfd855112489663e703c6e7a50dc31)

My next step is to hook it to the external sysntesizers but I'm not sure that's going to work with the input disabled...

Advice welcome.

bottom line is I don't know what's really causing the xrun loop - though a partial solution is to force jack into playback only mode.  I want to be able to use inputs now...

thanks again!
joseph

---

### Post by 4ms on 2010-12-19
a bit more info - and some diags without going to the alsa-info site:

dadmin@camper:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
dadmin@camper:~$ 

dadmin@camper:~$ cat ~/.jackdrc
/usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2

dadmin@camper:~$ lspci |grep -i audio
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
dadmin@camper:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe9f8000 irq 16
dadmin@camper:~$ cat /proc/asound/modules
 0 snd_hda_intel


If I try a real input like input default or hw:0 or hw:0,0 or 0,1 (digital), or 0,2, jack messages gives:
12:58:09.522 Patchbay deactivated.
12:58:09.695 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
12:58:09.735 ALSA connection graph change.
12:58:10.031 ALSA connection change.

START JACK:
12:59:27.951 Startup script...
12:59:27.952 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
12:59:28.355 Startup script terminated with exit status=32512.
12:59:28.355 JACK is starting...
12:59:28.356 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
12:59:28.372 JACK was started with PID=1859.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xfe9f8000 irq 16
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
.....
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle
12:59:30.214 JACK is stopping...
jack main caught signal 15
alsa_driver_xrun_recovery
JackAudioDriver::ProcessAsync: read error, skip cycle

STOP JACK:
Released audio card Audio0
audio_reservation_finish
12:59:30.334 JACK was stopped successfully.
12:59:30.335 Post-shutdown script...
12:59:30.336 killall jackd
jackd: no process found
12:59:30.748 Post-shutdown script terminated with exit status=256.

thanks again,
joseph

---

