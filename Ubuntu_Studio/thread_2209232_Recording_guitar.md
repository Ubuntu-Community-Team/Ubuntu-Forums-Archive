---
title: "Recording guitar"
date: 2014-03-04
forum: Ubuntu Studio
---

### Post by Footnote31 on 2014-03-04
Hello everyone ):P

I am a musician and after switching to Ubuntu from Windows I wanted to record guitar. I'm already succesfully using tuxguitar, but that's about the only software I managed to get going. Specifically, I tried to record through Rakarrack(and possibly Guitarix in the future), and I used QJackCtl to connect the program with the inputs and outputs. However, everything I got was slow cracking noise, regardless of settings in any of the programs. I looked for answers and solutions to my problem everywhere, I compared error messages(seeing as this seems essential to solving problems in Ubuntu). Eventually, I thought I should maybe switch from jackd2 to jackd1, but this only worsened the condition, as now QJackCtl would either run with too much xruns or not at all(currently), while Rakarrack sends the error ''can not make a jack client, is jackd running?''(which of course is). I also tried editing the audio.conf file, but to no avail. As a final resort, I considered switching to Ubuntu Studio(even though I'm not using my laptop solely for recording).

So, basically, I'm stuck with both QJackCtl and Rakarrack refusing to open, with both jackd and pulseaudio running as processes. The QJack error is:   [COLOR=#999999]22:28:19.362 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]22:28:19.368 Statistics reset.[/COLOR]
 [COLOR=#cccc99]22:28:19.374 ALSA connection change.[/COLOR]
 [COLOR=#999999]22:28:19.394 JACK is starting...[/COLOR]
 [COLOR=#990099]22:28:19.394 /usr/bin/jackd -n2 -dalsa -dhw:0 -r88200 -p128 -n3 -Xraw[/COLOR]
 no message buffer overruns
 unknown option character l
 no message buffer overruns
 unknown option character l
 jackd 0.122.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 [COLOR=#66cc99]22:28:19.400 ALSA connection graph change.[/COLOR]
 JACK compiled with System V SHM support.
 `2' server already active
 no message buffer overruns
 [COLOR=#999999]22:28:19.452 JACK was started with PID=3900.[/COLOR]
 [COLOR=#999999]22:28:19.492 JACK was stopped with exit status=1.[/COLOR]
 [COLOR=#ff0000]22:28:21.613 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 no message buffer overruns
 unknown option character l

My sound devices(as listed in QJackCtl) are HDA Intel PCH(hw:0), ALC663 Analog(hw:0,0) and ALC663 Digital(hw:0,1). I'm using Ubuntu 13.10(64-bit) on Asus N56VJ laptop.


Any help is gladly appreciated. I'm not giving up on using Ubuntu for recording, regardless of all these problems:guitar:

---

### Post by su:bhatta on 2014-03-05
Have you tried using ALC663 Digital(hw:0,1) as the Interface in QJackCtl Settings ?

Have you followed this guide : [https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro/1204](https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro/1204)

---

### Post by jejeman on 2014-03-05
You have wrong command to start JACK
>  /usr/bin/jackd -n2 -dalsa -dhw:0 -r88200 -p128 -n3 -Xraw
you have one extra -n switch. So JACK interprets it as the name of the server, i guess.
>  `2' server already activeUsually name of the JACK server is "default". Rakarrack is by default connecting to "default" JACK server, not to "2" JACK server.

Check your JACK settings.
And for troubleshooting purposes first try to monitor guitar, both with just ALSA, then with JACK without recording.

---

### Post by luctor on 2014-03-05
Setting up a proper audio environment is a bit of a hassle, once you got it running the possibilities are endless.

It's a good idea to install the low-latency kernel 
_keep in mind if you have a Nvidia graphics card, the Nvidia drivers won't work and you'll have to use the nouveau drivers_
```
sudo apt-get install linux-image-lowlatency
```
add yourself to the audio group (username is your username ..)
```
sudo usermod -a -G audio username
```
use jack with realtime priority , option -R, lower samplerate to 44100

I recommend installing the kxstudio repos
[http://kxstudio.sourceforge.net/Repositories](http://kxstudio.sourceforge.net/Repositories)
Have a look at their apps, they are very useful
[http://kxstudio.sourceforge.net/Applications](http://kxstudio.sourceforge.net/Applications)

---

### Post by jejeman on 2014-03-05
> **luctor said:**
> _keep in mind if you have a Nvidia graphics card, the Nvidia drivers won't work and you'll have to use the nouveau drivers_
```
sudo apt-get install linux-image-lowlatency
```For which version? In 12.04 and 12.10 it works fine with nvidia driver.

---

### Post by Footnote31 on 2014-03-05
Thanks to everyone for their help:D As mentioned above, I tried to record myself without jack, via pulseaudio, just to see if it was the soundcard or mic problem, and it worked. Yet again, QJackCtl crashes everytime with a lot of Xruns, and Rakarrack still doesn't start. I tried all of the suggestions above except for installing the nouveau drivers(yes, it's nVidia) and I've obtained low-latency kernel via the aforementioned terminal command(I'm only holding it because it seems there's more to getting it work than just configure, make and make install commands). 

Now, the message from QJackCtl is: 

 [COLOR=#999999]19:54:12.880 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]19:54:12.880 Statistics reset.[/COLOR]
 [COLOR=#cccc99]19:54:12.887 ALSA connection change.[/COLOR]
 [COLOR=#999999]19:54:12.917 JACK is starting...[/COLOR]
 [COLOR=#990099]19:54:12.918 /usr/bin/jackd -n2 -dalsa -r44100 -p64 -n3 -Xraw -D -Chw: PCH,0 -Phw: PCH,0[/COLOR]
 no message buffer overruns
 unknown option character l
 no message buffer overruns
 unknown option character l
 [COLOR=#66cc99]19:54:12.922 ALSA connection graph change.[/COLOR]
 jackd 0.122.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 loading driver ..
 apparent rate = 44100
 creating alsa driver ... hw: PCH,0|hw: PCH,0|64|3|44100|0|0|nomon|swmeter|-|32bit
 [COLOR=#999999]19:54:12.962 JACK was started with PID=4057.[/COLOR]
 ALSA lib conf.c:4578: (parse_args) Unknown parameter 1
 ALSA lib conf.c:4711: (snd_config_expand) Parse arguments error: No such file or directory
 ALSA lib control.c:953: (snd_ctl_open_noupdate) Invalid CTL hw: PCH,0
 control open "hw: PCH,0" (No such file or directory)
 configuring for 44100Hz, period = 64 frames (1.5 ms), buffer = 3 periods
 ALSA: final selected sample format for capture: 32bit integer little-endian
 ALSA: use 3 periods for capture
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: use 3 periods for playback
**** alsa_pcm: [COLOR=#999999]xrun of at least 0.005 msecs(and many more)
.....
19:54:16.988 JACK is stopping...[/COLOR]

 jack main caught signal 15
 no message buffer overruns
 [COLOR=#999999]19:54:17.022 JACK was stopped successfully.[/COLOR]
[COLOR=#cc0000]
As you can see, I changed the samplerate and interface(I know ALC is the only input device, yet it fails just like any other option). I did notice the run command, and I tried to run it from terminal(I supposed there should be ''-n1'' instead of ''-n2''). Still, no change.

So, now I know it's definitely a Jack problem. I don't believe the kernel is responsible for this(as I managed to run both QJack with Alsa Modular Synth), but if that's the solution, I won't object.:-|


[/COLOR]

---

### Post by jejeman on 2014-03-05
Here is my command
```
/usr/bin/jackd -t1000 -dalsa -dhw:0 -r48000 -p128 -n2 -Xseq -o2
```
as you can see there is only one -n parameter. The first -n parameter is for JACK server name. You don't need that, it is even better if you don't. p64 is really low value. But here the most important thing is that
> control open "hw: PCH,0" (No such file or directory)Check you card name. Better to use "hw" number reference.
Also why -n3? USB card?
Sometimes the MIDI driver setting can cause JACK to crash, turn it off.

---

### Post by brianmc on 2014-03-08
> **Footnote31 said:**
> My sound devices(as listed in QJackCtl) are HDA Intel PCH(hw:0), ALC663  Analog(hw:0,0) and ALC663 Digital(hw:0,1). I'm using Ubuntu  13.10(64-bit) on Asus N56VJ laptop.

[...]

QJackCtl crashes everytime with a lot of Xruns, and Rakarrack still doesn't start. I tried all of the suggestions above except for installing the nouveau drivers(yes, it's nVidia) and I've obtained low-latency kernel via the aforementioned terminal command(I'm only holding it because it seems there's more to getting it work than just configure, make and make install commands). 

Now, the message from QJackCtl is: 

[COLOR=#990099]19:54:12.918 /usr/bin/jackd _***-n2***_ -dalsa -r44100 -p64 _***-n3***_ ***_-Xraw -D -Chw: PCH,0 -Phw: PCH,0_***[/COLOR]
 
[...]

creating alsa driver ... hw: PCH,0|hw: PCH,0|64|3|44100|0|0|nomon|swmeter|-|32bit
 
ALSA lib conf.c:4711: (snd_config_expand) Parse arguments error: No such file or directory
 ALSA lib control.c:953: (snd_ctl_open_noupdate) Invalid CTL hw: PCH,0
 control open "hw: PCH,0" (No such file or directory)
 configuring for 44100Hz, period = 64 frames (1.5 ms), buffer = 3 periods
 [COLOR=#cc0000]
[/COLOR]

First thing is you're trying for too-small a Frames/Period.
You've also a messy, and confusing, set of values set as the Interface, Input Device and Output Device. Just set them all back to (default) in [FONT=fixedsys]*QJackCtl*[/FONT]. If you want Jack to always run on one sound card, use the name. That would, probably, be hw:PCH which is then assumed if you've (default) for the  input and output devices. I've highlighted the bits that are just plain wrong with the above command line. If you leave everything as default, with CD quality (44.1kHz) samplerate, and start with 128 Frames/Period and 2 Periods/Buffer, leaving the MIDI Driver at blank to start with.

Your command line in .jackdrc should look like this:
```

[FONT=courier new]**/usr/bin/jackd -p128 -dalsa -dhw:PCH -r44100 -p128 -n2**[/FONT]
```

If that gives you Xruns, it is the *second [FONT=courier new]**'-p**[/FONT]<n>*' (currently [FONT=courier new]128[/FONT]) which should be increased by powers of two (512, 1024). Similarly, as the above poster suggests, you could try changing the Interface (shown as '*[FONT=courier new]-dhw:PCH[/FONT]*') to '[FONT=courier new]*-dhw:Digital*[/FONT]'. A lot of built-in sound hardware will be happiest with a sample rate of 48kHZ ([FONT=courier new]*-r48000*[/FONT]), but not anything higher. Some fiddling with alsamixer may also be required once you've got rid of Xruns. The '[FONT=fixedsys]***-n**<value>*[/FONT]' shown at the end of the above line corresponds to the periods in the hardware buffer; you had two of these, where you can only specify the value once and for one audio device. A value of three works well with a lot of USB audio hardware, but an onboard card should be fine with two.

Your original [FONT=courier new]*jackd*[/FONT] command looks as-if you've just kept cranking up the sample rate to push down the latency. You will have gone way-above what the hardware supports when you picked 88.2kHz; The CD sample rate is fine (chosen because the human ear can't distinguish it from any higher rate) and, unless/until you're doing a lot of signal processing it's good-enough for inputs. The blurb on any Windows audio software ***lies*** where it says zero latency. That's only available as a hardware function where the audio hardware directly routes inputs to outputs (or through a built-in mixer).

You'll notice a lag if your initial reliable latency is over 20ms (*Eg 23.2ms with 512 Frames/Period, 44100 Sample Rate, and 2 Periods/Buffer*); but, getting it to work before trying to tune it is the best approach.

You don't specify which distro you started from, but since you had to install [FONT=fixedsys]*linux-image-lowlatency*[/FONT], I'd guess it wasn't the Ubuntu Studio distro. Currently, it's easier to start from that *and add the extra applications you want/need.* Just remember, you'll probably not want to run them at the same time as doing near-realtime audio work.

---

### Post by Footnote31 on 2014-03-16
> **brianmc said:**
> 
  
Your command line in .jackdrc should look like this:
```

[FONT=courier new]**/usr/bin/jackd -p128 -dalsa -dhw:PCH -r44100 -p128 -n2**[/FONT]
```

You don't specify which distro you started from, but since you had to install [FONT=fixedsys]*linux-image-lowlatency*[/FONT], I'd guess it wasn't the Ubuntu Studio distro. Currently, it's easier to start from that *and add the extra applications you want/need.* Just remember, you'll probably not want to run them at the same time as doing near-realtime audio work.

Thanks for a very detailed reply, but I still get the same response. The command for starting jack is now almost identical to yours, but why is the p128 mentioned twice? I'll try to reinstall the system(it's obviously not ubuntu studio) but if that fails, I'm switching to US.

---

### Post by Footnote31 on 2014-03-18
Just to notify, I works now:). Turns out something was wrong with jack files, and a complete reinstallation solved the problem!

---

