---
title: "Fast Track Pro input not recognised"
date: 2010-04-01
forum: Ubuntu Studio
---

### Post by the downtown canon on 2010-04-01
Hi I'm just starting out on Ubuntu and linux...

I have an M-Audio fast-track pro and looking at other posts it should work out the box with the ALSA driver - The output is fine I can hear everything through the box but the input seems not to be detected. Pulseaudio recordingmeter does not pick up a thing. It's the same in jack or any program, the mic (which is working fine as I can hear it in the mix channel on the fast track) is not being picked up.

On sound preferences under the hardware tab it is there but gives only an option of 'analog sterio output'

 If I disable the on board sound card then on the input tab there is no device!

Any help much appreciated...

---

### Post by the downtown canon on 2010-04-01
In some other posts i've been seeing that it should come up as 2 devices - one in and one out - i can't tell how to check the drivers but in jack under interfaces there is hw:1 and hw:0 btu not hw:0,1 as would seem to be required. Any way to check the driver settings and add if needed?

Cheers.

---

### Post by cchhrriiss121212 on 2010-04-02
Firstly you should ignore anything to do with pulse audio, you can set levels using alsamixer. For using jack you should set the interface as hw:1 as that should be the fast track. You don't need to change any drivers, as the configuring will be done with jack.

If you have jack running (no errors when you press start), then you can see the in and out connection ports of the fast track in the connections window or by using a program called patchage.

---

### Post by the downtown canon on 2010-04-02
Right, here's a screen shot with as much info as I think relevant;

1. alsamixer shows card to be HDA ATI sb? shouldn't it be fast track?

2. In JACK settings when I select the interface as 1 (listed as fast track) the input and output need to be on default - if I change them then the interface reverts back to thedefault. this remains the same no matter if I have the on board sound card disabled in sound preferences.

3. I'm going to be using ardour so loaded up to check connections in the programme. In the patchbay you can see the input channels in ardour don't connect to anthing. There are 2 boxes for fast track though both of them are midi and therefore inactive.

Many thanks, your help is much appreciated.

---

### Post by cchhrriiss121212 on 2010-04-02
1. This is your onboard sound but I'm not sure how to change devices using alsa mixer, as my usb device is unsupported. If you try disabling the onboard sound then it might load the fast track by default. If you try alsamixer-gui then you can see the available cards on the proc window.

2. I would leave in/out on default unless you want to have the fast track for in and the onboard sound as out. Was that your intention?

3. My usb interface shows up as system in patchage, but yours has numerous boxes for alsa pcm. Do you know what those are? As they have capture ports I'm guessing they are the fast track, so try and connect them to ardour inputs.

---

### Post by the downtown canon on 2010-04-02
First things first - i tried to get the sound working consistently so used a beat in hydrogen to test. It works with hydrogen with the settings as interface > fast track (hw:1) and input / output as default (I didn't want the on-board to playback - only thought since the mic was not being picked up i had to select it) The code for hydrogen says;

```
SSE2 detected
cannot lock down memory for RT thread (Cannot allocate memory)
[ERROR]     Hydrogen          [audioEngine_process] Ladspa FX buffersize != nframes. FXBuffersize = 0
[WARNING]   JackDriver       [setBpm] 120
[WARNING]   JackDriver       calling jack_transport_locate(0)
[WARNING]   MainForm          

*** A newer version (v0.9.4) of Hydrogen is available at http://www.hydrogen-music.org

[WARNING]   JackDriver       calling jack_transport_locate(0)
[WARNING]   JackDriver       [updateTransportInfo] internal frames != jack transport frames. resync!
[WARNING]   JackDriver       calling jack_transport_locate(0)
[WARNING]   JackDriver       [updateTransportInfo] internal frames != jack transport frames. resync!

```

don't know what the warnings are about but i'm happy it works.

As for ardour when opening in the same settings there's no sound and no option for an input all modules displayed in patchage are midi. sometimes there's an option for system capture as an input and i got excited but still no sound and no recognition of mic input in ardour...aaaaaaaggggggghhhhhhhhhh

---

### Post by cchhrriiss121212 on 2010-04-02
You need to allocate more memory to your audio processes , which can be done by using ubuntu studio controls in the system menu. Half of your total RAM is recommended. That will get rid of that error.

> As for ardour when opening in the same settings there's no sound and no option for an input all modules displayed in patchage are midi.

This is might not be correct as I tried to explain before under #3 but I suppose I did not do a good job. On the screenshot you posted you can see various groups of alsa pcm with capture and playback ports in them and I think this might be the various inputs/outputs of your fast track. They have midi as their description, but they are not midi connections as they are always displayed in green, blue indicates that it is a sound port. They may just be mislabeled.

---

### Post by AutoStatic on 2010-04-02
What is the output of **aplay -l** and **arecord -l** in a terminal?

---

### Post by the downtown canon on 2010-04-02
> **AutoStatic said:**
> What is the output of **aplay -l** and **arecord -l** in a terminal?
```
thedowntowncanon@ubuntustudio-rob:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Pro [FastTrack Pro], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Pro [FastTrack Pro], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
thedowntowncanon@ubuntustudio-rob:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: Pro [FastTrack Pro], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Nearly there!
OK allocated memory, great solves that one, now;

1. With the settings as mentioned above no blue input boxes appear in patchage for ardour. no input.

2. If I keep the interface selected and change only input to fast track - same.

3. If I select input device as hw,1:1 - listed as usb device (got the idea from the arecord result, thanks!) then I get can image below in patchage. If I connect to master in I can hear my mic! WOW, I don't understand why really. On ardour I see the graphic on the master track. Now I guess it's a case of tinkering to get the right input configuration.
At the mo I can't hear the audio track playing on the master out only the click track... sure I'll figure it out tho, will post success when I have got it going.
thanks guys for your help...

---

### Post by the downtown canon on 2010-04-02
forgot the image

---

### Post by AutoStatic on 2010-04-03
You're welcome. Thanks you for posting the output. The Fast Track Pro has the ALSA designation 'Pro' so you could use that in QjackCtl also. So instead of 'hw:1' you can also use ```
hw:Pro
``` This way JACK always picks up the right soundcard, no matter what port you used for the Fast Track Pro and no matter what moment you plugged it in.
What is indeed weird is that the recording device has index hw:1,1. If you don't know that you'll be looking for ages why it doesn't work.

---

### Post by trulan on 2010-04-03
> **the downtown canon said:**
> At the mo I can't hear the audio track playing on the master out only the click track... 
The outputs of the tracks in Ardour need to be connected to the master bus input.  Ardour does this automatically but it probably got messed up while you were straightening out your soundcard issues.  Connect Audio 1 out to Master 1 in, Connect Audio 2 out to Master 2 in, connect Drums 1 out to Master 1 in, etc.

Using the same method you can also group your tracks in busses, for instance send all the vocals through one bus and all the instruments through another, then send both those busses into the Master one.  It's an incredibly flexible setup.

---

### Post by the downtown canon on 2010-04-03
> **AutoStatic said:**
>  The Fast Track Pro has the ALSA designation 'Pro' so you could use that in QjackCtl also. So instead of 'hw:1' you can also use ```
hw:Pro
```
How would I find this? I only see hw:1 or hw:0 or hw:0,1 etc. in the drop down list in QjackCtl...

Anyone know a good page describing what to do with the settings in QjackCtl - in particular what frames/period, period/buffer, port max, and timeout do?

Couple of issues - sometimes ardour or QjackCtl quits in the middle of doing something - is that normal? i kind of think it must be.
Yesterday I opened a project i'd been working on before dinner, (a couple of acoustic guitar tracks layered) and just had a wall of noise coming from the interface when i opened the project. I hadn't shut the system down so is it a case of overwork? opens up fine this morning...

---

### Post by the downtown canon on 2010-04-03
> **trulan said:**
> The outputs of the tracks in Ardour need to be connected to the master bus input.  Ardour does this automatically but it probably got messed up while you were straightening out your soundcard issues.  Connect Audio 1 out to Master 1 in, Connect Audio 2 out to Master 2 in, connect Drums 1 out to Master 1 in, etc.
that's exaxtly what had happened...

---

### Post by trulan on 2010-04-03
> **the downtown canon said:**
> that's exaxtly what had happened...
:DI could see that by your Patchage screenshot...A picture is sometimes worth a thousand words...

---

### Post by raboofje on 2010-04-04
> **the downtown canon said:**
> Anyone know a good page describing what to do with the settings in QjackCtl - in particular what frames/period, period/buffer, port max, and timeout do?

These are jack settings. Looks like jackd had no manpage or settings overview yet, but I found an old manpage which I updated and put at [http://trac.jackaudio.org/wiki/jackd%281%29](http://trac.jackaudio.org/wiki/jackd%281%29) .

'frames/period' is '--period', 'periods/buffer' is '--nperiods', 'port max' is '--port-max', 'timeout' is '--timeout'. Are you missing any information?

> Couple of issues - sometimes ardour or QjackCtl quits in the middle of doing something - is that normal?

Shouldn't be normal :). Do you see anything in the QjackCtl 'Messages' window, or in the console where you started the applications?

---

### Post by the downtown canon on 2010-04-05
cheers for the link - didn't see any messages will keep my eyes open...;)

---

### Post by AutoStatic on 2010-04-05
> **the downtown canon said:**
> How would I find this? I only see hw:1 or hw:0 or hw:0,1 etc. in the drop down list in QjackCtl...You have to enter it manually.

> Anyone know a good page describing what to do with the settings in QjackCtl - in particular what frames/period, period/buffer, port max, and timeout do?[http://wiki.linuxmusicians.com/doku.php?id=manuals_tutorials_and_howto_s#qjackctl](http://wiki.linuxmusicians.com/doku.php?id=manuals_tutorials_and_howto_s#qjackctl)

> Couple of issues - sometimes ardour or QjackCtl quits in the middle of doing something - is that normal?No. Does JACK or Ardour report any warning?

---

### Post by the downtown canon on 2010-04-05
thanks for the wiki link - ardour's been OK until just now when for some reason it quit. Opened it in terminal so it had this message

> ++++ JUST HIDING 1
Segmentation fault

when I started her back up again it was as I had left it about a minute before, one edit I had just done wasn't done so no big deal - I hadn't saved it for a while though so was grateful

---

### Post by trulan on 2010-04-05
In my experience, Ardour crashes occasionally when editing.  It is rock-solid when recording or playing, but when doing serious editing (where I'm stacking up some serious layers of Undo possibilities - does that have anything to do with it?) Ardour just will crash.  I've learned to save my work every few minutes while editing, and kind of gotten used to it.  Lots of cutting and pasting, start point and end point trimming, and region dragging, will eventually take it down.

A friend of mine suggested that my relatively slow processor (1.66Ghz) and 1gig ram may be somewhat to blame.  I've got a new machine on order (broke my firewire port) so I'll get a chance to see if he was right. ;)

---

### Post by OA-5599 on 2010-11-21
> **the downtown canon said:**
> 
3. If I select input device as hw,1:1 - listed as usb device (got the idea from the arecord result, thanks!) then I get can image below in patchage. If I connect to master in I can hear my mic! WOW, I don't understand why really. On ardour I see the graphic on the master track. Now I guess it's a case of tinkering to get the right input configuration.
At the mo I can't hear the audio track playing on the master out only the click track... sure I'll figure it out tho, will post success when I have got it going.
thanks guys for your help...


I know its an old thread. But maybe someone can help me. I think I've got the exact same problem. No input showing up. This is my aplay / arecord:

```
martin@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1828S Analog [VT1828S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1828S Digital [VT1828S Digital]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Pro [FastTrack Pro], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Pro [FastTrack Pro], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
martin@ubuntu:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1828S Analog [VT1828S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 2: Pro [FastTrack Pro], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

What's the number of my input device? I've tried all kinds of different combinations. But I can't get any input device.

---

### Post by cchhrriiss121212 on 2010-11-21
> What's the number of my input device? As mentioned in post #11 you can just type in hw:Pro in the interface selection box:
> This way JACK always picks up the right soundcard, no matter what port  you used for the Fast Track Pro and no matter what moment you plugged it  in.

---

### Post by OA-5599 on 2010-11-21
I've done that, still no input. Seems to be a different problem..

Edit: After I've done this:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/569932](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/569932)

```
1. Open the terminal
2. Type:
gksu gedit /usr/share/pulseaudio/alsa-mixer/profile-sets/maudio-fasttrack-pro.conf
(provide admin password)
3. In the opened document, locate the [Mapping analog-stereo-a-input] section.
4. Replace this line:
device-strings = hw:%f,0,0
With this:
device-strings = hw:%f,0,0 hw:%f,1,0
5. Save
6. Log out and then log in.
```

I can record in Audacity. Although it sounds very bad (a lot of noise). And still no input in jack. The device isn't broken. I've tried it with Windows (dual boot)

---

### Post by cchhrriiss121212 on 2010-11-21
What do you see under the connection window? Do you get outputs?
Could you also post the output from the jack message window, as well as "cat ~/.jackdrc" from a terminal.

---

### Post by OA-5599 on 2010-11-21
-I see 'playback_1' and 'playback_2' under 'system' in the connection window. Audio does play through jack. The outputs work.

-cat ~/.jackdrc:
```
/usr/bin/jackd -dalsa -dhw:Pro -r44100 -p1024 -n2
```

-Message window:
```
16:01:35.791 Patchbay deactivated.
16:01:35.799 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
16:01:35.815 ALSA connection graph change.
16:01:36.013 ALSA connection change.
16:01:40.105 Startup script...
16:01:40.105 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
16:01:40.507 Startup script terminated with exit status=32512.
16:01:40.507 JACK is starting...
16:01:40.507 /usr/bin/jackd -dalsa -dhw:Pro -r44100 -p1024 -n2
16:01:40.509 JACK was started with PID=2582.
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
Acquire audio card Audio2
creating alsa driver ... hw:Pro|hw:Pro|1024|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver USB-Audio running on card 2 - M-Audio FastTrack Pro at usb-0000:00:1d.0-1.4, full speed
ALSA: Cannot open PCM device alsa_pcm for capture. Falling back to playback-only mode
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
16:01:42.667 Server configuration saved to "/home/martin/.jackdrc".
16:01:42.667 Statistics reset.
16:01:42.678 Client activated.
16:01:42.679 JACK connection change.
16:01:42.681 JACK connection graph change.
```

---

### Post by cchhrriiss121212 on 2010-11-21
Try checking the force 16bit box. According to [this page]("http://alsa.opensrc.org/index.php/M-Audio_FastTrack_Pro"), the device will run at a max of 48KHz/16bit unless you apply a patch.
Relevant quote:
> It can sample and playback with up to 24bit, 96kHz but, due to the  insufficient bandwidth of USB1.1, will only work with **reduced channel  count** with anything higher than 16bit, 48 kHz

---

### Post by OA-5599 on 2010-11-21
I've tried that. No luck.

---

### Post by cchhrriiss121212 on 2010-11-21
You tried the patch? Could you try setting it to 16bit/48KHz with periods three, then post the message window again if it does not work.

---

### Post by OA-5599 on 2010-11-21
Not the patch, just the force 16-bit. Do you think I should try the patch?

---

### Post by cchhrriiss121212 on 2010-11-21
The patch couldn't hurt, but it should not be necessary given that the device works for so many others without it. Try it with the settings I mentioned earlier and with hw:1,1 in the input box.

---

### Post by OA-5599 on 2010-11-25
Sorry, I'm a bit late. Tried the settings you mentioned. Didn't work. I installed ubuntu studio because I thought it might work better with audio stuff, tried all the things I did earlier but didn't work either.

---

### Post by schef on 2011-02-01
I have soulved the problem.

[http://ubuntuforums.org/showthread.php?p=10417941]("http://ubuntuforums.org/showthread.php?p=10417941")

---

