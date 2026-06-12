---
title: "Single speaker output"
date: 2011-12-08
forum: Ubuntu Studio
---

### Post by Sylos on 2011-12-08
I have put this up on a thread on the laptop/hardware section but didnt get much response so Im putting it into the studio domain in the hope that those with alsa experience may be able to help.

I have just got a laptop with a single speaker output and Im only getting the left channel output through it. I have tried remapping a sink in pulse which works to get both left and right playing but the additive effect of the two 100% channels is causing massive clipping, speaker pop etc.

So Im asking if anyone can give me some guidance on how to stop the popping or how to achieve the output in a different way. I kinda think ALSA must be capable of it but cant wotk out how.

Also, the laptop os a present for my girlfriend so it would be best if any solution was automated and didnt require the use to jump hoops whenevr they want to use it. This may well rule out jack based solutions but for now I'll take any guidance.

And for now lets assume external speakers and headphones arent a suitable alternative.

Thanks

---

### Post by jejeman on 2011-12-08
Laptop has only one speaker? Interesting, which model is it?
Why don't you just lower the output volume?

---

### Post by satanselbow on 2011-12-08
> **jejeman said:**
> Laptop has only one speaker? Interesting, which model is it?
Why don't you just lower the output volume?

Don't think that is exactly what OP means... One MONO speaker? A tad unlikely...


Why not let have the useful information like...

Version of Ubuntu / Architecture
Model of laptop (there may be model specific solution already)
Which apps play mono? All?
Really Alsa or pulse (most likely in recent install)
Does headphone play mono / stereo or not at all?
What exactly have you done so far to fit the problem (scripts, tutorials followed)


There is plenty of useful info to provide; but you have not let us see the rabbit - which might explain why offers of support are few in numbers. Help us, help you ;)

---

### Post by Sylos on 2011-12-08
Forgive me - I forget myself.

Here is the proverbial rabbit characteristics:

Laptop is a packard bell easy note TK85-GO-045UK

useful output is as follows

```
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``` 

The system came with win 7 on and that plays both channels of audio but the sound only comes from one area - hence it appears to be a single speaker. When playing sound through with default pulse settings I get only one side (the left I think) coming from my little speaker.


The system is set up with pulse and I have tried using the remap-sink method to mix the two signals together but it causes awful clipping that seems to persist even when you reduce the output volume below half - the clipping still seems to happen but be less audible, Plus the volume is then unusably low.

Headphones work well in stereo when the defualt pulse settings  are used.

See below for the posts I read to try the remap-sink method.

[http://ubuntuforums.org/showthread.php?p=11519793#post11519793](http://ubuntuforums.org/showthread.php?p=11519793#post11519793)

I have also tried changing the channel_map=mono,mono to channel_map=left,left but the result is the same (as you would expect I suppose).
My failure with this method lead me to the conclusion that ALSA was the next port of call. I thought maybe a reverse engineering of the ALSA upmixing to create surround sound could work to mix the 2 channels into a usable non-clipping stream.

Im happy for any suggestions at this point.

Thanks

EDIT: I wonder if there is a way through pulseaudio to reduce the pre mix gain of each channel to 1/2 so that the clipping does not occur. Although I suppose that would be the same as running the output gain at 1/2 - would it?

Also I found this:

[http://ubuntuforums.org/showthread.php?t=1384860](http://ubuntuforums.org/showthread.php?t=1384860)

I wonder if that might enable to do the job if I get rid of pulse?

---

### Post by bluesscream on 2011-12-08
Isn't this a warranty case? This nb definitively has two standard speakers. 
Alternatively (if there is no chance for warranty claim) it should not be too difficult to find a service manual, open the case and check the right speaker's connection

---

### Post by Sylos on 2011-12-09
> **bluesscream said:**
> Isn't this a warranty case? This nb definitively has two standard speakers. 
Alternatively (if there is no chance for warranty claim) it should not be too difficult to find a service manual, open the case and check the right speaker's connection

Hello and thanks for the input.

How do you know there are 2 speakers for this model. I ask because I cant find the info anywhere and the evidence appears to point to only one. The pre-installed win 7appears to be configure to send both channels to the single left speaker - attempting to alter the balance has no effect. If I turn the right channel completely off it sounds the same - if I turn the left off - silence. I should point out win 7 calls this balance control - I call it individual speaker power control.

May give packard bell a shout on this...

EDIT: Called Packard Bell who confirmed laptop only equipped with single mono speaker - quality product!

---

### Post by bluesscream on 2011-12-10
Sorry, 

I could not believe this, but you are right. I searched again and after all  in the description of a german version of this series indeed I found the information in unmistakeable terms.

I found misleading informations on sites like this (full/more produkt details, technical specifications):
http://www.comet.co.uk/p/Laptops/buy-PACKARD-BELL-TK85-GO-045UK-Laptop/741442?cm_mmc=AW-_-Idealo-_-feed-_-741442_PACKARD%20BELL&_$ja=tsid:8361|prd:73258&awc=157_1323520347_7fa0fc89fc27aa3bfe76526ea9ee52ea#product_desciption

Such a packard bell nb had been on my short list too and I thought I was informed

stingy rules :-&

---

### Post by Sylos on 2011-12-10
> **bluesscream said:**
> Sorry, 

I could not believe this, but you are right. I searched again and after all  in the description of a german version of this series indeed I found the information in unmistakeable terms.

I found misleading informations on sites like this (full/more produkt details, technical specifications):
http://www.comet.co.uk/p/Laptops/buy-PACKARD-BELL-TK85-GO-045UK-Laptop/741442?cm_mmc=AW-_-Idealo-_-feed-_-741442_PACKARD%20BELL&_$ja=tsid:8361|prd:73258&awc=157_1323520347_7fa0fc89fc27aa3bfe76526ea9ee52ea#product_desciption

Such a packard bell nb had been on my short list too and I thought I was informed

stingy rules :-&

I would go ahead and remove it from your list in all honesty - it feels a little flimsy, has only one speaker and, to top it off, the MB doesnt support the turbo boost for the processor so Im not getting the full benefit of the i5 i paid for. I know I picked it and therefore its my fault but I cant help feeling a little sour.

I have been thinking a little more about the sound issue and wondered if maybe installing jack with pulse over it might allow me to use jack-mixer to sensibly attenuate the sound ready for being output through the single speaker. Not sure whether that or dmix through alsa is a better option. I assume it would be possible to add jack to the list of apps started at boot/ I really dont want to leave it so my good lady has to jump hoops to listen to music.

---

### Post by Sylos on 2011-12-11
So I have some success. Runnin pulse through the jack sink into jack then changing the jack connections to have left and right connected to output 1 gives me stereo with no distortion.

I now need help automating this from boot. I need a script to do he folloing:

1. kill pulse
2. start jackd
3. make the connection for left and right to output 1

this then needs to be added to the boot list.

Sadly I dont really know how to do this. I have go this far

```
/bin/bash
killall pulseaudio && jackd -d alsa -r 44100
```

I've no idea about the rest. Im also not sure what will happen when I try to use headphones with this set up running.

As always any suggestions gratefully received.

Cheers

---

### Post by jejeman on 2011-12-11
I don't understand, if you kill pulse how is then pulse-jack-sink working?
```
#!/bin/bash
killall pulseaudio && jackd -d alsa -r 44100 &
jack_connect system:capture_1 system:playback_1
jack_connect system:capture_2 system:playback_1

```This is example of connecting, now, it depends what are you connecting...

If you listen thru lineout you will get exactly tha same "stereo" on the left sepaker/phone. Right speaker/phone will be silent.

---

### Post by Sylos on 2011-12-11
> **jejeman said:**
> I don't understand, if you kill pulse how is then pulse-jack-sink working?
```
#!/bin/bash
killall pulseaudio && jackd -d alsa -r 44100 &
jack_connect system:capture_1 system:playback_1
jack_connect system:capture_2 system:playback_1

```This is example of connecting, now, it depends what are you connecting...

If you listen thru lineout you will get exactly tha same "stereo" on the left sepaker/phone. Right speaker/phone will be silent.

Thanks for the input. I have to kill pulse first otherwise it will be hogging the card and jack wont start. I suppose I should add another command to restart it but I know it respawns pretty frequently anyway. 

The reason I ask about the headphone option is that it appears to be that when you plug in it switches from the speaker mode (which is shown as being selected in the pulse settings) to outputting only through the headphones. I wondered if this involves changin the sink (hence it would then change to the default and still output to left and right headphones) or continues using the same sinks but through a different output port. If so I will probably need to write another script to change the settings back when headphones or used. Ideally I'd prefer that to be automated when the headphones are plugged in but I doubt I will be able to achieve that.

I will try your suggestion and see what I get.

Cheers

---

### Post by Sylos on 2011-12-12
Well jack has turned out to be way too unstable. Every time I start firefox the pulse/jack connection drops out and Im back to square one.

Looks like the alsa dmix option is going to be the only way.

---

### Post by Sylos on 2011-12-13
In the interests of having options (on the basis that no option seems ideal) I am still pursuing the jack option for now. I have set up jack with pulse using the 'new method' using scripts from qjackctl. I am however still having issues setting up the connection of left and right to playback_1. Connecting Captures to it doesnt seem to work as all is going through the jack sink. However, trying to set it from the jack sink doesnt seem to be working either. Below is what I have as my post start script:

```
#!/bin/bash
pactl load-module module-jack-sink
pactl load-module module-jack-source
pacmd set-default-sink jack_out
jack_connect PulseAudio_JACK_Sink:front-left system:playback_1
jack_connect PulseAudio_JACK_Sink:front-right system:playback_1
```

This results in the standard connection being made from the PulseAudio JACK Sink to both playback_1 and playback_2. Does anyone know if I have the command written correctly.

Also, what commands would I need to start qjackctl from a script? And would it be possible to start it and start the server from a script with it running as a background process rather than having all 3 windows pop up (minimal intrusion is what Im aiming for).

Thanks

EDIT: runnning my two connection commands from terminal returns error:

```
ERROR PulseAudio_JACK_Sink:front-left not a valid port

```

---

### Post by jejeman on 2011-12-13
Maybe you got wrong name for the port. You can use two ways to find out what are actuall names.
1. after typing jack_connect, use TAB to autocomplete port names
2. use command jack_lsp to list active ports

If you are using startup script, I think that you don't need qjackctl. You should start jack with jack command. Like you did in pervious version of the script.
> Connecting Captures to it doesnt seem to workNo, you should conncect pulse sink ports, like you tried. I was just giving an example for connection with capture ports.

---

### Post by Sylos on 2011-12-14
> **jejeman said:**
> Maybe you got wrong name for the port. You can use two ways to find out what are actuall names.
1. after typing jack_connect, use TAB to autocomplete port names
2. use command jack_lsp to list active ports

If you are using startup script, I think that you don't need qjackctl. You should start jack with jack command. Like you did in pervious version of the script.
No, you should conncect pulse sink ports, like you tried. I was just giving an example for connection with capture ports.

Thanks. I will give that a shot. The reason Im using qjackctl is because it allows me to set the pre and post start scripts. For me this is an advantage as it means I can have several short scripts top stop pulse, make the sink etc. My scripting abilities are awful so when I try to chain a lot together I always seem to fail. Once I have this set up using qjackctl I will attempt to write it to a single script just using the jackd commands and hopefully avoid the qjack intrusion.

Thanks

---

### Post by Sylos on 2011-12-14
Ok. So I have tried jack_lsp which gives:

```
jack_lsp
SSE2 detected
system:capture_1
system:capture_2
system:playback_1
system:playback_2
PulseAudio JACK Sink:front-left
PulseAudio JACK Sink:front-right
PulseAudio JACK Source:front-left
PulseAudio JACK Source:front-right
```

So i try using that but get:

```
jack_connect PulseAudio JACK Sink:front-right system:playback_1
SSE2 detected
ERROR Sink:front-right not a valid port
```

I've tried using the patchbay to create a profile and that seems to work using 2 input/output sockets (but not using only one in/out socket for both channels.

Is there a way to script starting qjackctl that starts the server and initialises the patch profile without the user having to?

Cheers

EDIT: Found the setting for patchbay persistence - just gotta figure out how to autostart the server.

EDIT 2: Got it started using qjackctl -s.

Would still appreciate any help that could be offered on making the connection without resorting to qjacktl though (the plain jackd way). Thanks

---

### Post by jejeman on 2011-12-14
How about
```
jack_connect "PulseAudio JACK Sink:front-right" system:playback_1
```

---

### Post by Sylos on 2011-12-15
Thanks jeje that one appears to work. 

This jack solution does have an interesting effect on the volume level. I assumed I would be able to use the pulseaudio volume control to attentuate the sound level but using the sink to jack appears to max the volume control so all I can do is reduce it. This means I have quite low volume that I cant boost. If I leave the pulse volume low and then connect to jack as soon as I try to adjust the volume it zips up to max without increasing the output. Better than the pulseaudio remap-sink method but still not ideal. I tried using a LADSPA amp plugin to boost it but that quickly gave distortion.

Im beginning to think a good solution may not be possible to achieve.

---

### Post by Sylos on 2012-01-07
Ok. So I have now got a working solution to this conundrum that is (for my needs at least) satisfactory and without any significant drawbacks.

For the benefit of anyone else trying to do this, heres what I did (I should point out that this is taken from searching the web and isnt my own ideas.

STEP 1: remove pulseaudio and install gstreamer components

```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio vlc-plugin-pulse

```

STEP 2: Create .asoundrc file telling alsa's dmix to mix the two channels of stereo to a single mono channel.

```
gedit /home/yourusername.asoundrc
```

Then enter the following code and save:

```
pcm.!default {
    type plug
    slave.pcm {
        type asym
        playback.pcm {
            type route
            slave.pcm "dmix:0"
            ttable.0.0 0.66
            ttable.0.1 0.33
            ttable.1.0 0.33
            ttable.1.1 0.66
        }
        capture.pcm "hw:0"
    }
}

```

This should now give you a sound set up where both channels are mixed to a single channel.

See thread [http://ubuntuforums.org/showthread.php?t=1384860](http://ubuntuforums.org/showthread.php?t=1384860)

Now, removing pulseaudio will mess up your hotkeys for Volume and Mute. Thankfully some kind souls have created some python scriptage to sort this out.

```
sudo apt-get install python python-notify python-gtk2 python-alsaaudio python-eggtrayicon
```

then get the python tools required..

```
wget http://howto.blbosti.com/files/alsa/...let_1.1.tar.gz
```

Then extract them...

```
sudo tar -C /usr/local/bin/ -xzvf alsa_mixer_applet_1.1.tar.gz
```

Then make the files executable...

```
cd /usr/local/bin
sudo chmod +x alsa*
sudo chmod +x volbar.py

```

We then need them to be executed at startup so go to System>Preferences>Startup Applications and add the following:

```
Name: Volbar
Command: /usr/local/bin/volbar.py

Name: alsavol
Command: /usr/local/bin/alsavol.py

```

We then need to alter the volbar script to use the gnome-alsamixer (it was written for xfce). So...

```
sudo gedit /usr/local/bin/volbar.py
```

Change line 97 to read...

```
subprocess.Popen("gnome-alsamixer")
```

Then set the pyhton commands as the hotkeys. Go to System>Prefs>Keyboard shortcuts.

Then set up the individual keys as follows:

```
Name: ALSA Volume mute
Command: /usr/local/bin/alsa_master_mute

Name: ALSA Volume down
Command: /usr/local/bin/alsa_master_down

Name: ALSA Volume up
Command: /usr/local/bin/alsa_master_up

```


For the info on this see [http://ubuntuforums.org/showthread.php?t=1693726](http://ubuntuforums.org/showthread.php?t=1693726)

---

